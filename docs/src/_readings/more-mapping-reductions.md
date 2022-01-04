---
title: More Mapping Reductions
layout: content
mathjax: true
---

$\newcommand{\NP}{\mathsf{NP}\xspace}$

# Problem: Graph Reductions

Here is an additional NP-completeness problem, this time concerning graph problems for you to consider:

---

Define the following problems:

\begin{align}
\mathsf{CLIQUE} = \{ \desc{G, k} \mid \text{ $G$ has a $k$-clique } \} \\
\mathsf{COVER}  = \{ \desc{G, k} \mid \text{ $G$ has a $k$-vertex cover } \}
\end{align}

A $k$-clique is a $k$-complete subgraph of $G$.
A $k$-vertex cover is a $k$-sized subset of vertices of $G$ that cover (_i.e._, are \emph{incident} with) all the edges of $G$.
Assume that \mathsf{CLIQUE} is $\NP$-complete.
Show that \mathsf{COVER} is $\NP$-complete.
  
---

Proceed similarly to the previous lab:

1.  First write at least two examples of $\mathsf{COVER}$ instances