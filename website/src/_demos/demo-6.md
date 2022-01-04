---
title: "Demonstration Exercise #6"
layout: content
mathjax: true
---

$$
\newcommand{\prob}[1]{\mathsf{#1}\xspace}
\newcommand{\desc}[1]{\langle #1 \rangle}
\newcommand{\np}{\mathsf{NP}\xspace}
\newcommand{\comp}[1]{\overline{#1}}
$$

# Problem 1: Satisfying Variations

For this problem, we'll explore variations of the 3-SAT problem, generalized to the $k$-SAT problem:

$$
\prob{kSAT} = \{\, \desc{\phi} \mid \text{\( \phi \) is a satisfiable \( k \) cnf-formula} \,\}.
$$

a.  Suppose that you have a 2cnf-formula clause of the form $(x_1 \vee x_2)$.
    Describe how you would turn this clause into a logically equivalent 3cnf-formula clause.
    Argue in a sentence or two why your transformation is correct.

b.  With this fact, prove that $\prob{2SAT} \leq_p \prob{3SAT}$.

c.  Suppose that you have a 4cnf-formula clause of the form $(x_1 \vee x_2 \vee x_3 \vee x_4)$.
    Describe how you would turn this clause into a logically equivalent 3cnf-formula clause.
    Argue in a sentence or two why your transformation is correct.

    (_Hint_: you will want to split up the 4cnf clause into, _e.g._, $(x_1 \vee x_2 \vee \ldots) \wedge (\ldots \vee x_3 \vee x_4)$.
    How do you complete these two 3cnf clauses so that only one of $x_1, \ldots, x_4$ is necessary to be true to make _both_ clauses true?
    You should consider making a new variable distinct from $x_1, \ldots, x_4$ to help you with this transformation.)

d.  With this fact, prove that $\prob{4SAT} \leq_p \prob{3SAT}$.

e.  Finally, we can generalize $k$-SAT to any combination of sizes of cnf-formula as follows:

    $$
    \prob{CSAT} = \{\, \desc{\phi} \mid \text{$\phi$ is a satisfiable formula in CNF form} \,\}.
    $$

    Show that $\prob{CSAT} \leq_p \prob{3SAT}$.

    (_Hint_: each sub-formula of $\phi$ can have arbitrary size.
    Make sure that your reduction covers _every_ possible size of formula.)

# Problem 2: Color Me Badd

A $k$-coloring of a graph $G$ is an assignment of $k$ distinct colors to the nodes of $G$ such that no two nodes that share an edge also share the same color.
In this problem, we will show that:

$$
\prob{3COLOR} = \{\, \desc{G} \mid \text{\( G \) is a graph at \( G \) has a 3-coloring} \,\}
$$

Is $\np$-complete.

a.  Prove that $\prob{3COLOR} \in \np$.

b.  To prove that $\prob{3COLOR}$ is $\np$-hard, we will reduce from $\prob{3SAT}$.
    Our mapping function takes as input a 3cnf-formula $\phi$ and produces a graph $G$ as output with the property:

    $$
    \text{\( \phi \) is satisfiable} \Leftrightarrow \text{\( G \) has a 3-coloring}.
    $$

    The core of this construction is a _color gadget_ which is a sub-graph that forces a particular coloring of its nodes:

    ![The color gadget.]({{ "/img/demo-6-color-gadget.png" | relative_url }})

    Note that the color gadget is a complete 3-graph.
    Because of this, each node must be a distinct color.
    Here, we will use the colors $T$, $F$, and $B$.
    The first two colors will correspond to the values true and false respectively.
    The final color is a "base" color that we introduce merely to fulfill the requirement that the graph coloring must employ three colors.
    With the color gadget, we are able to _force_ nodes in our overall construction to take on particular colors.

    Recall in our mapping function that we must map objects of our input domain---variables, clauses, and assignments of $\phi$---to objects in our output domain---nodes, edges, and colorings of $G$.
    First we will map the variables to nodes and assignments to colorings.
    For each $x_i$, we will create two nodes labeled $x_i$ and $\comp{x_i}$.
    Create a subgraph with these two nodes and the color gadget to force exactly one of the two nodes to be colored $T$ and the other $F$.
    Argue in a few sentences why your constructed subgraph correctly implements this behavior.

c.  Next, we will describe how to map the input clauses onto the output graph.
    Suppose that we have two variable nodes $x_i$ and $x_j$ and we want to compute the "or" of the two nodes.
    Create a subgraph with these two nodes with the property that one of the nodes of this subgraph, the "output" node, _can_ be colored $T$ if at least one of $x_i$ and $x_j$ are colored $T$.
    Give an example of your "or"-gadget and how it may output $T$ when given two variables, exactly one of which is colored $T$.

d.  Extend the "or"-gadget from the previous part to three variable nodes $x_i$, $x_j$, and $x_k$.  
    Furthermore, force the output node of this gadget to be colored $T$.
    Argue in a few sentences why the clause gadget outputs $T$ if and only if at least one of $x_i$, $x_j$, and $x_k$ is true.

    (_Hint_: note that "or" gadget from the previous part may not have the "if and only if" behavior that we need.
    However, this extended gadget should have that behavior, but its a surprisingly subtle argument!
    Use the color gadget to force colorings as necessary and argue why certain "bad" colorings present in the basic "or" gadget are not possible with the extended gadget.)

e.  Describe the complete mapping function $m : \phi \rightarrow G$ for this reduction, combining all of the gadgets from the previous parts.

f.  As an example, give the output of your mapping function for the following 3-sat formula (from figure 7.33 of Sipser):

    $$
      \phi = (x_1 \vee x_1 \vee x_2) \wedge (\comp{x_1} \vee \comp{x_2} \vee
        \comp{x_2}) \wedge (\comp{x_1} \vee x_2 \vee x_2)
    $$

g.  Finally, we'll prove the correctness of our construction.
    First, prove the "if" direction: if $\phi$ is satisfiable, then $m(\phi)$ is 3-colorable.
    You may appeal to your previous arguments for the correctness of the sub-components of the construction as necessary.

h.  Prove the "only if" direction of the claim: if $m(\phi) = G$ and $G$ is 3-colorable, then $\phi$ is satisfiable.
    You may appeal to your previous arguments for the correctness of the sub-components of the construction as necessary.

# Problem 3: Closing Space

Prove that the class of $\mathsf{PSPACE}$ languages are closed under the following properties:

+   Complementation: $\overline{L} = \{\, w \mid w \notin L \,\}$.
+   Kleene star: $L^*$ (strings formed from zero or more repetitions of strings drawn from $L$).

You do not have to given full symbolic descriptions of the relevant Turing machines, but you should describe their relevant details in sufficient detail that their construction is unambiguous.
Make sure to argue that your resulting Turing machines takes a polynomial amount of space!

(_Hint 1_: what do assume exists since you know the language $L$ is in $\mathsf{PSPACE}$?)

(_Hint 2_: what properties of $\mathsf{PSPACE}$ can you use to make your constructions, in particular for Kleene Star, easier?)
