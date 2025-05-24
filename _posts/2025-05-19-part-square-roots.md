---
title: Partitioning square roots
categories:
  - quant-question-bank
tags:
  - optimization
---

How would you partition the square roots of the first 50 natural numbers
$\sqrt 1, \sqrt 2, \dots, \sqrt{50}$ into two groups $A, B$, such that

$$\left|\sum_{a \in A} a - \sum_{b \in B} b \right|$$ 

is minimized? Give a bound on your objective value.

<details>
  <summary>Solution</summary>
   

This is an intentionally very open-ended problem, here is just one
potential solution.

One answer is to look at this as differences of adjacent square roots.
That is look at them as $\sqrt 2 - \sqrt 1, \sqrt 4 - \sqrt 3$, and so
on. Then the problem becomes deciding to add or subtract each of these
differences to our running sum. One might think simply switching between
adding and subtracting based on crossing 0 would be a reasonable
approach. How would you bound this though? Well if we cross 0 at step
$i$, then we are at most $\sqrt{i+1} - \sqrt{i}$ away from 0. By
difference of squares identity, we see that
$\sqrt{i+1} - \sqrt{i} = \frac{1}{\sqrt{i+1} + \sqrt{i}} = O(i^{-1/2})$
Adjacent differences are of the same order, so we will cross 0. 
Once we cross 0 once, we will always stay within $O(1/\sqrt{i})$ of 0.
Thus our bound is $O(1/\sqrt{50})$.
</details>