---
title: First color out
categories:
  - quant-question-bank
tags:
  - combinatorics
---

We have a sack with 60 balls: 30 yellow, 20 red, and 10 white. If we
draw randomly from the sack w/o replacement until all are drawn, what is
the probability white is the first color with all balls removed?

<details markdown="block">
  <summary>Solution</summary>
  

Condition on a color being last ball. This reduces problem to two color
case, where it is just fraction of white balls for the two colors left.
If $W$ is the event of interest, and $R, Y$ are the event red and yellow
are the last ball, respectively, then

$$
\begin{aligned}
\mathrm{Pr}(W) &= \mathrm{Pr}(W \mid Y) \mathrm{Pr}(Y) + \mathrm{Pr}(W \mid R) \mathrm{Pr}(R) \\
&= \frac{2}{3}\frac{1}{2} + \frac{3}{4}\frac{1}{3} = \frac{7}{12}
\end{aligned}
$$
</details>