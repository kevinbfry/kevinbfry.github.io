---
title: Checking if a number is $2^n$
categories:
  - quant-question-bank
tags:
  - programming
  - bit manipulation
---

How would you programmatically check if an integer is a power of $2$?

<details markdown="block">
  <summary>Solution</summary>

  There are many possible solutions. The most trivial one is successive 
  halving until you hit a non-integer, or 1.

  {% highlight python %}
  while x != 1:
      x /= 2
      if int(x) != x:
          return False
  return True
  {% endhighlight %}

  A slightly more clever approach is sum the bits of $x$ and stop if it
  exceeds 1.
  
  {% highlight python %}
  n = 0
  while x > 0:
      n += x & 1
      if n == 2:
          return False
      x >>= 1
  return True
  {% endhighlight %}

  But the cleanest approach is to realize that a power of 2 is
  represented in binary by one 1 followed by some number $y$ of 0's, 
  and only a power of two has such a binary representation. Thus 
  a power of 2 minus 1 will have a 0 followed by $y$ 1's. Hence 
  we have the simple check for if $x$ is a power of 2.
  
  {% highlight python %}
  return x & (x-1) == 0
  {% endhighlight %}
</details>
