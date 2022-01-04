---
title: "Reading 1: Introduction"
layout: course-content
course-number: CSC 341
course-title: Automata, Formal Languages, and Complexity Theory
---

# Introduction

Welcome to CSC 341!
In this course, we'll explore the *theory of computation*, a branch of computer science that develops abstract models of computation.
With these models of computation, we can:

+ Categorize like-problems according to their complexity.
+ Explore categories of computation to analyze their essential similarities and differences.
+ Exploit the common structure of problems to combine and transform them in novel ways.
+ Construct methods of solving one problem in terms of another.

The theory of computation is inherently a mathematical field—we need the precision of formal mathematics to create faithful computational models.
As such, we will also revisit the interplay between mathematical formalism and practical computer science.
While this course contains some of the most beautiful and mind-opening mathematics you will study in your undergraduate career, we also want to be pragmatic about our study.
The theory of computation contains practical concepts and algorithmic techniques that ought to be a part of our software development toolkits.

## Constructive Proof

In your previous mathematics courses, you learned about the structure of mathematics:

+ *Definitions* model some aspect of the world and set the context of our analysis.
+ *Propositions* propose properties about and relationships between these definitions.
+ *Proofs* establish the validity of these propositions.

The theory of computation is no different.
Definitions establish a particular model of computation.
We then state propositions that propose properties of that model and prove that those propositions are indeed true.

More often than not, we will resort to a particular form of proof, *constructive proof*, in our analyses.
A constructive proof is one where we establish the truth of a proposition by *building* an object that implies its validity.
For example, we might prove that a particular problem is computable by building a machine that computes that result.
Constructive proof is of particular interest to computer scientists because we are interested in *implementation*.
The resulting artifact of a constructive proof is usually an algorithm or machine that lends itself to a real-world implementation.

## Book Reading

In addition to course readings, we will also be reading from the required textbook for the course:

+ *Introduction to the Theory of Computation*, Sipser.

For next class, read through §0 (Introduction) for an overview of the field of the theory of computation as well as a review of the background mathematics for the course.
Pay special attention to the section in §0.2 (Strings and Languages) for the definitions of strings and languages, a core concept in this course that you will have likely not encountered in  a formal setting.

## Course Cadence

Every course reading will be accompanied by a small set of problems to allow you to work with the concepts introduced therein.
These problems, along with the daily exercises assigned during the previous class, are due online before the next class period.
The class activities---lectures, individual tasks, and group work---will assume that you have completed both the reading and its associated problems.
If you have questions, it is your responsibility to work with your peers or the course staff in-person or online to resolve them before class!

---

**Exercise (Setup Your Development Environment)**

For this first reading, you do not need to turn in anything.
However, take the time to ensure that your development environment for the course is ready to go.

We'll be using LaTeX typesetting system for writing up homework solutions.
LaTeX is the de facto standard in computer science and other mathematics-oriented disciplines for producing technical documents.
I suggest the following two ways of developing documents in LaTeX:

+ Using the Overleaf service ([https://overleaf.com](htps://overleaf.com)), which provides a cloud-based IDE for LaTeX document development.
+ Using LaTeX on MathLAN or a personal machine through a TeXLive installation ([https://tug.org/texlive](https://tug.org/texlive)).
  You can then edit and compile LaTeX documents through the IDE provided by your system or through the command-line tools if you already have a terminal-based workflow.

Choose one of these options and work through the Overleaf 30 minute tutorial on the basics of LaTeX if you are unfamiliar with it:

+ <https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes>

In class, we will briefly review the basics of LaTeX and the spend the bulk of our time reacquainting ourselves with mathematical formalism and proof.
