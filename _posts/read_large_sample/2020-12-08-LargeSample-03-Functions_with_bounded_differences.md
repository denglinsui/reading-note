---
title: "「Large Sample」3 Functions with Bounded Differences"
subtitle: "Functions with Bounded Differences - The Efron-Stein inequality&Bounded Difference"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Large Sample
  - Course
  - 笔记
---

#  Functions with Bounded Differences

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/03.pdf" target="_blank">「Large Sample」3 Functions with Bounded Differences</a>.

## Basic Definition

- $X_1,\cdots,X_n$ are independent;

- $\mathbb{E}_i=\mathbb{E}(|X_1,\cdots.X_i)$;

- $Z=f\left(X_{1}, \ldots, X_{n}\right)$;

- $\Delta_{i}=\mathbb{E}_{i} Z-\mathbb{E}_{i-1} Z$;

- $Z-\mathbb{E} Z=\sum_{i=1}^{n} \Delta_{i}$;

- $\mathbb{E}^{(i)}=\mathbb{E}(|X_1,\cdots.X_{i-1},X_{i+1},\cdots,X_n)$

- Bounded difference with parameter $\{c_i\}$'s
  $$
  \sup _{x_{1}, \ldots, x_{n}, x_{i}^{\prime} \in \mathcal{X}}\left|f\left(x_{1}, \ldots, x_{n}\right)-f\left(x_{1}, \ldots, x_{i-1}, 	x_{i}^{\prime}, x_{i+1}, \ldots, x_{n}\right)\right| \leq c_{i}, 1 \leq i \leq n
  $$

- Martingale difference(MGD) sequence $\left\{\left(X_{i}, \mathcal{F}_{i}\right)\right\}$

  - $\left\{\mathcal{F}_{i}\right\}$ is a filtration.
  2. $X_{i}$ is integrable.
  3. $\mathbb{E}\left(X_{i} \mid \mathcal{F}_{i-1}\right)=0 \forall i \in \mathbb{N}$

- MGD $\sigma_i^2$-sub-Gaussian
  $$
  \mathbb{E}\left\{\exp \left(\lambda X_{i}\right) \mid \mathcal{F}_{i-1}\right\} \leq \exp \left(\lambda^{2} \sigma_{i}^{2} / 2\right) \forall i \in \mathbb{N}
  $$
  

## Efron-Stein Inequality

### Lemma

$$
\operatorname{Var}(Z)=\mathbb{E}\left\{\left(\sum_{i=1}^{n} \Delta_{i}\right)^{2}\right\}=\sum_{i=1}^{n} \mathbb{E}\left(\Delta_{i}^{2}\right)
$$

*Note*: Independence is not necessary here.

### Efron-Stein Inequality

Use the notation above 
$$
\operatorname{Var}(Z) \leq \sum_{i=1}^{n} \mathbb{E}\left\{\left(Z-\mathbb{E}^{(i)} Z\right)^{2}\right\} \stackrel{\text { def }}{=} v
$$
If $X_1',\cdots,X_n'$ are independent copies and denote $Z_{i}^{\prime}=f\left(X_{1}, \ldots, X_{i-1}, X_{i}^{\prime}, X_{i+1}, \ldots, X_{n}\right)$, then
$$
\begin{aligned}
v&=\frac{1}{2} \sum_{i=1}^{n} \mathbb{E}\left\{\left(Z-Z_{i}^{\prime}\right)^{2}\right\}=\sum_{i=1}^{n} \mathbb{E}\left\{\left(Z-Z_{i}^{\prime}\right)_{+}^{2}\right\}\\
&=\sum_{i=1}^{n} \mathbb{E}\left\{\left(Z-Z_{i}^{\prime}\right)_{-}^{2}\right\}=\inf _{Z_{i}} \sum_{i=1}^{n} \mathbb{E}\left\{\left(Z-Z_{i}\right)^{2}\right\}
\end{aligned}
$$

## Martingale Difference Sequence

If $\left\{X_{i}\right\}$ is $\sigma_{i}^{2}$ -sub-Gaussian $\mathrm{MGD}$, then for any $t \geq 0$,
$$
\mathbb{P}\left\{\sum_{i=1}^{n}\left(X_{i}-\mathbb{E} X_{i}\right) \geq t\right\} \vee \mathbb{P}\left\{\sum_{i=1}^{n}\left(X_{i}-\mathbb{E} X_{i}\right) \leq-t\right\} \leq \exp \left(-\frac{t^{2}}{2 \sum_{i=1}^{n} \sigma_{i}^{2}}\right)
$$
If $f: \mathcal{X}^{n} \rightarrow \mathbb{R}$ satisfies $c_{i}$ -bounded difference, then for any $t \geq 0$
$$
\mathbb{P}\left\{f\left(X_{1: n}\right)-\mathbb{E} f\left(X_{1: n}\right) \geq t\right\} \leq \exp \left(-\frac{2 t^{2}}{\sum_{i=1}^{n} c_{i}^{2}}\right)
$$

# Reference

- [Functions with Bounded Differences](http://shjkx.wang/index.php/%E7%BB%9F%E8%AE%A1%E5%A4%A7%E6%A0%B7%E6%9C%AC%E7%90%86%E8%AE%BA_%E6%9C%89%E7%95%8C%E5%B7%AE%E5%88%86%E5%87%BD%E6%95%B0%E6%96%B9%E6%B3%95)

  



