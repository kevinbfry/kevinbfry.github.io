---
title: Find next in binary search tree
categories:
  - quant-question-bank
tags:
  - data structures
---

For a binary search tree (BST), if you are at node $A$, how would you 
find the lexicographically next node after $A$? That is, how would you
find the smallest value that is larger than the value at node $A$?

<details>
  <summary>Solution</summary>
  This is one of those basic questions you get when they just want to 
  quickly assess if you have some familiarity with a topic. By definition
  of a BST, each node is smaller than all nodes to the right of it, and 
  larger than all nodes to the left of it. Thus the smallest value larger
  than node $A$ is found by traversing right once, and then left until we
  hit a node without a left child.
</details>
