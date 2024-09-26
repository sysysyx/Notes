> [!exercise]

`BEGINPROOF`
$$\begin{align}
&x_{1},x_{2}\in\{x:f(x)<c\}\implies f(x_{1}),f(x_{2})<c \\
&\implies\forall\varepsilon\in[0,1],f(\varepsilon x_{1}+(1-\varepsilon)x_{2})<\varepsilon f(x_{1})+(1-\varepsilon)f(x_{2})<c \\
&\implies\forall\varepsilon\in[0,1],\varepsilon x_{1}+(1-\varepsilon)x_{2}\in\{x:f(x)<c\}
\end{align}$$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
显然 $P\subset Q$ 都是 $\mathbb R$ 上的线性空间, 且 $\dim P=\dim Q=n-k$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
设点 $x$ 不是顶点, 则不存在 $c\in\mathbb R^n$ 使得 $c^T x<c^Ty,\forall y\in P,y\neq x$, 这就是说它不能是任意线性不等式约束的取等点
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
![[hw1-20240926191638068.webp]]
极点:
$$(0,0),\quad (0,2),\quad (8,0),\quad (4,2)$$
这些点同时都是基解, 同时还有 $(0,4)$
`ENDPROOF`

> [!exercise]

- 至少存在一个极点是最优点
- 若两个极点都是最优点, 其所有线性组合都是最优点

> [!exercise]

(1) 真
$$\dim\{x:Ax=b\}=1$$
由可行集是凸集, 一条直线上至多有两个基本可行解
(2)(3) 假, 反例:
$$P=\{x:x>0,x_{1}=1\}$$
目标函数 $f(x)=x_{1}$
(4) 真, 对线性优化问题, 最优解的线性组合也是最优解

> [!exercise]

`BEGINPROOF`
可行方向
$$\theta(1,0,-1)+(1-\theta)(0,1,-1)\quad \theta\in[0,1]$$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
![[hw1-20240926200154167.webp]]
最优点 $(4,2)$, 此处 $-4x_1-x_2=-18$
`ENDPROOF`

> [!exercise]

(a)
$$\begin{align}
L(x,\mu)&=c^Tx-\mu^T(Ax-b),\qquad \mu\geq0 \\
g(\mu)&=\min_{x}L(x,\mu)=\min_{x}(c-A^T\mu)^Tx+\mu^Tb=\begin{cases}
\mu^Tb &A^T\mu=c \\
-\infty& else
\end{cases}
\end{align}$$
从而对偶问题
$$\begin{align}
\max & \quad \mu^Tb \\
\text{s.t.} & \quad A^T\mu=c
\end{align}$$
(b)
$$\begin{align}
L(x,\mu)&=c^Tx+\mu^T(Ax-b),\qquad \mu\geq0 \\
g(\mu)&=\min_{x}L(x,\mu)=\min_{x}(c+A^T\mu)^Tx-\mu^Tb=\begin{cases}
-\mu^Tb &A^T\mu+c=0 \\
-\infty& else
\end{cases}
\end{align}$$
从而对偶问题
$$\begin{align}
\max & \quad -\mu^Tb \\
\text{s.t.} & \quad A^T\mu=-c
\end{align}$$
(c) DP  问题
$$\begin{align}
\max&\quad b^T\lambda \\
\text{s.t.}&\quad A^T\lambda\leq c
\end{align}$$
的对偶由 (a), (b) 给出, 为一 (LP) 问题