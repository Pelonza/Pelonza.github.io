(Design and reason about an approximation algorithm to an optimization problem.)

In banking, _float_ is the time between making a payment with a check and the time that the funds for payment are deducted from your bank account. Before the advent of quick electronic check-clearing, it was advantageous for companies to open many bank accounts in disparate locations to maximize float. By doing so, these companies can maximize the interest on their accounts before their funds are deducted.

Imagine that we are such a company well on our way to maximize profits. Define the following sets of values:

+   Let $$B$$ be a set of banks with which we can open bank accounts.
+   Let $$P$$ be the set of people to whom we make payments.
+   Let $$v_{ij} \geq 0$$ be the float created when we pay payee $$j \in P$$ from bank account $$i \in B$$.

Furthermore, suppose that we are limited to opening at most $$k$$ bank accounts. Each bank will be used to pay one of our people although one bank can pay multiple people if it is optimal to do so.

Our goal is to find a set of banks $$S \subseteq B$$ with $$|S| \leq k$$ that maximizes our total float among all of payees. To do so, we observe that from our chosen subset $$S$$, for each payee $$j$$ we want choose the bank $$i$$ from $$S$$ that maximizes $$v_{ij}$$. Thus, our overall objective is to find a subset $$S$$ that maximizes the following function $$V(S)$$:

$$
V(S) = \sum_{j \in P} \max_{i \in S} v_{ij}.
$$

Give a _natural greedy approximation algorithm_ for this problem. You do not need to prove a bound for this algorithm, but you should argue (in a few sentences) why your choice of greedy heuristic is likely to be "optimal" insofar as a greedy approach might go.

(_Hint_: start with an empty set of banks. Until we reach the limit $$k$$, greedily choose a new bank to add to the solution. How can we use $$V(S)$$ to determine which bank to add at each step?)

|___|
