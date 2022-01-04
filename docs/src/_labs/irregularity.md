---
title: Irregularity
layout: content
mathjax: true
---

# Problem 1: Pumps

a.  Revisit the first proof of irregularity in the book (example 1.73, pp. 80, $B = \{ 0^n 1^n \mid n ≥ 0 \}$ is irregular).
    For each of the variables introduced in the proof, say whether that variable is *held arbitrary* or *chosen* to be a particular value.

    +   $p$.
    +   $s$.
    +   $x$, $y$, and $z$.
    +   $i$.

b.  In the proof, Sipser chooses the string $0^p 1^p$ to analyze.
    By the conditions of the pumping lemma, draw in the diagram of the string below where $x$, $y$, and $z$ must lie.

    $$
    \underbrace{0\;\cdots\;0}_{p}\;\underbrace{1\;\cdots\;1}_{p}
    $$

    (_Note_: it might be useful to reproduce this diagram in monospace font using a code block and then indicate where x, y, and z exist in the string using ASCII art.)

c.  There are many choices of strings that satisfy the conditions of the pumping lemma, but not all of them lead to contradictions.
    For each of the candidate strings below, determine whether (i) the string satisfies the conditions of the pumping lemma, and if so, (ii) what does the pumping lemma say about the shape of $x$, $y$, and $z$, and (iii) whether we can complete a pumping lemma proof using this string.
    Finally, if you can complete proof with the string, do so.

    +   $0^5 1^5$.
    +   $0^{2p} 1^{2p}$.
    +   $0^{p/2} 1^{p/2}$.

# Problem 2: Nope, Not Regular

Consider the language $A = \{\, www \mid w \in \Sigma^* \,\}$ with $\Sigma = \{\, 0, 1 \,\}$.
Prove that $A$ is irregular with the pumping lemma using the template discussed in class.

# Problem 3: Nope, Definitely Regular (Optional)

(Sipser 1.30).
Consider the language $A = 0^* 1^*$.
The following is an erroneous "proof" that $A$ is irregular.

::: proof
_Proof_.
Assume for the sake of contradiction that $A$ is regular.
Then the pumping lemma applies.
Let $p$ be the pumping length and choose $s = 0^p 1^p ∈ A$.
Observe that $|0^p 1^p| = 2p \geq p$.
Let $s = xyz$ according to the conditions of the pumping lemma.
There are three cases to consider:

1.  The string $y$ only contains $0s$.
    Therefore $xyyz \notin A$ because it has has more $0$s than $1$s.
2.  The string $y$ only contains $1$s.
    Likewise, $xyyz \notin A$ because it has more $1$s than $0$s.
3.  The string $y$ contains a substring of $0$s followed by a substring of $1$s.
    The string $xyyz \notin A$ because the substring $yy$ will be of the form $0^a 1^b 0^a 1^b$ for some constants $a$ and $b$.

In all cases, we arrive at a logical contradiction.
Therefore, our original assumption that $A$ is regular must be false; therefore, $A$ is irregular.

{% include qed.html %}
:::

+   In a few sentences, describe the erroneous step(s) of reasoning in the proof.
+   Prove that $A$ is actually regular.
