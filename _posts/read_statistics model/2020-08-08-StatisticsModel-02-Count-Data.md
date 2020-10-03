---
title: "「Statistics Model」2 Count Data"
subtitle: "Count Data - Poisson v.s. Binomial/Contingency Tables"
layout: post
author: "Linsui"
header-style: text
tags:
  - Statistics Model
  - Course
  - 笔记
---

# Count Data

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/StatisticsModel/02.pdf" target="_blank">「Statistics Model」2 Count Data</a>.

The count data comes from Poisson:
$$
Y\sim P(\mu)
$$
In this part, we consider two ways to analyze the data, through Poisson and through Binomial.

## Discussion of Poisson and Binomial

### Poisson Model

**Model Assumption**: 

$Y$: the number of events in a Poisson process of rate $\exp(x ^\top\beta)$ observed for a period $T$ , where $\mu = T \exp(x^\top\beta) =
\exp(x^\top \beta + \log T )$.   

**Explanation**: 

1. The canonical link of Possion is $\mu=\exp(x^\top\beta)$; 
2. The expected mean increases proportional to the $T$; 
3. This is a log-linear model with linear predictor $η' = x^\top\beta+ \log T $  , where $\log T$, a fixed part, is a *offset* term.

**<u>Note:</u>** The offset term can also be the the amount of population.

### Binomial Model derived by Poission Model

$Y_i\sim P(\mu_i), i=1,2$ are independent. Then,  
$$
Y_1|Y_1+Y_2=m\sim \text{Bin}(n,\frac{\mu_1}{\mu_1+\mu_2})
$$
Since $Y$ are output of Poission model, we can use the log-linear model discussed above, that is,  $\mu_{1}=\exp \left(\gamma+x_{1}^{\mathrm{T}} \beta\right)$ and $\mu_{2}=\exp \left(\gamma+x_{2}^{\mathrm{T}} \beta\right)$. Then, 
$$
\pi=\exp \left\{\left(x_{2}-x_{1}\right)^{\mathrm{T}} \beta\right\} /[1+\exp \left\{\left(x_{2}-x_{1}\right)^{\mathrm{T}} \beta\right\} ]
$$
In this case, we can use logistic model to estimate $\beta$, but we cannot estimate $\gamma$.

<u>Note</u>: The analysis of binomial model requires observations, otherwise it will lose some information. Therefore, $se_{Poission}(\beta)\leq se_{Binomial}(\beta)$ .

## Contingency Tables

### Sampling Scheme

There are several sampling schemes for obtaining continegency tables ($R\times C$):

1. No constraints on the row and column totals. For the count in the $(r,c)$ cell, $y_{rc}\sim P(\mu_{rc})$. The likelihood is:
   $$
   \prod_{c c}\left\{\frac{\mu_{t c}^{\text {sc }}}{y_{y c} !} e^{-\mu_{c_{c}}}\right\}
   $$

2. Fix the total number $\sum_{r c} y_{r c}=m$. Then, the data are multinomially distributed. Denoting $\pi_{r c}=\mu_{r c} / \sum_{s, t} \mu_{s t}$, the likelihood is:
   $$
   \frac{m !}{\prod_{r, c} y_{r c} !} \prod_{r, c} \pi_{r c}^{y_{r c}}, \quad \sum_{r, c} \pi_{r c}=1
   $$

3. Fix the row totals $m_{r}=\sum_{c} y_{r c}$. Then, the data are independently multinomial distributions for each row. Denoting $\pi_{r c}=\mu_{r c} / \sum_{t} \mu_{r t}$, the likelihood is:
   $$
   \prod_{r}\left\{\frac{m_{r} !}{\prod_{c} y_{r c} !} \prod_{c} \pi_{r c}^{y_{r c}}\right\}, \quad \sum_{c} \pi_{1 c}=\cdots=\sum_{c} \pi_{R c}=1
   $$

### Estimation

Noting that count data is discrete, we use GLM to analyze it. Here, we use a link $\mu_{rc}=\exp(\gamma_r+x_{rc}^\top\beta)$ and consider sampling scheme 1 (Poisson) and 2 (Multinomial).

