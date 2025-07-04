---
title: Bounding $R^2$ 
categories:
  - quant-question-bank
tags:
  - computational linear algebra
---

# Rotating data 

We have $X \sim U[-2,2], Y \sim U[-1,1]$. If we apply rotation matrix
$$R = \begin{bmatrix}
        \sqrt 2 / 2 & -\sqrt 2/2 \\ \sqrt 2/2 & \sqrt 2/2
    \end{bmatrix}$$, how does OLS fit change? Intercept?

<details markdown="block">
  <summary>Solution</summary>
   

Use covariance/variance definition and plug and chug.

<details markdown="block">
  <summary>Solution</summary>

</details>

# Group all anagrams 

Given text file of words, write code that outputs a file that has
grouped the words by anagram, outputting all words that are anagrams of
eachother on the same line.

# Details of k-means algorithm

Have unlabeled $d$-dimensional data, know there are $k$ groups. How find
groups? Should answer $k$-means. Explain how the algorithm works. Prove
that the algorithm converges. What would you do about ties? How would
you pick $k$?

<details markdown="block">
  <summary>Solution</summary>
   

Two alternating steps:

-   Assign centers: Random for intialization. In later iterations, take
    mean of points in group.

-   Assign groups: Assign points to group based on closest center

This converges because assigning centers is a convex problem, so always
descend on this step. When assigning groups, we also descend with each
steps. And note that there are a finite number of group assignments
$k^n$, so we must terminate.

For ties, we can simply break them by some deterministic rule: stay in
same cluster if cluster is in running, else randomly assign.

# Voleon: Pseudoinverse

Solving underdetermined system.

# Betting on a tournament bracket 

Have a tournament bracket. Each team has ratings $r_t$, and the prob of
team 1 beating team 2 is $r_1 / (r_1 + r_2)$. Also given prices to
buy/sell a team. Come up with strategy to maximize performance, one
round at a time.

# Betting on coin flips 

You and $n$ others each can bet an amount on a coin being heads or tails
(up to your total cashpile). If incorrect, lose $X$. If correct, you
split total pot with all other winners. Come up with a strategy to
maximize performance.

# IP: Find Median 

Given $X_1,\dots,X_n$ find the median. First in O(nlogn), then in O(n).

# IP: Max \# drawdown days 

Given a vector of returns $\{R_t\}$, if the mean is $\mu=8$ and the
standard deviation is $\sigma=3$, can you bound the maximum number of
drawdown days?

# NM: Linear algebra and mean operator 

We have a matrix $A \in \mathbb{R}^{m \times n}$ and vector $X \in \mathbb{R}^n$.
Suppose that $m^{-1}\mathbf{1}^\top A X = Avg(X) = n^{-1} \mathbf{1}^\top X$. What does
that tell us about $A$? Further, can you show that
$|Avg(AX)| \le |Avg(X)|$?

# JY: Eigenvalues and transposes 

If $A \in \mathbb{R}^{n \times n}$, does it necessarily have the same
eigenvalues as $A^T$? Now suppose $B = .5 (A + A^T)$. Can you say
anything about the eigenvalues of $B$ and $A$?

# CV

Some random intro, obviously pointing you to use CV. Then asks about
tradeoff in number of folds $k$. If you use fewer folds, the fitted
functions become more independent, and thus each fold's error estimate
will be more independent. On the other hand, with more folds you have
more correlation between folds, but you also average over more points.
Unclear which one wins out.

I'll also write out some facts about CV here

-   In general, for lots of folds, you will get small bias but high
    variance because averaging doesn't do much with such correlated
    folds. With smaller folds, you get lower variance since they are
    more independent, but you may have more bias depending on model and
    sample size $n$.

-   **LOOCV** is fast for OLS (and other similar smoothers). Can simply
    fit full model and do $\sum_i r_i^2 / (1-h_ii)^2$. Proof by
    Woodbury, so should work for any smoother where adding/removing a
    sample is just a rank one update to the smoothing matrix.

-   **GCV** approximates LOOCV update for linear methods
    ($n^{-1} \sum r_i^2/(1-S_{ii})^2$) with denominator $1 - \mathrm{tr}(S)/n$.

<details markdown="block">
  <summary>Solution</summary>
 
</details>

# Bootstrapping 

How to bootstrap prediction error? LOOB bootstrap error; like LOOCV but
average over all bootstraps not containing $i$. How to bootstrap
standard errors

