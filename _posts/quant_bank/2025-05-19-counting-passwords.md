---
title: Counting passwords
categories:
  - quant-question-bank
tags:
## TODO: everything???
  - combinatorics
---

If I have an 8 digit passcode, taking values $0-9$, what is the
probability that a randomly generated passcode has exactly $5$
occurrences of the same digit? What is the probability of having exactly
one digit occur $4$ times in a passcode?

<details markdown="block">
  <summary>Solution</summary>
  

We have 10 digits to choose from, and 8 choose 5 choices of places. The
remaining three digits can take any of the 9 remaining values, so
there's $9^3$ possibilities there. Divide it all by $9^8$. That is

$$\frac{10\binom{8}{5}9^3}{9^8}$$

For exactly 4 its a bit trickier, as we have some double counting. So
its 

$$\frac{10\binom{8}{4}9^4}{9^8} - \frac{10\binom{8}{4}9}{9^8}$$
</details>