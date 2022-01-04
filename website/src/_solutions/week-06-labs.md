---
title: Week 6 Lab Solutions
layout: content
mathjax: true
---

$$
\newcommand{\SAT}{\mathsf{SAT}}
\newcommand{\CLIQUE}{\mathsf{CLIQUE}}
\newcommand{\ISO}{\mathsf{ISO}}
$$

# Problem: Representation

1.  A list of vertices and a list of edges, each of which is a pair of vertices from the first list.
2.  A list of pairs of weights and costs for each of the objects.
3.  A list of pairs of variables and truth values.
4.  A string consisting of tape symbols with a single state that represents both the current state and the current position of the tape.
5.  A tuple consisting of a list of states, the start state, the set of final states, and triples of a state, character, and state denoting the transition function.

# Problem: Poly Want A Cracker

+   For each vertex $v$ of $V'$, check every other vertex $v'$ of $V'$ and verify that $(v, v')$ is not an edge of $E$, $\mathcal{O}(|V|^2)$ time overall.
+   Use depth-first search to determine the set of states reachable from the start state and ensure that every such state is an accepting state, $\mathcal{O}(|Q|)$ time overall.
+   Enumerate every possible triple of distinct vertices and see if they form a 3-clique, $\mathcal{O}(|V|^3)$ such triples overall.

# Problem: Bridging the Gap

Let $A$ be a decidable language and $V$ be a polynomial-time verifier for $A$ that runs in some polynomial time $f(n)$.
Non-deterministic Turing machine $N$ does the following to decide $A$ on input $w$:

1.  Non-deterministically generate a certificate $c$ of size $f(|w|)$.
2.  Run $V(w, c)$ and accept if $V$ accepts.
3.  If no such $c$ leads to acceptance, then reject.

The non-deterministic search is bounded by the size of potential certificates, observing that an algorithm that runs in time $f(n)$ cannot access memory larger than size $f(n)$.

# Problem: Membership

1.  Let the certificate to the verifier for $A_1$ be an assignment of truth values to the literals of the boolean formula.
    Checking that formula is satisfiable given the assignment amounts to running the formula which takes a linear amount of time.
2.  Let the certificate to the verifier for $A_2$ be a set $S^* \subseteq S$.
    Checking that the sum of the elements of $S^*$ is $t$ takes a linear amount of time.
3.  Let the certificate to $A_3$ be a subset $V' \subseteq V$.
    Checking that $V'$ is a covering amounts to checking every edge and verifying that at least one of its vertices is in $V'$.
    This process is linear in the number of edges of $G$.

# Problem: Completeness

::: proof
**Claim**: $\CLIQUE \leq_p \ISO$.

Let $(G, k)$ be an instance of $\CLIQUE$.
From this instance, constructing $(G, K_k)$, an instance of $\ISO$ where $K_k$ is the complete graph on $k$ vertices.

First we show that if $G$ has a $k$-clique, then a subset of $G$ is isomorphic to $K_k$.
Observe that the $k$-clique of $G$ is, itself, a complete graph of size $k$.
Therefore, this $k$-clique is the subset of $G$ that is isomorphic to $K_k$.

Next we show that if a subset of $G$ is isomorphic to $K_k$, then $G$ has a $k$-clique.
Observe that $K_k$ itself is a $k$-clique embedded in $G$, so we are done.
:::

# Problem: Details, Details, ...

1.  The inputs to the mapping function is a Turing machine $M$ and an input $w$.
    The output is a boolean formula $\phi$.
2.  The tableaus have $n^k$ rows because it is assumed that $M$ runs in some polynomial amount of time $n^k$.
    Each row is a step of the computation.
3.  We can bound the size of the tape to a polynomial because a Turing machine cannot access more memory than steps of time it takes to run.
4.  $x_{i, j, s}$ is true if and only if cell $(i, j)$ of the tableau is filled with symbol $s$.
5.  Each of the boolean formulae of Cook-Levine:
    +   $\phi_\mathsf{cell}$: checks that every cell of the tableau has exactly one symbol enabled.
    +   $\phi_\mathsf{start}$: checks that the first row corresponds to the initial configuration of $M$ on $w$.
    +   $\phi_\mathsf{move}$: checks every $2 \times 3$ window of the tableau correctly encodes a potential step of execution of $M$.
    +   $\phi_\mathsf{accept}$: checks that some row of the tableau ends on $\q_\mathsf{accept}$.
6.  The constructed boolean function accounts for non-determinism by emitting sub-formulae in $\phi_\mathsf{move}$ to account for every possible step of non-determinism.
    The assumed solver for $\SAT$ is then responsible for determine which of non-deterministic paths would result in acceptance, if any of them do.
