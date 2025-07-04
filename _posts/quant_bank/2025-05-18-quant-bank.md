---
title: Quant Question Bank
categories:
  - quant-question-bank
tags:
## TODO: everything???
---

<!-- TODO: Split by topic? -->

# Counting numeric passwords

If I have an 8 digit passcode, taking values $$0-9$$, what is the
probability that a randomly generated passcode has exactly $$5$$
occurrences of the same digit? What is the probability of having exactly
one digit occur $$4$$ times in a passcode?

<details>
  <summary>Solution</summary>
  

We have 10 digits to choose from, and 8 choose 5 choices of places. The
remaining three digits can take any of the 9 remaining values, so
there's $$9^3$$ possibilities there. Divide it all by $$9^8$$. That is

$$\frac{10\binom{8}{5}9^3}{9^8}$$

For exactly 4 its a bit trickier, as we have some double counting. So
its 

$$\frac{10\binom{8}{4}9^4}{9^8} - \frac{10\binom{8}{4}9}{9^8}$$

# Seating bar patrons

Suppose you run a bar that has 25 seats at the bar. Patrons will enter
and seat themselves according to the following rules. They will not sit
next to someone, and they will choose the seat that maximizes the
distance between them and other patrons. You can only choose where the
first patron sits. How should you seat the first patron to maximize the
number of patrons that can sit?

<details>
  <summary>Solution</summary>
  

One might initially think sitting the patron in the middle seat, 13,
would work. But working through the problem you see that patrons would
sit at 13, 1, 25, 7, 19. The 6th patron would then have to sit at one of
4, 10, 16, 22. This would leave 2 seats between patrons, which is
suboptimal. Thus we instead want to pick the first seat such that all
bisections will be odd. By trial and error one can figure out that 9 and
(by symmetry) 17 are the correct solutions.

There is a more general question about how you should seat the first
patron if you have $$2k + 1$$ seats, but I have no idea how to do that
one.

# First color out

We have a sack with 60 balls: 30 yellow, 20 red, and 10 white. If we
draw randomly from the sack w/o replacement until all are drawn, what is
the probability white is the first color with all balls removed?

<details>
  <summary>Solution</summary>
  

Condition on a color being last ball. This reduces problem to two color
case, where it is just fraction of white balls for the two colors left.
If $$W$$ is the event of interest, and $$R, Y$$ are the event red and yellow
are the last ball, respectively, then

$$\mathrm{Pr}(W) = \mathrm{Pr}(W \mid Y) \mathrm{Pr}(Y) + \mathrm{Pr}(W \mid R) \mathrm{Pr}(R) = \frac{2}{3}\frac{1}{2} + \frac{3}{4}\frac{1}{3} = \frac{7}{12}$$

# Partitioning square roots

How would you partition the square roots of the first 50 natural numbers
$$\sqrt 1, \sqrt 2, \dots, \sqrt{50}$$ into two groups $$A, B$$, such that

$$\left|\sum_{a \in A} a - \sum_{b \in B} b \right|$$ 

is minimized? Give a bound on your objective value.

<details>
  <summary>Solution</summary>
   

This is an intentionally very open-ended problem, here is just one
potential solution.

One answer is to look at this as differences of adjacent square roots.
That is look at them as $$\sqrt 2 - \sqrt 1, \sqrt 4 - \sqrt 3$$, and so
on. Then the problem becomes deciding to add or subtract each of these
differences to our running sum. One might think simply switching between
adding and subtracting based on crossing 0 would be a reasonable
approach. How would you bound this though? Well if we cross 0 at step
$$i$$, then we are at most $$\sqrt{i+1} - \sqrt{i}$$ away from 0. By
difference of squares identity, we see that
$$\sqrt{i+1} - \sqrt{i} = \frac{1}{\sqrt{i+1} + \sqrt{i}} = O(i^{-1/2})$$
Adjacent differences are of the same order, so we will cross 0.

Once we cross 0 once, we will always stay within $$O(1/\sqrt{i})$$ of 0.
Thus our bound is $$O(1/\sqrt{50})$$.

# Pizza 

I like to eat pizza on weekends. $$\mathrm{Pr}(\text{eat pizza Sat}) = .3$$ and
$$\mathrm{Pr}(\text{eat pizza Sun}) = .4$$. Probability will eat pizza on a given
weekend? (bounds, explaining bounds).

# Gold and silver coins

