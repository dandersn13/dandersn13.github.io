---
layout: default
---

## Machine-learning for Littlewood-Richardson coefficients

The [Littlewood-Richardson coefficients](https://en.wikipedia.org/wiki/Littlewood–Richardson_rule#Littlewood–Richardson_coefficients) are numbers which show up as tensor product multiplicities in representation theory, as intersection numbers in algebraic geometry, and as structure constants for the multiplication of Schur polynomials.  They have an incredibly rich combinatorial structure, and there are many beautiful constructions realizing them as ways of counting various objects.

Inspired by [Kyu-Hwan Lee](https://automorphy.github.io/al-folio/)'s paper on [Kronecker coefficients](https://arxiv.org/abs/2306.04734), I decided to try training a model to learn Littlewood-Richardson coefficients.

The first natural question is to ask a classifier to recognize the _Horn cone_, that is, to decide whether a given coefficient is zero or not.

A Littlewood-Richardson coefficient $c_{\lambda,\mu}^{\nu}$ (henceforth, an _LR number_) depends on three partitions &mdash; $\lambda$, $\mu$, and $\nu$ &mdash; which we just represent as nonincreasing lists of nonnegative integers.  Considered as vectors in $\mathbb{R}^{3n}$, the triples of partitions for which $c_{\lambda,\mu}^{\nu}\neq 0$ form a convex cone, cut out by linear inequalities.  This is a highly structured set, and much is known about it.  (See for instance Fulton's 2000 [survey](https://www.ams.org/journals/bull/2000-37-03/S0273-0979-00-00865-X/S0273-0979-00-00865-X.pdf).)

I used Anders Buch's [lrcalc](https://sites.math.rutgers.edu/~asbuch/lrcalc/) to generate tables of triples of partitions, labelled by 0 or 1 according to whether the corresponding LR number is zero or not.  Then I fed this into [LightGBM](https://lightgbm.readthedocs.io/en/latest/index.html) to generate a decision-tree model, and test its predictive accuracy.  Trained on approximately half of the data for partitions fitting inside a 5-by-5 box, the model predicted 0 with 95.79% accuracy, and 1 with 99.59% accuracy.

Details are in the repository [ml-lrc](https://github.com/pseudoeffective/ml-lrc).

This exercise was mainly an experiment in setting up ML tools for algebraic combinatorics.  It's not clear (yet) if it will lead to interesting mathematics, or interesting interpretability ideas.  But here are a few quick observations:
* The model was surprisingly accurate, even with relatively little data and a small number of iterations to generate trees.
* The whole process was remarkably quick.  Not just the model training &mdash; that was the quickest part &mdash; but _everything_ from start to finish, including installing and learning LightGBM, generating and preparing the data, and (coarsely) analyzing the results.  I started on Sunday, having never worked in ML or data science, and I am posting this report on Thursday, after working on this project in spare time.  (The bulk of that time was spent setting up my GitHub page!)
* This is not to suggest that significant work in the subject is easy &mdash; far from it &mdash; but merely that with the user-friendly tools available now, the barrier to entry is low.  (Students take note...)

Thanks to [Kyu-Hwan Lee](https://automorphy.github.io/al-folio/) for his related work!
