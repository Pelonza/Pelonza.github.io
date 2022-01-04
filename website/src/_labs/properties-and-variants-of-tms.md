---
lab: Properties and Variants of TMs
layout: content
mathjax: true
---

# Problem 1: Multi-(tape) Kill

1.  Summarize each direction of the proof of equivalence of ordinary TMs and multi-tape Turing machines in a sentence a piece.

2.  Multi-tape Turing machines have a finite, fixed number of tapes at construction time.
    Suppose we tried extending the model so that the machine had an _infinite_ number of tapes at construction time.
    Describe the fundamental difficulties we would encounter in trying to construct and execute such a model.

3.  In contrast, imagine extending the model so that the multi-tape model can have a _dynamic_, _unbounded_ number of tapes.
    The model would need an operation to spawn a new tape and the transition function would need to be modified to operate over a list of tapes.
    In contrast to the infinite tape model, does this variant seem equivalent to ordinary TMs? Why?

# Problem 2: The Matrix

1.  Summarize each direction of the proof of equivalence of ordinary TMs and non-deterministic TMs in a sentence a piece.

2.  When converting NFAs to DFAs, we induced a _state explosion_, drastically increasing the space complexity of the automata.
    Where does this _space hit_ occur in the NTM-to-TM transformation?

3.  Review the proof of the NTM-to-TM transformation in the book (theorem 3.16).

    a.  What is the purpose of the "address" in the construction?
    b.  What does the TM do if a string is not accepted by the original NTM?
        How do we fix this problem?

# Problem 3: Blah Blah Blah

1.  Summarize each direction of the proof of equivalence of ordinary TMs and enumerators in a sentence a piece.

2.  Give a formal description of *what* an enumerator is.
    Include a rigorous description of its components, its behavior, and the inclusion condition for its language, _i.e._, the condition under which $w \in L(E)$ for some enumerator $E$
