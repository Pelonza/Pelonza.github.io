---
title: Finding Essence
layout: content
mathjax: true
---

# Problem: All NFAs

An _all_-NFA $M$ is a 5-tuple $(Q, \Sigma, \delta, q_0, F)$ that behaves like an NFA except that it accepts $x \in \Sigma^*$ if _every_ possible state that $M$ could be in after reading input $x$ is a state from $F$.
Note, in contrast, that an ordinary NFA accepts a string if _some_ state among these possible states is an accept state.
Prove the following claim:

::: proof
**Claim**: all-NFAs recognize the class of regular languages.
:::

1.  **Understand the Definitions**: create a small, toy all-NFA $M$ that exhibits the essence of the all-NFA construction and give a pair of strings, one of which $M$ accepts and the other $M$ rejects.
    Give the execution traces of these strings on $M$.
2.  **Assess the Claim**: read the claim.
    Identify what you must do (_i.e._, construct) in order to prove this claim.
3.  **Explore the Design Space**: use your toy all-NFA $M$ and convert it to an equivalent NFA.
    Likewise, create a small, toy NFA $N$ and convert it into an equivalent all-NFA.
    Perform your conversion with an eye towards _generalizing the conversion process_.
    In other words, you should try to work mechanically on the structure of the machines rather than with knowledge of the particulars of their languages.
4.  **State Essence**: your previous exploration should convince you that the claim is true.
    In a sentence or two, identify the "essence" as to why the claim is true.
    Try to appeal to the behaviors of NFAs/DFAs versus all-NFAs.
    Work through more examples if you are still unsure of the essence of this claim.
5.  **Develop a Proof Strategy**: based on this essence, describe at a high-level plan how to (a) convert an all-NFA into a DFA/NFA and (b) convert an DFA/NFA into an all-NFA.
6.  **Start with the Easy Case**: next, formally prove the "easy direction" of the claim.
7.  **Finish It Off**: finally, finish the proof by proving the "hard direction" of the claim.
