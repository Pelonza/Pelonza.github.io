---
title: Nondeterminism
layout: content
mathjax: true
---

# Problem 1: Interpretation

![Example NFAs]({{ "/img/nfas.png" | relative_url }})

a.  Determine whether the strings:
    +   $101$
    +   $0111$
    +   $1010$
    +   $\epsilon$

    Are accepted by the NFAs above.

b.  Give a formal description of the languages that each of the NFAs above recognize.


# Problem 2: Nondeterministic Design Patterns

Construct an NFA that productively takes advantage of nondeterminism to recognize each of the following languages.
In the following languages, $\Sigma = \{\, 0, 1 \,\}$.

+   **Guessing**: $L_1 = \{\, x \mid x \in \Sigma^*, \text{$x$ contains $01010$} \,\}$.
+   **Language Union**: $L_2 = \{\, x \mid x \in \Sigma^*, \text{$x$ has an odd number of $0$s or ends in three $1$s} \,\}$.
    (_Hint_: build machines that recognize "odd $0$s" and "ends in three $1$s" separately and then combine them with nondeterminism!)

# Problem 3: Infinite Nicolas Cages?

Consider the following partial NFA that features an "epsilon loop."
The remainder of the NFA does some computation on $q_0$ which is irrelevant for our purposes.

~~~
  ┌───ϵ───┐
  ↓       │
→ q0 -ϵ→ q1
  │
  └── ⋯
~~~

And consider the following critique of this construction:

> This NFA is impossible!
> The epsilon loop will spawn an infinite number of threads of execution!

Explain in a few sentences why such a situation is "ok" by appealing to the formal definitions of a NFA.

(_Hint_: do the definitions prescribe how we should execute a NFA?)
