---
title: Week 5 Lab Solutions
layout: content
mathjax: true
---

# Problem: Just The Facts, Turing Edition

1.  Can a Turing machine ever write the blank symbol `␣` on its tape?
    **Yes. Γ includes the blank tape symbol, so it is a valid input to δ.**
2.  Can the tape alphabet $Γ$ be the same as the input alphabet $Σ$?
    **No. The blank tape symbol must always be in Γ but not Σ.**
3.  Can a Turing machine's head *ever* be in the same location in two successive steps?
    **No. On every step, the head must move left or right; it cannot hold still.**
4.  Can a Turing machine contain just a single state?
    **No. A Turing machine must at least have distinguished accept and reject states.**
5.  What happens when a Turing machine's head moves off the left end of the tape?
    **It stays on the left-most tape cell, _i.e._, it hits a wall.**
    What happens when it moves off the right end of the tape?
    **We spawn a new cell with a blank tape symbol to move onto.**
    **Alternatively, we can view the tape as containing an infinite number of blank symbol cells to the right.**

6.  One difference between Turing machines and our previous machine-based models of computation is the presence of a reject state.
    Why was this unnecessary for finite automata?
    Why is it necessary for Turing machines?
    **Reject states unnecessary for a finite automata because there is no way to go into an infinite loop, so rejection can be defined as "not accept."**
    **It is necessary for TMs because they can loop.**

7.  Describe the difference between a Turing machine that *recognizes* a language versus a machine that *decides* a language.
    **A TM that decides a language (a) accepts all strings that are in the language and (b) rejects all strings not in the language.**
    **A TM that recognizes a language (a) accepts all strings that are in the language and (b) rejects _or loops_ on all strings no in the language**.

8.  We can strongly characterize the runtime of any finite automata in terms of the size of its input.
    What can we say about the runtime of a Turing machine in terms of the size of its input?
    **We can say nothing! A TM may run into an infinite loop, regardless of tape contents.**
9.  Give a implementation-level diagram of a Turing machine that does
    not terminate on any input.
    **Our TM contains a start state $q$ as well as an accept and reject state.**
    **All three states simply loop on themselves on any possible input and advance the tape head right without modification.**
    **Observe that on any input, this TM will loop on $q$ and can never reach the accept or reject states.**

# Problem: Implementation Details

A TM $M$ that implements $L_1$ proceeds as follows:

+   First, $M$ inserts a special symbol $!$ at the beginning of the tape so that it can seek to the beginning easily.
+   Next, $M$ returns to the beginning of the tape and repeats the following until it can no longer find a $0$ on the tape:
    -   $M$ sweeps the tape from beginning to end, looking for a $0$.
        Once $M$ finds a $0$, it replaces the $0$ with an $x$.
    +   $M$ sweeps the tape again from beginning to end, this time looking for a $1$.
        Once $M$ finds a $1$, it replaces the $1$ with an $x$.
        If $M$ does not find a $1$, it _rejects_.
+   Once done with this process, all $0$s on the tape have been replaced with $x$s.
    $M$ sweeps the tape one more time from beginning to end and _rejects_ if it finds a $1$.
    Otherwise, $M$ should have seen all $x$s; it _accepts_ in this case.

A TM $N$ that implements $L_2$ behaves somewhat similarly to $N$ but flips when it accepts and rejects:

+   First, $N$ inserts a special symbol $!$ at the beginning of the tape so that it can seek to the beginning easily.
+   Next, $N$ returns to the beginning of the tape and repeats the following until it can no longer find a $0$ on the tape:
    -   $N$ sweeps the tape from beginning to end, looking for a $0$.
        Once $N$ finds a $0$, it replaces the $0$ with an $x$.
    +   $N$ sweeps the tape again from beginning to end, this time looking for a $1$.
        Once $M$ finds a $1$, it replaces the $1$ with an $x$.
        If $N$ does not find a $1$, it _accepts_.
+   Once done with this process, all $0$s on the tape have been replaced with $x$s.
    $N$ sweeps the tape one more time from beginning to end and _accepts_ if it finds a $1$.
    Otherwise, $M$ should have seen all $x$s; it _rejects_ in this case.

# Problem: Multi-(tape) Kill

1.  **TM-to-multi-TM**. Trivial as a regular TM is a (single tape) multi-tape machine.

    **Multi-TM-to-TM**. Lay out the $k$ tapes of the multi-TM onto the single tape of the regular TM end-to-end with appropriate delimiters in place to separate the different tapes.
    Sweep the single tape to read/write symbols from each of the multi-TM's tapes.

2.  An infinite number of tapes would not result in a well-defined machine.
    δ would need to output an infinite set of tapes, and during execution, the TM would need to somehow update the infinite tapes in a finite amount of time to make progress on each step.

3.  The dynamic, unbounded multi-tape model is equivalent to ordinary TMs.
    Note that we can lay out the tapes end-to-end like the static multi-tape TM model.
    Since the transition function must operate over a list of tapes, it must account for the fact that the number of tapes is unknown.
    Furthermore, while the number of tapes is unbounded, it is not infinite, so at any point in time, there is only a finite number of tapes to traverse.

# Problem: The Matrix

1.  **TM-to-NTM**: Trivial as a regular TM is a (degenerate) NTM.

    **NTM-to-TM**: Maintain a counter that represents the "path" through the tree representing all the non-deterministic choices that can be made during the NTM's execution.
    Simulate the NTM up to the number of steps as represented by the counter, "increment" the counter, and then repeat.

2.  The "space hit" for a TM simulating a NTM does not necessarily come from space complexity---the additional cost is a single counter---but instead comes in the form of time complexity in that we have to still explore every branch of the NTM's execution in sequence.
    Furthermore, we have to repeat tons of work, because we explore the execution tree in breadth-first order, repeating the "prefixes" of each execution trace to go deeper into the tree.

3.  The address of the book's construction keeps track of the current "path" through the NTM's tree of nondeterministic choices.
    It also doubles, implicitly, as a limiter on how many steps of execution we take on any given run, thus avoiding the problem of "looping" on one branch and not making progress with others.

    The book construction has a "bug" in it in that if the string is rejected by the NTM, then the corresponding TM loops forever (note the construction never says when it rejects).
    We want to reject a string when all the concurrent branches of execution die.
    However, the "address" setup makes it difficult to detect this because we don't know, _e.g._, if the execution corresponding to counter value $x$ occurs at the "same time" as the execution corresponding to counter value $x+1$.

    To address this, we can take a different approach: we can enqueue the _current, live configurations of executions_ onto the tape, similarly to how we encode a multi-tape TM.
    The deterministic TM then simulates one step of execution on the head of the queue, potentially enqueuing more configurations to process.
    By using a queue, we avoid "livelocking" on a looping branch of execution, and we can easily detect when to reject a string: when the queue is empty.

# Problem: Blah Blah Blah

1.  **TM-to-Enumerator**: enumerate all possible strings in lexographical order, run them through the TM in a breadth-first manner (to avoid livelocking), and output a string once a TM accepts it.

    **Enumerator-to-TM**: run the enumerator and accept when our input string is outputted by the enumerator.

2.  An enumerator $E$ operates over a alphabet $\Sigma$ and is a black box that outputs strings over $\Sigma$.
    In other words, it doesn't have any "external" components that we can manipulate!
    $E$ simply enumerate strings from $\Sigma^*$.
    A string $w \in L(E)$ iff $E$ outputs $w$ at some point during its execution.
