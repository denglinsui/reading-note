---
title: "「Bayesian」2 Slice Sampler"
subtitle: "Slice Sampler - Simpler/General and examples"
layout: post
author: "Linsui"
header-style: text
tags:
  - Bayesian
  - Course
  - 笔记
---

# Slice Sampler

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/pdf/Bayesian/02.pdf" target="_blank">「Bayesian」2 Slice Sampler</a>.

## Simple Slice Sampler

The generation from a distribution with density $f(x)$ is equivalent to uniform generation on the subgraph of $f$,


$$
\mathscr{S}(f)=\lbrace(x, u) ; 0 \leq u \leq f(x)\rbrace
$$


and $f$ need only be known up to a normalizing constant.  

We consider using a *random walk* on $\mathscr{S}(f)$  and this is slice sampling.

### Algorithm

1. Move from $(x, u)$ to $\left(x, u^{\prime}\right)$ by


$$
u^{\prime} \mid x \sim \text { Uniform }\lbrace(\{u: u \leq f_{1}(x)\}\rbrace
$$

2. Move from $\left(x, u^{\prime}\right)$ to $\left(x^{\prime}, u^{\prime}\right)$ by


$$
x \mid u^{\prime} \sim \text { Uniform }\left(\lbrace x: u^{\prime} \leq f_{1}(x)\rbrace\right)
$$

<u>Note</u>: The uniform distribution on $\mathscr{S}(f)$ is indeed stationary for both steps. This algorithm will work well only if the exploration of the subgraph of $f_1$ by the corresponding random walk is fast enough.

### Example

#### Simple slice sampler   

Generate from the density $f(x)=(1/2)e^{-\sqrt{x}}\boldsymbol{1}(x>0)$

- $U\vert x \sim \mathcal{U}\left(0, \frac{1}{2} e^{-\sqrt{x}}\right)$; 
- $X\vert u \sim \mathcal{U}\left(0,[\log (2 u)]^{2}\right)$

#### Truncated normal distribution

Generate from the density  $f(x) \propto f_{1}(x)=\exp \left(-(x+3)^{2} / 2\right) \mathbb{I}_{[0,1]}(x)$

- $U\vert x \sim \mathcal{U}\left(0, \exp \lbrace -(x+3)^{2} / 2\rbrace\right)$
- $X\vert u\sim\mathcal{U}\lbrace y ; \exp \lbrace-(y+3)^{2} / 2\rbrace \geq u\rbrace\cap[0,1]$

## The General Slice Sampler  

Expressing the distribution of $u$ is always difficult, it inspires us to find a way to simplify this. 

Suppose there is a decomposition of $f$:
$$
f(x) \propto \prod_{i=1}^{k} f_{i}(x)
$$

### Algorithm

At iteration $t+1,$ simulate

1. $\omega_{1}^{(t+1)} \sim U_{\left[0, f_{1}\left(x^{(t)}\right)\right]}$

   $\cdots$

​            k. $\omega_{k}^{(t+1)} \sim U_{\left[0, f_{k}\left(x^{(t)}\right)\right]}$

​            k+1. $x^{(t+1)} \sim U_{A^{(t+1)}},$ with
$$
A^{(t+1)}=\left\{y ; f_{i}(y) \geq \omega_{i}^{(t+1)}, i=1, \ldots, k\right\}
$$


<u>Note</u>: When $f_k$'s are simple, the expressions is tractable, but it happens that the intersection set is small.

### Example

#### A 3D slice sampler

Generate from the density:
$$
f(x)=\exp \left(-x^{2} / 2\right) \times(1+\cos (\pi x)) \times \mathrm{I}(x \in[-0.5,0.5])
$$

- Step 1: generate $\omega\vert x$
  - $\omega_1\sim U[0,\exp(-x^2/2)]$
  - $\omega_2\sim U[0,1+\cos(\pi x)]$
- Step 2: generate $x'\vert \omega$
  - $I_1=[-\sqrt{-2\log(\omega_1)},\sqrt{-2\log(\omega_1)}]$
  - $I_2=[\frac{\arccos(\omega_2'-1)}{\pi},\infty)$
  - $I_3=[-0.5,0.5]$
  - $x'\sim \boldsymbol{1}_{I_1\cap I_2\cap I_3}(x)$