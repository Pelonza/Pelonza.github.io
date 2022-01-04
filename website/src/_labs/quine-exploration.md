---
title: Quine Exploration
layout: content
mathjax: true
date: 2021-11-22
---

The recursion theorem when stated in terms of Turing machines can feel rather abstract.
However, we can apply the heart of the recursion theorem towards a fun programming activity, _quines_.
Quines are programs that produce themselves as output.
In this lab, we'll try to map the proof of the recursion theorem into a general strategy for developing quines.

# Problem 1: Review Yourself

First, let's review the construction of the $\text{SELF}$ machine from the reading.
Recall that the machine is composed of two Turing Machines, $A$ and $B$.
Discuss with your group and ultimately answer in your own words (not the book's):

1.  What does $A$ do?
2.  What does $B$ do?
3.  How does $\text{SELF}$ use $A$ and $B$ to accomplish its behavior, _i.e._, leave its own description, $\langle \text{SELF} \rangle$ on the tape?

Check your answers with a member of the course staff before moving on.

# Problem 2: Text to Source

The reading presented a textual version of $\text{SELF}$ that is slightly closer to the:

> Print two copies of the following, the second in quotes:
> "Print two copies of the following, the second in quotes:"

Intuitively, we read the first line as a command and the second, quoted line as the object the command manipulates.
This is analogous to the distinction between strings and source code, say, in Python:

```python
>>> 1+1     # this evaluates to the number 2
>>> "1+1"   # this evaluates to the string "1+1"
```

Mapping this back onto the Turing Machine construction:

+   $A$ is the quoted text, _i.e._, the second line, and
+   $B$ is the "command" text, _i.e._, the first line.

Use this outline of $\text{SELF}$ to build a small quine in a programming language of your choice---I recommend either Python or C.
Some notes about your construction:

There are two main difficulties you will encounter carrying out this construction in a real programming language:

1.  You need to translate "print this string" where the string contains (roughly) the source code of the program.
    Using a local variable to store this string first (analogous to $A$ being the quoted text) is a good starting point.
2.  While a seemingly benign comment in the textual version of $\text{SELF}$, "the second in quotes" is integral to
    capture $A$ in the output.
    This also becomes somewhat problematic in a real programming language for a technical reason: string quotation.
    In other words, `"""` is not a well-formed string in most languages!
    You would typically need to escape the quote, _i.e._, `"\""`, but then printing this string yields `"""` and not `"\""`
    which is what the source would say!
    You will need an alternative way to put "the second in quotes" other than using quotes themselves.
    Remember that many languages allow you to print characters via ASCII codes, avoiding the need to write down a quote directly!

(A final note, I am well aware that many quines are on the Internet already.
Please try not to look at these while you do this part of the lab.
The fun in this is discovering the construction yourself!)

(For fun: can you write an _ouborous_ quine, _e.g._, a quine in Python that outputs a quine in C that outputs the original quine in Python again?)

# Problem 3: Lambdas

In the previous problem, our quine operated by printing and then patching up the string after the fact via string interpolation.
One might wonder if this is a weird artifact of string interpolation that is more a "hack" than what the recursion theorem is getting at.
It turns out that we can achieve the effects of the recursion theorem with just functions!
Consider the following code snippets in Racket:

~~~racket
# Code snippet #1
((lambda (x) (x x)) (lambda (x) (x x)))

# Code snippet #2
(define Y
  (lambda (t)
    ((lambda (f)
       (t (lambda (z) ((f f) z))))
     (lambda (f)
       (t (lambda (z) ((f f) z)))))))

(define fact
  (lambda (f)
    (lambda (n)
      (if (= n 0)
          1
          (* n (f (- n 1)))))))

(define fact5 ((Y fact) 5))
~~~

1.  Try out each code snippet in Racket to get a feel for what it does.
    +   For code snippet #1, you can run it directly in the REPL, _i.e._, it is an expression rather than a function declaration.
    +   For code snippet #2, you can put the definitions in a source file and inspect the rules of `fact5`.

2.  In a few sentences, explain at a high-level what each snippet does and how it accomplishes that goal.
    In code snippet #1, identify roughly what is $A$ and $B$ in the construction.
    In code snippet #2, identify what the `f` parameter is in the definition of `fact`.

3.  Use code snippet #2 and $Y$ to write down a recursive definition for `(fib n)` which returns the `n`th Fibonacci number, defined recursively as:

    \begin{align}
    \mathsf{fib}(0) =&\; 0 \\
    \mathsf{fib}(1) =&\; 1 \\
    \mathsf{fib}(n) =&\; \mathsf{fib}(n-1) + \mathsf{fib}(n-2)
    \end{align}
