---
title: "Reading 37: Entanglement"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Entanglement

As we have discussed previously, a qubit is a two-state system in a superposition between these two states.
We describe the state of a qubit as a linear superposition of two basis vectors, traditionally called \\( \ket{0} \\) and \\( \ket{1} \\):

\\[
  \ket{\psi} = \alpha_0 \ket{0} + \alpha_1 \ket{1}.
\\]

\\( \alpha_0 \\) and \\( \alpha_1 \\) are *probability amplitudes*.

In this brief reading, we'll talk about some of the mathematical properties of qubits that will allow us to explain some of the "popular science" terms surrounding quantum computation.

## Multiple Qubit Systems

When we consider multiple classical bits, they compose additively.
For example, two classical bits \\( b_0 \\) and \\( b_1 \\) can be thought of as composing together to form the 2-bit system \\( b_0 b_1 \\) with four possible values.
In contrast, experimentation tells us that qubits do not compose additively; they compose according to the *tensor product* of their bases.
The tensor product (\\( \otimes \\)) can be thought of as the Cartesian product of the bases of the original vectors.
In other words, the two-qubit system consisting of \\( \ket{\psi_1} \\) and \\( \ket{\psi_2} \\) is represented by the following quantity:

\\[
  \ket{\psi_1} \otimes \ket{\psi_2} = \ket{\psi_1 \psi_2} = \alpha_{11} \ket{00} + \alpha_{12} \ket{01} + \alpha_{21} \ket{10} + \alpha_{22} \ket{11}.
\\]

In general, a \\( k \\)-qubit system is represented by \\( 2^k \\) coefficients, one for each basis vector.
Whereas we can simulate a classical bit string of length \\( k \\) using a linear amount of space, we require an *exponential* amount of space to simulate all of these coefficients.
This exponential blow up of coefficients allows us to manipulate lots of data efficiently using only a relatively few qubits.

## Entanglement

Note that even though \\( \ket{\psi_1} \\) and \\( \ket{\psi_2} \\) each have their own coefficients, say for example:

\begin{align}
  \ket{\psi_1} = \beta_{11} \ket{0} + \beta_{12} \ket{1} \\\\ \ket{\psi_2} = \beta_{21} \ket{0} + \beta_{22} \ket{2}
\end{align}

The pigeonhole principles tells us that we cannot express all of the possible state configurations represented by the tensor construction using just \\( \beta_{11} \\), \\( \beta_{12} \\), \\( \beta_{21} \\), and \\( \beta_{22} \\).
If we cannot express the coefficients of the 2-qubit state \\( \alpha_{11}, \ldots \alpha_{22} \\) in terms of the qubits' individual coefficients we say that the state is an *entangled* state.

A classic example of an entangled state is *Bell's state*:

\\[
  \ket{\Phi^+} = \frac{1}{\sqrt{2}} (\ket{00} + \ket{11})
\\]

Note that the coefficients of \\( \ket{00} \\) and \\( \ket{11} \\) are both \\( \frac{1}{\sqrt{2}} \\), and the coefficients of \\( \ket{10} \\) and \\( \ket{01} \\) are (implicitly) \\( 0 \\).
To show that Bell's state is not entangled, we must find a solution to the following system of equations:

\begin{align}
\beta_{11} \beta_{21} = \beta_{12} \beta_{22} = \frac{1}{\sqrt{2}} \\\\ \beta_{11} \beta_{22} = \beta_{12} \beta_{21} = 0.
\end{align}

However, this is impossible because at least one of each of the pairs of \\( (\beta_{11}, \beta_{22}) \\) and \\( (\beta_{12}, \beta_{21}) \\) must be \\( 0 \\), but then this implies at least one of \\( \beta_{11} \beta_{21} \\) or \\( \beta_{12} \beta_{22} \\) will also be \\( 0 \\).

The presence of entangled quantum states illustrates the power of qubits.
Using only \\( k \\) qubits, we gain access to an exponential space whereas with classical bits, we would need an exponential number of bits to do so.

### EPR Pairs

