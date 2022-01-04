(Represent a problem using a context-free model of computation.)

Consider the following context-free grammar $$G$$ with start symbol $$S$$ and alphabet $$\Sigma^* = \{\, <, >, - \,\}$$, _i.e._, angle brackets and dashes:

$$
S \rightarrow\;\; U T \mid T V \\
T \rightarrow\;\; T - \mid - T \mid - \\
U \rightarrow\;\; < \\
V \rightarrow\;\; >
$$

(a) Give a derivation demonstrating that $$UTV \overset{*}{\Rightarrow} <---> $$.

|___|

(b) Give a formal definition for $$L(G)$$.

|___|
