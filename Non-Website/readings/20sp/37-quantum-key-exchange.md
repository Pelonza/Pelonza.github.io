---
title: "Reading 37: Quantum Key Exchange"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Quantum Key Exchange

One application of quantum computing using the concepts that we've discussed so far is *secure key exchange*.
In this scenario, two parties wish to establish a shared secret, here a symmetric encryption key, over a public channel.
Simply communicating the key over the public channel is ill-advised: an eavesdropper can listen on the channel and obtain the key.

The [Diffie-Hellman key exchange protocol](https://en.wikipedia.org/wiki/Diffie–Hellman_key_exchange) allows us to establish shared secrets over public channels by taking advantage the hardness of the [discrete logarithm](https://en.wikipedia.org/wiki/Discrete_logarithm) problem.
However in the presence of quantum computation, [Shor's algorithm](https://en.wikipedia.org/wiki/Shor%27s_algorithm) allows us to solve this problem in polynomial time, effectively defeating the scheme.
We, therefore, need alternative techniques that are resilient to the power afforded by quantum computation for secure key exchange.

A simple quantum protocol for doing so is [BB84](https://en.wikipedia.org/wiki/BB84), named after its creators Charles Bennett and Giles Brassard.
BB84 does not guarantee that the parties can establish a shared secret.
It instead uses the properties of quantum mechanics to ensure that the two parties can detect whether a third party has inspected the secret.
The two parties can then safely repeat the process until they no longer detect that a third party has interfered.

BB84 requires that there be two public channels between the two parties that wish to establish a shared secret: a two-way classical channel and a one-way quantum channel.
The protocol between the two parties, traditionally called Alice (\\( A \\)) and Bob (\\( B \\)), works as follows:

---

1.  \\( A \\) generate a sequence of \\( k \\) random classical bits: \\( x_1, \cdots, x_k \\).
    A fraction of these bits will serve as the final shared private key.
2.  For each bit \\( x_i \\), \\( A \\) flips a coin:

    -   If the coin lands on heads, then \\( A \\) encodes \\( x_i \\) as a qubit \\( \psi_i \\) in the computational (0-1) basis as follows:

        \begin{gather}
          x_i = 0 \Longrightarrow \psi_i = \ket{0} \\\\ x_i = 1 \Longrightarrow \psi_i = \ket{1}
        \end{gather}

    +   If the coin lands on tails, then \\( A \\) encodes \\( x_i \\) as a qubit \\( \psi_i \\) in the Hadamard basis as follows:

        \begin{gather}
          x_i = 0 \Longrightarrow \psi_i = \ket{+} \\\\ x_i = 1 \Longrightarrow \psi_i = \ket{-}
        \end{gather}

3.  \\( A \\) sends \\( \psi_1, \ldots, \psi_k \\) over the quantum channel to \\( B \\).
4.  For each qubit \\( \psi_i \\), \\( B \\) flips a coin:

    +   If the coin lands on heads, then \\( B \\) measures \\( \psi_i \\) in the computational basis and interprets the result as secret key bit \\( x_i' \\) as follows:

        \begin{gather}
          \psi_i \rightarrow \ket{0} \Longrightarrow x_i' = 0 \\\\ \psi_i \rightarrow \ket{1} \Longrightarrow x_i' = 1
        \end{gather}

    +   If the coin lands on tails, then \\( B \\) measures \\( \psi_i \\) in the Hadamard basis and interprets the result as secret key bit \\( x_i' \\) as follows:

        \begin{gather}
          \psi_i \rightarrow \ket{+} \Longrightarrow x_i' = 0 \\\\ \psi_i \rightarrow \ket{-} \Longrightarrow x_i' = 1
        \end{gather}

5.  Once \\( B \\) is done measuring and interpreting all of the quantum bits, \\( A \\) and \\( B \\) communicate for each \\( x_i \\) and \\( \psi_i \\) which bases they used to encode and decode, respectively, each shared key bit.
    Any such bits where \\( A \\) and \\( B \\) chose differing bases are thrown away.

6.  Of the remaining bits \\( A \\) and \\( B \\) use a fraction of them to test whether someone has eavesdropped on their communication.
    These bits are then thrown away.
    The final bits left over constitute the shared key between \\( A \\) and \\( B \\).

---

First, observe that for each qubit, \\( B \\) has a \\( \frac{1}{2} \\) chance of guessing the same basis that \\( A \\) used to encode the qubit.
As a result, we expect that \\( A \\) and \\( B \\) will keep half of the transferred bits, on average.
If \\( B \\) is wrong in their choice of basis, then \\( B \\)'s interpretation of the qubit is only correct with some probability.
Since \\( A \\) and \\( B \\) need to agree on the eventual secret key with certainty, it makes sense that qubits where there is uncertainty are thrown out.

What happens if an eavesdropper, traditionally named Eve or \\( E \\), snoops on the channel?
Note that the only information communicated on the classical channel is the bases used to encode each bit, so \\( E \\) must inspect the quantum bits in order to make any headway.
However, because of quantum mechanics, the only thing \\( E \\) can do is measure the qubit against a random basis and then send the qubit along to \\( B \\).
This is due to several reasons:

+   Qubit probability amplitudes cannot be observed directly.
    Instead, we can only measure qubits which statefully changes the qubit formerly in superposition into one of its bases with certainty.
+   Note that \\( A \\) and \\( B \\) do not communicate the bases they have chosen until *after* \\( B \\) has measured all of the qubits that \\( A \\) has sent.
    As a result, \\( E \\) cannot simply hold onto a qubit they intercept; they need to send it over to \\( B \\).
+   We might wonder if \\( E \\) can copy the qubit they intercept and send the copy to \\( B \\), none the wiser.
    However, the No-Cloning theorem answers this in the negative:

    > **No-Cloning Theorem**.  It is impossible to create a copy of an unknown quantum state.

    It turns out this theorem is a consequence of entanglement and the fact that all operations on qubits must be Unitary, *i.e.*, reversible.
    However, this means that \\( E \\) cannot hold onto a copy of the qubit, wait for \\( A \\) and \\( B \\) to communicate their bases, and then sample the qubit.

Let's suppose that \\( E \\) measures the qubit against a random basis and then sends that qubit to \\( B \\).
Because measurement is a stateful transformation and \\( E \\)'s measurement of the qubit must come before \\( B \\), \\( B \\) will measure the qubit with certainty.
\\( B \\) and \\( E \\) will measure the same result, but at face value, it seems like \\( B \\) cannot detect this fact.
However, if \\( A \\) and \\( B \\) *compare their resulting classical bits*, they have a chance of noticing a discrepancy which tips them off to the fact that \\( E \\) eavesdropped.

Normally, if \\( A \\) and \\( B \\) compared classical bits \\( x_i \\) and \\( x_i' \\) that they kept after completing the protocol, this means that \\( A \\) and \\( B \\) used the same basis to measure their bits and thus the bits will be equivalent with certainty.
However, if \\( E \\) has measured before \\( B \\), then \\( E \\) measured with a random basis.

+   If \\( E \\) happened to choose the same basis as \\( A \\) then \\( E \\).
+   However, if \\( E \\) chose a different basis then \\( E \\)'s interpretation of the qubit only has a \\( \frac{1}{2} \\) chance of agreeing with \\( A \\)'s encoding.
    Because of the stateful nature of quantum measurement, this means that \\( B \\)'s interpretation will also have the same property!

Overall, for any quantum bit that \\( A \\) and \\( B \\) agree on with respect to bases and that \\( E \\) intercepts and measures, there is a \\( \frac{1}{4} \\) chance that \\( B \\)'s interpretation of the qubit \\( x_i' \\) differs from \\( A \\)'s interpretation \\( x_i \\).
Therefore, in step 6 \\( A \\) and \\( B \\) use some fraction of the overall bits for which they agree on bases as *check bits*.
They check that \\( x_i = x_i' \\) over the classical channel and then throw those bits away afterwards (since \\( E \\) could see these bits). If such a pair of classical bits are not equal, then they know \\( E \\) inspected and measured a transferred qubit.
They can, therefore, throw away the computation since \\( E \\) may know part of the private key and then try again!