Then, some derivations show that:
$$
\widehat{\beta}_{Poiss}=\widehat{\beta}_{Mult},\widehat{\mathrm{sd}}(\widehat{\beta}_{Poiss})=\widehat{\mathrm{sd}}(\widehat{\beta}_{Mult})
$$
<u>Note</u>: Some softwares only depends on log-linear model. With this result, data comes from sampling method 2 can be analyzed with log-linear model.

#### Derivation

The relation of the likelihood is shown following:
$$
\begin{aligned}
\ell_{\text {Poiss }}(\beta, \tau) 
&=\sum_{r, c}\left(y_{r c} \log \mu_{r c}-\mu_{r c}\right) \\
&=\sum_{r}\left(m_{r} \gamma_{r}+\sum_{c} y_{r c} x_{r c}^{\top} \beta-e^{\gamma_{r}} \sum_{c} e^{x_{r c}^{\mathrm{T}} \beta}\right)\\
&\left.\equiv \sum_{r}\left(m_{r} \log \tau_{r}-\tau_{r}\right)+\sum_{r}\left\{\sum_{c} y_{r c} x_{r c}^{\mathrm{T}} \beta-m_{r} \log \left(\sum_{c} e^{x_{r}^{\top} \beta}\right)\right\}\right\} \\
&=\ell_{\text {Poiss }}(\tau ; m)+\ell_{\text {Mult }}(\beta ; y \mid m)
\end{aligned}
$$
where $\tau_{r}=\sum_{c} \mu_{r c}=e^{\gamma_{r}} \sum_{c} e^{x_{r c}^{r}}$.

 So that
$$
\begin{aligned}
\frac{\partial \ell_{\text {Poiss }}(\beta, \tau) }{\partial \beta}&=
\frac{\partial \ell_{\text {Multi }}(\beta, \tau) }{\partial \beta}
\end{aligned}
$$
This implies the estimation of $\beta$ are equal.

The expected information for $\beta$ is:
$$
\begin{aligned}
\widehat{I}_{Poiss}(\beta)&=\sum_{r} \widehat{\tau}_{r} \frac{\partial^{2} \log \left(\sum_{c} e^{x_{r c}^{\mathrm{T}} \widehat{\beta}}\right)}{\partial \beta \partial \beta^{\mathrm{T}}}=\sum_{r} m_{r} \frac{\partial^{2} \log \left(\sum_{c} e^{x_{r c}^{\mathrm{T}} \widehat{\beta}}\right)}{\partial \beta \partial \beta^{\mathrm{T}}}\\
\widehat{I}_{Mult}(\beta)&=\sum_{r} m_{r} \frac{\partial^{2} \log \left(\sum_{c} e^{x_{r c}^{\mathrm{T}} \widehat{\beta}}\right)}{\partial \beta \partial \beta^{\mathrm{T}}}
\end{aligned}
$$
So that
$$
\widehat{\mathrm{sd}}(\widehat{\beta}_{Poiss})=\widehat{\mathrm{sd}}(\widehat{\beta}_{Mult})
$$
<u>Note</u>: In fact, the expected information matrixes for these two sampling scheme are different. It's interesting to find that if $\tau_r$ is unknown and need estimation, the estimated expected information matrixes under the two circumstances are the same. 

# References

- [Statstical Models](https://www.cambridge.org/core/books/statistical-models/8EC19F80551F52D4C58FAA2022048FC7?__cf_chl_jschl_tk__=aa921ed4560dcaea177e8da320fca59b236ef827-1593743587-0-Aced3me35WQuzFYEtvpkZ_Elir4Gt9CInH2WMwxG_WMgu4KEpsi7sRFlcnKh7V23HK1UMQFiSC5tiTEtuo9sT_C1lnAlJ5k9gVej2S3NqvLdnMPR3JlpJ4tR3sNiaE2m7rCjabSX1l32yLgl6CS83-fxUdQoBmiU6KuWIdy14rAD-SYlV22sSmUD9CxSp5gCS2rnf_ip0AsWuC21P-XuwRh9uZZLDtfqLu4K5kjapJfsT2QB7Beeb2ljamMYfL3vm0t9FUs5S02iNGs89CtSdGA25F3XxEyF9IPVtZlfkvhNFWh-DOxW1JbbsmznYnxyC82lgvqZxQSgnVcwUQXqfWRyzET6iqsyMgG6L19WTHD2H8N74h-Sz18oB3cn-XX9b08yXYm7AKYzvR3NV7eh_f-sL15-pI9aMIZaN-ub2YfW)

