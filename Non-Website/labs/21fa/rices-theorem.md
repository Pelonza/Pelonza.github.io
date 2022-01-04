---
title: Rice's Theorem
layout: content
mathjax: true
---

$$
\newcommand{\desc}[1]{\langle #1 \rangle}
$$

In this problem, we'll walk through and complete a proof of Rice's Theorem which was introduced in the reading.

Let $P$ be a language whose strings are Turing machine descriptions that satisfy an arbitrary predicate $f$, _i.e._,

$$
P = \{\, \desc{M} \mid f(M) \,\}
$$

(_Note_: throughout this lab, $P$ will refer to this Turing machine, not the complexity class $P$!)

where $f$ is a proposition ranging over Turing machine descriptions.
For example, the following are propositions over a Turing machine, call it $M$:

+   $L(M)$ is finite.
+   $M$ writes a `$` on its tape for some input.

Rice's Theorem demands two properties are true about $P$.

+   $P$ is non-trivial: there exists $M_1$ and $M_2$ such that $\desc{M_1} \in P$ and $\desc{M_2} \notin P$.
+   $P$ is a language property: if $L(M_1) = L(M_2)$ then $\desc{M_1} \in P \Leftrightarrow \desc{M_2} \in P$.

# Problem 1: Language Property Example

Let's first check that we understand what we mean by "language property".

Let:

$$
P = \{\, \desc{M} \mid \text{$M$ writes a `\$' on its tape for some input.} \,\}.
$$

With your group, ultimately discuss and answer why $P$ _does not_ fulfill the definition of language property.
Make sure to appeal to the above definition of language property in your argument.

# Problem 2: Core Reduction

Now let's proceed with the core of the proof of Rice's theorem.
First we'll complete the core reduction under a set of assumptions about our property $P$.
We'll then discuss after the fact why these assumptions are sound given the constraints of Rice's theorem.

Assume the following:

+   There exists a TM $T$ such that $\desc{T} \in P$.
+   Define the TM that rejects all strings to be $T_{\emptyset}$.
    Assume that $\desc{T_{\emptyset}} \notin P$.

Use $T$ to construct a mapping reduction from $A_\mathsf{TM}$ to $P$.
Keep in mind the following insights while constructing your mapping reduction:

+   Your mapping construction, when given an input to $A_\mathsf{TM}$ of the form $\desc{M, w}$ should produce a TM $\desc{M'}$ with the property that $M$ accepts $w$ iff $\desc{M'} \in P$.
+   Note that we have asserted that (a) a machine $T$ exists that is in $P$ and (b) the machine that rejects all strings $T_\emptyset$ is not in $P$.
    Use these as the targets for your mapping function as described in "Undecidable Proof Strategies" handout.

Once you have a candidate reduction, check your answer with the course staff.

# Problem 3: The First Constraint

With the reduction completed, we need to show where the two constraints came from.
Let's briefly talk about the first constraint.

In a few sentences, explain why the constraints of Rice's Theorem on $P$ imply that there exists a TM $T$ such that $\desc{T} \in P$.

# Problem 4: The Final Fix-Up

The second constraint is really an assumption "without loss of generality".
In other words, even if $T_\emptyset \in P$, we can still complete the proof with a little bit inconsequential fix-up to our proof.
Note that we can't simply work with $T_\emptyset$ directly in this case because our mapping reduction will fail in a style similar to $E_{TM}$.
We instead need to do something else.

It turns out that the fix-up is to consider instead the complement of $P$:

$$
\overline{P} = \{\, \desc{M} \mid \desc{M} \notin P \,\}.
$$

The reduction above then holds, but shows that $A_\mathsf{TM} \leq_m \overline{P}$ rather than $P$.

Determine how a decider for $\overline{P}$ could be used to create a decider for $P$, allowing us to conclude that $A_\mathsf{TM} \leq \overline{P}$ as well.
Check your reasoning for this and the previous part with the course staff when you are done.
