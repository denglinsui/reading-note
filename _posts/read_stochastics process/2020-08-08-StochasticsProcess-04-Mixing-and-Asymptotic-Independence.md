---
title: "「Stochastics Process」4 Mixing and Asymptotic Independence"
subtitle: "Mixing and Asymptotic Independence - Singularity/Regularity/The Cramér-Wold decomposition/Mixing"
layout: post
author: "Linsui"
header-style: text
hidden: true
mathjax: true
tags:
  - Stochastics Process
  - Course
  - 笔记
---

# Mixing and Asymptotic Independence

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/pdf/StochasticsProcess/03.pdf" target="_blank">Stochastics Process」4 Mixing and Asymptotic Independence</a>. 

In this part, we care about:

- Predictability
- Asymptotic Independence and hence generalized central limit theorem.

## Singularity and regularity  

To start with, singularity measures the new information added with increasing observation interval; while regularity measures the infomation $x(t)$ originate.

Note that $\mathscr{H}(x, t)=\mathscr{S}(x(s) ; s \leq t)$ and define $\mathscr{H}(x,-\infty)=\cap_{t \leq t_{0}} \mathscr{H}(x, t),t\rightarrow-\infty$. $\mathscr{H}(x, t)$ can be intepreted as the information of $x(s),s\leq t$ and $\mathscr{H}(x, -\infty)$ is the ancient information(far from now).

### Definition

For process $\{x(t), t \in \mathbb{R}\}$ is **singular** if $\mathscr{H}(x,-\infty)=\mathscr{H}(x)$; is **regular** if $\mathscr{H}(x,-\infty)=\mathbf{0}$.

<u>Note</u>: Singularity is also called purely determinism, that is, all future can be obtained from arbitary far back past.

### The Cramér-Wold decomposition

Every stochastic process $\{x(t), t \in \mathbb{R}\},$ with $E\left(|x(t)|^{2}\right)<\infty,$ exists a decomposition of two *uncorrelated* processes
$$
x(t)=y(t)+z(t)
$$
where $\{y(t), t \in \mathbb{R}\}$ is regular and $\{z(t), t \in \mathbb{R}\}$ is singular.

#### $AR(1)$ Prcess with added term

For $x(t)=a x(t-1)+e+e(t)$, it can be decomposed as $y(t)+z(t)$
$$
y(t)=\sum_{k=0}^{\infty} a^{k} e(t-k)\qquad z(t)=\frac{1}{1-a} e
$$
where $y(t)$ is regular and $z(t)$ is singular.

### Spectrum Decomposition

The spectrum distribution function can be decomposed as
$$
F(\omega)=F^{(s)}(\omega)+F^{(ac)}(\omega)+F^{(d)}(\omega)
$$
where $F^{(ac)}(\omega)=\int_{\infty}^\omega f(x)dx$, $f(\omega)=F'(\omega)$, $F^{(d)}(\omega)=\sum_{\omega_{k} \leq \omega} \Delta F_{k}$ and $F^{(s)}(\omega)$ is the singular part.

### Conditions for Stationary Sequences

Fristly, note the integral $P=\frac{1}{2 \pi} \int_{-\pi}^{\pi} \log f(\omega) \mathrm{d} \omega$ is either finite or $-\infty$.

Then, for a stationary sequence $\left\{x_{n}, n \in \mathbb{N}\right\}$

- If $P=-\infty,$ then $x_{n}$ is singular. 
- If $P>-\infty,$ and the spectrum is *absolutely continuous* with $f(\omega)>0$ for almost all $\omega$, i.e.​ $F(\omega)=F^{(ac)}(\omega)$,​ then $x_{n}$ is regular. 
- If $P>-\infty,$ but $F(\omega)$ is either discontinuous, or is continuous with non-vanishing singular part, $F^{(s)}(\omega) \neq 0,$ then $X_{n}$ is neither singular nor regular.

<u>Note</u>: A stationary sequence $x(t)$ is regular $\Leftrightarrow
x_{t}=\sum_{k=-\infty}^{t} h_{t-k} y_{k}
$
where $y_{k}$ is uncorrelated.

#### Some Special Case

- If the spectrum is *discrete* with a finite number of jumps, then $f(\omega) = 0\ a.s.$  and $P = -\infty$, so the process is singular;

- If the spectrum is *absolutely continuous* with density $f(\omega)$, singularity
  and regularity depends on whether $f(\omega)$ comes close to $0$ or not.  

