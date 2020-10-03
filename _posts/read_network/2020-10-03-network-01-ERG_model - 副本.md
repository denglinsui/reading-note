---
title: "「Network」1 Erdős–Rényi-Gilbert Random Graph Model"
subtitle: "Random Graph Model - ERG Random Graph Model"
layout: post
author: "Linsui"
header-style: text
tags:
  - Network
---

# Background

The Erdős–Rényi model was firstly introduced by [Paul Erdős](https://en.wikipedia.org/wiki/Paul_Erdős) and [Alfréd Rényi](https://en.wikipedia.org/wiki/Alfréd_Rényi) in 1959, while [Edgar Gilbert](https://en.wikipedia.org/wiki/Edgar_Gilbert) introduced the other model contemporaneously and independently of Erdős and Rényi.

The underlying ideas for them are respectively:

- Erdős and Rényi: All graphs on a fixed vertex set with a fixed number of edges are equally likely;
- Gilbert: Each edge has a fixed probability of being present or absent, independently of the other edges. 

# Model

## Erdős and Rényi 

The network is denoted as $G(N,E)$ because they assumed the number of nodes and edges are fixed. 

- An undirected graph involving $N$ nodes and a fixed number of edges, $E$, chosen randomly from the $\left(\begin{array}{c}N \\ 2\end{array}\right)$ possible edges in the graph. 
- All $\left(\begin{array}{c}\left(\begin{array}{c}N \\ 2\end{array}\right) \\ E\end{array}\right)$ graphs are equally likely.

## Gilbert

The network is denoted as $G(N,E)$ because Gilbert assumed the number of nodes and the probability of each edge existing is fixed. 
$$
\ell(G(N, p) \text { has } E \text { edges } \mid p)=p^{E}(1-p)^{\left(\begin{array}{c}
N \\
2
\end{array}\right)-E}
$$
Or equivalently,
$$
\ell(Y \mid p)=\prod_{i \neq j} p^{Y_{i j}}(1-p)^{1-Y_{i j}}
$$

# Properties

When considering asymptotic behavior is the value of $\lambda=pN$:

- If $\lambda<1,$ then a graph in $G(N, p)$ will have no connected components of size larger than $O(\log N),$ a.s. as $N \rightarrow \infty$
- 
  If $\lambda=1,$ then a graph in $G(N, p)$ will have a largest component whose size is of $O\left(N^{2 / 3}\right),$ a.s. as $n \rightarrow \infty$
- If $\lambda$ tends to a constant $c>1,$ then a graph in $G(N, p)$ will have a unique "giant" component containing a positive fraction of the nodes, a.s. as $N \rightarrow \infty .$ No other component will contain more than $O(\log N)$ nodes, a.s. as $N \rightarrow \infty$.

# Reference

-  [A survey of statistical network](clarivate.com/webofsciencegroup/solutions/journal-citation-reports/)
-  [Erdős–Rényi model](https://en.wikipedia.org/wiki/Erdős–Rényi_model)