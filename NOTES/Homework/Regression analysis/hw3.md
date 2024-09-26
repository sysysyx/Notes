> [!exercise]

(a)
$$\begin{align}
\mathbb E(a^Tx)&=\int a^Tx\mathrm{d}\omega=a^T\int x\mathrm{d}@w=a\mu \\
\operatorname{var}(a^Tx)&=\int (a^Tx-a^T\mu)(a^Tx-a^T\mu)^T\mathrm{d}\omega=a^T\Sigma a
\end{align}$$

(b)
$$\begin{align}
\operatorname{cov}(a^Tx,b^Tx)&=\int (a^Tx-a^T\bar{x})(b^Tx-b^T\bar{x})^T\mathrm{d}x=a^T\Sigma b \\
\rho(a^Tx,b^Tx)&=\frac{\operatorname{cov}(a^Tx,b^Tx)}{\sigma_{a^Tx}\sigma_{b^Tx}}=\frac{a^T\Sigma b}{\sqrt{ a^T\Sigma ab^T\Sigma b }}
\end{align}$$

(c)
$$\mathbb E\|x\|^2=\int x^T x\mathrm{d}\omega=\sum\mathbb E[x_{i}^2]=\sum\operatorname{var}(x_{i})+\mathbb E[x_{i}]^3=tr\Sigma+\|\mu\|^2$$

> [!exercise]

`BEGINPROOF`
$$\begin{align}
\Sigma_{a^\perp b^\perp}&=\int(a-\Sigma_{az}\Sigma_{zz}^{-1} z-\bar{a}+\Sigma_{az}\Sigma_{zz}^{-1} \bar{z})(b-\Sigma_{bz}\Sigma_{zz}^{-1} z-\bar{b}+\Sigma_{bz}\Sigma_{zz}^{-1} \bar{z} \\
&=\Sigma_{ab}-\Sigma_{az}\Sigma_{zz}^{-1}\Sigma_{zb}=\Sigma_{ab\circ z}
\end{align}$$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
$$\begin{align}
R^2&=\phi_{y\sim(x,z)}= \frac{\Sigma_{y(x,z)}\Sigma_{(x,z)(x,z)}^{-1}\Sigma_{(x,z)y}}{\Sigma_{yy}} \\
&=\frac{\begin{pmatrix}
\sigma_{yx}&\sigma_{yz}
\end{pmatrix}\begin{pmatrix}
\sigma_{xx}&\sigma_{xz} \\
\sigma_{zx}&\sigma_{zz}
\end{pmatrix}^{-1}\begin{pmatrix}
\sigma_{xy}\\
\sigma_{zy}
\end{pmatrix}}{\sigma_{yy}} >0
\end{align}$$
$$\Sigma_{yy\circ(x,z)}=\sigma_{yy}-\Sigma_{y(x,z)}\Sigma_{(x,z)(x,z)}^{-1}\Sigma_{(x,z)y}\geq0\implies R^2<1$$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
(a)
$$\begin{pmatrix}
\sigma^2+\varepsilon_{1}^2&\sigma^2&\sigma^2 \\
\sigma^2& \sigma^2+\varepsilon_{2}^2&\sigma^2\\
\sigma^2&\sigma^2&\sigma^2
\end{pmatrix}$$

$$\begin{align}
R^2&=\frac{\begin{pmatrix}
\sigma^2&\sigma^2
\end{pmatrix}\begin{pmatrix}
\sigma^2+\varepsilon_{1}^2&\sigma^2 \\
\sigma^2&\sigma^2
\end{pmatrix}^{-1}\begin{pmatrix}
\sigma^2 \\
\sigma^2
\end{pmatrix}}{\sigma^2+\varepsilon_{2}^2} \\
&=\frac{\begin{pmatrix}
\sigma^2&\sigma^2
\end{pmatrix}\begin{pmatrix}
\sigma^2&\sigma^2 \\
\sigma^2&\sigma^2+\varepsilon_{1}^2
\end{pmatrix}\begin{pmatrix}
\sigma^2 \\
\sigma^2
\end{pmatrix}}{(\sigma^2+\varepsilon_{2}^2)\sigma^2\varepsilon_{1}^2} \\
&=\frac{4\sigma^4+\sigma^2\varepsilon_{1}^2}{(\sigma^2+\varepsilon_{2}^2)\varepsilon_{1}^2}
\end{align}$$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
上次作业已经证明 $\sigma_{a^Tx}=a^T\Sigma_{x}a$ 从而第一个式子显然, 第二个式子当且仅当 $a$ 与 $x$ 同向时取等, 其它情况必然更小
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
假定 $A_{11}$ 为 $n_{1}$ 阶方阵, $A_{22}$ 为 $n_2$ 阶方阵, 分别带入
$$x=(x_{1},\cdots,x_{n_{1}},0,\cdots,0);\qquad x=(0,\cdots,0,x_{n_{1}+1},\cdots,x_{n_{1}+n_{2}})$$
由正定 $x^TAx>0$, $\forall x_{1},\cdots,x_{n}$, 从而 $A_{11}$, $A_{22}$ 正定, 且
$$A^{-1}=\begin{pmatrix}
A_{11}-A_{21}A_{12}^{-1}A_{21}&\cdots \\
\cdots&\cdots
\end{pmatrix}$$
正定, 从而 $A_{11}-A_{21}A_{12}^{-1}A_{21}$ 正定
`ENDPROOF`