(Prove that a problem is NP-complete by way of a reduction.)

Recall the following problems over undirected graphs:


+   Hamiltonian path: $$\mathsf{HAMPATH} = \{\, \langle G, x, y \rangle \mid \text{There is a path from \( x \) to \( t \) in \( G \) that visits every node exactly once} \,\}$$.
+   Longest paths: $$\mathsf{LPATH} = \{\, \langle G, x, y, t \rangle \mid \text{There is a path from \( x \) to \( t \) in \( G \) of length at least \( t \)} \,\}$$.

Show that $$\mathsf{HAMPATH} \leq_p \mathsf{LPATH}$$. Make sure to argue both sides of the correctness condition of your reduction.

(_Hint_: what is the relationship between the length of a Hamiltonian path and the number of vertices in $$G$$?)

|___|
