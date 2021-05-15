---
title: "「Network」6 Normal Approximation of Local Structure"
subtitle: "Normal Approximation - Stein method"
layout: post
author: "Linsui"
header-style: text
tags:
  - Network
---

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/Network/06.pdf" target="_blank">「Network」6 Normal Approximation of Local Structure</a>.

# Normal Approximation

In this part, we want to approximate the number of triangle with normal  distribution in the sense of weak convergence. This approach is called Stein method.

## Total Variation Distance

Total variation distance measures the similarity between two distributions. It is defined as
$$
d_{T V}(P, Q)=\sup _{A \subset \mathbb{Z}^{+}}|P(A)-Q(A)| .
$$

We use $\mathbb{Z}^+$ because Poisson distribution is discrete. For continuous distribution, we use $A\subset \mathbb{R}$.

## A Stein characterisation

### An equivalent expression of Normal

$W \sim \mathcal{N}(0,1)$  if and only if for all continuous and piecewise continuously differentiable functions $f: \mathbb{R} \rightarrow \mathbb{R}$ with $\mathbb{E}\left|f^{\prime}(W)\right|<\infty$
$$
\mathbb{E}[W f(W)]=\mathbb{E} f^{\prime}(W).
$$

### Stein Equation

Stein Equation for normal distribution (for $h$) is 
$$
f^{\prime}(w)-w f(w)=h(w)-N h.
$$
where $Nh = \mathbb{E}h(Z)$

Note that the right side becomes total variation after taking expectation and maximum. The solution is
$$
\begin{aligned}
f_{h}(w) &=e^{\frac{w^{2}}{2}} \int_{-\infty}^{w}(h(x)-N h) e^{-x^{2} / 2} d x \\
&=-e^{\frac{w^{2}}{2}} \int_{w}^{\infty}(h(x)-N h) e^{-x^{2} / 2} d x .
\end{aligned}
$$
and it satisfies 
$$
\left\|f_{h}\right\| \leq 2\left\|h^{\prime}\right\| ; \quad\left\|f_{h}^{\prime}\right\| \leq \sqrt{\frac{2}{\pi}}\left\|h^{\prime}\right\| ; \quad\left\|f_{h}^{\prime \prime}\right\| \leq 2\left\|h^{\prime}\right\| .
$$

### Stein Summary

Attributing to the equivalent expression of Normal, we could measure the distribution of $W$ with Normal distribution with
$$
\sup _{h \in \mathcal{H}}|\mathbb{E} h(W)-N h|=\sup _{f_{h}}\left|\mathbb{E} f_{h}^{\prime}(W)-\mathbb{E}\left[W f_{h}(W)\right]\right|
$$

## Application

### Sum of iid Binomial distribution

Let $X_{1}, X_{2}, \ldots$ be independent with mean zero and same variance $\operatorname{Var}\left(X_{i}\right)=\frac{1}{n}$; denote $W=\sum_{i=1}^{n} X_{i}$. For any continuous and piecewise continuously differentiable function $h: \mathbb{R} \rightarrow \mathbb{R}$ we have
$$
|\mathbb{E} h(W)-N h| \leqslant\left\|h^{\prime}\right\|\left(\frac{2}{\sqrt{n}}+\sum_{i=1}^{n} \mathbb{E}\left|X_{i}^{3}\right|\right)
$$

### Local Dependence

#### dissociated decomposition

Denote $X_{i}, i \in I$  where  $I$ be a finite index set. Denote $W=\sum_{i \in I} X_{i}$ and suppose $\forall i \in I$ there is a set $K_{i} \subset I$ with
$$
W=W_{i}+Z_{i} \text { with } Z_{i}=\sum_{k \in K_{i}} X_{k}, \quad i \in I
$$
s.t. $W_{i}\perp X_{i}$. Further assume that
$$
W_{i}=W_{i k}+V_{i k} \text { with } V_{i k}=\sum_{j \in K_{k} \backslash K_{i}} X_{j}
$$
for $i \in I, k \in K_{i}$ so that $W_{i k}$ is independent of the pair $\left(X_{i}, X_{k}\right)$.

#### Bound for dissociated decomposition

With the notation above, assume that

- $X_{i}, i \in I$ are mean zero  and that $\operatorname{Var}(W)=1$;
- $k \in K_{i} \Longleftrightarrow i \in K_{k}$. 

Then, for any continuous and piecewise continuously differentiable function $h$,
$$
\begin{array}{l}
|\mathbb{E} h(W)-N h| \\
\leqslant ||4 h^{\prime} \| \sum_{i \in I} \sum_{j, k \in K_{i}}\left(\mathbb{E}\left(\left|X_{i} X_{j} X_{k}\right|+\mathbb{E}\left(\left|X_{i} X_{j}\right|\right) \mathbb{E}\left(\left|X_{k}\right|\right)\right)\right.
\end{array}
$$

### Normal Approximation for Triangles in ER model

Denote $W$ denote as standardised number of triangles in ER model with $p \leq \frac{1}{2}$ and $n \geq 3 .$ Then, for any continuous and piecewise continuously differentiable $h$,
$$
|\mathbb{E} h(W)-N h| \leqslant \frac{4}{3} \times \frac{29 n^{5} p^{3}}{\sigma^{3}}\left\|h^{\prime}\right\|
$$
When $p$ does not depend on $n$ then this expression is of order $O\left(n^{-1}\right)$.

*Note*: Standardised version of $Y_{\alpha}=a_{u, v} a_{v, w} a_{u, w}$ (Triangle with vertexes $(u,v,w)$) is
$$
X_{\alpha}=\frac{Y_{\alpha}-p^{3}}{\sqrt{\operatorname{Var}(T)}}
$$