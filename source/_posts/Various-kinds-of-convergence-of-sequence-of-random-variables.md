---
title: Various kinds of convergence of sequence of random variables
mathjax: true
categories: Probability
tags:
  - convergence almost sure
  - convergence with probability one
  - congvergence in probaility
  - convergence in distribution
  - convergence in mean of order p
abbrlink: 2144e38d
date: 2019-09-01 09:36:07
---
This post will states various kinds of convergence of sequence of random variables, i.e. convergence almost sure(w.p.1), convergence in probability, convergence in distribution and convergence in mean of order p. At first, we will state definitions for all above kinds of convergence and then we will see their relations. Secondly, Cauchy criterions for almost sure convergence, convergence in probability and convergence in mean $p$-th power will be demonstrated.

Let $\{\xi_n\},\xi$ be a sequence of random variables on $(\Omega, \mathcal{F},P)$

{% alert info %}

<b> Definitions: </b> <br>

(1). $\xi_n$ converges to $\xi$ in probability denoted as $\xi_n \stackrel{p}{\rightarrow} \xi$: if for every $\varepsilon>0$, 
   $$ P\{\lvert\xi_n-\xi\rvert>\varepsilon\}\rightarrow 0,\, n\rightarrow \infty. \tag{1}$$

(2). $\xi_n$ converges to $\xi$ almost surely (with probability 1) denoted as $\xi_n\rightarrow \xi$ (P-a.s.) or $\xi_n\stackrel{a.s}{\rightarrow}\xi$, if 

$$P\{w: \xi_n \nrightarrow \xi\}=0.\tag{2}$$

(3). $\xi_n$ converges to $\xi$ in mean of order $p$ denoted as $\xi_n \stackrel{L^p}{\rightarrow} \xi$ if

$$E|\xi_n-\xi|^p\rightarrow 0,\quad n\rightarrow \infty.\tag{3}$$

(4). $\xi_n$ converges to $\xi$ in distribution denoted as $\xi_n \stackrel{d}{\rightarrow}\xi$, if 
$$
    Ef(\xi_n)\rightarrow Ef(\xi),\quad n\rightarrow \infty.\tag{4}
$$
for every bounded continous function $f=f(x)$.

{% endalert %}

<!--more-->

{% alert info %}

<b>Theorem 1</b><br>
    (a) A necessary and sufficient condition that $\xi_n\rightarrow \xi(P-a.s.)$ is that $$P\{\sup_{k\geq n}|\xi_k-\xi|\geq \varepsilon\} \rightarrow 0, \quad n\rightarrow \infty.\tag{5}$$
    for every $\varepsilon >0$.<br>
    (b) The sequence $\{\xi_n\}_{n\geq 1}$ is fundamental with probability 1 if and only if 

$$    P\{ \sup_{k\geq n, l\geq n}|\xi_k-\xi_l|\geq \varepsilon \} \rightarrow 0, \quad n\rightarrow \infty\tag{6}$$

​    for every $\varepsilon\rightarrow 0$. Or equivalently,
​    $$ P\{\sup_{k\geq 0} |\xi_{n+k}-\xi_n|\geq \varepsilon\}\rightarrow 0, \quad n \rightarrow \infty.\tag{7}$$
{% endalert %}

Proof:

{% alert info %}

<b>Corollary 1</b><br>
 Since
$$
 P\{\sup_{k\geq n} |\xi_k-\xi|\geq \varepsilon\}=P\{\cup_{k\geq n}(|\xi_k-\xi|\geq \varepsilon)\} \leq \sum_{k\geq n}P\{|\xi_k-\xi|\geq \varepsilon\}
$$
 a sufficient condition for $\xi_n\stackrel{a.s.}{\rightarrow} \xi$ is that
 $$\sum_{k=1}^{\infty} P\{|\xi_k-\xi|\geq \varepsilon\}< \infty$$
 is satisfied for every $\varepsilon>0$.
{% endalert %}

Let $A_1, A_2, A_3,\cdots$ be a sequence of events in $\mathcal{F}$. Also we let $\{A_n, \text{i.o.}\}$ denote the event of $\varlimsup A_n$, then we have the following<br>

{% alert info %}

<b>Borel-Cantelli Lemma</b><br>
    (1) If $\sum P(A_n)<\infty$, then $P\{A_n \text{ i.o.}\}=0.$
    (2) If $\sum P(A_n)=\infty$ and $A_1, A_2,\cdots$ are independent, then $P\{A_n \text{ i.o.}\}=1.$
{% endalert %}


