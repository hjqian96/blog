---
title: Expectation
mathjax: true
categories:
  - Probability
tags:
  - Lebesgue Integral
  - Integrable
  - Uniformly Integrable
abbrlink: '24251726'
date: 2019-08-13 20:51:23
---
This article I will demonstrate the definition of expectation of a random variable and state three very important Theorems (Lemma), i.e. Monotone Convergence Theorem, Fatou's Lemma and Dominated Convergence Theorem.

<!--more-->

<center>Part I</center>
***
At first, we will start with the simple case, that is when $\xi$ is a simple random variable ($\xi$ only takes finite many values).
Let $(\Omega, \mathcal{F},P)$ be a finite probability space and $\xi$ is a simple random variable, i.e. $\xi=\sum_{k=1}^{n}x_kI_{A_k}(w)$, then we define
$$E\xi=\sum_{k=1}^{n}x_k P(A_k)$$

Next, we will define the expectation for a nonnegative random variable $\xi$. Then $\exists\xi_n\geq 0$ simple random varibales such that $\xi_n \uparrow\xi$ for each $w\in \Omega$. Since $E\xi_n \leq E\xi_{n+1}$, we have

{% alert info %}

<b>Definition 1</b>
The Lebesgue integral of the <strong>nonnegative</strong> random variable $\xi$ or its expectation is 
$$E\xi\equiv \lim_nE\xi_n$$

{% endalert %}


This definition is consistent according the following lemam 1, i.e. the limit is independent of the choice of the approximating sequence $\{\xi_n\}$. That is if $\xi_n \uparrow \xi$ and $\eta_m \uparrow \eta$ where $\{\eta_m\}$ is simple random variables, then we will have $\lim_n E\xi_n=\lim_m E\eta_m$.

{% alert info %}
<b>Lemma 1</b><br>

Let $\eta \text{ and }\xi_n$ be simple random variables, and $\xi_n\uparrow \xi \geq \eta$, then we will have $\lim_n E\xi_n \geq E\eta$.
{% endalert %}


Proof: 

Let $\varepsilon >0$ and $A_n=\{w: \xi_n \geq \eta -\varepsilon\}$ then $A_n \uparrow \Omega$ and $\xi_n =\xi_n I_{A_n} +\xi_n I_{\bar{A_n}} \geq \xi_n I_{A_n} \geq (\eta-\varepsilon) I_{A_n}$. Therefore, we have
$$
E\xi_n \geq E(\eta -\varepsilon) I_{A_n} =E\eta I_{A_n} -\varepsilon P(A_n)
= E\eta -E\eta I_{\bar{A_n}} -\varepsilon P(A_n) \geq E\eta -CP(\bar{A_n})-\varepsilon
$$
where $C=max_{w}\eta(w)$, then we get the results.

Remark: The expectation $E\xi$ of the nonnegative random variable $\xi$ satisfies 
$$E\xi= \sup_{\{s\in S: s\leq \xi \}}Es$$
where $S=\{s\}$ is the set of simple random variables.

Now, we extend our defintion of expectation to general random variables.

{% alert info %}
<b>Definition 2</b>
The expectation $E\xi$ of random variable $\xi$ <strong>exists</strong> or is defined if $min(E\xi^{+},E\xi^{-})< \infty$. In this case, define
$$E\xi=E\xi^{+}-E\xi^{-}$$
we say $E\xi $ is finite if both $E\xi^{+}$ and $E\xi^{-}$ are finite.
                                                                                                                         
 {% endalert %}


Remark: since the expectation of a random variable is actually Lebesgue integral, so the definition of expectation is just following how to define Lebesgue integral, i.e. step function $\rightarrow$ nonnegative measurable function $\rightarrow$ general measurable function.


<center>Part II</center>
***
The next part I will only state some properties about expectation and skip its proof. 

- Let $c$ be a constant and $E\xi $ exists, then $E(c\xi)$ exists and $E(c\xi)=cE\xi$.
-  Let $\xi \leq \eta$, then $E\xi \leq E\eta$ with the understanding that if $-\infty < E\xi$ then $-\infty < E\eta$ and $E\xi < E\eta$ or if $E\eta<\infty $ then $E\xi< \infty $ and $E\xi \leq E\eta$.
-  If $E\xi$ exists then $\lvert E\xi \rvert \leq E\lvert \xi \rvert$.
-  If $E\xi$ exists then $E(\xi I_{A})$ exists for each $A\in \mathcal{F}$; if $E\xi $ is finite, then $E(\xi I_{A})$ is finite.
-  If $\xi \text{ and } \eta$ are nonnegative random variables, or such that $E\lvert \xi \rvert <\infty$ and $E\lvert \eta \rvert <\infty$, then $E(\xi+\eta)=E\xi+E\eta$.

We say that a property holds "<strong>P-almost surely</strong>" if $\exists$ a set $\mathcal{N}\in \mathcal{F}$ with $P(\mathcal{N})=0$ such that the property holds for every point $w \in \Omega \setminus \mathcal{N}$.

