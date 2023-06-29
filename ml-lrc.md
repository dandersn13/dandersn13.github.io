---
layout: default
---

## Machine-learning for Littlewood-Richardson coefficients

The [Littlewood-Richardson coefficients](https://en.wikipedia.org/wiki/Littlewood–Richardson_rule#Littlewood–Richardson_coefficients) are numbers which show up as tensor product multiplicities in representation theory, intersection numbers in algebraic geometry, and as structure constants for the multiplication of Schur polynomials.  They have an incredibly rich combinatorial structure, and there are many beautiful constructions realizing them as ways of counting various objects.

Inspired by [Kyu-Hwan Lee](https://automorphy.github.io/al-folio/)'s paper on [Kronecker coefficients](https://arxiv.org/abs/2306.04734), I decided to try training a model to learn Littlewood-Richardson coefficients.

The first natural question is to ask a classifier to recognize the _Horn cone_, that is, to decide whether a given coefficient is zero or not.

A Littlewood-Richardson coefficient $c_{\lambda,\mu}^{\nu}$ (henceforth, an _LR number_) depends on three partitions &mdash; $\lambda$, $\mu$, and $\nu$ &mdash; which we just represent as nonincreasing lists of nonnegative integers.  Considered as vectors in $\mathbb{R}^{3n}$, the triples of partitions for which $c_{\lambda,\mu}^{\nu}\neq 0$ form a convex cone, cut out by linear inequalities.  This is a highly structured set, and much is known about it.  (See for instance Fulton's 2000 [survey](https://www.ams.org/journals/bull/2000-37-03/S0273-0979-00-00865-X/S0273-0979-00-00865-X.pdf).)
