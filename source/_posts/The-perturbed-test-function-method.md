---
title: The perturbed test function method
mathjax: true
categories:
  - Weak Convergence
tags:
  - perturbed test function method
  - weak convergence
comments: true
abbrlink: aeb99872
date: 2020-04-30 15:12:31
---

This post mainly demonstrate how to construct the perturbed test function that the theorems in previous post will make use of. For simplicity, here we suppose the limit of $x^{\varepsilon}$ satisfy an ODE limit and the noise term $\xi^{\varepsilon}(u)$ is independent on $x^{\varepsilon}$ (state independent case). Later on, if time permits, diffusion limit and state dependent case will be posted and I will put an link for reference.

<!--more-->

we mention that state independent actually means for each $t$ and set $A \in \sigma\{\xi^{\varepsilon},u>t\}$,
$$
\begin{align}
    P\{A| \xi^{\varepsilon},u\leq t\}=P\{A|\xi^{\varepsilon},x^{\varepsilon},u\leq t\}
\end{align}
$$

The system model for this post is the following 

$$
\begin{align}
\dot{x^{\varepsilon}}=G(x^{\varepsilon},\xi^{\varepsilon}), \quad x\in \mathbb{R}^{r}
\end{align}
$$

What we would like to obtain is that $\{x^{\varepsilon}(\cdot)\}$ converge weakly to a limit $x(\cdot)$ satisfying an ODE limit
$$
\begin{align}
\dot{x}=\overline{G}(x)
\end{align}
$$

Since this post will use the tightness of $\{x^{\varepsilon}(\cdot)\}$ and we are not going to address such issue in this post, therefore we jsut make an assumption that $\{x^{\varepsilon}(\cdot)\}$ is tight. Last post shows that we need some convergence of conditional expectation. The following ones are some assumption we need.

- (A1) $G(\cdot,\cdot), G_{x}(\cdot,\cdot)$ are continuous in $(x,\xi)$ and are bounded on each bounded $x$-set.
- (A2) There is a continuously differentiable function $\overline{G}(x)$ such that for each $t<T$ and $x$
$$
\int_{t}^{T}[E_{t}^{\varepsilon}G(x,\xi^{\varepsilon}(u))-\overline{G}(x)]du \stackrel{P}{\rightarrow} 0
$$

{% alert info %}
<stong>Theorem 1</stong> <br>
Suppose $x^{\varepsilon}(0)\Rightarrow x_{0}$ and assumption $(A1)$ and $(A2)$ holds. Assume the solution to $\dot{x}=\overline{G}(x)$ with $x_{0}=x(0)$ is bounded for $t<\infty$.<br>
Then we have $\{x^{\varepsilon}(\cdot)\}$ is tight in $C^{r}[0,\infty)$ and $x^{\varepsilon}(\cdot)\Rightarrow x(\cdot)$, the unique solution of $\dot{x}=\overline{G}(x)$.
{% endalert %}

Proof: <br>

At first, we will assume that $G(\cdot,\cdot)$ is nonzero only on a compact set. Otherwise, we could use truncation techinque (refer Kushner [^1]).

Since $G(x^{\varepsilon},\xi^{\varepsilon})$ is bounded uniformly on each $[0,T]$, so is $\{\dot{x^{\varepsilon}}\}$, then we have $\{x^{\varepsilon}(\cdot)\}$ is tight in $C^{r}[0,\infty)$ (it might refer to Billingsley [^2]).

For $f(\cdot)\in \hat{C}^{2}_{0}$, apply the infinitesimal operator $\hat{A^{\varepsilon}}f(x^{\varepsilon}(\cdot))$

