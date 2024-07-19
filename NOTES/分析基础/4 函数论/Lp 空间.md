# $L^p$ 空间

> [!def] $L_p$ 空间
> 对于测度空间 $(\Omega,\mathcal F,\mu)$ 对任意 $p:0<p<\infty$, 我们令
$$L^p(\Omega,\mathcal F,\mu)=\{f\in \mathcal L(\Omega,\mathcal F)\mid \mu(|f|^p)<\infty\}$$
> 在这一空间中不区分 $\mu$-a.e. 相等的函数, 即将其视为按 $\mu$ 等价关系所作的商空间, 令
> $$\|f\|_p=\mu(|f|^p)^\frac1p$$
> 特别地, $L_\infty(E)$ 是指 $E$ 上几乎处处有界的可测函数空间

Rmk: 关于 $L_\infty$ 范数的定义
$$\begin{align}
\|f\|_{L^\infty(E)}&=\mathrm{ess}\ \sup_{x\in E}|f(x)|=\inf_{m(Z)=0}\sup_{x\in E\setminus Z}|f(x)|\\
&=\inf\{M>0:|f(z)|\underset{\text{a.e.}}\leq M\}& 收缩\\
&=\sup\{M>0:m([f(z)>M])>0\}&膨胀
\end{align}$$
这个叫做函数 $f$ 的**本性上界*

Properties:
- $L^p$ 空间是 Banach 空间
- $L^p$ 可分当且仅当底空间可分
- $L^p$ 空间的对偶

后续将一一验证

首先准备一些不等式
$$\begin{align}
|a+b|^r&\leq \max(1,2^{r-1})(|a|^r+|b|^r)\\
|ab|&\leq \frac{|a|^p}{p}+\frac{|b|^q}{q}\quad(\frac1p+\frac1q=1)&\text{(young)}
\end{align}$$
前一个式子在 $r>1$ 时是 $x^r$ 的凸性, $r<1$ 时是凹性; 后一个式子来自对数函数的凹性
$$\log(\frac{|a|^p}p+\frac{|b|^q}q)\geq\frac1p\log({|a|^p})+\frac1q\log({|b|^q})=\log ab$$
从而有

> [!proposition]
> - $C_r$ 不等式: $r>0$, $C_r:=\max(1,2^{r-1})$
> $$\mu(|f+g|^r)\leq C_r\mu(|f|^r+|g|^r)$$
> - Holder 不等式: $\frac1p+\frac1q=1$ (我们称这样的为共轭范数)
> $$\mu(|fg|)\leq \|f\|_p\|g\|_q$$
> - Minkowski 不等式: $s\geq1$
> $$\|f+g\|_s\leq \|f\|_s+\|g\|_s$$
> - Jensen 不等式: 在概率空间中, 若 $\varphi$ 为连续凸函数
> $$\varphi(\mu(f))\leq \mu(\varphi(f))$$

`BEGINPROOF`
(1) 是上述第一个式子的直接推论
(2) 令 $F=\frac f{\|f\|_p}$, $G=\frac{g}{\|g\|_q}$, 则由上述第二个式子
$$\mu(|FG|)\leq \frac{\mu(|F|^p)}p+\frac{\mu(|G|^q)}q=1$$
(3) 不妨设 $f,g\in \mathcal L^s$, 则
$$\begin{align}
\int|f+g|^s\ d\mu&\leq \int|f||f+g|^{s-1}\ du+\int|g||f+g|^{s-1}\ d\mu\\
\small{\left(s':\frac1s+\frac1{s'}=1\right)} &\leq \|f\|_s(\int|f+g|^s\ d\mu)^{1/s'}+\|g\|_s(\int|f+g|^s\ d\mu)^{1/s'}
\end{align}$$
简单变形立得
(4) 对
$$\varphi(\mu(f))+\underset{支撑线}{k(x-\mu(f))}\leq \varphi(x)$$
两边积分即得
`ENDPROOF`

