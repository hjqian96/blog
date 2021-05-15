---
abbrlink: '0'
---
Numerical Scheme for Stochastic Differential Equations

This post will mainly introduce some numerical scheme to approximate solutions of stochastic differential equations and correspoding auxiluary results for each numerical scheme.



#### Truncated EM scheme

Let' s consider the following stochastic differential equations
$$
\begin{align*}
\begin{cases}
dX(t)=f(X(t))dt+g(X(t))d\, B(t)\\
X(0)=x_0
\end{cases}
\end{align*}
$$
where $f :\mathbb{R}^d\rightarrow \mathbb{R}^d$ and $g: \mathbb{R}^d\rightarrow \mathbb{R}^{d\times m}$. we impose two hypothese to above SDE.

**Assumptions:**

1. $ f,g$ satisfy *local Lipschitz condition*, that is for any $R>0$, there exists $K_R>0$ s.t. $|f(x)-f(y)|\vee |g(x)-g(y)| \leq K_R |x-y|$.
2. Coefficients satisfy Khaminskii-Type condition: $\exists \,p>2$ and $K>0$ such that $x^{T}f(x)+\frac{p-1}{2}|g(x)|^2 \leq K(1+|x|^2)$.