$$
\hat{A^{\varepsilon}}f(x^{\varepsilon}(t))=f'_{x}(x^{\varepsilon}(t))\dot{x^{\varepsilon}(t)}=f'_{x}(x^{\varepsilon}(t)) G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))
$$
Due to the noise term $\xi^{\varepsilon}(t)$ in $G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))$, $\hat{A^{\varepsilon}}f(x^{\varepsilon}(t))$ is not equal to $Af(\xi^{\varepsilon}(t))$. Therefore we need to average the noise by using perturbed test function method. To make it clear, we emphasize again that here we have
$$
\begin{align}
\hat{A^{\varepsilon}}f(x^{\varepsilon}(t))&=f'_{x}(x^{\varepsilon
}(t))G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))\\
& = f'_{x}(x^{\varepsilon}(t))\overline{G}(x^{\varepsilon})+f'_{x}(x^{\varepsilon})[G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))-\overline{G}(x^{\varepsilon}(t))]
\end{align}
$$

From above, we can see we have one more term $f'_{x}(x^{\varepsilon})[G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))-\overline{G}(x^{\varepsilon}(t))]$, hence by defining a perturbed test function, we are supposed to cancel this term. 

Define a perturbation
$$
f_{1}^{\varepsilon}(t)=f_{1}^{\varepsilon}(x^{\varepsilon}(t),t)=\int_{t}^{T}f'_{x}(x^{\varepsilon}(t))\left[E_{t}^{\varepsilon}G(x^{\varepsilon}(t),\xi^{\varepsilon}(u))-\overline{G}(x^{\varepsilon}(t))\right]du
$$
Then we take the perturbed test function as 
$$
\begin{align}
f^{\varepsilon}(t)& =f(x^{\varepsilon}(t))+f_{1}^{\varepsilon}(t) \\
& = f(x^{\varepsilon}(t))+f_{1}^{\varepsilon}(x^{\varepsilon}(t),t)\\
& = f(x^{\varepsilon}(t))+\int_{t}^{T}f'_{x}(x^{\varepsilon}(t))\left[E_{t}^{\varepsilon}G(x^{\varepsilon}(t),\xi^{\varepsilon}(u))-\overline{G}(x^{\varepsilon}(t))\right]du
\end{align}
$$

Then we will see next what is actually $\hat{A^{\varepsilon}}f^{\varepsilon}(t)=\hat{A^{\varepsilon}} f(x^{\varepsilon}(t))+\hat{A^{\varepsilon}} f_{1}^{\varepsilon}(t)$.

$$
\begin{align*}
\hat{A^{\varepsilon}} f_{1}^{\varepsilon} & =\hat{A^{\varepsilon}} f_{1}^{\varepsilon}(x^{\varepsilon}(t),t)= \hat{A^{\varepsilon}} \int_{t}^{T}f'_{x}(x^{\varepsilon}(t))\left[E_{t}^{\varepsilon}G(x^{\varepsilon}(t),\xi^{\varepsilon}(u))-\overline{G}(x^{\varepsilon}(t))\right]du \\
&= \hat{A^{\varepsilon}} \int_{t}^{T} E_{t}^{\varepsilon} \left[f'_{x}(x^{\varepsilon}(t))(G(x^{\varepsilon}(t),\xi^{\varepsilon}(y))-\overline{G}(x^{\varepsilon}(t)))\right]du
\end{align*}
$$

we denote $\widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u)):= f'_{x}(x^{\varepsilon}(t))(G(x^{\varepsilon}(t),\xi^{\varepsilon}(y))-\overline{G}(x^{\varepsilon}(t)))$, hence we have the following

$$
\begin{align*}
\hat{A^{\varepsilon}} f_{1}^{\varepsilon}(t) & =\hat{A^{\varepsilon}} \int_{t}^{T} E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))du \\
&= p-\lim_{\delta\rightarrow 0} \frac{\int_{t+\delta}^{T}E_{t}^{\varepsilon}\widetilde{G}(x^{\varepsilon}(t+\delta),\xi^{\varepsilon}(u))du -\int_{t}^{T}E_{t}^{\varepsilon}\widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))du }{\delta}
\end{align*}
$$

