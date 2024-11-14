# Hilbert 空间

> [!def] 内积空间
> 内积空间 $\mathcal H$ 是指一个配备了内积结构的 $\mathbb C$-线性空间:
> $$\langle\cdot,\cdot\rangle:\mathcal H\times \mathcal H\to \mathbb C$$
> 满足
> - 共轭对称
> $$\langle \psi,\varphi\rangle =\overline{\langle \psi,\varphi\rangle}$$
> - 在第二个算符上的线性性
> $$\langle\psi,\alpha\varphi+\tilde\varphi\rangle=\alpha\langle \psi,\varphi\rangle + \langle \psi,\tilde \varphi\rangle $$
> - 正定性
> $$\langle\varphi,\varphi\rangle >0\qquad (\varphi\in\mathcal H\setminus \{0\})$$

若已知一个内积显然能得到范数 $\|a\|=\langle a,a\rangle$, 但是哪些范数能被写成内积呢, 由于
$$\langle x,y\rangle =\frac14(\langle x+y,x+y\rangle-\langle x+y,x+y\rangle+i\langle x+iy,x+iy\rangle -i\langle x-iy,x-iy\rangle)$$
想到可以定义
$$\langle x,y\rangle =\frac14(\|x+y\|^2-\|x-y\|^2+i\|x+iy\|^2-i\|x-iy\|^2)$$
其自然满足正定性和交换性, 但是问题在于线性性, 我们想要
$$\langle x,y_1+y_2\rangle\stackrel ?=\langle x,y_1\rangle +\langle x,y_2\rangle$$
其充要条件是平行四边形法则
$$\|x+y\|^2+\|x-y\|^2=2\|x\|^2+2\|y\|^2$$
必要性就是本节第一个式子, 充分性:
$$\begin{align}
&\|x+y_1\|^2-\|x-y_1\|^2+\|x+y_2\|^2-\|x-y_2\|^2\\
=&2\|x+\frac{y_1+y_2}2\|^2+2\|\frac{y_1-y_2}2\|^2-2\|x-\frac{y_1+y_2}{2}\|^2-2\|\frac{y_1-y_2}{2}\|^2\\
=&2\|x+\frac{y_1+y_2}2\|^2+2\|\frac{y_1+y_2}2\|^2-2\|x-\frac{y_1+y_2}{2}\|^2-2\|\frac{y_1+y_2}{2}\|^2\\
=&\|x+\frac{y_1+y_2}{2}+\frac{y_1+y_2}{2}\|^2+\|x\|^2-\|x-\frac{y_1+y_2}{2}-\frac{y_1+y_2}{2}\|^2-\|x\|^2
\end{align}$$
ps: 平行四边形法则中的等号可以改成不等号, 因为令 $x'=\frac{x+y}2$, $y'=\frac{x-y}2$ 就会得到相反的式子, 不过我觉得这个变形除了让人困惑毫无意义

> [!def] Hilbert 空间
> Hilbert 空间是指由内积诱导的范数完备的内积空间

Hilbert 空间是比 Banach 空间更强的数学结构, 不仅是量子力学的数学描述, 也是 Euclidean 空间最合理的无穷维推广, 当然前述的 Banach 代数的性质都可以沿用, 最重要的是我们要在 Hilbert 空间中搞出一种称作 **Hilbert 空间中正规算子 Borel-可测函数微积分**的东西,

> [!def] 正交
> 在 Hilbert 空间中内积为 $0$ 的两元素 $\varphi,\psi$ 正交, 记作 $\varphi\perp\psi$
> 称一簇元素 $\{\varphi_i\}_{i\in I}$ 正规是指 $\langle \varphi_i,\varphi_j\rangle =\delta_{i,j}$

^091a8f

**Properties:**
1. $\varphi\perp\psi\iff \|\varphi\|\leq \|z\psi+\varphi\|\quad (\forall z\in\mathbb C)$
2. 任意非空的闭凸集有最小范数元
3. 子空间 $M\in\operatorname{Closed}(\mathcal H)\Rightarrow M^\perp\in\operatorname{Closed}(\mathcal H),\quad M^\perp\cap M=\{0\}, M^\perp\oplus M=\mathcal H$
4. 若 $W$ 为 $\mathcal H$ 的一子空间, $(\overline W)^\perp=W^\perp$
5. $(M^\perp)^\perp=\overline M$

