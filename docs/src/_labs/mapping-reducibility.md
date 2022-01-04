---
title: Mapping Reducibility
layout: content
mathjax: true
---

$$
\newcommand{\NP}{\mathsf{NP}\xspace}\newcommand{\PUZZLE}{\mathsf{PUZZLE}\xspace}\newcommand{\SAT}{\mathsf{SAT}\xspace}
$$

# Problem: Card Reductions

(Sipser 7.28)
You are given a box and a collection of cards as indicated in the following figure.
Because of the pegs in the box and the notches in the cards, each card will fit in the box in either of two ways.
Each card contains two columns of holes, some of which may not be punched out.
The puzzle is solved by placing all the cards in the box so as to completely cover the bottom of the box (every hole position is blocked by at least one card that has no hole there).

![Image of cards with holes]({{ "/img/cards.png" | relative_url }})


Let:

$$
\PUZZLE = \{\, \langle c_1, \ldots, c_k \rangle \mid \text{Each \( c_i \) represents a card and this collection of cards has a solution } \,\}.
$$

Ultimately, our goal will be to show that $\PUZZLE$ is $\NP$-complete.

a.  First, let's explore this problem space a little bit.
    Design two sets of cards, $C_1$ and $C_2$.
    For $C_1$, ensure that there is a solution to the puzzle, _i.e._, an orientation of each card such that the bottom of the box is covered, and list this solution.
    For $C_2$, ensure that there is no such solution to the puzzle.
    Try to make these example cards _non-degenerate_, _i.e._, every card has no holes, so that you can use your examples to generalize these results.

b.  To show $\NP$-completeness, we must show membership and hardness.
    First, show that $\PUZZLE \in \NP$.

    (_Hint_: what is a potential solution to $\PUZZLE$?
    How do we verify that the solution is correct?)

c.  Now, let's talk about proving hardness.
    Here, we will show $\NP$-hardness by reducing $\SAT$ to $\PUZZLE$ where we know via the reading that $\SAT$ is $\NP$-complete.
    First, let's identify the "inputs" to each of the problems.
    What are the inputs to (predicates that decide) $\SAT$ and $\PUZZLE$?

d.  With the inputs, let's constrain our reduction function $f$.
    Write down the _type_ of the reduction function $f$, _i.e._, what does $f$ take as input and produce as output?
    Furthermore, write down the _correctness_ condition of $f$ based on its type.

e.  Next we must design $f$.
    It is likely not clear how to proceed as the problems are in vastly different domains!
    Ultimately what we want to do is _connect_ the various parts of the inputs of $\SAT$ and $\PUZZLE$ which will allow us to then build our reduction function in a way that "preserves" correctness.
    List down the _components_ of the inputs to $\SAT$ and $\PUZZLE$.

f.  At this point, we've gotten all the facts out necessary to design $f$.
    We must now experiment with designs that link together these parts and see if we can strike gold!
    To do this productively, first design a toy $\SAT$ example of 3–4 variables and 3–4 clauses with a satisfying assignment.
    Give at least _two potential designs_ for reductions from $\SAT$ to $\PUZZLE$ showing how your reductions operate on your toy example, _even if the designs do not work!_
    If the designs do not work, describe what was broken about the reduction and how you could then address it in a subsequent attempt.

g.  Repeat (f) until you find a working reduction.
    Once you have this reduction, formally show that $\SAT \leq_p \PUZZLE$, demonstrating that $\PUZZLE$ is $\NP$-hard.
    Make sure to prove both sides of the correctness condition of your reduction!
