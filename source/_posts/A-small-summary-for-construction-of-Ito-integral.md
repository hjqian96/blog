---
title: A small summary for construction of It$\hat{o}$ integral
mathjax: true
categories:
  - Stochastic Calculus Notes
tags:
  - It$\hat{o}$ integral
abbrlink: 6b27437e
date: 2020-01-07 21:36:49
---

How to define integral $\int_{S}^{T}f(t,w)dB_t(w)$? It is reasonable to define this integral for a simple class of functions [^1].

{% alert info %}

<b>Definition</b> <br>
Let $\mathcal{V}=\mathcal{V}(S,T)$ be the class of functions
$$f(t,w): [0,\infty)\times \Omega\rightarrow \mathbb{R}$$
such that <br>
(1)$(t,w)\rightarrow f(t,w)$ is $\mathcal{B}\times \mathcal{F}$-measurable, where $\mathcal{B}$ denotes the Borel $\sigma$-algebra on $[0,\infty)$.<br>
(2) $f(t,w)$ is $\mathcal{F}_t$-adapted.<br>
(3) $E\left[\int_{S}^{T}f^2(t,w)dt\right]<\infty.$<br>

{% endalert %}


Step 1: For elementary functions
$$
\phi(t,w)=\sum_{j>0} e_j(w)I_{[t_j,t_{j+1})}(t)
$$
where $e_j$ is $\mathcal{F}_{t_j}$ measurable. Then we define

$$\int_{S}^{T}\phi(t,w)dB_t(w)=\sum_{j>0} e_j(w)\left[B_{t_{j+1}}-B_{t_j}\right](w)$$

By direct calculation, such definition enjoys It$\hat{o}$ isometry, namely

$$E\left(\int_{S}^{T}\phi(t,w)dB_{t}(w)\right)^2= E\int_{S}^{T}f^2(t,w)dt$$

Step 2: for any function $f\in \mathcal{V}[S,T]$, we prove that there exists $\phi_n$ elementary functions such that
$$E[\int_{S}^{T}(\phi_n-f)^2]dt\rightarrow 0,\quad \text{as} n\rightarrow \infty$$

To get such result, it should split into three small steps.<br>

- Step 2.1: for any function $g\in \mathcal{V}$ be bounded and $g(\cdot, w)$ continuous for each $w$, prove there exists elementary functions $\phi_n\in \mathcal{V}$ such that
$$E\left[\int_{S}^{T}(g-\phi_n)^2dt\right]\rightarrow 0.$$
- Step 2.2: for any function $h\in \mathcal{V}$ be bounded, then prove that there exists bounded functions $g_n\in \mathcal{V}$ such that $g_n(\cdot, w)$ is continuous for all $w$ and $n$, and
$$E\left[\int_{S}^{T}(h-g_n)^2dt\right]\rightarrow 0.$$

- Step 2.3: for any function $f\in \mathcal{V}$, prove that there exists bounded functions $h_n\in \mathcal{V}$ such that
$$E\left[\int_{S}^{T}(f-h_n)^2dt\right]\rightarrow 0.$$

Step 3: Finally, we define $\int_{S}^{T}f(t,w)dB_t(w)$ in general as follows:
$$\int_{S}^{T}f(t,w)dB_t(w)=\lim_{n\rightarrow \infty} \int_{S}^{T}\phi_n(t,w)d_t(w)\quad \text{ in } L^2(P)$$

In fact, sequences $\{\int_{S}^{T}\phi_n(t,w)dB_t(w)\}$ is Cauchy in $L^2(P)$

$$
\begin{align*}
& E\left(\int_{S}^{T}\phi_n(t,w)dB_t(w)-\int_{S}^{T}\phi_m(t,w)dB_t(w)\right)^2\\
& = E\int_{S}^{T}(\phi_n(t,w)-\phi_m(t,w))^2dt \\
& \leq E\int_{S}^{T}(\phi_n(t,w)-f)^2dt+E\int_{S}^{T}(\phi_m(t,w)-f)^2dt\rightarrow 0.
\end{align*}
$$

Finally, we mention the following theorem.

{% alert info %}
<b>Theorem:</b>  <br>
Let $f\in\mathcal{V}[S,T]$. Then there exist a $t$-continuous version of 
$$\int_{0}^{t}f(t,w)dB_s(w); \quad 0\leq t\leq T$$
In other words, there exists a $t$-continuous stochastic process $J_t$ on $(\Omega,\mathcal{F},P)$ such that
$$
P\left[J_t=\int_{0}^{t}fdB\right]=1 \quad \text{for all} t,\,0\leq t \leq T
$$

{% endalert %}



[^1]: Stochastic Differential Equations.



