(Prove closure and algorithmic properties of Turing machines.)

Let a _No-Move Turing Machine_ (NMTM) be a (deterministic) Turing Machine that can decide on a step of computation to _not move the tape head_. Formally define the type of transition function of such a NMTM to be:

$$
\delta : Q \times \Gamma \rightarrow Q \times \Gamma \times \{\, L, R, N \,\}
$$

Where $$N$$ denotes the choice to not move the tape head.

Prove that NMTMs and Turing Machines are equivalent.

|___|
