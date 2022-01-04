---
title: "Closure Problems"
layout: content
mathjax: true
---

# Problem: Reversal

The _reverse_ of a language $L$, written $L^R$, is defined as follows:

$$
L^R = \{\, x_k \cdots x_1 \mid x_1 \cdots x_k \in L \,\}.
$$


1.  Give a proof sketch (high-level proof description) that complement is closed under the regular languages.
    In particular, which language model would you use to prove closure in this case?
    At a high-level, how do you transform an instance of this model into one that recognizes its reversal?
2.  Formally prove that if $L$ is regular, then $L^R$ is also regular.

# Problem: Complement

The *complement* of a language is defined to be the set of strings *not* in the language:

$$
\overline{L} = \{\, w \mid w \notin L \,\}.
$$

1.  Give a proof sketch (high-level proof description) that complement is closed under the regular languages.
    In particular, which language model would you use to prove closure in this case?
    At a high-level, how do you transform an instance of this model into one that recognizes its complement?
2.  Formally prove that if $L$ is regular, then $\overline{L}$ is also regular.
