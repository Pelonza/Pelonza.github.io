# Problem 1: ☠

1.  The definition does not need to change. The conditions for acceptance does
    not change for a DFA with death.
2.  DFA ⇒ DFA with death. A DFA is already a DFA with death, as the latter is
    simply the former with an expanded codomain for its transition function, ☠,
    as well as additional behavior if a transition sends the machine to ☠.
    However, the transition function of the original DFA is total over $Q$ and
    thus does not mention ☠.

    DFA with death ⇒ DFA. Let D = (Q, Σ, q₀, δ, F) be a DFA with death. Define
    a DFA D' that is equivalent to D as follows:

    D' = (Q ∪ q_d, Σ, q₀, δ', F)

    Where δ' is defined as follows:

    δ'(q_d, a) = q_d for any a ∈ Σ.
    δ'(q, a) = δ(q, a) whenever δ(q, a) ≠ ☠.
    δ'(q, a) = q_d whenever δ(q, a) = ☠.

    In other words, we create a new state q_d in D' that acts as a dead state
    that we transition to whenever we would have transitioned to ☠ in D.


# Problem 2: Embedding

(The mathematical formalization of the embedding is extremely tedious. I am
happy if people capture this high-level description of the construction and the
formalization is _roughly_ there.)

Let N₁ and N₂ be NFAs that recognize L₁ and L₂, respectively. For each state qᵢ
of N₁, define Mᵢ to be an NFA that contains starting state q₀ as well as a copy
of both N₁ and N₂. In Mᵢ, q₀ ϵ-transitions to the start states of its copy of
N₁. and each accepting state of its copy of N₂ ϵ-transitions to qᵢ in its copy
of N₁. The accept states of each Mᵢ are the accept states of its copy of N₁.

The NFA that recognizes L₁ ↶ L₂ is an NFA N that is the combination of a copy
of N₁ and the associated Mᵢ for each of states of N₁. Each state qᵢ of N₁ has
an additional ϵ-transition from it to the start state of Mᵢ. The start state of
N is the start state of N₁. The accepting states of N are the union of the
accepting states found in each copy of N₁ found among the Mᵢ.
