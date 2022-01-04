---
title: "NP-Completeness"
layout: content
mathjax: true
---

# Problem 1: Bridging the Gap

Let $A$ be a decidable language and $V$ be a polynomial-time verifier for the language.
Recall that a verifier is an algorithm that checks whether a candidate solution to the problem is indeed an actual solution.
Give a generic non-deterministic Turing machine $N$ that decides $A$ in polynomial time in terms of $V$.

# Problem 2: Membership

Show that each of the following languages are in $\mathsf{NP}$.

+   $A_1 = \{\, \langle P \rangle \mid \text{\( P \) is a satisfiable boolean formula} \,\}$.
+   $A_2 = \{\, \langle S, t \rangle \mid \text{\( S \subseteq \mathbb{Z} \) and there exists \( x_1, \ldots, x_k \in S \) such that \( \sum_{i}^{k} x_i = t \)} \,\}$.
+   $A_3 = \{\, \langle G, V', k \rangle \mid \text{\( G = (V, E) \) is a graph and \( V' \subseteq V \) is a \( k \)-covering of \( G \)} \,\}$.

# Problem 3: Completeness

Define the following languages:

+   $\mathsf{CLIQUE} = \{\, \langle G, k \rangle \mid \text{\( G \) is a graph and \( G \) contains a \( k \)-clique} \,\}$
+   $\mathsf{ISO} = \{\, \langle G, H \rangle \mid \text{\( G \) and \( H \) are graphs and there is a subset \( G' \) of \( G \) is isomorphic to \( H \)} \,\}$.

Show that $\mathsf{CLIQUE} \leq_p \mathsf{ISO}$.

(_Hint_: what is the type of the mapping function $f$ in this case?)
