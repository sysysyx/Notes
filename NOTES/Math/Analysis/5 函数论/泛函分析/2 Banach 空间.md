
# Banach 空间及其完备性

> [!proposition]
> Banach 空间是线性拓扑空间

下一步是讨论 Banach 空间间的线性映射,
$$A:X\to Y$$
假如它是连续的, 则由 [[#^b73170]] 其天然是有界的, 或者说
$$M=\sup_{\|x\|_X\leq r}\|Ax\|_Y<\infty$$
我们定义线性映射 $A$ 的**算子范数**为
$$\|A\|_{\mathcal B(X\to Y)}:=\sup(\{\|Ax\|_Y\mid x\in X,\|x\|\leq 1\})$$
其中 $\mathcal B(X\to Y)$ 是所有的有界线性映射, 我们还要判断它是个范数
- $$\|A\|_{\mathcal B(X\to Y)}=0\Rightarrow \|Ax\|_Y|_{B(0,1)}=0\Rightarrow A=0$$
- 三角不等式
$$\begin{align}
\|(A+B)x\|_Y&\leq \|Ax\|_Y+\|Bx\|_Y&{(Y\ 上的三角不等式)}\\
\sup_{\|x\|\leq 1}\|(A+B)x\|_Y&\leq\sup_{\|x\|\leq 1}[\|Ax\|_Y+\|Bx\|_Y]\\
&\leq \sup_{\|x\|\leq 1}\|Ax\|_Y+\sup_{\|x\|\leq 1}\|Bx\|_Y
\end{align}$$

若算则范数有限
$$\forall_{x,y},\|Ax-Ay\|\leq \|A\|\|x-y\|$$
这说明 Banach 空间间的有界线性泛函一定是连续的, 事实上在 [[#^b73170]] 我们提过一个更强的结论, 只要是拓扑线性空间即可. 

然后又到了喜闻乐见的套圈环节, 

> [!thm]
> 若 $X$, $Y$ 是两个 Banach 空间, 则 $(\mathcal B(X\to Y),\|\cdot\|_{\mathcal B(X\to Y)})$ 也是 Banach 空间

^003695

`BEGINPROOF`
已经证明 $\|\cdot\|_{\mathcal B(X\to Y)}$ 是个范数, 其间的加法和数乘可以正常定义, 那么只需要证明其完备即可, 假定一个 Cauchy 列 $\{A_n\}_n$ 可以令
$$\begin{align}
A:X&\to Y\\
x&\mapsto \lim_{n\to\infty}A_nx
\end{align}$$
(右边那个极限可行是因为 $Y$ Banach)
则 $A$ 显然是线性的, 则只要验证 $A_n\to A$ 即可, 在算子范数下
$$\forall_{x:\|x\|\leq 1},\|Ax-A_mx\|_Y=\lim_{n\to\infty}\|A_nx-A_mx\|_Y\leq \lim_{n\to\infty}\|A_n-A_m\|_{\mathcal B(X\to Y)}$$
从而 $\|A-A_m\|_{\mathcal B(X\to Y)}\leq\lim_{n\to\infty}\|A_n-A_m\|_{\mathcal B(X\to Y)}\xrightarrow{m\to\infty}0$ 
`ENDPROOF`

> [!def]
> 对 Banach 空间 $X$, $Y$, $A:X\to Y$ 称同构, 如果 $\forall_x,\|Ax\|_Y=\|x\|_X$


> [!thm] Baire category 
> 完备度量空间 $(E,d)$ 是第二纲集, 既其中稠密开集的可列交依然是稠密的

Rmk:
1. 这个定理非常依赖度量空间的完备性, 不完备的度量空间 $\mathbb Q$ 中有反例 $\bigcap_{q\in\mathbb Q}\mathbb Q\setminus \{q\}=\emptyset$
2. 反过来说也很有意思, 无处稠密的闭集的可列并是一稠密集的补集, 也就是说不能是全集

`BEGINPROOF`
记一列稠密开集 $\{E_i\}_{i\in\mathbb N}$, 任取 $B(x_0,r_0)\in E$
$$B(x_0,r_0)\cap E_1\in\operatorname{Open}(E)\Rightarrow \exists B(x_1,r_1):\overline{B(x_1,r_1)}\subset E_1\cap B(x_0,r_0)$$
再对 $B(x_1,r_1)$ 执行相同操作, 得到一列闭球
$$B(x_n,r_n):\emptyset\neq \bigcap \overline {B(x_n,r_n)}\subset \bigcap E_n$$
`ENDPROOF`

## 三大定理

### Banach-Steinhaus thm: 一致有界原则

> [!thm] Banach-Steinhaus thm: 一致有界原则
> 一簇从 Banach 空间映射到赋范线性空间的有界线性算子
> $$\underset{\alpha\in A}{T_\alpha}:\underset{\text{Banach}}X \to \underset{\text{NLS}}Y$$
> 要么是一致有界的即
> $$\|T_\alpha\|_{\text{op}}<M$$
> 要么在某个稠密 $G_\delta$ 集上满足
> $$\sup_{\alpha\in A}\|T_\alpha x\|=\infty$$

^1e566c

`BEGINPROOF`
令
$$\phi(x)=\sup_{\alpha\in A}\|T_\alpha x\|\qquad V_n=\{x\in X:\phi(x)>n\}$$
由于 $T_\alpha$ 和取范数运算都是连续的
$$V_n=\bigcup_{\alpha\in A}[\|T_\alpha x\|>n]\in\operatorname{Open}(Y)$$
对 $V_n$ 考虑如下情形
- 若每个 $V_n$ 都是稠密 $G_\delta$ 集, 则由 Baire 纲定理知为情形 2;
- 若存在 $V_m$ 不稠密, 往证其为情形 1.

存在 $B(x_0,r)\cap V_m=\emptyset$, 则 $\forall_{\|x\|<r}\forall_\alpha,\|T_\alpha(x_0+x)\|\leq m$, 利用线性结构
$$\forall_{\alpha\in A},\forall_{\|x\|\leq r},\|T_\alpha x\|=\|T_\alpha(x_0+x)\|+\|T_\alpha(x_0)\|\leq 2m\Longrightarrow 存在一致上界\ M= \frac{2m}{r}$$
`ENDPROOF`

其重要应用是, 对于一簇有界线性算子, 在 $A$ 上一致, $X$ 上逐点有界
$$\sup_{\alpha\in A}\|T_\alpha x\|_Y<\infty\quad (x\in X)$$
能推出在 $A$ 和 $X$ 上都一致有界
$$\sup_{\alpha\in A}\|T_\alpha\|_{\mathcal B(X\to Y)}<\infty$$

> [!proposition]
> $X$, $Y$, $Z$ Banach, 双线性函数$B:X\times Y\to Z$ 在两个分量上连续 (既 $B_x:y\mapsto B(x,y)$, 以及类似的 $B_y$ 是连续的), 则 $B$ 是连续的

`BEGINPROOF`
**证法 1:**
由 $B_x$ 的连续性
$$\begin{align}
&\|B(x,y)\|_Z\leq c(x)\|y\|_Y
\end{align}$$
令 $\|y\|_Y=1$, 则有 $\|B(x,y)\|\leq c(x)$.

考虑连续线性函数簇 $\mathcal F:=\{B(\cdot ,y):X\to Z\mid y\in\partial B_1(0_Y)\}$ 有逐点的上界 $c(x)$. 从而有一致上界 $M$ 使得 $\|B(\cdot,y)\|_{\mathcal B(X\to Z)}\leq M\quad (y\in \partial B_1(0_Y))$, 从而
$$\|B(x,y)\|_Z=\|y\|_Y\left\|B\left(x,\frac{y}{\|y\|_Y}\right)\right\|_Z\leq\|y\|_Y\left\|B\left(\cdot ,\frac{y}{\|y\|_Y}\right)\right\|_{\mathcal B(X\to Z)}\|x\|_X\leq M\|x\|\|y\|$$

`ENDPROOF`
当然这个假设了线性性, 如果不线性反例就多起来了, 比如
$$\frac{xy}{x^2+y^2}$$
这种假装跳一下的怪东西 (如图)

![[赋范线性空间-20240721112801616.webp]]
### 开映射定理

我们首先利用线性性把开映射的性质固定在, 既

> [!claim]
> TVS $X$, $Y$, 线性映射 $f:X\to Y$ 将开集映到开集当且仅当 $$\forall_{N\in\operatorname{ONbhd}(0_X)},\exists_{M\in\operatorname{ONbhd}(0_Y)}:M\subset f(N)$$

^705386

`BEGINPROOF`
必要性显然, 下证充分性: 对 $\forall N\in\operatorname{Open}(X)$, 往证 $\forall y\in f(N),\exists \operatorname{ONbhd}(y)\ni M\subset f(N)$ (邻域结构), 这是因为
$$N-x\in\operatorname{ONbhd}(0_X)\Rightarrow \exists_{M_y\in\operatorname{ONbhd}(0_Y)}:M_y\subset f(N-x)= f(N)-y\Rightarrow M=M_y+y$$
`ENDPROOF`
> [!proposition]
> Banach 空间之间的线性映射 $\Lambda:X\to Y$ 是有界的当且仅当
> $$\operatorname{Int}\Lambda^{-1}\overline{B(0_Y,1)}\neq \emptyset$$

`BEGINPROOF`
$$\exists x_0+B(0_X,\varepsilon)\subset \Lambda^{-1}\overline {B(0_Y,1)}\iff \forall_{\|x\|<\varepsilon},\|\Lambda (x_0+x)\|\leq 1+\|\Lambda x \|<\infty $$
`ENDPROOF`

这个思路和下面定理其实差不多

> [!thm] 开映射定理
> 有界线性算子
> $$\Lambda:\underset{\text{Banach}}X\to \underset{\text{Banach}}Y$$
> 如果是满射, 则任一开集的像是开的
> $$U\in\operatorname{Open}(X)\Rightarrow \Lambda(U)\in\operatorname{Open}(Y)$$

Rmk:
- 一个直接的推论 $\exists_{\delta>0},\Lambda(B_X)\supset \delta B_Y$;
- 若 $\Lambda$ 是双射, 定理是说 $\Lambda^{-1}$ 是连续的.

`BEGINPROOF`
ps: 这个证明感觉被我简化过分了, 但至少我没发现错误 qwq

Step1: **利用某些 Baire 纲大法**
$$\begin{align}
&X=\bigcup_{k\in\mathbb N}kB(0,1)=\bigcup_{k\in\mathbb N}B(0,k)\\
\xRightarrow{满射}.&Y=\Lambda X=\Lambda\bigcup B(0,k)=\bigcup \Lambda B(0,k)\\
\end{align}$$
完备 Banach 空间 $Y$ 是第二纲, 那么 $\Lambda B(0,k)$ 就不能都是第一纲的, 而显然只要有一个是第纲全是第二纲, 从而其闭包有非空的内部, 既
$$\forall_{r>0},\operatorname{Int}{\overline {\Lambda B(0,r)}}\neq\emptyset$$
Step2: **把各种点都往原点挪一挪**: 由上知道存在 $y,\varepsilon$ 使得 $B(y,\varepsilon)\subset \overline{\Lambda B(0_X,r)}$, 从而对任意 $\|\tilde y\|<\varepsilon$, 有 $y+\tilde y\in\overline {\Lambda B(0_X,r)}$, 分别取
$$x,\tilde x\in \overline {B(0,r)}:\quad \Lambda x=y,\quad \Lambda\tilde x=y+\tilde y,$$
则 $\|x-\tilde x\|\leq 2r$, $\Lambda (\tilde x-x)=\tilde y$, 从而由 $\tilde y$ 的任意性
$$B(0,\varepsilon)\subset \Lambda\overline {B(0,2r)}\subset \Lambda B(0,4r)$$
`ENDPROOF`
### 闭图像定理

所谓的图像就是
$$\Gamma(f):=\{(x,y)\in X\times Y\mid f(x)=y\}$$
容易知道一个线性算子的图像本身也是一个线性空间, 并且其若是一个闭集, 则其本身是一个 Banach 空间

> [!thm]
> 两 Banach 空间之间的线性映射 $\Lambda:X\to Y$ 是有界的当且仅当其图像是闭的

`BEGINPROOF`
**必要性:** 考虑 $\Gamma$ 中的一 Cauchy 列 $(x_n,\Lambda x_n)\to (x,y)$, 由乘积拓扑的定义, 投影映射
$$p_1:(x,y)\mapsto x\qquad p_2:(x,y)\mapsto y$$
是连续的, 从而
$$\begin{align}
x=p_1(\lim (x_n,y_n))=\lim p_1(x_n,y_n)=\lim x_n\\
y=p_2(\lim (x_n,y_n))=\lim p_2(x_n,y_n)=\lim y_n\\
\end{align}$$
又由于 $\Lambda$ 是连续的
$$\Lambda x=\Lambda \lim_{n\to\infty}x_n=\lim_{n\to\infty}\Lambda x_n=y$$
从而 $(x,y)\in \Gamma$ 于是 $\Gamma$ 是闭的

**充分性:** 若 $\Gamma$ 是 $(X,Y)$ 的一个闭子线性空间则可以令
$$\begin{align}
\tilde \Lambda:X&\to \Gamma\\
x&\mapsto (x,Ax)
\end{align}$$
则 $\tilde \Lambda$ 是一个双射, 其逆 $p_1|_{\Gamma}$ 为连续函数, 从而由开映射定理, $p_1|_\Gamma$ 有连续的逆.
`ENDPROOF`

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
将 $S$ 赋予 $L^2$ 中的内积并取出其中的 $n$ 个单位正交元素 $\varphi_1,\cdots,\varphi_n$, 我们的目标是限制这个 $n$. 令 $B:=\partial B(0_{\mathbb C^n},1)$, 以及
$$\begin{align}
\psi:B&\to S\\
c&\mapsto \sum_{j=1}^nc_j\varphi_j
\end{align}$$
则 $\|\varphi(c)\|_2\leq \|c\|_{\mathbb C^n}=1$, 从而 
$$\|\varphi(c)\|_\infty\leq M$$
则对任意 $c\in B$, 存在 $\Omega'_c\subset \Omega: \mu(\Omega')=1,\forall_{x\in\Omega},|\psi(c)(x)| \leq M$ , 取 $B$ 的一个可列稠密子集 $Q$, 则
$$\exists\Omega'\subset\Omega:\mu(\Omega')=1,\forall_{c\in Q},\forall_{x\in\Omega'},|\psi(c)(x)|\leq M$$
并且对固定的 $x\in \Omega'$, $B\ni c\mapsto |\psi(c)(x)|$ 是连续的, 这说明
$$\forall_{c\in B},\forall_{x\in\Omega'},|\psi (c)(x)|\leq M$$
从而
$$\forall_{x\in\Omega},\sum_j|\varphi_j(x)|^2\leq M^2\Rightarrow n=\left\|\sum_{j=1}^n\varphi_j(x)\right\|_2^2\leq M^2\Rightarrow \dim (S)\leq M^2$$
`ENDPROOF`
> 好奇妙的倒来倒去

# 凸性和 Hahn-Banach 定理

这是线性空间的一个最基本的性质

> [!thm] $\mathbb R$ Hahn-Banach
> 取 $X$ 为一 $\mathbb R$ 线性空间, 函数 $p:X\to \mathbb R$ 满足
> $$\forall_{x,y\in X},\forall_{\alpha\in[0,1]}, p(\alpha x+(1-\alpha)y)\leq \alpha p(x)+(1-\alpha)p(y)$$
> 若定义在一子空间 $Y\subset X$ 上的线性映射 $\lambda:Y\to\mathbb R$ 满足 $\forall_{x\in Y}\lambda(x)\leq p(x)$, 则存在延拓
> $$\Lambda:X\to\mathbb R:\Lambda|_Y=\lambda,\ \forall_{x\in X},\Lambda(x)\leq p(x)$$

^55a7fc

注意线性延拓存在是平凡的 (若承认 Zorn 引理), 关键是仍然被 $p$ 控制

`BEGINPROOF`
先扩一个点: 对任意 $z\in X\setminus Y$, 记 $\tilde Y=\operatorname{span}(Y,z)$, 尝试延拓 $\tilde\lambda:\tilde Y\to\mathbb R$ 由线性性模
$$\tilde\lambda(az+y):=a\tilde \lambda(z)+\lambda(y)$$
因此只需要定义 $\tilde\lambda(z)$ 使得 $\lambda\leq p$ 即可. 任取 $y_1,y_2\in Y$, $\alpha,\beta>0$, 则
$$\begin{align}
\beta\lambda(y_1)+\alpha\lambda(y_2)&=(\alpha+\beta)\tilde\lambda\left(\frac{\alpha}{\alpha+\beta}(y_1-\alpha z)+\frac{\beta}{\alpha+\beta}(y_2+\beta z)\right)\\
&\leq (\alpha+\beta)p\left(\frac{\alpha}{\alpha+\beta}(y_1-\alpha z)+\frac{\beta}{\alpha+\beta}(y_2+\beta z)\right)\\
&\leq \beta p(y_1-\alpha z)+\alpha p(y_1+\beta z)
\end{align}$$
则
$$\frac1\alpha[-p(y_1-\alpha z)+\lambda y_1]\leq \frac1\beta[-p(y_2+\beta z)-\lambda y_2] $$
从而可以令
$$\sup_{\alpha>0,y_1\in Y}\frac1\alpha[-p(y_1-\alpha z)+\lambda y_1] \leq \tilde \lambda (z)\leq \inf_{\beta>0,y_2\in Y}\frac1\beta[-p(y_2+\beta z)-\lambda y_2]$$
只需令 $\alpha=a\ (a<0)$ 或 $\beta=a\ (a>0)$ 即可得到所需式子了

为了说明这个扩展在全空间有效, 我们需要 **Zorn 引理**: 考虑 $\lambda$ 的所有扩张 $(Z,\lambda)$, 在其上定义偏序
$$(Z,\lambda)\leq (Z',\lambda')\iff Z\subset Z',\lambda'|_Z=\lambda$$
对全序子集 $\{(Z_v,\lambda_v)\}$ 可以定义其极大元 $\left(Z=\bigcup Z_v,\lambda=\lambda_v\right)$, 从而任意全序子集有极大元, 由 Zorn 引理, 存在一个最大的扩张 $(X',\Lambda)$, 由上述讨论必然由 $X'=X$, 从而命题得证.
`ENDPROOF`

下一步是将其扩展到复线性空间上

> [!thm] $\mathbb C$ Hahn-Banach
> 对线性空间 $X$ 以及其上的凸函数 $p:X\to\mathbb R$, 若有定义在 $Y\subset X$ 上的线性函数 $\lambda:Y\to\mathbb C$ 使得 $|\lambda(x)|\leq p(x)$ 则存在其 $X$ 上的延拓 $\Lambda$ 使得 $\Lambda|_Y=\lambda$ 且 $|\Lambda|\leq p$

`BEGINPROOF`
只需令 $l(x):=\operatorname{Re}(\lambda(x))$ 则 $l(ix)=\operatorname{Re}(i\lambda(x))=-\operatorname{Im}(\lambda(x))$, 从而 $\lambda (x)=l(x)-il(ix)$ 再利用 [[#^55a7fc]] 定理延拓 $l$ 至 $L$, 再令 $\Lambda(x)=L(x)-iL(ix)$ 验证即可.
`ENDPROOF`

在赋范线性空间中这一定理有如下的表现形式

> [!cor] NLS Hahn-Banach
> 设 NLS $\mathcal X$ 有线性子空间 $\mathcal X_{0}$, $f_{0}$ 是定义在 $\mathcal X_0$ 上的有界线性泛函, 则其必有在 $\mathcal X$ 上的一个保范延拓, 即存在函数 $f$ 满足
> (a) $f(x)\mid_{\mathcal X_{0}}=f_{0}$
> (b) $\|f\|=\|f_{0}\|_{\mathcal X_{0}}$

^d9c423

`BEGINPROOF`
在 $\mathcal X$ 上定义 $p(x)\stackrel \Delta=\|f_{0}\|_{0}\|x\|$ 这是 $\mathcal X$ 上的一个凸函数, 从而必定存在 $\mathcal X$ 上的线性泛函 $f$ 满足
$$\begin{align}
f\mid_{\mathcal X_{0}}&=f_{0} \\
|f(x)|&=\|f_{0}\|_{0}\|x\|\implies \|f\|\leq\|f_{0}\|_{0}
\end{align}$$
又显然有 $\|f_{0}\|_{\mathcal X_{0}}\leq\|f\|$, 从而 $\|f\|=\|f_{0}\|_{\mathcal X_{0}}$
`ENDPROOF`

> [!cor]
> 在赋范线性空间 $\mathcalＸ$ 中, 任给一个 $x_{0}\neq0$, 必定存在 $f\in\mathcal X^*$ 使得 $f(x_{0})=\|x_{0}\|$ 且 $\|f\|=1$
> 反过来说对任意 $x\in X$, 要使 $x=0$ 必须且只需 $\forall f\in\mathcal X^*,f(x_{0})= 0$

^7f7d0f

`BEGINPROOF`
在 $\mathcal X_{0}=\mathbb Kx_{0}$ 中有有界线性泛函 $f(\lambda x_{0})=\lambda\|x_{0}\|$ 再依 [[#^d9c423]] 延拓
`ENDPROOF`

> [!thm]
> 设 NLS $\mathcal X$ 有子空间 $M$ 及 $x_{0}\in \mathcal X\setminus M$, 记 $d=\rho(x_{0},M)=\inf_{x\in M}\|x-x_{0}\|$, 则必定存在 $f\in\mathcal X^*$ 满足
> (a) $f\mid_{M}=0$
> (b) $f(x_{0})=d$
> (c) $\|f\|=1$

`BEGINPROOF`
考虑 $\mathcal X_{0}\stackrel\Delta=\{x=x'+ax_{0}\mid x'\in M,a\in\mathbb K\}$, 定义
$$\begin{align}
f_{0}:\mathcal X_{0}&\to\mathbb K \\
x'+ax_{0}&\to ad
\end{align}$$
则 $f_{0}$ 显然适合 (a)(b), 且
$$|f_{0}(x'+ax_{0})|=|a|d=|a|\rho(x_{0},M)\leq|a|\left \| \frac{x'}{a}+x_{0} \right\|=\|x'+ax_{0}\|=\|x\|$$
因此 $\|f_{0}\|\leq1$, 又由 $d$ 的定义知 $\|f_{0}\|\geq1$, 从而 $\|f_{0}\|=1$ 再用 [[#^d9c423]] 延拓一下就好了
`ENDPROOF`

## 应用

1. 抽象可微函数的中值定理

设 NLS $\mathcal Y$, 函数
$$\begin{align}
f:(a,b)&\to\mathcal Y \\
t&\mapsto f(t)
\end{align}$$
在 $\mathcal Y$ 中存在极限
$$\lim_{ \Delta t \to 0 } \frac{f(t+\Delta t)-f(t)}{\Delta t} $$
则将其定义为 $f$ 在点 $t$ 的微商, 记为 $f'(t)$, 若 $f$ 在 $(a,b)$ 处处有微商, 则称 $f$ 可微, 对这样的函数我们可以拿到中值定理

> [!thm]
> 设抽象函数 $f:(a,b)\to\mathcal Y$ 中可微, 那么对任意 $t_{1},t_{2}\in(a,b)$, 存在 $\theta\in(0,1)$ 使得
> $$\|f(t_{2})-f(t_{1})\|\leq\|f'(\theta t_{2}+(1-\theta) t_{1})\||t_{2}-t_{1}\| $$

中间不是等号而是小于等于是因为范数的定义

`BEGINPROOF`
由 [[#^7f7d0f]] 存在 $y\in\mathcal Y^*$, 使得 $\|y\|=1$ 且
$$\langle y,f(t_{2})-f(t_{1})\rangle =\|f(t_{2})-f(t_{1})\|$$
则存在函数
$$\begin{align}
\varphi:[0,1]&\to\mathbb R \\
\eta&\mapsto \langle y^*,f(t_{1}+\eta(t_{2}-t_{1}))\rangle \\
\end{align}$$
并且
$$\varphi'(\eta)=\langle y^*,f'(t_{1}+\eta(t_{2}-t_{1}))(t_{2}-t_{1})\rangle $$
对其使用微分中值定理
$$\begin{align}
\|f(t_{2})-f(t_{1})\|&=\varphi(1)-\varphi(0)=\varphi'(\theta) \\
&=\langle y^*,f'(t_{1}+\theta(t_{2}-t_{1}))(t_{2}-t_{1})\rangle \\
&\leq \|y^*\|\|f'(t_{1}+\theta(t_{2}-t_{1}))\||t_{2}-t_{1}| \\
&= \|f'(\theta t_{2}+(1-\theta) t_{1})\||t_{2}-t_{1}\| 
\end{align}$$
`ENDPROOF`

2. 凸规划的 Lagrange 乘子
3. 凸函数的次微分

凸集分离定理是数学规划的理论基础, 下面的 Kuhn-Tucker 定理将介绍它是如何发挥作用的

#todo 等会去最优化笔记里粘一段

# 对偶

> [!def] Banach 空间的对偶
> 对于 Banach 空间 $(X,\|\cdot \|)$, 其对偶是指 $X^*=(\mathcal B(X\to\mathbb C),\|\cdot \|_{\text{op}})$ 其中
> $$\|A\|_{\text{op}}=\|A\|_{\mathcal B(X\to\mathbb C)}=\sup_{x\in X:\|x\|\leq 1}|\lambda (x)|$$
> Banach 空间的对偶也是 Banach 空间, 这由 [[#^003695]] 保证.

此处的结构称为对偶的主要原因是, $X^*$ 中的元素可以视为 $X$ 的线性函数, $X$ 中的元素也可以视为 $X^*$ 上的线性函数 $X^*\ni\lambda\mapsto \lambda(x)\in \mathbb C$, 由于这种对称的结构, 我们后续采用一个更直观的记法: 
$$\begin{align}
X^*\times X&\to \mathbb C\\
(\lambda,x)&\mapsto \mathbb \lambda(x)
\end{align}$$
这个结构几乎就是内积了. 现在我们反过来看这个映射:

> [!thm] $X\subset X^{**}$
> 若 $X$ 为一 Banach 空间, 则映射
> $$\begin{align}J:X&\to X^{**}\\ x&\mapsto T_x:\lambda\mapsto \lambda(x) \end{align}$$
> 为一保范的单射, 其像为 $X^{**}$ 的一子空间 (大概率不是 $X^*$)

`BEGINPROOF`
容易知道
$$\forall x\in X,\lambda\in X^*,|J(x)(\lambda)|=|(x,\lambda)|\leq \|\lambda\|_{\text{op}}|x|\Rightarrow \|J(x)\|\leq \|x\|$$
反过来, 固定一个 $x_0$, 应用 Hahn-Banach 定理, 线性函数
$$X\supset \mathbb Cx_0\ni\alpha x_0\xmapsto{f} \alpha\|x_0\|_X:f(y)\leq \|y\|$$
从而存在 $\lambda_0\in X^*$ 满足
$$\begin{align}
\|\lambda_0\|_{\text{op}}&=\sup\{|\lambda_0(y)|: \|y\|\leq 1\}\\
&\leq \sup\{\|y\|: \|y\|\leq 1\}=1
\end{align}$$
从而证明了等式的反向:
$$\|J(x_0)\|_{\mathcal B(X^*\to\mathbb C)}=\sup_{\tilde \lambda\in X^*:\|\tilde \lambda\|_{\text{op}}\leq 1}\left|\tilde \lambda(x_0)\right|\geq |\lambda_0(x_0)| =\|x_0\|_X$$
其余由 $J$ 的线性性显然.
`ENDPROOF`

## 弱拓扑和弱对偶拓扑

> [!def] weak topology
> 记 $X$ 为一 Banach 空间, 则 $X$ 上的弱拓扑是指能够使所有 $\lambda\in X^*$ 连续的拓扑

Rmk:  拓扑 $\mathcal J_1$ 比 $\mathcal J_2$ 弱是指 $\mathcal J_1\subset \mathcal J_2$, 显然这个弱拓扑比 $X$ 上先天的范数拓扑更弱, 则任意弱连续函数是个范数连续函数, 即其算子范数有限.

具体来说, 这个弱拓扑是由 $\lambda^{-1}\operatorname{Open}(\mathbb C)$ 生成的拓扑, 所以弱拓扑中的开集长这个样子
$$\bigcup_\alpha\bigcap_{j=1}^{n_\alpha}\underset{\in \mathbb X^*}{\lambda_{\alpha,j}^{-1}}\underset{\in\operatorname{Open}(\mathbb C)}{(E_{\alpha,j})}$$
从而对任意 $x\in U$ 其中 $U$ 为一弱开集, 则存在
$$x\in \bigcap_{j=1}^n\lambda_j^{-1}(B_{\varepsilon_j}(z_j))\subset U$$
从而容易推出 (注意有限交)
$$x_0\in\bigcap_{j=1}^n\lambda_{j}^{-1}(B_\varepsilon(\lambda_j (x_0)))\xlongequal{线性性}x_0+\bigcap_{j=1}^n\lambda_j^{-1}(B_\varepsilon(0_\mathbb C))\subset U$$

弱拓扑的另一个视角是讨论收敛条件

> [!def] 弱收敛
> 称 $\{x_n\}$ 弱收敛至 $x$, 是指其在弱拓扑下收敛于 $x$, 且
> $$x_n\xrightarrow{\text{weak}}x\iff \forall \lambda\in X^*,(\lambda,x_n)\to (\lambda,x)$$

> [!thm]
> Banach 空间上任意弱收敛列是范数有界的

`BEGINPROOF`
这是一致有界原则的直接应用, 由线性性我们只讨论收敛到 $0$ 的点列
$$x_n\xrightarrow{\text{weak}}0\iff \forall \lambda\in X^*,(\lambda,x_n)\to 0$$
视 $x_n$ 为 $X^*$ 上的一簇有界线性泛函, 则其依 $n$ 一致有界, 于是依 $\lambda$ 和 $n$ 都一致有界 ([[#^1e566c]]), 从而等价于
$$\exists M>0, \forall \lambda\in B_1(0_{X^*}),n\in \mathbb N,(\lambda,x_n)<M$$
这说明 $x_n$ 范数有界
`ENDPROOF`
下面是弱拓扑的一些性质:

> [!lem]
> 若 $X$ 为一无穷维 Banach 空间, 则任意 $U\in\operatorname{Open}_{\text{weak}}(X)$ 在范数 $\|\cdot\|_{X}$ 下无界, 且拓扑 $\operatorname{Open}_{\text{weak}}(X)$ 不由任意范数导出

^9d3b7b
`BEGINPROOF`
(1) 原因是 $\dim\operatorname{Im}(\lambda_j)\leq1$, 而其局部基仅为有限交, 必然在某个维度上逃逸到无穷
(2) 假设有一度量 $d$ 诱导弱收敛, 由 (1) 容易构造出一列点依度量收敛 (即弱收敛) 到 $0$ 但依范数趋于 $\infty$, 这是不可能的.
`ENDPROOF`


> [!lem]
> Banach 空间依弱拓扑为一 TVS 

`BEGINPROOF`
首先验证 $T_1$, 即独点集是闭集, 即
$$\forall x_0\neq0_X,\exists\varepsilon> 0,\exists \lambda\in X^*:|\lambda(x_0)|>\varepsilon$$
这只需对 $\mathbb C x_0\ni\alpha x_0\mapsto \alpha\|x_0\|$ 应用 Hahn-Banach 定理即可.
加法连续性和数乘连续性显然
`ENDPROOF`

由上讨论, 我们发现 Banach 空间至少可以附上两个拓扑, 一个是范数诱导的拓扑, 另一个是其诱导的弱拓扑, 而弱拓扑不可度量化, 我们从一个 Banach 空间出发, 拿到了两个不同胚的拓扑线性空间, 而在有限维上我们是不能这么干的.

> [!def] 弱对偶拓扑
> 对 Banach 空间 $X$, 称 $X^*$ 上使得任意 $x\in J(X)\subset X^{**}$ (注意不是全体) 连续的拓扑为弱对偶拓扑

则显然 $X^*$ 上的弱对偶拓扑比弱拓扑更弱, 而若 $X$ 是一个自反的空间, 其弱对偶拓扑就是弱拓扑, 事实上反过来也成立

> [!thm]
> 对 Banach 空间 $X$, 若 $X^*$ 上的弱拓扑与弱对偶拓扑等价, 则 $X$ 自反即 $X=X^{**}$

ref: Conwey, p131, thm4.2

## Banach-Alaoglu

我们知道, Banach 空间中的单位球紧当且仅当其有限维, 对于无限维空间, 能否有一个更弱的拓扑使得单位球紧呢, 弱拓扑就是这样一个拓扑

> [!thm] Banach-Alaoglu
> 若 $X$ 为一 Banach 空间, 则
> $$\overline{B_1(0_{X^*})}\subset X^*$$
> 依 $X^*$ 上的弱对偶拓扑是紧的

这个证明太烦人了有空再看
