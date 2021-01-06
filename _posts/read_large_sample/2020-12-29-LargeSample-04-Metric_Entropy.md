---
title: "「Large Sample」4 Metric Entropy"
subtitle: "Metric Entropy - Covering/Packing/Bracketing"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Large Sample
  - Course
  - 笔记
---

#  Metric Entropy

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/04.pdf" target="_blank">「Large Sample」4 Metric Entropy</a>.

## Some Definition

Suppose $(\Theta, \rho)$ is a metric space. 

- For $\epsilon>0$, $\left\{\theta^{i}\right\}_{i=1}^{N}$  is a **$\epsilon$-covering ** of $\Theta$ if $\forall\theta\in\Theta,\rho(\theta,\theta^i)\leq \epsilon$.
- **covering number** $N(\epsilon,\Theta,\rho)$: The cardinality of the minimum $\epsilon$-covering of $\Theta$.
- **metric entropy** $H(\epsilon,\Theta,\rho)$: $H(\epsilon,\Theta,\rho)=\log N(\epsilon,\Theta,\rho)$
- For $\delta>0$,  $\left\{\theta^{i}\right\}_{i=1}^{N}$  is a **$\delta$-covering ** of $\Theta$ if $\forall i\not=j,\rho(\theta^i,\theta^j)>\delta$.
- **packing number** $M(\delta,\Theta,\rho)$: The cardinality of the maximum $\delta$-packing of $\Theta$.

Suppose $\mathcal{F}$ is a functional family with measure $\mu$ on $\mathcal{X}$

- For $\epsilon>0$, $\left\{\left[l_{i}, u_{i}\right]\right\}_{i=1}^{M}$ is an **$\epsilon$-bracketing** if $\forall f \in \mathcal{F},$ $l_{i}(x) \leq f(x) \leq u_{i}(x), \forall x \in \mathcal{X}$ and $\left\|l_{i}-u_{i}\right\|_{L_{p}(\mu)} \leq \epsilon$.
- **bracketing number** $N_{[]}\left(\epsilon, \mathcal{F}, L_{p}(\mu)\right)$: The cardinality of the minimum $\epsilon$-bracketing of $\mathcal{F}$.

## Proporties

- $M(2 \epsilon, \Theta, \rho) \leq N(\epsilon, \Theta, \rho) \leq M(\epsilon, \Theta, \rho)$
- $N\left(\epsilon, \mathcal{F}, L_{p}(\mu)\right) \leq N_{[]}\left(2 \epsilon, \mathcal{F}, L_{p}(\mu)\right)$
- When $\mu$ is a probability measure: $N_{[]}\left(\epsilon, \mathcal{F}, L_{p}(\mu)\right) \leq N\left(\epsilon / 2, \mathcal{F}, L_{\infty}\right)=N_{[]}\left(\epsilon, \mathcal{F}, L_{\infty}\right)$

### Volume comparison lemma

Consider $\Theta=\left\{\theta \in \mathbb{R}^{d}:\|\theta\| \leq r\right\}$ with $\rho(x, y)=\|x-y\| , then
$$
\left(\frac{r}{\epsilon}\right)^{d} \leq N(\epsilon, \Theta, \rho) \leq\left(1+\frac{2 r}{\epsilon}\right)^{d}
$$
also
$$
d \log \frac{r}{\epsilon} \leq \log N(\epsilon, \Theta, \rho)=H(\epsilon, \Theta, \rho) \leq d \log \left(1+\frac{2 r}{\epsilon}\right)
$$
**Sketch proof**: 

- Lower bound: Compare the volume of $\Theta$ and $\epsilon$-ball;
- Upper bound: Compare the volume of $\Theta+\epsilon B$ with $\epsilon$-ball (via packing);

## Main Theorem(ULLN)

### Bracketing Number

Consider $X_{1}, \cdots, X_{n}\stackrel{i.i.d}{\sim}\mathbb{P}$  with $N_{[]}\left(\epsilon, \mathcal{F}, L_{1}(\mathbb{P})\right)<\infty,\forall\epsilon>0 .$ Then,
$$
\sup _{f \in \mathcal{F}}\left|P_{n} f-\mathbb{P} f\right| \stackrel{\mathbb{P}}{\rightarrow} 0 . \quad \text { ULLN }
$$

### Covering number

If $\mathcal{F}$ is a functional class with envelop function $F \in L_{1}(\mathbb{P})$ .  $\forall M>0$ and $\epsilon>0$ , we have $\log N\left(\epsilon, \mathcal{F}_{M}, L_{1}\left(P_{n}\right)\right)=o_{p}(n)$. Then,
$$
\left\|P_{n}-\mathbb{P}\right\|_{\mathcal{F}} \stackrel{\mathbb{P}}{\rightarrow} 0
$$
**Discussion**: The condition imposed on bracketing number is stricter than that on covering number, but bracketing number is harder to calculate than covering number.

# Reference

- [Metric Entropy](http://shjkx.wang/index.php/%E8%AE%A8%E8%AE%BA:%E7%BB%9F%E8%AE%A1%E5%A4%A7%E6%A0%B7%E6%9C%AC%E7%90%86%E8%AE%BA_%E5%BA%A6%E9%87%8F%E7%86%B5)

  



