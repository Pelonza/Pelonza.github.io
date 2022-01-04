---
title: Constructive and Classical Proof
layout: content
mathjax: true
---

Whether we adopt the perspective of programmer or mathematician, we rely on modeling techniques such as mathematical sets or data structures to represent a subject, _e.g.,_ general computation, in a way that is amendable for subsequent analysis.
However, whereas programmers are primarily interested in _implementing_ algorithms that operate over these subjects, mathematicians are primarily interested in _stating and proving properties_ of our subjects.
Mathematical proof, therefore, is our primary activity in this course.

There are two broad classes of proof we will employ in this course:

+   **Constructive proof** arises whenever we can prove a property by building a thing.
    This may be a concrete object, _e.g._, a machine that obeys a particular property, or a more abstract object, _e.g._, an execution trace demonstrating that a machine accepts some input.
+   **Classical proof**, specifically **proof by contradiction**, arises whenever we want to prove the _absence_ of some thing.
    For example, we might want to show that there does not exist a machine that fulfills a certain property.
    Provided that there are an infinite number of possible machines, we cannot exhaustively check that every machine does not fulfill the property in question.
    Instead, we argue by contradiction: (1) supposing that such a machine exists, and (2) showing that a logical contradiction arises from this assumption.

Of special interest to us as computer scientists are constructive proof.
Aconstruction of an abstract object that fulfills a property is really an _algorithm_ for building objects that satisfies those properties.
Thus, the study of constructive proof allows us to unite our two perspectives, programmer and mathematician, on the theory of computation.

Regardless of the technique employed, all of our reasoning must obey the following mantra:

> **Go to definition!**

That is, our reasoning must be rooted in the formal definitions of the objects involved.
For example, we will write down precisely what a machine contains.
Therefore, when we write a constructive proof involving such machines, we will need to specify all of the machines' components in some form or another.

In preparation for today's class,

+   (Re-)read Sipser §0.3 to review the structure and design of mathematical proof.
    We'll also have more to say about the process in class.
+   Try proving this following fact about graphs on your own.
    Challenge yourself to write as formal of a mathematical proof as possible.

<div class="definition">
**Definition ($k$-colorability)**: let a _coloring_ of a graph $G = (V, E)$ be a function $f : V \rightarrow C$ from the vertices $V$ of $G$ to an abstract finite set of colors $C$ such that vertices connected together by an edge from $E$ have distinct colors.
Call a graph $k$-colorable if there exists such a set of colors $C$ and coloring function $f$ with $|C| = k$.
</div>

<div class="definition">
**Definition (Cycle)**: a _cycle_ in a graph $G$ is a sequence of vertices $v_1, v_2, \ldots, v_k$ of $G$ such that each adjacent pair of vertices $v_i$ and $v_{i+1}$ are connected by an edge in $E$ and $v_k$ and $v_1$ are also connected by an edge.
</div>

<div class="claim">
**Claim**: If a graph contains an odd-length cycle, then it is _not_ 2-colorable.
</div>
