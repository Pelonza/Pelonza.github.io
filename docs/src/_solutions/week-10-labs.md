---
title: Week 10 Lab Solutions
layout: content
mathjax: true
---

# Problem: To Infinity and Beyond

a.  There's an infinite number of strings $w \in \Sigma^*$, so the Turing machine does not terminate if $D_1$ and $D_2$ are not equal.
b.  If we simulate $D_1$ and $D_2$ in a step-by-step, pairwise fashion, we observe there are at most $|Q_1| \times |Q_2|$ states that both machines can be in where $Q_1$ and $Q_2$ are the states of $D_1$ and $D_2$, respectively.
    Any string $w$ with length greater than $|Q_1| \times |Q_2|$ will necessarily enter a loop in either $D_1$ and $D_2$ that would have been encountered early in the simulation of the pair of machines on $w$.
    Thus, if $D_1$ and $D_2$ have differing behavior on $w$ at this point, we would have seen such a deviation early in the string's execution during the first $|Q_1| \times |Q_2|$ steps.
    Therefore, it is sufficient to only test all strings of size at most $|Q_1| \times |Q_2|$, a finite amount.

# Problem: Can You Do It? Yes You Can!

a.  For every accepting state $q$ of $D$, determine if any accepting state of $D$ is reachable from $q$ in one or more steps of execution. If no such accepting state fulfills this property, then no string of $D$ is a prefix of another and so it is prefix-free.
b.  The algorithm for determining prefix-freeness for DFAs fails for TMs when we attempt to determine reachability.
    Reachability demands that we know the contents of the tape which we cannot know in the general case without simulating the TM on a specific input.

# Problem: Countability

a.  Let $⟦w⟧$ be the binary interpretation of $w$ (where leading 0s are ignored).
    Then our bijection from $L$ to $\mathbb{N}$ is:

    $$
    f(w) = 2^{|w|}-2 + ⟦w⟧.
    $$

b.  If $|\Sigma| = n$, and let $⟦w⟧$ be the $n$-ary interpretation of $w$, then we can generalize $f(w)$ to be:

    $$
    f(w) = n^{|w|}-n + ⟦w⟧.
    $$

c.  Observe that a Java program is a string composed from a finite alphabet.
    From (b), we can immediately conclude that there is a bijection between Java programs and $\mathbb{N}$.

# Problem: Hey, Wait Second

Natural numbers are finite sequences of digits whereas real numbers are infinite sequences of digits.
Thus, the string we create from the digitalization process is not a well-formed natural number.

# Problem: Running the (Diagonal) Line

_Proof_.
Assume for the sake of contradiction that $\mathsf{HALT}_{\mathsf{TM}}$ is decidable; let $H$ decide it.
Define Turing machine $D$ that takes another Turing machine $M$ as input as:

+   $D$ = On input $M$:
    -   Run $H$ on inputs $M$ and $\langle M \rangle$.
        -   If $H$ accepts, then go into an infinite loop.
        -   If $H$ rejects, then _accept_.

Now observe what happens when we run $D$ on $\langle D \rangle$.

+   If $D$ accepts $\langle D \rangle$ then it was because $H$ rejected $D$ and $\langle D \rangle$, implying $D$ went into an infinite loop on itself.
+   If $D$ goes into an infinite loop on $\langle D \rangle$ then it was because $H$ accepted $D$ and $\langle D \rangle$, implying $D$ halted on itself.

Both cases induce a contradiction, so our original assumption that $\mathsf{HALT}_{\mathsf{TM}}$ was decidable must be incorrect.

# Problem: It Hurts My Head

In both cases, we reduce from $A_\mathsf{TM}$ with function $f$.

a.  $f(M, w) = M'$ where:

    +   $M'$ = On input $x$:
        -   If $x = 01$, then accept $x$.
        -   Run $M$ on $w$.
            -   If $M$ accepts $w$, then accept if $x = 10$.
            -   If $M$ rejects $w$, then reject.

b.  $f(M, w) = (M_1, w)$ where:
    +   $M'$ is identical to $M$ except that if its alphabet mentions '\$' then rewrite $M'$ to mention $\hat{\$}$ instead.

    +   $M_1$ = On input $x$:
        -   If $x \neq w$ then reject.
        -   Run $M$ on $w$.
            -   If $M$ accepts $w$, then write '\$' on the tape and accept.
            -   If $M$ rejects $w$, then reject.
