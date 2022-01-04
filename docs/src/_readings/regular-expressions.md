---
title: "Reading 4: Regular Expressions"
layout: content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Regular Expressions

We'll study one final model of "regular" computation: the regular expression.
Whereas finite automata are machine-like models, the regular expression is a *linguistic* model.
While seemingly unrelated, there are both theoretical and pragmatic connections between the models.
As the text illustrates, regular expressions and finite automata are equivalent in computational power.
Pragmatically speaking, regular expressions---a fundamental building block for parsing and pattern recognition---are efficiently implemented by translation into equivalent finite automata.

## Sipser Reading

Through section 1.3 (Regular Expressions).

---

**Reading Problem (Slightly Unnatural)**
Give a regular expression for a language $L$ of strings drawn from the alphabet $\Sigma = \\{ 0, 1, -, . \\}$ that
obey the following properties:

+   All strings in $L$ are strings of binary digits.
+   Each string may optionally be preceded by a single $(-)$.
+   Each string may optionally contain a single $(.)$.
    At least one binary digit must follow the $(.)$ if it appears in the string.
