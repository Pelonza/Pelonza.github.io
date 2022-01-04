---
lab: PSPACE-Completeness
layout: content
mathjax: true
---

# Problem: The Puzzle Game

Recall the _puzzle_ problem, $\text{PUZZLE}$, from a previous lab:

> You are given a box and a collection of cards as indicated in the following figure.
> Because of the pegs in the box and the notches in the cards, each card will fit in the box in either of two ways.
> Each card contains two columns of holes, some of which may not be punched out.
> The puzzle is solved by placing all the cards in the box so as to completely cover the bottom of the box (_i.e._, every hole position is blocked by at least one card that has no hole there).

Consider a related problem, the two-player _puzzle game_, $\text{PUZZLE-GAME}$.
The game consists of an _ordered_ stack of cards as described in $\textsf{PUZZLE}$. Players take turns placing the cards in order into the box, choosing whether or not the card is flipped.
After placing all the cards, player one wins if all the hole positions are covered in the stack; player two wins if this is not the case.

Define:
$$
\text{PUZZLE-GAME} = \{\, C \mid \text{\( C \) is an ordered stack of puzzle cards and player 1 has a winning strategy} \,\}.
$$

In this problem, we'll show that $\text{PUZZLE-GAME}$ is $\mathsf{PSPACE}$-complete.

1.  Show that $\text{PUZZLE-GAME} \in \mathsf{PSPACE}$.

2.  From the reading, you know that:

    $$
    \text{FORMULA-GAME} = \{\, \phi \mid \text{\( \phi \) is a TQBF and player 1 has a winning strategy} \,\}.
    $$

    is $\mathsf{PSPACE}$-complete.
    Furthermore, the restriction of the boolean formulas to 3-cnf form is also $\mathsf{PSPACE}$-complete.
    Use this fact to construct a polynomial time mapping function from the 3-cnf version of $\textsf{FORMULA-GAME}$ to $\textsf{PUZZLE{-}GAME}$, demonstrating that $\textsf{PUZZLE-GAME}$ is $\mathsf{PSPACE}$-hard.
    In a few sentences, argue why your construction is correct.

    (_Hint_: Adopt the solution for $\textsf{PUZZLE}$ directly.)

3.  Show your construction is correct by giving an example of the output of your mapping function on the following TQBF in 3-cnf form:

    $$
    \exists x_1 \forall x_2 \exists x_3 \ldotp [ (x_1 \vee x_2 \vee x_1) \wedge (x_2 \vee x_3 \vee x_3) \wedge (\overline{x_2} \vee \overline{x_3} \vee \overline{x_3}) ]
    $$

    As well as a winning strategy for player 1 on the resulting puzzle game.
