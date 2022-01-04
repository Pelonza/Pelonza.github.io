(Represent a problem using a context-free model of computation.)

Consider the following context-free grammar $$G$$ with start symbol $$S$$:

$$
S \rightarrow XYX \\
X \rightarrow X0 \mid 0 \\
Y \rightarrow 1Y \mid \epsilon
$$

(a) Give a derivation demonstrating that $$S \overset{*}{\Rightarrow} 00100$$.

|___|

(b) Give a formal definition for $$L(G)$$.

|___|

---

**Solutions**

(a) S ⇒ XYX ⇒ X0YX ⇒ 00YX ⇒ 001YX ⇒ 001X ⇒ 001X0 ⇒ 00100.
(b) L(G) = 0^+ 1^* 0^+
