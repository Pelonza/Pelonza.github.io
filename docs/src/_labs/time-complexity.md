---
title: Time Complexity
layout: content
mathjax: true
---

$$
\newcommand{\desc}[1]{\langle #1 \rangle}
$$

# Problem 1: Representation

For each of the following objects, describe a plausible representation for those objects as strings.

1.  An undirected graph $G$.
2.  A finite collection of objects $O_1, \ldots, O_n$, weights for each object $w_i$, and costs for each object $c_i$.
3.  An assignment of truth values to a finite collection of boolean variables $x_1, \ldots, x_k$.
4.  A Turing machine configuration $C$.
5.  A deterministic finite automata $D$.

# Problem 2: Poly Want A Cracker

Show that each of the following languages are in $P$.

+   $\{\, \desc{G, V'} \mid \text{\( G = (V, E) \) is a graph, \( V' \subseteq V \) and no two vertices of \( V' \) are incident with each other} \,\}$.
+   $\{\, \desc{D} \mid \text{\( D \) is a DFA and \( L(D) = \Sigma^* \)} \,\}$.
+   $\{\, \desc{G} \mid \text{\( G \) is a graph and \( G \) contains a triangle (a 3-clique)} \,\}$.
