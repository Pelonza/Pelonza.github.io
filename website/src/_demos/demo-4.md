---
title: "Demonstration Exercise #4"
layout: content
mathjax: true
---

# Problem 1: Irregularities

Consider the following language $L$:

$$
L = \{\, x^i y^j z^k \mid k = i + j \,\}.
$$

a.  Prove that $L$ is irregular with the pumping lemma.
b.  Prove that $L$ is irregular using the Myhill-Nerode theorem.

# Problem 2: Don't Judge a Book

In are study of finite automata, we have come to realize that the states of our automata constitute the "memory" of our computation.
Some computations require very little memory.
Others, however, require a large amount of memory.
Regardless, if that memory requirement is _bounded_, we can write a finite automata that performs that computation.

For the remaining problems, we will analyze the following family of languages over $\Sigma = \{\, 0, 1 \,\}$.

$$
L_n = \{\, w \mid w \in \Sigma^*, \text{the \( n \)th to the last character of \( w \) is a \( 1 \)} \,\}.
$$

For example $L_3$ is the set of strings where the third-to-the-last character is a $1$ and $L_1$ is the set of strings where the last character is a $1$.

First, let's see why these family of languages might be more complicated than they seem at first glance.
Let's consider $L_2$, the set of strings where the second-to-the-last character is a $1$.
Here is a DFA $D$ that attempts to recognize $L_3$.

![A DFA $D$ that attempts to recognize $L_3$]({{ "/img/nth-last-01.png" | relative_url }})

While this DFA works in some cases, it doesn't work in all of them!
Analyze $D$ and find an example string that $D$ rejects but should be accepted.
Give an execution trace of this string on $D$ to demonstrate that $D$ has the wrong behavior on it.
Based off of you example, describe what is wrong with $D$ in a sentence or two.

# Problem 3: Nondeterminism to the Rescue!

While seemingly tricky, nondeterminism allows us to quickly implement machines that recognize this family of languages.
Give NFAs that recognize $L_1$, $L_2$, and $L_3$ that employ nondeterminism to "guess" when we have seen the last $n$ characters of the input.
Your NFAs should follow a common pattern of implementation such that $L_n$ takes $n+1$ states to implement as a NFA.

# Problem 4: Back to DFAs

Of course, nondeterminism is a theoretical device, so it is useful to bring our constructions "back to reality" by converting our NFAs to DFAs.
Use the _subset construction_ technique to convert each of your NFAs for $L_1$, $L_2$, and $L_3$ into DFAs.
You should also notice a pattern to the number of subset states that actually participate in each of your DFAs, _i.e._, are reachable from the starting state.

# Problem 5: By Hand

The pattern that you saw in the previous problem suggests a troubling trend: we need an exponential number of states to capture $L_n$!
But of course, the subset construction, by virtue of being general, may include extraneous states that we could simplify away with direct implementation strategies.

To explore this idea, build a DFA for $L_2$ (strings where the second-to-last character is a $1$) independent of the NFAs/DFAs from the previous problems.
For each state of your DFA, describe an invariant/property associated with that state that eventually implies correctness of the overall machine.

(_Hint_: to do this, consider how much of the input do you have to _remember_ in order to carry out the computation faithfully.
Call this subset of the input a _window_ and then formulate your state invariants in terms of these windows.)

# Problem 6: Bounds

You should observe that the DFA you derived by-hand in problem 5 is identical to the DFA you generated in problem 4 for $L_2$!
This suggests that _we can do no better_ than an exponential number of states for this class of problems.
We can state this formally as follows:

::: proof
**Claim**: any DFA $D$ that recognizes $L_n$ has _no fewer_ than $2^n$ states.
:::

Use ideas behind the Myhill-Nerode theorem to prove that this claim is true.

(_Hint_: think about the invariants you developed in the previous problem.
Think of them as sets of strings, predict how many such sets/invariants you need for $L_n$, and argue why these sets form equivalence classes for $L_n$.)
