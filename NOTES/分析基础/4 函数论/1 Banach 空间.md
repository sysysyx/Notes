# 拓扑线性空间

泛函分析是无穷维线性空间中的分析, 我们想要的结构有
- 线性结构 (数的加减和数乘可以自然地推广到函数上)
- 拓扑结构, 或者更强的度量结构

在最理想的情况下, 我们想要把理论建立在这东西上

> [!def] 线性拓扑空间
> 如果线性空间 $X$ 中同时有 $T_1$ 拓扑结构 $\mathcal O$, 并且线性空间中的两种运算加法 ($m_+:X\times X\to X$) 和数乘 ($m_\cdot: \mathbb C\times X\to X$) 依拓扑 $\mathcal O$ 和 $\mathbb C$ 上的通常拓扑是连续映射, 那么称 $X$ 是拓扑线性空间


Examples: 
下面这两个拓扑线性空间不是 Banach 空间
$$\Omega\underset{\text{open}}\subset \mathbb R^n,\qquad C(\Omega),\qquad H(\Omega)$$
(虽然我们还没定义这两个东西上的拓扑)

## 局部基

#todo 对于范数诱导的拓扑, 上述有界的定义和常规定义 ($\exists_{R>0},S\subset B(0,R)$) 等价

研究拓扑线性空间的一般方法是不管对哪个点, 先利用线性结构平移到 $0$ 再处理, 所以一个比较重要的量是 $0$ 处的局部基, 即一个集类
$$\mathcal B\subset \underset{\text{open neighborhood}}{\operatorname{ONbhd}(0_X)}:\forall_{0_X\in U},\exists_{u\in\mathcal B},u\subseteq U$$
这是常规拓扑中 $B_0(\varepsilon)$ 的推广, 在没有度量用的日子里只能靠局部基过过日子这样子

类似度量空间, 我们可以在此定义 Cauchy 列, 即
$$x:\mathbb N\to X:\forall_{V\in\mathcal B},\exists_{N\in\mathbb N},\forall_{n,m>\mathbb N},x_n-x_m\in V$$
这需要验证两件事:
1. 这一定义不依赖局部基的选取
2. 当拓扑由度量诱导出时, 由此定义的 Cauchy 列与常规定义等价

不过我不想验证, 俺寻思这挺对的

> [!lem] 拓扑线性空间中的闭包
> 对于拓扑线性空间 $X$ 的子集 $A$, $\overline A=\bigcap_{U\in\operatorname{ONbhd}(0)}(A+U)$

`BEGINPROOF`
$$\begin{align}
x\in \overline A&\iff \forall_{U\in\operatorname{Nboh}(0)},(x+U)\cap A\neq\emptyset\\
&\iff  \forall_{U\in\operatorname{Nboh}(0)},x\in A-U\\
&\small{(U\in\operatorname{ONbhd}(0)\iff -U\in\operatorname{ONbhd}(0))}\\
&\iff \forall_{U\in \operatorname{ONbhd}(0)}, x\in A+U\end{align}$$
`ENDPROOF`

我们的任务是把之前在 $\mathbb R^n$ 上建立的那套拓扑在这个体系下重新建立一遍

一些术语: 
1. 局部紧/局部凸/局部有界: 指任意点 (由于线性空间结构, 只在 $0$ 处考虑即可) 有紧/凸/有界的开邻域
2. 可度量化/可赋范: 指其拓扑可以由度量/范数诱导出来, 特别地, Frechet 空间是指由平移不变的拓扑诱导出的拓扑线性空间
3. Heine-Borel 性: 是指其中的任意有界闭集都是紧集

称拓扑线性空间 $X$ 的子集 $S$ 是
1. 有界的 (bounded), 如果 $\forall_{N:\ (0\in N)},\exists_{t>0},\forall_{s>t},S\subseteq sN$
2. 星形的 (balanced), 如果 $\forall_{\mathbb C\ni \alpha \leq 1},\alpha S\subseteq S$
3. absorbing, 如果 $\forall_{x\in X},\exists_{t>0},x\in tS$

