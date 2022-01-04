---
title: Markdown
layout: content
mathjax: true
---

In this course, we will use [Markdown](https://daringfireball.net/projects/markdown/) and common extensions for rendering mathematics.
Markdown is a markup language is designed to be easily readable in its plaintext source format, but also flexible enough to capture common structure found in most documents.
Because of its simplicity, Markdown is versatile and can be compiled to a variety of document formats, including PDF and HTML.

# Markdown Tools

There are tons Markdown editors and compilers out there.
For this course, we are not picky about what you use as long as it doesn't get in the way of your learning.
Here are a few tools that you might consider based on your experience with other environments:

## Any Text Editor And Pandoc

If you are comfortable working at the Unix terminal, [Pandoc](https://pandoc.org) is a universal translator for document formats.
You can write your document in any readily available plaintext text editor, _e.g._, Vim or Emacs, and as needed, run Pandoc to convert your Markdown into a PDF.
While simple, the downside of this approach is that it doesn't provide a live preview of your document.
However, Markdown source is readable enough on its own that live preview isn't a necessity.

For example, once installed:

~~~terminal
$> pandoc document.md -o document.pdf
~~~

Will convert Markdown file `document.md` into a PDF, `document.pdf`.
Pandoc is available on MathLAN (the department's Linux cluster) if you happen to do your work on it.

## Visual Studio Code

A general development environment that is gaining in popularity is [Visual Studio Code](https://code.visualstudio.com/).
If you use Visual Studio Code or are interesting in picking it up, it is not difficult to install it along with the [Markdown+Math extension](https://marketplace.visualstudio.com/items?itemName=goessner.mdmath).
With VSCode, you will be able to edit Markdown with a live preview.
However, you will need to a do a little bit of juggling to export your work to a final PDF for submission.
You will either need to convert the file to HTML and then use the "print to PDF" feature of your operating system or use a conversion tool like Pandoc.

## Dedicated Desktop Applications

In addition to these solutions that integrate into existing developer workflows, there are also [many standalone Markdown editors](https://www.oberlo.com/blog/markdown-editors).
Some of these are paid (avoid those, unless you _really_ like the tool), and some of these are free.
Ultimately, you need an editor that:

1.  Supports math extensions.
2.  Gives you a live preview of your work.
3.  Has a way to output to PDF.

One such option is [Typora](https://typora.io/) which is currently free while it is still in beta.

## Cloud-hosted Options

Finally, if you aren't interested in installing programs, there are a number of cloud services that offer Markdown editing support.
The main one I'll recommend is [HackMD](https://hackmd.io/) which you will see me occasionally use in class.
Like VSCode+MDMath, outputting to PDF is a bit janky; you will ultimately need to "print to PDF" from your browser.

# Learning Markdown

Once you have a Markdown workflow in place, the good news is that Markdown is easy to learn.
Here is a brief code snippet exhibiting all of the features we need for the course:

~~~md
# This is a top-level header!

Look, I can write paragraphs! Amazing! I write them as blocks
of text. I can add in newlines as necessary to make things more
readable, but a new paragraph starts...

...when I add a blank newline in the middle. In addition, I can
**bold** text and _italicize text_ as well. I can also write in
monospace font for inline code like this: `(string-append s1 s2)`.
(p.s., those are backticks).

## Here's a subsection header!

I can also make lists with... bullets!

+   Note that to get nested bulleted lists.
+   I need to use 4-space indentation.
    -   Like this!
    -   You can use stars, pluses, or minuses for bullets...
    -   ...Markdown doesn't care.
+   You can also have numbered lists...
    1.  By using numbers!
    2.  Isn't that neat?
    3.  Wow!

Here is a quote block, useful for writing prose that should stick out.
You might use this to state a propert or claim

> **Claim**: the grass is
> always greener on the other side of the fence.

I can also write code blocks using triple backticks:

```
(define (length l)
  (match l
    ['() 0]
    [(cons _ xs) (+ 1 (length xs))]))
```
~~~

Try copy-pasting this into your Markdown editor to see the results!

For additional features, you can checkout the [Markdown Guide](https://www.markdownguide.org/) a free reference for the language.
