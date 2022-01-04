---
title: Diagonalization
layout: content
mathjax: true
---

# Problem 1: Countability

a.  Prove that the language $L = \Sigma^*$ where $\Sigma = \{\, 0, 1 \,\}$ is countably infinite.

    (_Hint_: simply declaring that the mapping from $\Sigma^*$ to $\mathbb{N}$ is the binary interpretation of $w \in \Sigma^*$ is insufficient since $0$ and $000$ are distinct strings but both represent the value zero.
    The resulting mapping would, therefore, not be a bijection!}
b.  Generalize your construction to any \( \Sigma \) of finite size.
c.  Use this fact to argue that the set of possible Java programs is countably infinite.

# Problem 2: Hey, Wait a Second

Consider the following proof that $\mathbb{N}$ is uncountable.

::: proof
_Proof_.
Assume that $\mathbb{N}$ is countable.
Then there is a bijection $f$ that covers every natural numbers in $\mathbb{N}$.
Construct the natural number $n$ where the $i$th digit of $n$ is the $i$th digit of the $i$th natural number in the bijection (_i.e._, $f(i)$) plus one mod 10 (so that it is a decimal digit).
That is, if $k$ is the $i$th digit of the $i$th natural number, then the $i$th digit of $n$ is given by $k + 1 \mod 10$.
$n$ is a valid natural number and by construction, $n$ differs from every natural number in the bijection by one digit.
Therefore, $n$ cannot be in the bijection and therefore our assumption that such a bijection exists is incorrect.
Thus, $\mathbb{N}$ is uncountable.
:::

However, we already know that $\mathbb{N}$ is countable (the bijection is the identity function).
What is wrong with this proof?

(_Hint_: think about the assumptions latent in Cantor's diagonalization argument that the reals are uncountable.
What specifically is different in this case?}

# Problem 3: Running the (Diagonal) Line

Consider the following language:

$$
\mathsf{HALT}_\mathsf{TM} = \{\, (M, w) \mid \text{Turing machine \( M \) halts on input \( w \)} \,\}.
$$

By "halts", we mean that the Turing machine either accepts or rejects.
Adapt the diagonalization proof that $A_\mathsf{TM}$ is undecidable from the end of chapter 4.2 to show that $\mathsf{HALT}_\mathsf{TM}$ is undecidable.
In a few sentences, describe how the diagonalization matrix figure 4.21 changes when adapted to your new proof.
