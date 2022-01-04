---
title: "Reading 24: Undecidability"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Undecidability

+ Sipser, Chapter 5 "Reducibility" through 5.1 "Undecidable Problems From Language Theory" up to "Reductions via Computational histories".
+ [Undecidability and Reductions (Youtube.com)](https://www.youtube.com/watch?v=tiehcXptVgY)

+ [Tech Video: Mapping Reduction and Undecidability Example](https://youtu.be/V3TFosM3PE4)

# Q&A

> Why do we only have to prove one direction of this reduction? In other words, do we not need to show that our TM can also reduce to A_TM?

The same reason why we only go in one direction with NP-hardness—we just need to show that A_tm is upper-bounded by our target problem to establish that the target problem is undecidable.  More generally, there might be "harder" problems that A_tm reduces to (establishing that problem is at least undecidable), but the converse might not be true!

> The book uses the proof by contradiction strategy I outlined in my previous answer. But, why don't we just use the logic "If A is undecidable and reducible to B, then B is undecidable"? For example, to show HALT_tm is undecidable, isn't it just simpler to say that A_tm is undecidable and A_tm reduces to HALT_tm, and so HALT_tm must be undecidable? Or is this faulty logic? 

Nope, that's correct. I outline the relationship between the book's initial reduction proof and the mapping reductions that we used with NP-hardness.  Just like in that situation, we know that if we use a mapping reduction from a NP-hard problem, we know our "to" language is also NP-hard.  So then our proof can focus on the map instead of all the skeleton-stuff around it!

> What about that REGULAR_TM proof?

I'll make a tech video for it and link it above!
