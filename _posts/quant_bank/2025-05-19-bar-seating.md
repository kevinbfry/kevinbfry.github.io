---
title: Seating bar patrons
categories:
  - quant-question-bank
tags:
---

Suppose you run a bar that has 25 seats at the bar. Patrons will enter
and seat themselves according to the following rules. They will not sit
next to someone, and they will choose the seat that maximizes the
distance between them and other patrons. You can only choose where the
first patron sits. How should you seat the first patron to maximize the
number of patrons that can sit?

<details markdown="block">
  <summary>Solution</summary>
  

One might initially think sitting the patron in the middle seat, 13,
would work. But working through the problem you see that patrons would
sit at 13, 1, 25, 7, 19. The 6th patron would then have to sit at one of
4, 10, 16, 22. This would leave 2 seats between patrons, which is
suboptimal. Thus we instead want to pick the first seat such that all
bisections will be odd. By trial and error one can figure out that 9 and
(by symmetry) 17 are the correct solutions.

There is a more general question about how you should seat the first
patron if you have $2k + 1$ seats, but I have no idea how to do that
one.
</details>