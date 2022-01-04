---
title: "Time Compelxity"
layout: content
mathjax: true
---

# Time Complexity

On Monday, we begin our journey into complexity theory!
First we'll review the basics of complexity theory as presented in CSC 207 and 301, situating our notions of complexity within our primary model of computation, the Turing machine.

* Sipser 7.1 and 7.2, "Measuring Complexity" and "The Class P".

*Skim* the beginning of 7.1 to review the definition of Big-O.
The rest of the reading gives various examples of high-level Turing machine descriptions (*i.e.*, algorithms) and their complexity analysis, ultimately settling on the class $P$.
Pay attention to how our notion of time complexity is defined and analyzed in terms of Turing machines.
Also, pay special attention to the end of 7.1 which talks about the runtime of Turing machine variants when adapted as ordinary Turing machines.
These sorts of transformations and their effects on runtime (in particular, the nondeterministic-to-deterministic transformation) will be important later when we discuss other complexity classes.

---

**Reading Problem (Just The Facts)**

Answer these conceptual questions in a sentence or two a piece.

1. What is the complexity class $P$?
2. How do I show that a language belongs to $P$?
3. In theorem 7.11, we show that a DTM can simulate a NTM with runtime $t(n)$ in $2^{\mathcal{O}(t(n))}$ time.
   How does the proof of the theorem bound the total number of leaves in the tree when a Turing machine can potentially go into infinite loops?
