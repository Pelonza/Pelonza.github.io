---
title: "Reading 7: Irregularity"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Irregularity

DFAs, NFAs, and regular expressions are all *restricted* models of computation in that we trade-off computational expressiveness for tractability in terms of analysis.
We crystallize the limitations of these models by showing that some languages are provably not regular.
We can do this via two methods:

1. *The pumping lemma* which describes a necessary characteristic of the repetitive nature of infinite regular languages.
2. *The Myhill-Nerode theorem* which relates finite automata properties to regularity directly.

## Reading

* Learn about the pumping lemma from Sipser, chapter 1.4, "Nonregular Languages".
* Learn about the Myhill-Nerode theorem from this handout on the subject:
    + [Myhill Nerode Theorem](/courses/csc341/20sp/files/myhill-nerode-theorem.pdf)

---

**Reading Problem (Skeletons)**

The pumping lemma and Myhill-Nerode theorem each give a unique technique for proving that a language is irregular.
Give a *proof skeleton* for each technique.
A proof skeleton for a particular proof technique is an *outline* of a proof using that technique, clearly indicating:

1. What is *generic* in the proof, *i.e.*, what parts of the skeleton hold for all claims when using this technique.
2. What we must ultimately *show* when proving a particular claim.
   This part should be unique to each claim.
