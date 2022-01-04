---
title: "Reading 35: Qubits"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Qubits

Finally, we will now combine probabilistic programming, a circuit-based model of computation, and a little bit of secret sauce to arrive at a basic model of quantum computation.
The core of this model is a variation of a bit called a *quibit*.
Recall that a bit is conceptually a value that takes on one of two possibilities, traditionally called \\( 0 \\) or \\( 1 \\), "on" or "off", "true" or "false", *etc.*
Bits arise in classical computing devices because the electric current measured in digital circuits is only stored and measured in terms of two states: is there a significant or insignificant amount of current in the circuit?
Qubits arise as a consequence of quantum phenomena where the system captures states that are not simply "on" or "off", but in a *superposition* of the two.

A naive perspective of "superposition" in this context would suggest that a qubit is a bit that has a certain probability of being a \\( 0 \\) or a \\( 1 \\).
But as Scott Aaronson and Zach Weinersmith illustrate in [The Talk](https://www.smbc-comics.com/comic/3the-talk-3), the nature of a qubit transcends our classical intuition about probabilities since quantum phenomena is just that: "unclassical."
This is why a technical, mathematical perspective on quantum computing is so useful.
Mathematics allows us to model and reason about unintuitive phenomena so that we can gain some higher level understanding how it works.

Nevertheless, we don't have time to go into this level of depth.
So we will attempt to tread a line between giving high-level, yet technically accurate descriptions of the elements of quantum computation and diving into the mathematical weeds as needed to justify our descriptions.
To begin our journey, read the aforementioned "The Talk" by Aaronson on Weinersmith that gives the 50,000 foot perspective on the subject:

+ Scott Aaronson and Zach Weinersmith.  [The Talk](https://www.smbc-comics.com/comic/the-talk-3).  Saturday Morning Breakfast Cereal.  December 14, 2016.

And then work through this high-level, interactive tutorial of qubits and quantum gates by David Kemp.
His tutorial builds on the ideas of probabilistic programming and circuits that we have explored so far.

+ David Kemp. [An Interactive Introduction To Quantum Computing](https://davidbkemp.github.io/QuantumComputingArticle/).  From [davidbkemp.github.io](https://davidbkemp.github.io).  December 2017.

Make sure to read both parts of the tutorial!
The second article ends with a basic application---Grover's Search Algorithm---and some discussion of the mathematics behind the tutorial.
We'll further explore the mathematics in class on Wednesday!