-   Usual method. Assume
    \\[B^{-1} \sum \|\hat\theta^{(b)} - \bar\theta^{(B)}\|_2^2 \approx SE(\hat\theta)\\]

-   For CI's standard way is assuming
    \\[\hat\theta - \theta \overset{d}{\approx} \hat\theta^{(b)} - \hat\theta\\]
    and go from bootstrap quantiles
    \\[\mathrm{Pr}(q_{\alpha/2} < \hat\theta^{(b)} < q_{1-\alpha}/2) \approx \mathrm{Pr}(2\hat\theta - q_{1-\alpha/2} < \theta < 2\hat\theta - q_{\alpha/2})\\]

-   Could also mention studentized bootstrap CI. Instead of using
    bootstrap quantiles directly, nested bootstrap. For each bootstrap
    sample, bootstrap again and estimate standard error on that $s^b$.
    Then compute quantiles of studentized statistic
    $(\theta^b - \hat\theta)/s^b$. Then
    \\[\mathrm{Pr}(q_{\alpha/2} < (\theta^b - \hat\theta)/s^b < q_{1-\alpha/2}) \approx \mathrm{Pr}(\hat\theta - s^b q_{1-\alpha/2} < \theta < \hat\theta - s^b q_{\alpha/2})\\]
# What do different firms look for?

## Jane Street

Jane Street likes expected value, optimal strategy/tradeoff type
questions. They care to see how you think, often by starting with crude
bounds and then refining, or basic strategies then iteratively
improving. Also like thinking about edge cases then smoothly
interpolating between them.

## 5 Rings

5 Rings is known for asking questions with a timed response: they'll give you 10 seconds for some questions, 30 seconds for others. You have to think fast on your feet, and maybe even make good guesses using intuition and heuristics.

## Voleon

They like to ask about lots of machine learning models, so let's talk about a few common ones here:

-   OLS: In particular, the hat matrix $H$. Big $H_ii$ (close to 1)
    means leverage point. $\hat y= Hy, r= (I-H)y$, and
    $\mathrm{Cov}(\hat y) = H\sigma^2, \mathrm{Cov}(r) = (I-H)\sigma^2$. Leverage
    doesn't necessarily mean big residual
    $r_{i} = y_i - \hat y_{i} = (1-H_ii) (y_i - \hat y_{-i})$.

-   **Trees:** You fit a tree by making binary decision rules on a given
    feature. Usually done in greedy fashion. Trees are pruned based on
    cost complexity in regression ($SSE(T) + \alpha |T|$) and
    cross-entropy/gini/misclass. rate for classification
    ($Err(T) + \alpha|T|$). In classification, usually cross-entropy for
    growing, misclass. for pruning. Handle missing values well using
    surrogate splits. $O(p n\log n)$ complexity.

-   **RF:** Grow many trees, each on a different bootstrap sample. At
    each split, choose from only subset of features $\sqrt{p}$. Average
    trees to get final model.

-   **Boosting:** Fit weak learners to combine into a strong learner.
    Essentially increase weights of mistakes, decrease weights for
    others.

-   **Gradient boosting:** Fit trees on gradients to learn regions. Then
    fit each region based on original loss function.

-   **SVM:** Finding maximum margin classifier, allowing for some points
    to fall inside margin. SVC is usually inner product on original
    feature space. Because it only relies on inner products of $x,x'$,
    can use kernel trick to do same thing on higher-dimensional spaces.
    This makes it an SVM.

They also put you through a data analysis interview, where you have to work through a data problem in real-time with your interviewer.


## DRW: 2025/07/01 quant interview questions (prob don't upload for a year or so)

- 3x3 matrix: find sum of squares of eigenvalues
- 3x3 correlation matrix: bound correlation of two variables given other correlations
- 3 toys: have 3 boxes. uopened they are worth $3. One has A worth $2, one has B worth $3, and one has C worth $4. What is optimal strategy for opening boxes to maximize profit? Give expectation, variance of optimal profit.
- Buses: People come according to a poisson process with aprameter 10. Buses arrive according an exponentional distribution with parameter 5. What is average number of people on a bus?
- Markov chain problem: Two parties A and B. After each election, 10% of A voters switch, and 12% of B voters switch. If we start with 70% B and 30% A, what is the steady state distribution of voters?
- Basic bayes problem: probably won't do this one. Coin is biased to 2/3, but is equally likely to be biased heads as tails. What is probability it is biased towards heads if you get 3 heads out of 4 flips?
