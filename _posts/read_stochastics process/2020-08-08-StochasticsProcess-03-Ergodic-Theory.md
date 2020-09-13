---
title: "「Stochastics Process」3 Ergodic Theory"
subtitle: "Ergodic Theory - Transformation View/Process View"
layout: post
author: "Linsui"
header-style: text
mathjax: true
hidden: true
tags:
  - Stochastics Process
  - Course
  - 笔记
---

# Ergodic Theory

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/pdf/StochasticsProcess/03.pdf" target="_blank">「Stochastics Process」3 Ergodic Theory</a>.

Ergodicity describes the phenomenon that the time average of one relization (sample path) of stationary process converges to the expectation of it at $t=0$. It transforms a probabilistic problem to a deterministic problem.

The general ergodicity properties of Gaussian processes can be inferred already from its covariance function.  

Ergodicity is the equivalence of
$$
\mathbb{E}(x)=\int_\Omega x(\omega) dP(\omega)\qquad \frac{1}{n}\sum_{1}^n x(T^{k-1}\omega)
$$


## Ergodic Theorem in $\mathcal{L}^2$

### Ergodic Example in $\mathcal{L}^2$

$\{x(t)\}$ is a stationary stochastic process with covariance function $r(t)$. Then if $\mathbb{E}(x(t))=0$,
$$
\frac{1}{T} \int_{0}^{T} r(t) \mathrm{d} t \rightarrow 0 \quad \text { implies } \quad \frac{1}{T} \int_{0}^{T} x(t) \mathrm{d} t \stackrel{q \cdot m}{\rightarrow} 0
$$
as $T\rightarrow\infty$.

### Continuity at $t=0$

If the spectral distribution $F$ is a step function and the spectral representation $x(t)=\int e^{i\omega t}dZ(\omega)$ is available:
$$
\begin{array}{l}
\lim _{T \rightarrow \infty} \frac{1}{T} \int_{0}^{T} r(t) e^{-i \omega_{k} t} \mathrm{d} t=\Delta F_{k} \\
\lim _{T \rightarrow \infty} \frac{1}{T} \int_{0}^{T}|r(t)|^{2} \mathrm{d} t=\sum_{k}\left(\Delta F_{k}\right)^{2} \\
\lim _{T \rightarrow \infty} \frac{1}{T} \int_{0}^{T} x(t) e^{-i \omega_{k} t} \mathrm{d} t=\Delta Z_{k}
\end{array}
$$

- If the spectral distribution is continuous at $t=0$, then $\frac{1}{T} \int_{0}^{T} r(t) \mathrm{d} t \rightarrow 0 $ and hence implies ergodic;
- If the spectral distribution is discontinuous at $t=0$, then $\frac{1}{T} \int_{0}^{T} r(t) \mathrm{d} t \rightarrow \Delta F_{k} $ and hence implies non-ergodic.

### Non-Ergodic Example in $\mathcal{L}^2$

Suppose $\omega_k>0$, $x(t)=\sum_{k} A_{k} \cos \left(\omega_{k} t+\phi_{k}\right)$. Then, for $x(t)^2$

- $\mathbb{E}(x(0)^2)=\sum\mathbb{E}(A_k^2/2)$
- $\frac{1}{T}\int_0^Tx(t)^2dt\rightarrow \sum A_k^2/2\not=\sum\mathbb{E}(A_k^2/2)$

## Stationarity and Transformation

In this part, stationarity means strictly stationary.

**Measure Preserving Transformation**: $P\left(T^{-1} A\right)=P(A)$ for all $A \in \mathscr{F}$, then $T$ is *measure preserving transformation* and $P$ is *invariant*.

### From measure presering transformation to a stationary sequance

Take a random variable $x(\omega)$ on $(\Omega,\mathcal{F},\mathbb{P})$ and $T$ is measure presering. Let $x_k(\omega)=x(T^{k-1}\omega)$ and then the sequence is strictly stationary.

### From stationary sequance to a measure presering transformation

The *shift transformation* $T: T\omega=(x_2,x_3,\cdots)$ is a measure preserving transformation, if $\{x_k\}$ is a strictly stationary sequence.

## The Ergodic Theorem(Transformation View)

In this part, we want to explore the ergodic theorem in the transformation view. For a fixed initial outcome $\omega$, the time average 
$$
\frac{1}{n} \sum_{1}^{n} x\left(T^{k-1} \omega\right)
$$
With the relationship of measure preserving transformation and strictly stationary sequence, what we care about is
$$
S_{n} / n=\frac{1}{n} \sum_{1}^{n} x_{k}
$$
As the form suggested, this is the law of large numbers in stochastics process.

### Invariant Set/r.v & Ergodic Transformation

Consider $(\Omega,\mathcal{F},\mathbb{P})$ and measure preserving transformation $T:\Omega\rightarrow\Omega$

**Invariant set $A\in\mathscr{F}$**:  $T^{-1}A=A$

**Family of invariant ses $\mathscr{S}$**:  $\mathscr{J}=\{\text {invariant sets } A \in \mathscr{F}\}$

**Invariant random variable $x\in(\Omega,\mathscr{F},\mathbb{P})$**: $x(\omega)=x(T\omega)\ a.s.\Leftrightarrow x\in\mathscr{S}$ 

<u>Note</u>: The equivalent definition of invariant random variable links it to invariant sets.

**Ergodic**: A measure preserving transformation $T$ on a probability space $(\Omega,\mathcal{F},\mathbb{P})$ is called *ergodic* $\Leftrightarrow \forall A\in\mathscr{S}=\mathbb{P}(A)=0,1\Leftrightarrow$every (bounded) invariant random variable $x$ is $a.s.$ a constant.