> [!thm] 分离性
> $$\underset{紧}K,\underset{闭}C\subseteq \underset{拓扑线性空间}X,K\cap C=\emptyset\Longrightarrow\exists_{V\in\operatorname{ONbhd}(0_X)},(K+V)\cap (C+V)=\emptyset$$

注意到 $K+V=\bigcup_{x\in K}\underset{开集}{(x+V)}$ 是开的, 实际上有一步推广 $\overline{(K+V)}\cap (C+V)=\emptyset$
特别地, 如果取 $K=\{0\}$, $C=U^c:U\in\operatorname{ONbhd}(0)$, 那么有 $\overline V\cap U^c=\varphi$, 这就是说
$$\forall_{U\in\operatorname{ONbhd}(0_X)},\exists_{V\in\operatorname{ONbhd}(0_X)},\overline V\subset U$$

**证明思路:**
如果我们有度量可用, 那直接量 
$$d_{\text{min}}=\inf \{d(x,y):x\in K,y\in C\}>0$$
再令
$$V=B_0(d_{\text{min}}/2)$$
将是绝杀, 但是用不得, 我们手头有一个差不多的工具 $\mathcal B$, 先从上述 $K=\{0\}$ 的特殊情况开始, 对这个开集 $U$,  我们想找到一个和 $B_0(d_{\text{min}/2})$ 相似的东西, 即
$$V\in \operatorname{ONbhd}(0_X):V=-V,V+V\subset U$$
我们可以通过把一些满足部分条件的集合交起来拿到想要的东西:
由于加法是连续的, $m_+^{-1}(U)\subset X\times X$ 是开集, 从而存在 $V_1,V_2\underset{开集}\subset U: V_1+V_2\subset W$, 于是我们可以令
$$V=V_1\cap V_2\cap(-V_1)\cap (-V_2)$$
简单验证可知 $V$ 就是我们想要的开集, 从而容易得到
$$(V+V)\cap U^c=\emptyset\xRightarrow{对称}V\cap (U^c+V)=\emptyset\xRightarrow{开集}\overline V\cap U^c=\emptyset$$
(这个结构在 Baire 纲定理的证明中也相当重要, 只有闭的集列才有可能收敛到一个点) 另外我们还可以递归这个流程得到满足
$$V+V+V+V\subset U$$
的对称开集, 这就是说每个开集都可以无限地细分下去

**紧性是有限性的推广**, 把上述这个过程对每个点 $x\in K$ 走一遍, 再利用紧性即可得证

`BEGINPROOF`
$\forall x\in K$ (如果 $K=\emptyset$ 命题显然), $x\not\in C$, $C^c-x\in\operatorname{ONbhd}(0)$ 存在
$$\begin{align}
&V_x+V_x+V_x\subset C^c-x\\
.\xRightarrow{V_x\ 对称}&(x+V_x+V_x)\cap (C+V_x)=\emptyset
\end{align}$$
由于 $K$ 是紧集, 开覆盖 $\bigcup_{x\in X}(x+V_x)$ 有有限的子覆盖 $\bigcup_{i=1}^n(x_i+V_x)$, 记$V=\bigcap_{i=1}^nV_x$, 则
$$K+V\subset \bigcup_{j=1}^n(x_j+V_{x_j}+V)\subset \bigcup_{j=1}^n(x_j+V_{x_j}+V_{x_j})$$
并且 $\bigcup_{j=1}^n(x_j+V_{x_j}+V_{x_j})\cap C+V=\emptyset$
`ENDPROOF`

> [!cor]
> $$E\ 有界\iff \overline E\ 有界$$

我们本来只能拿到 $E\subset tW\Rightarrow \overline E\subset t\overline W$, 但是上述的定理允许我们取更细的限制, 即
$$\forall{V\in\operatorname{ONbhd}(0)},\exists{\operatorname{ONbhd}(0)\ni W\subset N:\overline W\subset N}$$
从而
$$E\ 有界\Rightarrow \exists_{t>0},E\subset tW\Rightarrow\overline E\subset t\overline W\subset tV$$

