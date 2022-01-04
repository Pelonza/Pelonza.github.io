(Prove that a problem is NP-complete by way of a reduction.)

Define the $$\mathsf{diffSAT}$$ problem to be identical to the boolean satisfiability problem $$\mathsf{SAT}$$ except that we require that the formula has at least _two distinct satisfying assignments_. Formally:

$$
\mathsf{diffSAT} = \{\, \phi \mid \text{\( \phi \) is a boolean formula with at least two different satisfying assignments} \,\}.
$$

Show that $$\mathsf{SAT} \leq_p \mathsf{diffSAT}$$. You do not have to give a fully symbolic proof, but you should include enough detail in your prose to cover all relevant details. In particular, describing the patterns of boolean formula you create in your reduction would be useful here.

Also note that this is the general satisfiability problem, not $$\mathsf{3SAT}$$. The $$\phi$$ in question is any boolean formula involving literals, their negations, $$(\wedge)$$, $$(\vee)$$, and $$(\neg)$$.

(_Hint 1_: this is a "force"-style of reduction. Force $$\mathsf{diffSAT}$$ to solve $$\mathsf{SAT}$$.)

(_Hint 2_: think of this reduction in steps. First, how will you add additional literals and clauses to $$\phi$$ to allow for two satisfying assignments? Then, how will you enforce that the two satisfying assignments are not identical?)

(_Hint 3_: making a copy of $$\phi$$ with some modifications is a good place to start.)

|___|
