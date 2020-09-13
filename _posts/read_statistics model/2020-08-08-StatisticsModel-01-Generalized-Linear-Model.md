---
title: "「Statistics Model」1 Generalized Linear Model"
subtitle: "Generalized Linear Model - Link function/Estimation/Inference"
layout: post
author: "Linsui"
header-style: text
tags:
  - Statistics Model
  - Course
  - 笔记
---

# Generalized Linear Model

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/pdf/StatisticsModel/01.pdf" target="_blank">「Statistics Model」1 Generalized Linear Model</a>.
>

## Why do we need GLM?

Ordinary linear regression predicts the expected value of a given unknown quantity as a linear combination of a set of observed values. This is appropriate when the response variable has a normal distribution.  However, these assumptions are inappropriate for some types of response variables.

For example, when the response is not normal, e.g. binary data, the linear model is inappropriate. Sometimes, the output doesn't linearly change with respect to input. Therefore, the ordinary linear regression need to be extended.

## Definition of GLM

Both of OLM and GLM use the **linear predictor** $\eta=x^\top \beta$  through $\mu=\mathbb{E}(y)$.

|              OLM               |                             GLM                              |
| :----------------------------: | :----------------------------------------------------------: |
| $y\sim\mathcal{N}(\mu,\sigma)$ | $f(y ; \theta, \phi)=\exp \{ \frac{y \theta-b(\theta)}{\phi}+c(y ; \phi)\}$ |
|           $\mu=\eta$           |                        $\eta=g(\mu)$                         |

where $\theta$  depends on the **linear predictor**, the **dispersion parameter** $\phi$ is
often *known*, and $g$ is a monotone **link function**.

The GLM generalized OLM in the aspects of the distribution of response variables and the link between $\mu$ and $\eta$ (nonlinear relations between the mean response and the covariates).

### Exponential Family

The GLM extend the distribution of $y$ from the normal distribution to the exponential family. There are some useful properties:

- Moment-generating function: $M(t)=\exp \{b(\theta+t \phi)-b(\theta)\}$
- Mean: $\mathrm{E}(Y)=b^{\prime}(\theta)=\mu$
- Variance: $\operatorname{var}(Y)=\phi b^{\prime \prime}(\theta)=\phi b^{\prime \prime}\{b^{\prime-1}(\mu)\}=\phi V(\mu)$

where $V(\mu)$ is the **variance function**.

<u>Note:</u> If $\phi$ is known, the variance function $V(\mu)$ and its domain $\Rightarrow\kappa(\theta)\Rightarrow m(\theta)\Rightarrow$ distribution.

### Link Function $g(\mu)$

The link function provides the relationship between the linear predictor and the mean of the distribution function.  

The link function $g$ should remove restrictions on $\mu$ by mapping to $\eta$:


$$
\eta_i=g(\mu_i)
$$


**Canonical link**: $\eta=\theta=b'^{-1}(\mu)$. When $\phi$ is known, the model is a natural exponential family.

## Estimation and Inference

### Discussion of $\beta$

#### Estimation of $\beta$

To estimate $\beta$, with Chain rule, we solve the equation:


$$
\begin{array}{l}
\frac{\partial \ell(\beta)}{\partial \beta}=\frac{\partial \eta^{\mathrm{T}}}{\partial \beta} \frac{\partial \theta}{\partial \eta^{\mathrm{T}}} \frac{\partial \ell}{\partial \theta^{\mathrm{T}}}=X^{\mathrm{T}} u(\beta)
\end{array}
$$


$\beta$ and $\theta$ interacts through $\eta=X^\top\beta$.  That is, $\beta-\eta-\mu-\theta$.

For the exponential familiy, the elements of score statistics $u(\beta)$ and weighted matrix $W(\beta)$  are


$$
\begin{array}{l}
u_{j}=\frac{\partial \theta_{j}}{\partial \eta_{j}} \frac{\partial \ell_{j}\left(\theta_{j}\right)}{\partial \theta_{j}}=\frac{y_{j}-\mu_{j}}{g^{\prime}\left(\mu_{j}\right) \phi_{j} V\left(\mu_{j}\right)} \\
w_{j}=\left(\frac{\partial \theta_{j}}{\partial \eta_{j}}\right)^{2} \frac{\partial^{2} \ell_{j}\left(\theta_{j}\right)}{\partial \theta_{j}^{2}}=\frac{1}{g^{\prime}\left(\mu_{j}\right)^{2} \phi_{j} V\left(\mu_{j}\right)}
\end{array}
$$


