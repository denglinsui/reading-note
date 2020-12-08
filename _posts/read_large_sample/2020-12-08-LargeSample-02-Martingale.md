---
title: "「Large Sample」2 Martingale"
subtitle: "Martingale - Definition, Stopping Time and Convergence"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Large Sample
  - Course
  - 笔记
---

#  Martingale

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/02.pdf" target="_blank">「Large Sample」2 Martingale</a>.

## Basic Definition

- Under measurable space $(\Omega,\mathcal{F})$:	

- Filtration $\{\mathcal{F}_n\}$: $\mathcal{F}_0\subset\mathcal{F}_1\subset\cdots\mathcal{F}_\infty$.

- $\{\mathcal{F}_n\}$-adapted r.s. $M_n$: $M_n\in\mathcal{F}_n$

- Martingale $\{M_n\}$:

  - $\{\mathcal{F}_n\}$-adapted

  - $\mathbb{E}\left|M_{n}\right|<\infty$
  - $\mathbb{E}\left(M_{n+1} \mid \mathcal{F}_{n}\right)=M_{n} \quad \forall n$

- Sub-Martingale $\{M_n\}$:

  - $M_n\leq\mathbb{E}\left(M_{n+1} \mid \mathcal{F}_{n}\right) \quad \forall n$

- Super-Martingale $\{M_n\}$:

  - $M_n\geq\mathbb{E}\left(M_{n+1} \mid \mathcal{F}_{n}\right) \quad \forall n$

- $\{\mathcal{F}_n\}$-predictable r.s.$H_n$: $H_n\in\mathcal{F}_{n-1}$.

- Martingale $X$ transformation(through predictable $H$) $(H\cdot X)$:

  - $(H \cdot X)_{n}=\sum_{m=1}^{n} H_{m}\left(X_{m}-X_{m-1}\right)$
  - $(H \cdot X)_{0}=0$

- Stopping Time $T$: $[T=n]\in\mathcal{F}_n$.

## Proporties

### Transformation of martingale

- Martingle $M_n$ + $\phi$ convex + $\mathbb{E}\left(\left|\phi\left(M_{n}\right)\right|\right)<\infty\rightarrow \phi(M_n)$ ia a sub-martingale;
- Sub-martingle $M_n$ + $\phi$ non-decreasing&convex + $\mathbb{E}\left(\left|\phi\left(M_{n}\right)\right|\right)<\infty\rightarrow \phi(M_n)$ ia a sub-martingale;
- Example:
  - Martingle $M_n$ +$\mathbb{E}\left|M_{n}\right|^{p}<\infty\rightarrow|M_n|^p$ is a sub-martingale;
  - Sub-martingale $M_n\rightarrow(M_n-a)_+$ is a sub-martingale;
  - Super-martingale $M_n\rightarrow M_{n\wedge a}$ is a super-martingale.
- Martingle $X_n$+predictable&bounded $H_n\rightarrow (H\cdot X)_n$ is a martingale;
- Sub/Super-martingle $X_n$+predictable&bounded $H_n\geq0\rightarrow (H\cdot X)_n$ is a sub/super-martingale;
- Sub/Super-martingle $X_n$+$T$ is a stopping time $\rightarrow M_{n\wedge T}$ is a   sub/super-martingle.
  - Denote $H_n=\boldsymbol{1}_{T\geq n}$ predictable; 
  - Consider $(H\cdot M)=M_{n\wedge T}-M_0$.

### Doob Sub-martingale Decomposition

For any sub-martingale $\left\{\left(X_{n}, \mathcal{F}_{n}, \mathbb{P}\right), n \geq 0\right\}$, there is a unique decomposition 
$$
X_{n}=M_{n}+A_{n}
$$
where 

- $\left\{\left(M_{n}, \mathcal{F}_{n}, \mathbb{P}\right), n \geq 0\right\}$ is a martingale;
- $\left\{A_{n}, n \geq 0\right\}$ is predictable and non-decreasing.

*Hint*:  Denote $d_{j}:=X_{j}-\mathbb{E}\left[X_{j} \mid \mathcal{F}_{j-1}\right], d_{0}:=X_{0}$, then

- $M_{n}:=\sum_{j=0}^{n} d_{j}$
- $A_{n}:=X_{n}-M_{n}$

## Stopping Times

### Wald's Equation

- $X_{1}, X_{2}, X_{3}, \cdots$ are  $i . i . d .$ +$\mathbb{E}\left|X_{i}\right|<\infty$ + $T$ is a stopping time + $\mathbb{E}(T)<\infty$. Let  then$S_{n}=\sum_{i=1}^n X_{i}$,
  $$
  \mathbb{E} S_{T}=\mathbb{E} X \mathbb{E} T
  $$

- $X_{1}, X_{2}, X_{3}, \cdots$ are  $i . i . d .$ +$\mathcal{E}X_n=0$+$\mathbb{E}\left|X_{i}\right|^2=\sigma^2<\infty$ + $T$ is a stopping time + $\mathbb{E}(T)<\infty$. Let $S_{n}=\sum_{i=1}^n X_{i}$, then
  $$
  \mathbb{E} S_{T}^{2}=\sigma^{2} \mathbb{E} T
  $$

## Martingale Convergence Theorem

If $X_n$ is a non-negative super-martingale, the it converges to a a.s. finite $X_\infty$ and 
$$
\mathbb{E}\left(X_{\infty}\right) \leq \mathbb{E}\left(X_{0}\right)
$$

## Levy's 0-1 Law

Suppose $X$ defined on $(\Omega,\mathcal{F},\mathbb{P})$ and $\mathcal{F}_n$ is a filtration, then
$$
\mathbb{E}\left(X \mid \mathcal{F}_{k}\right) \rightarrow \mathbb{E}\left(X \mid \mathcal{F}_{\infty}\right), \quad k \rightarrow \infty
$$
a.s, and $L_1$.

## Doob's Maximal Inequality

Suppose $Y_n$ is a sub-martingale and $b\in\mathbb{R}$, denote  $
M_{N}= \max _{0 \leq n \leq N} Y_{n}$ , then
$$
b \mathbb{P}\left(M_{N} \geq b\right) \leq \mathbb{E}\left(Y_{N} \mathbf{1}_{\left\{M_{N} \geq b\right\}}\right) \leq \mathbb{E}\left(Y_{N}\right)
$$
*Hint*: Denote $T(\omega)=\inf\{n:Y_n(\omega)\geq b\}$ or $N$ if it's empty and decompose $\mathbb{E}Y_T\leq\mathbb{E}Y_N$ w.r.t to the set $[M_n\leq b]\cup[M_n\geq b]$. 

*Remark*: This inequality controls the maximum probability w.r.t the summation.



# Reference

- [Martingale: Lecture Notes](http://shjkx.wang/index.php/%E8%AE%A8%E8%AE%BA:%E7%BB%9F%E8%AE%A1%E5%A4%A7%E6%A0%B7%E6%9C%AC%E7%90%86%E8%AE%BA_%E9%9E%85%E5%9F%BA%E6%9C%AC%E7%90%86%E8%AE%BA)

  



