---
title: "Reading 38: Frontiers in Quantum Computing"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

\\( \newcommand{\class}[1]{\mathsf{#1}} \\)

# Frontiers in Quantum Computing

Our dive into quantum computing is motivated by two breakthrough results from the previous year: Google's "quantum supremacy" achievement and \\( \class{MIP}^* = \class{RE} \\).
Now that we've taken a small dive into quantum computing, let's look at these results in more detail.

## Quantum Supremacy

+ Scott Aaronson.  [Scott's Supreme Quantum Supremacy FAQ!](https://www.scottaaronson.com/blog/?p=4317).  23 September 2019.
+ Arute, et al.  [Quantum Supremecy Using a Programmable Superconducting Processor](https://www.nature.com/articles/s41586-019-1666-5).  Nature.  23 October 2019.
+ Scott Aaronson.  [Quantum Supremacy: The Gloves Are Off](https://www.scottaaronson.com/blog/?p=4372).  23 October 2019.

How can we demonstrate that a quantum computer actually does quantum things?
This turns out to be more difficult task than one might expect.
As we've seen, a system of \\( n \\) qubits induces an exponential state space.
For low numbers of qubits, a classical computer can simulate computation in this space directly.
Distinctions arise when \\( n \\) starts getting sufficiently large, *e.g.* \\( n = 50 \\), so the space because intractable to simulate in a classical setting.

*Quantum supremacy* is an milestone where a supposed quantum computational device is capable of performing a certain well-defined task in a relatively short amount of time that would be infeasible for a classical device to perform.
This is an engineering problem because getting even a small number of qubits working together in concert is still a technical challenge.
This is also a theoretical problem because, by definition, a device that achieves quantum supremacy will be able to do something that no classical machine can do.
How do we verify that the quantum device actually produced a correct result?

Google's landmark paper, [Quantum Supremecy Using a Programmable Superconducting Processor](https://www.nature.com/articles/s41586-019-1666-5), illustrates how they overcame these difficulties.
Check out the section "A suitable computational task" to learn more about their testing technique where they generated and sampled random quantum circuits using their architecture.

As an aside, you may have heard about D-Wave's quantum computer that uses *quantum annealing* which has been around for the better half of a decade now.
How does this relate to Google's work?
It turns out that quantum annealing can only solve some categories of problems, in particular, minimization problems with many potential solutions.
General quantum computation is broader and in theory can handle any problem.
See [Anastasia Marchenkova's discussion](https://medium.com/quantum-bits/what-s-the-difference-between-quantum-annealing-and-universal-gate-quantum-computers-c5e5099175a1) of the topic for more details.

## MIP* = RE

+ Thomas Vidick.  [A Masters Project](https://mycqstate.wordpress.com/2020/01/14/a-masters-project/).  14 January 2020.
+ Zhengfeng Ji, Anand Natarajan, Thomas Vidick, John Wright, Henry Yuen.  [MIP* = ME](https://arxiv.org/abs/2001.04383).  DOI:arXiv:2001.04383.  13 January 2020.

Recall that the class \\( \class{NP} \\) was defined by problems for which there exists a polynomial time *verifier* for candidate solutions of this problem.
This verifier is a procedure that takes a candidate solution, called a *certificate*, and checks that it is correct in polynomial time.
We can generalize this idea of a verifier to arrive at a new model of computation called *[an interactive proof system](https://en.wikipedia.org/wiki/Interactive_proof_system)*.
Sipser describes interactive proof systems in detail in section 10.4.

At a high level, an interactive proof system is a computational model with two systems:

+   A *prover* with unbounded resources and computational power but cannot be trusted.
+   A *verifier* that, in contrast, is resource-constrained, *e.g.*, must run in polynomial time.

The prover and verifier exchange messages regarding the input and the verifier must eventually accept or reject the input based on this message history.

Different constraints on these interactions result in different complexity classes, for example:

+   If interaction between prover and verifier is restricted to a single message from prover to verifier, the certificate, and the verifier must then accept or reject the input with certainty, we obtain \\( \class{NP} \\).
+   If we extend this model by making the verifier *probabilistic* and relax our acceptance criteria so that verifier only needs to be correct with a certain probability, we obtain the \\( \class{MA} \\) class.
    (*Note*: \\( \class{MA} \\) stands for Merlin-Arthur---Merlin is the all-powerful prover and Arthur is the limited, yet diligent verifier.)
+   If we further extend the model so that the verifier and prover can now send a polynomial number of messages to each other before the verifier renders its final decision, we obtain the class \\( \class{IP} \\).
    It turns out that \\( \class{IP} = \class{PSPACE} \\), one of the foundational results from the theory of computation.

However, is this the most powerful kind of interactive proof system possible while still keeping the verifier practical?
It turns out that we can obtain a more powerful interactive proof system by extending the system with *an additional prover*.
The two provers can collaborate beforehand, but once they begin interacting with the verifier, they are not allowed to communicate with each other.
The verifier can communicate with both provers freely.
The Wikipedia article on interactive proof systems describes the power of this extension beautifully:

> Just as it's easier to tell if a criminal is lying if he and his partner are interrogated in separate rooms, it's considerably easier to detect a malicious prover trying to trick the verifier into accepting a string not in the language if there is another prover it can double-check with.

How much power does this add to the system?
It turns out that it has been show that \\( \class{MIP} \\), the class of multiple interactive provers is equal to the class of problems solvable nondeterministically in exponential time, *i.e.*, \\( \class{MIP} = \class{NEXPTIME} \\)!

But can we go even further?
It turns out that we can, and this is what \\( \class{MIP}^* = \class{RE} \\) means.
\\( \class{MIP}^* \\) is the class of multiple interactive provers that are *quantumly entangled*.
From our brief study of entanglement, we know that this establishes a sort of correspondence between the two provers that the verifier can further exploit.
But how far can the verifier take this?
In January of this year, it was shown that \\( \class{MIP}^* \\) is equivalent to the class of *recursively enumerable languages*.
Recall that this is the class of problems that are recognizable by a Turing machine---this includes the halting problem!
In other words, this interaction between quantum provers and verifier is able to get around the "infinities" problem we saw with verifying that a TM halts on an input!

To learn more about this result, check out Quantum Frontier's [blog post on the subject](https://quantumfrontiers.com/2020/03/01/the-shape-of-mip-re/).
