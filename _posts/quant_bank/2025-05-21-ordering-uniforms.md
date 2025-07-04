---
title: Ordering uniforms
categories:
  - quant-question-bank
tags:
  - probability
  - maximum likelihood
---

Suppose you are going to be shown three iid uniform rv,
$U_i \sim U[0,1]$. Your task is to after seeing $U_1$, assign it lowest,
middle, or highest. Then see $U_2$ and assign it the remaining two of
lowest, middle, or highest. Then by default $U_3$ is assigned the
remaining label. What should your strategy be to maximize the
probability of labeling all 3 correctly?

<details markdown="block">
  <summary>Solution</summary>
   

Let $L_1$ be the event $U_1$ is the lowest, and $W_i$ be the event
we win the game of guessing the relative order of $i$ uniforms.s
If we pick lowest for $U_1=u$, our probability of winning is the
probability of guessing the relative order of the last two correctly
times the probability of the last two being larger than $u$. That is

$$\mathrm{Pr}(L_1 \cap W_3 \mid U_1=u) = (1-u)^2 \mathrm{Pr}(W_2)$$
<!-- $$\mathrm{Pr}(L_1 \cap W  \mid U_1=u) = (1-u)^2 \mathrm{Pr}(\text{win 2 unif game})$$ -->

The probability of winning the two uniform game is $3/4$. This can be
intuitively seen by noting you can only be incorrect when they land on
the same half, and in that case you are only wrong half the time by
exchangeability.

If we instead pick middle for $U_1=u$ our probability of winning is
$2u(1-u)$. Thus we need to find where these two are equal to decide our cutoff.

$2u(1-u) = 3(1-u)^2/4$

Solving this yields $u=3/11$. Therefore we should pick lowest for 
$u_1 < 3/11$, highest for $u_1 > 8/11$, and middle otherwise.
</details>