`BEGINPROOF`
(1) 是显然的, 对于 (2), 记
$$x_n:\|x_n\|\to\inf_{x\in E}\|x\|:=d$$
我们通过有限维上的直观, 认为 $x_n$ 大概收敛到一个点, 从而只需证明 $\|x_m-x_n\|\to 0$
由于 $E$ 是凸集, $E\ni \frac{x_m+x_n}2\to d$, 从而
$$\underbrace{\frac{\|x_n\|^2+\|x_m\|^2}2}_{A}=\underbrace{\left\|\frac{x_n+x_m}{2}\right\|^2}_{B}+\underbrace{\left\|\frac{x_n-x_m}{2}\right\|^2}_{C} $$
$A\to d,B\to d\Rightarrow C\to0$, 由完备性 $x_n\to x$.
(3): $M\cap M^\perp=\{0\}$, 因为若 $\varphi\in M\cap M^\perp\setminus \{0\}$, 则 $\langle \varphi,\varphi,\rangle >0$. 

对任意 $\varphi\in H$, 由 (2) 可以取
$$\psi:=\arg\min_{\psi\in M}\|\psi-h\|$$
则由 (1)
$$\varphi-\psi\perp M$$
(4) 本质是内积的连续性, (5) 是 (4) 的直接推论
`ENDPROOF`
## 对偶和伴随

Hilbert 空间有作为 Banach 空间的对偶, 但是内积结构的最重要的作用是给出了显示的**共轭 $\mathbb C$-线性同构**:

> [!thm]
> 有共轭 $\mathbb C$-线性同构
> $$\begin{align}
> K:\mathcal H&\xrightarrow{\sim}\mathcal H^*\\
> \varphi&\mapsto \langle \varphi,\cdot\rangle 
> \end{align}$$

`BEGINPROOF`
共轭 $\mathbb C$ 线性显然
**保范性:**
$$\begin{align}
\|K(\varphi)\|_{\text{op}}&=\sup_{\|\psi\|=1}|K(\varphi)(\psi)|=\sup_{\|\psi\|=1}|\langle \varphi,\psi\rangle |\\
&=\sup_{\displaylines{\|\alpha\varphi+\psi\|=1\\ \psi\perp\varphi}}|\langle \varphi,\psi\rangle |=\|\varphi\|
\end{align}$$
**单射:**
$$K(\psi)=K(\varphi)\Rightarrow \|K(\psi-\varphi)\|=\|K(\psi)-K(\varphi)\|=0\Rightarrow \psi=\varphi$$
**满射:** 任取 $\lambda\in\mathcal H^*$, 则
$$\mathcal H=\ker\lambda\oplus \ker\lambda^\perp$$
任取 $0\neq\eta\in\ker\lambda^\perp$, 则 $\forall\varphi\in\mathcal H$
$$\begin{align}
&\lambda((\lambda\varphi)\eta-(\lambda\eta)\varphi)=0\\
\Longrightarrow &(\lambda\varphi)\eta-(\lambda\eta)\varphi\in\ker\lambda\\
\Longrightarrow & 0=\langle \eta,(\lambda\varphi)\eta-(\lambda\eta)\varphi\rangle=(\lambda\varphi)\langle \eta,\eta\rangle -(\lambda\eta)\langle \eta,\varphi\rangle  \\
\Longrightarrow &\lambda\varphi =\left\langle \frac{\overline {(\lambda\eta)}}{\|\eta\|^2}\eta ,\varphi\right\rangle 
\end{align}$$
`ENDPROOF`

对于一个 Hilbert 空间, 考虑其上所有有界线性泛函
$$\mathcal B(\mathcal H)\equiv \{A:\mathcal H \to\mathcal H\mid \text{linear }\|A\|<\infty\}$$
我们知道这是个 Banach 代数, 但由于内积的存在, 我们能找到更多的结构 -- **伴随**: 假设有元 $A\in\mathcal B(\mathcal H)$ 考虑上述定义的 $K$, 我们有 $KAK^{-1}\in\mathcal B(\mathcal H^*))$, 称为 $A$ 的伴随. 而由于我们有 $\mathcal H$ 到 $\mathcal H^*$ 的同构, 我们想要利用其得到 $A$ 的伴随在 $\mathcal H$ 的表现.

第一个问题就是一个元素和其伴随能否互相确定, 严格来说就是: 

> [!thm]
> 对于 $A\in\mathcal B(\mathcal H)$, 若有 $\forall \varphi\in\mathcal H,\langle \varphi,A\varphi\rangle =0$ 则 $A=0$,

^61e3c5