Now we will do some computation.

$$
\begin{align*}
& \frac{1}{\delta} \left[\int_{t+\delta}^{T}E_{t}^{\varepsilon}\widetilde{G}(x^{\varepsilon}(t+\delta),\xi^{\varepsilon}(u))du -\int_{t}^{T} E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))du \right] \\
&= - \frac{1}{\delta} \int_{t}^{t+\delta} E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))du +\frac{1}{\delta} \int_{t+\delta}^{T} E_{t}^{\varepsilon} \left[ \widetilde{G}(x^{\varepsilon}(t+\delta),\xi^{\varepsilon}(u))-\widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))\right]du\\
& \stackrel{\delta\rightarrow 0}{\rightarrow}\\
& -E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(t))+\int_{t}^{T} \left[E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))\right]'_{x} \dot{x}^{\varepsilon}(t) du
\end{align*}
$$

Therefore we have the following
$$
\begin{align}
\hat{A^{\varepsilon}} f^{\varepsilon}(t) 
& = \hat{A^{\varepsilon}} f(x^{\varepsilon}(t))+\hat{A^{\varepsilon}} f_{1}^{\varepsilon}(t) \\
& = f'_{x}(x^{\varepsilon}(t))\overline{G}(x^{\varepsilon}(t))+f'_{x}(x^{\varepsilon}(t))\left[G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))-\overline{G}(x^{\varepsilon}(t))\right] \\
& - f'_{x}(x^{\varepsilon}(t)) \left[G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))-\overline{G}(x^{\varepsilon}(t)) \right] +\int_{t}^{T} \left[E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))\right]'_{x} \dot{x}^{\varepsilon}(t) du \\
& = f'_{x}(x^{\varepsilon}(t))\overline{G}(x^{\varepsilon}(t))+\int_{t}^{T} \left[E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))\right]'_{x} G(x^{\varepsilon}(t),\xi^{\varepsilon}(t)) du
\end{align}
$$

As you could see in the above calculation, we did eliminate the term $f'_{x}(x^{\varepsilon}(t))\left[G(x^{\varepsilon}(t),\xi^{\varepsilon}(t))-\overline{G}(x^{\varepsilon}(t))\right]$.

Now, the final step is just to show some convergence results for $f_{1}^{\varepsilon}$ and $\hat{A^{\varepsilon}}f^{\varepsilon}(t)$.

- $f_{1}^{\varepsilon}(x^{\varepsilon}(t),t)=\int_{t}^{T}f'_{x}(x^{\varepsilon}(t))\left[E_{t}^{\varepsilon}G(x^{\varepsilon}(t),\xi^{\varepsilon}(u))-\overline{G}(x^{\varepsilon}(t))\right]du$

Then by condition $(A1), (A2)$ and the boundness of $\{x^{\varepsilon}(t);t\leq T\}$, we have
$$
\begin{align}
& \limsup_{\varepsilon\rightarrow 0, t<T} E|f_{1}^{\varepsilon}(x^{\varepsilon}(t),t)| \\
& \limsup_{\varepsilon\rightarrow 0, t<T} E|\int_{t}^{T}f'_{x}(x^{\varepsilon}(t))\left[E_{t}^{\varepsilon}G(x^{\varepsilon}(t),\xi^{\varepsilon}(u))-\overline{G}(x^{\varepsilon}(t))\right]du| \\
& =0
\end{align}
$$

- Prove $p-\lim \int_{t}^{T} \left[E_{t}^{\varepsilon} \widetilde{G}(x^{\varepsilon}(t),\xi^{\varepsilon}(u))\right]'_{x} G(x^{\varepsilon}(t),\xi^{\varepsilon}(t)) du=0$. The following are some calculations.

