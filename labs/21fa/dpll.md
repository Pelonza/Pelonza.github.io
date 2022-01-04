---
title: Boolean Constraint Propogation
layout: content
mathjax: true
---

In today's class, we talked about Davis-Putnam-Logemann-Loveland (DPLL) algorithm for deciding satisfiability of CNF formulae.
In our short lab for today, we'll work through some examples of using DPLL.

# Problem 1: Satisfying or Not

Use DPLL to efficiently find satisfying assignments for the following boolean formulae:

\begin{align}
\phi_1 =&\; (x4 \vee x4 \vee x1) \wedge (x4) \wedge (\neg x3) \wedge (\neg x1 \vee x3) \\
  \wedge &\; (\neg x2 \vee x2 \vee \neg x4) \wedge (\neg x4 \vee \neg x3 \vee \neg x4 \vee \neg x3 \vee \neg x5) \wedge (\neg x4 \vee x5 \vee x5 \vee \neg x2) \\
  \wedge &\; (\neg x4 \vee \neg x3 \vee \neg x1 \vee \neg x4 \vee x4) \wedge (x2) \wedge (x5 \vee \neg x5)
\end{align}

\begin{align}
\phi_2 =&\; (x3 \vee \neg x1 \vee x4) \wedge (\neg x4 \vee x1 \vee \neg x4) \wedge (x4 \vee \neg x3 \vee x3) \\
  \wedge &\; (x4) \wedge (x4 \vee x4 \vee x3) \wedge (x3 \vee x1 \vee x2 \vee \neg x5 \vee x4) \\
  \wedge &\; \wedge (x2 \vee x2 \vee x1) \wedge (\neg x1 \vee \neg x4 \vee x1 \vee \neg x2) \\
  \wedge &\; \wedge (\neg x2 \vee x1 \vee x3 \vee \neg x2 \vee \neg x3) \wedge (\neg x5 \vee x5 \vee \neg x2 \vee x5).
\end{align}

Use DPLL to demonstrate why each of the following formulae are _not_ satisfiable:

\begin{align}
\phi_3 =&\; (\neg x1 \vee \neg x3) \wedge (\neg x1) \wedge (x1 \vee x3 \vee \neg x1) \wedge (\neg x5 \vee \neg x1 \vee x5) \\
  \wedge &\; (x2) \wedge (x2 \vee \neg x2) \wedge (x2 \vee \neg x2 \vee \neg x5) \wedge (\neg x2) \wedge (x3 \vee \neg x5) \wedge (x3 \vee \neg x1)
\end{align}

\begin{align}
\phi_4 = &\; (x2 \vee \neg x1 \vee x2) \wedge (x5 \vee \neg x1 \vee \neg x1) \wedge (\neg x5 \vee \neg x4 \vee x1) \\
  \wedge &\; (\neg x2 \vee x1 \vee \neg x5 \vee \neg x3 \vee \neg x1) \wedge (x4 \vee \neg x1 \vee x1) \wedge (x5) \\
  \wedge &\; (\neg x5) \wedge (x5 \vee x1 \vee \neg x2 \vee \neg x4) \wedge (\neg x1) \wedge (x2 \vee \neg x5 \vee \neg x5 \vee \neg x1 \vee x4)
\end{align}

# Problem 2: Heuristics

As you have noticed, unit propagation can go a long way towards simplifying SAT instances.
However, you may have also noticed that your _heuristic for choosing the next literal to explore_ is also relevant!

Based on your experiences with DPLL so far, suggest a polynomial-time heuristic that you can apply to guide your backtracking search in DPLL.
In a few sentences, justify why this heuristic might lead to a more productive search.
