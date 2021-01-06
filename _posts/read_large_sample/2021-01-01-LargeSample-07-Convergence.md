---
title: "「Large Sample」7 Convergence"
subtitle: "Convergence - Convergence Rate/Convergence in LAW"
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

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/LargeSample/07.pdf" target="_blank">「Large Sample」7 Convergence</a>.

## Basic Notation

- $M_{n}(\theta) =\frac{1}{n} \sum_{i=1}^{n} l_{\theta}\left(X_{i}\right)=P_{n} l_{\theta}$
- $M(\theta) =\mathbb{P} l_{\theta}$
- $\Delta_{n}(\theta) =\left\{M_{n}(\theta)-M(\theta)\right\}-\left\{M_{n}\left(\theta_{0}\right)-M\left(\theta_{0}\right)\right\} 
  =\left(P_{n}-\mathbb{P}\right)\left(l_{\theta}-l_{\theta_{0}}\right)$
- $\mathcal{D}$: A metric space.

## Basic Definition

- **Modulus of Continuity** : 
  - $f:T\rightarrow\mathbb{R}$, $w_{f}(\delta)=\sup _{\rho(s, t)<\delta} \mid f(s)-f(t)$
  - $\mathbb{W}_{n}(\delta)=\sup _{d(\theta, \theta_0) \leq \delta}\left|\Delta_{n}(\theta)\right|$
- **Weak Convergence** $X_{n} \stackrel{d}{\rightarrow} X$: $\mathbb{E}\left\{f\left(X_{n}\right)\right\} \rightarrow \mathbb{E}\{f(X)\}$ for all bounded and (Lipschitz) continuous function $f$;
- **Tightness**: $X:\Omega\rightarrow \mathcal{D}$ is tight if $\forall \epsilon>0$, $\exists K\subset \mathcal{D}$ compact s.t. $\mathbb{P}(X \in K)>1-\epsilon$;
- **Asymptotically Tight**: $\{X_n\}:\Omega\rightarrow \mathcal{D}$ is asymptotically tight if $\forall\epsilon>0,\exists K\subset\mathcal{D}$, s.t. $\limsup _{n \rightarrow \infty} \mathbb{P}\left(X_{n} \notin K^{\delta}\right)<\epsilon$ where $K^{\delta}=K+\delta B(0,1)$.
- $L^\infty(T)=\{f:\|f\|_\infty <\infty\}$ where $T$ is compact;
- $UC(T,\rho)=\{f:T\rightarrow \mathbb{R} \text{ is uniformly continuous}\}$；
- **Equicontinuous**: $\mathcal{F}=\{f\}$ is equicontinuous if  $\lim _{\delta \downarrow 0} \sup _{f \in \mathcal{F}} w_{f}(\delta)=0$;
- **Asymptotically Equicontinuous**: $\{X_n\}$ is asymptotically equicontinuous if $\forall\epsilon,\eta>0,\exist$ finite partition of $T$, $\{T_1,\cdots,T_k\}$ s.t. $\limsup _{n \rightarrow \infty} \mathbb{P}\left(\max _{1 \leq i \leq k} \sup _{s, t \in T_{i}}\left|X_{n, s}-X_{n, t}\right| \geq \epsilon\right) \leq \eta$

## Theorems

### Prohorov Theorem

- If $X_{n} \stackrel{d}{\rightarrow} X$, $X$ is tight $\Leftrightarrow X_n$ is asymptotically tight;
- If  $X_n$ is asymptotically, then $\exist\{X_{n_k}\}\& X$ tight s.t. $X_{n_k} \stackrel{d}{\rightarrow} X$.

### Arzela-Ascoli Theorem

For compact metric space $(T,\rho)$

- $\mathcal{F} \subseteq U C(T, \rho)$ is relatively compact w.r.t supremum norm 

  $\Leftrightarrow$

2. $\mathcal{F}$  is uniformly equicontinuous and  $\exists t_{0} \in T$  s.t. sup $_{f \in \mathcal{F}}\left|f\left(t_{0}\right)\right|<\infty$

### Weak Convergence in $L^\infty(T)$

For $X_{n} \in L^{\infty}(T),$ for $X \in U C(T, \rho)$ is tight we have $X_{n} \stackrel{d}{\rightarrow} X \Leftrightarrow$
- Finite Dimensional Convergence: $\forall k<\infty, t_{1}, \ldots, t_{k} \in T$
  $$
  \left(X_{n, t_{1}}, \ldots, X_{n, t_{k}}\right) \stackrel{d}{\rightarrow}\left(X_{t_{1}}, \ldots, X_{t_{k}}\right)
  $$
  

- $X_{n}$ is asymptotically equicontinuous.

## Donsker Class

 $\mathcal{F}\subset L^\infty(\mathcal{F})$  is called $\mathbb{P}$ -**Donsker**  if
$$
\left(\sqrt{n}\left(P_{n}-\mathbb{P}\right) f_{1}, \cdots, \sqrt{n}\left(P_{n}-\mathbb{P}\right) f_{k}\right) \rightarrow\left(G_{f_{1}}, \ldots, G_{f_{k}}\right)
$$
where  $G$ is a gaussian process and $\operatorname{cov}\left(G_{f_{i}}, G_{f_{k}}\right)=\operatorname{cov}\left\{f_{i}(X), f_{j}(X)\right\}, \text { where } X \sim \mathbb{P}$.

### Some sufficient Conditions

- Let $\mathcal{F}=\{f:\mathcal{X}\rightarrow\mathbb{R}\}$ with an envelop function $F$ that $\mathbb{P} F^{2}<\infty$ and

$$
\int_{0}^{\infty} \sup _{Q} \sqrt{\log N\left(\|F\|_{L_{2}(Q)} \epsilon, \mathcal{F}, L_{2}(Q)\right)} \mathrm{d} \epsilon<\infty
$$

​			 	Then $\mathcal{F}$ is a $\mathbb{P}$-Donsker.

- When $\mathcal{F}$ is a VC-subgraph-class of functions with envelop function $F$ that  $\mathbb{P} F^{2}<\infty$, then  $\mathcal{F}$ is a $\mathbb{P}$-Donsker.

### Example (Kolmogorov-Smirnoff test)

Suppose $X_{1}, \ldots, X_{n} \stackrel{\text { i.i.d }}{\sim} F$ (continuous) and aim to test $\mathcal{H}_0:F=F_0$ with test statistics $K S_{n}=\sqrt{n} \sup _{t \in \mathbb{R}}\left|F_{n}(t)-F_{0}(t)\right|$. Under $\mathcal{H_0}$, $K S_{n}=\sqrt{n} \sup _{t \in \mathbb{R}}\left|F_{n}(t)-F(t)\right|=\sup _{f \in \mathcal{F}}\left|\sqrt{n}\left(P_{n}-\mathbb{P}\right) f\right|$ where $\mathcal{F}=\{\mathbf{1}[\cdot \leq t], t \in \mathbb{R}\}$. Then, $\mathcal{F}$ is a Donsker class and then we can use gaussian process to conduct hypothesis test.

# Reference

- [Convergence Rate and Convergence in Law](http://shjkx.wang/index.php/%E8%AE%A8%E8%AE%BA:%E7%BB%9F%E8%AE%A1%E5%A4%A7%E6%A0%B7%E6%9C%AC%E7%90%86%E8%AE%BA_%E6%94%B6%E6%95%9B%E9%80%9F%E7%8E%87%E5%92%8C%E4%BE%9D%E6%B3%95%E5%88%99%E6%94%B6%E6%95%9B)

  

  




