---
title: Maximum principle for deterministic optimal control problem
mathjax: true
tags:
  - Maximum principle
  - Hamiltonian System
categories:
  - Stochastic Control
abbrlink: 83e6edd3
date: 2019-10-29 17:11:59
---
This post we will focus on the maximum principle for deterministic optimal control problem. Later on, we will see its sufficent conditions for optimality and corresponding maximum principle for stochastic optimal control problem.
<!--more-->

The formulation of the deterministic optimal control problem. We consider the following control problem
$$
\begin{cases}
    \dot{x}(t)=b(x,x(t),u(t)) \quad \text{a.e.} t\in[0,T]\\
    x(0)=x_0
\end{cases}
\tag{1}
$$
where the control $u(t)$ belongs to $\mathcal{V}[0,T]=\{u(t): [0,T]\rightarrow U | u(\cdot) \text{ is measurable}\}$ with $U$ being a metric space and $b:[0,T]\times\mathbb{R}^n\times U\rightarrow \mathbb{R}^n$. The cost functional associated with $(1)$ is the following:
$$J(u(\cdot))=\int_{0}^{T} f(t,x(t),u(t))dt+h(x(T)) \tag{2}$$.

The optimal control problem is stated as follows:

**(problem D)**: Minimize (2) over $\mathcal{V}[0,T]$.


<table><tr><td bgcolor=#B0C4DE><b>Lemma 1</b> Content </td></tr></table>
**Proof:**

<table><tr><td bgcolor=#B0C4DE><b>Theorem 1</b> Content </td></tr></table>
**Proof:**