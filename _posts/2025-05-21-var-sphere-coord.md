---
title: Uniform on unit sphere 
categories:
  - quant-question-bank
tags:
  - probability
  - mental math
---

If we draw uniformly form the unit sphere, and call its coordinates
$(X,Y,Z)$, what is the variance of $X$?

<details>
  <summary>Solution</summary>
  

  This seems hard to calculate explicitly, but looking at the symmetry of the
  problem yields an easy answer. We know that by construction every coordinate
  is mean 0 and that

  $$
  X^2 + Y^2 + Z^2 = 1
  $$

  and by symmetry $\mathrm{Var}(X) = \mathrm{Var}(Y) = \mathrm{Var}(Z)$. Therefore,
  we must have $\mathrm{Var}(X) = 1/3$.
</details>