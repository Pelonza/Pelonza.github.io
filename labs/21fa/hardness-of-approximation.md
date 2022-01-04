---
title: Hardness of Approximation
layout: content
mathjax: true
---

::: definition
Consider $n$ jobs that must be scheduled on a single sequential processor.
Define the following constants for each job $j$:

+   $p_j$, the processing time of $j$.
+   $r_j$, the release date of $j$, _i.e._, $j$ cannot start before time $r_j$.
+   $d_j$, the due date of $j$.

Define a _valid schedule_ to be an assignment of start times to jobs that denote when the job starts.
Furthermore, the release dates of each job are respected and no job's execution overlaps another job's execution.

With such a schedule, define:

+   $C_j$, the time that job $j$ completes.
+   $L_j$, the lateness of job $j$, _i.e._, $L_j = C_j - r_j$.

Define the _minimum lateness job scheduling problem_ to be the problem of finding a valid schedule for a set of jobs that minimizes the lateness of the latest job in the schedule.
:::

Show that the following algorithm that finds a scheduling of the jobs:

> When the processor is idle, schedule an available job with the earliest due date.

Is a $2$-approximation algorithm for this problem.
