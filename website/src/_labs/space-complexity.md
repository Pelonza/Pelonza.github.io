---
lab: Space Complexity
layout: content
mathjax: true
---

# Problem 1: Developing the Strategy

Review the proof that $\mathsf{SAT}$ is in $\text{PSPACE}$ (Example 8.3).
In a sentence or two, describe how the construction captures the exponential nature of the search space using a polynomial amount of memory.

# Problem 2: Space!

Next prove that the following problems are in $\text{PSPACE}$:

a.  $\mathsf{CLIQUE} = \{\, (G, k) \mid \text{\( G \) has a \( k \)-clique} \,\}$.
b.  $\mathsf{SUBSET} = \{\, (S, t) \mid \text{\( S \) is a set, \( t \in \mathbb{N} \), and there exists a \( S^* \subseteq S \) such that \( \sum_{x \in S^*} x = t \).} \,\}$.

# Problem 3: Generalization

Now that you've had some experience thinking about how $\text{PSPACE}$ algorithms work, let's generalize our constructions.
At this point, you should observe that there seems to be a pattern for every $\text{NP}$ problem and realizing it as a $\text{PSPACE}$ algorithm.
This pattern is similar to the verifier-to-NTM direction of the proof of Theorem 7.20 (pp. 294).

Adapt this direction of the proof to formally prove that $\text{NP} \subseteq \text{PSPACE}$.

(_Hint_: the definition of $\text{NP}$ says that you start with a verifier for the problem.
You must then build a polynomial space algorithm for the problem using this verifier.
What do you use your polynomial space to "remember?")
