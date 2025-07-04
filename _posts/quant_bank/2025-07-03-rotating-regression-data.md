---
title: Rotating regression data
categories:
  - quant-question-bank
tags:
  - linear regression
---

We have $X \sim U[-2,2], Y \sim U[-1,1]$. If we apply rotation matrix

$$R = \begin{bmatrix}
        \sqrt 2 / 2 & -\sqrt 2/2 \\ \sqrt 2/2 & \sqrt 2/2
    \end{bmatrix}$$
to the joint matrix $Z = \begin{bmatrix} X & Y \end{bmatrix}$ to get $\tilde Z = RZ$. What is the OLS fit of $\tilde Y \sim \tilde X$? What about the intercept?

<details markdown="block">
  <summary>Solution</summary>
  This is another example where it is very useful to understand the different perspectives on linear regression. In this case, the statistical interpretation is most useful.
  
  We begin with the intercept. It will be 0, as the transformed variables are mean 0. This is because they are a linear combination of the original variables, which are mean 0 by construction.
  
  Then the coefficient becomes easy. In a univariate regression with mean zero random variables $\tilde Y \sim \tilde X$, the coefficient is simply $\mathrm{cov}(\tilde X,\tilde Y) / \mathrm{var}(\tilde X)$. Thus the new regression coefficient is just an exercise in algebra as $\tilde X = \sqrt{2}(X - Y) / 2$ and $\tilde Y = \sqrt{2} (X + Y) / 2$.

</details>
