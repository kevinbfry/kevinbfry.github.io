---
title: OLS coefficient bounds
categories:
  - quant-question-bank
tags:
  - probability
  - linear regression
---

If $Y \sim X$ gives coefficient $\hat\beta$, what is the bound on the coefficient
$\hat\theta$ from $X \sim Y$?

<details>
  <summary>Solution</summary>
  

Note that 

$$
\begin{gather*}
\hat\beta = \mathrm{Cov}(X,Y) / \mathrm{var}(X) \\
\hat\theta = \mathrm{Cov}(X,Y) / \mathrm{var}(Y)
\end{gather*}
$$

and so

$$
\hat\beta\hat\theta = \mathrm{Cor}(X,Y)^2
$$

Since correlation is bounded between $-1$ and $1$, we must have $\hat\beta\hat\theta$
is bounded between $0$ and $1$. Thus $\hat\theta \in \left[0, \hat\beta^{-1}\right]$.
</details>