> [!thm]
> 对任意拓扑线性空间 $X$ 的子集 $U\in \operatorname {Nbhd}(0_X)$, 存在星形集 $\operatorname {Nbhd}(0_X)\ni V\subset U$
> 特别地, 若 $U$ 是凸的, 则也存在凸的 $V$

`BEGINPROOF`
由于**数乘的连续性**, 存在 $\delta>0$, $W\in\operatorname{ONbhd}(0)$ 使得 $\forall_{0<t<\alpha},t W\subset U$ 则 $V=\bigcup_{0<t<\alpha}tW$ 为所求. 假如同时有 $U$ 的凸性, 取 $A=\bigcap_{\alpha\in\mathbb C,|\alpha|=1}\alpha U$, 再如上建立 $V$ 即可保持凸性 (?) #不会qaq 
`ENDPROOF`

利用连续性我们还能得到更多的结论, 对任意 $x\in X$, $U\in\operatorname{ONbhd}(0_X)$, 由于函数
$$\begin{align}
m^\mathbb C_\cdot:\mathbb C&\to X\\
\alpha&\mapsto \alpha x
\end{align}$$
是连续的, 必然存在 $\delta>0$ 使得 $\forall |\alpha|<\delta, \alpha x\in U$, 由此能推出

> [!thm]
> 对拓扑线性空间 $X$
> 1. $\forall U\in\operatorname{ONbhd}(0_X)$ 取 $r_n\to\infty$, 则 $X=\bigcup_{n}r_nU$, 即 $U$ 一定是 absorbing 的
> 2. 所有的紧集是有界的
> 3. 对于 $\delta_n\downarrow 0$ 和有界子集 $U\in\operatorname{ONbhd}(0_X)$, 则 $\{\delta_nU\}$ 是一组局部基

`BEGINPROOF`
1. 只需要取足够大的 $n$ 使 $\frac1{r_n}<\delta$ 
2. 这可以由上述 $U$ 的任意性看出来, 由于紧性, 开覆盖
$$\underset{任意紧集}K\subset \bigcup_{n=1}^\infty r_nU$$
必定有有限的子覆盖
3. 反过来说, 对于 $V\in\operatorname{ONbhd}(0)$ 由 $U$ 的有界性 $\exists_{s>0}, U\subset sV$, 那只要取 $\delta_n<\frac1s$ 即可

**下一步是考虑保持结构的映射**, 同样线性结构允许我们将 $0$ 附近的性质平移到全局

> [!proposition]
> 若 $\Lambda:\underset{拓扑线性空间}{X\to Y}$ 在 $0$ 处连续, 则处处连续

`BEGINPROOF`
取 $U\in\operatorname{open}(Y)$ 往证 $\Lambda^{-1}(U)\in\operatorname{Open}(X)$, 若其为空集立刻证毕, 否则取 $x\in\Lambda^{-1}(X)$
$$\begin{align}
&0_X\in\Lambda^{-1}(U)-x\\
\iff &\Lambda(0_X)=0_Y\in\Lambda(\Lambda^{-1}(U)-x)\xlongequal{线性} U-\Lambda (x)\\
\iff &U-\Lambda(x)\in\operatorname{ONbhd}(0_Y)\\
\xRightarrow{0\ 处连续}&\Lambda^{-1}(U-\Lambda(x))=\Lambda^{-1}(U)-x\in\operatorname{ONbhd}(0_X)
\end{align}$$
`ENDPROOF`

> [!lem] 
> 对线性映射 $\Lambda:\underset{拓扑线性空间}V\to \mathbb C$ 且 $\ker(\Lambda)\neq V$ 以下等价
> - $\Lambda$ 连续
> - $\ker(\Lambda)\in\operatorname{Closed}(V)$
> - $\ker\Lambda$ 在 $V$ 中不稠密
> - $\exists U\in\operatorname{ONbhd}(0)$: $\Lambda(U)$ 有界

