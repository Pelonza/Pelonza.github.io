---
title: "Reading 6: Properties of the Regular Languages"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Properties of the Regular Languages

When studying models of computation, we are interested in two broad sorts of properties:

1. *Closure* properties that state that, when given regular languages, that an operator produces a regular language.
2. *Decision* properties or *procedures* that allow us to analyze a particular DFA, NFA, or regular expression.

## Sipser Reading

Review the closure proofs for DFAs, NFAs, and regular expressions found between in sections 1.1 to 1.3.
These include the proofs that union (1.45), concatenation (1.47), kleene star (1.49) are closed under the regular languages.

## Decision Procedures

Also read this handout on decision properties of the regular languages:

* [DFA Decision Procedures](/courses/csc341/20sp/files/dfa-decision-procedures.pdf)

---

**Reading Problem (Complement)**

The *complement* of a language is defined to be the set of strings *not* in the language:

\\[
  \overline{L} = \\{ w \mid w \not\in L \\}.
\\]

Give a proof sketch (high-level proof description) that complement is closed under the regular languages.
In particular, which language model would you use to prove closure in this case?
At a high-level, how do you transform an instant of this model into one that recognizes its complement?
