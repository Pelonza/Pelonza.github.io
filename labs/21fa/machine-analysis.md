---
title: Machine Analysis
layout: content
mathjax: true
---

$$
\newcommand{\EQdfa}{\mathsf{EQ}_\mathsf{DFA}}
$$

# Problem 1: To Infinity And Beyond

Consider the following language:

$$
\EQdfa = \{\, (D_1, D_2) \mid \text{\( D_1 \) and \( D_2 \) are equivalent DFAs} \,\}
$$

Recall that two DFAs are equivalent if their languages are identical.
Theorem 4.5 of Sipser shows that $\EQdfa$ is decidable by way of language closure properties.
In this problem, we'll consider a more direct approach.

a.  Consider the following proof that $\EQdfa$ is decidable by way of constructing a deciding Turing machine that recognizes the language.

    ::: proof
    Define $M$, a deciding Turing machine that decides $\EQdfa$ as follows:

    M = On input $D_1$, $D_2$---two DFAs:

    1.  For every possible string $w \in \Sigma^*$, if $D_1$ and $D_2$ have differing acceptance behavior on $w$, _i.e._, one rejects and the other accepts, then _reject_.
    2.  Otherwise, $D_1$ and $D_2$ have the same acceptance behavior on all strings: _accept_.
    :::

    This construction has a fatal flaw!
    In a few sentences, describe what the flaw is.
b.  We can patch up this flaw by noting that we don't have to test all strings.
    Determine a bound on the size of strings we need to test to determine if two DFAs are equal.
    In a few sentences, argue why this bound is correct.

# Problem 2: Can You Do It? Yes You Can!

a.  Call a language $L$ _prefix-free_ if for all $w \in L$, there does not exist a $w' \in L$ such that $w \neq w'$ and $w'$ is a prefix of $w$.
    For example $ab$ is a prefix of $abcde$ and thus $abcde$ would not be in a prefix-free language if $ab$ was also in the language.
    Give a deciding procedure to determine if the language of a DFA $D$ is prefix free.
    Argue the correctness of your construction in a few sentences.
b.  Apply the construction you developed to the problem of determining whether a Turing machine is prefix-free.
    Identify:

    +   What you must change about the construction in order to adapt it to TMs.
    +   What problem(s) do you ultimately run into with your construction that you cannot reconcile?

c.  The previous part does not necessarily mean that the prefix-free property is not decidable for TMs in general.
    Try to collaboratively develop a new algorithm to determine whether a TM is prefix-free.
    Describe the algorithm at a high-level and give a positive example of its execution, _i.e._, a TM whose language is prefix-free and how the algorithm accepts this TM.
d.  It turns out that the problem of determining whether a TM is prefix free is actually undecidable!
    Since we can't prove this fact yet, give an example of a TM that your algorithm should accept or reject, but the algorithm either fails to give the correct answer or goes into an infinite loop.
