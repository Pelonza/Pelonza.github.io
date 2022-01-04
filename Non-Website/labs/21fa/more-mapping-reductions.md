---
title: More Mapping Reductions
layout: content
mathjax: true
---

$\newcommand{\NP}{\mathsf{NP}\xspace}\newcommand{\desc}[1]{\langle #1 \rangle}$

# Problem 1: Graph Reductions

Consider the following graph problem, _independent set_:

$$
\mathsf{INDSET} = \{\, \desc{G, k} \mid \text{\( G \) has a \( k \)-vertex independent set} \,\}.
$$

An _independent set_, is a subset of the vertices of a graph where no pair of vertices in the independent set have an edge between them.

Like the previous lab, let's go through a systematic process for proving this claim.

a.  First, **explore the problem space**.
    Come up with two examples of instances of $\mathsf{INDSET}$, one where there is a vertex cover and one where there is not a vertex cover.
b.  Next, **show that $\mathsf{INDSET} \in \NP$**.
c.  Now, **identify the inputs to $\mathsf{CLIQUE}$ and $\mathsf{INDSET}$**.
d.  With this, **identify the inputs and outputs of the reduction function** we must design as well as the **correctness condition** for that reduction function based on its type.
e.  To begin designing the reduction function, let's first **decompose the inputs and outputs of the reduction function into components** that we can attempt to draw associations between.
f.  Now, onto exploration of designs.
    In the previous lab, we essentially "forced" $\mathsf{PUZZLE}$ to solve $\mathsf{3SAT}$.
    However, this perspective on designing the reduction will not be as fruitful with these problems even though they operate on the same domain.
    To make forward progress, I encourage you to instead consider how $\mathsf{CLIQUE}$ and $\mathsf{INDSET}$ are actually _the same problem_.
    More concretely, I recommend looking at the definition of clique and independent set and analyzing their relationship with each other.

    Just like the previous lab, **come up with at least two potential designs** for the reduction function and **push them through on a toy $\mathsf{CLIQUE}$ instance**.
    For each design that does not work, describe what was broken and how you could potentially fix it.

    (_Hint_: it might be useful to think about _graph complements_ for this reduction.)
g.  Finally, once you have a plausible reduction strategy, formally prove that $\mathsf{CLIQUE} \leq_p \mathsf{INDSET}$.

# Problem 2: More Graph Reductions

Here is another $\NP$-completeness problem for you to consider, following the trajectory of Karp and his 21 $\NP$-complete problems:

$$
\mathsf{SETPACK} = \{\, \desc{\mathcal{U}, S, k} \mid \text{\( S \) is a family of subsets of \( \mathcal{U} \), there is a set packing of $S$ of size at least $k$.} \,\}.
$$

A _set packing_ of size $k$ is a family $S$ of subsets of $\mathcal{U}$ with $|U| \geq k$ that are pairwise disjoint, _i.e._, no sets share an element in common.
Clearly, the empty set is a valid set packing for any set---instead, we are interested in maximizing the size of the set packing while obeying the restriction that no pairs of sets in the packing share a common element.

As with the previous lab questions, systematically work through the process of showing that $\mathsf{SETPACK}$ is indeed $\NP$-complete.
In your deliberations, you should plan to reduce the $\mathsf{INDSET}$ problem to $\mathsf{SETPACK}$.

(_Hint_: here, the first perspective on reductions will be more useful.
Force $\mathsf{SETPACK}$ to solve a $\mathsf{INDSET}$ instance for you.)
