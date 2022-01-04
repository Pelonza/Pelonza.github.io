(Design and reason about an approximation algorithm to an optimization problem.)

Recall that a bipartite graph $$G = (V, E)$$ is an undirected graph where the vertices $$V$$ can be divided into two disjoint subsets $$V = X \cup Y, X \cap Y = \emptyset$$ such that for every edge $$(x, y) \in E$$, $$x \in X$$ and $$y \in Y$$. In other words, for every edge, one of its vertices is drawn from $$X$$ and the other from $$Y$$.

Consider the problem of finding a _minimal_ subset of the vertices of the left-hand side of the graph $$X^* \subseteq X$$ such that every vertex of $$Y$$ shares an edge with a vertex of $$X^*$$.
For example in the following bipartite graph:

~~~
A---1
   /
  /
 /
B---2
 \ /
  \
 / \
C---3
~~~

The set $$\{\, A, C \, \}$$ covers all the right-hand elements, $$1, \ldots, 3$$. However, it is not minimal. The set $$\{\, B \,\}$$ also covers all the elements but is smaller.

Give a _natural greedy approximation algorithm_ for this problem. You do not need to prove a bound for this algorithm, but you should argue (in a few sentences) why your choice of greedy heuristic is likely to be "optimal" insofar as a greedy approach might go.

|___|
