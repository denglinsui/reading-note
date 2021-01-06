---
title: "「Large Sample」5 Discretization"
subtitle: "Discretization - Covariance Estimation"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Large Sample
  - Course
  - 笔记
---

#  Discretization

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/05.pdf" target="_blank">「Large Sample」5 Discretization</a>.

## Weyl Inequality

The non-increasing ordered singular value of $A,B\in \mathbb{R}^{m\times n}$, $\max _{k=1, \ldots, \min (m, n)}\left|\sigma_{k}(A)-\sigma_{k}(B)\right| \leq\|A-B\|_{\mathrm{op}}=\sigma_{\max }(A-B)$

*Hint*: $\sigma_{k}(A)=\min_{\dim(V)=n-k+1 }\max_{v\in V;\|v\|=1} v^T Av$, in addition,  $\sigma_{k}(A)=\max _{\dim(V)=k} \min_{x \in V ;\|x\|_{2}=1}\|A x\|_{2}$

## Covariance Estimation

If $X_{1}, \ldots, X_{n}\in \mathrm{SG}_{d}\left(\sigma^{2}\right)$, then $\forall\delta \in(0,1),\exists C>0$
$$
\mathbb{P}\left(\|\widehat{\Sigma}-\Sigma\|_{\text {op }} \leq \sigma^{2} C \min \left\{\sqrt{\frac{d+\log (2 / \delta)}{n}}, \frac{d+\log (2 / \delta)}{n}\right\}\right) \geq 1-\delta
$$
where $\widehat{\Sigma}=\frac{1}{n} \sum_{i=1}^{n} X_{i} X_{i}^{\mathrm{T}}$ .

**Proof Sketch**: 

- Discretization (Use $y$ close enough to $x^*$ s.t. $\|A\|_{\mathrm{op}}=\left|x^{*\mathrm{T}} A x^*\right|)$:  

  $\|A\|_{\text {op }}=\max _{x \in \mathbb{S}^{n-1}}\left|x^{\mathrm{T}} A x\right| \leq(1-2 \epsilon)^{-1} \max _{y \in \mathcal{N}_{\epsilon}}\left(y^{\mathrm{T}} A y\right)$

- Use summation bound maximum: 

  $\max _{y \in \mathcal{N}_{\epsilon}}\left(y^{\mathrm{T}} A y\right)\leq \sum _{y \in \mathcal{N}_{\epsilon}}\left(y^{\mathrm{T}} A y\right)$

- Bound the cardinality of $\mathcal{N}_\epsilon$ by volume comparison theorem;

  $\sum_{\mathcal{N}_{\epsilon}}\left(Y^{\mathrm{T}} A Y\right)\rightarrow |\mathcal{N}_{\epsilon}|Y^{\mathrm{T}} A Y$

- Use the concentration inequality to bound $Y^{\mathrm{T}} A Y$.

  



# Reference

- [Discretization](http://shjkx.wang/index.php/%E7%BB%9F%E8%AE%A1%E5%A4%A7%E6%A0%B7%E6%9C%AC%E7%90%86%E8%AE%BA_%E4%B8%80%E6%AD%A5%E7%A6%BB%E6%95%A3%E5%8C%96%E6%96%B9%E6%B3%95)

- [Singular Value](https://en.wikipedia.org/wiki/Singular_value#:~:text=The%20singular%20values%20are%20no)

  



