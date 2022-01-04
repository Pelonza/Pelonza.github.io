---
title: Interpreting Definitions
layout: content
mathjax: true
---

For our labs, you will work with a _designated study group_ of 2--3 people throughout the week.
You will turn in a single lab write-up for each lab for your entire group.
I recommend that you designate one person in your group for writing up your solutions, turning them in, and sending everyone a copy of the final version for their records.
Note that all labs for a given week are due on the _Saturday_ of the week, giving you time to coordinate with your partners to finish up work if you need additional time.

To turn in a lab assignment, you should submit a PDF containing your responses to the relevant assignment on Gradescope.
You may use LaTeX for generating this PDF (as well as any other deliverables for this course).
If you are unfamiliar with LaTeX, you may either pick up LaTeX from an appropriate tutorial such as the one found on [Overleaf](https://overleaf.org) or [Wikibooks](https://en.wikibooks.org/wiki/LaTeX) or you may want to try using [Markdown](https://markdownguide.org) with appropriate extensions for rendering math instead.
I use Markdown to write all of the material that you see on this course website.
For more information on how to set up an environment for writing Markdown, see this supplementary reading from my CSC 208 course:

+   [Markdown]({{ "/readings/markdown.html" | relative_url }})

## A Note on Collaborative Learning

While this is a mathematics-oriented course, group work is essential to help you develop your understanding of the material.
When approaching group work, try not to work individually and then compare answers at the end!
Instead, consider the following strategies for making collaboration on these problems more beneficial to you and your partner:

+   Vocalize your thought process to your partner.
    Try to explain what you are thinking about using words or pictures.
+   If something your partner says confuses you, or you don't understand what's going on, ask a question!
    Remember that good mathematics is elegant and simple; you help your partner by forcing them to try to explain things in such a manner.
+   If you feel like your partner is slowing down your progress, keep in mind that (a) lab work is not a race! and (b) trying to help a peer get through the material helps clarify and reinforce the material for yourself as well!

# Problem 1: Linguistic Manipulation

As an exercise in reading, exploring, and understanding definitions, let's analyze a definition we will see next week when we study regular languages, the _star operator_.

::: definition
**Definition (Star Operator)**: Let $\Sigma$ be an alphabet.
Then $\Sigma^*$ is the set of all possible strings formed from letters drawn from $\Sigma$:

$$
\Sigma^* = \{\, x_1 x_2 \cdots x_k \mid k \geq 0, \forall i \in [1, k] \ldotp x_i \in \Sigma \,\}.
$$
:::

1.  Let $\Sigma = \{\, 0, 1 \,\}$.
    Give three examples of strings found in $\Sigma^*$.
2.  Let $\epsilon$ (lowercase Greek epsilon) be the empty string, _i.e._, the string with no characters.
    Is $\epsilon \in \Sigma^*$?
    Why or why not?
3.  What is the size or _cardinality_ of $\Sigma^*$.
    Justify your answer in a sentence or two.
4.  Does your answer to the previous part hold for _any_ choice of $\Sigma$?
    If so, justify your answer in a sentence.
    If not, provide a counterexample $\Sigma$ where your answer to the previous part does not hold.
5.  Does $\Sigma^* = \emptyset$ for some alphabet $\Sigma$?
    If so, give an example $\Sigma$ where this holds.
    Otherwise, justify your answer in a sentence.

# Problem 2: Distinguishability

In this problem, we'll consider a property related to strings, _distinguishability_.
While this concept will become useful to us when we discuss irregularity in a few weeks, its formal definition serves as a useful exercise in breaking part and analyzing mathematics.

::: definition
**Definition (Distinguishability)**: Let $L$ be a set of strings and $x$ and $y$ be strings (not necessarily in $L$).

+   We say that $x$ and $y$ are _distinguishable by $L$_ if there exists a string $z$ (also not necessarily from $L$ itself) such that exactly one of $xz$ and $yz$ are in $L$.
+   We say that $x$ and $y$ are _indistinguishable by $L$_ if they are not distinguishable.

Furthermore, if $x$ and $y$ are strings drawn from $L$ and are indistinguishable, we write $x \equiv_L y$.
:::

(_N.B._, we use $L$ as the variable for our set of strings because we will eventually call this set our _language_ once we introduce finite automata.)

1.  Let $\Sigma = \{\, a, b \,\}$ and $L_1 = \{\, abba, baba, aabb, bbbb \,\}$.
    Give an example pair of strings that is distinguishable by $L_1$ and a pair of strings that are indistinguishable by $L_1$.
    (_Hint_: again, note that these strings need not necessarily be in $L_1$.)

2.  Now let $L_2$ be the infinite set of strings where the first and last characters are different:

    $$
    L_2 = \{\, w \mid w \in \Sigma^*, w = x_1 \cdots x_k, x_1 \neq x_k \,\}
    $$

    Construct two examples of pairs of strings that distinguishable and three pairs of strings that are indistinguishable by $L_2$.

3.  Using the intuition you built up from the previous part, try to describe what it means to be _indistinguishable_ at a high-level in a sentence or two.

4.  **(Optional)** Recall the definition of equivalence relation from the reading.
    Argue why the indistinguishability relation $(\equiv_L)$ is an equivalence, appealing to the formal definition of an equivalence relation.
    If you'd like, also formally prove this fact.
