---
title: "「Concept」2 Network Flow"
subtitle: "Network Flow - a casual concept"
layout: post
author: "Linsui"
header-style: text
tags:
  - Concept
---

# Description

> In [graph theory](https://en.wikipedia.org/wiki/Graph_theory), a **flow network** (also known as a **transportation network**) is a [directed graph](https://en.wikipedia.org/wiki/Directed_graph) where each edge has a **capacity** and each edge receives a flow.

>  A flow must satisfy the restriction that the amount of flow into a node equals the amount of flow out of it, unless it is a **source**, which has only outgoing flow, or **sink**, which has only incoming flow.

## Definition

Denote $G=(V,E)$ as a network, then $(G,c,s,t)$ is a **flow network** if two nodes in $G$ is distinguished, a source $s$ and a sink $t$ and $c:V\times V\rightarrow\mathbb{R}$ is a non-negative **capacity** function.

# Application Field

- computer network
- circulation with demands
- fluids in pipes
- currents in an electrical circuit
- or anything similar in which something travels through a network of nodes.

# Reference

-  [Flow Network: wiki](2020-10-08-concept-02-Network_Flow)