---
title: "「Network」4 Network Distance"
subtitle: "Network Distance - Structural Distance"
layout: post
author: "Linsui"
header-style: text
tags:
  - Network
---

# Structural Distance

Structural distance captures local changes. It suites to data where local changes can induce radical changes.

## Hamming Distance

$$
d_{H}(G, \tilde{G})=\sum_{i, j} \frac{\left|A_{i j}-\tilde{A}_{i j}\right|}{N(N-1)}=\frac{1}{N(N-1)}\|A-\tilde{A}\|_{1}
$$



## Jaccard Distance

Jaccard Distance includes a normalization with respect to the volume of the union graph.
$$
\begin{aligned}
d_{\text {Jaccard }}(G, \tilde{G}) &=\frac{|G \cup \tilde{G}|-|G \cap \tilde{G}|}{|G \cup \tilde{G}|} \\
&=\frac{\sum_{i, j}\left|A_{i j}-\tilde{A}_{i j}\right|}{\sum_{i, j} \max \left(A_{i, j}, \tilde{A}_{i j}\right)} \\
&=\frac{\|A-\tilde{A}\|_{1}}{\|A+\tilde{A}\|_{*}},
\end{aligned}
$$
It is the metric induced by Steinhaus transformation $\delta(x, y)=\frac{2 d(x, y)}{d(x, c)+d(y, c)+d(x, y)}$ with empty graph $c$.  

## Four Aspects of Dissimilarity Scores

- **Edge-Importance**: modifications of the graph structure yielding disconnected components should be penalized more.
- **Edge-submodularity**: a specific change is more important in a graph with a few edges than in a denser graph on the same nodes.
- **Weight awareness**: the impact on the similarity measure increases with the weight of the modified edge  
- **Focus awareness**: random changes in graphs are less important than targeted changes of the same extent  

# Reference

-  [Tracking network dynamics: A survey using graph distances](https://projecteuclid.org/euclid.aoas/1532743483)