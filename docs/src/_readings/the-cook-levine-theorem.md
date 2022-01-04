---
title: "The Cook-Levine Theorem"
layout: content
mathjax: true
---

# The Cook-Levine Theorem

Pragmatically, we show that problems are NP-complete by reduction from a known NP-complete problem.
If we know that a problem B is (poly-time) reducible from a problem A ($A \leq_p B$), then we know that $B$ is as hard as $A$.
Furthermore, if $A$ is NP-complete, then we know that $B$ is reducible from any other problem $X$ in NP by first reducing $X$ to $A$ and then $A$ to $B$.

However, how do we establish the first NP-complete problem?
This is the focus of the Cook-Levine theorem which claims that:

$$
\mathsf{SAT} = \\{ \phi \mid \text{ $\phi$ is a satisfiable boolean formula } \\}.
$$

is NP-complete.

The proof is fundamentally easy to understand---circuits are ultimately boolean formula and we can thus use such formulae to represent general computation---but it is extremely detail-oriented and touches on all aspects of the formal definition of Turing machine we discussed prior to the first exam.
Hence we will spend a substantial amount of time ensuring that we understand the proof in depth, so that we have a clear foundation to work from in understanding NP-completeness.

* Sipser 7.4 from "The Cook-Levine Theorem".

---

**Reading Problem (Windows)**

The presentation of Cook-Levine in Sipser relies heavily on the notion of "window".

1. Windows are used in the $\phi_{\text{move}}$ formula of the proof.
   What does this boolean formula capture?
2. Suppose that we are translating the Turing machine $M_1$ from figure 3.10 of the text (pp. 173 in the third edition) to a boolean formula according to Cook-Levine.
   Suppose that the current configuration $C_i$ under consideration is $"xxq_{3}10\\#xx00"$.
   (Recall that a configuration represents the current contents of the tape, the current state, and the position of the tape head.)
   Describe (a) a *legal* window involving configurations $C_i$ and the next configuration $C_{i+1}$ and a (b) *illegal* window involving these configurations.
