---
title: "「Stochastics Process」2 Karhunen-Loeve Expansion"
subtitle: "Karhunen-Loeve Expansion - Principle Component/Expansion along eigenfunctions/The Karhunen-Loève theorem"
layout: post
author: "Linsui"
header-style: text
mathjax: true
tags:
  - Stochastics Process
  - Course
  - 笔记
---

# Karhunen-Loeve Expansion

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/pdf/StochasticsProcess/02.pdf" target="_blank">「Stochastics Process」2 Karhunen-Loeve Expansion</a>.

## Linear time invariant filters

## Principle Component

**Goal**: Specify a few values, *principle component*, in order to reconstruct almost the entire outcome of the full vector.   

Given random vector $\mathbf{x}=(x_1,\cdots,x_n)^\top$ with mean zero and covariance matrix $\Sigma=\mathbb{E}(xx^\top)$ with eigenvalues $\lambda_1\geq\lambda_2\geq\cdots\lambda_n>0$ and orthonormal eigen vectors $p_k$.

With these assumptions, we want to find random variables $z_1,\cdots,z_n$ with mean zero and covariance matrix $\mathbf{I}_n$. The specific expression of $z_k$ is
$$
z_{k}=\frac{1}{\sqrt{\lambda_{k}}} \mathbf{p}_{k}^{\prime} \mathbf{x}
$$
The **principle component** of $\mathbf{x}$ is $y_k=\sqrt{\lambda_k}z_k$, or $\mathbf{y}=\mathbf{PX}$. It analogies to the eigenvector in the linear algebra.

Similarly, the original x-variables can be expressed as a linear combination of the uncorrelated variables $y_k$ and $z_k$:
$$
x_{k}=\mathbf{p}_{k}^{\prime} \mathbf{y}=\sum_{j=1}^{n} \sqrt{\lambda_{j}} p_{j k} z_{j}
$$

  ## Expansion along eigenfunctions

### Comparison with Finite Dimension

Here, we generalize the orthogonormality and eigenvectors in functional space.

|                 |                  fINITE dIMENSION                  |                  iNFINITE dIMENSION                   |
| --------------- | :------------------------------------------------: | :---------------------------------------------------: |
| orthogonal      |             $\sum p_i\overline{q_i}=0$             |          $\int_a^b c(t)\overline{d(t)}dt=0$           |
| normal          |                  $\sum |p_i|^2=1$                  |                $\int_a^b |c(t)|^2dt=1$                |
| eigen component | $\boldsymbol{\Sigma} \mathbf{p}=\lambda\mathbf{p}$ | $\int_{a}^{b} r(s, t) c(t) \mathrm{d} t=\lambda c(s)$ |

### Decomposition

Consider an one continuous parameter stochastic process $x(t), t\in[a,b]$. Similarly, we want to find the orthonormal basis for $\mathcal{H}(x)$, which satisfies
$$
\begin{aligned}
x(t) &=\sum_{k} c_{k}(t) z_{k} \\
r(s, t) &=\sum_{k} c_{k}(s) \overline{c_{k}(t)}
\end{aligned}
$$
To achieve this, 

- Firstly, find eigen functions $c_k(t)$ according to covariance function $r(s,t)$. 
- Then, $z_k$'s are obtained by $z_{k}=\frac{1}{\lambda_{k}} \int_{a}^{b} \overline{c_{k}(t)} x(t) \mathrm{d} t$
- The orthonormal eigenfunctions are $\phi_{j}(t)=\frac{1}{\sqrt{\lambda_{j}}} c_{j}(t)$

The optimal choice is minimizing integrated approximation error
$$
\int_{a}^{b} E\left(e_{n}^{2}(t)\right) \mathrm{d} t=\int_{a}^{b} E\left(x^{2}(t)\right) \mathrm{d} t-\sum_{0}^{n} \lambda_{k}
$$
Actually, we wish it converges to zero uniformly.

## The Karhunen-Loève theorem

#### The Karhunen-Loève theorem

Let $\{x(t), a \leq t \leq b\}$ be continuous in quadratic mean with mean zero and covariance function $r(s, t)=E(x(s) \overline{x(t)})$. Then there exist orthonormal eigenfunctions $\phi_{k}(t), k=0,1, \ldots, N \leq$ $\infty,$ for $a \leq t \leq b,$ with eigenvalues $\lambda_{0} \geq \lambda_{1} \geq \ldots,$ to the equation
$$
\int_{a}^{b} r(s, t) \phi(t) \mathrm{d} t=\lambda \phi(s)
$$
such that the random variables $z_{k}=\frac{1}{\sqrt{\lambda_{k}}} \int_{a}^{b} \overline{\phi_{k}(t)} x(t)dt$  are uncorrelated, $V\left(z_{k}\right)=1,$ and can represent $x(t)$ as
$$
x(t)=\sum_{0}^{\infty} \sqrt{\lambda_{k}} \phi_{k}(t) z_{k}
$$
<u>Note</u>: We can also express $x(t)$ as this $x(t)=\sum_{0}^{\infty} \sqrt{\lambda_{k}} \phi_{k}(t) z_{k}=\sum_{0}^{\infty} \int_a^b\overline{\phi_{k}(t)}x(t) dt\ \phi_{k}(t)$. In this way, the orthonormal term is $\phi_k(t)$.

### Optimality of the Karhunen-Loève expansion  

If $\psi_{k}(t), k=0,1, \ldots,$ is any sequence of functions and $y_{k} \in \mathscr{H}(x)$
are uncorrelated random variables, then, for each $n$
$$
\int_{a}^{b} E\left(\left|x(t)-\sum_{0}^{n} \sqrt{\lambda_{k}} \phi_{k}(t) z_{k}\right|^{2}\right) \mathrm{d} t \leq \int_{a}^{b} E\left(\left|x(t)-\sum_{0}^{n} \psi_{k}(t) y_{k}\right|^{2}\right) \mathrm{d} t
$$

# Reference

- [Stationary Stochastic Processes: Theory and Applications](https://www.amazon.com/Stationary-Stochastic-Processes-Applications-Statistical/dp/1466557796)

  

