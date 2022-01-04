---
title: Demonstration Exercise 1
layout: content
mathjax: true
---

Demonstration exercises are your opportunity to showcase your mastery of the week's material.
In lab, you gain practice employing the fundamental skills we introduce in class.
In contrast, the demos are _integrative_ in nature, requiring to put those skills _into context_ as well as _mix different skills together_ to solve problems that are more like the ones you find in the real world.

# Formatting and Submitting Your Work

Create a PDF (either generated from LaTeX or an appropriate Markdown workflow) for each demonstration exercise, using headings to label each problem.
Your write-ups for each problem should reflect good writing principles and mathematical style:

+   Grammatically correct English prose and mathematics.
+   Structure of the prose made obvious through subheadings, paragraphs, and lists.
+   Math appropriately integrated into the prose as needed.

To achieve this, you will need to set aside ample time for revision and editing of your work before the deadline.
Approach the demonstration exercises not like a one-and-done problem set, but as a _writing assignment_ where you are putting in work that you eventually refine into a polished, complete product.

When you are done, you should submit your PDF to Gradescope.

# Problem: Protocols

A powerful application of finite automata is the specification and verification of _protocols_.
In this problem, we'll examine a protocol between a client and a conference management server (CMS) such as [HotCRP](https://hotcrp.com).
A client to this system may be an _author_ editing a paper for a review.
That same client might also be a _reviewer_ editing reviews for papers submitted to the conference.
Such a system segregates the two _roles_ so that authors cannot edit reviews of other papers they are in competition with.

The client may issue the following commands to the server:

+   Connect
+   Change role to author
+   Change role to reviewer
+   Edit paper
+   Edit review
+   Disconnect

A valid _session_ between the client and CMS adheres to the following rules.

1.  The client must connect to the server before performing any other action.
2.  Once connected, the client is initially given the author role.
3.  While connected, the client can switch their role between author and reviewer. 
    (Presumably, the client needs to have proper rights to switch roles, but that is not captured in this protocol.)
4.  As an author, the client can edit papers but not reviews
5.  As a reviewer, the client can edit reviews but not papers.
6.  The client cannot connect to the server if it is already connected.
7.  The client must disconnect from the server to end the session.

Note that in a single session, the client may connect and disconnect multiple times.
However, every valid session ends with the client disconnected from the CMS.

1.  Specify a language $L$ that captures valid sessions between the client and the server.
    $L$ should be specified in set-theoretic terms without appeal to a machine, and you should clearly define its alphabet $\Sigma$.

2.  Give a deterministic finite automata $D$ that recognizes $L$ in terms of a state diagram.
    You may either use a library to build this in your LaTeX/Markdown source, _e.g._, TikZ for LaTeX, or embed a picture of the diagram made in a third party tool or drawn by-hand.
    In your state diagram, you make take the shortcut that any transition from a state that is not drawn implicitly goes to an additional "dead" state.

3.  Prove that the DFA $D$ recognizes $L$.
    To do this:

    +   Assign a property to each state of $D$ that captures the essence of what that state means, _e.g._, the "disconnected" state.
    +   Perform an exhaustive case analysis on each state $q$ of $D$, arguing that each of $q$'s transitions is valid and preserves the property of $q$ according to the rules of the protocol.

4.  Give an implementation of the protocol in a real-world programming language of your choice, inlining the code in your write-up.
    Please use the `verbatim` environment in LaTeX or a fenced code-block in Markdown to do this.

    Implement the protocol as a function that takes two inputs:

    +   The current state of the client and
    +   The next command issued by the client

    And produces the next state of the client as output.
    You may choose any representation of states and commands appropriate for your chosen language.

5.  Finally, based on your experiences developing $D$ and your "real-world" implementation of the protocol, describe the pros and cons of first using a finite automata to _model_ a protocol _before_ going to implementation.
    Be open-minded about the benefits you consider not just in terms of correctness but also productivity.
