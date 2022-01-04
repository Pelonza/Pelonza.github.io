---
title: "Reading 36: Quantum Gates"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Quantum Gates

We saw in last class's reading that qubits are two-state objects in quantum superposition:

\\[
  \ket{Ψ} = α_0 \ket{0} + α_1 \ket{1}.
\\]

where \\( \alpha_0 \\) and \\( \alpha_1 \\) are probability amplitudes (*i.e.*, can be complex numbers).

Ultimately, the goal of quantum computation is to manipulate these probability amplitudes through operations realized as *quantum gates* and then *measure* the qubit, producing a final two-state value (in the case of a single qubit) based on those probabilities.

We'll continue our brief exploration into the guts of quantum programming by looking at these operations in more detail.
Kemp's mathematics-light tutorial is good to review as it discusses the basics of quantum entanglement in terms of 2-qubit Hadmard and CNOT gates:

+ David Kemp. [An Interactive Introduction To Quantum Computing](https://davidbkemp.github.io/QuantumComputingArticle/).  From [davidbkemp.github.io](https://davidbkemp.github.io).  December 2017.

To begin unearthing some of the mathematical details behind qubits and quantum gates, I found this set of tutorials by Jonathan Hui to be digestible enough even for someone with only a passing familiarity with linear algebra.

* Jonathan Hui.  [QC—What Are Qubits in Quantum Computing](https://medium.com/@jonathan_hui/qc-what-are-qubits-in-quantum-computing-cdb3cb566595).  From [medium.com](https://medium.com).  November 2018.

Part 2 of the tutorial, linked above, talks about the mathematics of qubits.
If you have time, I recommend starting to skim Parts 2 (skipping over the optional Scrodinger's Equation section) and 3, paying attention to how the mathematical descriptions of "Unitary", "Entanglement", the "Hadamard Gate" line up with the more informal descriptions of Kemp.