Let $e$ denote unit vector, $\widetilde{G}_{e}(\cdot)$ denote derivative in the direction $e$. Thus
$$
\begin{align*}
\int_{t}^{T} E_{t}^{\varepsilon} \widetilde{G}_{e}(x,\xi^{\varepsilon}(u))du  & =\int_{t}^{T} E_{t}^{\varepsilon} \widetilde{G}_{x}(x,\xi^{\varepsilon}(u))\cdot e du \\
& =\int_{t}^{T} E_{t}^{\varepsilon} \frac{\widetilde{G}(x,\xi^{\varepsilon}(u))-\widetilde{G}(x,\xi^{\varepsilon}(u))}{\delta}du \\
& - \int_{t}^{T} E_{t}^{\varepsilon} \frac{\widetilde{G}(x,\xi^{\varepsilon}(u))-\widetilde{G}(x,\xi^{\varepsilon}(u))}{\delta}du + \int_{t}^{T} E_{t}^{\varepsilon} \widetilde{G}_{x}(x,\xi^{\varepsilon}(u))\cdot e du \\
& =\int_{t}^{T} E_{t}^{\varepsilon} \frac{\widetilde{G}(x,\xi^{\varepsilon}(u))-\widetilde{G}(x,\xi^{\varepsilon}(u))}{\delta}du \\
& -\left[ \int_{t}^{T}E_{t}^{\varepsilon} \int_{0}^{1} e\cdot \widetilde{G}'_{x}(x+ve\delta,\xi^{\varepsilon}(u))dv du-\int_{t}^{T} E_{t}^{\varepsilon}\widetilde{G}_{x}(x,\xi^{\varepsilon}(u))\cdot e\right] \\
& =\int_{t}^{T} E_{t}^{\varepsilon} \frac{\widetilde{G}(x,\xi^{\varepsilon}(u))-\widetilde{G}(x,\xi^{\varepsilon}(u))}{\delta}du \\
& -\int_{t}^{T} du E_{t}^{\varepsilon} dv \left[\widetilde{G}'_{x}(x+ve\delta,\xi^{\varepsilon}(u))-\widetilde{G}'_{x}(x,\xi^{\varepsilon}(u))\right]e
\end{align*}
$$

During above calculation, we used
$$
\begin{align*}
\widetilde{G}(x+e\delta,\xi^{\varepsilon}(u))-\widetilde{G}(x,\xi^{\varepsilon}(u))&=e\delta \int_{0}^{1}\widetilde{G}'_{x}(x+ve\delta,\xi^{\varepsilon}(u))dv \\
\frac{d\widetilde{G}(x+ve\delta)}{dv}&=\widetilde{G}_{x}(x+ev\delta,\xi^{\varepsilon}(u))\cdot e\delta
\end{align*}
$$

- since $G_{x}(\cdot,\cdot)$ is continuous in $(x,\xi)$, then <br>
$\int_{t}^{T} du E_{t}^{\varepsilon} dv \left[\widetilde{G}'_{x}(x+ve\delta,\xi^{\varepsilon}(u))-\widetilde{G}'_{x}(x,\xi^{\varepsilon}(u))\right]e \rightarrow 0$ as $\delta\rightarrow 0$ uniformly in $\varepsilon$ and $e$ by $(A1)$.
- For any fixed $\delta>0$, $\int_{t}^{T} E_{t}^{\varepsilon} \frac{\widetilde{G}(x,\xi^{\varepsilon}(u))-\widetilde{G}(x,\xi^{\varepsilon}(u))}{\delta}du \stackrel{P}{\rightarrow }0$ as $\varepsilon\rightarrow 0$ due to $(A1), (A2)$ and $\widetilde{G}(x,\xi^{\varepsilon}(u))=f'_{x}(x)(G(x, \xi^{\varepsilon}(u))-\widetilde{G}(x))$

To conclude, we showed that $\hat{A^{\varepsilon}}f^{\varepsilon}(t)\rightarrow Af(x)=f'_{x}(x(t))\overline{G}(x(t))$.


[^1]: Kushner 1984
[^2]: Billingsley: Probability and measures