---
title: Solving an underdetermined system
categories:
  - quant-question-bank
tags:
  - linear algebra
  - optimization
---

A lot of firms will ask questions that are variations on the following: Suppose you have a $p$ 
-dimensional parameter $x$ you want to estimate, and you have $n < p$ samples of equations relating 
these values, represented by a matrix $A$ and vector $b$ satisfying $Ax = b$. How would you estimate $x$?

<details markdown="block">
  <summary>Solution</summary>
  This is an underdetermined system. So there are technically infinitely many solutions. But a rational approach is to pick the solution with smallest Euclidean norm. That is, we aim to solve

  $$
  \begin{aligned}
  \min_x &\ \|x\|_2^2 \\
  \mathrm{s.t.} &\ Ax = b
  \end{aligned}
  $$

  We apply the method of Lagrange multipliers, so our problem is to now solve

  $$
  \min_{x,\lambda} \|x\|_2^2 - \lambda^\top(Ax - b)
  $$

  Taking derivatives and setting to 0 we get the following equations

  $$
  \begin{gathered}
  2x = A^\top \lambda \\
  Ax = b
  \end{gathered}
  $$

  Some basic algebra leads to the result that $x = A^\top (AA^\top)^{-1}b$. 

  Every matrix has a singular value decomposition, so we can write $A = UDV^\top$. So our answer is equivalently

  $$
  \begin{aligned}
  A^\top (AA^\top)^{-1}b &= VD^TU^T(UDV^TVD^TU^T)^{-1} b \\
  &= VD^TU^T(USU^T)^{-1} b \\
  &= VD^TS^{-1}U^T \\
  &= VD^{-T}U^T
  \end{aligned}
  $$

  where $S = DD^\top$ is a diagonal matrix with diagonals $\sigma_i^2$.



</details>