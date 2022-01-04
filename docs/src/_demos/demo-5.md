---
title: "Demonstration Exercise #5"
layout: content
mathjax: true
---

# Problem 1: Membership

Consider the following problems and prove that they are in NP.
Be explicit about (a) the type of witnesses of the problem and (b) the verification algorithm for witnesses.
Argue that the verification algorithm operates in polynomial time.

1.  $\mathsf{COLOR} = \{\, \langle G, k \rangle \mid \text{There is a \( k \)-coloring of graph \( G \)} \,\}$.
2.  $\mathsf{SCHED} = \{\, \langle J, (\prec), W, k, t \rangle \mid \text{There is a schedule of \( J \) jobs on \( k \) processors taking time \( t \) or less} \,\}$.

**Graph Coloring**

A $k$-graph coloring of a graph $G$ is an assignment of $k$ colors to nodes such that no two nodes share both the same color and an edge.

**Job Scheduling**

Consider a set of $J$ jobs equipped with:

1.  A partial order $\prec$ on $J$ that determines that for each $J_m, J_n \in J$ whether $J_m \prec J_n$ (understood to mean that $J_m$ must be completed before $J_n$)
2.  Weight determined by the function $W : J \rightarrow \mathbb{N}$ that says how long each job takes to complete.

There exists $k$ distinct processors on which to run jobs.
The goal is to find a scheduling of jobs on these processors that respects the ordering such that all jobs complete in target time $t$ or less.

# Problem 2: The Complexity Strikes Again

Consider the following combinatorial decision problems:

**0-1 Knapsack**

Let $B$ be a set of objects equipped with two functions:

+   A _weight function_ $w : B \rightarrow \mathbb{N}$ assigning weights to objects.
+   A _value function_ $v : B \rightarrow \mathbb{N}$ assigning values to objects.

Suppose that we have a knapsack that can hold at most $W$ weight.
Find a subset $B^* \subseteq B$ that can fit in the knapsack and has at least value $V$.

**Subset Sum**

Let $S \subseteq \mathbb{N}$ be a (multi-)set of natural numbers.
Find a subset $S^* \subseteq S$ such that $\sum_{s \in S^*} s = t$ for some target number $t$.

1.  Write down formal language definitions for these two problems: $\mathsf{knapsack}$ and $\mathsf{subsetsum}$.

2.  Assume that $\mathsf{subsetsum}$ is $\mathsf{NP}$-complete.
    Prove that $\mathsf{knapsack}$ is $\mathsf{NP}$-complete.
    Make sure that you explicitly justify the complexity of your verifier and the complexity and correctness of your constructed mapping function in your proof.
