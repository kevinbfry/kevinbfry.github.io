---
title: Gold and silver coins
categories:
  - quant-question-bank
tags:
  - probability
  - maximum likelihood
---

Suppose we play a game where we flip a gold coin 500 times and a silver
coin 500 times. We get 3 dollars per gold head, and 1 dollar per silver head,
getting nothing for tails. Suppose we play the game once and earn 900 dollars.
What is the most likely value of $M$, the number of gold heads, to get
900 dollars?

<details markdown="block">
  <summary>Solution</summary>
   

We can start with assuming we get 225 gold coins and 225 silver coins. 
It seems reasonable to assume that 

$$|p(x) - p(x-1)| < |p(y)-p(y-3)|$$ 

for values of $x,y$ moderately close to 250 where $p$ is the pmf 
of a $\mathrm{Binom}(500,.5)$ r.v. This means we can increase the likelihood 
by moving to 224 gold coins and 228 silver coins. We can continue taking steps 
in this way until we reach 217 gold coins and 249 silver coins. Moving to 216 gold coins
now lowers the pmfs of both binomials. Thus this approximation suggests the 
optimal number is 217 gold coins.

How good is this heuristic? Very good, it turns out. In this case it turns out that 217
gold coins is the MLE.

```python
from scipy.stats import binom

rv = binom(500,.5)
N = 900

def biv_binom(x):
    return rv.pmf(x) + rv.pmf(N-3*x)

biv_binom(218), biv_binom(217), biv_binom(216)
```




    (0.03404944566045723, 0.03597830938502978, 0.03544790237947028)
</details>