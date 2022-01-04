---
title: Introduction to Turing Machines
layout: content
mathjax: true
---

# Problem 1: Just The Facts, Turing Edition

(Adapted from Sipser 3.5)
Answer the following short questions about Turing machines:

1.  Can a Turing machine ever write the blank symbol `␣` on its tape?
2.  Can the tape alphabet $Γ$ be the same as the input alphabet $Σ$?
3.  Can a Turing machine's head *ever* be in the same location in two successive steps?
4.  Can a Turing machine contain just a single state?
5.  What happens when a Turing machine's head moves off the left end of the tape?
    What happens when it moves off the right end of the tape?

6.  One difference between Turing machines and our previous machine-based models of computation is the presence of a reject state.
    Why was this unnecessary for finite automata?
    Why is it necessary for Turing machines?

7.  Describe the difference between a Turing machine that *recognizes* a language versus a machine that *decides* a language.

8.  We can strongly characterize the runtime of any finite automata in terms of the size of its input.
    What can we say about the runtime of a Turing machine in terms of the size of its input?
9.  Give a implementation-level diagram of a Turing machine that does
    not terminate on any input.

# Problem 2: Implementation Details

(Adapted from Sipser 3.8)
Give implementation-level diagrams of the following languages:

+   $L_1 = \{ w \mid \text{\( w \) contains an equal number of 0s and 1s} \}$.
+   $L_3 = \{ w \mid \text{\( w \) does not contain an equal number of 0s and 1s} \}$.