`BEGINPROOF`
$$\begin{cases}
0=i\langle i\varphi+\psi,iA\varphi+A\psi\rangle=i\langle i\varphi,A\psi\rangle+ i\langle \psi,iA\varphi\rangle=\langle \varphi,A\psi\rangle -\langle \psi,A\varphi\rangle \\
0=\langle \varphi,A\psi\rangle +\langle \psi,A\varphi\rangle 
\end{cases}$$
两式相加得到 $\langle \varphi,A\psi\rangle =0$ 再令 $\varphi=A\psi$ 得到 $\forall \psi\in\mathcal H,\|A\psi \|^2=0\implies A\psi=0$
`ENDPROOF`


下面正式开始证明: 我们先找到一个中间节点

> [!thm]
> 对任意有界双线性函数 $f:\mathcal H^2\to\mathbb C$ (即)
> $$S:=\sup(\{|f(\varphi,\psi)|:\|\varphi\|=\|\psi\|=1\})<\infty$$
> 必然存在 $F\in\mathcal B(\mathcal H)$ 满足
> $$f(\varphi,\psi)=\langle F\varphi,\psi\rangle\qquad (\varphi,\psi\in\mathcal H)$$
>  且 $\|F\|=S$ 

`BEGINPROOF`
固定一个 $\varphi$, 此时函数 $\mathcal H\ni \psi\mapsto f(\varphi,\psi)$ 为一有界线性函数, 则由上述同构存在 $F(\varphi)\in\mathcal H$ 使得 $f(\varphi,\psi)=\langle F(\varphi),\psi\rangle$, 并且由于 $|f(\varphi,\psi)|\leq S\|\varphi\|\|\psi\|$, 有 $\|F(\varphi)\|\leq S\|\varphi\|$. 而由于 $f$ 为双线性函数, $F$ 必然为线性函数, 下证 $\|F\|=\|S\|$ 由上讨论有 $\|F\|\leq S$, 同时
$$|f(\varphi,\psi)|=|\langle F\varphi,\psi\rangle|\leq\|F\varphi\|\|\psi\|\leq\|F\|\|\varphi\|\|\psi\|\implies\|F\|\geq S$$
`ENDPROOF`
利用上述这个性质, 我们取
$$f(\varphi,\psi)=\langle \varphi,A\psi\rangle$$
则必然有 $A^*\in\mathcal B(\mathcal H):\langle \varphi,A\psi\rangle =\langle A^*\varphi,\psi\rangle$, 并且 $\|A^*\|=\|A\|$.

那么很自然的我们有
$$\langle A^{* *}\varphi,\psi\rangle =\langle \varphi,A^*\psi\rangle =\langle A\varphi,\psi\rangle$$
由 [[#^61e3c5]] $A^{* *}=A$

相比在 Banach 空间上建立的 Banach 代数, 利用这一结构我们能在 $\mathcal H$ 上建立一个称为 $C^*$ 代数的更丰富的结构

> [!claim]
> $$\|A\|^2=\|A^*A\|$$

`BEGINPROOF`
$$\|A\varphi\|^2=\langle A\varphi,A\varphi\rangle=\langle \varphi,A^*A\varphi\rangle \leq\|A^*A\|\|\varphi\|^2$$
另一方向
$$\|A^*A\|\leq\|A^*\|\|A\|=\|A\|^2$$
`ENDPROOF`

从这里就能抽象出 $C^*$ 代数的定义

> [!def] $C^*$ 代数
> 一个 $C^*$ 代数是指一个 Banach 代数 $\mathcal A$ 配上一个 $\mathbb C$-逆线性映射 映射
> $$*:\mathcal A\to \mathcal A$$
> 满足 $\|a^*a\|=\|a\|^2,\forall a\in\mathcal A$

后续将详细研究它

回到 $\mathcal B(\mathcal H)$, 证明一些简单的性质

> [!thm]
> $$\ker(A^*)=\operatorname{im}(A)^\perp\qquad \ker(A)=\operatorname{im} (A^*)^\perp$$
> $$\ker(A)=\ker (A^*A)$$

证明依定义显然

利用内积还可以在 $\mathcal B(\mathcal H)$ 上定义序关系

> [!def] 自伴算子的序
> 对于 $A\in\mathcal B(\mathcal H)$, 称其为正定的, 记作 $A\geq0$, 如果
> $$\langle \varphi,A\varphi\rangle \geq0\quad(\varphi\in\mathcal H)$$
> 相似地, 若有 $A-B\geq0$, 记作 $A\geq B$

