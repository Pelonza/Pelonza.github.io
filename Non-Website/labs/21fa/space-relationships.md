---
title: Space Relationships
layout: content
mathjax: true
---

# Problem 1: Configurations

Consider a Turing machine with $q$ states and $g$ possible tape symbols.
Write down an expression for the number of possible configurations of this Turing machine with a tape size of $n$.
Explain your expression in a sentence or two.

# Problem 2: Cycles

Prove the following fact regarding halting Turing machines and configurations:

::: proof
**Claim**: A Turing machine that halts does not repeat a configuration.
:::

# Problem 3: Upper Bounds

Observe that if a language is in $\text{PSPACE}$ then a Turing machine that recognizes it uses a polynomial amount of space.
Use your results from the first two problems to prove the following claim:

::: proof
**Claim**: $\text{PSPACE} \subseteq \text{EXPTIME}$.
:::

(_Hint_: establish the number of configurations of such a Turing machine and use the previous problem's claim to establish an upper-bound on the number of steps the Turing machine.)
