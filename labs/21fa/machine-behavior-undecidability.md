---
title: Machine Behavior Undecidability
layout: content
mathjax: true
---

$$
\newcommand{\prob}[1]{\mathsf{#1}}
\newcommand{\Atm}{A_\mathsf{TM}}
\newcommand{\desc}[1]{\langle #1 \rangle}
$$

# Problem 1: Enter the Machine

Many problems concerning properties of models of computations turn out to be
decidable.  We can break this up into two sorts:

1.  _Language properties_ that concern the strings that a machine accepts.
2.  _Behavioral properties_ that concern how a machine operates.

In this problem, we will discuss properties of the second sort.
Because these properties are not tied to the acceptance/rejection behavior of the machine, most undecidablity proofs of these properties all follow a strict formula.

Let's consider such a problem from the textbook:

> (Sipser 5.13) A useless state in a Turing machine is one that is never entered on any input string.
> Consider the problem of determining whether a Turing machine has any useless states.
> Formulate this problem as a language and show it is undecidable.

First, let's do what Sipser says!
First formulate this problem as a language $\prob{USELESS}$.
Importantly, identify what an assumed decider $D$ for $\prob{USELESS}$ takes as input.

# Problem 2: Mappings

Now let's show that $\prob{USELESS}$ is undecidable by a mapping reduction from $\Atm$.
To do so, we'll follow the strategy suggested in the handout that accompanied today's reading.
First let's establish what our mapping function should look like and how it should behave.

The heart of the mapping reduction is a mapping from inputs to $\Atm$ to $\prob{USELESS}$.
What does the mapping function $f$ take as input and  produce as output?

# Problem 3: The Condition

Once we know the types of the mapping reduction, we now need to reason about the correctness condition linking acceptance between $\Atm$ and $\prob{USELESS}$.

Let $\desc{M, w}$ be inputs to a decider for $\Atm$ and $\desc{M'}$ the input to a decider for $\prob{USELESS}$.
Give the correctness condition for $f$ based on these inputs.

# Problem 4: The Construction

We have now established our correctness condition for our construction.
Based on this condition, we need to figure out a way to have our machine $M'$ _conditionally_ have the property of $\prob{USELESS}$: $M'$ has a useless state.
Recall that a state is useless if no input string causes $M'$ to enter that state.
Because the transitions of a Turing machine are dependent on the positions of the tape head and contents of the tape at that position, we need to know how a Turing machine executes in order to determine if it contains a useless state.
This is ultimately why $\Atm$ can be reduced to $\prob{USELESS}$.

For the purposes of our construction, however, we want to conditionally make $M'$ have a useless state in such a way that it is painfully obvious that this is the case.
This will simplify our reasoning when we go to make sure that $M'$ obeys the correct condition outlined above.
Two ways that we might go about this are:

1.  Give $M'$ a state $u$ that has no physical transition to it from any other state in \( M' \).
    It is obvious that $u$ is useless because there is no way to reach it in this situation.
2.  Give $M'$ a state $u$ that is connected from some other state in the Turing machine, but make that transition involve reading a tape symbol that provably never appears on the tape, _e.g._, by ensuring that it is a alphabet symbol and it is not mentioned in the read position of any transition of the Turing Machine.

The first option does not not work for our purposes because the transitions are fixed when $M'$ is constructed; we can't condition the existence of a transition based on whether $M$ accepts $w$.
However, the second option is controllable at runtime---we can condition the appearance of the symbol that will allow us to transition to our useless state on whether $M$ accepts $w$.

Putting all of this together, we have the following skeleton for the construction of our mapping function and the Turing machine $M'$ it produces:

---

$M' =$ On input $x$:

+   Run $M$ on $w$.
    -   If $M$ accepts: _$M'$ should have a useless state_.
    -   If $M$ rejects: _$M'$ should not have a useless state_.

---

Note that also in the case where $M$ loops on $w$, we want to have the same behavior as the rejection case.

Use this information to complete the construction of $M'$ as specified above.

# Problem 5: The Proof of Correctness

Finally, we need to verify that $M'$ does the right thing.
Rather than proving our correctness condition instead (which is a biconditional), I find it easier to reason about the three cases that might occur as a result of $M$'s execution of $w$ (convince yourself these three cases cover the two cases of the biconditional you derived above):

+   $M$ accept $w$.
+   $M$ rejects $w$.
+   $M$ loops on $w$.

Prove that $M'$ has the appropriate behavior for the three cases outlined above with respect to your correctness condition for the mapping function.
