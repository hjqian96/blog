---
title: Idea to prove weak convergence by using perturbed test function method (I)
mathjax: true
categories:
  - Weak Convergence
tags:
  - Weak Convergence
  - Tightness
  - Perturbed Test Function Method
abbrlink: 484e613f
date: 2020-04-27 21:44:46
---

This post is my reading notes on Kushner [^1].
It is about the outline for proving weak convergence related to Martingale problem. For theorems listed below, proofs will not be demonstrated in this post. If time permits, it will appear on a seperate post that will be showed the link once I finish.

Before moving to the idea of proving weak convergence, we start with some preliminary knowledge.

#### p-limit and infinitesimal operator $\hat{A^{\varepsilon}}$

- $\mathscr{M}$ denote the set of real-valued measurable function of $(w,t)$
that are nonzero only on a bounded $t$-variable.
- $\bar{\mathscr{M}^{\varepsilon}}$ denote the subset for which $\sup_{t}E|f(t)|<\infty$ and $f(t)$ is $\mathcal{F}_{t}^{\varepsilon}$-measurable.

we define the $p$-limit as follows.

{% alert info %}

<strong>Definition 1</strong> <br>
let $f$ and $f^{\delta}$ be in $ \bar{\mathscr{M}^{\varepsilon}}$ for each $\delta>0$, then we say $f= p-\lim_{\delta}f^{\delta}$ iff
$$
\sup_{t,\delta} E|f^{\delta}(t)|<\infty  \\
\lim_{\delta\rightarrow 0} E|f^{\delta}(t)-f(t)|=0 \quad \text{for each} t.
$$
{% endalert %}

we define the infinitesimal operator as follows.

{% alert info %}

**Definition 2**<br>
let $f$ and $f^{\varepsilon}$ be in $ \bar{\mathscr{M}^{\varepsilon}}$ for each $\varepsilon>0$, then we say $f(\cdot)\in \mathscr{D}(\hat{A^{\varepsilon}})$ and $\hat{A^{\varepsilon}}f=g$ if $f, g\in \bar{\mathscr{M}^{\varepsilon}}$ and 
$$
\text{p}\_\lim_{\delta\rightarrow 0} \left[\frac{E_{t}^{\varepsilon}f(t+\delta)-f(t)}{\delta}-g(t)\right]=0
$$
i.e.
$$
\lim_{\delta\rightarrow 0} E\left| \frac{E_{t}^{\varepsilon}f(t+\delta)-f(t)}{\delta}-g(t) \right|=0.
$$
{% endalert %}

Basically, above definition for $\hat{A^{\varepsilon}}$ says that if $f\in \mathscr{D}(\hat{A^{\varepsilon}})$, then $\hat{A^{\varepsilon}}$ exists in some sense and 
$$
\hat{A^{\varepsilon}}=\text{p}-\lim_{\delta\rightarrow 0} \frac{E_{t}^{\varepsilon}f(t+\delta)-f(t)}{\delta}-g(t).
$$

Due to above definition, $\hat{A^{\varepsilon}}$ is a type of infinitesimal operator. Now we are in position to state a useful property of $\hat{A^{\varepsilon}}$ by the following theorem [^2].

{% alert info %}
**Theorem 1**: <br>
Suppose $f(\cdot)\in \mathscr{D}(\hat{A^{\varepsilon}})$. Then
$$
M_{\varepsilon}^{f}(t) \equiv f(t)-\int_{0}^{t} \hat{A^{\varepsilon}} f(u)du
$$
is a martingale and also
$$
\begin{align}
    E_{t}^{\varepsilon} f(t+s)-f(t)=\int_{t+s}^{t} E_{t}^{\varepsilon} \hat{A^{\varepsilon}} f(u)du \quad \text{w.p.1} \tag{1-1} \label{1-1}
\end{align}
$$
{% endalert %}

<strong>Remark 1</strong>: $\eqref{1-1}$ actually implies the Martingale property.

<strong> Remark 2</strong>: we make a remark that if $f$ is continuously differentiable and have compact support, then $\hat{A^{\varepsilon}}$ is simply a *differentiation operator*. Take an example, if $f$ satisfies previous conditioin, then  $\hat{A^{\varepsilon}}f(x)=f'_{x}(x)\dot{x}$.

#### Idea of the Perturbed Test Function Method

