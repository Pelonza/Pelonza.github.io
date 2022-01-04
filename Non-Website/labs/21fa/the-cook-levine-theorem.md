---
title: "The Cook-Levine Theorem"
layout: content
mathjax: true
---

# Problem: Details, Details, ...

Answer the following key questions about the proof of the Cook-Levine theorem that tests our understanding of Turing machines and polynominal-time reductions.

1.  What are the inputs and outputs of the mapping function of the reduction?
2.  Why do the tableaus under consideration have $n^k$ rows?
3.  Why can we bound the size of the tape, _i.e._, the number of columns of the tableau, to $n^k$?
4.  What do the boolean variables $x_{i, j, s}$ represent in the reduction?
5.  In a few sentences each, describe the structure and purpose of the following boolean formulae?

    +   $\phi_\mathsf{cell}$,
    +   $\phi_\mathsf{start}$,
    +   $\phi_\mathsf{move}$,
    +   $\phi_\mathsf{accept}$?

6.  Does a $2 \times 2$ window, _i.e._, two rows and two columns, work?
    Why or why not?
7.  How does the constructed boolean function account for the nondeterminism of the NTM it simulates?
