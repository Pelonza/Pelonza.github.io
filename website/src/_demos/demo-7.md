---
title: "Demonstration Exercise #7"
layout: content
mathjax: true
---

# Problem 1: Tic-Tacs

a.  Consider the following position in a standard tic-tac-toe game:

    ~~~
     x |   |
    ---|---|---
       | o |
    ---|---|---
     o |   | x
    ~~~

    Let's say that it is the `x`-player's turn to move next.
    Describe a winning strategy for this player.
    (Recall that a winning strategy isn't merely the best move to make in the current position.
    It also includes all the responses that this player must make to win regardless of how the opponent moves.)

b.  Define the _generalized tic-tac-toe game_ as:

    $$
    \mathsf{GTAC} = \{\, (M, m, n, k) \mid \text{\( M \) is a \( m \times n \) board and player one has a winning strategy.} \,\}.
    $$

    A generalized tic-tac-toe game is played on an $m \times n$ board with some placement of $x$s (player one's pieces) and $o$s (player two's pieces).
    The player wins the game if they can arrange $k$ of their pieces on the board in a line—vertically, horizontally, or diagonally.
    The \mathsf{GTAC} problem asks whether for a given board if player one has a strategy that allows them to win given the current board configuration.

    Show that $\mathsf{GTAC} \in \mathsf{PSPACE}$.

    (_Hint_: adapt the solution for \mathsf{FORMULA{-}GAME} from the reading to this setting.)


# Problem 2: Reductions

Prove that the following languages are undecidable by reduction from a known, undecidable language:

a.  $L_1 = \{\, M \mid \text{\( M \) is a TM and \( L(M) \) is infinite} \,\}$.
b.  $L_2 = \{\, M \mid \text{\( M \) is a TM and the \( L(M) \) is finite} \,\}$

(_Hint_: A contradiction can be established with a simple mapping reduction for $L_1$.
However, $L_2$ is surprisingly not as simple; you will need to write a general reduction instead!}


# Problem 3: Machinations

Consider two languages that represent decision procedures over Turing machines:

+   $L_1$: determine if a TM $M$ on input $w$ ever attempts to move its head left when its head is on the left-most tape cell.
+   $L_2$: determine if a TM $M$ on input $w$ ever attempts to move its head left during computation on $w$.

a.  $L_1$ is undecidable; prove it.
    In your construction, make it clear how the decider for $L_1$ will detect the relevant behavior from $M$ on $w$.

b.  $L_2$ is decidable; prove it.

    (_Hint_: imagine a Turing machine that _never_ moves its head left during computation.
    What can it never do?)

c.  With what you learned from these proofs, come up with a language $L_3$ that is also a decidable problem that analyzes how a TM $M$ computes on input $w$.
