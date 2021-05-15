---
title: Stopping times
tags:
  - Stopping time
  - Optional time
  - Hitting time
mathjax: true
abbrlink: c419613f
date: 2019-07-26 11:26:01
categories: Stochastic Calculus Notes
---

For this article, I will mainly demonstrate the definition of stopping time, optional time and hitting time and their propertities.

### Definition
For a measurable space $(\Omega,\mathcal{F})$ equipped with a filtration $\{\mathcal{F}_t\}$
a random time $T$ is a <u>[Stopping time](https://en.wikipedia.org/wiki/Stopping_time)</u> of the filtration if $\{w,T(w)\leq t\} \in \mathcal{F}_t$ for every $t \geq 0$;
a random time $T$ is a Optional time of the filtration if $\{w,T(w)< t\} \in \mathcal{F}_{t}$ for every $t \geq 0$.

**Remark**: Every stopping time is optimal and the two concepts concide if the filtration is right-continuous. Since $\{T<t \}=\cup_{n=1}^{\infty} \{ T\leq t-(1/n) \} \in \mathcal{F_t}$, so the stopping time is optional. For the next claim, suppose $T$ is a optional time and the filtration is right-continuous, then for every positive integer $m$, we have $\{T\leq t\} = \cap_{n=m}^{\infty} \{ T < t+(1/n)\} \in \mathcal{F}_{t+\frac{1}{m}}$, therefore $\{T\leq t\}\in \mathcal{F}_{t^{+}} = \mathcal{F}_{t} $. 

Now, consider a stochastic process $X$ with right-continuous paths, which is adapted to a filtration $\{\mathcal{F}_t\}$. For $\Gamma \in \mathcal{B}(\mathbb{R}^d)$ of the state space, we could define the <u>[Hitting time](https://en.wikipedia.org/wiki/Hitting_time)</u> as follows: $$ H_{\Gamma}(w)= \inf\{t\geq 0; X_t(w)\in \Gamma\}$$.
<!--more-->

### Some Propertities of Stopping time
{% alert info %}
<b>Lemma 1</b>: If $T$ is optional and $\theta >0$ constant, then $T+\theta$ is a stopping time.

{% endalert %}

**Proof:**  If $0\leq t<\theta$, then $\{T+\theta <t\}$ is empty, which is in $\mathcal{F}_t$; if $t\geq \theta$, then $\{T+\theta < t\}=\{T< t-\theta\}\in\mathcal{F}_{(t-\theta)^{+}}\subseteq\mathcal{F}_t$.

{% alert info %}
<b>Lemma 2</b>: If $T,S$ are stopping times, then so are $T\wedge S$, $T\vee S$, $T+S$.

{% endalert %}

**Proof:**  we only consider the third case. For $t>0$,
$$
\begin{align}
    \{T+S>t\}=&\cup\{T=0, S>t\} \cup\{0<T<t,T+S>t\}\\
&\cup \{T>t, S=0\} \cup\{T>t,S>0\}
\end{align}
$$
Since the first, third and fourth events are in $\mathcal{F}_t$, then we only need to consider the second item,
$$
\{ 0<T<t,T+S>t\}= \bigcup_{r\in Q^{+} \\r<T<t} \{t<T<r,S>t-r\}
$$

{% alert info %}

<b>Lemma 3</b>: Let $\{T_n\}_{n=1}^{\infty}$ be a sequence of optional times, then the random times

$$ \sup\limits_{n\geq 1}T_n,\quad \inf\limits_{n\geq 1}T_n,\quad \varlimsup_{n \to \infty}T_n,\quad \varliminf_{n\to \infty}T_n $$

{% endalert %}


**Proof:** since 
$$
\begin{align}
    \{\sup_{n\geq 1} T_n \leq t \}&=\cap_{n=1}^{\infty} \{T_n \leq t\} \\
    \{\inf_{n\geq 1} T_n < t\}&=\cup_{n=1}^{\infty} \{T_n < t\}
\end{align}
$$

---------

Until now, we've already know the definition of stopping time and some basic propertities about it. But how can we measure the information accumulated up to a stopping time $T$, i.e. how to define the $\sigma$-algebra $\mathcal{F}_T$ ? 

### Definition
Let $T$ be a stopping time of the filtration $\mathcal{F}_t$, then 
$$
\mathcal{F_T}=\left\{ A \in \mathcal{F} \,|\, A\cap \{T\leq t\} \in \mathcal{F}_t, \text{ for } t\geq 0 \right\}
$$
{% alert info %}
<b>Lemma 4</b>: For any two stopping times $T$ and $S$ and $X$ a process,

1. For any $A\in \mathcal{F}_S$, we have $A\cap\{S\leq T\}$ and $A\cap \{ S< T \}$ lie in $\mathcal{F}_T$. In particular, if $S\leq T$, we have $\mathcal{F}_S \subseteq \mathcal{F}_T$;
  <br/>
2. Both $T$ and $T\wedge S$ are $\mathcal{F}_T$-measurable and $\mathcal{F}_{T\wedge S}=\mathcal{F}_{T}\cap \mathcal{F}_{S}$. Also each of the events $\{T< S\}, \{S< T\}, \{T\leq S\}, \{S \leq T\}, \{T=S\}$ belongs to $\mathcal{F}_T\cap\mathcal{F}_S$;
  <br/>
3. If the process $X$ is [progressively measurable](progressively measurable process) then $X(T)$ is $\mathcal{F}_T$-measurable on the event $\{T<\infty\}$.

{% endalert %}

**Proof:** 

1. (a) Let $A\in \mathcal{F}_S$, then we need to show that $(A\cap \{T\leq S\})\cap \{T\leq t\} \in \mathcal{F}_t$. Since
$$
(A\cap \{T\leq S\})\cap \{T\leq t\} = (A\cap \{S\leq t\})\cap \{S\wedge t\leq  T\wedge t\} \cap \{T\leq t\}
$$
The first by the defnition of $A\in \mathcal{F}_S$, the second because both $S\wedge t$ and $T\wedge t$ are $\mathcal{F}_t$-measurable: for any $\mu \in \mathbb{R}$, $\{S\wedge t \leq \mu\} =\Omega$ if $\mu\geq t$ and $\{S\wedge t \leq \mu\} = \{S\leq u\}$ if $\mu < t$ which are in $\mathcal{F}_t$ in both cases. For the third term, $\{T\leq t \} \in \mathcal{F}_t$ since $T$ is a stopping time. In particular, if $S\leq T$, then we have $\mathcal{F}_S \subseteq \mathcal{F}_T$. 
(b) To show $A\cap \{S\leq T\} \in \mathcal{F}_T$, write
$$
A\cap \{S< T\} =\bigcup_{n\geq 1} A\cap \{S+\frac{1}{n}\leq T\} 
$$
For the right hand-side, since $A\cap \{S+\frac{1}{n}\leq T\}= A\cap \{S\leq T-\frac{1}{n}\} \in \mathcal{F}_{T-\frac{1}{n}} \subseteq \mathcal{F}_T$, then we have $A\cap \{S< T\} \in \mathcal{F}_T$.

2. (a) Since $\{T\leq s\}\cap \{T\leq t\} =\{T\leq s\wedge t\} \in \mathcal{F}_t,\; \forall s$, according to the definition of stopping time, we have $T$ is $\mathcal{F}_T$-measurable. Similarily, $S\wedge T$ is $\mathcal{F}_{S\wedge T} \subseteq \mathcal{F}_{T}$-measurable.

3. To prove $X(T)$ is $\mathcal{F}_T$-measurable, we need to show that for any $B\in\mathcal{B}(\mathbb{R}^d)$, $\{X_T \in B,T< \infty\} \cap \{T\leq  t\}\in\mathcal{F}_t$. At first, we claim that $w\mapsto X(T(w)\wedge t,w)\in \mathcal{F}_t$ since we could view it as the composition
$$
w\longmapsto (T(w)\wedge t,w)\longmapsto X(T(w)\wedge t,w)
$$
The fisrt step $w\longmapsto (T(w)\wedge t, w)$ is measurable as a map from $(\Omega, \mathcal{F}_t)$ into the product space $([0,t]\times \Omega, \mathcal{B}_{[0,t]}\otimes \mathcal{F}_t)$ since as proved in (1.(a)) that $w\longmapsto T(w)\wedge t$ is measurable from $\mathcal{F}_t$ into $\mathcal{B}_{[0,t]}$ and the other component is the identity map which is measurable. The second step of the compostion is measurable by the progressively measurable of X from $([0,t]\times \Omega, \mathcal{B}_{[0,t]}\otimes \mathcal{F}_t$ into $(\mathbb{R}^d,\mathcal{B}_{\mathbb{R}^d})$.
Therefore, $\{X_T \in B,T< \infty\} \cap \{T\leq t\}= \{X_{T\wedge t}\in B\}\cap \{T\leq t\}\in\mathcal{F}_t$.





