---
title: "「Large Sample」6 Integral Entropy"
subtitle: "Integral Entropy - Chaining"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Large Sample
  - Course
  - 笔记
---

#  Integral Entropy

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/06.pdf" target="_blank">「Large Sample」6 Integral Entropy</a>.

## Basic Definition

- **Stochastic Process** $\left\{X_{t}\right\}_{t \in \mathcal{T}}$ indexed by $\mathcal{T}$:  A collection of real valued random variables.
- **Sub-Gaussian Process**  $\left\{X_{t}\right\}_{t \in \mathcal{T}}$ indexed by $(\mathcal{T},\rho)$: $\mathbb{E}\left[\exp \left\{\lambda\left(X_{s}-X_{t}\right)\right\}\right] \leq \exp \left\{\frac{\lambda^{2} \rho(s, t)^{2}}{2}\right\} \quad \forall \lambda>0, s, t \in \mathcal{T}$.
  - e.g.1. Let $\mathcal{T}=\mathbb{R}^{d}$ and $Z \sim N\left(0, \sigma^{2} I_{d}\right)$, then $X_t=t^TZ$ is a sub-gaussian process;
  - e.g.2. Consider $(T,\|\|)$, $X_i\in\mathcal{X}$,  $l: T \times \mathcal{X} \rightarrow \mathbb{R}$ and $|l(t, x)-l(s, x)| \leq\|t-s\|$. For a sequence of i.i.d Rademacher random variables $\epsilon_{i}$, then $Z_{t}=\sum_{i=1}^{n} \epsilon_{i} l\left(t, X_{i}\right)$ is a sub-Gaussian process with $\rho(s, t)=\sqrt{n}\|s-t\|$.

## Dudley's integral entropy

**Goal**: Bound $\mathbb{E}\left(\sup _{t \in \mathcal{T}} X_{t}\right)$ where $\left\{X_{t}\right\}_{t \in \mathcal{T}}$ is a separable sub-Gaussian and mean-zero process w.r.t the metric $\rho$;

**Tool**: Chaining;

**Conclusion**: $\mathbb{E}\left(\sup _{t} X_{t}\right) \leq 4 \sqrt{2} \int_{0}^{D / 2} \sqrt{\log N(u, \mathcal{T}, \rho)} \mathrm{d} u$

**Sketch Proof**: 

- Preparation: 

  - Let $\epsilon_{k}=2^{-k} D,$ where $D=\sup _{s, t \in \mathcal{T}} \rho(s, t)$;
  - Let $\mathcal{T}_{0}=\{t_0\}, \mathcal{T}_{1}, \mathcal{T}_{2}, \ldots$ be a sequence of $\epsilon_k$-net of $\mathcal{T}$;
  - Define $\pi_{k}: \mathcal{T} \rightarrow \mathcal{T}_{k}$ that $\rho\left(r, \pi_{k}(r)\right) \leq \epsilon_{k}$.

- Decomposition for $t\in\mathcal{T}_k$:

  - $X_{t}-X_{t_0}=\sum_{i=1}^{k}\left(X_{\pi _i\circ \ldots \circ \pi_k(t)}-X_{\pi_{i-1}\circ \pi_i^{\cdots} \cdot \circ \pi_k(t)}\right)$

- Bound the maximum for $t\in\mathcal{T}_k$:
  $$
  \begin{aligned}
  \max_{t\in\mathcal{T}_k}\left(X_{t}-X_{t_0}\right)&\leq \sum_{i=1}^{k}\max_{t\in\mathcal{T}_k}\left(X_{\pi _i\circ \ldots \circ \pi_k(t)}-X_{\pi_{i-1}\circ \pi_i^{\cdots} \cdot \circ \pi_k(t)}\right)\\
  &\leq \sum_{i=1}^{k} \max _{t \in T_{i}}\left(X_{t}-X_{\pi_{i-1}(t)}\right)
  \end{aligned}
  $$

  - $\max _{t \in T_{i}}\left(X_{t}-X_{\pi_{i-1}(t)}\right)$ is a finite maximum $\left|\mathcal{T}_{i}\right|$ of $\left(2^{1-i} D\right)^{2}$ -sub-Gaussian variables。

- Bound $\mathbb{E}\left\{\max _{t \in \mathcal{T}_{k}}\left(X_{t}-X_{t_{0}}\right)\right\}$ for $t\in\mathcal{T}_k$:

  - $\mathbb{E}\left\{\max _{t \in T_{i}}\left(X_{t}-X_{\pi i-1 t)}\right)\right\} \leq \sqrt{2 \cdot 2^{2(1-i)} D^{2} \log \left|\mathcal{T}_{i}\right|}$
  - Then

  $$
  \begin{aligned}
  \mathbb{E}\left\{\max_{t \in \mathcal{T}_{k}}\left(X_{t}-X_{t_{0}}\right)\right\} & \leq \sum_{i=1}^{k} \mathbb{E}\left\{\max _{t \in \mathcal{T}_i}\left(X_{t}-X_{\pi_{i-1} (t)}\right)\right\} \\
  & \leq \sum_{i=1}^{k} \sqrt{2 \cdot 2^{2(1-i)} D^{2} \log \left|\mathcal{T}_{i}\right|} \\
  &=\sum_{i=1}^{k} 2 \sqrt{2} D 2^{-i} \sqrt{\log N\left(D 2^{-i}, \mathcal{T}, \rho\right)} \\
  & \leq 4 \sqrt{2} \sum_{i=1}^{k} \int_{\left.D 2^{-(i+1}\right)}^{D 2^{-i}} \sqrt{\log N(u, \mathcal{T}, \rho)} \mathrm{d} u \\
  &=4 \sqrt{2} \int_{D 2^{-(k+1)}}^{D / 2} \sqrt{\log N(u, \mathcal{T}, \rho)} \mathrm{d} u
  \end{aligned}
  $$

- Bound $\mathbb{E}\left(\sup _{t} X_{t}\right)$ for $t\in\mathcal{T}$:
  $$
  \begin{aligned}
  \mathbb{E}\left(\sup _{t} X_{t}\right) &=\mathbb{E}\left\{\lim _{k} \sup _{t \in \mathcal{T}_{k}}\left(X_{t}-X_{t_{0}}\right)+X_{t_{0}}\right\} \\
  & \leq \liminf _{k} \mathbb{E}\left\{\sup _{t \in \mathcal{T}_{k}}\left(X_{t}-X_{t_{0}}\right)\right\} \\
  & \leq 4 \sqrt{2} \int_{0}^{D / 2} \sqrt{\log N(u, \mathcal{T}, \rho)} \mathrm{d} u
  \end{aligned}
  $$
  





# Reference

- [Integral Entropy](http://shjkx.wang/index.php/%E7%BB%9F%E8%AE%A1%E5%A4%A7%E6%A0%B7%E6%9C%AC%E7%90%86%E8%AE%BA_%E7%A7%AF%E5%88%86%E7%86%B5)

  

  




