(Prove that a problem is in a particular time complexity class.)

Consider a multiset (a set that allows for repeated elements) $$S$$. The _3-partition_ problem involves partitioning the elements of $$S$$ into triples, _i.e._, $$(x, y, z)$$ with $$x, y, z \in S$$, such that every triple sums to the same value. For example,

$$
\{\, 0, 0, 0, 2, 2, 2, 3, 3, 6, \,\}
$$

can be partitioned into the triples $$(0, 0, 6)$$, $$(3, 3, 0)$$, and $$(2, 2, 2)$$, all of which sum to $$6$$.

Show that the 3-partition problem is in $$\mathsf{NP}$$.

|___|