- If $f(\omega) \geq c>0$ for $-\pi<\omega \leq \pi$, then the integral is finite and the process is regular.

### Conditions for Stationary Processes

Define the integral $Q=\int_{-\infty}^{\infty} \frac{\log f(\omega)}{1+\omega^{2}} \mathrm{d} \omega$.

Then, for a stationary process $\{x(t), t \in \mathbb{R}\}$

- If $Q=-\infty,$ then $x(t)$ is singular.
- If $Q>-\infty,$ and the spectrum is absolutely continuous, then $x(t)$ is regular.

<u>Note</u>: For a statioanry process $\{x(t)\}$, there is a singular-regular decomposition $x(t)=x^{(s)}(t)+\int_{u=-\infty}^{t} h(t-u) \mathrm{d} \xi(u)$, where $\{\zeta(t), t \in \mathbb{R}\}$ is a process with uncorrelated increments.

#### Discussion

Consider three process with covariance function and spectral density

- $r_1(t)=e^{-t^2/2}$, $f_1(\omega)=\frac{1}{\sqrt{2 \pi}} e^{-\omega^{2} / 2} $, $Q=-\infty$
- $r_2(t)=\frac{sin(t)}{t}$, $f_2(\omega)=\frac{1}{2} \boldsymbol{1}_{\{\omega:|\omega|\leq 1\}}$, $Q=-\infty$
- $r_3(t)=\exp(-\alpha|t|)$, $f_3(\omega)=\frac{\alpha}{\pi\left(\alpha^{2}+\omega^{2}\right)}$, $Q>-\infty$

For the first two cases, $Q=-\infty$, which means $x(t)$ is singular and hence it is *predictable*. However, from the perspective of covariance function $r(t)\rightarrow 0, t\rightarrow\infty$, when the time varies with relatively long distance, the r.v. $x(s+t)$ and $x(s)$ are nearly irrelative ( If $x(t)$ is in additional Gaussian, they are nearly independent.) 

Therefore, independent doesn't implies unpredictability. It also depends on the convergence rate of covariance function: for the case one $e^{-t^2/2}$ is too fast; for the case two $\frac{sin(t)}{t}$ is too slow.

## Mixing

### Global Mixing for General Process

$\{x(t)\}$ is stochastic process defined on $\mathscr{M}_a^b$,  $t$ is arbitary and $A \in \mathscr{M}_{-\infty}^{t}$. $U^{-k} B=\{x(\cdot) ; x(k+\cdot) \in B\} \in \mathscr{M}_{k}^{\infty}$.

- **uniform mixing**: $\exists\ \phi(n)$ s.t. $\phi(n) \rightarrow 0$ as $n \rightarrow \infty,$ $B \in \mathscr{M}_{t+n}^{\infty}$

$$
|P(A \cap B)-P(A) P(B)| \leq \phi(n) P(A)
$$

- **strong mixing**: $\exists\ \alpha(n)$ s.t. $\alpha(n) \rightarrow 0$ as $n \rightarrow \infty,$ $B \in \mathscr{M}_{t+n}^{\infty}$

$$
|P(A \cap B)-P(A) P(B)| \leq \alpha(n)
$$

- **ergodic mixing**:  $B \in \mathscr{M}_{t}^{\infty}$, 

$$
\lim _{k \rightarrow \infty} P\left(A \cap U^{-k} B\right)=P(A) P(B)
$$

- **weak mixing**: $B \in$ $\mathscr{M}_{t}^{\infty}$

$$
\lim _{n \rightarrow \infty} \frac{1}{n} \sum_{k=1}^{n}\left|P\left(A \cap U^{-k} B\right)-P(A) P(B)\right|=0
$$

<u>Note</u>: From the expression, we know that mixing evaluates the level of independence w.r.t the distance $n$.

<u>Note</u>: Uniform mixing $\Rightarrow$ Strong mixing $\Rightarrow$ Ergodic mixing

### Global Mixing for Gaussian Process

Let $\{x(t), t \in \mathbb{Z}\}$ be a stationary Gaussian process. 

- **uniformly mixing**: $r(t)=0$ for $|t|>m$, $m$-dependent.
- **strongly mixing**: $f(\omega) \geq c>0$ on $-\pi<\omega \leq \pi$
- **weakly mixing**: $\Leftrightarrow$ ergodic $\Leftrightarrow$ the spectral distribution function is continuous.

# Reference

- [Stationary Stochastic Processes](https://www.amazon.com/Stationary-Stochastic-Processes-Applications-Statistical/dp/1466557796)

  

  


