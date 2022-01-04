---
title: "Reading 14: NP-Completeness"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# NP-Completeness

Now that we've reviewed the basics of complexity theory, we'll jump into the meat of the discussion: NP-Completeness.
The \\( P = NP \\) asks whether the class of polynomial time problems is equivalent to the class of nondeterministic polynominal time problems.
To understand the nature of the problem and why it is so important, we'll investigate the class \\( NP \\) in more detail as well as explore the idea of *completeness* for a complexity class: problems that define the "outer border" of that class.

* Sipser 7.3 "The class NP" and 7.4 "NP-Completeness" to "The Cook-Levin Theorem".

---

**Reading Problem (More Facts)**

Answer these conceptual questions in a sentence or two a piece.

1. How do we define the class \\( NP \\) in terms of a "certificate"?
   How does the "certificate" relate to the "non-determinism" part of \\( NP \\)?
2. How do I show that a language is \\( NP \\)-complete?
3. Suppose that \\( A \leq_p B \\).
   Which of these languages is "solving" the other?
   Which of these languages is "stronger" than the other?
