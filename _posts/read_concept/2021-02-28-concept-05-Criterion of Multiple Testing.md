---
title: "「Concept」5 Criterion for Multiple Testing"
subtitle: "Criterion for Multiple Testing - False Discovery & POWER"
layout: post
author: "Linsui"
header-style: text
tags:
  - Concept
---

# Introduction

Here we consider multiple testing for both continuous and discrete data. To measure the effectiveness of rejection procedure, both pointwise and cluster-based criterion are given.

 Denote $S_0$ as the index of null hypothesis and $\mathcal{T}=\{T: \mathcal{X} \rightarrow \mathbb{R}\}$ as the set of threshold procedure, then we have

- the **false discovery proportion** 

  $\begin{aligned} \Gamma(T) &=\frac{\lambda\left(S_{0} \cap R_{T}\right)}{\lambda\left(R_{T}\right)} \\ & \equiv \frac{\lambda\left(S_{0} \cap\{s \in S: X(s) \geq T(X)\}\right)}{\lambda(\{s \in S: X(s) \geq T(X)\})} \end{aligned}$

- the **false cluster proportion**

  $\Xi_{\tau}(T)=\frac{\#\left\{1 \leq k \leq m_{T}: \frac{\lambda\left(S_{0} \cap C_{k}\right)}{\lambda\left(C_{k}\right)}>\tau\right\}}{m_{T}}$

  where $C_1,\cdots,C_{m_T}$ are connected components of $R_T$.

# False Discovery

- the **false discovery rate**: $FDR=\mathbb{E}\Gamma(T)$;
- the **false discovery exceedance**: $FDX_{\gamma}=\mathbb{P}(\Gamma(T)>\gamma)$
- the **false cluster rate**: $FCR_{\tau}=\mathbb{E}\Xi_{\tau}(T)$
- the **false cluster exceedance**: $FCX_{\gamma,\tau}=\mathbb{P}(\Xi_\tau(T)>\gamma)$

# POWER

- the **false nondiscovery proportion**

  $\begin{aligned} \Lambda(T) &=\frac{\lambda\left(S_{1} \cap\left(S \backslash R_{T}\right)\right)}{\lambda\left(S \backslash R_{T}\right)} \\ & \equiv \frac{\lambda\left(S_{1} \cap\{s \in S: X(s)<T(X)\}\right)}{\lambda(\{s \in S: X(s)<T(X)\})} \end{aligned}$

- the **false nondiscovery rate**:$FNR=\mathbb{E}\Gamma(T)$

# Additional Reading

When I plot the result of `RFSimulate()` in R package `RandomFields()`, the panel is empty. This can be solved by opening a new window and plot it:

```R
x11(); 
plot(simu) 
```

# Reference

-  [False Discovery Control for Random Fields](https://doi.org/10.1198/0162145000001655)
-  [Plotting realisations of random Gaussian fields using RandomFields package results in blank graph. Why?](https://stackoverflow.com/questions/43094652/plotting-realisations-of-random-gaussian-fields-using-randomfields-package-resul)

