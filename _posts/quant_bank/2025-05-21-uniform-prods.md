---
title: Product of uniforms 
categories:
  - quant-question-bank
tags:
  - probability
  - calculus
---

If $U_1, U_2 \overset{iid}{\sim} U[0,1]$, compute $Pr(U_1U_2 \le .5)$?

<!-- <details markdown="block">
  <summary>Solution</summary>
   -->

<details markdown="block">
  <summary>Solution</summary>
  
  $$
  \begin{aligned}
      \int_{0}^1\int_{0}^{\min(1,.5/u_1)} du_2 du_1
      &= .5 + \int_{.5}^1\int_{0}^{.5/u_1} du_2 du_1 \\
      &= \int_{.5}^1 .5/u_1 du_1 \\
      &= .5(1 + \ln(2))
  \end{aligned}
  $$
</details>



