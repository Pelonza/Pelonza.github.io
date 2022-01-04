---
title: PTASs
layout: content
mathjax: true
date: 2021-11-29
---

$$
\newcommand{\prob}[1]{\mathsf{#1}}
$$

# Problem: Tours, Approximately

A polynomial-time approximation scheme (PTAS) is an approximation algorithm for a minimization problem that produces solutions that are within a factor of $(1 + \epsilon)$ (dually $(1 - \epsilon)$ for maximization problems) of the optimal solution, for some constant parameter $\epsilon$.
In the book, Sipser describes a 2-approximation algorithm for $\prob{VERTEX-COVER}$ which is a PTAS with $\epsilon = 1$.
Several NP-complete problems has PTAS.

Recall that a _Hamiltonian cycle_ is a cycle in a graph that touches every vertex exactly once.
From this, we can discuss the _traveling salesman problem_ (TSP) which requires us to find the shortest Hamiltonian cycle in a weighted undirected graph.
For simplicity's sake, when we talk about TSP, we assume that the graph is complete, _i.e._, every location is reachable from every other location.
It turns out that it is provable that TSP has no PTAS which is not good since TSP occurs in many real-life situations!

In order to gain a tractable approximation for TSP, we need to add in an extra constraint, _the triangle inequality_, which states that for any
triple of vertices $u$,$v$,$w$:

$$
l(u, v) + l(v, w) \geq l(u, w)
$$

Where $l(u, v)$ is the weight of the edge $uv$.
If we add this constraint to TSP, then we can obtain a _2-approximation_ scheme for TSP.

a.  Come up with two small example graphs, one that exhibits the triangle inequality and one that does not.
    Based on your graphs, answer the following question and justify your response in a sentence or two: if we know that the triangle inequality holds of a graph, what do we know about the shortest path between any pair of vertices in the graph?
b.  Review the concept of a _minimum spanning tree_ (MST) for a graph.
    In particular, what is a MST and how can you compute one efficiently?
    Give an example weighted, undirected graph and a MST for that graph.
c.  Now, derive an approximation algorithm for the TSP using the notion of a minimum spanning tree.

    (_Hint_: Think about using the MST of the graph as a starting point for the tour.
    How can the MST be used to visit all the vertices of the graph?
    From this, you can view the problem as "fixing up" this tour so it is indeed Hamiltonian.)
d.  Finally, justify in a paragraph or two the correctness of your algorithm.
    In particular, why is algorithm a 2-approximation scheme.
    That is, why is the result is no larger than two times the optimal tour of the graph.

    (_Hint_: your reasoning should appeal to the triangle inequality in some way!)