We call pair of qubits in Bell's state *EPR pairs* named after Einstein, Podolsly, and Rosen who first explored the implications of entangled states.
Note that *entanglement* does not imply a physical connection between the two qubits---entangledness is a property of how qubits compose.
So we can certainly take the qubits of the pair and separate them.

Imagine that we take the qubits of an EPR pair and give a qubit each to Alice and Bob.
Also imagine that Alice and Bob are physically apart, far enough that they cannot possibly communicate with each other.
Now suppose that Alice measures her qubit.
With probability \\( \frac{1}{\sqrt{2}}^2 = \frac{1}{2} \\), Alice will measure her qubit to a 0 or 1.
This statefully modifies her qubit so that further measurements of the qubit produces the same basis with absolute certainty.

The trick here is that Bob's qubit is intertwined with Alice and by virtue of the entanglement under consideration:

+ If Alice's qubit is measured to be 0, then Bob's qubit will be measured to 0 with certainty.
+ If Alice's qubit is measured to be 1, then Bob's qubit will be measured to 1 with certainty.

In effect, it appears that Alice's measurement has a stateful effect on Bob's qubit even though they are physically apart!
If Alice and Bob are sufficiently far away and the Alice's and Bob's measurements happen sufficiently close in time together, it seems like information is being "transferred" between the two qubits faster than the speed of light!

Of course this can't happen and this is what quantum mechanics attempts to explain.
In short, we can think of Alice and Bob as seeing the same "stream" of random behavior, but correlated because their entangled nature.
There is much more to say here including the philosophical ramifications of quantum mechanics, but all of this is out of the scope of our brief exploration of this space.

### Applications of Entanglement

Entanglement of qubits is the reason for the richness of the multi-qubit state space.
However, can we do anything interesting with entanglement?
Note that we can enrich the BB84 key exchange protocol with EPR pairs.
Rather than Alice generating classical bits, encoding them as qubits, and sending them to Bob, the following protocol due to Ekert takes advantage of an EPR generator which can generate EPR pairs.

1.  When Alice and Bob want to exchange a secret, they consult the EPR generator to obtain \\( k \\) EPR pairs.
    Each pair is split up so that Alice and Bob each receive one qubit from each pair.
2.  For each pair, Alice and Bob randomly choose a basis---computational or Hadamard---to measure their qubit and interpret a classical bit from the result as in BB84.
3.  After Alice and Bob have measured their \\( k \\) qubits, they communicate over a public classical channel which bases they used for each pair and throw out all such pairs where they disagree.

The strength of this approach compared to BB84 is that Alice and Bob can generate shared keys on the fly by simply agreeing to consult the EPR generator, taking advantage of the fact that entanglement allows us to correlate behavior (in a very rough sense) without previous collaboration.

Two other applications of EPR pairs that we'll mention here are two basic operations that are duals of each other---*dense coding* which allows us to use one qubit to encode and transmit two classical bits and *quantum teleportation* that allows us to use two classical bits to transmit the state of a single qubit.
In both cases, we use an EPR pair and send one of its qubits to each party, call them Alice and Bob, in question.

+   In the dense coding case, Alice wants to transmit two classical bits to Bob.
    Alice applies a particular quantum operation to her qubit (a *Pauli transformation*) depending on the value of the two classical bits she wants to send.
    Alice then sends her qubit to Bob, and Bob performs a particular sequence of quantum operation on both elements of the EPR pair (a *CNOT* transformation and the *Hardamard transformation*) to recover the result.
+   In the quantum teleportation case, Alice wants to send the state of an unknown qubit that she possesses.
    She combines this unknown qubit with her EPR pair qubit using several quantum transformations and then measures the result, sending the results to Bob.
    Bob then takes this information and applies a transformation to his EPR qubit which will then take on the amplitudes of Alice's unknown qubit!

Note that "quantum teleportation" is named as such because Alice's unknown qubit is effectively transferred to Bob.
Because Alice measures her qubits (the unknown qubit and her half of the EPR pair), the information of the unknown qubit is lost on Alice's side!

### More Information

Much of this information is summarized from a variety of sources, notably *Quantum Computing: A Gentle Introduction* by Rieffel and Polak.
I highly recommend their text if you would like a gentle, yet rigorous introduction to the field of quantum computing.
