---
title: "Reading 11: Properties and Variants"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
mathjax: true
---

# Properties and Variants

Now that we've gotten accustomed to the variety of operations we can emulate with Turing machines, we'll now take a look at the properties of Turing machines.
In particular, we'll look at *closure properties* and *equivalent models of computation* and see how *robust* the Turing machine model is even though it is minimal.

## A Note On Descriptions

The book discusses this concept in chapter 3.3, but it is worthwhile to talk about the *different levels of descriptions* we can give for Turing machines now that their behavior is rapidly getting more and more complex.

+ A *formal description* of a Turing machine is a precise description given either graphically (if the Turing machine is concrete) or symbolically (if the Turing machine is abstract).
* An *implementation description* is a step-by-step procedure that describes how the Turing machine behaves at a low level, *i.e.*, in terms of tape head behavior.
* A *high-level description* describes how a Turing machine behaves at a high level, *i.e.*, in terms of problem-specific operations that we assume are implementable using low-level Turing machine movements.

When should we choose one description over the other?
Through last class (and for Demonstration Set #3), you should be giving formal descriptions of Turing machine behavior since we're concerned with capturing the low-level behavior of the model.
However, from this point forward, our low-level descriptions will be too unwieldy to provide for every machine we must consider.
So we will have to choose between implementation and high-level descriptions depending on what the machine's underlying language is about.

+ Give an implementation description when the language concerns the low-level operations of the Turing machine.
+ Give a high-level description when the language is about specific problem domain and not the inner workings of the underlying Turing machine.

In essence, we have to ask ourselves what is the "hard part" about the computation described in the language.
If the hard part is about getting a Turing machine to perform a certain kind of computation, then an implementation description is appropriate.
Otherwise, a high-level description gets to the point without introducing unnecessary detail.

## Reading

* Sipser, chapter 3.2 "Variants of Turing Machines".

---

**Reading Problem (Stack 'Em Up)**

(Adapted from Sipser 3.9).

(a) Consider an array data structure that allows for arbitrary (index-based) read-write access of its elements.
Describe a procedure whereby *two* stack data structures (that only allow pushing and popping of the top of the stack) can simulate an array.
(*Hint*: place the stacks top-to-top.)

(b) Let a \\( k \\)-PDA be a pushdown automata equipped with \\( k \\) stacks.
On every transition, a \\( k \\)-PDA can pop and push to any combination of its \\( k \\) stacks in the standard way.
Use your answer to part (a) to give a high-level proof sketch of how a \\( 2 \\)-PDA is equivalent in power to an ordinary Turing machine.
Note that you need to show both sides of the equivalent---given a \\( 2 \\)-PDA, construct an equivalent Turing machine and given a Turing machine, construct an equivalent \\( 2 \\)-PDA.