This section is about what is the perturbed test function method which is useful to prove weak convergence. Before proceeding to introduce the method, let us first look at the realtion between the solution of the [martingale problem](https://web.ma.utexas.edu/mediawiki/index.php/Martingale_Problem) and that of the stochastic differential equations. 

First, we say that $x(\cdot)$ solves the martingale problem for operator $A$ if $M_{f}$ is a martingale for each $f \in \hat{C}_{0}^{2}$ [^3], where $M_f(\cdot)= f(x(t))-f(x(0))-\int_{0}^{t}Af(x(s))ds$.

Second, if $x(\cdot)$ solves a SDE, then it can be shown that the following holds
$$
\begin{align}
& E h(x(t_i);i\leq \kappa)\left[M_{f}(t+s)-M_{f}(t)\right] \\
& = E h(x(t_i);i\leq \kappa)\left[f(x(t+s))-f(x(t))-\int_{t}^{t+s} Af(x(u))du \right] \\
&=0
\tag{2-1}\label{2-1}
\end{align}
$$
where conditions about $h,\kappa,t_i$ are omitted here to make the outline or idea as simple as possible.

For $x(\cdot)$ satisfies $\eqref{2-1}$ for $h,\kappa,t,t+s, t_{i}$, then 
$$
E[M_{f}(t+s)-M_{f}(t)|x(u),u\leq t]=0
$$
for each $t$ and $s>0$, which shows that $M_{f}(\cdot)$ is a martingale. That is to say, this process $x(\cdot)$ sovles the martigale problem for operator $A$.

The **idea** of perturbed test fucntion method lies on if we cannot obtain exactly $\eqref{2-1}$, instead we have
$$
\begin{align}
E h(x(t_i);i\leq \kappa)\left[f^{\varepsilon}(t+s)-f^{\varepsilon}(t)-\int_{t}^{t+s} \hat{A^{\varepsilon}}f^{\varepsilon}(u) du\right]=0
\end{align}
$$

In addition, we put some conergence condition on $f^{\varepsilon}$ in a sense, that is if we could show 
$$
\begin{align}
 E|f^{\varepsilon}(t)-f^{\varepsilon})| &\rightarrow 0 \quad \text{ for each } t \\
 E|\hat{A^{\varepsilon}} f^{\varepsilon}(t)-Af(x^{\varepsilon}(t))|&\rightarrow 0\\ 
 \sup_{t\leq T, \varepsilon >0} E|\hat{A^{\varepsilon}} f^{\varepsilon}(t)| &<\infty \quad\text{for each } T<\infty.
\end{align}
$$

Therefore based on above convergence results, we could say the limit of $x^{\varepsilon}(\cdot)$ satisfies $\eqref{2-1}$. Then suppose $\{x^{\varepsilon}(\cdot)\}$ is tight, the limit of any weakly convergent subsequence satisfies $\eqref{2-1}$. If $x^{\varepsilon}(0) \Rightarrow x(0)$ and there is a unique solution to the martingale problem for operator $A$ and each initial condition, then the limit is that unique solution with initial condition $x(0)$.

#### The Main Convergence Theorem

{% alert info %}
**Theorem 2**
Let the martingale problem for diffusion or jump diffusion operator $A$ have a unique solution $x(\cdot)$ in $D^{r}[0,\infty)$ for each initial condition.

For each $T>0$, $f(\cdot)\in C_{1}$ a dense set in $\hat{C}_{0}$, suppose there exists $f^{\varepsilon}(\cdot)\in \mathscr{D}(\hat{A^{\varepsilon}})$ (here at first we assume the existence of $f^{\varepsilon}$, later on using perturbed test function method will show that existence seperatly) such that
$$
\text{p}-\lim_{\varepsilon}\left[f^{\varepsilon}(\cdot)-f(x^{\varepsilon}(\cdot))\right]=0
$$
and either
$$
\text{p}-\lim_{\varepsilon}\left[\hat{A^{\varepsilon}}f^{\varepsilon}(\cdot)-Af(x^{\varepsilon}(\cdot))\right]=0 \quad \text{for } t\leq T
$$
or 
$$
E\left|\int_{t}^{T}\left[E_{t}^{\varepsilon}\hat{A^{\varepsilon}}f^{\varepsilon}(u)-E_{t}^{\varepsilon} Af(x^{\varepsilon}(u))\right]du\right| \stackrel{\varepsilon\rightarrow 0}{\rightarrow } 0 \quad \text{for eachs} t\leq T
$$

Suppose $\{x^{\varepsilon},\varepsilon>0\}$ be tight in $D^{r}[0,\infty)$ (here we assume the tightness at first, how to prove tightness will be addressed later on) and $x^{\varepsilon}(0)\Rightarrow x(0)$

Then we have $x^{\varepsilon}(\cdot)\Rightarrow x(\cdot)$ with $x(0)=x_{0}$.

{% endalert %}

#### Tightness

Since Theorem 2 requries tightness for $\{x^{\varepsilon}\}$ in $D^{r}[0,\infty)$, this section we are supposed to deal with tightness issue.

For tightness in either $C^{r}[0,\infty)$ or $D^{r}[0,\infty)$, we need
$$
\lim_{K\rightarrow \infty} \overline{\lim_{\varepsilon}} P\{\sup_{t\leq T} |x^{\varepsilon}|\geq K\} =0 \quad \text{for each } T<\infty. \tag{3-1}\label{3-1}
$$

