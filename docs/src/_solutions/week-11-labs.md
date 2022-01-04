---
title: Week 11 Lab Solutions
layout: content
mathjax: true
---

$$
\newcommand{\tile}[2]{\left[\frac{\texttt{#1}}{\texttt{#2}}\right]}
\newcommand{\desc}[1]{\langle #1 \rangle}
$$

# Lab: Machine Behavior Undecidability

## Problem 1: Enter the Machine

$$
\mathsf{USELESS} = \{\, \langle M \rangle \mid \text{\( M \) is a TM with at least one useless state} \,\}.
$$

## Problem 2: Mappings

$f$ takes an input to $A_\mathsf{TM}$, a Turing machine $M$ and input $w$ to that Turing machine as input, and produces an input to $\mathsf{USELESS}$, a Turing machine $M'$, as output.

## Problem 3: The Condition

$M$ accepts $w$ if and only if $M'$ has at least one useless state.

## Problem 4: The Construction

::: proof
_Proof_.
Assume for the sake of contradiction that $\mathsf{USELESS}$ is undecidable, so let $D$ decide it.
Define a decider for $A_\mathsf{TM}$, $A$, as follows:

$A$ = On input $\langle M, w \rangle$:

*   Define a Turing machine $M'$ that possesses a distinguished state $q_\mathsf{last}$ that can be only be reached from $q_\mathsf{start}$ and
    reading a special symbol $\omega$ that does not appear anywhere else in $M$ or $M'$.
    Define $M'$ as follows:
    +   $M'$ = On input $x$:
        -   If $x = \epsilon$, then visit every one of the states of $M'$ except for $q_\mathsf{last}$.
            Do so by writing a special symbol $@$ on the tape head that is not mentioned in any of the other transitions of $M'$.
            Then use this tape symbol to transition to every state (except for $q_\mathsf{last}$) in lexicographical order.
        -   If $M$ accepts $w$, transition to $q_\mathsf{start}$, write an $\omega$ to the tape, and then use that to transition to $q_\mathsf{last}$.
        -   Regardless of which branch we take, end by infinite looping anywhere on $M'$
-   Run $D$ on $M'$ and do the opposite of what $D$ does.
:::

Note that we must use a general reduction instead of a mapping reduction because the rejection and infinite loop cases require that $M'$ do positive behavior; they must transition to $q_\mathsf{last}$.
Since we cannot get positive behavior out of the infinite loop, we instead use complementary behavior and negate the results of the assumed decider for $\mathsf{USELESS}$.

## Problem 5: The Proof of Correctness

::: proof
Observe that $M'$ reaches all of its states on input $\epsilon$ except for $q_\mathsf{last}$.
Thus, we only need to reason about whether a particular case reaches $q_\mathsf{last}$.

+   When $M$ accepts $w$, we transition to $q_\mathsf{last}$ explicitly so $M'$ has no useless states.
    Therefore, $D$ rejects $M'$ and $A$ (the assumed decider for $A_\mathsf{TM}$) accepts.
+   When $M$ rejects $w$, we do not reach $q_\mathsf{last}$.
    Therefore, $D$ accepts $M'$ and $A$ rejects.
+   When $M$ loops on $w$, we do not reach $q_\mathsf{last}$.
    Therefore, $D$ accepts $M'$ and $A$ rejects.
:::

# Lab: PCP

## Problem: Honey Bunches of Oats

An example match:

$$
\tile{ab}{abab}, \tile{ab}{abab}, \tile{aba}{b}, \tile{b}{a}, \tile{b}{a}, \tile{aa}{a}, \tile{aa}{a}.
$$

::: proof
_Proof_.
Let $T$ be the set of tiles and for each tile $t \in T$, let $|t|$ be the difference of the number of $a$s on top of $t$ and the number of $a$s on the bottom of $t$.
Then $T$ has a solution if and only if the following equation has a solution:

$$
\sum_{t \in T} |t| \cdot x_t = 0.
$$

Where each $x_t$ is a natural number denoting the number of occurrences of $t$ in a candidate solution.
Such linear equations are always solvable, _e.g._, by Gaussian elimination, and thus this restricted version of PCP is decidable.
:::

# Lab: Rice's Theorem

## Problem 1: Language Property Example

$P$ is a machine property, not a language property!
For example, let $M_1$ and $M_2$ be Turing machines that reject all strings so $L(M_1) = L(M_2) = \emptyset$.
However, let $M_1$ write '\$' on the tape before rejecting whereas $M_2$ rejects immediately.
Then $M_1 \in P$ and $M_2 \notin P$.

## Problem 2: Core Reduction

:::proof
Let $T$ be a TM such that $\desc{T} \in P$ and let $\desc{T_\emptyset} \notin P$.
Define the mapping reduction $f(M, w) = M'$ where $M'$ is defined as follows:

$M' =$ On input $x$:

+   Run $M$ on $w$.
    -   If $M$ accepts $w$, run $T$ on $x$ and do what $T$ does.
    -   If $M$ rejects $w$, reject $x$.

Observe that if $M$ accepts $w$ when $M' \in P$ because $M'$ identically to $T$ which is assumed to be in $P$.
If $M$ does not accept $w$, then $L(M') = \emptyset$ and thus it behaves identically to $T_\emptyset$ which is assumed to not be in $P$.

Finally, note that since $P$ is a language property, membership of $P$ is determined entirely by the strings that $M'$ accepts, so any additional behavior of $M'$ beyond simulation of $T$ does not affect whether $M'$ is in $P$.
:::

## Problem 3: The First Constraint

The non-trivial property allows us to posit the existence of a pair of Turing machines, one of which is in $P$ and the other not in $P$.

## Problem 4: The Final Fix-Up

Assume that we have a decider for $\overline{P}$, call it $\overline{D}$.
A decider for $P$, call it $D$ operates by running $\overline{D}$ and doing the opposite of what it does.
Because $\overline{D}$ is a decider, we do not need to worry about whether $\overline{D}$ loops.
