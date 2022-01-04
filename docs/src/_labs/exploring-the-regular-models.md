---
title: Exploring the Regular Models
layout: content
mathjax: true
---

# Problem 1: Go To Implementation

1.  Describe how you might *implement* a deterministic finite automata efficiently.
    Describe how you would (a) represent each of the components of the DFA and (b) simulate the transition function on a particular input.
    What is the time and space complexity of the process of simulating a DFA?

2.  In contrast, describe how you might *execute* the matching procedure of a regular expression directly using recursion.
    What is the time and space complexity of directly executing a regular expression?

3.  Many implementations of regular expressions, _e.g._,, in Python provide a function to _compile_ a regular expression into an optimized form as an alternative to direct interpretation.
    Based on your knowledge of the relationship of DFAs, NFAs, and regular expressions and the above analysis, what do you believe happens if you compile a regular expression?

# Problem 2: All or Nothing

Give an algorithm to determine whether a DFA $D$ accepts *all* strings, _i.e._, $L(D) = Σ^*$.
Prove that your algorithm is correct.

# Problem 3: That's Regular? (Optional)

(Adapted from Sipser 1.32)
It may seem like the class of regular languages is restricted to simple analyses on limited alphabets.
However, with appropriate encodings, we can capture some surprisingly fundamental sorts of computation.

Consider the following alphabet:

$$
\Sigma_3 = \Bigg\{ \begin{bmatrix}0 \\ 0 \\ 0\end{bmatrix}, \begin{bmatrix}0 \\ 0 \\ 1\end{bmatrix}, \begin{bmatrix}0 \\ 1 \\ 0\end{bmatrix}, \ldots, \begin{bmatrix}1 \\ 1 \\ 1\end{bmatrix} \Bigg\}.
$$

$\Sigma_3$ contains all size 3 columns of 0s and 1s.
A string of symbols in $\Sigma_3$ gives three rows of 0s and 1s.
Consider each row to be a binary number and let:

$$
B = \{\, w \in \Sigma^*_3 \mid \text{The bottom row of \( w \) is the sum of the top two rows} \,\}.
$$

For example,

$$
\begin{bmatrix}0 \\ 0 \\ 1\end{bmatrix} \begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix} \begin{bmatrix}1 \\ 1 \\ 0\end{bmatrix} \in B,
$$

but:
$$
\begin{bmatrix}0 \\ 0 \\ 1\end{bmatrix} \begin{bmatrix}1 \\ 0 \\ 1\end{bmatrix} \not\in B.
$$

Observe that in the first case, we carry from the $2^0 = 1$s place to the $2^1 = 2$s place.
If we we were to carry from the $2^2 = 4$s place, we would end up dropping the carry as this is the last column (_i.e._, there is no $2^3 = 8$s place).

Show that $B$ is regular.
To do this, note that we've already proven language reversal, $L^R$, is closed under the regular languages.
You will likely find it easier to work with $B^R$ instead.