Suppose we play a game where we flip a gold coin 500 times and a silver
coin 500 times. We get \$3 per gold head, and \$1 per silver head,
getting nothing for tails. Suppose we play the game once and earn \$900.
What is the most likely value of $$M$$, the number of gold heads, to get
\$900?

<details>
  <summary>Solution</summary>
   

Computation shows answer is 220 gold coins. But how to get at this
without a computer?

# Ordering uniforms 

Suppose you are going to be shown three iid uniform rv,
$$U_i \sim U[0,1]$$. Your task is to after seeing $$U_1$$, assign it lowest,
middle, or highest. Then see $$U_2$$ and assign it the remaining two of
lowest, middle, or highest. Then by default $$U_3$$ is assigned the
remaining label. What should your strategy be to maximize the
probability of labeling all 3 correctly?

<details>
  <summary>Solution</summary>
   

If we pick lowest for $$U_1=u$$, our probability of winning is the
probability of guessing the relative order of the last two correctly
times the probability of the last two being larger than $$u_1$$. That is

$$\mathrm{Pr}(\text{lowest first} \mid U_1=u) = (1-u)^2 \mathrm{Pr}(\text{win 2 unif game})$$

The probability of winning the two uniform game is $$3/4$$, this can be
intuitively seen by noting you can only be incorrect when they land on
the same half, and in that case you are only wrong half the time by
exchangeability.

If we instead pick middle for $$U_1=u$$ our probability of winning is
$$2u(1-u)$$. Therefore the point where the payoffs equal is $$u=7/11$$.


# Two 6-sided die 

Let $$X,Y$$ be the outcomes of rolling two iid six-sided dies. Compute
$$\mathrm{Pr}(X+Y < XY)$$.

# OLS coefficient bounds

If $$Y \sim X$$ gives $$\beta = 3$$, what is the bound on the coefficient
from $$X \sim Y$$?

# Uniform on unit sphere 

If we draw uniformly form the unit sphere, and call its coordinates
$$(X,Y,Z)$$, what is the variance of $$X$$?

# Random walk hitting time 

If $$X_0=0$$, and goes up or down one at each time step with equal
probability, what is the probability $$X$$ hits $$4$$ before $$X$$ hits $$-6$$?

# Sine integral 

Compute $$\int_\pi^{2\pi} sin x dx$$.

# Product of uniforms 

If $$U_1, U_2 \overset{iid}{\sim} U[0,1]$$, compute $$Pr(U_1U_2 \le .5)$$?

# 2 player game 

