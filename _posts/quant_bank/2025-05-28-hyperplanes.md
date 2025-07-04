---
title: Hyperplanes 
categories:
  - quant-question-bank
tags:
  - linear algebra
  - linear regression
  - principle components analysis
---

You have points in 3D. How to find hyperplane that minimizes z-axis error? How to
find hyperplane that minimizes orthogonal error? When would you prefer one over 
the other?

<details markdown="block"> 
  <summary>Solution</summary>
  
  This may sound weird at first, but these actually map onto very common
  techniques, assuming the error metric we care about is euclidean error. 
  The first question is simply linear regression with the z-axis
  component as the response $Y$ and the x and y coordinates and the features
  $X$. 

  The second question is actually just the first principle component of the 
  data. By definition, the first principle component defines the direction
  along which the data varies the most, that is the residuals after 
  projecting onto this direction has the minimal variance.

  As far as when to use each approach? The first approach is much more 
  natural for solving a machine learning problem, and seems like it 
  should give better predictions. However, consider a situation where
  you know your features (the x and y coordinates), are noisy. Then,
  the principle components approach will be able to account for the 
  noise in your features when making its predictions.

</details>