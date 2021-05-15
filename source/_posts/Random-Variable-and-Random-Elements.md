---
title: Random Variable and Random Elements
mathjax: true
categories: Probability
tags:
  - Random Variable
  - Random Elements
abbrlink: 5abe79c7
date: 2019-08-13 21:07:29
---

<center>Part I Random variables</center>
***
{% alert info %}
<b> Definition 1:  </b> <br>
A real function $\xi=\xi(w): (\Omega,\mathscr{F}) \mapsto (\mathbb{R},\mathscr{B}(\mathbb{R}))$ is an $\mathscr{F}$-measurable function or <strong>random variable </strong> if for every $B\in \mathscr{B}(\mathbb{R})$, we have
$$\{w: \xi(w)\in B\} =\xi^{-1}(B) \in \mathscr{F} \tag{1}$$.
{% endalert %}

{% alert info %}
<b> Definition 2: </b> <br>
A probability measure $P_{\xi}$ on $(\mathbb{R},\mathscr{B}(\mathbb{R})$ with
$$
P_{\xi}(B)=P\{w: \xi(w)\in B\},\quad B\in \mathscr{B}(\mathbb{R})
$$
is called the <em>probability distribution</em> of $\xi$ on $(\mathbb{R},\mathscr{B}(\mathbb{R}))$.
{% endalert %}

{% alert info %}
<b> Definition 3: </b> <br>
    The function $$F_{\xi}(x)=P\{w: \xi(w)\leq x\}, \quad x\in \mathbb{R}$$
    is called the <em>distribution fucntion </em> of $\xi$.
{% endalert %}

<!--more-->
To estabilish that $\xi(w)$ is a random variable, we have to verify property $(1)$ for every $B\in\mathscr{B}(\mathbb{R})$. The following lemma shows that the class of such "test" sets can be narrowed.

{% alert info %}

<b> Lemma 1 </b> 
Let $\mathscr{E}$ be a system of sets such that $\sigma(\mathscr{E})=\mathscr{B}(\mathbb{R})$. Then $\xi=\xi(w)$ is $\mathscr{F}$-mesaurable $\Leftrightarrow $ $\{w:\xi(w)\in E\} \in \mathscr{F}$ for all $E\in \mathscr{E}$.
{% endalert %}


Proof:<br/>

- The necessity("$\Rightarrow$") is obvious;
- For the sufficient part, we will use <strong>the principle of appropriate sets</strong> (the appropriate sets are sets satisfying the property we would like to prove).
Let $\mathscr{D}=\{D: D\in \mathscr{B}(\mathbb{R}) \text{ satisfying } \xi^{-1}(D)\in \mathscr{F}\}$. we could easily show that the operation "form the inverse image" preserve the set theoretic  operations of union, intersection and complement: i.e.
$$
\begin{align*}
\xi^{-1}\bigl(\bigcup_{\alpha}B_{\alpha}\bigr) &=\bigcup_{\alpha} \xi^{-1}(B_{\alpha}) \\
\xi^{-1}\bigl(\bigcap_{\alpha}B_{\alpha}\bigr) &=\bigcap_{\alpha} \xi^{-1}(B_{\alpha})\\
\overline{\xi^{-1}(B_{\alpha})} &= \xi^{-1}(\overline{B_{\alpha}})
\end{align*}
$$

Therefore it follows that $\mathscr{D}$ is a $\sigma$-algebra. Then we have
$$
\mathscr{E}\subseteq \mathscr{D} \subseteq \mathscr{B}(\mathbb{R})
$$

and 
$$
\sigma(\mathscr{E}) \subseteq \sigma(\mathscr{D})=\mathscr{D} \subseteq \mathscr{B}(\mathbb{R})
$$

Therefore we have $\mathscr{D}=\mathscr{B(\mathbb{R})}$, so this lemma is proved.

According to the preceding lemma, we would get the following corollary since $\sigma(E1)=\sigma(E2)=\mathscr{B}(\mathbb{R})$ where $E1=\{x:x<c, c\in \mathbb{R}\}, E2=\{x:x\leq c, c\in \mathbb{R}\}$

{% alert info %}
<b> Corollory </b> <br>
    $\xi =\xi(w)$ is a random variable $\Leftrightarrow$ $\{w:\xi(w)< x \} \in \mathscr{F}$ or $ \{w:\xi(w)\leq x \} \in \mathscr{F}$ for every $x \in \mathbb{R}$.

{% endalert %}

Now, we know what's random variable. The next thing we are going to do is to testifty wether a random variable under some operations still be random variable.<br>

{% alert info %}

<b> Lemma 2 </b> <br>
    Let $\varphi=\varphi(x)$ be a Borel function and $\xi$ be a random variable, then
    $\eta(w)=\varphi(\xi(w))$ is also a random variable.
{% endalert %}


Proof:<br/>

For any $B\in\mathscr{B}(\mathbb{R})$,
$$
\{w:\eta(w)\in B\} =\{w:\varphi(\xi(w))\in B\}=\{w: \xi(w)\in\varphi^{-1}(B)\} \in\mathscr{F}
$$
since $\varphi$ is Borel function, so $\varphi^{-1}(B)\in\mathscr{B}(\mathbb{R})$.

If $\xi$ is a random variable, so are $\xi^{n}, \xi^{+}, \xi^{-}, \lvert\xi\rvert$. If $\{\xi_k\}$ is a collection of random variables, so are $\sum_{k=1}^{\infty} \lvert \xi_k\rvert, \varlimsup\xi_k,\varliminf \xi_k$.

The next theorem is vital important, it shows that we can approximate any random variable by simple random variables. This is the fundation to construct Lebesgue integral.<br/>

{% alert info %}
<b> Theorem 1 </b> <br/>
    (a) For every random variable $\xi=\xi(w)$ (extended ones included i.e. $\xi\in [-\infty,+\infty]$), there exists a sequence of random variables $\{\xi_n\}$ s.t. $\lvert\xi_n\rvert \leq \lvert\xi\rvert$ and $\xi_n(w)\rightarrow\xi(w), n\rightarrow\infty$ for all $w\in \Omega$.<br/>
    (b) If for a nonnegative random variable $\xi(w)\geq 0$, there exists a sequence of random variables $\{\xi_n\}$ s.t. $\xi_n(w)\uparrow \xi(w)$.

{% endalert %}


Proof:

(b) For $n=1,2,\cdots$, Let
$$
\xi_n(w)=\sum_{k=1}^{n2^{n}} \frac{k-1}{2^n} I_{k,n}(w) +nI_{\xi(w)\geq n}(w)
$$
where $I_{k,n}(w)=I_{(k-1)/2^n\leq \xi(w)\leq k/2^n}$.<br/>
The so have $\xi_n(w)\uparrow \xi(w)$.<br/>
For the general case in (a), since $\xi=\xi^{+}-\xi^{-}$, we could use simple random variables to approximate $\xi^{+}, \xi^{-}$ resepctively. Finally, we could use simple random variables to approxiamte $\xi$.

<center>Part II Random variables</center>
***

Before we preceed to random elements, we consider set $\{w:\xi(w)\in B\}$ for all $B\in \mathscr{B}(\mathbb{R})$. We could verify that such sets could form a $\sigma$-algebra called <strong>$\sigma$-algebra generated by $\xi$</strong> denoted by $\mathscr{F}_{\xi}$.

In the previous Lemma 2, we show that $\varphi(\xi(w))$ is a random variable if $\varphi(x)$ is a Borel function. Now, we are able to say that the converse is true for $\mathscr{F}_{\xi}$ random variable.<br/>

{% alert info %}

<b> Theorem 2 </b> <br>
   Let $\eta$ be a $\mathscr{F}_{\xi}$ random variable. Then there exists a Borel function $\varphi(x)$ s.t. $\eta=\varphi(\xi(w))$ for every $w\in \Omega$.
{% endalert %}


**Proof**:

Let $\Phi^{\xi}=\{\eta(w):\eta \text{ is } \mathscr{F}_{\xi}\text{-measurable}\}$ and $\tilde{\Phi}_{\xi} =\{\eta(w): \eta \text{ is }\mathscr{F}_{\xi}\text{-measurable and } \eta=\varphi(\xi(w)), \text{ where }\varphi \text{ is a Borel function } \}$, i.e. the class of $\mathscr{F}_{\xi}$-measurable functions represened in the form of $\varphi(\xi)$ where $\varphi$ is a Borel function. Therefore, $\tilde{\Phi}_{\xi} \subseteq \Phi^{\xi}$. Hence it's sufficient to prove that $\Phi^{\xi} \subseteq \tilde{\Phi}_{\xi}$.

**Step 1**: The first step is to prove that the indicator funtion $I_{A}(w) \in \Phi^{\xi}$ for every $A \in \mathscr{F}_{\xi}$. so we let $A\in \mathscr{F}_{\xi}$ and $\eta=I_{A}(w)$, then if $A\in \mathscr{F}_{\xi}$, there exist a $B\in \mathscr{B}(\mathbb{R})$ such that $A=\{w:\xi(w)\in B\}$. So <br/>
we let 
$$
\chi_B(x)=
\begin{cases}
1, \quad x\in B \\
0, \quad x\notin B
\end{cases}
$$
Then we know that $I_{A(w)}=\chi_B(\xi(w))\in \tilde{\Phi}_{\xi}$.

**Step 2**: according to Step 1, we know that the indicator function is in $\tilde{\Phi}_{\xi}$ for every $A\in \mathscr{F}_{\xi}$. So the simple $\mathscr{F}_{\xi}$-measurable function $\sum_{k=1}^{n} c_k I_{A_k}(w), A_k \in\mathscr{F}_{\xi}$ belongs to $\tilde{\Phi}_{\xi}$.

**Step 3**: For any arbitrary $\mathscr{F}_{\xi}$ function $\eta$, accordin to Theorem 1, there exists a sequence of simple $\mathscr{F}_{\xi}$-measurable function $\{\eta_n\}$ s.t. $\eta_n \rightarrow\eta(w)$. From Step 2, for each $\eta_n$, there exists Borel function $\varphi_n=\varphi_n(x)$ s.t. $\eta_n(w)=\varphi_n(\xi(w))$. Therefore $\varphi_n(\xi(w))\rightarrow \eta(w)$ as $n\rightarrow \infty, w\in \Omega$. Let $E=\{x\in \mathbb{R}: \lim_n\varphi_n(x) \text{ exists }\}$. It is a Borel set and the function below
$$
\varphi(x)=
\begin{cases}
  lim_n \varphi_n(x), \quad x\in B\\
  0, \quad x\notin B
\end{cases}
$$
is a Borel function. Then $\eta(w)=\lim_n\varphi_n(\xi(w))=\varphi(\xi(w))$ for all $w\in \Omega$.

Consequently, $\tilde{\Phi}_{\xi}=\Phi^{\xi}$.

<center> Part III Random Elements</center>
***
{% alert info %}
<b> Definition 4: </b> <br>
  Let $(\Omega,\mathscr{F}), (E,\mathscr{E})$ be mesurable space. We say that $X=X(w):(\Omega,\mathscr{F})\rightarrow(E,\mathscr{E})$ is $\mathscr{F}/\mathscr{E}$-measurable function or is a <strong>random element</strong>( with values in E), if $\{w:X(w)\in B\}\in \mathscr{F}$, for every $B\in\mathscr{E}$.

{% endalert %}


If $(E,\mathscr{E})=(\mathbb{R},\mathscr{B}(\mathbb{R}))$, then the definition of a random element is the same as the definition of a random variable. We could see that random element is more general since $(E,\mathscr{E})$ is any measurable space.

If $(E,\mathscr{E})=(\mathbb{R}^n,\mathscr{B}(\mathbb{R}^n))$. Then we call the random element $X(w)$ is a "random point" in $\mathbb{R}^n$. If $\pi_k$ is the projection of $\mathbb{R}^n$ on the $k$-th coordinate axis, then $X(w)$ has the representation $X(w)=(\xi_1(w),\xi_2(w),\cdots,\xi_n(w))$ where $\xi_k=\pi_k(X(w))$. That is a random element in $\mathbb{R}^n$ is an n-dimenional random vector( i.e. an ordered set of random variables). In fact, we could show that the converse is also true: every random vector $X(w)=(\xi_1(w),\xi_2(w),\cdots,\xi_n(w))$ is a random element in $\mathbb{R}^n$. Since for every $B\in \mathscr{\mathbb{R}^n}=\underbrace{\mathscr{B}(\mathbb{R})\otimes \cdots \otimes \mathscr{B}(\mathbb{R})}_{n}$, so there exists $B_k\in \mathscr{B}(\mathbb{R}), k=1,2,\cdots,n$ and according the definition of random element, we have
$$
\{w: X(w)\in(B_1\times B_2\cdots B_n)\}=\prod_{k=1}^{n}\{w:\xi_k(w)\in B_k\}\in \mathscr{F}
$$





 













