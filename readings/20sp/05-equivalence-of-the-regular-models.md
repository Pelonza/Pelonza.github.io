---
title: "Reading 5: Equivalence of the Regular Models"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Equivalence of the Regular Models

Now that we've explored our three basic models of computation, we'll now turn our attention to their theory.
We'll begin by discussing these equivalences—DFAs, NFAs, and regular expressions all recognize precisely the class of *regular languages*—and how we prove them.

## Sipser Reading

Review the equivalence proofs of DFAs, NFAs, and regular expressions found between in sections 1.1 to 1.3.

---

**Reading Problem (Constructive)**

Consider the following regular expression:
\\[
  R = \Sigma^* 101 \Sigma^*
\\]
Using the proof of lemma 1.55 (regular expressions recognize regular languages), give a NFA that recognizes the same language as \\( R \\).
Note that this will not look exactly like the optimal NFA you might derive if you hand-crafted such a NFA instead!
