---
title: Approximation with Linear Programming
layout: content
mathjax: true
date: 2021-12-01
---

In class, we introduced the problem of _0-1 integer programming_.

::: definition
Suppose we have an _objective function_ over $m$ variables $f(x_1, \ldots, x_m) = c_1 x_1 + \cdots + c_m x_m$.
Furthermore, suppose we have _constraints_ on the variables in the form of $n$ equations of the form $a_{i1} x_1 + \cdots + a_{im} x_m \leq b_i$ for $i \in 1, \ldots, n$.
In addition, we require that the variables can only take on the values $0$ or $1$.

Our goal is to choose values for $x_1, \ldots, x_m$ that _maximizes_ $f(x_1, \ldots, x_m)$ while satisfying all of the $n$ constraint equations.
:::

We discussed how the 0-1 integer programming can serve as a reduction point for a variety of problems.
We then discussed how we can reduce a problem, _e.g._, the _set cover_ problem:

::: definition
Let $S_1, \ldots, S_m \subseteq \mathcal{U}$ be subsets drawn from a universe $\mathcal{U}$.
Furthermore, assign to each subset a weight $w_i$ for $i \in 1, \ldots, m$.
Create a sub-collection of these subsets such that:

+   The subsets cover all the elements of $\mathcal{U}$.
    In other words, if $T$ is the collection of subsets, then we want $\bigcup_{S \in T} S = \mathcal{U}$.
+   The sum of the weights of the sub-collection should be minimal.
:::

An approximation algorithm comes from:

1.  Reducing set cover to 0-1 integer programming.
2.  Solving the resulting integer program as a linear program, a process called _linear relaxation_.
3.  Recovering an approximate solution for the integer program from the linear program.

For now, let's focus on the first step of the process.
Give a polynomial time reduction from 0-1 integer programming to set cover.
