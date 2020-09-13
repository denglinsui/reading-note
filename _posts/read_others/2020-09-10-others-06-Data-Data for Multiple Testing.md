---
title: "「Others」6 Data for Multiple Testing"
subtitle: "Data for Multiple Testing - Multiple Testing"
layout: post
author: "Linsui"
header-style: text
tags:
  - Data
  - Others
---

# Description

This page collects data that is used in multiple testing. 

*Note*: When the data collected is abundant enough, I will categorize them (I hope I will).

# Data

#### `estrogen`(雌性激素) dataset

The description of `estrogen` dataset is mainly from [Lei Lihua's demo](https://lihualei71.github.io/demo_gene_drug.nb.html).

`estrogen` dataset is a gene/drug response dataset frome NCBI Gene Expression Omnibus(NEO). **It consists of  gene expression measurements for $n=22283$ genes, in response to estrogen treatments in breast cancer cells for five groups of patients, with different dosage levels and $5$ trials in each.** The task is to identify the genes responding to a low dosage.  The p-values $p_i$ for gene $i$ is obtained by a one-sided permutation test which evaluates evidence for a change in gene expression level between the control group (placebo) and the low-dose group.



# Reference

-  [Lei Lihua's demo](https://lihualei71.github.io/demo_gene_drug.nb.html)