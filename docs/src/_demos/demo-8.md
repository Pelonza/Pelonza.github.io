---
title: "Demonstration Exercise #8"
layout: content
mathjax: true
---

# Problem 1: Chicken and Rice

a.  Use Rice's Theorem to show the following language is undecidable:

    $$
    L_1 = \{\, M \mid \text{\( M \) is a TM and \( 010 \in L(M) \)} \,\}.
    $$

b.  Is the following language undecidable according to Rice's Theorem?
    Explain in a sentence or two.

    $$
    L_2 = \{\, M \mid \text{\( M \) is a TM and on some input, \( 010 \) exists on the tape at some point} \,\}.
    $$

# Problem 2: Scheme Is Real, Right?

a.  Consider the problem of determining whether the branches of an arbitrary if-expression in Scheme, _i.e._, a problem of the form `(if b e1 e2)`, produces the same type of value (_e.g._, only integers or strings).
    For example, this property is:

    +   True of `(if b 0 1)`.
    +   False of `(if b 5 #t)`.
    +   True of `(if b (if #t 0 "hi") 1)` (because we are only checking the branches of the top-level conditional).

    Note that the content of the guard `b` in these cases is irrelevant because we want to know whether the types of values of each branch are the same, _irrespective of whether we go into either of the branches on any choice of `b`_.

    Formulate this problem as a language and show that this problem is undecidable.
    For this problem, you may assume:

    +   The existence of a Scheme function `run-tm` that takes a Turing machine description $M$ and input $w$ and returns `#t` if $M$ accepts $w$ and `#f` if $M$ rejects $w$.
    +   The "type" of the value "produced" by the infinite loop is the "bottom" type, $\bot$.
        In the context of this proof, $\bot$ has type $a$ for any $a$ so that if were able to establish that a branch of computation had type $\bottom$, that branch has some _unknown_ type $a$ that is not necessarily equal to any particular concrete type we have in mind.
b.  Now consider the fact that a computer program on a 64-bit machine runs with $2^{64}$ bits of memory.
    Show that the halting problem for such computer programs is decidable.
    Make sure to argue the (a) correctness and (b) termination of your algorithm.

    (_Hint_: consider the decidability proof of $A_{\mathsf{LBA}}$.)
c.  The answers to the two previous parts seem to be at odds.
    In a few sentences, describe the critical difference between the two cases that makes the first part undecidable but the second part decidable.
d.  Finally with all this in mind, it seems like that undecidability is merely a theoretical device.
    However, it does have important practical implications!  In a few sentences, describe these practical implications---if we feel the need to solve some variant of the halting problem for a computational device, what must we keep in mind and how should we approach the problem?
