
> [!example] Grothendieck
> 对于概率测度空间 $(\Omega,\mathcal F,\mu)$, $p\in(1,\infty)$, 若 $L(\mu)$ 的线性子空间 $S$ 满足
> - $S\in\operatorname{Closed}(L^p(\mu))$
> - $S\subset L^\infty(\mu)$
> 
> 则 $S$ 为有限维的.

`BEGINPROOF`
将 $S$ 赋予 $L^p$ 的子空间拓扑并嵌入 $j:S\to L^\infty$ (这也是上述两个条件的用处), 在 $S$ 中取
$$f_n\xrightarrow{L^p}f,\qquad f_n\xrightarrow{L^\infty}g$$
则 $f\xlongequal{\text{a.e.}}g$, 因为
$$\|f-g\|_p\leq \|f-f_n\|_p+\|f_n-g\|_p\leq \|f-f_n\|_p+\|f_n-g\|_\infty\to 0$$
从而 $j$ 的图像是闭的, 则 $\|j\|_{\mathcal B(S\to L^\infty)}<\infty$, 既存在 $K>0$ 满足
$$\|f\|_{\infty}\leq K\|f\|_p\qquad f\in S$$
若 $p\leq 2$, 则 $\alpha\mapsto \alpha^{\frac2p}$ 为凸函数, 由 Jensen 不等式 $\|f\|_p\leq \|f\|_2$ 从而 $\|f\|_\infty\leq K\|f\|_2$

若 $p>2$, 则由于 $|f|^p\leq \|f\|_{\infty}^{p-2}|f|^2$ 两边积分有 $\|f\|_p\leq K^{\frac {p-2}2}\|f\|_2$, 总之存在 $M>0$ 满足
$$\|f\|_\infty\leq M\|f\|_2\qquad f\in S$$
既嵌入 $L^2\to L^\infty$ 是连续的.
将 $S$ 赋予 $L^2$ 中的内积并取出其中的 $n$ 个单位正交元素 $\varphi_1,\cdots,\varphi_n$, $B:=\partial B(0_{\mathbb C^n},1)$, 以及
$$\begin{align}
\psi:B&\to S\\
c&\mapsto \sum_{j=1}^nc_j\varphi_j
\end{align}$$
则 $\|\varphi(c)\|_2\leq \|c\|_{\mathbb C^n}=1$, 从而 
$$\|\varphi(c)\|_\infty\leq M$$
则对任意 $c\in B$, 存在 $\Omega'_c\subset \Omega: \mu(\Omega')=1,\forall_{x\in\Omega},|\psi(c)(x)| \leq M$ 现在固定一点, 取 $B$ 的一个可列稠密子集 $Q$, 则
$$\exists\Omega'\subset\Omega:\mu(\Omega')=1,\forall_{c\in Q},\forall_{x\in\Omega'},|\psi(c)(x)|\leq M$$
并且对固定的 $x\in \Omega'$, $B\ni c\mapsto |\psi(c)(x)|$ 是连续的, 这说明
$$\forall_{c\in B},\forall_{x\in\Omega'},|\psi (c)(x)|\leq M$$
从而
$$\forall_{x\in\Omega},\sum_j|\varphi_j(x)|^2\leq M^2\Rightarrow n=\left\|\sum_{j=1}^n\varphi_j(x)\right\|_2^2\leq M^2\Rightarrow \dim (S)\leq M^2$$
`ENDPROOF`
