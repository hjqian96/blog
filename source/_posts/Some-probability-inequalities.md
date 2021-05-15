---
title: Some Probability Inequalities
categories:
    - Probability
    - Inequality
tags: [Gronwall Inequality, Chebyshev's Inequality, Jesen's Inequality, Lyapunov's Inequality, Holder's Inequality, Minkowski's Inequality]
mathjax: true
abbrlink: 81ff34cf
date: 2019-08-03 22:00:33
---
This article, I will mainly demonstrate some vital important inequalities in  probability theory and in analysis which are used very often when we are going to prove something, like to prove convergence.

<!--more-->

{% alert info %}
<b>Gronwall Inequality: </b> <br>
Let $v(t)$ be a <strong>nonnegative</strong> function such that 
$$
v(t)\leq C+A\int_{0}^{t}v(s)ds
$$
where $0\leq t\leq T$.Then we have $v(t)\leq Ce^{At}$  for all $0\leq t\leq T$。
{% endalert %}


**Proof:**

Let $w(t)=\int_{0}^{t}v(s)ds$, then we could get $w'(t)\leq C+Aw(t)$, i.e. $w'(t)-Aw(t)\leq C$. Multiply $exp(-At)$ to both side of ineqaulity, we get
$$
w'(t)e^{-At}-Aw(t)e^{-At} \leq C
$$
That is $w(t)e^{-At}\leq C$, therefore we could get $w(t)\leq \frac{C}{A}(exp(At)-1)$, then $v(t)\leq C exp(At)$.

{% alert info %}
<b>Chebyshev's Inequality: </b> <br>
Let $\xi$ be a <strong>nonnegative</strong> random variable. Then for every $\varepsilon >0$, we have
$$
P(\xi\geq \varepsilon)\leq\frac{E\xi}{\varepsilon}
$$
{% endalert %}


**Proof:**

$E\xi \geq E[\xi\cdot I_{\{\xi \geq \varepsilon\}}] \geq \varepsilon EI_{\{\xi\geq \varepsilon\} } =\varepsilon P(\xi \geq \varepsilon)$

The following variant of Chebyshev's inequalities hold: if $\xi$ is any random variable then
$$P(\xi \geq \varepsilon) \leq \frac{E\xi^2}{\varepsilon^2}$$
and 
$$P(\lvert \xi-E\xi \rvert \geq \varepsilon)\leq \frac{\text{var} \xi^2}{\varepsilon^2}$$

{% alert info %}
<b>Jesen's Inequality</b> <br>
Let $\varphi$ be a Borel convex function and $E\lvert\xi \rvert < \infty$, then
$$
\varphi(E\xi) \leq E\varphi(\xi)
$$
{% endalert %}


**Proof: **

since $\varphi$ is convex, then for each $x_0 \in \mathbb{R}$, there exists $\lambda(x_0)$ s.t.
$$\varphi(x) \geq \varphi(x_0)+(x-x_0)\lambda(x_0)$$
for all $x \in \mathbb{R}$. Then let $x=\xi$, $x_0=E\xi$, then we have
$$ \varphi(\xi)\geq \varphi(E\xi)+(\xi-E\xi)\lambda(E\xi)$$
therefore, we could get $E\varphi(\xi)\geq \varphi(E\xi)$.

{% alert info %}

<b>Lyapunnov's Inequality </b> <br>
For $0< s< t$,
$$(E\lvert\xi\rvert^{s})^{1\over s} \leq (E\lvert\xi\rvert^{t})^{1\over t}$$

{% endalert %}

**Proof: **
To prove this, let $\eta = \lvert \xi \rvert^s$, then applying Jensen's Inequality to $g(x)=x^r, \text{ where } r=\frac{t}{s}$, then we obtain
$\lvert E\eta \rvert^r \leq E\lvert \eta \rvert^r$, i.e.
$$
(E\lvert \xi \rvert)^{\frac{t}{s}} \leq E\lvert \xi^s \rvert
$$

In the following we are going to demonstrate Young's Inequality, Holder's Inequality and Minkowski's Inequality. I always put them together since we are going to use Young's ineqaulity to prove Holder's Inequality, and to use Holder's Inequality to prove Minkowski's Inequality. It will be very helpful to remember them by this way.

For Young‘s Inequality, I will skip its proof (you could refer [this](https://math.stackexchange.com/questions/566169/a-proof-of-youngs-inequality)) and only state it.

{% alert info %}

<b>Young's Inequality: </b> <br>
For $a>0, b>0$ and $p \text{ and } q$ are real numbers greater than 1 satisfying $1/p+1/q=1$, then $ab\leq \frac{a^p}{p}+\frac{b^q}{q}$.

{% endalert %}

{% alert info %}

<b>Holder's Inequality: </b> <br>
Let $1< p<\infty, 1< q <\infty$ and $\frac{1}{p}+\frac{1}{q}=1 $. If $E\lvert \xi\rvert^p <\infty$ and $E\lvert \eta\rvert^p<\infty$, then $E\lvert \xi\eta\rvert<\infty$ and
$$
E\lvert\xi\eta\rvert \leq \left(E\lvert\xi\rvert^p\right)^{\frac{1}{p}}\left(E\lvert\eta\rvert^q\right)^{\frac{1}{q}}
$$

{% endalert %}



**Proof: **

- If $E\lvert \xi \rvert^p=0 \text{ or } E\lvert \eta \rvert^q=0 $, it is obvious.
- Let $E\lvert \xi \rvert^p>0, E\lvert \eta \rvert^q>0$, then let 
$$
\tilde{\xi} =\frac{\xi}{(E\lvert \xi \rvert^p)^{\frac{1}{p}}}, \tilde{\eta}=\frac{\eta}{(E\lvert \xi \rvert^q)^{\frac{1}{q}}}
$$
According to Young's Inequality, we have $\lvert \xi\eta \rvert \leq \frac{\lvert \tilde{\xi}\rvert^p}{p} +\frac{\lvert\tilde{\eta}\rvert^q}{q}$. Hence we obtain

$$ E\lvert \tilde{\xi} \tilde{\eta}\rvert \leq \frac{E\lvert\tilde{\xi}\rvert^p}{p}+\frac{E\lvert\tilde{\eta}\rvert^q}{q}=\frac{1}{p}+\frac{1}{q}=1$$

This establishes Holder's Inequality

{% alert info %}

<b>Minkowski's Inequality:  </b> <br>
If $ E \lvert\xi\rvert^p <\infty$ and $ E \lvert\eta\rvert^q <\infty$, $1\leq p <\infty $, then we have $ E \lvert\xi+\eta \rvert^p <\infty$ and

$$\left(E \lvert\xi+\eta\rvert^p\right)^{\frac{1}{p}}\leq E \left(\lvert \xi\rvert^p
\right)^{\frac{1}{p}} E \left(\lvert \eta\rvert^p
\right)^{\frac{1}{p}} $$

{% endalert %}

**Proof: **

To Prove Minkowski's Inequality, at first we have $(a+b)^p \leq 2^{p-1}(a^p+b^p)$, then we obtain $E\lvert \xi+\eta\rvert^p\leq \infty$. 

- If $p=1$, it is obvious.
- Let $p>1$, then $\lvert \xi+\eta\rvert^p = \lvert \xi+\eta\rvert\cdot \lvert \xi+\eta\rvert^{p-1}\leq \lvert \xi\rvert\cdot \lvert \xi+\eta\rvert^{p-1}+\lvert \eta\rvert \cdot \lvert \xi+\eta\rvert^{p-1}$. The only thing we need to do is applying Holder's Inequality to both $\lvert \xi\rvert\cdot \lvert \xi+\eta\rvert^{p-1}$ and $\lvert \eta\rvert \cdot \lvert \xi+\eta\rvert^{p-1}$, finally we could get Minkowski's Inequality.

