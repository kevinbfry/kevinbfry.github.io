---
title: Finding colinear subset
categories: 
  - quant-question-posts
tags: 
  - linear algebra
  - PCA
---

This note explores the following quant interview question: if you are given a matrix $X \in \mathbb{R}^{n\times p}$ that you are told has colinearity, how would you find which subset of columns of $X$ are the cause of the colinearity?

The simple part of othe problem is noting that colinearity means that there exists non-zero vectors $\gamma$ such that $X\gamma = 0$. Writing the SVD of $X$ as $X=UDV^\top$, where $U\in\mathbb{R}^{n\times p}$ orthogonal, $D \in \mathbb{R}^{p\times p}$ diagonal, and $V \in \mathbb{R}^{p\times p}$ orthogonal. Since we know there is colinearity, there is some $r < p$ such that $D_{jj} = 0$ for all $j=r+1,\dots, p$. Putting this together, we see that all such vectors $\gamma$ are such that

\\[\gamma \in \mathcal V_r = \mathrm{span}(V_{r+1},\dots,V_p)\\]

So now the question has become, how do we find sparse directions in $\mathcal V_r$? And if we find more than one, how do we decide which is indicating the true colinear subset(s)? I do not know how to answer this comprehensively, but here are some sensible things to try. The obvious place to start is with the basis vectors $V_j$. If these are sparse, then the non-zero elements may be a good candidate subset of colinear columns. However, what if our vector $\gamma$ has a few very large values, then some small values, and then maybe some values that are 0. We would like to be able to say that we can attribute most of the colinearity to the columns with large $\gamma_i$ values. This however is only true if our columns are already on the same scale. To see this, consider if half the columns are measured in units of miles, while the other half are measured in units of inches. Thus we would naturally expect the $\gamma$ values for the mile columns to be much larger than the inch columns. So, we should normalize our columns before performing this analysis if we want to have some justification for assigning more dependence to columns with larger $\gamma$ values.

Another idea would be to try and find a basis of sparse vectors of $\mathcal V_r$, perhaps using the [sparse PCA method](https://hastie.su.domains/Papers/spc_jcgs.pdf) of Zou, Hastie, and Tibshirani. 

Often we do not have perfect colinearity, instead only approximate colinearity. So instead of looking at the space corresponding to the 0 eigenvalues, we instead look at the space corresponding to almost 0 eigenvalues.

**Note:** Eventually, I plan to revisit this post to expand on this and to add empirical results comparing the effectiveness of different approaches.