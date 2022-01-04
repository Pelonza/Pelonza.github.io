---
title: Regular Expressions
layout: content
mathjax: true
---

# Problem 1: Sugar

Definition 1.52 of Sipser gives the formal definition of a regular expression.
You might notice that this includes a minimal set of operators compared to a real-world regular expression language.
The set of additional operators found in these real-world languages are not essential; indeed, with a little bit of thought, we can use the minimal set to emulate these extended operators.

For each of the given extended regular expression operators, give an equivalent regular expression using the operators defined in Sipser.

1.  $R+$: matches one or more occurrences of $R$.
2.  $R?$: matches zero or one occurrences of $R$.
3.  $[c_1 \cdots c_k]$: matches exactly one occurrence of any of the characters $c_1$, ..., $c_k$.
4.  $n\{R\}$: matches $n$ repetitions of $R$.
5.  $R\$$: matches any string that ends with $R$.

# Problem 2: Awkward

(*Adapted from Sipser exercise 1.6.*)

Give DFAs/NFAs and regular expressions for each of the following
languages. In all cases, $\Sigma = \{ 0, 1 \}$.

+   $L_1 = \{\, w \mid \text{$w$ does not contain $01$ or $101$} \,\}$.
+   $L_2 = \{\, w \mid \text{$w$ starts with $0$ and has odd length or starts with $1$ and has even length} \,\}$.
