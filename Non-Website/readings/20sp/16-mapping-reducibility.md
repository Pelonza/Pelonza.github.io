---
title: "Reading 16: Mapping Reducibility"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Mapping Reducibility

This upcoming week, we will study NP-completeness in depth.
Our goals are threefold:

1. Refine our skills of developing mapping reductions between problems of increasingly disparate nature.
2. Identify the types of problems that are NP-complete.
3. Gain context into the famous \\( P = NP \\) problem.

To do this, we need to utilize our skills of rigorous mathematical reasoning and mathematical fortitude to effectively explore a large space of possibilities for our reductions and ultimately settle on a correct one.

+ Review Sipser 7.4 "Polynomial Time Reducibility" to "The Cook-Levine Theorem"
  Read and study Theorem 7.32 (\\( \text{3SAT} \leq_p \text{CLIQUE} \\)) in detail.
+ Skim Sipser 7.5 "Additional NP-Complete Problems".
  Read and study Theorem 7.44 (\\( \text{VERTEX-COVER} \\) is NP-complete) in detail.

---

**Reading Problem (Details)**

1. In the construction of the \\( \text{CLIQUE} \\) instance in Theorem 7.32, it is noted that "no edge is present between two nodes of contradictory labels".
   Suppose that this restriction was lifted so that there *is* an edge present between nodes with contradictory labels.
   Identify specifically where the proof of correctness fails with this change.
2. In the construction of the \\( \text{VERTEX-COVER} \\) instance in Theorem 7.44, the size of the vertex cover is set to be \\( k = m + 2l \\) where \\( m \\) is the number of variables and \\( l \\) is the number of clauses in \\( \phi \\), the input \\( \text{3-SAT} \\) instance.
   How does this formula for \\( k \\) relate to the choice of vertices in the cover for the group, *i.e.*, explain where \\( m \\) and \\( 2l \\) come from in terms of the construction of the potential cover and explain why these are the correct values.