If $\eqref{3-1}$ holds for each $T<\infty$, then $\{x^{\varepsilon}\}$ is tight in $D^{r}[0,\infty)$ if $\{f(x^{\varepsilon}(\cdot))\}$ is tight in $D^{r}[0,\infty)$ for each $f(\cdot)$ in any dense set in $\hat{C}_{0}$. You might refer to [^4].

{% alert info %}
**Theorem 3** <br>
Suppose $\{y^{\varepsilon}(\cdot)\}$ is a sequence of processes in $D^{r}[0,\infty)$ and $\{y^{\varepsilon}(\cdot)\}$ satisfies $\eqref{3-1}$, that is to say
$$
\lim_{K\rightarrow \infty} \overline{\lim_{\varepsilon}} P\{\sup_{t\leq T} |x^{\varepsilon}|\geq K\} =0 \quad \text{for each } T<\infty.
$$
Let $\{y^{\varepsilon}(\cdot)\}$ be $\mathcal{F}_{t}^{\varepsilon}$-measrable, $E_{t}^{\varepsilon}=E[\cdot| \sigma\{y^{\varepsilon}(s); s\leq t\}]$. For each $T<\infty, \delta>0, \varepsilon >0$, there be a random variable $\gamma_{\varepsilon}(\delta)$ s.t.
$$
\begin{align}
E_{t}^{\varepsilon} \min\{1, |y^{\varepsilon}(t+u)-y^{\varepsilon}|^{2}\}&\leq E_{t}^{\varepsilon} \gamma_{\varepsilon}(\delta), \quad 0\leq u\leq\delta, t\leq T \\
\lim_{\delta \rightarrow 0}\overline{\lim_{\varepsilon \rightarrow 0}} E\gamma_{\varepsilon}(\delta) & =0
\end{align}
$$
Then $\{y^{\varepsilon}(\cdot)\}$ is tight in $D^{r}[0,\infty)$.

{% endalert %}

Above theorem is for general processes $y^{\varepsilon}(\cdot)$, in our case, we need $y^{\varepsilon}(\cdot)$ equals $f(x^{\varepsilon}(t))$ or $f(x^{\varepsilon,N}(t))$. The next theorem is about the tightness for $x^{\varepsilon}(\cdot)$.

{% alert info %}
**Theorem 4**<br>
For $x^{\varepsilon}(\cdot)$, we suppose
$$
\lim_{K\rightarrow \infty} \overline{\lim_{\varepsilon}} P\{\sup_{t\leq T} |x^{\varepsilon}|\geq K\} =0 \quad \text{for each } T<\infty
$$
$C_{2}$ is a dense set of functions in $\hat{C}_{0}$ that contains the square of each function. For each $f(\cdot)\in C_{2}$, suppose there exists $\{f^{\varepsilon}(\cdot)\}$ such that $f^{\varepsilon}(\cdot)\in \mathscr{D}(\hat{A^{\varepsilon}})$ (here we assume the existence of perturbed test function at first, it will be addressed in next post). And also either (I) and (II) holds,

(I) For $T>0$, $\{\hat{A^{\varepsilon}}f^{\varepsilon}(t),0<t\leq T\}$ is uniformly integrable for $f(\cdot)\in C_{2}$ and
$$
\begin{align}
    \lim_{\varepsilon \rightarrow 0}P\{\sup_{t\leq T}|f^{\varepsilon}(t)-f(x^{\varepsilon})|\geq \alpha\}=0,\quad \text{ for each } \alpha>0
\end{align}
$$
(II)
$$
\begin{align} 
    \lim_{\varepsilon \rightarrow 0}P\{\sup_{t\leq T}|f^{\varepsilon}(t)-f(x^{\varepsilon})|\geq \alpha\}=0,\quad \text{ for each } \alpha>0
   \end{align}
$$
for each $T<\infty, f(\cdot)\in C_{2}$, there exists a random variable $B_{T}^{\varepsilon}(f)$, s.t.
$$
\begin{align}
    \sup_{t\leq T}|A^{\varepsilon}f^{\varepsilon}(t)| &\leq B_{T}^{\varepsilon}(f)\\
    \lim_{K\rightarrow \infty}\overline{\sup_{\varepsilon}} P\{B_{T}^{\varepsilon}\geq K\} & =0
\end{align}
$$
Then we have $\{x^{\varepsilon}(\cdot)\}$ and $\{f(x^{\varepsilon}(\cdot))\}$ are tight in $D^{r}[0,\infty)$.

{% endalert %}


[^1]: Kushner(84):Approximation and Weak Convergence Methods for Random Process, with Applications to Stochastic Systems Theory
[^2]: Kurtz, 1975
[^3]: $\hat{C}_{0}^{2}$ is a dense subset 
[^4]: Billingsley: Convergence of probability measures.
