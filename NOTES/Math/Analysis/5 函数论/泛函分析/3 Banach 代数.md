
# Banach 代数
考虑 Banach 空间的自线性映射 $\mathcal B(X)$, 我们知道它本身是一个 Banach 空间, 并且其中有自然的乘法即映射复合, 并且
$$\|AB\|_{\text{op}}\leq \|A\|_{\text{op}}\|B\|_{\text{op}}$$
从中可以抽象出一个代数结构

> [!def] Banach 代数
> 一个 Banach 代数是指一个 Banach 空间 $\mathcal{A}$ 配上一个乘法运算 $\mathcal A^2\to\mathcal A$ 使得
> - 与加法和数乘分别有结合律
> - 其范数满足次可乘性
> $$\forall_{a,b\in\mathcal A},\|ab\|\leq\|a\|\|b\|$$
> - 存在乘法单位元
> $$\exists\mathbb 1\in\mathcal A:\forall a,a\mathbb 1=\mathbb 1a=a$$

好, 现在数数我们都在这东西上叠了多少结构了:
- 一个范数
- 一个拓扑 (由范数引出)
- 一个线性 (加法和数乘, 都是连续的)
- 一个乘法 (由次可乘性连续)

Examples:
- $L^p$ 空间配上逐点相乘
- 连续函数在 $L^\infty$ 范数意义下构成的空间配上逐点相乘

总之还是得研究这个代数的性质, 这个乘法不交换, 所以要讨论左逆和右逆, 容易证明左逆和右逆同时存在则相等, 我们记 $\mathcal A$ 中的可逆元为 $\mathcal {G_A}$, 

利用完备性我们能得到一个有趣性质

> [!proposition]
> $x\in\mathcal A$
> $$\|x-\mathbb 1\|<1\iff x^{-1}=\sum_{n=0}^\infty(1-x)^n$$
> 且
> $$\|x^{-1}\|\leq \frac{1}{1-\|1-x\|}$$

`BEGINPROOF`
$$x\lim_{N\to\infty}\sum_{n=0}^N(1-x)^n\xlongequal{乘法连续}\lim_{N\to\infty}x\sum_{n=0}^N(1-x)^n=1-\lim_{N\to\infty}(1-x)^{N+1}=1$$
`ENDPROOF`

下面研究可逆元素整体的性质

> [!proposition]
> $\mathcal {G_A}\in\operatorname{Open}(\mathcal A)$ 且 $a\mapsto a^{-1}$ 为一同胚

`BEGINPROOF`
开集的证明: 往证 $B_{\|a^{-1}\|^{-1}}(a)\subset \mathcal {G_A}$, 对于 $\tilde a\in B_{\|a^{-1}\|^{-1}}(a)$
$$\|\tilde a-a\|\leq \|a^{-1}\|^{-1}\Rightarrow \|a^{-1}\tilde a-\mathbb 1\|<1$$
从而 $a^{-1}\tilde a$ 可逆
$$\underbrace{(a^{-1}\tilde a)^{-1}a^{-1}}_{\tilde a^{-1}}\tilde a=1$$
说明 $\tilde a$ 有左逆, 同理有右逆. 并且
$$\|\tilde a^{-1}\|\leq \|a^{-1}\|\|a\tilde a^{-1}\|\leq \|a^{-1}\|\frac1{1-\|\tilde aa^{-1}-\mathbb 1\|}\leq \frac{\|a^{-1}\|}{1-\|a^{-1}\|\|\tilde a-a\|}$$
另外由于
$$a^{-1}(b-a)b^{-1}=a^{-1}-b^{-1}$$
得到
$$\begin{align}
\|a^{-1}-\tilde a^{-1}\|&\leq \|a^{-1}\|\|a-\tilde a\|\|\tilde a^{-1}\|\\
&\leq \frac{\|a^{-1}\|^2\|a-\tilde a\|}{1-\|a^{-1}\|\|a-\tilde a\|}
\end{align}$$
观察这个函数就知道取逆是个连续映射了, 从而是个同胚.
`ENDPROOF`
再补充一个其实应该出现在线性代数里的命题

> [!proposition]
> $a,b\in\mathcal A$
> $$\mathbb 1-ab\in\mathcal {G_A}\iff \mathbb 1-ba\in\mathcal {G_A}$$

