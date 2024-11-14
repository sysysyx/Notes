本章主要研究形如下式的的波方程的 Cauchy 问题
$$\begin{cases}
\Box u(x,t)=f \\
u(x,0)=u_{0} \\
\partial_{t}u(x,0)=u_{1}
\end{cases}$$
其中 $\Box$ 为 d'Alembertian 算子:
$$\Box\xlongequal\triangle(\partial_{t}^2-\Delta_{x}):$$
$x\in\mathbb R^n$, 本章我们主要关注 $n=2$ 和 $n=3$ 的情形.

# 5.1 显式解

首先可以对问题做一些简化, 对于 $u_0=f=0$ 的情形, 我们记 $u_1$ 对应的上述方程的解为 $u=S(u_1)$, 则 (猜测) 对于一般的 $(u_{0},u_{1})$, 其解可以写作
$$u=S(u_{1})+\partial_{t}S(u_{0})$$
> 可以验证
> $$
\begin{cases}
u(x,0)=S(u_{1})(x,0)+\partial_{t}S(u_{0})(x,0)=u_{0} \\
\partial_{t}u(x,0)=\partial_{t}S(u_{1})(x,0)_{u_{1}}+\partial_{t}^2S(u_{0})(x,0)=u_{1}+\Delta_{x}S(u_{0})(x,0)=u_{1}
\end{cases}
$$

我们对方程的 $x$ 分量作 Fourier 变换 (此处符号滥用)
$$\hat{u}(\xi,t)=\int_{\mathbb R^n}e^{-ix\xi}u(x,t)\ \mathrm{d}x$$
则方程变为
$$\begin{cases}
\partial_{t}^2\hat{u}(\xi,t)+|\xi|^2\hat{u}(\xi,t)=\hat{f}(\xi,t) \\
\hat{u}(\xi,0)=\hat{u}_{0}(\xi,0) \\
(\partial_t\hat{u})(\xi,0)=\hat u_{1}(\xi)
\end{cases}$$
此处要求 $u_{0},u_{1},f$ **充分下降**以使 $(\hat{\Delta_{x}u})(\xi,t)=|\xi|^2\hat{u}(\xi,t)$, 这可以由具体的计算看出

而这是一个关于 $t$ 的 ODE, 可以设
$$\hat{u}(\xi,t)=A(\xi,t)\cos t|\xi|+B(\xi,t)\sin t|\xi|$$
再令 $\partial_{t}A\cos t|\xi|+\partial_{t}B\sin t=0$, 则有 $-\partial_{t}A\sin t|\xi|,+\partial_{t}B\cos t|\xi|=\frac{\hat{f}}{|\xi|}$

> 算的时候会发现 $|\xi|^2\hat{u}(\xi,t)$ 被约掉了, 这个换元带来的另一个巧合是初值的情形

后两个初值方程变为
$$A(\xi,0)=\hat{u}_{0}(\xi)\qquad B(\xi,0)=\frac{\hat{u}_{1}(\xi)}{\xi}$$
联立就能解出

> [!thm]
> 若 $u_{0},u_{1},f$ 随 $x\to \infty$ 充分下降, 则解
> $$\hat{u}(\xi,t)=\hat{u}_{0}(\xi) \cos t|\xi|+\hat{u}_{1}(\xi) \frac{\sin t|\xi|}{|\xi|}+\int_{0}^t \hat{f}(\xi,s) \frac{\sin(t-s)|\xi|}{|\xi|}\ \mathrm{d}s$$

从这个式子里能看出一些有意思的东西, 一是刚才的 $S(v)$ 可以带入写出来
$$\hat{S(v)}(\xi,t)=\hat{v}(\xi) \frac{\sin t|\xi|}{|\xi|}$$
从而也能验证对一般的 $(u_{0},u_{1})$ 的表示, 这个式子又"碰巧"长的和上面那个积分式里的东西长得很像, 这个事实被称作 Duhamel 原则

> [!thm] Duhamel principle
> 初值为 $0$, 右侧为 $f$ 的 Cauchy 问题的显式解为
> $$u(x,t)=\int_{0}^t S(f(\cdot,t))(x,t-s)\ \mathrm{d}s$$

^b42ac8

