---
title: Demonstration Exercise 2
layout: content
mathjax: true
---

# Problem 1: ☠

Formally define a _DFA with death_ $D = (Q, \Sigma^*, q_0, \delta, F)$ as a DFA except that the type of the transition function is:

$$
\delta : Q \times Σ \rightarrow Q \cup \{\, ☠ \,\}.
$$

We assume that $☠ \notin Q$. Intuitively, if a state-character pair transitions to ☠ (LaTeX: `\skull`, Unicode: ☠), then no additional input is consumed and the machine rejects the input string.

1.  Recall that $M$ accepts $w$ if there exists a sequence of states $r_0, r_1, \ldots, r_n \in Q$ such that:

    +   $r_0 = q_0$,
    +   $\delta(r_i, w_{i+1}) = r_{i+1}$ for $i = 0, \ldots, n-1$, and
    +   $r_n in F$.

    Does the definition of acceptance need to change for a DFA with death?
    If so, give a modified definition, explaining what changes you made in a sentence or two.
    If not, explain why in a sentence or two.

2.  Prove that a DFA with death is equivalent to a DFA.
    Make sure to prove both sides of this equivalence!

# Problem 2: Embedding

Define the embedding of language $L_2$ into $L_1$, written $L_1 \curvearrowleft L_2$ (LaTeX: `\curvearrowleft`, Unicode: ↶) as:

$$
L_1 \curvearrowleft L_2 = \{\, x_1 y x_2 \mid x_1 x_2 \in L_1, y \in L_2 \,\}.
$$

(_Note_: it is $x_1 x_2$, _i.e._, their concatenation, that is in $L_1$.
$x_1$ and $x_2$, individually, may not be in $L_1$.)

Prove that the language embedding operator (↶) is closed under the regular languages.

(_Hint 1_: work through a number of examples of finite automata, combining them with the (↶) operator and developing an intuitive sense of how to compute the embedding.)

(_Hint 2_: to implement this construction elegantly, you will need to use nondeterminism heavily!
Also, don't be afraid to replicate your assumed machines for $L_1$ and $L_2$ repeatedly.)

(_Hint 3_: regarding formalizing your construction, it is likely fairly complicated!
I recommend developing a systematic notation for talking about the various states and transitions of your final machine.
For example, if you want to denote a copy of a machine, say $N$, that is associated with some state, call it $q$, you might call the copy $N_q$.)