我们称一个线性函数是有界的当且仅当其将有界集映到有界集 (这和有界函数是不同的, 有界函数将全空间映到有界集, 不过这么干的话就只有 $0$ 是有界线性映射了)

> [!thm]
> 对于两个线性拓扑空间 $X$, $Y$ 之间的线性映射 $\Lambda:X\to Y$ 以下 $1\Rightarrow 2\Rightarrow 3$
> - $\Lambda$ 是连续的
> - $\Lambda$ 是有界的
> - 若 $x:\mathbb N\to X$ 满足 $\lim_{n\to\infty}x_n=0$ 则 $\{\Lambda x_n\}_n$ 是有界的
> 
> 另外若 $X$ 是可度量化的, 则以上三个等价

^b73170

`BEGINPROOF`
1 => 2
$$\forall W\in\operatorname{Obhd}(0_Y),\exists V\in\operatorname{ONbhd}(0_X):\Lambda V\in W$$
从而对任意有界集 $E$
$$E\subset tV\Rightarrow \Lambda  E\subset \Lambda tV=t\Lambda V\subset tW$$
2 => 3 是天然成立的, 因为 $\operatorname{ONbhd}(0)$ 都是 absorbing 的
加上可度量化条件以后 3 => 1 比较烦人 #todo
`ENDPROOF`
## 度量化和半范数

下面研究拓扑和度量 (范数) 之间的关系

> [!thm] 拓扑线性空间度量化
> 若 $X$ 是一个有可列局部基的拓扑线性空间, 则存在度量 $d:X^2\to [0,\infty)$ 满足
> - $d$ 与 $X$ 上的拓扑兼容;
> - 对任意 $\varepsilon>0$, $B_{\varepsilon}(0_X)$ 是星形的;
> - $d$ 与线性结构兼容 (即平移不变).

这就是说, 一个拓扑线性空间只要有可列的局部基, 就能赋上一个度量变成度量空间
不过这个证明太烦人了, 暂且 #todo

用度量生成范数已经是老生常谈了, 这里是一个不用完整范数也能生成拓扑的方法

> [!thm] 半范数
> 线性空间 $X$ 上的一个半范数是指 $p:X\to[0,\infty)$ 满足
> 1. $p(x+y)\leq p(x)+p(y)$
> 2. $\forall_{\alpha\in\mathbb C}, p(\alpha x)=|\alpha|p(x)$

这就是个和线性结构相容的正值函数, 对此容易证明另一个方向的三角不等式
$$\forall_{x,y},p(x)=p(x-y+y)\leq p(x-y)+p(y)\Rightarrow p(x)-p(y)\leq p(x-y)$$
和 $p(0)=p(0\cdot x)=0p(x)=0$ 所以其实和真正的范数也不差啥了, 唯一的差距就是就是允许在某些非零处取零, 所以对半范数的核的研究比较重要, 这显然是个线性空间, 因为
$$p(x)=p(y)=0\Rightarrow p(x+y)\leq 0+0=0,\forall_\alpha, p(\alpha x)=\alpha\times 0=0$$
所以想要用半范数造一个范数也比较简单, 只要把核商掉就好了

对半范数的定量研究可以借助其 "单位球" $B:\{x\in X:p(x)<1\}$ 既是凸的, 星形的, 又是absorbing 的, 那么我们可以定义 $B$ 的 Minkowski 函数
$$\mu_B(x)=\inf\{t>0:x\in tA\} \quad (x\in X)$$
断言 $p=\mu_B$, 证明就是说车轱辘话:
$$\begin{align}
\forall_{x\in X},\forall_{s>p(x)},x\in sB\Longrightarrow \mu_B(x)\leq p(x)\\
\forall_{x\in X},\forall_{t<p(x)},x\not \in tB\Longrightarrow \mu_B(x)\geq p(x)
\end{align}$$


