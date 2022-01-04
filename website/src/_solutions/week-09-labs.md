---
title: Week 9 Lab Solutions
layout: content
mathjax: true
---

# Problem: Proper Endpoints

A logspace Turing machine that decides $L$ will keep a counter, encoded in binary, that tracks the number of `(` seen.
The input is read left-to-right.
When a `(` is encountered, the counter is incremented.
When a `)` is encountered, the counter is decremented.

During the course of execution, the Turing machine rejects if the counter ever goes negative.
The Turing machine also rejects if the end of the input is reached and the counter is non-zero.
Otherwise, the Turing machine accepts.

# Problem: Problem Complements

a.  The first formula is in $\mathsf{SAT}$.
    For example, the formula is satisified when $x_1$, $x_2$, and $x_3$ are all set to true.
b.  The second formula is in $\overline{\mathsf{SAT}}$.
    Observe that to enable the first two clauses, $x_1$ and $x_2$ must be set to opposite truth values.
    However, if this is the case, then one of the last two clauses cannot be enabled.

# Problem: Verifying Complements

a.  Since $A$ is in $\mathsf{NP}$ we know that there exists a polynomial time verifier $V$ for $A$.
    However, it is not clear how to turn $V$ into a polynomial time verifier for $\overline{A}$.
    If $V(w, c)$ accepts, we can safely reject because this would imply that $w \in A$ and thus $w \notin \overline{A}$.
    However, if $V(w, c)$ rejects, it may not be because $w \notin A$; it may be because the certificate is wrong.
    We would then need to enumerate all the possible certificates $c$ and verify that $V$ rejects all such certificates.
    However, enumerating such certificates requires more than polynomial time.

b.  The reverse direction is similar.
    Answers from a verifier for instances of $\overline{A}$ do not translate into a suitably efficient algorithm for verifying instances of $\overline{A}$

# Problem: Easy Complements

a.  We show both directions of the set equality:

::: proof
**Claim**: $\mathsf{P} \subseteq \mathsf{coP}$.

_Proof_.
Let $A \in P$ and $M$ be a TM that decides $P$.
Modify $M$ to create $M'$ by turning $q_\text{accept}$ into $q_\text{reject}$ and vice versa.
Observe that $L(M') = \overline{A} \in \mathsf{coP}$ and $M'$ runs in polynomial time because it is identical to $M$ except for its acceptance and rejection states.

**Claim**: $\mathsf{coP} \subseteq \mathsf{P}$

Proof.
The proof is identical to the previous case.
:::

b.  Applying this construction to show $\mathsf{NP} = \mathsf{coNP}$ does not work because of the asymmetric nature of nondeterminism.
    Only _some_ branch of a nondeterministic computation must accept for the overall Turing machine to accept.
    However, _all_ nondeterministic branches must fail for the overall Turing machine to fail.
    Because of this, we can't simply flip states---we must conceive of a way to "collect up" all the results of nondeterministic branches and analyze.
    However, nondeterminism does not allow us to share information between branches.

# Problem: Complexity Soup

\begin{gather*}
\mathsf{L} \subseteq \mathsf{NL} = \mathsf{coNL} \subseteq \mathsf{P} \subseteq \mathsf{NP} \subseteq \\
\mathsf{PSPACE} = \mathsf{NPSPACE} \subseteq \mathsf{EXPTIME} \subseteq \mathsf{EXPSPACE}.
\end{gather*}

Here is a canonical complete problem for each class:

+   $\mathsf{L}$-complete: $\mathsf{UPATH}$, determining whether there is a path between two points in an undirected graph.
+   $\mathsf{NL}$-complete: $\mathsf{PATH}$, determining whether there is a path between two points in directed graph (also known as $s$-$t$ connectivity).
+   $\mathsf{P}$-complete: $\mathsf{UNARY{-}BOUNDED{-}HALT}$, determining whether a Turing machine halts on a given input in at most $n$ steps with $n$ given in a unary encoding.
+   $\mathsf{NP}$-complete: $\mathsf{SAT}$, the boolean satisfiability problem.
+   $\mathsf{PSPACE}$-complete: $\mathsf{TQBF}$, the totally quantified boolean satisfiability problem.
+   $\mathsf{EXPTIME}$-complete: $\mathsf{BINARY{-}BOUNDED{-}HALT}$, same as $\mathsf{UNARY{-}BOUNDED{-}HALT}$ but with the input number of steps given in binary.
+   $\mathsf{EXPSPACE}$-complete: $R_{\textsf{eq}\uparrow}$, determining whether two regular expressions involving the exponentiation operator are equal.
