---
title: Demonstration Exercise 3
layout: content
mathjax: true
---

# Problem 1: Who Needs Von Neumann?

Most computational devices are based on a *Von Neumann* architecture which consists of a central-processing unit and memory.
However, non-Von Neumann architectures are possible and sometimes preferred depending on the workload in question.
In particular, consider tasks that can be represented as _non-deterministic finite automata_.

Non-determinism is physically realized on traditional hardware by translation to a deterministic finite automata as a pre-processing step.
Note that, once compiled, executing a DFA is efficient on paper---$\mathcal{O}(n)$ time and $\mathcal{O}(1)$ space for an input of size $n$.
But in reality, this may not be accurate. Review the NFA-to-DFA translation and in a few sentences, describe the circumstances in which executing NFAs in this manner may be inefficient or otherwise infeasible.

# Problem 2: Introducing the AP

To mitigate these problems, Micron Technology has developed a non-Von Neumann computing architecture that executes non-deterministic finite automata directly, the *Automata Processor* (AP).
Intuitively, we think of non-determinism as a sort of parallelism where (a) threads of execution act independently of each other and (b) we are looking for at least one thread of execution that accepts its input.
On the AP, execution of non-determinism is truly parallelized, leading to significant gains in performance if our problem can be expressed using a collection of NFAs.

As an example of its usage, consider the following problem from computational biology.
A *sequence motif* is a nucleotide pattern of significance.
For example, the N-glycosylation site motif is:

    > Asn, followed by anything but Pro, followed by either Ser or Thr, followed by anything but Pro (<https://en.wikipedia.org/wiki/Sequence_motif>).

We would like to detect whether a given DNA sequence contains one of a given set of sequence motifs.
What makes this problem interesting is that both the number of motifs and the size of the input sequence are both large.

We can represent sequence motifs using regular expressions. Let $R_1, \ldots, R_k$ be a collection of $k$ regular expressions representing our $k$ motifs that we wish to find:

$$
L_1 = \{ w \mid \text{\( R_i \in R_1, \ldots, R_k \), \( w' \) is a substring of \( w \), \( w' \in L(R_i) \)} \}.
$$

Give a NFA $N$ that recognizes $L_1$.
And explain briefly how your NFA could take advantage of the parallelism of the Automata Processor.

# Problem 3: Not so Rosy

Problems like motif detection can be solved in an efficient manner by exploiting the parallelism of non-determinism.
However, some regular languages do not have this property.

Consider the language:

$$
L_2 = \{ w \mid \text{ \( w \in \{ 0, 1 \}^* \), \( w \) has an even number of 0s } \}.
$$

Give a NFA that recognizes $L_2$.
Explain in a few sentences why your construction may not exploit the parallelism inherent in the AP.

# Problem 4: Tah-dah!

We shall see in the coming weeks that with general computing, full automatic parallelization of arbitrary code is undecidable.
However, in the case of finite automata and the Automata Processor, this is not the case if we are clever enough!

Consider a DFA $D$ and an input $w$ and suppose that we want to parallelize execution of $D$ on $w$ $k$-ways using non-determinism.
That is, we want to fully take advantage of $k$ parallel processes to execute $D$ on $w$.

Describe an algorithm that (a) breaks up the computation of $D$ into $k$ NFAs that operate in parallel and then (b) combines the results of the NFAs into a result for the original DFA.
With such an algorithm, we can then combine those $k$ NFAs into a single mega-NFA that can be run truly in parallel on an Automata Processor.
In a few sentences, argue the correctness of your construction---a "formal" proof is not necessary!

(*Hint 1*: since you don't know how $D$ computes, your best bet is to consider chopping up the input $w$ into $k$ pieces and working with those individual pieces.)

(*Hint 2*: when executing a finite automata in your algorithm, you will need to know more than just acceptance of the execution.
You are free to assume that you can track other things like execution traces, where each branch of the finite automata ends, _etc_.)

# Problem 5: Optimize

a.  The algorithm you developed in the previous problem might seem magical as it allows you to parallelize _any_ workload that is expressible as a finite automata.
    There are, of course, significant performance downsides to your approach that make it impractical.
    In a few sentences, describe the potential performance issues with your algorithm, both in terms of time as well as space complexity.
b.  Optimizing this naive approach is an area of active research in the field of next-generation computer architectures.
    Nevertheless, there are some simple things we might consider to optimize the algorithm.
    In a paragraph, describe such an optimization to your algorithm and argue informally why it is correct.

    (_Hint_: think about the execution of individual segments of the input in your algorithm.
    You are likely doing lots of computation to cover all the possible cases of execution for the automata.
    Are any of these executions unnecessary, for example because of the state you start in or the length of the segment?)