**下一步是研究半范数之间的关系**

对于一簇半范数 $\mathcal P$, 称其可分是指 $\bigcap_{p\in\mathcal P}\ker p=\{0\}$, 当然这时候我想要用这堆东西凑一个范数出来, 例如 
$$P(x)=\sup_{p\in\mathcal P}\frac{p(x)}{1+p(x)}$$
但是有个问题, 可以想见这个范数会在很多地方取 $1$ (甚至可能是全空间), 所以并不好用, 由此生成的拓扑也毫无意义


> [!thm]
> 假定 $\mathcal P$ 是线性空间 $X$ 上的一簇可分的半范数, 定义
> $$\forall n\in\mathbb N,p\in\mathcal P,V_n(p):=\left\{x\in X: p(x)<\frac1n\right\}$$
> 记 $\mathcal B$ 为 $=\{V_n(p),n\in \mathbb N,p\in\mathcal P\}$ 的所有有限交, 则 $\mathcal B$ 为 $X$ 上一拓扑的凸的, 星形的局部基, 并且满足以下条件
> - 拓扑与线性结构相容, 既 $X$ 是个拓扑线性空间
> - 任意 $p\in\mathcal P$ 是连续的
> - $E\subset X$ 是有界的当且仅当它在任一 $p\in\mathcal P$ 下是有界的

^cc23aa

`BEGINPROOF`
定义 $A\in\operatorname{Open}(X)$ 当且仅当 $A$ 是 $\mathcal B$ 中元素经过可列的平移和并运算得到, 从而这一拓扑自然平移不变且局部基为 $\mathcal B$, 则这个拓扑满足
- $T_1$:
$$\begin{align}
&\forall x\neq0,\exists p\in\mathcal P:p(x)>0\Rightarrow\exists V_n(p):0\not\in x-V_n(p)\Rightarrow x\not\in\overline{\{0\}}\\
&\Longrightarrow\{0\}\in\operatorname{Closed}(X)\xRightarrow{平移不变}T_1
\end{align}$$
- 加法连续: $\forall U\in\operatorname{ONbhd}(0)$, $\exists V_{n_1}(p_1)\cap\cdots\cap V_{n_m}(p_m)\subset U$ 则有 $V:=V_{2{n_1}}\cap\cdots\cap V_{2n_m}$ 使得 $V+V\subset U$.
- 数乘连续: 同上定义 $U$, $V$, 则由单位球的性质 $V$ absorbing 且星形, $\forall x\in X,\alpha\in\mathbb C$, $\exists_{s>0},x\in sV$, 记 $t:=\frac s{1+|\alpha|s}$, 从而
$$\forall_{y\in x+tV},\forall_{\beta:|\alpha-\beta|<1/s},\beta y-\alpha x=\beta(y-x)+(\beta-\alpha)x\in |\beta|tV+|\beta-\alpha|sV\subset V+V\subset U$$
这证明了 $X$ 是个局部凸的拓扑线性空间 $V_n(p)$ 的定义保证了 $p$ 在 $0$ 处连续, 由线性结构知其处处连续, 下面证明判断 3:
利用 Minkskovi 函数, 必要性是显然的, 充分性: 同上定义 $U$, $V$, 则有上界
$$E\subset \max_{i}2n_i\sup p_i|_{E}V\subset CU$$
`ENDPROOF`
用半范数造拓扑的一个例子是开集上的连续函数空间

