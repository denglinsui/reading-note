---
title: "「Network」7 Threshold Behavior"
subtitle: "Threshold Behavior - Through DFS"
layout: post
author: "Linsui"
header-style: text
tags:
  - Network
---

> Since there are some problems about mathjax, I also upload the pdf version <a href="https://denglinsui.github.io/reading-note/pdf/Network/07.pdf" target="_blank">「Network」7 Threshold Behavior</a>.



We focus on simple ER model here.

# What is a Threshold Behavior

Some Example

- Numbers of Triangle
  - When $np<1$, we do not expect to see triangles;
  - When $np>1$, we would expect to see many triangles;
- Size of Largest Component
  - When $p<\frac{1}{n}$, the largest component has size $O(\log n)$.
  - When $p<\frac{1}{n}$, then the largest component has linear size with high probability.



## The DFS algorithm  

DFS algorithm is also the depth-first search algorithm. It searches the vertexes of a graph. It labels the vertexes with three types in each round (One vertex moves):

- $S$: explored;
- $T$: unvisited;
- $U=\mathcal{V} \backslash(S \cup T)$ : under investigation.

### Algorithm

Start: $S=U=\emptyset, T=\mathcal{V}$
If $U \neq \emptyset$ : Let $v$ be the last vertex added to $U$.

1. If $v$ has a neighbour $u$ in $T$ then delete $u$ from $T$ and insert it into $U$.
2. If $v$ does not have a neighbour in $T$ then $v$ is moved from $U$ to $S$.

If $U=\emptyset$ : choose the first vertex of $T$ and move it from $T$ to $U$. If $U \cup T=\emptyset$ : query all the remaining pairs of vertices in $S=V$, then stop.

### Properties of DFS

- At each round, either from $T$ to $U$, or from $U$ to $S$.
- Each round may consist of multiple queries of edges to determine whether or not the edge is present.
- At any stage of the algorithm it has been revealed already that the graph $G$ has no edges between the current set $S$ and the current set $T$
- The set $U$ always spans a path ( and hence a connected component).

## Threshold Behavior

### Small Component

Let $\varepsilon>0$, and let $G \sim \mathcal{G}(n, p)$, with $n \geq 3 .$ Let $\varepsilon<1$ and let $p=\frac{1-\varepsilon}{n} .$ Then the probability that all connected components of $G$ are of size at most $\frac{7}{\varepsilon^{2}} \log n$ tends to $1$ as $n \rightarrow \infty$.

### Large Component

Let $\varepsilon>0$, and let $G \sim \mathcal{G}(n, p)$, with $n \geq 3 .$ Let $\varepsilon<\frac{1}{10}$ and let $p=\frac{1+\varepsilon}{n} .$ Then the probability that $G$ contains $a$ path of length at least $\frac{1}{5} \varepsilon^{2} n$ tends to 1 as $n \rightarrow \infty$.