Proof:<br>
- According to definition, we have
$$
\{A_n,\text{i.o.}\}=\varlimsup A_n=\cap_{n=1}^{\infty}\cup_{k\geq n} A_k.
$$
Therefore,
$$
P\{A_n,\text{i.o.}\}=P\left\{\cap_{n=1}^{\infty}\cup_{k\geq n} A_k \right\}=\lim P\left(\cup_{k\geq n}\right) \leq \lim\sum_{k\geq n} P(A_k)
$$
Then we have (a).
- If $A_1, A_2, A_3,\cdots$ are independent, then $\bar{A_1},\bar{A_2},\cdots$ are independent. Hence for $N\geq n$, we have 
$$
P\left( \cap_{k=n}^{N}\bar{A_k}\right)=\Pi_{k=n}^{N}P(\bar{A_k})
$$
then we can get
$$
P\left( \cap_{k=n}^{\infty}\bar{A_k}\right)=\Pi_{k=n}^{\infty}P(\bar{A_k})
$$
Since $\log(1-x)\leq -x,\,0\leq x\leq 1$, then we are able to obtain
$$
\log\Pi_{k=n}^{\infty}[1-P(A_k)]=\sum_{k=n}^{\infty}\log[1-P(A_k)]\leq -\sum_{k=n}^{\infty} P(A_k)=-\infty.
$$
Therefore, we have $P\left(\cap_{k=n}^{\infty}\bar{A_k}\right)=0$ for all n, then $P(A_n,\text{i.o.})=1$.

At the begining of this post, we demonstrates definitions of various kinds of convergence in Proability theory. Now we are going to see what are relationships between them.<br>

{% alert info %}

<b>Theorem 2</b><br>
    We have the following implications for various types of convergence:<br>
    
$$
\xi_n \stackrel{a.s.}{\rightarrow}\xi \implies \xi_n\stackrel{P}{\rightarrow} \xi,\tag{9}
$$
    
$$
\xi_n\stackrel{L^p}{\rightarrow}\xi \implies \xi_n\stackrel{P}{\rightarrow}\xi,\quad p>0,\tag{10}
$$

$$
\xi_n\stackrel{P}{\rightarrow}\xi \implies \xi_n\stackrel{d}{\rightarrow}\xi.\tag{11}
$$
{% endalert %}

Proof:<br>

- In order to prove $\eqref{9}$, we are going to make use of Corollary 1.


As we known in analysis, every fundamental sequence is convergent, i.e. Cauchy criterion. Similarily, we are going to establish Cauchy criterion for the convergence of a sequence of random variables. The rest parts are about Cauchy criterion for almost sure convergence, convergence in probability and convergence in mean $p$-th power.

{% alert info %}

<b>Theorem 3</b>(Cauchy Criterion for Almost Sure Convergence)<br>
$$
\xi_n\stackrel{a.s.}{\rightarrow} \xi \Leftrightarrow \{\xi_n\}_{n\geq 1} \text{ is fundamental with probability 1} \tag{12}
$$

{% endalert %}


Proof:<br>

- "$\Rightarrow$" If $\xi_n\stackrel{a.s.}{\rightarrow}\xi$, then according to Theorem 1, we have
$$
\sup_{k\geq n,l\geq n}|\xi_k-\xi_l|\leq \sup_{k\geq n}|\xi_k-\xi|+\sup_{l\geq n}|\xi_l-\xi|
$$
Therefore, we have
$$
P\{\sup_{k\geq n,l\geq n}|\xi_k-\xi_l|\geq \varepsilon\}\leq P\{\sup_{k\geq n}|\xi_k-\xi|\geq \frac{\varepsilon}{2}\}+P\{\sup_{l\geq n}|\xi_l-\xi|\geq \frac{\varepsilon}{2}\} \rightarrow 0
$$
Hence we get $\{\xi_n\}_{n\geq 1}$ is fundamental w.p.1

- "$\Leftarrow$" Let $\{\xi_n\}_{n\geq 1}$ be fundamental with probability 1, then let $N=\{w: \xi_n(w)\text{ is not fundamental}\}$. Therefore for every $w\in \Omega \setminus N$, $(\xi_n(w))$ is fundamental, then by Cauchy's theorem for real numbers, we get $\lim \xi_n(w)$ exists. Finally, we define
$$
\xi(w)=
\begin{cases}
    \lim \xi_n(w), \quad w\in \Omega\setminus N,\\
    0, \quad w\in N