> [!example]
> 对于 $\Omega\in \operatorname{Open}(\mathbb R^n)\setminus\{0\}$ 存在一列紧集 $K_{\mathbb N}$ 满足
> $$K_n\subset \overset \circ{K}_{n+1},\quad \lim_{n\to\infty}K_n=\Omega$$
> 在 $C(\Omega)$ 上定义一簇半范数
> $$p_n(f)=\sup \{|f(x)|:x\in K_n\}$$
> 显然其零空间上的交是 $\{0\}$, 由 [[#^cc23aa]] 可以由其构造一个局部凸的拓扑
> 事实上这个拓扑是可度量化的, 其度量是
> $$d(f,g)=\max_n\frac{2^{-n}p_n(f-g)}{1+p_n(f-g)}$$
> 这个度量甚至是完备的. 但是这个拓扑不局部有界, 所以它不能赋范.
> 另外 $H(\Omega)$ 是 $C(\Omega)$ 的一个闭子空间

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
将 $S$ 赋予 $L^2$ 中的内积并取出其中的 $n$ 个单位正交元素 $\varphi_1,\cdots,\varphi_n$, $B:=\partial B(0_{\mathbb C^n},1)$, 以及
$$\begin{align}
\psi:B&\to S\\
c&\mapsto \sum_{j=1}^nc_j\varphi_j
\end{align}$$
则 $\|\varphi(c)\|_2\leq \|c\|_{\mathbb C^n}=1$, 从而 
$$\|\varphi(c)\|_\infty\leq M$$
则对任意 $c\in B$, 存在 $\Omega'_c\subset \Omega: \mu(\Omega')=1,\forall_{x\in\Omega},|\psi(c)(x)| \leq M$ 现在固定一点, 取 $B$ 的一个可列稠密子集 $Q$, 则
$$\exists\Omega'\subset\Omega:\mu(\Omega')=1,\forall_{c\in Q},\forall_{x\in\Omega'},|\psi(c)(x)|\leq M$$
并且对固定的 $x\in \Omega'$, $B\ni c\mapsto |\psi(c)(x)|$ 是连续的, 这说明
$$\forall_{c\in B},\forall_{x\in\Omega'},|\psi (c)(x)|\leq M$$
从而
$$\forall_{x\in\Omega},\sum_j|\varphi_j(x)|^2\leq M^2\Rightarrow n=\left\|\sum_{j=1}^n\varphi_j(x)\right\|_2^2\leq M^2\Rightarrow \dim (S)\leq M^2$$
`ENDPROOF`
> 好奇妙的倒来倒去

# 凸性和 Hahn-Banach 定理

> [!thm] $\mathbb R$ Hahn-Banach
> 取 $X$ 为一 $\mathbb R$ 线性空间, 函数 $p:X\to \mathbb R$ 满足
> $$\forall_{x,y\in X},\forall_{\alpha\in[0,1]}, p(\alpha x+(1-\alpha)y)\leq \alpha p(x)+(1-\alpha)p(y)$$
> 若定义在一子空间 $Y\subset X$ 上的线性映射 $\lambda:Y\to\mathbb R$ 满足 $\forall_{x\in Y}\lambda(x)\leq p(x)$, 则存在延拓
> $$\Lambda:X\to\mathbb R:\Lambda|_Y=\lambda,\ \forall_{x\in X},\Lambda(x)\leq p(x)$$

^55a7fc

注意线性延拓存在是平凡的, 关键是仍然被 $p$ 控制

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

> [!thm] Hahn-Banach
> 对线性空间 $X$ 以及其上的凸函数 $p:X\to\mathbb R$, 若有定义在 $Y\subset X$ 上的线性函数 $\lambda:Y\to\mathbb C$ 使得 $|\lambda(x)|\leq p(x)$ 则存在其 $X$ 上的延拓 $\Lambda$ 使得 $\Lambda|_Y=\lambda$ 且 $|\Lambda|\leq p$

`BEGINPROOF`
只需令 $l(x):=\operatorname{Re}(\lambda(x))$ 则 $l(ix)=\operatorname{Re}(i\lambda(x))=-\operatorname{Im}(\lambda(x))$, 从而 $\lambda (x)=l(x)-il(ix)$ 再利用 [[#^55a7fc]] 定理延拓 $l$ 至 $L$, 再令 $\Lambda(x)=L(x)-iL(ix)$ 验证即可.
`ENDPROOF`
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