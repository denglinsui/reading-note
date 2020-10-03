---
title: "「Stochastics Process」1 Linear Filters"
subtitle: "Linear Filter - Time Field/Spectrum Field/Differential Equations/White noise"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Stochastics Process
  - Course
  - 笔记
---

# Linear filters	

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/StochasticsProcess/01.pdf" target="_blank">「Stochastics Process」1 Linear Filters</a>.

## Linear time invariant filters

> **Linear filters** process time-varying input signals to produce output signals, subject to the constraint of [linearity](https://en.wikipedia.org/wiki/Linearity).

This transformation can be described as:
$$
\widehat{x}(t+h)=\sum_{k} a_{k} x\left(t-s_{k}\right), \text { some } a_{k}, s_{k}>0
$$

------



### Mathematical Definition

#### In the time-field view

Given the *impulse response function*  $h(t)$,   $\mathscr{S}:x(t) \mapsto y(t)$, then the *output function*  $y(t)$ (i.e. $\widehat{x}(t+h)$) is:
$$
y(t)=\int_{-\infty}^{\infty} h(u) x(t-u) \mathrm{d} u=\int_{-\infty}^{\infty} h(t-u) x(u) \mathrm{d} u
$$
where the corresponding filter is *causual realizable* if $h(u)=0, u<0$. This can be understood by only the past information  available.

#### In the spectrum-field view

Suppose $\{x(t),t\in\mathbb{R}\}$ is a stationary process with spectral representation $\int_{-\infty}^\infty e^{i\omega t}\mathrm{d}Z(w)$. Then, $\mathscr{S}:x(t) \mapsto y(t)$, 
$$
y(t)=\int_{-\infty}^\infty g(\omega)e^{i\omega t}\mathrm{d}Z(w)
$$
 where $g(\omega)$ is the *frequency function* and it satisfies $\int_{-\infty}^{\infty}|g(\omega)|^{2} \mathrm{d} F(\omega)<\infty$.

<u>Note:</u> it as $y(t)=\int|g(\omega)| e^{i(\omega t+\arg g(\omega))} \mathrm{d} Z(\omega)$, we see the filter amplifies the amplitude of $\mathrm{d}Z(\omega)$ by a factor $|g(\omega)|$ and adds $\arg g(\omega)$ to the phase.  

#### In the linear view (More general)

$\mathscr{S}$ is a trasformation defined on $\Xi$ such that, $\Xi \ni x \mapsto \mathscr{S}(x) \in \Xi$, for constant $a_1,a_2$ and time delay $\tau$,
$$
\begin{aligned}
\mathscr{S}\left(a_{1} x_{1}+a_{2} x_{2}\right) &=a_{1} \mathscr{S}\left(x_{1}\right)+a_{2} \mathscr{S}\left(x_{2}\right) \\
\mathscr{S}(x(\cdot+\tau)) &=\mathscr{S}(x)(\cdot+\tau)
\end{aligned}
$$

------



### Time-field v.s. Spectral-filed

The impulse response and frequency response function form a
Fourier transform pair  
$$
\begin{array}{l}
h(u)=\frac{1}{2 \pi} \int_{-\infty}^{\infty} e^{i \omega u} g(\omega) \mathrm{d} \omega, \text { if } \int_{-\infty}^{\infty}|g(\omega)|^{2} \mathrm{d} F(\omega)<\infty \\
g(\omega)=\int_{-\infty}^{\infty} e^{-i \omega u} h(u) \mathrm{d} u, \text { if } \int_{-\infty}^{\infty}|h(u)| \mathrm{d} u<\infty
\end{array}
$$

#### Comman Linear Filters

$$
\begin{array}{l|l|l|l}
\text { Operation } & \text { Symbolic } & \begin{array}{l}
\text { Impulse } \\
\text { response }
\end{array} & \begin{array}{l}
\text { Frequency } \\
\text { response }
\end{array} \\
\hline \hline \text { time shift } & y(t)=x\left(t-\tau_{0}\right) & \delta_{\tau_{0}}(u) & e^{-i \omega \tau_{0}} \\
\hline \text { derivation } & y(t)=x^{\prime}(t) & \delta_{0}^{\prime}(u) & i \omega \\
\hline \begin{array}{l}
\text { exponential } \\
\text { smoothing }
\end{array} & \begin{array}{l}
y(t)= 
\int_{-\infty}^{t} e^{-\alpha(t-u)} x(u) \mathrm{d} u
\end{array} & \begin{array}{l}
e^{-\alpha u}, u>0
\end{array} & \frac{1}{\alpha+i \omega}
\end{array}
$$

------



### Correlation and spectral relations

#### In the spectrum-field view

Given stationary process $\{x(t),t\in\mathbb{R}\}$  with zero mean, the output process $\{y(t)\}$ through a frequency function $g(\omega)$. Then,
$$
\begin{aligned}
r_{y}(t)=E(y(s+t) \cdot \overline{y(s)})&=\int_{-\infty}^{\infty}|g(\omega)|^{2} e^{i \omega t} \mathrm{d} F(\omega)\\
f_{y}(\omega)&=|g(\omega)|^{2} f_{x}(\omega)
\end{aligned}
$$

#### In the time-field view

Given stationary process $\{x(t),t\in\mathbb{R}\}$  with mean $m_x$ and covariance function $r_x(t)$, the output process $\{y(t)\}$ through an impulse response function  $h(u)$. Then,
$$
\begin{aligned}
E(y(t)) &=m_{y}=m_{x} \int_{-\infty}^{\infty} h(u) \mathrm{d} u=m_{x} g(0) \\
r_{y}(t) &=\int_{U} \int_{y} h(u) \overline{h(v)} r_{x}(t+u-v) \mathrm{d} u \mathrm{d} v
\end{aligned}
$$
where $g(0)=\int h(u) \mathrm{d} u$ is the *gain of the filter*.

------



## Linear Filters and Differential Equations

From the discussion above, the linear filters can be interpreted in the two form. Sometimes, the filter in spectrum form is so simple that we can solve our problems efficiently. 

For example, there is always no analyzable derivative of stochastic process in the time-field. However, if we can get the spectrum form in the spectrum-field, the spectrum density of the derivative is simply $\omega^2f_x(\omega)$.

### Linear differential equations driven by a stochastic process

If stationary process $\{x(t),t\in\mathbb{R}\}$ and $\{y(t),t\in\mathbb{R}\}$, are any differentiable that are the solutions of 
$$
\sum_{k=0}^{p} a_{p-k} y^{(k)}(t)=\sum_{j=0}^{q} b_{q-j} x^{(j)}(t)
$$
Then their spectral density obey the relation
$$
\left|\sum_{k=0}^{p} a_{k}(i \omega)^{p-k}\right|^{2} f_{y}(\omega)=\left|\sum_{j=0}^{q} b_{j}(i \omega)^{q-j}\right|^{2} f_{x}(\omega)
$$

------



## White Noise in Linear System

Of special importance is the case when the input is *white noise*, $\{w'(t),t\in\mathbb{R}\}$. 

### Property of white noise

- The spectral density is constant:

$$
f_{n}(\omega)=\frac{\sigma^{2}}{2 \pi},-\infty<\omega<\infty
$$

- Give  a Wiener process $\{w(t), t \in \mathbb{R}\}$ and define $x(t)=\int_{-\infty}^{\infty} h(t-u) \mathrm{d} w(u)$ and  $g(\omega)=\int_{-\infty}^{\infty} e^{-i \omega u} h(u) \mathrm{d} u$. 

$$
\begin{aligned}
r_{x}(t)&=\int_{-\infty}^{\infty} h(t-u) h(-u) \mathrm{d} u\\
f_{x}(\omega)&=\frac{|g(\omega)|^{2}}{2 \pi}
\end{aligned}
$$

- If  $x(t)=\int_{-\infty}^{\infty} h(t-u) \mathrm{d} w(u)$ solves the stable stochastic differential equation
  $$
  a_{0} y^{(p)}(t)+a_{1} y^{(p-1)}(t)+\ldots+a_{p-1} y^{\prime}(t)+a_{p} y(t)=\sigma w^{\prime}(t)
  $$
  Then its spectral density is
  $$
  f_{x}(\omega)=\frac{\sigma^{2}}{2 \pi} \cdot \frac{1}{\left|\sum_{k=0}^{p} a_{k}(i \omega)^{p-k}\right|^{2}}
  $$

<u>Note:</u> The construction of $x(t)$ in the second property is exactly applying linear filter to $w'(t)$.

# Reference

- [Linear filter: Wiki](https://en.wikipedia.org/wiki/Linear_filter)

- [Stationary Stochastic Processes: Theory and Applications: Chapter 4](https://www.amazon.com/Stationary-Stochastic-Processes-Applications-Statistical/dp/1466557796)

  

  


