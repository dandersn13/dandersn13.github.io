---
layout: default
---

## Machine learning Littlewood-Richardson coefficients

The [Littlewood-Richardson coefficients](https://en.wikipedia.org/wiki/Littlewood–Richardson_rule#Littlewood–Richardson_coefficients) are numbers which show up as tensor product multiplicities in representation theory, intersection numbers in algebraic geometry, and as structure constants for the multiplication of Schur polynomials.  They have an incredibly rich combinatorial structure, and there are many beautiful constructions realizing them as ways of counting various objects.

Inspired by [Kyu-Hwan Lee](https://automorphy.github.io/al-folio/)'s paper on [Kronecker coefficients](https://arxiv.org/abs/2306.04734), I decided to try training a model to learn Littlewood-Richardson coefficients.

The first natural question is to ask a classifier to recognize the _Horn cone_, that is, to decide whether a given coefficient is zero or not.
