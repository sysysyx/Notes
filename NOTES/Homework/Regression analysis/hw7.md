> [!exercise]

^19300b

(a) (1) $\implies$ (2)
设 $P$ 为空间 $V$ 向平面 $X$ 投影的投影矩阵, 则 $P\mid_{X}=I$, 又 $P(V)=X$, 则 
$$P\circ P=I\circ P=P$$
即 $P$ 幂等, 由正交性, $\forall x\in V^\perp$, $Px=0$, 则 $P^*=P$, 于是 $P$ 对称

(2) $\implies$ (3)
幂等矩阵的特征值只能是 $0$ 或 $1$, 由对称性可知 $Q$ 正交

(3) $\implies$ (1) 取 $Q$ 代表的标准正交基显然

(b) 由 (a)(3) 可知 $rank(P)=r=tr(P)$

> [!exercise]

必要性显然, 考虑充分性 $Ax\in \mathrm{Im}(A)\cap \ker(A^*)=\{0\}$

> [!exercise]

$A$ 的列可以写为 $A_{j}=UDV_{j}$ 则 $C(A)\subset C(U)$, 由于二者都是 $r$ 维且建立在同一数域上, 必然相等. $UU^T$ 是对称幂等矩阵, 由 [[#^19300b]], 是正交投影矩阵, 其像空间为 $C(A)$

> [!exercise]

由于 $C$ 满秩, $rank(A)=\min\{rank(B),r\}=rank(B)$, $A$ 的列是 $B$ 的列的线性组合, 从而
$C(A)\subset C(B)$, 又二者维数相同, $C(A)=C(B)$

> [!exercise]

(a)
$$A_{1}^TA_{2}=0\implies A_{1}\perp A_{2}\implies P_{A}=P_{A_{1}\cup A_{2}}=P_{A_{1}}+P_{A_{2}}$$
(b)
$$A_{2}^\perp \perp A_{1},A=A_{1}\cup A_{2}=A_{1}\cup A_{2}^\perp\implies P_{A}=P_{A_{1}}+P_{A_{2}^\perp}$$

> [!exercise]

没懂啥叫 "本质上相当于"...

> [!exercise]

$$\hat{y}=P_{\mathbb 1}y=\frac{\mathbb 1\mathbb 1^T}{\mathbb 1^T\mathbb 1}y=\frac{1}{n}\sum_{i}y_{i}=\bar{y}\implies \hat{\mu}=\bar{y}$$

> [!exercise]

$$P_{X}=X(X^TX)^{-1}X^T$$
其中
$$(X^TX)^{-1}=\frac{1}{n\sum x_{i}^2-\left( \sum x_{i} \right)^2}\begin{pmatrix}
\sum x_{i}^2&-\sum x_{i} \\
-\sum x_{i}&n
\end{pmatrix}$$
从而
$$P_{X}= \frac{\mathbb 1\mathbb 1^T}{n}+\frac{(x-\mathbb 1\bar{x})(x-\mathbb 1\bar{x})^T}{\|x-\mathbb 1\bar{x}\|^2}$$


> [!exercise]

变量 $z$ 应该与 $x$ 相关