---
title: Solving SAT Efficiently
layout: content
mathjax: true
---

Recall that when dealing with intractable problems, we must compromise on one of three pillars:

1.  Producing a correct/optimal solution.
2.  Finding a solution in polynomial time.
3.  Operating over arbitrary, unconstrained inputs.

We have seen in our study of approximation that we can compromise on one, or both, of points (1) and (3) to arrive at an _approximation algorithm_ for our problem where we gain tractability at the cost of accepting a bound on the generated solution.

It seems rather pointless to compromise on (2) since intractability is precisely defined to be _not_ having a polynomial time algorithm.
However, if a problem admits an algorithm that has worst-case exponential complexity but those cases are rare or only occur in cases that "don't matter," then we would be likely to use such an algorithm "in practice."

In today's class, we'll look at solving the boolean satisfiability problem, $\mathsf{SAT}$, directly, but with appropriate heuristics so that our brute-force algorithm performs relatively well in practice.
In preparation for our discussion, check out the [2021 SAT Competition](https://satcompetition.github.io/2021) where researchers compete in building the most efficient SAT solvers possible.
You might find it useful to check out the summary descriptions of the various solver, found on the download page of the competition:

+   [2021 SAT Competition Solver Descriptions](https://satcompetition.github.io/2021/downloads/SolverDescriptions.tar.xz)

If you are interested in learning more about SAT solving and its applications to software verification, check out these longer readings:

+   Armin Biere. [Bounded Model Checking](http://fmv.jku.at/papers/Biere-SAT-Handbook-2021-BMC-Chapter-Manuscript.pdf). In _The Handbook of Satisfiability_, Second Edition. 2021.
+   Clark Barrett and Cesare Tinelli. [Satisfiability Modulo Theories](https://homepage.cs.uiowa.edu/~tinelli/papers/BarTin-HBMC-18.pdf). In _The Handbook of Model Checking_. 2018.
