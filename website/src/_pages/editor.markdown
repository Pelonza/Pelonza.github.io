---
title: Unicode Editor
permalink: /editor/
layout: editor
editor: true
---

<form id="dummy"><textarea id="unicode-editor" rows=14>Enter text here...</textarea></form>

This simple text editor supports the entry of Unicode symbols with LaTeX commands.
LaTeX commands are parsed and automatically converted into their Unicode equivalents according to [unimathsymbols.txt](http://milde.users.sourceforge.net/LUCR/Math/).
It also saves your text to local storage so that it persists between sessions, _e.g._, you accidentally close your tab.
The implementation is somewhat janky and highly unoptimized—every edit is 𝒪(n)!—so don't write a book in this or anything.