\end{cases}
$$
Hence we could get that $\xi(w)$ is a random variable and $\xi_n\stackrel{a.s.}{\rightarrow}\xi$.

Before we proceed to Cauchy criterion for convergence in probability, we demonstate a theorem about subsequence. In real analysis, we know that a fundamental sequence of real numbers or a Cauchy sequence has a convergent subsequence. Here we still have similar results, which is the following theorem.

{% alert info %}

<b>Theorem 5</b><br>
    IF the sequence $(\xi_n)$ is fundamental in probability, then there exists a subsequence $(\xi_{n_k})$ is fundamental w.p.1. i.e.
$$
    \xi_n\stackrel{p}{\rightarrow}\xi \implies \exists\, \xi_{n_k} \text{ s.t. } \xi_{n_k}\stackrel{a.s.}{\rightarrow}\xi.
$$

In the above theorem, we take advantage of Cauchy criterion for convergence in probability which we will state later.

{% endalert %}

Proof:<br>
By using Theorem 4, it suffices to prove that $\xi_{n_k}\stackrel{a.s.}{\rightarrow}\xi$. Since $(\xi_n)$ is fundamental in probability, we have 
$$
\lim_{n,m\rightarrow \infty} P(|\xi_n-\xi_m|>\eta)=0.
$$
Then $\forall\,k>0, \exists \,n_k>0, \text{s.t.} \forall\, s\geq n_k, t\geq n_k$,
$$
P(|\xi_s-\xi_t|>2^{-k})\leq 2^{-k}.
$$
Especially, let $s=n_{k+1}, t=n_k$, then we have $P(|\xi_{n_{k+1}}-\xi_{n_k}|>2^{-k})\leq 2^{-k}$. Therefore, we have
$$\sum_{k} P(|\xi_{n_{k+1}}-\xi_{n_k}|>2^{-k})<\sum_{k}2^{-k}<\infty.$$
By Borel-Cantelli lemma, $P(|\xi_{n_{k+1}}-\xi_{n_k}|>2^{-k} \text{i.o.})=0$, i.e. the event $\{|\xi_{n_{k+1}}-\xi_{n_k}|\leq2^{-k}\}$ has probability 1. Hence 
$$\sum_{k=1}^{\infty}|\xi_{n_{k+1}}-\xi_{n_k}|\leq \sum_{k=1}^{\infty}2^{-k} <\infty.$$
Let $N=\{w: \sum_{k=1}^{\infty}|\xi_{n_{k+1}}-\xi_{n_k}|=\infty\}$, then define
$$
\xi(w)=
\begin{cases}
    \xi_{n_1}(w)+\sum_{k=1}^{\infty}|\xi_{n_{k+1}}-\xi_{n_k}|, \quad w\in \Omega\setminus N, \\
    0, \quad w\in N
\end{cases}
$$
Therefore we are able to attain $\xi_{n_k}\stackrel{a.s.}{\rightarrow}\xi$. $\quad\quad$&diams;

{% alert info %}

<b>Theorem 6</b>( Cauchy Criterion for convergence in Probability)<br>

​    $$\xi_n\stackrel{p}{\rightarrow}\xi\Leftrightarrow (\xi_n) \text{ is fundamental in probability}$$.

{% endalert %}

Proof:<br>

- "$\Leftarrow$" If $\xi_n\stackrel{p}{\rightarrow}\xi$, then
$$
P\{|\xi_n-\xi_m|\geq \varepsilon\} \leq P\{|\xi_n-\xi|\geq \frac{\varepsilon}{2}\}+P\{|\xi_n-\xi|\geq \frac{\varepsilon}{2}\} \rightarrow 0
$$
Therefore $(\xi_n)$ is fundamental in probability
- "$\Rightarrow$" If $(\xi_n)$ is fundamental in probability, then there exists a sequence $(\xi_{n_k})$ and a random variable such that $\xi_{n_k}\stackrel{a.s.}{\rightarrow}\xi$, then $\xi_{n_k}\stackrel{p}{\rightarrow}\xi$. Therefore,
$$
P\{|\xi_n-\xi|\geq \varepsilon\}\leq P\{|\xi_n-\xi_{n_k}|\geq \frac{\varepsilon}{2}\}+P\{|\xi_{n_k}-\xi|\geq \frac{\varepsilon}{2}\} \rightarrow 0.
$$



