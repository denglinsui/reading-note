---
title: "「Network」2 ERGMs"
subtitle: "ERGMs - Exponential random graph models"
layout: post
author: "Linsui"
header-style: text
tags:
  - Network

---

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/Network/02.pdf" target="_blank">「Network」2 ERGMs - Exponential random graph models</a>.

# Background

The idea comes from exponential family
$$
\mathbb{P}_{\theta}(\mathbf{Z}=\mathbf{z})=\exp \left\{\theta^{T} \mathbf{g}(\mathbf{z})-\psi(\theta)\right\}
$$


# Model

$G=(V,E)$, $Y_{ij}$ describes the existence of edge between $i$ and $j$
$$
\mathbb{P}_{\boldsymbol{\theta}}(\mathbf{Y}=\mathbf{y})=\left(\frac{1}{\kappa}\right) \exp \left\{\sum_{H} \theta_{H} g_{H}(\mathbf{y})\right\}
$$

- each $H$ is a *configuration*, which is defined to be a set of possible edges among a subset of the vertices in $G$;
- $g_{H}(\mathbf{y})=\prod_{y_{i j} \in H} y_{i j},$ and is therefore either one if the configuration $H$ occurs in $\mathbf{y},$ or zero, otherwise;
- a non-zero value for $\theta_{H}$ means that the $Y_{i j}$ are dependent for all pairs of vertices $\{i, j\}$ in $H,$ conditional upon the rest of the graph

# R package

`ergm`

# Reference

-  [Statistical Analysis of Network Data with R](https://www.springer.com/gp/book/9781493909834)