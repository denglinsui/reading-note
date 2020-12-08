---
title: "「Large Sample」1 Concentration Inequality"
subtitle: "Concentration Inequality - Chernoff & Hoeffding & Bernstein Inequality"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Large Sample
  - Course
  - 笔记
---

#  Concentration Inequality

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/01.pdf" target="_blank">「Large Sample」1 Concentration Inequality</a>.

## Chernoff Bound

Given r.v. $X$, if $\varphi(\lambda)=\mathbb{E}\left\{e^{\lambda(X-\mu)}\right\},\forall \lambda\in[0,b]$, then by 

- applying Markov Inequality to  $Y=e^{\lambda(X-\mu)}$
- Optimize $\lambda$.

we can get
$$
\log [\mathbb{P}\{(X-\mu) \geq t\}] \leq-\sup _{\lambda \in[0, b]}\left(\lambda t-\log \left[\mathbb{E}\left\{e^{\lambda(X-\mu)}\right\}\right]\right)
$$

## Hoeffding Bound

Hoeffding bound is obtained by controlling the moment generating function via sub-gaussian, getting an explicit expression of the conjugate function and optimize $\lambda$.

### Subgaussian

$X$ is a sub-gaussian with parameter $\sigma^2$ if it satisfies
$$
\mathbb{E}\left\{e^{\lambda(X-\mathbb{E} X)}\right\} \leq \exp \left(\frac{\lambda^{2} \sigma^{2}}{2}\right), \forall \lambda \in \mathbb{R}
$$

### Hoeffding's Inequality

If $X_{i}$ are sub-gaussian with parameter $\sigma_{i}^{2}$ , then
$$
\mathbb{P}\left\{\frac{1}{n} \sum_{i=1}^{n}\left(X_{i}-\mathbb{E} X_{i}\right) \geq t\right\} \leq \exp \left(-\frac{n^{2} t^{2}}{2 \sum_{i=1}^{n} \sigma_{i}^{2}}\right)
$$

## Bernstein Bound

Hoeffding bound only uses the information of the first moment. If we use the higher moment information, then we can get a shaper (up to a constant) bound than it (For bounded random variable).

### Bernstein Inequality

Consider $X_1,\cdots,X_n$ are independent mean $0$ random variable. If $X_i\leq1$ a.s., then for $\epsilon>0$, we have
$$
\mathbb{P}\left(\frac{1}{n} \sum_{i=1}^{n} X_{i}>\epsilon\right) \leq \exp \left\{\frac{n \epsilon^{2}}{2\left(\sigma^{2}+\epsilon / 3\right)}\right\}
$$


# Reference

- [Concentration Inequality: Lecture Notes](http://shjkx.wang/index.php/%E8%AE%A8%E8%AE%BA:%E7%BB%9F%E8%AE%A1%E5%A4%A7%E6%A0%B7%E6%9C%AC%E7%90%86%E8%AE%BA_%E9%9B%86%E4%B8%AD%E4%B8%8D%E7%AD%89%E5%BC%8F)

  



