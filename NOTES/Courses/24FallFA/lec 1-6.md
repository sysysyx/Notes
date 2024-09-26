设 $X$ 为列紧度量空间, $C(X)$ 为 $X$ 上的连续函数, 称集合 $C(X)$ 的一个子集 $F$ 为
- 一致有界的, 当且仅当存在一个常数 $C$ 使得 $\forall f\in F$, $\max_{x\in X}f(x)<C$
- 等度连续的, $\forall \delta>0,\exists\varepsilon>0:\forall d(x,y)<\epsilon,f\in F,|f(x)-f(y)|<\delta$

> [!thm] Ascoli-Arzela thm
> 列紧度量空间 $X$ 上 $F\subset C(X)$
> $$列紧\iff 一致有界且等度连续$$

`BEGINPROOF`
**必要性**:
(a) 一致有界
$$列紧\implies\exists C>0,\forall f\in F,d(f,0)=\sup|f(x)|<C\iff 一致有界$$
(b) 等度连续: 借助 $\varepsilon$ 网有限化
$$\begin{align}
列紧&\implies \forall\varepsilon>0,\exists有穷\varepsilon网\{f_{1},\cdots,f_{n}\}\subset F:\forall f\in F,\exists i:d(f,f_{i})<\varepsilon \\
\end{align}$$
我们知道列紧度量空间上的连续函数一致连续
$$f_{i}\ 一致连续\xRightarrow{\delta=\min_{i}\{\delta_{i}\}}f_{i}\ 等度连续$$
稍加控制显然
**充分性**: 由等度连续
$$\forall\varepsilon>0,\exists\delta>0,\forall f\in F,d(x,y)<\delta,|f(x)-f(y)|<\varepsilon$$
因此我们想到利用 $X$ 的列紧性, 找到有限 $\delta$-网 $\{x_1,\cdots,x_{n}\}$
而在这些点上有自然映射
$$\begin{align}
\varphi:F&\to\mathbb R^n \\
f&\mapsto (f(x_{1}),\cdots,f(x_{n}))
\end{align}$$
由 $F$ 一致有界, 其像必然也一致有界, 此时由 $\mathbb R^n$ 中的有界集是列紧集, 从而存在 $\mathbb R^n$ 中的一个有穷 $\varepsilon$-网, 通过经典手法将其转化到 $\varphi(F)$ 上, 假设为 $$(\varphi(f_{1}),\cdots,\varphi(f_{k}))$$
往证 $(f_i)$ 为 $F$ 上的网:
$$\begin{align}
&\forall x\in X,\exists x_{i}:d(x,x_{i})<\delta \implies \forall f,|f(x)-f(x_{i})|<\varepsilon \\
&\exists f_{j}:|\varphi (f)-\varphi(f_{j})|<\varepsilon
\end{align}$$
综上
$$|f(x)-f_{j}(x)|\leq |f(x)-f(x_{i})|+|f(x_{i})-f_{j}(x_{i})|+|f_{j}(x_{i})-f_{j}(x)|\leq 3\varepsilon $$
`ENDPROOF`

设 $\Omega$ 为 $\mathbb R^n$ 上的有界开凸集 (比如开球或者 $[0,1]^n$), 定义
$$C^k(\overline \Omega):=\{f:\Omega\to\mathbb R\mid  f\ 可以延拓到\  \overline\Omega\  上且其\ i\leq k\ 阶微分也可以连续延拓到边界\}$$
定义其上的范数
$$\|f\|_{C^k}=\sum_{|I|<k} \sup_{x\in\overline\Omega}\frac{\partial^{|I|}f}{\partial x^I}(x)$$
