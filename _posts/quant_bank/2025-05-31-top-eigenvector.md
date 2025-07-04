---
title: Finding top eigenvector 
categories:
  - quant-question-bank
tags:
  - computational linear algebra
---

How do you find the top eigenvector of a square matrix?

<details markdown="block">
  <summary>Solution</summary>
  The most simple answer to this is the power method. It is 
  a very simple algorithm that applies to any diagonalizable matrix. 
  Diagonalizable matrices admit eigendecompositions, and thus 
  powers $A^k$ will have eigenvalues $\lambda_i^k$. Hence
  the leading eigenvalue will tend to dominate as we increase $k$, and
  so as $k$ increases, $u_k$ will converge to the top eigenvector.
  Now that we have some intuition, here is the algorithm. For a 
  matrix $A$, begin with a random unit vector $u_0$. The update rule 
  is then:
  $$u_{k+1} = \frac{Au_k}{\|Au_k\|_2}$$

  A more advanced method is Arnoldi iteration. Intuitively, it extends the
  idea of the power method, utilizing the information in $u_0,\dots,u_K$
  to estimate the top $K$ eigenvalues of $A$. The full details are rather 
  involved, and so I will simply advise interested readers to look into Arnoldi
  iteration themselves.
</details>