> [!cor]
> $$\|fg\|_1\leq \|f\|_p\|g\|_q\leq \frac1p\|f\|_p+\frac1q\|g\|_q$$
> 等号成立当且仅当存在常数 $\alpha$, $\beta$ 满足 $\alpha^2+\beta^2\neq0$, $\alpha|f|^p\xlongequal{\text{a.e.}}\beta|g|^q$, 从而有
> $$\frac1p\|f\|_p^p=\sup_{g\in L^q}\mu(fg-\frac1q\|g\|_q^q)$$

^0b72fa

事实上, 有加强的 Minkovski 不等式

> [!thm] 加强的 Minkovski 不等式
> 对 $\sigma$-有限测度空间 $(X_1,\mu_1)$, $(X_2,\mu_2)$ 及 $f\in \mathcal L^+(X_1\times X_2)$, $1\leq p<\infty$
> $$\|\mu_2(f)(y)\|_{p(x)}\leq \mu_2(\|f\|_{p(x)})$$
> 等式成立当且仅当 $f(x,y)=H(x)G(y)$

^e12c2b

`BEGINPROOF`
记 $H(x):=\int f(x,y)d\mu_2(y)$, 由 [[#^0b72fa]] 只需证对任意 $g\in L^q$:
$$\int gH\ d\mu_1-\frac1q\|g\|_{L^q(\mu_1)}^q\leq \frac1p M^p$$
其中 $M$ 为原不等式右侧. 事实上, 这是 Fubini 定理和 Holder 不等式
$$\int gH\ d\mu_1 \xlongequal{\text{Fubini}}\int \int g(x)f(x,y)\ d\mu_1(x)d\mu_2(y)\overset{\text{Holder}}\leq \|g\|_{L^q(\mu_1)}M\leq \frac1q\|g\|_{L^q}^q+\frac1pM^p $$
`ENDPROOF`
另外**几个有趣的观察**:
- 若 $p<q<r\leq\infty$, $L^q\subset L^p+L^r$, 因为
$$\underset{L^q}f=\underset{L^p}{fI_{[|f|>1]}}+\underset{L^r}{fI_{[|f|\leq 1]}}$$
- 对于有限测度空间 $X$,  $p<q\leq\infty$, $L^q\subset L^p$ 且
$$\|f\|_p\leq \|f\|_q\mu(X)^{1/p-1/q}$$
特别地, 对于概率测度空间, $\|f\|_p\leq \|f\|_q$, 证明依赖 Holder 不等式:
$$\mu(f^p\times 1)\leq \|f^p\|_{q/p}\|1\|_{q/(q-p)}$$

## 完备性

> [!thm] $L^p$ 是 Banach 空间
> 对任意 $p\in [1,\infty]$, $L^p$ 空间是 Banach 空间

`BEGINPROOF`
容易验证 $\|\cdot\|_p$ 作为范数合适
$$\begin{align}
\|f\|_p=0&\Leftrightarrow f\xlongequal{a.e.}0\\
\|\alpha f\|_p&=|\alpha|\|f\|_p
\end{align}$$
关键是收敛性: 若一函数列按 $L^p$ 范数 Cauchy, 我们断言
$$\exists f:f_n\xrightarrow{L^p}f\iff (f_n-f_m)\xrightarrow{L^p}0$$
必要性: 由 $C_r$ 不等式
$$|f_n-f_m|^r\leq C_r(|f_n-f|^r+|f_m-f|^r)$$
充分性: 由于 $L^r$ 基本列都是依测度收敛基本列, 存在 $f$ 使得 $f_n\xrightarrow{\mu}f$, 由 Fatou 引理 
$$\mu(|f_n-f|^r)\leq \limsup_{m\to\infty}\mu(|f_n-f_m|^r)\to 0\text{ as }n\to\infty$$
`ENDPROOF`

## 可分性

我们知道, 可以用简单函数依测度从下逼近任意可测函数, 并且由于 $p>1$ 
$$|f_n-f|^p\leq 2^{p}|f|$$
由控制收敛定理
$$\lim_{n\to\infty}\|f_n-f\|_p=0$$
即可以在 $L^p$ 空间中逼近任意点

下面先给出可分的定义

> [!def] 可分 $\sigma$ 代数
> 一个可分 $\sigma$ 代数, 又称可测 $\sigma$ 代数, 是指存在可数稠密子集族的 $\sigma$ 代数

这允许我们通过**观察有限的子集的性质推断整个 $\sigma$ 代数**

> [!def] 测度可分
> 称 $\sigma$ 可分测度空间 $(\Omega,\mathcal F,\mu)$ 为一 $\mu$ 可分的, 如果存在一个可分的 $\mathcal F$ 的子 $\sigma$ 代数 $\mathcal F_0$, 使得 $\forall A\in\mathcal F$, $\exists B\in\mathcal F_0$, 满足 $\mu(A\Delta B)=0$

$$可数稠密子集族\rightarrow 等测核/包\rightarrow可测集$$

rmk:
这个子集类时常由 Borel 集充当
于是测度可分等价于任意集合的测度可以用一类可数子集逼近


> [!thm]
> 对于 $\sigma$ 有限测度空间, 以下等价
> - 测度可分
> - $\forall p\geq1$, $L^p$ 为可分 Banach 空间
> - $\exists p\geq1$ $L^p$ 为可分 Banach 空间

`BEGINPROOF`
(1) => (2):
设存在一个 $\Omega$ 的可数划分 $\Omega=\sum_n A_n$ 使得 $A_n\in\mathcal F_0$ (差零测集直接不管), $\mu(A_n)<\infty$
取一个代数 $\mathcal L$ 使得 $A_n\in\mathcal L$ 且 $\sigma(L)=\mathcal F_0$, 令其至多可数 (存在性显然), 令
$$\mathcal H=\{\sum_{i=1}^na_iI_{B_i}:B_i\in\mathcal L,a_i\in\mathbb Q\}$$
则
$$\mathcal H\underset{稠密}\subset S(\Omega,\mathcal F)\cap L^p\underset{稠密}\subset L^p$$
(2) => (3) 显然, 下证 (3) => (1)

设有 $L^p$ 为 可分 Banach 空间, 则存在可数稠子集 $\mathcal H$, 我们想要构造 $\mathcal F_0$ 为使得 $\mathcal H$ 中元素可测的最小 $\sigma$ 代数 $\sigma(\mathcal H)$
$$\begin{align}
\forall A\in\mathcal F,\mu(A)<\infty&\Rightarrow I_A\in L^p\\
&\Rightarrow \exists \mathcal H\ni f_n\xrightarrow{L^p}I_A\\
B_n:=[\frac12<f_n<\frac32]&\Rightarrow B_n\in \mathcal F_0,\quad I_{B_n}\xrightarrow{\mu}I_A\\
&\Rightarrow \exists n':I_{B_{n'}}\xrightarrow{\text{a.e.}}I_A\\
B:=\limsup B_{n'}&\Rightarrow B\in\mathcal F_0,\  I_B=I_A,\ \mu(B\Delta A)=0
\end{align}$$
`ENDPROOF`


但是关于这个 $\mathcal H$ 的存在性我依然存疑 #todo

> [!example]
> yja p72 抄个反例上来

> [!cor]
> 若 $\mathcal F$ $\mu$ 可分, 则其上的任意子 $\sigma$ 代数也是 $\mu$ 可分的

在任意一个 $L^p$ 空间中考虑, 只需证明, 可分度量空间的子空间可分

![[Lp 空间-20240720001640193.webp]]
现在把上面研究过的那一套东西再对 $L^\infty$ 操作一遍

> [!thm]
> $\|\cdot\|_\infty$ 是 $L^\infty(\Omega,\mathcal F,\mu)$ 上的范数, $L^\infty(\Omega,\mathcal F,\mu)$ 按范数 $\|\cdot\|_\infty$ 为一 Banach 空间

证明是显然的

## 对偶

本节的主定理: $L_p$ 的对偶空间是 $L_q$ ($\frac1p+\frac1q=1$)

> [!thm]
> $p>1, \frac1p+\frac1q=1$
> $$\begin{align}
> L^q(\Omega,\mathcal F,\mu)&\xrightarrow{\sim}L^p(\Omega,\mathcal F,\mu)^*\\
> g&\mapsto \left(T_g:\ f\mapsto \mu(fg)\right)\\
> 保范:\|g\|_q&=\|T_g\|
> \end{align}$$

`BEGINPROOF`
**保范性的证明**: 设 $g\in L^q(\Omega,\mathcal F,\mu)$, 由 Holder 不等式
$$T_g(f)=\|fg\|_1\leq \|f\|_p\|g\|_q\Rightarrow \|T_g\|_{\text{op}}\leq \|g\|_q$$
上式是 $L^q$ 上的有界线性泛函, 我们下面来证这是等式, 不妨设 $\|g\|_q>0$, 令
$$f=|g|^{q-1}\operatorname{sgn}(g)$$
由于 $(q-1)p=q$, $\|f\|_p^p=\|g\|_q^q$, 从而 $T_g(f)=\mu(|g|^q)=\|g\|_q^q=\|g\|_q\|g\|_q^{q-1}=\|g\|_q\|f\|_p$, 这说明 $\|T_g\|_{\text{op}}\geq\|g\|_q$, 从而 $\|T_g\|_{\text{op}}\geq\|g\|_q$

**显然 $g\mapsto T_g$ 为一线性单射, 下证其为满射**: 设 $T\in L^p(\Omega,\mathcal F,\mu)^*$, 往证存在 $g\in L^q(\Omega,\mathcal F,\mu)$ 使得 $T_g=T$

**我们首先在有限测度集上处理**: 令 $\mathcal G=\{A\in\mathcal F\mid \mu(A)<\infty\}$, 对每个 $A\in\mathcal G$, 取
$$T_A(f)=T(fI_A)$$
则 $T_A\in L^p(\Omega,\mathcal F,\mu)^*$, 且 $\|T_A\|_{\text{op}}\leq \|T\|_{\text{op}}$, 令
$$v_A(B)=T_A(I_B)=T(I_{A\cap B}),\quad \mu_A(B)=\mu(A\cap B),\quad (B\in \mathcal F)$$
则 $v_A$ 为 $(\Omega,\mathcal F)$ 上一有限符号测度, 且 $v_A\ll \mu_A$. 则可以令 $g_A=\frac{d v_A}{d\mu_A}$, 则显然 $g_AI_{A^c}\xlongequal{\text{a.e.}}0$, 下证 $g_A\in L^q(\Omega,\mathcal F,\mu)$ 且 $T_{gA}=T_A$. 

对此, 令 $E_n=[|g_A|\leq n]\cap A$, 则 $E_n\uparrow A$. 记 $h_n=g_AI_{E_n}$, 且对任意 $f\in L^p(\Omega,\mathcal F,\mu)$, 有
$$\begin{align}
T_{h_n}(f)&=\mu(f h_n)=\mu(fg_AI_{E_n})=\mu_A(g_AfI_{E_n})=\mu_A(g_AfI_{E_n})\\
&=v_A(fI_{E_n})=T_A(fI_{E_n})=T_{A\cap E_n}(f)=T_{E_n}(f)
\end{align}$$
于是
$$\|h_n\|_q=\|T_{h_n}\|=\|T_{E_n}\|\leq \|T\|$$
又 $h_n\uparrow g_A$, 由 Fatou 引理 $\|g_A\|_q\leq \|T\|$, 从而 $g_A\in L^q(\Omega,\mathcal F,\mu)$, 于是有
$$T_{g_A}(f)=\mu(g_Af)=\mu_A(g_Af)=v_A(f)=T_A(f)$$
这表明 $T_{g_A}=T_A$

**下面处理到整个空间上**, 设 $A\subset B$, $A,B\in \mathcal G$, 则 $\|T_A\|\leq \|T_B\|$, 且 $g_BI_A\xlongequal{\text{a.e.}}g_A$, 于是可以取 $\mathcal G\ni A_n\uparrow$ 使得
$$\sup_n\|T_{A_n}\|=\sup \{\|T_A\|\mid A\in\mathcal G\}$$
令 $g\xlongequal{\text{a.e.}}\lim_{n\to\infty}g_{A_n}$, $\|g_A\|_q\leq \|T\|$ 由 Fatou 引理 $\|g\|\in L^q$ 下证 $T_g=T$. 令 $A=\bigcup_n A_n$, 则对任意 $f\in L^p(\Omega,\mathcal F,\mu)$, 我们有
$$T_g(f)=\mu(fg)=\lim_{n\to\infty}\mu(fg_{A_n})=\lim_{n\to\infty}T_{A_n}(f)=\lim_{n\to\infty}T(fI_{A_n})$$
因此只需证 $T(fI_{A^c})=0$

**用反证法,** 假定存在某 $f\in L^p(\Omega,\mathcal F,\mu)$ 使得 $T(fI_{A^c})\neq0$, 令 $D_n=[|f|>\frac1n]\cap A^c$ 则 $\mu(D_n)<\infty$ 且由控制收敛定理 $fI_{D_n}\xrightarrow{L^p}fI_{A^c}$, 故存在某 $n_0$, 使 $T(fI_{D_0})$ 非零, 即 $T_{D_{n_0}}(f)\neq0$, 于是 $\|T_{D_{n_0}}\|>0$. 令 $C_n=A_n\cup D_{n_0}$ 则
$$\begin{align}
\|T_{C_n}\|^q&=\|g_{C_n}\|_q^q=\|g_{A_n}+g_{D_n}\|_q^q\\
&=\|g_{A_n}\|_q^q+\|g_{D_n}\|_q^q=\|T_{A_n}\|^q+\|T_{D_n}\|^q
\end{align}$$
则 $\sup_n\|T_{C_n}\|>\sup_n\|T_{A_n}\|$, 这与 $A_n$ 的选择相矛盾

`ENDPROOF`

对于 $L^\infty$ 空间, 情况要稍微复杂一点, 想要它和 $L^1$ 空间对偶, 就需要原空间 $\sigma$-有限

> [!thm]
> 对一 $\sigma$-有限测度空间, $(L^{1})^*$ 和 $L^\infty$ 之间有保范线性同构
> $$\begin{align}
> L^\infty&\to (L^1)^*\\
> g&\mapsto (T_g:f\mapsto \mu(fg))\\
> \|g\|_\infty&=\|T_g\|
> \end{align}$$
> 特别地 $\|fg\|_1\leq \|g\|_\infty\|f\|_1$


`BEGINPROOF`
**保范性**: 显然 $\|T_g\|\leq \|g\|_\infty$ 为证 $\|T_g\|=\|g\|_\infty$, 不妨设 $\|g\|>0$. 对任意 $\varepsilon>0$, 取
$$A\subset [|g|>\|g\|_\infty-\varepsilon]\quad \mu(A)>0_{\text{(由本性上界定义)}}$$
构造一个上极限: 令 $f=I_A\operatorname{sgn}(g)\subset L^1(\Omega,\mathcal F,\mu)$ 从而
$$\begin{align}
\|f\|_1&=\mu(|f|)=\mu(A)\\
T_g(f)&=\mu(|fg|)=\mu(I_A|g|)\geq(\|g\|_\infty-\varepsilon)\mu(A)
\end{align}$$
这表明 $\|T_g\|\geq\|g\|_\infty-\varepsilon$ 由 $\varepsilon$ 的任意性 $\|T_g\|=\|g\|_\infty$

**满射**: 现设 $T\in (L^1)^*$, 往证存在 $g\in L^\infty:T_g=T$. 令
$$\mathcal G=\{A\in\mathcal F\mid \mu(A)<\infty\}\qquad \mathcal G\ni A_n\uparrow \Omega_{(由于\ \sigma\text{-有限})}$$
令
$$v_n(B)=T(I_{A_n\cap B}),\qquad \mu_n(B)=\mu(A_n\cap B),\qquad B\in\mathcal F$$
取 $g_n=\frac{dv_n}{d\mu_n}$, 则显然有 $g_n\in L^\infty(\Omega,\mathcal F,\mu)$ 且对 $f\in L^1(\Omega,\mathcal F,\mu)$ 有
$$T_{A_n}(f)=T(fI_{A_n})=v_n(f)=\mu_n(fg_n)=\mu(fg_n)=T_{g_n}(f)$$
而由于 $\|g_n\|_\infty=\|T_{A_n}\|\leq \|T\|$, 可以令 $g_n\uparrow_{\text{a.e.}} g$, 则 $g\in L^\infty$ 且
$$T_g(f)=\mu(fg)=\lim_{n\to\infty}\mu(fg_n)=\lim_{n\to\infty}T(fI_{A_n})=T(f),$$
从而 $T_g=T$
`ENDPROOF`

定理中关于 sigma 有限的条件不能去掉, 例如
$$\Omega=\mathbb R\qquad \mathcal F=\{A\subset\mathbb R:A或 A^c为至多可数集\}\qquad\mu:计数测度$$
则 $f\in L^1$ 当且仅当 $f$ 仅在一至多可数集上非零且 $\|f\|_1=\sum_x|f(x)|<\infty$. 
$$F:f\mapsto \sum_{x>0}f(x)$$
为 $L^1$ 上一连续线性泛函, $g=I_{0,\infty}$ 为唯一满足 $T_g=T$ 的函数, 但其不是 $\mathcal F$-可测的

# $L^p$ 空间的几何

## 卷积和光滑化

卷积为一种函数间的运算, 类比数的乘法
$$f*g(x):=\int f(x-y)g(y)\ dy$$
其基本性质如下:
- $f*g=g*f$
- $(f*g)*h=f*(g*h)$: 
$$\int \int f(x-y-z)g(z)h(y)\ dzdy\xlongequal{\text{Fubini}}\int \int f(x-y-z)g(z)h(y)\ dydz$$ 再倒一倒: $(f*g)*h=(f*h)*g=(h*f)*g=(h*g)*f=f*(g*h)$
- $\forall z\in\mathbb R^n$, $\tau_z(f*g)=(\tau_zf)*g=f*(\tau_z g)$, 其中 $\tau_zf(x)=f(x-z)$
- $\operatorname{supp}(f*g)=\overline{\operatorname{supp}(f)+\operatorname{supp}(g)}$, 其中 $\operatorname{supp}(f)=\overline{[f\neq0]}$

我们先定义一个平滑的鼓包:
$$\rho(t):=\begin{cases}
c\exp\left(\frac 1{|x|^2-1}\right )&|x|<1\\
0&|x|\geq1
\end{cases}$$
其中 $c$ 为使 $\rho$ 为概率分布的常数, 然后用这个鼓包造一个核
$$\rho_\varepsilon(x):=\frac1{\varepsilon}\rho\left(\frac x\varepsilon\right)$$
这个东西称为**标准光滑子**, 我们通常记
$$f_\varepsilon:=f*\rho_\varepsilon$$
为函数的光滑化, 这样构造出的函数能满足很多性质:
- $\forall\varepsilon>0$, $f_\varepsilon\in C^\infty$
- 若 $f\in C(U)$, 则 $f_\varepsilon\to f$ 在 $U$ 的任意紧子集上一致收敛
- 若 $f\in L_{\text{loc}}^p(U)$, $1\leq p<\infty$ 则 $f_\varepsilon\xrightarrow{L_{\text{loc}}^p}f$
- $f_\varepsilon(x)\to f(x)$ 若 $x$ 为 $f$ 的 Lebesgue 点

> [!proposition] Young's ineq 
> 若 $f\in L^1$, $g\in L^p$, $1\leq p\leq \infty$ 则 $f*g$ 几乎处处存在, 且
> $$\|f*g\|_p\leq \|f\|_p\|g\|_1$$

`BEGINPROOF`
由 [[#^e12c2b]] 
$$\left(\int \left(\int f(x-y)g(y)\ dy\right)^p\ dx\right)^{\frac1p}\leq\int \left(\int f(x-y)^pg^p(y)\ dx\right)^{\frac1p}dy=\|f\|_p\|g\|_1$$
`ENDPROOF`
## 一致凸性

## 范数可微

## 弱收敛和强收敛

# $L^p$ 空间的插值

