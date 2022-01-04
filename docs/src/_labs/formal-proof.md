---
title: Formal Proof
layout: content
mathjax: true
---

In this lab, we'll work on authoring proofs.
Try to be as rigorous, yet concise in your proofs as possible.
If you have any questions about levels of formality or formatting, please don't hesitate to ask!

## Problem 1: Formal Proof

Formally prove the following claims over strings.

::: claim
**Claim 1**: Call an element $u$ of a set $S$ and an associated binary operation over that set $(+) : S → S$ a _unit_ if $\forall x \in S \ldotp x + u = u + x = x$.
We claim that $ϵ$ is a unit for strings and concatenation over strings.
:::

::: claim
**Claim 2**: Let $x$ and $y$ be strings.
If $x$ is a prefix of $y$ and $y$ is a prefix of $x$ then $x = y$.
:::

(_Hint_: make this an algebraic argument based on the definition of prefix from the book!)

## Problem 2: Induction Revisited

Consider the following definitions regarding binary trees.

::: definition
**Definition (Binary Tree)**: a binary tree is either:

-   A _leaf_ or
-   A _node_ with two sub-trees, its _children_.

We define the _root_ of a binary tree to be a node that is not the child of any other node in the tree.
:::

::: definition
**Definition (Level and Height)**: the _level_ of a node in a binary tree is the length of the path from the root to that node.
The _height_ of a binary tree is the maximal level of any node in the tree.
We also use "level" to denote the _set of all nodes_ that share the same level in the tree.
:::

::: definition
**Definition (Complete and Perfect Trees)**: a tree is _complete_ if each of its levels contain its maximal number of possible nodes.
A tree is _perfect_ if each node of the tree contains zero or two children.
:::

Now prove the following claim by structural induction.

::: claim
Let $h$ be the height of a complete, perfect binary tree. If $n \leq h$,
then there are $2^n$ nodes at level $n$ of this tree.
:::

## Problem 3: Constructive Proof (Optional)

Chess is played on a $n \times n$ board (usually $n = 8$).
Consider the _rook_ piece, which can move in any number of squares in a cardinal (non-diagonal) direction. A _rook's tour_ is a sequence of moves for a single rook that causes the piece to visit _every_ square of the board _exactly once_.
When considering a tour, we are free to place our piece on the board at any position initially.
Also, we only consider a square visited if the piece _ends its movement_ on that square.

Prove via induction that there exists a rook's tour for any chessboard of size $n ≥ 1$.

(_Hint 1_: note that proving the existence of a rook's tour means constructing a rook's tour for an arbitrary board, _i.e._, designing an algorithm that generates the tour!)

(_Hint 2:_ pay attention to the details! This is not as straightforward of a proof as you might think!)
