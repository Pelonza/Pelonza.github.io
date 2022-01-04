---
title: "Reading 9: The Essence of Context-Free Languages"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# The Essence of Context-Free Languages

Context-free grammars are our primary model of computation for context-free languages.
However, context-free grammars do not really unveil the "essence" of the class of context-free languages is.
Their machine analog, the *pushdown automata*, makes the essence of CFLs much more apparent.
We'll discuss PDAs briefly as an extension of finite automata as well as the properties of CFLs in contrast with the regular languages.


## Reading

For next class, please read about pushdown automata and briefly skim the section on non-context-free languages.

* Sipser, chapter 2.2 "Context-free Grammars" through 2.3 "Non-Context-Free Languages" (skim 2.3).

---

**Reading Problem (PDAs, Ew)**

Give a diagram of a pushdown automata \\( P \\) that recognizes the following language (over alphabet \\( \Sigma = \\{ 0, 1 \\} \\)):

\\[
  A = \\{ w \mid \text{\\( w \\) is a palindrome (\\( w = w^R \\))} \\}.
\\]
