> [!exercise] cpt 2 exe 1
> 对任意的 $\{X_n\}$, 若 $\sum_n \mathbb E[|X_n|]<\infty$ 则 $\sum_n X_n$ a.s. 收敛

经典用期望限制整体, 那自然想到 Chebyshelf, 我们通过 Cauchy 列绕一下
$$
\forall \delta>0,\mathbb P \left[ \left|\sum_{i=m}^n X_{i}\right|>\delta \right]\leq \frac{1}{\delta} \mathbb{E}\left[ \sum_{i=m}^n |X_{i}| \right]= \frac{\sum_{i=m}^n\mathbb{E}[|X_{i}|]}{\delta}\to0\qquad \text{as }m,n\to \infty
$$