<u>Note</u>: For measure preserving transformation, such limit $S_n/n$ always exist. The next question is what the limiting distribution or limiting value it is.

### Brikhoof Ergodic Theorem

Let $T$ be a measure preserving transformation on $(\Omega, \mathscr{F}, P) .$ Then, for any random variable $x$ with $E(|x|)<\infty$
$$
\lim _{n \rightarrow \infty} \frac{1}{n} \sum_{0}^{n-1} x\left(T^{k} \omega\right)=E(x \mid \mathscr{J}), a . s
$$
<u>Note</u>: This implies the limiting behavior depends on initial state.

#### Measure Preserving Ergodic Transformation

If $T$ is additionally ergodic, then 
$$
\lim _{n \rightarrow \infty} \frac{1}{n} \sum_{0}^{n-1} x\left(T^{k} \omega\right)=E(x), a . s
$$

#### Infinite Expectation 

If $x$ is non-negative with $\mathbb{E}(x) = ∞$ then $S_n/n → ∞$ if $T$ is ergodic. 

#### Ergodic Non-Random Walks  

Take a set $A ∈ F$ and consider its indicator function $χ_A(ω)$. If $T$ is ergodic,  
$$
\frac{1}{n} \sum_{0}^{n-1} \chi_{A}\left(T^{k} \omega\right) \stackrel{a . s .}{\rightarrow} P(A)
$$

## The Ergodic Theorem(Process View)

### Stationary Sequence

Let $\{x_n\}$ be a strictly stationary *sequence*

**Invariant set $A\in\mathscr{F}$**:  $A=\left\{\left(x_{n}, x_{n+1}, \ldots\right) \in B\right\}, n\geq 1, b\in\mathscr{B}_\infty$

**Family of invariant ses $\mathscr{S}$**:  $\mathscr{J}=\{\text {invariant sets } A \in \mathscr{F}\}$

**Invariant random variable $\phi\in\left(\mathbb{R}^{\infty}, \mathscr{B}_{\infty}\right)$**: $z=\phi\left(x_{n}, x_{n+1}, \ldots\right),n\geq 1$

**Ergodic**: The sequence is called *ergodic* $\Leftrightarrow \forall A\in\mathscr{S}=\mathbb{P}(A)=0,1$.

#### Ergodic Theorem

1. If $\left\{x_{n}, n \in \mathbb{N}\right\}$ is a stationary sequence with $E\left(\left|x_{1}\right|\right)<\infty,$ and $\mathscr{J}$ denotes the $\sigma$ -field of invariant sets, then

$$
\frac{1}{n} \sum_{1}^{n} x_{k} \stackrel{a . s .}{\rightarrow} E\left(x_{1} \mid \mathscr{J}\right), a . s
$$

2. If $\left\{x_{n}, n \in \mathbb{N}\right\}$ is stationary and ergodic, then

$$
\frac{1}{n} \sum_{1}^{n} x_{k} \stackrel{a . s .}{\rightarrow} E\left(x_{1}\right), a . s
$$

#### Transitivity

If $\left\{x_{n}, n \in \mathbb{N}\right\}$ is stationary and ergodic, and $\phi\left(x_{1}, x_{2}, \ldots\right)$ is measurable on $\left(\mathbb{R}^{\infty}, \mathscr{B}_{\infty}\right),$ then the process $y_{n}=\phi\left(x_{n}, x_{n+1}, \ldots\right)$ is also stationary and ergodic.

### Stationary Process

For continuous time processes $\{x(t), t \in \mathbb{R}\},$ the *shift transformation* $ U_{\tau}$ is
$$
\left(U_{\tau} x\right)(t)=x(t+\tau)
$$
**Measure preserving transformation**: If $x(t)$ is strictly stationary.

**Invariant set $B$**: If $\mathbb{P}(B\not=U_\tau B)=0$  

**Family of invariant ses $\mathscr{S}$**:  $\mathscr{J}=\{\text {invariant sets } A \in \mathscr{F}\}$

**Ergodic**: The process is called *ergodic* $\Leftrightarrow \forall A\in\mathscr{S}=\mathbb{P}(A)=0,1$.

#### Ergodic Theorem

1. For any stationary process $\{x(t), t \in \mathbb{R}\}$ with $E(|x(t)|)<\infty$ and integrable sample paths, as $T \rightarrow \infty$

$$
\frac{1}{T} \int_{0}^{T} x(t) \mathrm{d} t \stackrel{a . s .}{\rightarrow} E(x(0) \mid \mathscr{J})
$$

2. If further $\{x(t), t \in \mathbb{R}\}$ is ergodic, then

$$
\frac{1}{T} \int_{0}^{T} x(t) \mathrm{d} t \stackrel{a . s .}{\rightarrow} E(x(0))
$$

## Ergodic Gaussian Sequences and Processes

Ergodicity for Gaussian stationary processes is characterized by their covariance function r(t) in continuous or discrete time.  

### Ergodicity for Gaussian stationary processes

Let$\{x(t), t \in \mathbb{R}\}$ be stationary and Gaussian with $E(x(t))=0$ , $V(x(t))=1$ and covariance function $r(t)$.

1. $x(t)$ is ergodic $\Leftrightarrow$ $F(\omega)$ is continuous everywhere.
2. If $r(t) \rightarrow 0$ as $t \rightarrow \infty,$ then $x(t)$ is ergodic. 

<u>Note</u>: A sufficient condition is $f(\omega)$ exists. That means $F(\omega)=\int_{-\infty}^{\omega} f(x) \mathrm{d} x$ is continuous.

# Reference

- [Stationary Stochastic Processes: Theory and Applications](https://www.amazon.com/Stationary-Stochastic-Processes-Applications-Statistical/dp/1466557796)

  

  


