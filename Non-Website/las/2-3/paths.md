(Explain the practical ramifications of the P vs. NP problem.)

Consider the following two variants of problems involving finding paths between points in a simple, (non-negative) weighted graph:

+   $$\mathsf{SPATH} = \{\, \langle G, x, y, t \rangle \mid \text{There is a path from \( x \) to \( t \) in \( G \) of length at most \( t \)} \,\}$$.
+   $$\mathsf{LPATH} = \{\, \langle G, x, y, t \rangle \mid \text{There is a path from \( x \) to \( t \) in \( G \) of length at least \( t \)} \,\}$$.

It turns out that $$\mathsf{SPATH}$$ is in $$P$$ and $$\mathsf{LPATH}$$ is $$\mathsf{NP}$$-complete!

(a) Suppose you are at a logistics company, writing software to route cargo between cities. You are given a choice of two different assignments:

+   Write software to find the shortest path to ship a given piece of freight from one city to another.
+   Write software to find a path through the country from one city to another that  maximizes deliveries.

Which assignment would you choose?
Explain your answer in a few sentences.

(_Note_: there is not a _definite_ right answer here. I'm interested in your choice coupled with your reasoning based on the lessons of this course.)

|___|
