---
title: DFA Basics
layout: content
mathjax: true
---

# Problem 1: Connect the Dots

Answer the following questions about the fundamental definitions that connect languages, machines, and computation.

+   What do the metavariables $\Sigma$, $\Sigma^*$, and $L$ traditionally represent?
    Give a concrete example that covers all three concepts.
+   What are the _types_ of the five components of a finite automata: $(Q, \Sigma, \delta, q_0, F)$?
+   What does $L(M)$ conventionally mean? If $L(M) = A$, what is the relationship between $M$ and $A$?
+   If we want to _prove_ that "$M$ accepts $w$," what we must we do?

# Problem 2: Tracing the Lines

Consider the following DFA $D$:

![A sample deterministic finite automata over the alphabet $\Sigma = \{\, 0, 1 \,\}$.]({{ "/img/dfa-basics-01.png" | relative_url }})

+   Give execution traces, _i.e._, the series of states that the DFA steps through on the following input strings.
    Also state whether $D$ accepts the given input string.
    Make sure to give each of your group members a chance to take the lead in creating these traces.

    -   $01100$
    +   $101101$
    +   $11111$
    +   $\epsilon$ (the empty string)
    +   $1010101$

+   Importantly, we can each think of state of a finite automata as encoding an _property_ about the current computation, _i.e._, some property of the set of characters read so far.
    Based on the traces you wrote above, give an appropriate property for each of $q_0$, $q_1$, $q_2$, and $q_3$ _solely in terms of the input read so far after arriving at that state_, not about the various parts of the DFA.

+   Using these traces and the properties you wrote down for each state, give a formal description of $L(D)$.
