---
title: Week 8 Lab Solutions
layout: content
mathjax: true
---


# Problem: Developing the Strategy

Because we don't care about time complexity, we are free to explore the exponential search space of $\mathsf{SAT}$ directly provided that we can track our current position using a polynomial amount of space.
We can do this because we just need to track the boolean assignments of a linear number of variables.

# Problem: Space!

$\mathsf{CLIQUE}$ is in $\mathsf{PSPACE}$ because we can exhaustively search all $k$-sized sub-graphs of $G$ and determine if any is a clique, _i.e._, every vertex of the sub-graph is connected to every other vertex.
This takes a polynomial amount of space because we just need to track for each of the vertices of $G$ whether they are currently in or out of the subset.

$\mathsf{SUBSET}$ is in $\mathsf{PSPACE}$ because we can exhaustively search all subsets $S^* \subseteq S$ and check for each whether they sum to $t$.
Like $\mathsf{CLIQUE}$ we can do this search in polynomial space because we just need to track for each element of $S$ whether it is currently in $S^*$ or not.

# Problem: Generalization

::: proof
**Claim**: $\mathsf{NP} \subseteq \mathsf{PSPACE}$.

_Proof_.
Let $A \in \mathsf{NP}$ and let $V$ verify $A$.
Furthermore, suppose that the runtime of $V$ is some polynomial $f$.
Build a polynomial-space decider $D$ for $A$ as follows.

$D(w) = $

+   Enumerate all certificates $c$ up to size $f(|w|)$ and run $V(w, c)$.
+   Accept if any such input-certificate pairs are accepted by the verifier and reject otherwise.

Observe that the verifier can only access certificates whose size does not exceed the runtime of $V$.
Thus, enumeration of these certificates is possible because we need only keep track of the possible certificates using a polynomial-length counter (proportional in size to $f$).

# Problem: Configurations

A configuration representing a TM with an $n$-sized tape is broken up into $n$ tape cells, each of which can be one of $g$ possible symbols and a tape head denoted by one of $q$ states that can appear in one of $n$ positions: $g^n \times qn$ possibilities overall.

# Problem: Cycles

Suppose to the contrary that a TM that halts does repeat a configuration.
Then there must be a chain of sequential $C_1, C_2, \ldots, C_k, C_1$ that starts and ends in the same configuration $C_1$.
Because the configuration fully determines the current state of the TM, we know that from the second $C_1$, we will simply repeat this chain again, resulting in an infinite loop, contradicting the assumption that the TM halts.

# Problem: Upper Bounds

::: proof
**Claim**: $\mathsf{PSPACE} \subseteq \mathsf{EXPTIME}$.

_Proof_.
Let $A \in \mathsf{PSPACE}$ and let $M$ decide $A$ in polynomial space $f$.
Observe that $M$ has an exponential number of possible configurations and that if it were to repeat any such configuration, it would go into an infinite loop.
Therefore, $M$ takes as most an exponential number of steps, one for each configuration.
:::

# Problem: The Puzzle Game

1.  $\mathsf{PUZZLE-GAME} \in \mathsf{PSPACE}$ because we can determine if there is an optimal strategy by leveraging the quantifier-as-turns analogy.
    The following recursive algorithm decides $\mathsf{PUZZLE-GAME}$:

    *   Let $c$ be the top card of the deck and $cs$ of the deck.
        Also let $p$ be the current player.
        +   If $p$ is the first player, then try:
            -   To orient $c$ as-is and recursively decide the game with deck $cs$, setting $p$ to the second player.
            -   To flip $c$ and recursively decide the game with $cs$, setting $p$ to the second player.
            If player 1 wins in _either_ recursive case, then player 1 wins the overall game.
            Otherwise, they lose.
        +   If $p$ is the second player, then try
            -   To orient $c$ as-is and recursively decide the game with deck $cs$, setting $p$ to the first player.
            -   To flip $c$ and recursively decide the game with $cs$, setting $p$ to the first player.
            If player 1 wins in _both_ cases, then player 1 wins the overall game.
            Otherwise, they lose.

    If the deck is empty, inspect the oriented stack of cards.
    If the stack covers the bottom of the box, then player 1 wins.
    Otherwise player 2 wins.

2.  To reduce $\mathsf{FORMULA-GAME}$ to $\mathsf{PUZZLE-GAME}$, follow the reduction from $\mathsf{3SAT}$ to $\mathsf{PUZZLE}$.
    However, for every variable that is existentially quantified, player one chooses the alignment of the card.
    For every variable that is universally quantified, player two chooses the alignment of the card.
    Furthermore, player one chooses the orientation of the extra card (that has exactly one column punched out).
