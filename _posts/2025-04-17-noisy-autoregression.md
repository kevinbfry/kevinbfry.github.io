---
title: Estimating Variances in Autoregression
categories: 
  - quant-questions
tags: 
  - autoregression
  - method of moments
  - linear regression
---

I was asked this in a quant research onsite interview. It is a question about estimating variances in a noisy autoregression setting.

# Setting

$$
X_t = X_{t-1} + \epsilon_{t-1}, \quad Y_t = X_t + \gamma_t \\
X_0 = 0, \quad \epsilon_t \overset{iid}{\sim} (0, \sigma_\epsilon^2), \quad \gamma_t \overset{iid}{\sim} (0, \sigma_\gamma^2), \quad \gamma_s \perp \epsilon_t \ \forall s,t
$$

$$X_t$$ are latent variables, only $$Y_t$$ are observed.

### Goal: Estimate $$\sigma_\epsilon^2, \sigma_\gamma^2$$

During the interview, we discussed two possible approaches and if there was any benefit of one over the other. I thought the second method was better, but my interview claimed there was no difference (I'll explain more later). In this note we will implement both on simulated data to investigate this disagreement.


```python
import numpy as np
```


```python
np.random.seed(1)
```


```python
sigma_eps = np.sqrt(.5)
sigma_gamma = np.sqrt(.75)

T = 2_000
```


```python
# Normal errors
eps = np.random.randn(T)*sigma_eps
gamma = np.random.randn(T)*sigma_gamma

eps.var(), gamma.var()
```




    (0.5058530475701912, 0.7357306515553749)




```python
X = np.cumsum(eps)
X[:10], eps[:10]
```




    (array([ 1.14858562,  0.71600851,  0.34253469, -0.4161687 ,  0.1957669 ,
            -1.43166672, -0.19789849, -0.73615305, -0.51055834, -0.68688983]),
     array([ 1.14858562, -0.43257711, -0.37347383, -0.75870339,  0.6119356 ,
            -1.62743362,  1.23376823, -0.53825456,  0.22559471, -0.17633148]))




```python
Y = X + gamma
```

## Solve using MoM with two equations

With this setting, my first intuition is to look at differences. And in this case this intuition works out well, as differences remove the latent variables $$X_t$$, leaving us with only linear combinations of our noise variables $$\epsilon_t, \gamma_t$$. In particular, we can write these two equations and solve for the variance by method of moments (MoM).

$$
\begin{gather*}
\Delta_k Y = Y_t - Y_{t-k} \\
\mathrm{var}(\Delta_1 Y) = \sigma^2_\epsilon + 2\sigma^2_\gamma \\
\mathrm{var}(\Delta_2 Y) = 2\sigma^2_\epsilon + 2\sigma^2_\gamma \\
\end{gather*}
$$



```python
var_d1y = np.diff(Y,1).var()
var_d2y = np.diff(Y[::2]).var()
hat_sigma_eps = np.sqrt(var_d2y - var_d1y)
hat_sigma_gamma = np.sqrt((var_d1y - hat_sigma_eps**2) / 2)
hat_sigma_eps**2, hat_sigma_gamma**2
```




    (0.6188456170828185, 0.6932916958164618)



## Solve with OLS
When asked to improve on this solution I proposed that instead of just two equations, use $$n$$ equations and find best estimate by ordinary least squares regression (OLS). This seemed like a natural way to pool the information from the many moment equations we have in this setting, since the estimated variances will often obey a CLT.

My interview agreed you could do this, but asked if this would produce a better solution than the MoM approach. I argued it would, as you had more information from more estimated variances of differences. However, my interviewer argued the colinearity of the rows meant there was no additional information, and thus no benefit of OLS over MoM. Let's see what happens in our simulation.


```python
n = 4
Z = np.array([np.diff(Y[::k]).var() for k in range(1,n+1)])
W = np.hstack((np.arange(1,n+1)[:,None],2*np.ones((n,1))))
Z, W
```




    (array([2.00542901, 2.62427463, 2.9731524 , 3.68803624]),
     array([[1., 2.],
            [2., 2.],
            [3., 2.],
            [4., 2.]]))




```python
ols_sol = np.linalg.inv(W.T @ W) @ W.T @ Z
ols_sol
```




    array([0.53966995, 0.7367741 ])



It's not perfect but clearly does improve the estimate, especially of $$\sigma_\epsilon^2$$.

This is because my interview is correct that the added feature matrix rows in $$W$$ are linearly dependent, the extra rows in $$Z$$ do add new information. Thus, we do see better estimation from adding more moment equations. If the combined matrix of $$\begin{bmatrix} W & Z \end{bmatrix}$$ was linearly dependent, then yes the added rows would not add any more information and yield the same solution.

Now the problem did not specify the errors were normally distributed, only specified their mean and variance. So we could try something with fatter tails, like a t-distribution. This should ensure we're not accidentally benefitting from using a nice distribution like the normal.


```python
## student t errors
df = 5
eps = np.random.standard_t(df,T)*sigma_eps / np.sqrt(df / (df - 2))
gamma = np.random.standard_t(df,T)*sigma_gamma / np.sqrt(df / (df - 2))

eps.var(), gamma.var()
```




    (0.48906363912803774, 0.7296331959847161)




```python
X = np.cumsum(eps)
Y = X + gamma
```

### Solve using MoM with two equations



```python
var_d1y = np.diff(Y,1).var()
var_d2y = np.diff(Y[::2]).var()
hat_sigma_eps = np.sqrt(var_d2y - var_d1y)
hat_sigma_gamma = np.sqrt((var_d1y - hat_sigma_eps**2) / 2)
hat_sigma_eps**2, hat_sigma_gamma**2
```




    (0.6018669357994432, 0.7074736001630793)



### Solve with OLS


```python
n = 4
Z = np.array([np.diff(Y[::k]).var() for k in range(1,n+1)])
W = np.hstack((np.arange(1,n+1)[:,None],2*np.ones((n,1))))
Z, W
```




    (array([2.01681414, 2.61868107, 2.96137538, 3.62967548]),
     array([[1., 2.],
            [2., 2.],
            [3., 2.],
            [4., 2.]]))




```python
ols_sol = np.linalg.inv(W.T @ W) @ W.T @ Z
ols_sol
```




    array([0.51812783, 0.75565847])



Again we see that the OLS method provides better estimates than simply using two equations.

During the interview, I did not want to disagree too strongly with my interviewer. I must have made a mistake in my thinking on the spot, and I did not want to get bogged down on one question. After all, they have worked on this question much more than me. However, after this analysis I think in future I should continue to discuss the topic until I fully understand why I am wrong, or can convince the other person I am right. Perhaps I misunderstood the question, or I have made an error in this note. Please let me know if I have.
