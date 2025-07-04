---
title: 2 player game 
categories:
  - quant-question-bank
tags:
  - mental math
---

Suppose two players play a game alternating turns. Player 1 goes first
and has 50% chance of winning in that round. Player 2 goes second (if P1
doesn't win) and has 33% chance of winning. They keep alternating in
this way until one player wins. What is the probability that P1 wins?

<details>
  <summary>Solution</summary>
  

    This is a very standard question, and so we can use a standard tool: setting up and solving the recursive
    equation.

    $$
    \begin{gather*}
    \mathrm{Pr}(\text{P1 wins}) = p_1 + (1-p_1)(1-p_2)\mathrm{Pr}(\text{P1 wins})
    \end{gather*}
    $$

    which gives the answer $p_1/(p_1+p_2-p_1p_2)$, in this case $3/4$.

    Another variation is that there are not alternating turns. Instead, for each turn 
    of the game, Player 1 has probability $p_1$ of winning, Player 2 has probability 
    $p_2$ pf winning, otherwise they play another turn.
</details>
