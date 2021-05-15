---
title: Formulation of stochastic optimal control problem and its existences
tags:
  - Stochastic control
  - Optimal control
categories: Stochastic Control
mathjax: true
abbrlink: 6e8b91b3
---
This article I will state some basic definitions about stochastic optimal control. Basically, it answers what is stochastic optimal control problem. For this kind of problem, there is a **diffusion system** described by It$\hat{o}$ stochastic differential equation, many **decisions** which can affect the system, a **criterion** that measures the performance of the decision, sometimes some **constraints** that the decision are subject to. And our goal is to optimize(maximize or minimize) the criterion by selecting a nonanticipative decision among ones satisfying constraints. Such problem we called stochastic optimal control problem.

Given a filtered probability space $(\Omega, \mathcal{F},\{\mathcal{F}_{\{t\geq 0\}}\},\mathbb{P})$ satisfying usual condition (i.e. the probability space is complete and the filtration is right-continuous) on which an $m$-dimensional standard Brownina motion $W(\cdot)$ is defined, we consider the following controlled SDE:

$$

$$

