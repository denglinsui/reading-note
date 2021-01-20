---
title: "「Large Sample」8 U Statistics"
subtitle: "U Statistics - One Sample/ Unbiased Statistics"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Large Sample
  - Course
  - 笔记
---

#  Convergence

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/08.pdf" target="_blank">「Large Sample」8 U Statistics</a>.

## Definition

Assume a known function $h$ in $r$ arguments is

- permutation symmetric;
-  A unbiased estimator of parameter $\theta$: $\theta = \mathbb{E} h(X_1,X_2,\cdots, X_r)$.

A **U Statistics** with **kernel** $h$ is defined as:
$$
U=\frac{1}{\binom{n}{r}} \sum_{\beta} h\left(X_{\beta_{1}}, \ldots, X_{\beta_{r}}\right)
$$

## Property

U statistics

- is permutation symmetric in $X_1,X_2,\cdots,X_n$;

- has smaller variance than $h(X_1,X_2,\cdots, X_r)$;

- $U=\mathrm{E}\left(h\left(X_{1}, \ldots, X_{r}\right) \mid X_{(1)}, \ldots, X_{(n)}\right)$

- **Asymptotic Normality**: If $E h^{2}\left(X_{1}, \ldots, X_{r}\right)<\infty,$ then $\sqrt{n}(U-\theta-\hat{U}) \stackrel{\mathbf{P}}{\rightarrow} 0 .$ Consequently,
  the sequence $\sqrt{n}(U-\theta)$ is asymptotically normal with mean 0 and variance $r^{2} \zeta_{1},$ where, with $X_{1} \ldots \ldots X_{r}, X_{1}^{\prime} \ldots . X_{r}^{\prime}$ denoting i.i.d. variables,
  $$
  \zeta_{1}=\operatorname{cov}\left(h\left(X_{1}, X_{2} \ldots \ldots X_{r}\right), h\left(X_{1}, X_{2}^{\prime}, \ldots, X_{r}^{\prime}\right)\right)
  $$

# Reference

- [Asymptotic Statistics](https://www.cambridge.org/core/books/asymptotic-statistics/A3C7DAD3F7E66A1FA60E9C8FE132EE1D)

  

  




