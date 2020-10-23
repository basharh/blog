---
title: "Making Sense of ESLint"
date: "2018-10-09"
direction: "ltr"
---

An overview of ESLint
<!-- end -->

#### Background

ESLint is one of those tools that have become indispensable for the modern
coding experience. Its integration with editors has also provided a great
benefit. Understanding the role of ESLint and its configuration is still
problematic and eslint configurations tend to be fragile due to it being one of
those tools that are seldom re-visited once its configured.

### Outline

- why eslint is so important
- the role of eslint in the current developer experience
- what does eslint do?
- the components of its configuration
- where does it apply?

#### Steps

- define linting in general
- define linting in the context of code
  - helps detect patterns that are not necessarily syntax errors but indicate
    potentially problematic or inaccurate code
- which languages does eslint support?
  - which variants of javascript does it support?
  - how does eslint adjust to the differnet runtimes or versions of javascript

#### Definitions

##### Linting as Uncovering Issues that are not Errors

In English `lint` is normally used as a noun. In programming, to lint is to
find issues in the code that are not necessarily errors but represent uses of
the languages that are probably unintended. Some examples of such issues
include declaring variables that are not used in the code or assigning a
variable to itself. Issues like this will not necessarily cause errors but
indicate locations in the code where the programmer is not doing what is
intended for the program.

##### Linting as uncovering issues that are not detectable by a compiler

Linting can also be defined as the process of finding issues in the code that
are not flagged by a compiler. In the case of interpreted programs the role
of linting becomes more important as there is no compilation step at all. The
set of all issues that a linter can indicate is not defined. Linting can flag
issues that might cause bugs or runtime errors but can also include issues with
code style or code formatting that have no effect on program behavior.

#### ESLint

The flexible role of a linter is one of the reasons why eslint can be a little
difficult to understand. So what is ESLint? ESLint is a linting tool that falls
in the category of linters of other languages. What makes eslint special
however is that its linting rules, ie the issues that it can test for, is
dynamic and pluggable. ESLint provides the framework for rules to be written by
anyone. And although it ships with some built-in rules, those rules are written
the same way as any rules written by someone wanting to introduce a new rule.

#### Challenges Poised by JavaScript

##### Evovling Standards

ESLint is built primarily to target JavaScript. JavaScript is a tricky language
to lint for a number of reasons. The first is that javascript itself is
constantly evolving. New standards are being released often and what
constitutes JavaScript at any point can change. This needs to be reflected in
the linting configuration that is used.

##### Different Runtimes

Another dimension to JavaScript is the runtime. JavaScript is an interpreted
language that is designed to run in different environments. For a most of its
life JavaScript ran soley on the browser and that environment was for the most
part defined. New server-side runtimes such as Node have introduced new
runtimes however. These runtimes with their specific environments require
special linting configurations as well to check if javascript is being used as
intended on those environments.

##### Babel And Transpilers

In addition to the evolving standards, modern users of javascript don't wait
for standards to be released or supported by their target runtimes to use a new
feature. New JavaScript features can be integrated into the language by using
pluggable transpilers. The most famous transpiler out there is Babel which lets
you use new features of JavaScript by using its plugin system.

##### Module Systems And Bundlers

JavaScript didn't have the concept of modules built into the language until
ES6. Prior to that there were two main standards to writing modules: AMD and
CommonJS. CommonJS in particular represented an extension to the language so it
didn't translate to JavaScript runtimes without some sort of transformation.
Note: Module behavior was dicated by libraries before it was standardized by
es6.  Prior to es6, module behavior was implemented by libraries(or loaders).
ESLint *probably* requires knowledge of the module system required by a
codebase so that it can properly apply the linting rules for it.

The support of commonjs in Nodejs was built-in to the runtime. In order
for commonjs modules to be used in the browser, they needed to be transformed.
