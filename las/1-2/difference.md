(Prove closure and algorithmic properties of the regular languages.)

Recall the formal definition of the _set difference_ operator:

$$
S - T = \{\, x \mid x \in S, x \notin T \,\}.
$$

Recall that languages are sets of strings, so the set difference operator lifts to languages directly. For example:

+   If $$101 \in L_1$$ and $$101 \notin L_2$$, then $$101 \in L_1 - L_2$$.
+   If $$000 \in L_1$$ and $$000 \in L_2$$, then $$000 \notin L_1 - L_2$$.
+   If $$111 \notin L_1$$ and $$111 \in L_2$$, then $$111 \notin L_1 - L_2$$.

Show that if $$L_1$$ and $$L_2$$ is regular, then $$L_1 - L_2$$ is also regular. You do not have to give a fully-symbolic proof, but your argument should cover all relevant details of the construction.

(_Hint_: utilize the fact that regular languages are closed under set difference in your construction.)

|____|
