(Prove closure and algorithmic properties of the regular languages.)

Let $$f : \Sigma_1 \rightarrow \Sigma_2^*$$ be a function from an alphabet $$\Sigma_1$$ to _strings_ drawn from the alphabet $$\Sigma_2$$. We can _lift_ $$f$$ to operate over strings of $$\Sigma_1$$ in an element-wise fashion with concatenation so that:

$$
f(w_1 \cdots w_k) = f(w_1) \cdots f(w_k)
$$

For example, let $$\Sigma_1 = \{\, x, y, z \,\}$$ and $$\Sigma_2 = \{\, 0, 1 \,\}$$. And define $$f : \Sigma_1 \rightarrow \Sigma_2^*$$ by cases:

+   $$f(x) = 11$$.
+   $$f(y) = 00$$.
+   $$f(z) = \epsilon$$.

Then $$f(xyzyx) = 11000011$$. Finally, we can lift $$f$$ to operate on languages as follows:

$$
f(L) = \{\, f(w) \mid w \in L \,\}.
$$

Thus, if $$xyzyx \in L$$ then $$11000011 \in f(L)$$.

Show that if $$L$$ is a regular language then $$f(L)$$ is also a regular language.

(_Hint_: recall that you can choose to use _any_ regular model of computation to base your construction upon. Since $$f$$ operates in a textual, find-and-replace manner, it may be easier to use a textual model of regular computation in your proof.)

|____|
