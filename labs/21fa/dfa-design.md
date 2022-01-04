---
title: DFA Design
layout: content
mathjax: true
---

In this lab, we will go over the basic patterns of automata design that you will see through your study of the theory of computation.
Studying these patterns should:

+   Reinforce your knowledge of how finite automata operate.
+   Give you a toolbox of fundamental patterns for designing automata.
+   Give you a sense of what is possible and what is not possible with finite automata.

For each language $L_1$ through $L_7$, build a DFA that recognizes that language.
Throughout, $\Sigma = \{\, 0, 1 \,\}$.

+   **Emptiness**: $L_1 = \emptyset$, _i.e._ the empty set of strings.
+   **Everything**: $L_2 = Σ^*$, _i.e._, the set of all possible strings.
+   **Constants**: $L_3 = \{\, 0110 \,\}$, the singleton set containing the string $0110$.
+   **Prefixes and Suffixes**: $L_4 = \{\, 01x10 \mid x \in \Sigma^* \}$.
+   **Parity**: $L_5 = \{\, x \mid x \in \Sigma^*, \text{$x$ has an even number of 0s} \,\}$.
+   **Counts**: $L_6 = \{\, x \mid x \in \Sigma^*, \text{$x$ contains three $1$s} \,\}$.
+   **Constraints**: $L_7 = \{\, x \mid x \in \Sigma^*, \text{$x$ does not contain $01$} \,\}$.