由 [[#^b42ac8]], 我们只需要求出 $S(v)$ 即可, 下面具体到三维和二维的情形, 我们引入球面平均的方式表述这个解, 

> [!thm]
> $n=3$ 时
> $$S(v)(x,t)= \frac{t}{4\pi}\int_{|y|=1}v(x-ty)\ \mathrm{d} \sigma_{1}$$
> 其中  $\mathrm{d}\sigma_{R}$ 为半径为 $R$ 的球表面面积元

这是容易理解的, 因为波是一点开始以球面的形式向外传播, 同时对一点有影响的波的初值也构成一个球面, 直观的说, $S(v)$ 在一点的值为函数 $v$ 在 $B(x,r)$ 上的球面平均的 $t$ 倍

`BEGINPROOF`
我们知道
$$\hat{S(v)}(\xi,t)=\hat{v}(\xi) \frac{\sin t|\xi|}{|\xi|}$$
所以只需证
$$(\mathrm{d}\hat{\sigma}_{R})(\xi)=4\pi R \frac{\sin t|\xi|}{|\xi|}$$
做球面换元容易得到
`ENDPROOF`

对于二维的情形, 可以采用降维法, 即将其视作三维解的与 $x3$ 无关的一特殊情况, 由此立刻得到

> [!thm]
> $n=2$ 时
> $$S(v)(x,t)= \frac{1}{2\pi}\int_{|y|\leq t}v(x-y)(t^2-|y|^2)^{- 1/2}\ \mathrm{d}y$$

## 对解的一些分析

**有限速度传播**:

> [!thm]
> $n=3$ 时, $S(v)$ 在点 $(x,t)$ 的值仅被 $v$ 在球面 $\partial B(x,t)$ 上的值唯一确定
> $n=2$ 时, $S(v)$ 在点 $(x,t)$ 的值被 $v$ 在圆 $\overline {B(x,t)}$ 的值唯一确定

可以认为这是波方程信息传播速度的上限, 

**决定域**: 从另一个视角看, 解在某点的值受到一个被截断的锥的控制, 我们将其定义为决定域

> [!def] 决定域 domain of determination
> 若闭域 $D\subset \mathbb R^n_{x}\times[0,\infty]$, $\omega=\{(x,0)\in D\}$, 称 $D$ 为基 $\omega$ 的决定域, 如果对任意 $(x,t)\in D$, 锥 $C_{x,t}=\{(y,s),0\leq s\leq t,|y-x|\leq t-s\}$  在 $D$ 内部, 则称 $D$ 为基 $\omega$ 上的一决定域

用决定域的语言表述有

> [!cor]
> 对于基 $\omega$ 上的一决定域 $D$, 若 $u\in C^2(D)$ 为 $D$ 上一 Cauchy 问题的解, 其对应的 $f=0$, $u_{0},u_{1}=0$ 则 $u=0$


**强惠更斯 (Huygens) 原则**: 在 $n=3$ 时, 对解有影响的区域可以缩到更小, 只有一层球面, 其内部会留下一块空腔(lacuna)

举例来说, 若初值仅在 $|x|<M$ 处非零, 则解不仅在 $|x-t|>M$ 处非零, 还在一顶点为 $(x,M)$ 的倒立锥内非零



在 section 6.6 我们会应用到这个性质.

**渐进性质**

> [!thm]
> 对于 $n=3$ 的情形, Cauchy 问题的解 $u=S(v)$, 若有 $v\in C^{\infty}$ 在 $|x|>M$ 处取 $0$ 则通过极坐标变换
> $$r=|x|,x=r\omega$$
> 对于 $t>2M$ 有表示
> $$u(x,t)= \frac{1}{r}F\left( r-t,\omega, \frac{1}{r} \right)$$
> 其中
> $$F(\rho,\omega,z)\in C^\infty\left( \mathbb R\times S^2\times\left[ 1, \frac{1}{M} \right] \right)$$
> 在 $|\rho|\geq M$ 处取 $0$

`BEGINPROOF`
做变换 $\rho=r-t$, 由上述讨论已知 $\rho>0$ 时 $F=0$

为方便记, 先假设 $x=r(1,0,0)$

对于 $|\rho|<M$, $t$ 比较大时 $r$ 也比较大, 对点 $(x,t)$ 有影响的部分 $B(x,t)$ 与 $B(0,M)$ 相交的部分非常小, 具体可以写成 $(r-\sqrt{ t^2-|y|^2 },y)$ 从而 $\mathrm{d}\sigma_{t}=t\sqrt{ t^2-|y|^2 }$ 非常接近 $\mathrm dy$
$$\begin{align}
S(v)(x,t)&=(4\pi)^{-1}\int_{|y|\leq M}v(r-(t^2-|y|^2)^{1/2},y)\sqrt{t^2-|y|^2}\mathrm{d}y
\end{align}$$
其中只有 $t$ 一个元素不是我们希望的情形, 而我们有
$$r-\sqrt{ t^2-y^2 }=\left[  1+\sqrt{ \left( 1-\frac{\rho}{r} \right)^2- \frac{|y|^2}{r^2} } \right]\left[ 2\rho+ \frac{|y|-\rho^2}{r} \right]$$
为一 $\left( \rho, \frac{1}{r}, y \right)$ 的 $C^\infty$ 函数

另一方面, 若假定 $x=r\omega$ 同样能得到一 $C^\infty$ 函数
`ENDPROOF`
从中能获得的一个非常重要的观察是解在以大概 $t^{-1}$ 的速率衰减, 在非线性情形尤其有用.

而对于 $r=\infty$ 即 $z=0$ 的情形, 初值 $F_{0}(\rho,\omega)=F(\rho,\omega,0)$ 满足
$$4\pi F_{0}(\rho,\omega)=\int_{\omega \cdot y=\rho}v(y)\ \mathrm{d}y$$
为 $v$ 的 Radon 变换

对 $n=2$ 的情形也有类似结论

> [!thm]
> 对 $n=2$ 的情形, 若 $v\in C_0^{\infty}$
> $$S(v)(x,t)=r^{-1/2}F\left( r-t,\omega, \frac{1}{r} \right)$$
> 且 $F$ 为一 $C^{\infty}$ 有界函数



# 5.2 波方程的几何

本节实际上定义了一堆微分算符, 关键是构造处一个叫做 Lorentz vector fields 的空间, 包括:
- 旋转
- 双曲旋转
- 放缩

## 5.2.1 旋转和放缩

暂且抛开方程, 仅关注空间 $\mathbb R^2_{x}$ 和 $\mathbb R_{x}^3$

**平面上**, 有极坐标变换
$$x=r\cos\theta\quad y=r\sin\theta\quad r=\sqrt{ x^2+y^2 }\quad \omega=(\cos\theta,\sin\theta)$$
对于 $u\in C^1(\mathbb R^2)$ 若有 $v(r,\theta)=u(r\cos\theta,r\sin\theta)$ 则
$$\begin{align}
r\partial_{r}v(r,\theta)&=(x\partial _{x}u+y\partial_{y}u)(r\cos\theta,r\sin\theta ) \\
\partial_{\theta}v(r,\theta) &= (x\partial_{y}u-y\partial_{x}u)(r\cos \theta,r\sin \theta)
\end{align}$$
后续简写作
$$S\xlongequal \triangle r\partial_{r}=x\partial_{x}+y\partial_{y}\qquad R\xlongequal \triangle \partial_{\theta}=x\partial_{y}-y\partial_{x}$$
$S$ 和 $R$ 即为放缩向量场和旋转向量场, 其积分曲线分别是射线 $t\mapsto e^tm_{0}$ 和圆周 $t\mapsto (x_{0}\cos t-y_{0}\sin t,x_{0}\sin t+y_{0}\cos t)$

由于向量
$$(\cos\theta,\sin\theta),\qquad (-\sin\theta,\cos\theta)$$
构成平面的一组正交基, 这时我们说
$$\partial_{r}=\cos\theta \partial_{x}-\sin\theta \partial_{y}\qquad r^{-1}\partial_{\theta}=-\sin\theta\partial_x+\cos\theta\partial_{y}$$
在每个点 $(x,y)$ 构成一组**正交标架**

我们还需要讨论这些新的微分算符和原有算符的交换性 (Lie 括号), 直接计算可得$$[R,\partial_{r}]=0,\quad [R,\Delta]=0,\quad [S,\Delta]=-2\Delta$$
其中 Lapalce 算子的在极坐标下
$$\Delta=\partial r^2+r^{-1}\partial_{r}+r^{-2}\partial_{\theta}^2$$

**空间上**, 极坐标变换
$$x_{1}=r\sin \phi \cos \theta\quad x_{2}=r\sin \theta \cos \phi\quad x_{3}=r\cos \phi$$
放缩同样为 $S=\sum_{i}x_{i}\partial_{i}$ 积分曲线同样为射线, 而旋转按平面的写法有三个
$$R=x\wedge \partial,\qquad R_{1}=x_{2}\partial_{3}-x_{3}\partial_{2},\quad R_{2}=x_{1}\partial_{3}-x_{3}\partial_{2},\quad R_{3}=x_{1}\partial_{2}-x_{2}\partial_{1}$$
我们只需要保留其中两个, 选择
$$\partial_{\theta}=R_{3},\partial_{\phi}=-\sin\theta R_{1}+\cos\theta R_{2}$$
可以覆盖除了 $x_3$ 轴的全部情况

对任意一点, 同样有正交标架
$$\partial_{r},\quad e_{\theta}=(r\sin\theta)^{-1}\partial_{\theta},\quad e_{\phi}=r^{-1}\partial_{\phi}$$
常规的标架在此标架下分解为
$$\partial=\omega \partial_{r}-\omega \wedge\left( \frac{R}{r} \right)$$
直接计算即可验证
$$\left( \omega \wedge \frac{R}{r} \right)_{1}=\omega_{2} \frac{R_{3}}{r}-\omega_{3} \frac{R_{2}}{r}=-\partial_{1}+\omega_{1}\partial_{r}$$
有时我们用简写 $\bar\partial_{i}=-\partial_{i}+\omega_{i}\partial_{r}$, 这表示一个切球的方向, 且有分解
$$\sum_{i}(\partial_{i}u)^2=(\partial_{r}u)^2+\sum_{i}(\bar{\partial}_{i}u)^2=(\partial_{r}u)^2+ \left| \frac{R}{r}u \right|^2$$
同样计算交换子
$$[R_{i},\partial_{i}]=0,\quad [R_{i},\Delta_{i}]=0,\quad [S,\Delta]=-2\Delta$$
为表示球极坐标分解下的 Lapalce 算子
$$\Delta_{\omega}=\sum R_{i}^2,\quad \Delta=\partial_{r}^2+ \frac{2}{r}\partial_{r}+r^{-2}\Delta_{\omega}$$
其中 $\Delta_\omega$ 称为单位球面上的 Lapalce 算子, 并且
$$\Delta_{\omega}=\partial_{\phi}^2+[(\sin \phi)^{-1}\partial_{\theta}]^2+ \frac{\cos{\phi}}{\sin \phi}\partial_{\phi}$$
(tedious computation)

## 5.2.2 双曲旋转和洛伦兹域

双曲旋转就是考虑时间的旋转, 考虑
$$H_{i}=t\partial_{i}+x_{i}\partial_{t},\quad i=1,\cdots,n$$
这一向量场代表的标架 $(t,x_{i})$ 恰好切双曲线 $t^2-x^2=C$ 所以称作双曲旋转, 而这一双曲线某种程度上对应了 d'Almbert 算符 $\Box=\partial_{t}^2-\Delta$

双曲旋转的最基本性质是
$$[H,\Box]=0$$
我们定义 Lorentz vector fields 为
- 常规的 $\partial_{t},\partial_{i}$
- 所有的旋转 $R$
- 双曲旋转 $H$
- 放缩 $S=t\partial_{t}+\sum x_{i}\partial_{i}$

总结来说

> [!thm]
> 所有的 Lorentz vector fields 都与波算子交换, 除了 $S$:
> $$[\Box,S]=2\Box$$

## 5.2.3 光锥, 空标架 (Null frame), 好微分形式

在上一节中我们知道了锥 $C_{x,t}$ 的重要性, 这一小节中主要关注其反方向的锥 $\{t-r=C\}$. 本节以 $n=3$ 为例, $n=2$ 的情形更加简单. 首先定义
$$L=\partial_{t}+\partial_{r}\qquad \underline{L}=\partial_{t}-\partial_{r}$$
则正交基
$$(L,\underline L,e_{\theta},e_{\phi})$$
称作一个 Null frame, 在任意点 $(x_{0},,t_{0})$, $(L,e_{\theta},e_{\phi})$ 构成锥 $\{x-t=x_{0}-t_{0}\}$ 的切空间.

举例说明介绍这组标价的意义: 考虑 $u=S(v)$ 其中 $v\in C^\infty$, 且在 $|x|>M$ 处取 $0$, 由上节我们有表示
$$u(x,t)=r^{-1}F\left( r-t,\omega, \frac{1}{r} \right)$$
且 $F\in C^{\infty}$ 对这一函数
$$\begin{align}
\underline Lu&=-2r^{-1}(\partial_{\rho}F)\left( r-t, \omega, \frac{1}{r} \right)+O(r^{-2}) \\
Lu&=O(r^{-2})\quad \left( \frac{R}{r} \right)u=O(r^{-2})
\end{align}$$
这就是说随着 $t\to \infty$, $\underline Lu$ 大致以 $t^{-1}$ 变化, 其余方向上大致以 $t^{-2}$ 变化, 我们就将这些分别称作 "坏的" 和 "好的" 微分形式. 这种好坏在和 Lorentz vector field 共同出现的时候体现的非常明显

> [!thm]
> 存在常数 $C$ 满足 $\forall u\in C^1(\mathbb R^n_{x}\times\mathbb R_{t}^+)$
> $$\begin{align}
> (1+r+t)|(Lu)(x,t)|&\leq C\left( \sum_{\text{Lorentz}}|Zu| \right)(x,t) \\
> (1+r+t)|r^{-1}(R_{i}u)(x,t)|&\leq C\left( \sum_{\text{Lorentz}}|Zu| \right)(x,t)  \\
> (1+|r-t|)|(\underline Lu)|&\leq C\left( \sum_{\text{Lorentz}}|Zu| \right)(x,t) \\
> (1+|r-t|)|(\partial u)(x,t)|&\leq C\left( \sum_{\text{Lorentz}}|Zu| \right)(x,t) 
> \end{align}$$
> 其中 $\partial$ 表示 $\partial_{t}$ 或 $\partial_{i}$

^e01195

> 这个后边有用不要擦

`BEGINPROOF`
$$\begin{align}
\sum\omega_{i}H_{i}=t\partial_{r}+r\partial_{t},&\quad S=t\partial_{t}+r\partial_{r} \\
\quad (r+t)L=\sum \omega_{i}H_{i}+S, &\quad (r-t)\underline L=\sum\omega_{i}H_{i}-S \\
(t+r) \frac{R}{r}=R+\omega\wedge H
\end{align}$$
`ENDPROOF`

这些控制非常有用的一个重要原因是 Lorentz vector field 和 d'Almbert 算符的交换性很好, 但是 $L, \frac{R}{r}$ 不是. 

假如我们有控制
$$|Zu|(x,t)\leq M(x,t)$$
并且函数 $M$ 在无穷远点趋于 $0$, 带入上式我们就会发现这些 "好的" 微分在无穷远点比 $M$ 下降速度快一个因子 $(1+r+t)$ 但是这个 "坏的" 微分 $\underline Lu$ 只在远离光锥 $t=r$ 处下降更快.

研究 Lorentz 域的一个作用是研究可变参数的波方程 (Cpt7) 或者非线性波方程的定性性质. 对于一个和 $\Box$ 差不多的算子 $P$, 他可能和 $Z$ 不交换, 但是我们可以试图控制 $[P,Z]$ 为一小量, 这并不依赖解的具体形式.

## 5.2.4 Klainerman 不等式

考虑非线性情形
$$\Box u=F(u,\partial u)$$
我们想讨论解全局上的存在性, 就需要对较大的 $t$ 对应的 $|u(x,t)|$ 有较好的控制


> [!lem] Sobolev 引理
> 对任意正整数 $m> \frac{n}{2}$, 存在常数 $C_{n,m}$ 使得 $\forall u\in S(\mathbb R_{x}^n)$ 则
> $$\|u\|_{L^\infty}\leq C_{n,m}\sum_{|a|\leq m}\|\partial_{x}^\alpha u\|_{L^2}$$

^2a0845

`BEGINPROOF`
> 这段证明对常数 $C$ 的使用及其混乱, 几乎个个不同

由于 Fourier 变换
$$\widehat{\partial_{x}^\alpha u}(\xi)=i^{|\alpha|}\xi^\alpha \hat{u}(\xi)$$
由 Plancherel 定理, 函数的 $L^2$ 范数应该能被其 Fourier 变换的 $L^2$ 范数控制住
$$A\xlongequal\triangle \sum_{|\alpha|\leq m}\|\partial_{x}^\alpha u\|_{L^2}^2\geq C\int\left( 1+\sum \xi_{i}^{2m} \right)|\hat{u}(\xi)|^2\mathrm{d}\xi$$
> 后面扔掉了一些项, 原书里写 $A^2$ 应该是个 typo

将 $\hat{u}$ 写成
$$\hat{u}<\underbrace{[\hat{u}(1+|\xi|^{2m})^{1/2}]}_{L^2\text{ norm }\leq C'A}\underbrace{(1+|\xi|^{2m})^{-1/2}}_{L^2}$$
第一个括号的判断是由于 $1+|\xi|^{2m}\leq C\left( 1+\sum \xi_{i}^{2m} \right)$, 综上, 由 Fourier 变换和 Holder 不等式
$$\|u\|_{L^\infty}\leq C\|\hat{u}\|_{L^1}\leq CA$$

`ENDPROOF`

在 Sobolev 引理中, 我们用 $\partial_{x}^\alpha$ 控制了 $u$, 在 Klianerman 不等式中, 我们将试图用 Lorentz 域中的元素作用出的结果控制 $u$:

> [!thm] Klainerman 不等式
> 存在常数 $C$ 使得 $\forall u\in S(\mathbb R_{x}^n\times [t-1,t+1])$
> $$(1+t+r)^{n-1}(1+|t-r|)|u(x,t)|^2\leq C\sum_{0\leq k\leq \frac{n+2}{2}}|(Z^ku)(\cdot,t)|^2_{L^2}$$
> 其中 $Z^k$ 表示任意 $k$ 个 Lorentz vector field 的乘积, 并且全部计入求和
>

`BEGINPROOF`

我们首先引入局部的 Sobolev 引理

> [!lem]
> $\forall\delta>0,\exists C_{\delta},\forall f\in C^\infty(\mathbb R^n)$
> $$|f(0)|^2\leq C_{\delta}\sum_{|\alpha|\leq \frac{n+2}{2}}\int_{|y|<\delta}|\partial^\alpha f(y)|^2\mathrm{d}y$$
> 其中 $C_{\delta}$ 可以取 $C_{n}(1+\delta^{-n-2})$

^3e4de6

`BEGINPROOF`
取核 $\chi\in C_{0}^\infty(\mathbb R^n)$, $\operatorname{supp}(\chi)\subset B(0,1)$, $\chi(0)=1$, 并对
$$\chi_{\delta}(y)f(y)=\chi\left( \frac{y}{\delta} \right)f(y)$$
使用 [[#^2a0845]] 得到
$$|f(0)|^2\leq C\sum_{|\alpha|\leq \frac{n+2}{2}}\int_{\mathbb R^n}|\partial^\alpha(\chi_{\delta}(y)f(y))|^2\mathrm{d}y\leq C(1+\delta^{-n-2})\sum_{|\alpha|\leq \frac{n+2}{2}}\int_{|y|<\delta}|\partial^\alpha f(y)|^2\mathrm{d}y$$
`ENDPROOF`
然后将其应用与 $S^{n-1}$ 上, 立刻得到

> [!lem]
> (a) $u\in C^\infty(S^{n-1})$ 则
> $$|u(\omega)|^2\leq C\sum_{|\alpha|\leq \frac{n+1}{2}}\int_{\mathbb S^{n-1}}|(\bar{\partial}^\alpha u)(\eta)|^2\mathrm{d}\sigma(\eta),\quad \forall\omega\in\mathbb S^{n-1}$$
> (b) $\forall\delta>0,\forall v\in C^\infty(\mathbb R\times\mathbb S^{n-1})$
> $$|v(\omega,r)|^2\leq C_{\delta}\sum_{j+|\alpha|\leq \frac{n+2}{2}}\int_{|\rho|<\delta}\int_{\eta\in\mathbb S^{n-1}}|\partial_{r}^j\bar{\partial}^\alpha v(\rho+r,\eta)|^2d\sigma(\eta)d\rho$$
> 并且 $\sup_{\delta\geq\delta_{0}}C_{\delta}<\infty,\forall\delta_{0}$

^8d2fbd

对于 $t+|x|<1$ 的情形 (就是前面的系数有个有限的控制, 未必是 $1$), 上式直接是 [[#^3e4de6]], 我们假定 $t+|x|>1$

Case1: $r\leq \frac{t}{2}$ 或 $r\geq \frac{3t}{2}$ 

对函数
$$y\mapsto u(t,x+(t+|x|)y)$$
应用 [[#^3e4de6]] 得到
$$\begin{align}
|u(x,t)|^2&\leq C\sum_{|\alpha|\leq \frac{n+2}{2}}\int_{|y|< \frac{1}{8}}|\partial_{y}^\alpha(u(t,x+(t+r)y))|^2\mathrm{d}y \\
&=C\sum_{|\alpha|\leq \frac{n+2}{2}}(t+r)^{2|\alpha|-n}\int_{|y|< \frac{t+r}{8}}|(\partial_{x}^\alpha u)(t,x+y)|^2\mathrm{d}y
\end{align}$$
我们希望借助 [[#^e01195]] 控制 $\partial_{x}^\alpha u(t,x+y)$ 而这需要点 $(t,x+y)$ 离光锥很远,  这也是为什么之前取系数 $\frac{1}{8}$:
$$|y|< \frac{1}{8}(t+|x|) \implies |t-|x+y||\geq \frac{3}{40}(t+|x|)$$
从而
$$\begin{align}
(t+r)^n|u(t,x)|^2&\leq C\sum_{|\alpha|\leq \frac{n+2}{2}}\int_{|y|< \frac{t+r}{8}}|(Z^\alpha u)(t,x+y)|^2\mathrm{d}y\leq C\sum_{|\alpha|\leq \frac{n+2}{2}}\|Z^\alpha u(t,\cdot)\|_{L^2}^2
\end{align}$$

case2: $\frac{t}{2}<r< \frac{3t}{2}$ 书中给出了一个简明的对于 $n=3$ 的证法, 这里简述任意的 $n$ 的证法

做换元
$$x=r\omega\quad q=r-t,\qquad v(t,q,\omega):=u(t,(t+q)\omega)$$
 则
 $$\partial_{q}v=\partial_{r}u,\quad \partial_{\omega}^\alpha v=\bar{\partial}^\alpha u$$
 又由 $\frac{t}{2}<r< \frac{3t}{2}\iff |q|< \frac{t}{2}$,只需证
 $$t^{n-1}(1+|q_{0}|)|v(t,q_{0},\omega)|^2\leq C\sum_{|\alpha|\leq \frac{n+2}{2}}\|Z^\alpha u(\cdot,t)\|_{L^2}^2,\quad\forall|q_{0}|< \frac{t}{2},\omega\in\mathbb S^{n-1}$$

这里再切一刀, 对于 $|q_{0}|\leq1$, 由 [[#^8d2fbd]] (2) 可以给出限制 (依托计算)
$1\leq|q_{0}|< \frac{t}{2}$ 的情形, 利用核 $\chi\in C_{0}^\infty\left( -\frac{1}{2}, \frac{1}{2} \right)$, $\chi(0)=1$
$$V_{q_{0}}(t,q,\omega):=\chi\left( \frac{q-q_{0}}{q_{0}} \right)v(t,q,\omega)$$
再对
$$\mathbb S^{n-1}\times R\ni(\eta,q)\mapsto V_{q_{0}}(t,q_{0}+q_{0}q,\eta)$$
应用 [[#^8d2fbd]] 即可得到限制
`ENDPROOF`