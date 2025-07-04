---
title: OLS when $X$ is too large. 
categories:
  - quant-question-bank
tags:
  - linear regression
  - computational linear algebra
---

What is OLS solution? How is it derived? How to compute with $n \gg p$,
such that $X$ cannot be loaded in memory. Consider both when $p$ very
small, but also when $p$ is also very big, such that a $p \times p$ matrix 
is also too big to load into memory

<details markdown="block">
  <summary>Solution</summary>

  The solution is
  $$\hat\beta = \left(X^\top X \right)^{-1} X^\top Y$$
  This is derived from the assumptions of OLS and maximizing the resulting 
  log-likelihood. In case you don't have the derivation down cold yet, it 
  goes as follows. The assumptions of OLS are:

  <ul>
    <li>The samples are independently distributed</li>
    <li>$Y_i \mid X_i \sim \mathcal{N}(X_i^\top \beta, \sigma^2)$</li>
    <li>The samples are homoskedastic (as indicated by the common $\sigma^2$)</li>
    <li>We are assuming the moel is well-specified (as indicated by the mean being $X_i^\top \beta$)</li>
  </ul>

  Thus we know the likelihood implied by this model and can maximize it. It is 
  equivalent to minimizing the negative log-likelihood, which is (up to constants
  and terms free of $\beta$):
  
  $$
  \min_\beta \frac{1}{2} \|Y - X\beta\|_2^2
  $$
  <p>
  A simple calculation can show that the solution to this problem is the $\hat\beta$ given above. 
  </p>
  <p>
  To compute this, the naive way is to compute $X^\top X$, invert it, then multiply it by $X^\top Y$.
  However, when $n \gg p$ such that we can no longer load $X$ into memory we need a different approach. 
  In this case we should load $X$ two columns at a time, computing $X_i^\top X_j$ and assembling the 
  full $X^\top X$ piece by piece in this way. 
  </p>
  <p>
  If we move to the case where $p$ is also very large, such that a $p \times p$ matrix cannot be 
  loaded into memory, we need to move beyond the naive computations. In this case methods such as
  Graham-Schmidt successive orthogonalization need to be implemented. The interested reader 
  should refer to Ch 3.2 in <a href="https://hastie.su.domains/ElemStatLearn/">ESL</a> for details. The 
  procedure only operates on pairs of columns at a time.
  </p>
  <p>
  As an aside, one of the most fundamental guidelines in computational linear algebra is 
  to never explicitly compute an inverse unless you have to. Often you can instead solve
  the system of equations implied by the inverse, in this case $X^\top X \beta = X^\top Y$,
  in much fewer computations.
  </p>
</details>