Suppose two players play a game alternating turns. Player 1 goes first
and has 50% chance of winning in that round. Player 2 goes second (if P1
doesn't win) and has 33% chance of winning. They keep alternating in
this way until one player wins. What is the probability that P1 wins?

# Prob Gaussians exceed eachother 

Probability $$X > 3Y$$ when they are iid Gaussians.

# Drawing primes 

If I draw 4 numbers without replacement from the first 16 primes, what
is the probability the sum is even?

# OLS when $$X$$ is too large. 

What is OLS solution? How is it derived? How to compute with $$n \gg p$$,
such that $$X$$ cannot be loaded in memory. Was looking for when $$p$$ very
small, but should also think about when $$p$$ is also big.

# Bounding product of coefficients 

If $$\hat\beta = Y \sim X$$ and $$\hat\theta = X \sim Y$$, bound

$$\hat\beta \cdot \hat\theta$$.

# CV 

Some random intro, obviously pointing you to use CV. Then asks about
tradeoff in number of folds $$k$$. If you use fewer folds, the fitted
functions become more independent, and thus each fold's error estimate
will be more independent. On the other hand, with more folds you have
more correlation between folds, but you also average over more points.
Unclear which one wins out.

I'll also write out some facts about CV here

-   In general, for lots of folds, you will get small bias but high
    variance because averaging doesn't do much with such correlated
    folds. With smaller folds, you get lower variance since they are
    more independent, but you may have more bias depending on model and
    sample size $$n$$.

-   **LOOCV** is fast for OLS (and other similar smoothers). Can simply
    fit full model and do $$\sum_i r_i^2 / (1-h_ii)^2$$. Proof by
    Woodbury, so should work for any smoother where adding/removing a
    sample is just a rank one update to the smoothing matrix.

-   **GCV** approximates LOOCV update for linear methods
    ($$n^{-1} \sum r_i^2/(1-S_{ii})^2$$) with denominator $$1 - \mathrm{tr}(S)/n$$.

# Bootstrapping 

How to bootstrap prediction error? LOOB bootstrap error; like LOOCV but
average over all bootstraps not containing $$i$$. How to bootstrap
standard errors

-   Usual method. Assume
    $$B^{-1} \sum \|\hat\theta^{(b)} - \bar\theta^{(B)}\|_2^2 \approx SE(\hat\theta)$$

-   For CI's standard way is assuming
    $$\hat\theta - \theta \overset{d}{\approx} \hat\theta^{(b)} - \hat\theta$$
    and go from bootstrap quantiles
    $$\mathrm{Pr}(q_{\alpha/2} < \hat\theta^{(b)} < q_{1-\alpha}/2) \approx \mathrm{Pr}(2\hat\theta - q_{1-\alpha/2} < \theta < 2\hat\theta - q_{\alpha/2})$$

-   Could also mention studentized bootstrap CI. Instead of using
    bootstrap quantiles directly, nested bootstrap. For each bootstrap
    sample, bootstrap again and estimate standard error on that $$s^b$$.
    Then compute quantiles of studentized statistic
    $$(\theta^b - \hat\theta)/s^b$$. Then
    $$\mathrm{Pr}(q_{\alpha/2} < (\theta^b - \hat\theta)/s^b < q_{1-\alpha/2}) \approx \mathrm{Pr}(\hat\theta - s^b q_{1-\alpha/2} < \theta < \hat\theta - s^b q_{\alpha/2})$$

# Checking if a number is $$2^n$$ 

<details>
  <summary>Solution</summary>
  
`x & (x-1) == 0`

# Hyperplanes 

You have points in 3D. How to find hyperplane that minimizes z-axis error? How to
find hyperplane that minimizes orthogonal error?

# Streaming mean and variance 

How to update mean and variance in streaming way? Welford algorithm:
$$\bar x_n = \bar x_{n-1} + \frac{x_n - \bar x_{n-1}}{n}$$
$$\sum_{i=1}^n (x_i - \bar x_n)^2 = \sum_{i=1}^{n-1} (x_i - \bar x_{n-1})^2 + (x_n - \bar x_{n-1})(x_n - \bar x_n)$$

# PCA/How to find top eigenvector 

Power method, Arnoldi iteration.

# How to regularize neural network? 

Dropout, data augmentation, implicit in SGD, early stopping.

# Find next in BST 

Go right, then go left until you can't.

# Rolling dice mod 6 

Probability the sum of 6 dice rolls is a multiple of 6?

# Group all anagrams 

Given text file of words, write code that outputs a file that has
grouped the words by anagram, outputting all words that are anagrams of
eachother on the same line.

# Details of k-means algorithm

Have unlabeled $$d$$-dimensional data, know there are $$k$$ groups. How find
groups? Should answer $$k$$-means. Explain how the algorithm works. Prove
that the algorithm converges. What would you do about ties? How would
you pick $$k$$?

<details>
  <summary>Solution</summary>
   

Two alternating steps:

-   Assign centers: Random for intialization. In later iterations, take
    mean of points in group.

-   Assign groups: Assign points to group based on closest center

This converges because assigning centers is a convex problem, so always
descend on this step. When assigning groups, we also descend with each
steps. And note that there are a finite number of group assignments
$$k^n$$, so we must terminate.

For ties, we can simply break them by some deterministic rule: stay in
same cluster if cluster is in running, else randomly assign.

# Bounding $$R^2$$ 

We have $$X_1, X_2, Y$$, where $$Y \sim X_1$$ has $$R^2=.1$$ and $$Y \sim X_2$$
has $$R^2=.2$$. Bound the $$R^2$$ of $$Y \sim X_1 + X_2$$.

# OLS on desert island 

Without any package imports, how compute OLS?

<details>
  <summary>Solution</summary>
   

NEW and better solution: Do QR decomposition! Only need to do
transposes, dot products, and back substitution (solve triangular system
of equations).

Tricky to compute inverse without importing packages. So just do
gradient descent. Do line search with backtracking. Armijo rule
(requires sufficient descent as well as sufficient decrease in slope).
Or better yet, Quasi-Newton with line search. Interviewer suggested
taking diagonal and inverting. I think this would be bad, because
approximation $$D$$ does not necessarily majorize true hessian $$H$$.
Therefore no guarantee of convergence.

# Rotating data 

We have $$X \sim U[-2,2], Y \sim U[-1,1]$$. If we apply rotation matrix
$$R = \begin{bmatrix}
        \sqrt 2 / 2 & -\sqrt 2/2 \\ \sqrt 2/2 & \sqrt 2/2
    \end{bmatrix}$$, how does OLS fit change? Intercept?

<details>
  <summary>Solution</summary>
   

Use covariance/variance definition and plug and chug.

# Voleon: Pseudoinverse

Solving underdetermined system.

# Betting on a tournament bracket 

Have a tournament bracket. Each team has ratings $$r_t$$, and the prob of
team 1 beating team 2 is $$r_1 / (r_1 + r_2)$$. Also given prices to
buy/sell a team. Come up with strategy to maximize performance, one
round at a time.

# Betting on coin flips 

You and $$n$$ others each can bet an amount on a coin being heads or tails
(up to your total cashpile). If incorrect, lose $$X$$. If correct, you
split total pot with all other winners. Come up with a strategy to
maximize performance.

# IP: Find Median 

Given $$X_1,\dots,X_n$$ find the median. First in O(nlogn), then in O(n).

# IP: Max \# drawdown days 

Given a vector of return $$\{R_t\}$$, if the mean is $$\mu=8$$ and the
standard deviation is $$\sigma=3$$, can you bound the maximum number of
drawdown days?

# NM: Linear algebra and mean operator 

We have a matrix $$A \in \mathbb{R}^{m \times n}$$ and vector $$X \in \mathbb{R}^n$$.
Suppose that $$m^{-1}\mathbf{1}^\top A X = Avg(X) = n^{-1} \mathbf{1}^\top X$$. What does
that tell us about $$A$$? Further, can you show that
$$|Avg(AX)| \le |Avg(X)|$$?

# JY: Eigenvalues and transposes 

If $$A \in \mathbb{R}^{n \times n}$$, does it necessarily have the same
eigenvalues as $$A^T$$? Now suppose $$B = .5 (A + A^T)$$. Can you say
anything about the eigenvalues of $$B$$ and $$A$$?


# What do different firms look for?

## Jane Street

Jane Street likes expected value, optimal strategy/tradeoff type
questions. They care to see how you think, often by starting with crude
bounds and then refining, or basic strategies then iteratively
improving. Also like thinking about edge cases then smoothly
interpolating between them.

## 5 Rings

5 Rings is known for asking questions with a timed response: they'll give you 10 seconds for some questions, 30 seconds for others. You have to think fast on your feet, and maybe even make good guesses using intuition and heuristics.

## Voleon

They like to ask about lots of machine learning models, so let's talk about a few common ones here:

-   OLS: In particular, the hat matrix $$H$$. Big $$H_ii$$ (close to 1)
    means leverage point. $$\hat y= Hy, r= (I-H)y$$, and
    $$\mathrm{Cov}(\hat y) = H\sigma^2, \mathrm{Cov}(r) = (I-H)\sigma^2$$. Leverage
    doesn't necessarily mean big residual
    $$r_{i} = y_i - \hat y_{i} = (1-H_ii) (y_i - \hat y_{-i})$$.

-   **Trees:** You fit a tree by making binary decision rules on a given
    feature. Usually done in greedy fashion. Trees are pruned based on
    cost complexity in regression ($$SSE(T) + \alpha |T|$$) and
    cross-entropy/gini/misclass. rate for classification
    ($$Err(T) + \alpha|T|$$). In classification, usually cross-entropy for
    growing, misclass. for pruning. Handle missing values well using
    surrogate splits. $$O(p n\log n)$$ complexity.

-   **RF:** Grow many trees, each on a different bootstrap sample. At
    each split, choose from only subset of features $$\sqrt{p}$$. Average
    trees to get final model.

-   **Boosting:** Fit weak learners to combine into a strong learner.
    Essentially increase weights of mistakes, decrease weights for
    others.

-   **Gradient boosting:** Fit trees on gradients to learn regions. Then
    fit each region based on original loss function.

-   **SVM:** Finding maximum margin classifier, allowing for some points
    to fall inside margin. SVC is usually inner product on original
    feature space. Because it only relies on inner products of $$x,x'$$,
    can use kernel trick to do same thing on higher-dimensional spaces.
    This makes it an SVM.

They also put you through a data analysis interview, where you have to work through a data problem in real-time with your interviewer.
