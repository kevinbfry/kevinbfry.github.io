---
title: Streaming mean and variance 
categories:
  - quant-question-bank
tags:
  - algorithms
---


How to update mean and variance in a streaming way? By streaming 
we mean without retaining the individual samples, i.e. computing
$\bar x_n$ from only $\bar x_{n-1}$ and $x_n$. 

<details markdown="block">
  <summary>Solution</summary>
  
  This is the well-known Welford algorithm:

  $$
  \begin{gathered}
  \bar x_n = \bar x_{n-1} + \frac{x_n - \bar x_{n-1}}{n} \\
  \sum_{i=1}^n (x_i - \bar x_n)^2 = \sum_{i=1}^{n-1} (x_i - \bar x_{n-1})^2 + (x_n - \bar x_{n-1})(x_n - \bar x_n)
  \end{gathered}
  $$

  You can easily verify these formulas for yourself with some easy but tedious algebra.

</details>
