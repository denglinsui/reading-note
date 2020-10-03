---
title: "「Statistics Model」3 Overdispersion"
subtitle: "Overdispersion - Definition/Ways of solving/Quasi-likelihood"
layout: post
author: "Linsui"
header-style: text
tags:
  - Statistics Model
  - Course
  - 笔记
---

# Overdispersion

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/StatisticsModel/03.pdf" target="_blank">「Statistics Model」3 Overdispersion</a>.

## Definition

**Overdispersion**: Models with over-large deviances and residuals, but otherwise showing no systematic lack of fit. Structure in the data is obscured by additional noise, so overdispersion increases uncertainty.  

**Example**: Count and proportion data are more variable than would be
expected under the Poisson and binomial models.   

## Approaches to Dealing with Overdispersion

###  Parametric models

**Basic Idea**: Suppose that the response $Y$ has a standard distribution conditional on the unobserved variable $\epsilon$, but that $\epsilon$ induces extra variation in $Y$ .

**Model Setting**: Assume $\epsilon$ is unobserved and it satisfies $\mathbb{E}(\epsilon)=1$ and $\mathrm{var}(\epsilon)=\xi$. We further assume $Y\sim P(\mu\epsilon)$. Then, $\mathbb{E}(Y)=\mu$ and $\mathrm{var}(Y)=\mu(1+\xi\mu)>\mu$. (Variance function is quadratic.)

In this way, we obtain a random variable whose variance is larger than Possion. If $\xi=0$, this model reduces to a Possion model.

<u>Note</u>: If we let $\mathrm{var}(\epsilon)=\xi/\mu$, then $\mathrm{var}(Y)=\mu(1+\xi)$ (Variance function is linear.)

### Quasi-likelihood

**Basic Idea**: Modify standard methos to accomodate overdispersion and treat the generalized linear model score statistic as an estimating function $g(Y ; \beta)$ for $\beta$. 

**Overview of Result**: Estimators retain their large-sample normal distributions by fitting standard models, but with an inflated variance matrix .

#### Quasi-likelihood Equation

An estimator $\widetilde{\beta}$ is obtained by solving *Quasi-likelihood Equation*:
$$
\begin{equation}
g(Y ; \beta)=X^{\mathrm{T}} u(\beta)=\sum_{j=1}^{n} x_{j} u_{j}(\beta)=\sum_{j=1}^{n} x_{j} \frac{Y_{j}-\mu_{j}}{g^{\prime}\left(\mu_{j}\right) \phi_{j} V\left(\mu_{j}\right)}=0
\end{equation}
$$
where $g\left(\mu_{j}\right)=\eta_{j}=x_{j}^{\mathrm{T}} \beta$.

If the mean structure has been chosen correctly, then $\mathbb{E}(Y_j) = \mu_j$ and the estimating function is unbiased, that is $\mathbb{E}\{g(Y ; \beta)\} = 0$ for all $\beta$.  Under regularity condition, 

- $\mathbb{E}(\widetilde{\beta})\rightarrow\beta$ 

- $\widetilde{\beta}\dot{\sim}\mathcal{N}(\beta,\mathrm{E}\left\{-\frac{\partial g(Y ; \beta)}{\partial \beta^{\mathrm{T}}}\right\}^{-1} \operatorname{var}\{g(Y ; \beta)\} \mathrm{E}\left\{-\frac{\partial g(Y ; \beta)^{\mathrm{T}}}{\partial \beta}\right\}^{-1})$, 

  - If the variance function specified, $\operatorname{var}\left(Y_{j}\right)=\phi_{j} V\left(\mu_{j}\right)$
    $$
    \widetilde{\beta}\dot{\sim}\mathcal{N}(\beta,(X^\top WX)^{-1})
    $$
    where $W=\mathrm{diag}(\left\{g^{\prime}\left(\mu_{j}\right)^{2} \phi_{j} V\left(\mu_{j}\right)\right\}^{-1})$.

  - If the variance function mispecified,
    $$
    \widetilde{\beta}\dot{\sim}\mathcal{N}(\beta,(X^\top WX)^{-1}(X^\top W'X)(X^\top WX)^{-1})
    $$
    where $W'$ is a diagonal matrix involving the true and assumed variance functions.  

**Comment**

- Under an exponential family model, the quasi-likelihood equation is the score statistics.
- $\widetilde{\beta}$ is optimal among estimators based on linear combinations of the $Y_j - \mu_j$, in analogy with the Gauss–Markov theorem.   
- The quasi-likelihood estimate $\widetilde{\beta}$ equals the maximum likelihood estimate, but with smaller deviance if $\phi>1$.   

#### Quasi-likelihood Function

$g(Y ;\beta)$ is the derivative with respect to $\beta$ of the *quasi-likelihood function*  
$$
Q(\beta ; Y)=\sum_{j=1}^{n} \int_{Y_{j}}^{\mu_{j}} \frac{Y_{j}-u}{\phi a_{j} V(u)} d u
$$
**Deviance**: $-2\phi Q(\beta;Y)$. This can compare nested model under overdispersion.

# Reference

- [Statstical Models](https://www.cambridge.org/core/books/statistical-models/8EC19F80551F52D4C58FAA2022048FC7?__cf_chl_jschl_tk__=aa921ed4560dcaea177e8da320fca59b236ef827-1593743587-0-Aced3me35WQuzFYEtvpkZ_Elir4Gt9CInH2WMwxG_WMgu4KEpsi7sRFlcnKh7V23HK1UMQFiSC5tiTEtuo9sT_C1lnAlJ5k9gVej2S3NqvLdnMPR3JlpJ4tR3sNiaE2m7rCjabSX1l32yLgl6CS83-fxUdQoBmiU6KuWIdy14rAD-SYlV22sSmUD9CxSp5gCS2rnf_ip0AsWuC21P-XuwRh9uZZLDtfqLu4K5kjapJfsT2QB7Beeb2ljamMYfL3vm0t9FUs5S02iNGs89CtSdGA25F3XxEyF9IPVtZlfkvhNFWh-DOxW1JbbsmznYnxyC82lgvqZxQSgnVcwUQXqfWRyzET6iqsyMgG6L19WTHD2H8N74h-Sz18oB3cn-XX9b08yXYm7AKYzvR3NV7eh_f-sL15-pI9aMIZaN-ub2YfW)

