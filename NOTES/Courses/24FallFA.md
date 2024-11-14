Cpt1 度量空间
1. 压缩映射原理 / Banach 不动点定理
2. 完备化: 稠密性与完备性, 完备化空间的存在
3. 列紧和自列紧, 列紧与完备, 有穷 $\varepsilon$-网和完全有界, Hausdorff, 可分, 紧, 度量空间紧等价于自列紧, AA定理
4. 赋范线性空间, 有限维上的范数等价, 最佳逼近问题, 单位球列紧等价于有穷维等价于任一有界集列紧 - Riesz 引理, 商空间
5. 凸集与不动点, Brouwer 与 Schauder
6. 内积空间, Poincare 不等式, Parseval 等式, 最佳逼近问题



> [!thm] Ascoli-Arzela
> $F\subset C(M)$
> $$列紧\iff 一致有界 \wedge 等度连续$$

`BEGINPROOF`
考虑空间
$$C(M),d(f_{1},f_{2})=\sup_{x}|f_{1}(x)-f_{2}(x)|$$
这一空间完备, 从而其上的列紧等价于完全有界 (Hausdorff 定理)
列紧 $\implies$ 一致有界: 反证显然
列紧 $\implies$ 等度连续: 由完全有界容易说明

一致有界且等度连续 $\implies$ 列紧: 目标是找有穷的 $\varepsilon$-网
首先找 $M$ 上的有穷 $\delta(\varepsilon)$ 网 $N=\{x_{1},\cdots,x_{n}\}$, 考虑映射 $T:\varphi\mapsto(\varphi(x_{1}),\cdots,\varphi(x_{n}))\in \mathbb R^n$, 则由一致有界, $T(F)$ 为 $\mathbb R^n$ 上的有界集, 从而是列紧集.
取其有穷 $\varepsilon$-网 $\tilde{N}(\varepsilon)=\{T\varphi_{1},T\varphi_{2},\cdots,T\varphi_{m}\}$, 则 $\{\varphi_{1},..,\varphi_{m}\}$ 为 $F$ 的 $\varepsilon$ 网

`ENDPROOF`

> [!lem] Riesz 引理
> NLS $X$ 任一真闭子空间 $X_{0}$
> $$\forall_{0}<\varepsilon<1,\exists y\in X,\|y\|=1, \forall x\in X_{0}, \|y-x\|\geq1-\varepsilon $$

> [!thm] Schauder
> 设 $C$ 是 NLS 空间 $X$ 中的一个闭凸子集, $T:C\to C$ 连续且 $T(C)$ 列紧, 则 $T$ 在 $C$ 上必有一个不动点

`BEGINPROOF`
取 $T(C)$ 的一 $\frac{1}{n}$-网 $N_{n}=\{y_{1},\cdots,y_{n}\}$, 构造映射 $I_{n}:T(C)\to \operatorname{co}N_{n}$, 满足 $\|I_{n}y-y\|< \frac{1}{n}$, 而映射 $I_{n}T|_{\operatorname{co}N_{n}}$ 为一有限维上闭凸子集的连续映射, 其必有不动点 $x_{n}$, 又因为 $T(C)$ 是列紧集而 $C$ 是闭集, 可以取子列 $Tx_{n'}\to x$, 再证明 $x_{n'}\to x$, 由 $T$ 的连续性立得 $Tx=x$
`ENDPROOF`
> [!lem] Poincare ineq
> $\forall u\in C_{0}^m(\Omega)$: $\Omega$ 有界开区间, 在 $\partial\Omega$ 的某邻域内为 $0$
> $$\sum_{|\alpha<m|}\int_{\Omega}|\partial^\alpha u(x)|^2\mathrm{d}x{\underset{\sim}{<}}_{\Omega,m}\sum_{|\alpha|=m}\int_{\Omega}|\partial^\alpha u(x)|^2\mathrm{d}x$$