So, given $I(\beta)=X(\beta)^{\mathrm{T}} W(\beta) X(\beta)$, we can find $\beta$ by iterative weighted least squres mothod:


$$
\widehat{\beta} \doteq \beta+I(\beta)^{-1} \frac{\partial \eta^{\mathrm{T}}(\beta)}{\partial \beta} u(\beta)
$$


In this case,  $y$ is a possible initial value for $\mu$  and $g(y)$ is for $\eta$.

#### Inference of $\beta$

Under regularity conditions,


$$
\widehat{\beta}\dot{\sim}\mathcal{N}(\beta,(X^\top WX)^{-1})
$$

### Discussion of $\phi$

At the discussion above, we assume $\phi_j$ are known. But if they are unknown and have $\phi_j=a_j\phi$, $\phi$ need to be estimated.

#### Estimstion of $\phi$

Note that,  $\phi=\operatorname{var}\left(y_{j}\right) /\{a_{j} V\left(\mu_{j}\right)\}$.

If $\beta$ were known,


$$
\widehat{\phi}=\frac{1}{n} \sum_{j=1}^{n} \frac{\left(y_{j}-\mu_{j}\right)^{2}}{a_{j} V\left(\widehat{\mu}_{j}\right)}
$$

If $\beta$ were unkown,


$$
\widehat{\phi}=\frac{1}{n-p} \sum_{j=1}^{n} \frac{\left(y_{j}-\widehat{\mu}_{j}\right)^{2}}{a_{j} V\left(\widehat{\mu}_{j}\right)}
$$

$$
P=\frac{1}{\phi} \sum_{j=1}^{n} \frac{\left(y_{j}-\widehat{\mu}_{j}\right)^{2}}{V\left(\widehat{\mu}_{j}\right) / a_{j}}
$$

### Fit Measure

#### Analysis of Deviance

Use scaled deviance:
$$
D^\star=2\{l_{max}-l(\widehat{\beta})\}\dot{\sim} \chi^2_{n-p}
$$

#### Pearson's Statistics

$$
P=\frac{1}{\phi} \sum_{j=1}^{n} \frac{\left(y_{j}-\widehat{\mu}_{j}\right)^{2}}{V\left(\widehat{\mu}_{j}\right)  a_{j}}\dot{\sim}\chi^2_{n-p}
$$

<u>Note:</u>  Their distributions depend on the situation.  

#### Full Model v.s. Reduced Model

For model A and model B:

$$
D_a-D_B\dot{\sim} \chi^2_{p_A-p_B}
$$


# References

- [Introduction to Generalized Linear Models](https://statmath.wu.ac.at/courses/heather_turner/glmCourse_001.pdf)
- [Statstical Models](https://www.cambridge.org/core/books/statistical-models/8EC19F80551F52D4C58FAA2022048FC7?__cf_chl_jschl_tk__=aa921ed4560dcaea177e8da320fca59b236ef827-1593743587-0-Aced3me35WQuzFYEtvpkZ_Elir4Gt9CInH2WMwxG_WMgu4KEpsi7sRFlcnKh7V23HK1UMQFiSC5tiTEtuo9sT_C1lnAlJ5k9gVej2S3NqvLdnMPR3JlpJ4tR3sNiaE2m7rCjabSX1l32yLgl6CS83-fxUdQoBmiU6KuWIdy14rAD-SYlV22sSmUD9CxSp5gCS2rnf_ip0AsWuC21P-XuwRh9uZZLDtfqLu4K5kjapJfsT2QB7Beeb2ljamMYfL3vm0t9FUs5S02iNGs89CtSdGA25F3XxEyF9IPVtZlfkvhNFWh-DOxW1JbbsmznYnxyC82lgvqZxQSgnVcwUQXqfWRyzET6iqsyMgG6L19WTHD2H8N74h-Sz18oB3cn-XX9b08yXYm7AKYzvR3NV7eh_f-sL15-pI9aMIZaN-ub2YfW)
