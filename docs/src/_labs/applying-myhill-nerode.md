---
lab: Applying Myhill-Nerode
layout: content
mathjax: true
---

# Problem 1: Equivalence Classes

Intuitively, we can think of the equivalence classes induced by $\equiv_L$ to be sets of string _prefixes_ that all share the same acceptance or rejection behavior.
As the Myhill-Nerode theorem tells us, each equivalence class is, itself, equivalent to a state of a DFA that recognizes language $L$!
To gain intuition about these equivalence classes, we'll first do some translation between DFA states and equivalence classes.

For each of the following regular languages:

a.  First, give a DFA that recognizes the language.
b.  Then from the states of the DFA, give the corresponding equivalence classes induced by the $\equiv_L$ relation.
    Describe these equivalence classes as a collection of sets of strings where each set corresponds to a class.
    Ensure that your equivalence classes (a) are disjoint, _i.e._, share no strings and (b) cover all possible strings drawn from $\Sigma^*$ although you do not need to formally prove these facts in this problem.

In all cases, the alphabet is over $\Sigma = \{\, 0, 1 \,\}$.

+   $L_1 = \{\, 11x \mid x \in \Sigma^* \,\}$.
+   $L_2 = \{\, w \mid w \in \Sigma^*, \text{\( w \) has an odd number of 0s and an even number of 1s } \,\}$.

We're accustomed to developing DFAs, so going from DFAs to these equivalence classes is a useful exercise to understand the concept.
However, to apply Myhill-Nerode for the purposes of proving _irregularity_ of a language, we will necessarily need to develop the equivalence classes without the aide of a finite automata!

For these two regular languages, proceed in the opposite order:

a.  First, give the corresponding equivalence classes induced by the $\equiv_L$ relation.
    Again, describe these classes as collections of sets of strings.
b.  From your equivalence classes, give a DFA that recognizes the language.

+   $L_3 = \{\, 0x0 \mid x \in \Sigma^* \,\}$.
+   $L_4 = \{\, w \mid w \in \Sigma^*, \text{every odd position of \( w \) is a \( 0 \)} \,\}$.

# Problem 2: Nope, Not Regular, Again

Consider the language $A = \{\, www \mid w \in \Sigma^* \,\}$ with $\Sigma = \{\, 0, 1 \,\}$.
Prove that $A$ is irregular using the Myhill-Nerode theorem.
