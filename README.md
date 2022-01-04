# PM's course materials for CSC 341

This archive contains my course materials for CSC 341, The Theory of
Computation. The course follows Sipser's Theory of Computation closely
with the following exceptions:

+   I only devote a day to introduce context-free grammars (chapter 2) and skip
    over the remaining content of the chapter. I find the material to be
    redundant with the finite automata material and prefer to emphasize the
    theory of computation aspects of the course over the language theory
    aspects.
+   I go through computational complexity (chapters 7–9) before covering
    decidability (chapters 4–6). I find that, from a mechanical perspective,
    the reductions concerning complexity are easier to understand than
    undecidability reductions. Undecidability reductions operate over
    higher-order functions (i.e., Turing machines that take other Turing
    machines as input) and operate in the context of contradictory proof.
    Complexity reductions, while more complicated to design, are constructive
    in nature and much easier to reason about.

I also try to devote the last 2 weeks of class to a special topic in the theory
of computation. Last semester (Fall 2021), I covered approximation algorithms
which I think dovetailed quite well with Sipser's presentation. For that
section of the course, I drew on material from:

+   The Design of Approximation Algorithm, Williamson and Shmoys

In the past I've covered quantum computation, the lambda calculus, and
primitive recursive functions. More recently, I've thought about reclaiming
these final weeks to give more time to the complexity section of the course.
I think there's merit in given students plenty of time to think and work
through complexity, so that they get a concrete, "lived-in" experience of
these problems and their relationships.

## Contents

+   `/demos`: demonstration exercises, i.e., weekly homeworks
+   `/labs`: in-class lab assignments
+   `/las`: learning assessments, i.e., online, timed exams. You can view these
    as quiz questions that focus on skills and comprehension rather than
    in-depth problem solving.
+   `/readings`: the readings I assigned for class. Most are just pointers to
    Sipser, but others include more in-depth treatment of the material.
+   `/website`: a dump of the previous course website as well as its
    Jekyll-based infrastructure.
