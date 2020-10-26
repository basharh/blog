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

The following is a quick tour of well-known JavaScript parsers. Where I've felt
that context is needed, I've provided background on the particular tool that
parser.

### Esprima

Esprima was the orignal JavaScript parser that ESLint used for subsequent
static analysis. Esprima however was slow to adopt new versions of the
JavaScript and that left ESLint behind on language versions. These shortcomings
of Esprima led the ESLint team to build their own parser that uses Acorn.

### Acorn

Unlike Babel parser, Acorn seems to be extensible to allow for arbitrary
syntax definitions.

### Espree

Espree is the ESLint project implementation of a JavaScript parser. It builds
on Acorn but augments Acorn to match the Esprima API. The ESLint team reasoning
behind this is that a number of tools rely on the Esprima API and in this way
Espree can still support the Esprima API while bringing in the flexibility of
the Acorn parser.

### Espree vs Esprima

https://github.com/eslint/espree#why-another-parser

### Babel Parser

Babel parser is a JavaScript parser for the Babel transformation tool. Babel is
a transpiler of modern JavaScript into JavaScript that could run on target
environments. There are a lot of moving parts to Babel and I am not 100% sure
of what they do. Babel tran

#### Babel Plugins

My understanding is that Babel will parse new JavaScript code. It will then
apply any transformations that are specified in the plugins configured.
Transformations are responsible for translating the AST produced by Babel into
target JavaScript code. The choice of plugins is determined by the target of
the transformation. It is up to the developer to choose those transformations
that will allow the latest JavaScript to work on their desired target
environments. One way to help with this is to use the `env` preset which is a
smart preset that will choose the plugins required based on a target
environment specification.

#### Target of Babel Plugins

I have yet to determine which version of JavaScript do the plugins transform.
Transformation plugins can theoretically apply any transformation to modern
JavaScript but do they always compile down to ES5? Or is the choice of target
customizable? There can be two options both of which might be supported. One is
to have different plugins apply a transformation of some modern JavaScript
feature into different targets. The other option would be to have a single
Babel plugin for a particular modern JavaScript feature be customizable via its
own options to target different environment.

To summarize, this means it could be multiple plugins for one feature where
each plugin targets one target versus a single plugin for one feature with
multiple targets based on plugin options.

#### User Extensions of JavaScript

I used to believe that Babel allows for custom JavaScript syntax
to be defined but this doesn't seem to be the case. Babel does seem to support
some extensions to JavaScript outside ECMAScript. Some examples of these
extensions are as flow, jsx, and typescript but this is done by babel
defined plugins.  I am not sure if Babel allows for custom extensions outside
the control of the Babel project but I don't think that's the case. In other
words, the Babel project doesn't seem to allow the babel parser to be extended
by arbitrary plugins.

#### The Babel Handbook

https://github.com/jamiebuilds/babel-handbook/blob/master/translations/en/README.md

### Esprima

### Espree(not to be confused with Estree)
