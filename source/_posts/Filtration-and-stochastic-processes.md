---
title: Filtration and stochastic processes
categories: Stochastic Calculus Notes
tags:
  - Filtration
  - Stochastic Processes
mathjax: true
abbrlink: 5bf2f49b
date: 2019-08-03 10:12:23
---
This article I will demonstrate some basic definitions about Stochastic Processes, such as Filtration, indistinguishable, modification.

A *filtration* on a probability space is a collection of $\sigma$-fields $\{\mathcal{F}_t: t\in \mathbb{R}^{+}\}$ satisfying:
$$
\mathcal{F}_S \subseteq \mathcal{F}_t \subseteq \mathcal{F} \text{ for all } 0\leq s \leq t <\infty
$$
Given a filtration$\mathcal{F}_t$, we could add a last member to it by defining:
$$\mathcal{F}_{\infty}=\sigma(\bigcup_{0\leq t<\infty} \mathcal{F}_t)$$

A stochastic process $X=\{X_t, t\in \mathbb{R}^{+}\}$ is adapted to the filtration $\{\mathcal{F}_t\}$ if $X_t$ is $\mathcal{F}_t$-measurable for $0\leq t \leq \infty$. The smallest filtration that one process adapted to is thef filtration that it generates, i.e.
$$\mathcal{F}_{t}^{X}=\sigma\{X_s:0\leq s \leq t\}$$
<!--more-->
For random variables $X$ and $Y$, we have the definition that $X=Y$ a.s., that is $X=Y$ with probability one (or they are equal except on the events of probability zero). Similarily, we have such relaxation for stochastic processes. Let $\{X_t,t\in \mathbb{R}^{+}\}$ and $\{Y_t,t\in \mathbb{R}^{+}\}$, we say X and Y are *indistinguishable* if there exists an event $\Omega_0 \subseteq \Omega$ such that $P(\Omega_0)=1$ and for each $w\in\Omega_0$, $X_t(w)=Y_t(w)$ for all $t\in \mathbb{R}^{+}$. Another weak notion is the modification, we say: $Y$ is a *modification* of $X$ if for each $t$, $P(X_t=Y_t)=1$.

According the definition of indistinguishable, we know that such two stochastic processes have almost all paths. In fact, indistinguishable processes should really be viewed as one and the same procees.

All the stochastic processes we study will have some regularity properties as function of $t$ for each fixed $w$, i.e. regularity properties for paths. A stochastic process $\{X_t,t\in \mathbb{R}^{+}\}$ is said to *continuous* if for each $w\in \Omega$, the path $t\mapsto X_t(w)$ is continuous as a function of $t$. An $\mathbb{R}^{d}$-valued process $X$ is *right-continuous with left limits* (shortly RCLL, also named "cadlag" in French) if for all $w\in \Omega$:

- Right-continuous: $X_t(w)=\lim_{s\searrow t}X_s(w)$ for all $t\in \mathbb{R}^{+}$;
- The existence of left limits: $X_{t-}(w)=\lim_{s\nearrow t}X_s(w)$ exists in $\mathbb{R}^{d}$ for all $t>0$

Similarily,we could define *left-continuous with right limits* (shortly LCRL, also named "caglad" in French).

Next two lemmas show some technical benefits of path regularity.

{% alert info %}
<b>Lemma 1</b><br> 
Let $X$ be adapted to the filtration $\{\mathcal{F}_t\}$ and suppose $X$ either left- or right- continuous. Then $X$ is [progressively measurable](). 

{% endalert %}


Before we prove Lemma 1, we give the definiton of "measurable" and "[progressively measurable](https://en.wikipedia.org/wiki/Progressively_measurable_process)". 

- A process $X$ is *measurable* if $X$ is $\mathcal{B}(\mathbb{R}_{+})\otimes \mathcal{F}$-measurable as a function of $\mathbb{R}_{+}\times \Omega$ into $\mathbb{R}^d$ (that is for any Borel set $B \in \mathcal{B}(\mathbb{R}^d)$, $\{(t,w):X(t,w)\in B\} \in \mathcal{B}(\mathbb{R}_{+})\otimes \mathcal{F}$.

- A process $X$ is *progressively measurable* if the restriction of the function X to $[0,T]\times \Omega$ is $\mathcal{B}_{[0,T]}\otimes \mathcal{F}_T$-measurable for each T (more expilicitly, for any $B\in \mathcal{B}_{\mathbb{R}^d}$, the event $\{(t,w)\in [0,T]\times \Omega: X(t,w)\in B\}\in \mathcal{B}_{[0,T]}\otimes\mathcal{F}_T$).

**Proof:**

We would like to prove $X$ is progressively measurable, i.e. for each fixed T, we need to show $X$ is $\mathcal{B}_{[0,T]}\otimes \mathcal{F}_T$-measurable. The idea is use step function which is $\mathcal{B}_{[0,T]}\otimes \mathcal{F}_T$-measurable to approximate $X$. Then we could get the progressively measurability for X.

Suppose $X$ is right-continuous. Fix $T<\infty$, define the step function as following:
$$
X_n(t,w)=X(0,w)\cdot 1_{0}(t)+\sum_{k=0}^{2^n-1}X\bigl(\frac{(k+1)T}{2^n},w\bigr)\cdot 1_{(\frac{kT}{2^{-n}},\frac{(k+1)T}{2^{-n}})}(t)
$$
Since $X_n$ is $\mathcal{B}_{[0,T]}\otimes \mathcal{F}_T$-meaurable as a sum of products of $\mathcal{B}_{[0,T]}\otimes \mathcal{F}_T$-meaurable functions. By the right-continuity, $X_n(t,w)\rightarrow X(t,w)$ as $n\rightarrow \infty$, then we could get $X$ is $\mathcal{B}_{[0,T]}\otimes \mathcal{F}_T$-meaurable.

{% alert info %}
<b>Lemma 2</b> <br>
Suppose X and Y are right-continuous processes defined on the same probability space. Suppose $P\{X_t=Y_t\}=1$ for all $t$ in some dense countable subset $S$ of $\mathbb{R}^{+}$. Then $X$ and $Y$ are indistinguisable. 
{% endalert %}

**Proof:**

Let $\Omega_0=\{\cap_{s\in S} \{w:X_s(w)=Y_s(w)\}\}$. By assumption, $P(\Omega_0)=1$. Fix $w\in \Omega_0$, for any given $t\in \mathbb{R}^{+}$, since $S$ is dense, then there exists a sequence $s_n\in S$ s.t. $s_n \searrow t$. According to right-continuity, we have 
$$
X_t(w)=\lim_{n\rightarrow \infty} X_{s_n}(w)=\lim_{n\rightarrow \infty} Y_{s_n}(w)=Y_t(w)
$$
Therefore $X_t(w)=Y_t(w)$ for all $t\in \mathbb{R}^{+}$ and $w\in \Omega_0$. Thus $X$ and $Y$ are indistinguishable.
