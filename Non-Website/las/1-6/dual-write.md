(Prove closure and algorithmic properties of Turing machines.)

Let a _Dual-head Turing Machine_ (DHTM) be a (deterministic) Turing Machine that possesses two tapes and two tape heads. Both tape heads start on the left-hand side of the tapes and the input is written to the first tape only. The second tape starts with blank tape cells.

On a step of computation, a DHTM reads from both tape cells, writes to both tape cells, and moves the tape heads in the _same_ direction, either left or right. Formally define the transition function of a DHTM as:

$$
\delta : Q \times \Gamma \times \Gamma \rightarrow Q \times \Gamma \times \Gamma \times \{\, L, R \,\}
$$

Given a DHTM $$D$$, build a Turing machine $$M$$ that recognizes the same language as $$D$$.

(_Hint_: how can you simulate the dual-head nature of the DHTM by enhancing the tape alphabet of the Turing machine?)

|___|
