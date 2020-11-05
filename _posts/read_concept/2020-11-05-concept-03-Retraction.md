---
title: "「Concept」3 Retraction"
subtitle: "Retraction - a topology concept"
layout: post
author: "Linsui"
header-style: text
tags:
  - Concept
---

# Description

> In [topology](https://en.wikipedia.org/wiki/Topology), a branch of [mathematics](https://en.wikipedia.org/wiki/Mathematics), a **retraction** is a [continuous mapping](https://en.wikipedia.org/wiki/Continuous_mapping) from a [topological space](https://en.wikipedia.org/wiki/Topological_space) into a [subspace](https://en.wikipedia.org/wiki/Subspace_topology) that preserves the position of all points in that subspace.
>
> A **deformation retraction** is a mapping that captures the idea of *continuously shrinking* a space into a subspace.

## Definition

Let $X$ be a topological space and $A$ a subspace of $X$. Then a continuous map
$$
r: X \rightarrow A
$$
is a **retraction** if the restriction of $r$ to $A$ is the identity map on $A$; that is, $r(a)=a$ for all $a$ in $A$. Equivalently, denoting by
$$
\iota: A \hookrightarrow X
$$
the inclusion, a retraction is a continuous map $r$ such that
$$
r \circ \iota=\mathrm{id}_{A}
$$

# Reference

-  [Retraction: wiki](https://en.wikipedia.org/wiki/Retraction_(topology))