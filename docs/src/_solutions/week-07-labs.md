---
title: Week 7 Lab Solutions
layout: content
mathjax: true
---

$$
\newcommand{\PUZZLE}{\mathsf{PUZZLE}}
\newcommand{\NP}{\mathsf{NP}}
\newcommand{\SAT}{\mathsf{3SAT}}
\newcommand{\INDSET}{\mathsf{INDSET}}
\newcommand{\CLIQUE}{\mathsf{CLIQUE}}
\newcommand{\SETPACK}{SETPACK}
$$

# Problem: Card Reductions

To show that $\PUZZLE$ is $\NP$-complete, we show that it is in $\NP$ and hard for $\NP$.

::: proof
**Claim 1**: $\PUZZLE \in \NP$.

_Proof_.
The verifier for $\PUZZLE$ takes a stack of cards as input and a recommended orientation of the cards as a certificate.
The verifier can then pile the cards, orienting them according to the certificate, and verify whether the bottom of the box is visible.
It takes a linear amount of work to orient and pile the cards and a constant amount of work to sight-verify the holes.
:::

::: proof
**Claim 2**: $\PUZZLE$ is $\NP$-hard

_Proof_.
We reduce $\SAT$ to $\PUZZLE$, _i.e._, $\SAT \leq_p \PUZZLE$.
Let $\phi$ be a boolean formula in 3-cnf form.
For each variable, create a card, and for each card, create a row on that card for each clause of $\phi$.
For each row on each card, punch a hole out of the left-hand column if the variable corresponding to the card _does not appear_ in the clause corresponding to the row.
Punch a hole out of the right-hand column if the variable's complement _does not appear_ in the clause.
Finally, include an extra card, the left-hand column is entirely punched out and the right-hand column untouched.

Now we show that this reduction preserves correctness of inputs.
Before we begin, we introduce some terms to simplify the presentation.
Call the left-hand column of each card the _positive column_ and the right-hand column the _negative column_.
Call the orientation of a card _positive_ when the card is untouched, _i.e._, the positive column is on the left and the negative column is on the right.
Call the orientation of a card _negative_ when the card is flipped, _i.e._, the positive column is on the right and the negative column is on the left.

First, we show that if $\phi$ is satisfiable, then the resulting cards have a solution.
Orient the cards so that if variable $x$ is true in the satisfying assignment, then the card is oriented positively.
If $x$ is false in the satisfying assignment, then the card is oriented negatively.
Finally, the extra card is included in the deck as-is.

Now consider each row of the resulting card deck and its corresponding clause in $\phi$.
Since the assignment in question is satisfying, one of the literals of these clause must be true, call it $x$.
Observe that by our construction, the card corresponding to $x$ must not be punched out in this position (the left-hand column of the row).
This is true for each such row since each clause is true and thus the left-hand column is covered.
Finally, by construction of the extra card, the right-hand column is also covered as it has no holes on the right-hand side.

Finally, we show if the card deck has a solution then $\phi$ is satisfiable.
Construct the satisfying assignment for $\phi$ by assigning each variable $x$ of $\phi$ to true if its corresponding card is positively oriented.
Otherwise, assign $x$ to false if its corresponding card is negatively oriented.

To see how the resulting assignment is indeed satisfying for $\phi$, consider each clause of $\phi$ and its corresponding row among the cards.
For the deck to have a solution, some card of the deck must cover the left-hand column of this row.
By construction, this card corresponds to some variable $x$ of this clause.
If the card is oriented positively, then $x$ itself makes the clause true.
If the card is oriented negatively, then $\overline{x}$ makes the clause true.
:::

# Problem: Graph Reductions

::: proof
**Claim 1**: $\INDSET \in \NP$.

_Proof_.
A verifier for $\INDSET$ takes a graph $G$ and target $k$ as input and a subset $V^*$ of the vertices $|V|$ of $G$ as a certificate.
The verifier then checks that $V^*$ has $k$ elements and is indeed an independent set by checking each pair of vertices of $V^*$ and observing that there is no edge between them.
There are $\mathcal{O}(|V|^2)$ such pairs to check, leading to a polynomial runtime overall.
:::


::: proof
**Claim 2**: $\INDSET$ is $\NP$-hard.

_Proof_.
We show that $\INDSET$ is $\NP$-hard by reducing $\CLIQUE$ to $\INDSET$.
Let $G = (V, E)$ be a graph and $k$ a target clique size.
We convert these inputs to $\CLIQUE$ into inputs for $\INDSET$ as follows:

+   Let the graph to $\INDSET$ be $\overline{G}$, the complement of $G$.
    $\overline{G}$ is $G$ but each pair of vertices of $\overline{G}$ has an edge iff the same pair of vertices _does not_ have an edge in $G$.
+   Let the target independent set size be $k$.

Consider any pair of vertices $v_1$ and $v_2$ of the $k$-clique.
Observe that by the nature of graph complement, $v_1$ and $v_2$ are not connected in $\overline{G}$.
Thus, the vertices of the $k$-clique form a $k$-independent in $\overline{G}$.
This relationship between $G$ and its complement is symmetric, therefore, $G$ has a $k$-clique if and only if $\overline{G}$ has a $k$-independent set.
:::

# Problem: More Graph Reductions


::: proof
**Claim**: $\INDSET \leq_p \SETPACK$.

Let $G = (V, E)$ be a graph and $k$ be the size of an independent set of $G$.
Construct the components of $\SETPACK$ as follows:

+   $U = V$
+   For each vertex $v \in V$, include a subset $X_v \in S$:

    $$
    X_v = \{\, (u, v) \mid (u, v) \in E \,\}.
    $$
+   Use the size of the independent set $k$ as the minimum set packing size $S$.

First we show that if $G$ has a $k$-independent set $V^*$, then there is a set packing for $(U, S, k)$, call it $S^*$.
Define $S^*$ as follows:

$$
S^* = \{\, X_v \mid v \in V^* \,\}.
$$

Consider two vertices in the independent set of $V^*$, say $u$ and $v$.
We consequently include $X_u$ and $X_v$ in $S^*$.
Observe that by construction that $X_u$ and $X_v$ are sets of edges drawn from $E$ and have no edges in common.
Because $u$ and $v$ each represent one of the end points of the edges in $X_u$ and $X_v$, the only way for them to have an edge in common is if edge $(u, v) \in E$.
However, this is not the case because $V^*$ is an independent set.
Therefore, every pair of sets in $S^*$ is pairwise disjoint and thus $S^*$ is a set packing of size $k$.

Now consider a $\SETPACK$ instance $(U, S, k)$ produced by our reduction and a set packing $S^*$ and $|S^*| \geq k$.
Each of the subsets $X_v$ of $S$ correspond to a vertex in $G$.
Observe that the set of these vertices form a $k$-independent set because they do not have a mutual edge in common.
If they did, then their corresponding sets in the $\SETPACK$ instance would not be disjoint.
:::
