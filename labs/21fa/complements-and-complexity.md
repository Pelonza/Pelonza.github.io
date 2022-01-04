---
title: Complements and Complexity
layout: content
mathjax: true
---

$$
\newcommand{\comp}[1]{\overline{#1}}
\newcommand{\SAT}{\mathsf{SAT}}
\newcommand{\NP}{\mathsf{NP}}
\newcommand{\coNP}{\mathsf{coNP}}
\newcommand{\NL}{\mathsf{NL}}
\newcommand{\coNL}{\mathsf{coNL}}
\newcommand{\PATH}{\mathsf{PATH}}
\newcommand{\PCLS}{\mathsf{P}}
\newcommand{\CoP}{\mathsf{coP}}
$$

In today's lab, we'll look at logspace as well as begin investigating the relationship between complexity classes, problems, and their _complements_.

# Problem 1: Proper Endpoints

Show that $A$, the language of properly nested parentheses is in $L$.
For example, `(()((())))` ∈ $A$ but `()((` is not.
(Thanks Adam.)

# Problem 2: Problem Complements

The complement of a language $A$, written $\comp{A}$, is simply the set of strings _not_ in the language, _i.e._,

$$
\comp{A} = \{\, w \mid w \notin A \,\}
$$

As a concrete example, recall the definition of $\SAT$:

$$
\SAT = \{\, \phi \mid \text{\( \phi \) is a satisfiable boolean formula} \,\}.
$$

The complement of $\SAT$ can therefore be defined as:

$$
\comp{\SAT} = \{\, \phi \mid \text{\( \phi \) is not a satisfiable boolean formula} \,\}.
$$

For each of the following formulae, determine whether they are in $\SAT$ or $\comp{\SAT}$.

a.  $(x_1 \vee x_3) \wedge (x_2 \vee x_3) \wedge (x_1 \vee \comp{x_3}) \wedge (\comp{x_2} \vee x_3)$.
b.  $(x_1 \vee x_2) \wedge (\comp{x_1} \vee \comp{x_2}) \wedge (x_1 \vee \comp{x_2}) \wedge (\comp{x_1} \vee x_2)$.

# Problem 3: Verifying Complements

Analogously, we can consider complexity classes whose languages consist of the complements of languages in the original class.
We prefix such classes with "co."
For example, the class of languages that are complements of languages in $\NP$ is $\coNP$.
In the $\NP$ case, we can think of $\coNP$ as the class of language complements with verifiers that take an input and certificate that report whether the input is _not_ in the original language.

a.  An important question we might ask is whether _solving a problem's complement is as easy as solving the original problem_.
    In terms of classes, this amounts to asking the question: $\NP = \coNP$?
    To get at this problem, let's first consider the left-to-right direction of this claim.
    Suppose that we know that a language $A$ is in $\NP$; thus, we know that there exists a verifier for $A$.
    Describe your best attempt at building a verifier for $\comp{A}$ using this assumed verifier for $A$.
    Describe where your attempt fails.

b.  Now, let's consider the right-to-left direction.
    Suppose we know that $\comp{A} \in \coNP$; thus, we know there exists a verifier for $\comp{A}$.
    Describe your best attempt at building a verifier for $A$ using this assumed verifier for $\comp{A}$.
    Describe where your attempt fails.

c.  Finally, summarize your findings from the previous two parts.
    What is the fundamental difficulty that you encountered when trying to build verifiers in either direction?
    What does this imply about the relationships between the two classes?
    Is it clear whether $\NP \subseteq \coNP$ or $\coNP \subseteq \NP$?

# Problem 4: Easy Complements

The final section (8.6) of the reading highlights a surprising fact, $\NL = \coNL$!
That is, even though we have difficulty navigating between "yes" and "no" answers in $\NP$, we can do so easily in $\NL$!
The proof that $\NL = \coNL$ is straightforward---show that $\comp{PATH} \in \coNL$---but the construction is a bit tricky and specific to fit within logspace bounds.

For this exercise, to get a sense of the weirdness involved with reasoning about complements, let's consider a simpler case: $\PCLS = \CoP$.

a.  Prove that $\PCLS = \CoP$.
    Make sure to prove both directions of this claim.
b.  Why does this proof not translate to a proof that $\NP = \coNP$.
