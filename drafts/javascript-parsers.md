---
title: "A Tour of JavaScript Parsers"
date: "2018-10-09"
direction: "ltr"
---

A quick overview of some popular tools for parsing JavaScript and their output
formats.
<!-- end -->

*This post is a draft.*

## Background

- what is parsing?
- where is javascript usually parsed?
- why are there so many javascript parsers?
- what are some of the most popular javascript parsers?
- what some of the most popular output formats?
- how do parsers deal with JavaScript extensions?

## Parsing

Parsing is the action of discovering the language constructs encoded in a
language text. In programming this usually takes the form of producing an
abstract syntax tree from an input text. The encoded constructs of a
programming language usually determine it expressiveness. But not necessarily.

## A Standard AST

An AST is normally not an end-product by itself. AST's are usually used as
input to other steps in pipeline. They are either used to compile the text into
another language or used by a runtime to execute a program. Another important
class of tools that use AST's are static analyzers whose role is to run
analysis on a program text without running it. Linters is one of the main tools
in the static analysis family.

Since AST's are an important input for several subsequent steps in the analysis
or execution of a program, it is useful to agree on a standard AST that can be
produced by a number of parsers. This way tools can pick and choose which
parsers they work with while making sure that the resulting AST will be the
same.

## JavaScript Parsers



### Esprima

Esprima was the orignal JavaScript parser that ESLint used for subsequent
static analysis. Esprima however was slow to adopt new versions of the
JavaScript and that left ESLint behind on language versions. These shortcomings
of Esprima led the ESLint team to build their own parser that uses Acorn.

### Acorn


### Espree

Espree is the ESLint project implementation of a JavaScript parser. It builds
on Acorn but augments Acorn to match the Esprima API. The ESLint team reasoning
behind this is that a number of tools rely on the Esprima API and in this way
Espree can still support the Esprima API while bringing in the flexibility of
the Acorn parser.

### Espree vs Esprima
https://github.com/eslint/espree#why-another-parser

### Babel Parser

### Esprima

### Espree(not to be confused with Estree)
