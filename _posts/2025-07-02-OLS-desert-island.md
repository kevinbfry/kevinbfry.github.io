---
title: OLS on a desert island
categories:
  - quant-question-bank
tags:
  - linear regression
  - computational linear algebra
---

Without any package imports, how would you compute OLS?

<details>
  <summary>Solution</summary>
  This is a pretty open-ended question, but however you go about solving it, you'll
  have to demonstrate knowledge of computational linear algebra algorithms. Here are some options:

  <ol>
  <li> <b>Just solve the linear system:</b> It is rather simple to write code to do simple Gaussian elimination to solve the system $X^\top X \beta = X^\top y$
  for $\beta$.</li> 

  <li> <b>Gradient descent:</b> The most basic optimization algorithm. Just take steps
  $$\hat\beta^{(t+1)} = \hat\beta^{(t)} - \alpha X^\top (y - X\hat\beta^{(t)})$$ </li>
  
  <li> <b>Quasi-Newton's method:</b> If you wanted to go a step further than gradient
  descent, you could do Newton's method. However, you would need to invert
  $X^\top X$, which is more costly than just solving the linear system. Instead
  you may try to approximate the inverse cheaply and use a Quasi-Newton method.
  Perhaps the simplest is a diagonal approximation. However, note that you cannot
  pick just any approximation, such as taking the diagonal elements of $X^\top X$
  and inverting that. In order to get convergence you need to ensure that the 
  approximate Hessian majorizes the true Hessian. This difficulty makes it not
  obvious how to pick an approximation that is better than gradient descent
  without being more computationally costly than other approaches.</li>

  <li> <b>QR:</b> You can solve the linear regression by the $QR$ decomposition. This
  can be solved with the Graham-Schmidt method, which only requires dot products
  and back substitution. Once you have found $Q,R$ s.t. $X = QR$, then 
  $\hat\beta = R^{-1} Q^\top y$. This can be easily solved by back-substitution since $R$
  is upper-triangular. For details see Chapter 3.2 in <a href="https://hastie.su.domains/ElemStatLearn/">ESL</a>.</li>

  <li> <b>Cholesky:</b> You could also compute a Choleksy decomposition $X^\top X = LL^\top$. Then you just need one forward-substitution and one back substitution
  to solve for $\hat\beta$.</li>
  </ol>

  I'm sure there are other approaches, but these are the ones that came to mind for me.

</details>
