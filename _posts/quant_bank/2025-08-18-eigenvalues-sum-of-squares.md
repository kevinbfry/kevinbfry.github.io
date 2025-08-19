---
title: Find the sum of squared eigenvalues
categories:
  - quant-question-bank
tags:
  - linear algebra
  - optimization
---
Find the sum of squared eigenvalues of a square matrix $X$.

<details markdown="block">
  <summary>Solution</summary>
  One could explicitly compute the eigenvalues if the matrix was small enough and then square them. But one could instead note that 
  $$
  \begin{gathered}
  \mathrm{tr}(X^2) = \sum_{i} \lambda_i^2 \\
  \mathrm{tr}(X^2) = \sum_{i,j} X_{ij}X_{ji}
  \end{gathered}
  $$
  And thus one can directly calculated the sum of squared eigenvalues without computing the eigenvalues themselves.


</details>