^bdc333

`BEGINPROOF`
断言
$$(\mathbb 1-ab)^{-1}=\mathbb 1+b(\mathbb 1-ab)^{-1}a$$
因为
$$\begin{align}
(\mathbb 1-ba)(\mathbb 1+b(\mathbb 1-ab)^{-1}a)&=\mathbb 1-ba+b(\mathbb 1-ab)^{-1}a-bab(\mathbb 1-ab)^{-1}a\\
&=\mathbb 1-ba+b(\mathbb 1-ab)^{-1}a-b(ab-\mathbb 1+\mathbb 1)(\mathbb 1-ab)^{-1}a\\
&=\mathbb 1-ba+b(\mathbb 1-ab)^{-1}a-b((\mathbb 1-ab)^{-1}-\mathbb 1)a\\
&=\mathbb 1-ba+b(\mathbb 1-ab)^{-1}a+ba-b(\mathbb 1-ab)^{-1}a\\
&=1
\end{align}$$
`ENDPROOF`
这个形其实很像谱, 后续将在 [[#^d05e33]] 中应用之
## Banach 空间值解析函数

这一段里我们把原本复分析中的像空间换成 Banach 空间, 可以发现原有的一堆性质仍然保留, 首先定义可微

> [!def] 可微 Banach 空间值解析函数
> 令 $X$ 为一 Banach 空间, $\Omega\subset \mathbb C$ 为一连通开集, 称函数
> $$f:\Omega\to X$$
> - 在点 $z_0$ 复可微, 是指极限
> $$\lim_{z\to 0}\frac{f(z_0+z)-f(z_0)}{z}$$
> 在 $X$ 范数诱导的拓扑意义下存在, 并且若函数全 $\Omega$ 可微, 记其值为 $f':\Omega\to X$
> - 在点 $z_0$ Frechet 可微, 如果存在线性函数 $L:\Omega\to\mathbb C$ 满足
> $$\lim_{\|z\|\to 0}\frac{\|f(z_0+z)-f(z_0)-Lz\|}{\|z\|}=0$$
> - 弱可微, 是指对任意 $\Lambda\in X^*$, $\Lambda\circ f:\mathbb C\to\mathbb C$ 复可微

Claim: 对于 $\mathbb C$ Banach 空间, 上述三种定义等价, 对于 $\mathbb R$- Banach 空间, 弱可微与复可微等价, 但是不与 Frechet 可微等价.

相应的, 我们也可以定义 Banach 空间值函数的 Riemann 积分, 对于任意分割 $P_n$
$$\int_{[a,b]}f=\lim_{P_n}\sum_{j=1}^n(x_j-x_{j-1})f(x_j)$$
类似微积分中的做法, 右侧这个极限良定当且仅当抖动
$$\omega(f,P):=\sum_{j=1}^n(x_j-x_{j-1})\sup\{f(s)-f(t):s,t\in(x_{j-1},x_j)\}$$
可以被控制得任意小, 另外一个专属 Banach 空间的做法:

> [!thm]
> 若函数 $f:[a,b]\to X$ 是连续的, 则对任意 $\lambda\in X^*$, $\lambda\circ f:[a,b]\to\mathbb C$ 是 Riemann 可积的并且
> $$\lambda\int f=\int \lambda\circ f$$
> 相对的, 若存在 $\psi\in X$ 满足 
> $$\forall\lambda\in X^*,\lambda\psi=\int \lambda\circ f$$
> 则
> $$\psi=\int f$$

^617262

`BEGINPROOF`
正向的证明需要两步操作, 一个是把两边积分的分割互相插入对方, 另一个是利用 $\lambda$ 的连续性交换次序, 逆向是显然的.
`ENDPROOF`
**这是把 $\mathbb C$ 上的条件搬到 Banach 空间的理论基础**

利用这个可以在这上定义围道积分, 然后把复分析那一套拿过来

> [!def]
> 对于逐段光滑函数 $\gamma:[a,b]\to\mathbb C$, 定义 $f:\mathbb C\to X$ 的围道积分为
> $$\int_\gamma f:=\int_{[a,b]}(f\circ \gamma )\gamma'$$
> 如果后者是 Riemann 可积的, 那么就把其值定义为 $f$ 沿 $\gamma$ 的围道积分

利用 Banach 空间的范数可以把复分析那一套东西直接搬过来

> [!lem] ML lemma
> $f:\mathbb C\to X$ 连续, 且 $\gamma:[a,b]\to\mathbb C$ 逐段光滑, 则
> $$\left\|\int_\gamma f \right\|\leq \sup_{t\in[a,b]}\|f(\gamma(t))\|_XL(\gamma)$$

> [!thm] Cauchy 积分公式
> $\Omega\subset \mathbb C$ 为一单连通集, $f:\Omega\to X$ 在其上 $\mathbb C$-可微, 则对任意单连通闭曲线 $\gamma:[a,b]\to\Omega$, 若 $z_0$ 在 $\gamma$ 内部
> $$f^{(n)}(z_0)=\frac{n!}{2\pi i}\int_\gamma\frac1{(z-z_0)^{n+1}}f(z)\ dz$$

`BEGINPROOF`
类比复分析, 只需证明 $n=0$ 的情况, 取 $\lambda\in X^*$, 则 $\lambda\circ f:\Omega\to\mathbb C$ 为 $\mathbb C$-可微, 从而
$$(\lambda\circ f)(z_0)=\frac1{2\pi i}\int_\gamma (\lambda\circ f)(z)\ dz$$
对任意 $\lambda$ 满足, 则由 [[#^617262]] 可知结论成立, 同理可推广到
`ENDPROOF`

那自然就有 Cauchy 不等式
$$\|f^{(n)}(z_0)\|_X\leq \frac{n!}{R^n}\sup_{z\in\overline{B_R(z_0)}}\|f(z)\|_X$$
以及

> [!thm] Banach 空间值解析函数的 Liouville 定理
> 令 $X$ 为一 Banach 空间, $f:\mathbb C\to X$ 为一弱整函数, 并且 $f(\mathbb C)$ 为一弱有界函数, 则 $f$ 为常值

^040fe9

`BEGINPROOF`
条件就是说对任意 $\Lambda\in X^*$, $\Lambda\circ f$ 为整函数和有界函数, 从而是常值函数, 这就是说 
$$\Lambda\circ f(z)=\lambda\circ f(0_\mathbb C),\forall\Lambda\in X^*$$
而对任意 $z:f(z)-f(0)\neq0$, 取一在 $f(z)-f(0)\neq0$ 上非零的对偶即可得到矛盾.
`ENDPROOF`
这或许是对偶空间对原始空间的控制的一例

## 谱

谱是 Banach 代数的主要概念, 此处 $\mathbb C$ 和 $\mathbb R$-Banach 空间的性质有所不同, 我们主要关注复的情形

> [!def] 谱
> 记 $\mathcal A$ 为一 Banach 代数, $\forall a\in\mathcal A$ 记 $\sigma(a)\subset \mathbb C$ 为 $a$ 的谱:
> $$\sigma(a):=\{z\in\mathbb C\mid (a-z\mathbb 1)\not\in \mathcal {G_A}\}$$
> 其补集 $\rho:=\mathbb C\setminus \sigma(a)$ 记作 $a$ 的 resolvent 集, $r(a)=\sup|\sigma(a)|$ 称为 $a$ 的谱半径

其重要性质是

> [!thm]
> $\forall a\in\mathcal A$, $\sigma(a)$ 为 $\mathbb C$ 的一非空紧子集

$\mathbb C$ 上的紧子集无非是有界闭集, 所以我们实际上要证三件事: 闭集, 有界, 和非空.

`BEGINPROOF`
**闭集**: 考虑函数
$$\begin{align}
\varphi:\mathbb C&\to \mathcal A\\
z&\mapsto a-z\mathbb 1
\end{align}$$
则 $\varphi$ 是个连续函数, 而 $\mathcal {G_A}$ 为一开集, 则 $\rho(a)=\varphi^{-1}(\mathcal {G_A})$ 为一开集, 从而其补集 $\sigma(a)$ 为闭集

**有界**: 往证 $r(a)\leq \|a\|$, 这是因为
$$\forall z:|z|>\|a\|, \|1-(1-\frac az)\|<1\Rightarrow (1-\frac az)\ 可逆\Rightarrow a-z\mathbb 1\ 可逆$$
从而 $\varphi(B^c_{\|a\|}(0_\mathbb C))\subset \rho(a)\Rightarrow \sigma(a)\subset B_{\|a\|}(0_\mathbb C)$

**非空**: 若 $\sigma(a)=\emptyset$, 则 $\rho(\sigma)=\mathbb C$
$$\begin{align}
\psi:\rho(a)&\to \mathcal A\\
z&\mapsto (a-z\mathbb 1)^{-1}
\end{align}$$
我们断言 $\psi$ 是复可微的, 因为 [^1]
$$\begin{align}
\psi'(z_0)&=\lim_{z\to 0}\frac{\psi(z+z_0)-\psi(z_0)}{z}\\&=\lim_{z\to 0}\frac{(a-(z+z_0)\mathbb 1)^{-1}-(a-z_0\mathbb 1)^{-1}}{z}\\
&=\lim_{z\to0}\frac{(a-z_0\mathbb 1)^{-1}((a-z_0\mathbb 1)-(a-(z+z_0)\mathbb 1))(a-(z+z_0)\mathbb 1)^{-1}}{z}\\
&=\lim_{z\to0}(a-z_0\mathbb 1)^{-1}(a-(z+z_0)\mathbb 1)^{-1}\\
&=\psi^2(z_0)
\end{align}$$
并且 $\psi$ 是有界的, 因为对 $|z|>\|a\|$, 有
$$\begin{align}
\|\psi(z)\|&=\left\|(a-z\mathbb 1)^{-1}\right\|\leq |z|^{-1}\left\|\left(\frac az-\mathbb 1\right)^{-1}\right\|\\
&\leq \frac{|z|^{-1}}{1-\left\|a/z\right\|}\to 0\quad\text{as }|z|\to\infty
\end{align}$$
而 $\forall\lambda, |\lambda\circ \psi(z)|\leq \|\lambda \|_{\text{op}}\|\psi(z)\|$ 从而若 $\psi$ 为整函数由 [[#^040fe9]] 立刻知 $\psi$ 为常数, 这与刚刚的计算相矛盾
`ENDPROOF`

[^1]: 这里我看的 notes 似乎带错数, 和我算的相反, 当然也不排除我唐了, 暂且写成个注在这里. 一个不用具体计算的证法是关注 (以及 Lax 的泛函这里也差个符号, 我越发觉得是我唐了) $$(z-h-a)^{-1}=\sum_{n\geq0}(z-a)^{-n-1}h^n$$在 $|h|<|(z-a)^{-1}|^{-1}$ 时后者收敛

下一个概念是谱范数的逼近

> [!thm] Gelfand 公式
> $\forall a\in\mathcal A$, 极限 $\lim_{n\to\infty}\|a^n\|^{1/n}$ 存在, 且
> $$r(a)=\lim_{n\to\infty}\|a^n\|^{1/n}=\inf\|a^n\|^{1/n}$$

`BEGINPROOF`
注意到数列 $b_n:=\log \|a^n\|$ 是次可加的, 即
$$b_{n+m}=\log\|a^{m+n}\|\leq \log(\|a^n\|\|a^m\|)=b_m+b_m$$
那么 $\lim_{n\to\infty}\frac1nb_n=\inf\frac1n b_n$ 存在, 即 $\lim_{n\to\infty}\|a^n\|^{1/n}=\inf\|a^n\|^{1/n}$ 存在, 这部分的证明是平凡的. 

首先证明 $\lim_{n\to\infty}\|a_n\|^{1/n}\geq r(a)$, 若 $z\in\sigma(a)$, 则
$$z^n\mathbb 1-a^n=(z\mathbb 1+a)(z^{n-1}\mathbb 1+\cdots+a^{n-1})$$
也不可逆 [^2], 于是 $|z^n|\leq \|a^n\|$, 从而 $r(a)\leq \inf\|a^n\|^{1/n}$

下面证明另一个方向, 借助上一证明中定义的 $\psi$, 考虑 
$$\psi(z)=(a-z\mathbb 1)^{-1}=-\sum_{n=0}^\infty z^{-n-1}a^n$$
在 $|z|>\|a\|$ 一致收敛, 从而可以利用 Cauchy 公式
$$\begin{align}
\int_{|z|=R}z^m\psi(z)\ dz&=-\int_{|z|=R}\sum_{n\geq0} z^{m-n-1}a^n\ dz\\
&=-\sum_{n\geq0}a^n\int_{|z|=R}z^{m-n-1}\ dz\\
&=-\sum_{n=0}^\infty a^n2\pi i\delta_{n,m}\\
&=-2\pi ia^m
\end{align}$$
从而
$$a^n=-\frac1{2\pi i}\int_{|z|=R}z^n\psi(z)\ dz\quad (R>\|a\|;n\in\mathbb N^+)$$
而我们知道 $\sigma(a)\subset B_{\|a\|}(0_\mathbb C)$, 这说明 $r(a)<\|a\|$, 而 $\psi$ 在 $|z|>r(a)$ 上调和, 从而可以把围道换成
$$a^n=-\frac1{2\pi i}\int_{|z|=R}z^n\psi(z)\ dz\quad (R>r(a);n\in\mathbb N^+)$$
两边取范数
$$\|a^n\|\leq R^{n+1}\sup_{|z|=R}\|\psi(z)\|\quad (R>r(a))$$
对 $n$ 取极限
$$\limsup_{n\to\infty}\|a^n\|\leq r(a)$$
`ENDPROOF`

[^2]: 注意在无穷维时 $a,b$ 分别不可逆不意味着 $ab$ 不可逆, 考虑把所有的基向量排列在 $\mathbb N$ 上, 向右迁移 $k$ 位和向左迁移 $k$ 位的线性泛函分别是不可逆的, 但复合起来是 $\mathbb 1$, 而此处可以进行此论断是因为这里的两个因子是可交换的.

> [!thm] Gelfand-Mazur
> 若 $\mathcal A$ 为一 Banach 代数且 $\mathcal A\setminus\{0\}\subset \mathcal {G_A}$, 则 $\mathcal A$ 等测度同构于 $\mathbb C$

`BEGINPROOF`
因为 $\sigma(a)$ 非空, 则其即为原点的独点集, 从而对任意 $a\in\mathcal A$, 存在 $z\in\mathbb C:a-z\mathbb 1=0\Rightarrow a=z\mathbb 1$, 则这个同构就是 $z\mapsto z\mathbb 1$.
`ENDPROOF`

> [!lem]
> $$\mathcal {G_A}\ni x_n\to x\in\partial\mathcal {G_A}\Rightarrow\|(x_n)^{-1}\|\to\infty$$

`BEGINPROOF`
考虑
$$\|1-(x_n)^{-1}x\|=\|(x_n)^{-1}(x_n-x)\|\leq \|(x_n)^{-1}\|\|x_n-x\|$$
若小于 $1$ 则 $(x_n)^{-1}x$ 可逆, 进而 $x\in\mathcal {G_A}$ 产生矛盾, 而 $\|(x_n-x)\|$ 是个逼近 $0$ 的东西, 所以 $\|(x_n)^{-1}\|$ 必然不能有界
`ENDPROOF`

> [!thm] 谱的连续性
> 若 $a\in\mathcal A$, 且 $\sigma(a)\subset\Omega\in\operatorname{Open}(\mathbb C)$, 若 $b$ 满足
> $$\|b-a\|\leq \left(\sup_{z\in\Omega^c}\left\|(a-z\mathbb 1)^{-1}\right\|\right)^{-1}$$
> 则 $\sigma(b)\subset\Omega$

`BEGINPROOF`
对任意 $z\in\Omega^c$
$$b-z\mathbb 1=\underbrace{(a-z\mathbb 1)}_{可逆}\underbrace{\left((a-z\mathbb 1)^{-1}(b-a)+\mathbb 1\right)}_h$$
则要令 $h$ 可逆只需
$$\begin{align}
&\|(a-z\mathbb 1)^{-1}(b-a)\|\leq \|(a-z\mathbb 1)^{-1}\|\|(b-a)\|\leq1\\
&\Longleftarrow\|b-a\|\leq \left(\sup_{z\in\Omega^c}\left\|(a-z\mathbb 1)^{-1}\right\|\right)^{-1}
\end{align}$$
`ENDPROOF`

换句话说, 函数 $\sigma$ 是 "连续" 的

> [!lem]
> $\forall a,b\in\mathcal A$
> $$\sigma(ab)\setminus\{0\}=\sigma(ba)\setminus\{0\}$$

^d05e33

这是 [[#^bdc333]] 的直接推论

## 调和函数微积分

我们先在 Banach 空间上构建多项式函数
$$\begin{align}
\chi_a:\mathcal P&\to\mathcal A\\
p&\mapsto p(a)=\sum_{j=1}^n c_jz^j
\end{align}$$
这个映射称为函数微积分, 某种意义上讲, 泛函分析的任务就是在函数空间中逐渐定义更广泛的函数微积分, 相应的, 我们也需要逐渐加强对函数空间的要求. 其高潮是 Hilbert 空间上正规算子的谱定理.

下面我们把这个多项式变成幂级数, 就能得到调和函数微积分:
$$f(a)=\sum_{n=0}^\infty c_na^n$$
这里要处理的问题有
- 若 $f$ 不是整函数, 上述表述未必成立
- 后面那个幂级数的收敛问题

我们先回忆幂级数的一般理论, 假设一函数在 $B_R(0_\mathbb C)$ 上调和, 则可以将 $f$ 写成 
$$f(z)=\sum_{n=0}^\infty c_nz^n$$
则若 $r(a)<R$, 由谱半径公式
$$\left\|\sum_{n=N}^Mc_na^n\right\|\leq \sum_{n=N}^M|c_n|\left (\|a^n\|^{1/n}\right)^n\underset{N\gg 1}\leq \sum |c_n|R^n$$
从而幂级数 Cauchy, 由完备性收敛

但是这对调和函数的要求其实很高, 我们像拿到更小的调和要求, 我们先给这个函数戳几个洞, 考虑有理函数

> [!thm]
> 记 $a\in\mathcal A$, $\alpha\in\rho(a)$, $\Omega:=\mathbb C\setminus {\alpha}$. 取出一些包裹 $\sigma(a)$ 的可定向曲线 $\gamma_{1\sim m}:[a,b]\to\Omega$ 使得
> $$\frac1{2\pi i}\sum_{j=1}^m\int_{\gamma_j}\frac1{z-\lambda}\ dz=\begin{cases}
> 1&\lambda\in\sigma(a)\\
> 0&\lambda\in\Omega^c\text{ or }\lambda=\alpha
> \end{cases}$$
> 则
> $$\frac1{2\pi i}\sum\int_{\gamma_j}(\alpha-z)^n(z\mathbb 1-a)^{-1}\ dz=(\alpha\mathbb 1-a)^n\quad n\in\mathbb Z$$

rmk: 可以想见这些曲线大概就是 "$\sigma(a)$ 中的一个点只被一个曲线圈进去" 的曲线, 其存在性由 $\sigma (a)$ 是非空紧集保证, 构造大概是切成足够小的小方格套住 $K$, 再把所有和 $K$ 交集非空的小方块边界全部定向的并起来 (这样避开了讨论 "套住" 这个不好定义的概念)

`BEGINPROOF`
首先证 $n=0$ 的情形, 即
$$\frac1{2\pi i}\sum_{j=1}^m\int_{\gamma_j}(z\mathbb 1-a)^{-1}\ dz=\mathbb 1$$
把这些曲线并起来简写成
$$\int_{\Gamma}\sum_{n=0}^\infty z^{-n-1}a^n=\sum_{n=0}^\infty a^n\int_\Gamma z^{-n-1}\ dz=\mathbb 1\int_\Gamma \frac1z\ dz=2\pi i\mathbb 1$$
(事实上因为 $z\mapsto (a-z\mathbb 1)^{-1}$ 在 $\rho(a)$ 上全纯, 这一步的 $\Gamma$ 实际上是把 $\sigma(a)$ 圈进来的一条大曲线)

后续其实就是一些符号计算, 记
$$y_n:=\frac1{2\pi i}\int_\Gamma(a-z)^n(z\mathbb 1-a)^{-1}\ dz$$
并证明
$$(z\mathbb 1-\alpha)^{-1}y_n=y_{n+1}$$
同时应用观察
$$\begin{align}
(z\mathbb 1-a)^{-1}-(\alpha\mathbb 1-a)^{-1}&=(\alpha\mathbb 1-a)^{-1}((\alpha\mathbb 1-a)-(z\mathbb 1-a))(z\mathbb 1-a)^{-1}\\
(z\mathbb 1-\alpha)^{-1}&=(\alpha\mathbb 1-a)^{-1}+(\alpha-z)(\alpha\mathbb 1-a)^{-1}(z\mathbb 1-a)^{-1}
\end{align}$$
带入得到
$$\begin{align}
y_n&=\frac1{2\pi i}\int_\Gamma(a-z)^n(z\mathbb 1-a)^{-1}\ dz\\
&=\frac1{2\pi i}\int_\Gamma(a-z)^n\left((\alpha\mathbb 1-a)^{-1}+(\alpha-z)(\alpha\mathbb 1-a)^{-1}(z\mathbb 1-a)^{-1}\right)\ dz\\
&=\frac{(\alpha\mathbb 1-a)^{-1}}{2\pi i}\left(\underbrace{\int_\Gamma(\alpha-z)^n\ dz}_{=0}+\int_\Gamma(\alpha-z)^{n+1}(z\mathbb 1-a)^{-1}\ dz\right)\\
&=(\alpha\mathbb 1-a)^{-1} y_{n+1}
\end{align}$$
`ENDPROOF`
直接带入可知

> [!cor]
> 对有理函数
> $$R(z)=\underset{多项式}{p(z)}+\sum_{i=1}^n\sum_{j=1}^qc_{i,j}(z-z_i)^{-j}$$
> 以及 $a\in\mathcal A$, $\sigma(a)\subset\Omega\in\operatorname{Open(\mathbb C)}$, $R$ 在 $\Omega$ 上全纯, 若有一簇曲线 $\gamma_k:[a,b]\to\Omega$, $k=1,\cdots,m$, 使得
> $$\frac1{2\pi i}\int_\Gamma\frac1{z-\lambda}\ dz=\begin{cases}
> 1&\lambda\in\sigma(a)\\
> 0&\lambda\not\in\Omega
> \end{cases}$$
> 则
> $$R(a)=\frac1{2\pi i}\int_\Gamma R(z)(z\mathbb 1-a)^{-1}\ dz$$

这就是有理函数的 Cauchy 公式, 下面证明调和函数的版本

> [!thm] 调和函数微积分
> $a\in\mathcal A$, $\sigma(a)\subset \Omega\subset\in\operatorname{Open})\mathbb C$, 一簇可定向曲线 $\gamma_j:[a,b]\to\Omega$, $j=1,\cdots,m$ 满足
> $$\frac1{2\pi i}\int_\Gamma\frac1{z-\lambda}\ dz=\begin{cases}
> 1&\lambda\in\sigma(a)\\0&\lambda\not\in\Omega
> \end{cases}$$
> 则对任意 $f\in H(\Omega)$, 
> $$\frac1{2\pi i}\int_\Gamma f(z)(z\mathbb 1-a)^{-1}\ dz=f(a)$$
> 这是一个含幺代数单同态:
> - $f(a)g(a)=(fg)(a)$, $f(a)+g(a)=(f+g)(a)$
> - $(z\mapsto1)(a)=\mathbb 1$, $(z\mapsto z)(a)=a$
> - 连续性体现在若有 $\Omega$ 的紧子集 $K$ 上 $f_n\xrightarrow{\text{uni}}f$, 则依范数 $f_n(a)\to f(a)$

`BEGINPROOF`
我们已经证明过 $z\mapsto (z\mathbb 1-a)^{-1}$ 为 $\rho(a)$ 上的一调和函数, 从而式子左边可积

下一步是说明 $f\mapsto f(a)$ 为单射, 我们需要讨论这一映射的核, 由积分公式
$$\begin{align}
f(a)=0&\Rightarrow \frac1{2\pi i}\int_\Gamma f(z)(z\mathbb 1-a)^{-1}\ dz=0\\
&\Rightarrow \frac1{2\pi i}\int_\Gamma f(z)(z\mathbb 1-\lambda \mathbb 1)^{-1}\ dz=0\quad(\lambda\in\sigma(a))
\end{align}$$
#todo 
`ENDPROOF`
从而我们知道 $f(a)g(a)=g(a)f(a)$, 即单个算子的函数乘法交换, 这也是我们把 $a$ 直接带入 $f$ 的理论依据, 否则可以想见把一个本来作用在交换的东西上的函数作用在不叫唤的东西上本身就会导致一堆问题

调和函数微积分的一些其它性质, 其实也是线代就见过的东西

> [!lem]
> $a\in\mathcal A$, $\sigma(a)\subset\Omega\in\operatorname{Open}(\mathbb C)$, $f\in\mathcal H(\Omega)$
> $$f(a)\in\mathcal {G_A}\iff 0\not\in f(\sigma(a)) $$

^03e798

`BEGINPROOF`
$$0\not\in f(\sigma(a))\Rightarrow g:=\frac1f\in\underset{\sigma(a)\subset\tilde\Omega\underset{\text{open}}\subset\Omega}{\mathcal H(\tilde \Omega)}\Rightarrow f(a)g(a)=\mathbb 1\Rightarrow f(a)\in\mathcal {G_A}$$
相对的
$$\begin{align}
\alpha\in \sigma(a):f(\alpha)=0&\Rightarrow f(\lambda )=h(\lambda)(\lambda-\alpha),h\in\mathcal H(\Omega)\\
&\Rightarrow f(a)=(a-\alpha\mathbb 1)h(a)=h(a)(a-\alpha\mathbb 1)\\
\small{(\alpha\in\sigma(a)\Rightarrow a-\alpha\mathbb 1\ 不可逆)}&\Rightarrow f(a)\not \in \mathcal G(A)
\end{align}$$
`ENDPROOF`


> [!thm] 谱映射定理
> $$\sigma(f(a))=f(\sigma(a))\equiv\{f(z):z\in\sigma(a)\}$$

`BEGINPROOF`
by [[#^03e798]] 
$$\begin{align}
z\in\sigma(f(a))&{}\iff f(a)-z\mathbb 1\not\in\mathcal {G_A}\\
&{}\iff 0\in\operatorname{Im}\left((\sigma(a)\ni\lambda\mapsto f(\lambda)-z)|_{\sigma(a)}\right)\\
&{}\iff z\in \operatorname{Im}\left((\sigma(a)\ni\lambda\mapsto f(\lambda))|_{\sigma(a)}\right)\\
&{}\iff z\in f(\sigma(a))
\end{align}$$
`ENDPROOF`
> [!lem]
> $a\in\mathcal A$, $\sigma(a)\subset \Omega\in\operatorname{Open}(\mathbb C)$, $f\in\mathcal H(\Omega)$, $f(\sigma(a))\subset\tilde\Omega\in\operatorname{Open}(\mathbb C)$, $g\in\mathcal H(\tilde \Omega)$
> $$g(f(a))=(g\circ f)(a)$$

`BEGINPROOF`
套两次调和函数微积分
$$\begin{align}
g(f(a))&=\frac1{2\pi i}\int_\Gamma g(z)(z\mathbb 1-f(a))^{-1}\ dz\\
(z\mathbb 1-f(a))^{-1}&=\frac1{2\pi i}\int_{\tilde\Gamma} (z-f(\zeta))^{-1}(a-\zeta\mathbb 1)^{-1}\ d\zeta\\
\\
g(f(a))&=\frac1{2\pi i}\int_\Gamma g(z)\frac1{2\pi i}\int_{\tilde\Gamma}(z-f(\zeta))^{-1}(a-\zeta\mathbb 1)^{-1}\ d\zeta\ dz\\
(一致收敛)&=\frac1{2\pi i}\int_{\tilde \Gamma }\underbrace{\frac1{2\pi i}\int_\Gamma g(z)(z-f(\zeta))^{-1}\ dz}_{g(f(\zeta))=g\circ f(\zeta)}(a-\zeta\mathbb 1)^{-1}\ d\zeta\\
&=\frac1{2\pi i}\int_{\tilde \Gamma}(g\circ f)(\zeta)(a-\zeta\mathbb 1)^{-1}\ d\zeta\\
&\equiv (g\circ f)(a)
\end{align}$$
当然这里需要判断 $(z-f(\zeta))^{-1}\in\mathcal H(\Omega)$, 这是因为 $z\in\tilde\Omega\setminus f(\sigma(a))$.
`ENDPROOF`
一个在实践中反复应用的例子是

> [!thm]
> $a\in\mathcal A$, $\sigma(a)$ 不将 $0$ 和 $\infty$ 分离, 则 $\log(a)\in\mathcal A$, 且 $a=\exp\log(a)$
