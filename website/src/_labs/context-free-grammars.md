---
title: Context-free Grammars
layout: content
mathjax: true
---

# Problem 1: The Basics

(Adapted from Sipser 2.3.)
Answer each part for the following context-free grammar $G$ with start symbol $R$.

\begin{align*}
R \rightarrow&\; XRX \mid S \\
S \rightarrow&\; aTb \mid bTa \\
T \rightarrow&\; XTX \mid X \mid \epsilon \\
X \rightarrow&\; a \mid b
\end{align*}

1.  What are the variables of $G$?
2.  What are the terminals of $G$?
3.  Give three strings in $L(G)$.
4.  Give three strings *not* in $L(G)$.
6.  Consider the string $XXX$.
    Show via a derivation that $XXX \overset{*}{\Rightarrow} aba$.
5.  Consider the string $T$.
    Show via a derivation that $T \overset{*}{\Rightarrow} aba$.
7.  Consider the string $T$.
    Show via a derivation that $T \overset{*}{\Rightarrow} XX$.
7.  Consider the string $R$.
    Show vi a derivation that $R \overset{*}{\Rightarrow} aabbb$.
8.  Give a description in English of $L(G)$.

# Problem 2: Conditional Ambiguity

In C-like programming languages, conditional statements frequently have the following form:

~~~
expr -> true | false | ...
stmt -> if expr then stmt | if expr then stmt else stmt | skip | ...
~~~

(The `skip` statement is a statement that does nothing.
For our purposes, it acts as a "base case" to the $stmt$ production.
You could substitute any "real" base statement such as a call to a function, *e.g.*, `printf()` instead.)

1.  Give a string and two parse trees demonstrating the ambiguity of this grammar.
2.  Which of the two parse trees is the "preferred" interpretation?

3.  Translate your toy example to an equivalent C program and try it out, *e.g.*, with `gcc` or `clang`.
    Which of the two parse trees is the one that your chosen compiler produces?

4.  Change the grammar above to remove the ambiguity.
    You may try to preserve the original syntax of the conditional statement, but you may also add additional syntax to remove the ambiguity.
    Your solution should be as faithful to good C programming practices as possible.