-  If $\xi=0 $(a.s.) then $E\xi =0$.
-  If $\xi=\eta $ (a.s.) and $E\lvert \xi\rvert <\infty$, then $E\eta <\infty$ and $E\xi=E\eta$.
-  Let $\xi\geq 0$ and $E\xi=0$, then $\xi=0$ (a.s.)
-  Let $\xi \text{ and }\eta$ be such that $E\lvert \xi \rvert$, $E\lvert \eta\rvert$ and $E(\xi I_{A})\leq E(\eta I_{A})$ for all $A\in \mathcal{F}$, then $\xi\leq \eta$ (a.s.)
-  Let $\xi$ be an extended random variable (that is $\xi \in \bar{\mathbb{R}}=[-\infty,+\infty]$) and $E\lvert \xi\rvert <\infty$, then $\lvert \xi \rvert <\infty$.

<center>Part III</center>
***
The last part we will consider some fundamental theorems on <strong>taking limits</strong> under the expectation sign.

{% alert info %}

<b>Monotone Convergence Theorem:</b><br>
If $\xi_n\geq \eta$ for all $n\geq 1$, $E\eta >-\infty$ and $\xi_n\uparrow\xi$, then $E\xi_n\uparrow E\xi$.

{% endalert %}


Proof:<br>

- suppose $\eta \geq 0$, for each $k\geq 1$, let $\{\xi_k^{n}\}_{n\geq 1}$be a subsequence of simple functions that $\xi_{k}^{(n)} \uparrow, n\rightarrow \infty$. Let $\zeta^{(n)} =max_{1\leq k\leq n} \xi_{k}^{(n)}$.
Then we have
$$
\zeta^{(n-1)} \leq \zeta_{(n)} = max_{1\leq k\leq n} \,\xi_{k}^{(n)} \leq max_{1\leq k\leq n} \,\xi_k =\xi_n
$$
Let $\zeta=\lim_n \zeta^{(n)}$, since $\xi_{k}^{(n)} \leq \zeta^{(n)}\leq \xi_n$, then $\xi_k\leq \zeta\leq \xi, \text{ as } n\rightarrow \infty$. Therefore $\xi=\zeta$. Since $\zeta^{(n)}$ are simple and $\zeta^{(n)}\uparrow \zeta$, then $E\xi=E\zeta =\lim E\zeta^{(n)} \leq \lim E\xi_n$.
On the other hand, since $\xi_{n}\leq \xi_{n+1}\leq \xi$, then $\lim E\xi_n \leq E\xi$.
Consequently, $\lim E\xi_n =E\xi$.
- Let $\eta$ be any random variable with $E\eta >-\infty$, if $E\eta =\infty$, then $E\xi_n=E\xi=\infty$. If $E\eta <\infty$, then it is clear that $0\leq \xi_n-\eta \leq \xi-\eta$ for $w\in \Omega$, therefore we have $E(\xi_n-\eta) \uparrow E(\xi-\eta)$. Consequently we have $E\xi_n \uparrow E\xi$ due to $E\eta <\infty$.

{% alert info %}

<b> Fatou's Lemma: </b><br>
(a) If $\xi_n\geq \eta$ for all $n\geq 1$, $E\eta >-\infty$, then 
$$E \varliminf \xi_n \leq \varliminf E\xi_n
$$
<br/>
(b) If $\lvert \xi_n\rvert \leq \eta$ for all $n\geq 1$ and $E\eta <\infty$, then 
$$ E\varliminf \xi_{n} \leq \varliminf E\xi_n \leq \varlimsup E \xi_{n} \leq E\varlimsup \xi_{n}$$

{% endalert %}


Proof: <br>
(a)Let $\zeta_n=\inf_{m\geq n} \xi_m$, then 
$$
E\varliminf \xi_n = \lim_{n} \inf_{m\geq n}\xi_m =\lim_{n}\zeta_n
$$
Since $\zeta_n \uparrow \varliminf \xi_n$ and $\zeta_n \geq \eta$ for all $ n\geq 1$, then according to Monotone Convergecen theorem, we have
$$
E\varliminf \xi_n =E\lim_{n} \zeta_n =\lim_n E\zeta_n =\varliminf_n E\zeta_n \leq \varliminf E\xi_n
$$
The second conclusion follows (a).

{% alert info %}

<b> Dominated Convergence Theorem:</b><br>
Let $\lvert\xi_n\rvert \leq \eta, E\eta <\infty$ and $\xi_n \rightarrow \xi$ (a.s.), then $E \lvert \xi \rvert <\infty$
$$E\xi_{n} \rightarrow E \xi $$
and 
$$E \lvert \xi_{n} -\xi \rvert\rightarrow 0$$
as $n\rightarrow 0$.


{% endalert %}

Proof:<br>

(a) By Fatou's Lemma, we have
$$ E \varliminf \xi_n \leq \varliminf E \xi_n \leq \varlimsup E \xi_n \leq E\varlimsup \xi_n$$
Since $\xi_n \rightarrow \xi$ (a.s.), we have $\varliminf \xi_n =\varlimsup \xi_n =\xi $ (a.s.), therefore $E\xi=E\varliminf \xi_n=E\varlimsup \xi_n$

(b) since $\lvert \xi_n-\xi \rvert \leq 2\eta$ and $\lvert \xi_n-\xi \rvert \rightarrow 0$ (a.s.), then we have $\lim_{n\rightarrow 0} E\lvert\xi_n -\xi \rvert =0$.

