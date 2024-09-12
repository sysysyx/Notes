某种来自远古数学人的恐怖符号计算

> [!ref]
> - [1加到100等于多少？从伯努利数到欧拉麦克劳林公式](https://www.bilibili.com/video/BV1wW421A75k/?share_source=copy_web&vd_source=10973e643a3adfd2c482399e0cf9310b)
> - 《解析与概率数论导引》 G. 特伦鲍母
> - [北京某高校《应用分析》（第二周、第一讲、第二小节）]( https://www.bilibili.com/video/BV1Yg4y1J7Ud/?share_source=copy_web&vd_source=10973e643a3adfd2c482399e0cf9310b)

> [!notation]
> 本节中用 $\mathscr O$ 表示不超过 1 的实数, 用于估计
> 本节的积分通常采用 Lebesgue-Stieltjes 积分

# Abel 求和公式
	果然这一部分东西放在这里最容易接受qwq

Abel 变换是一个处理求和乘积的常规思路, 对两个数列 $\{a_n\}_{n\in\mathbb N}$, $\{b_n\}_{n\in\mathbb N}$.
$$\sum_{N<n\leq N+M}a_nb_n=A_{N+M}b_{N+M+1}+\sum_{N<n\leq N+M}A_n(b_n-b_{n+1})$$



# 求和问题和伯努利数

## 递归定义

研究形如
$$S_m(n)=\sum_{i=1}^ni^m$$
的经典问题, $m$ 比较小时
$$\begin{align}
1+2+\cdots+n&=\frac{n(n+1)}{2}\\
1^2+2^2+\cdots+n^2&=\frac{n(n+1)(n+2)}{6}
\end{align}$$
可以分别通过倒过来加一次和写成三角形转一圈加算出来, 但是这个方法不好推广, 想要算更高阶的结果可以利用
$$n^m=\sum_{i=1}^ni^m-(i-1)^m
=\sum_{i=1}^n\sum_{j=0}^{m-1}\begin{pmatrix}m\\j\end{pmatrix}i^j=\sum_{j=0}^{m-1}\begin{pmatrix}m\\j\end{pmatrix}S_j(n)$$
得到递归式: 
设 $S_i(n)=\sum_{j=1}^{i}b_{ij}n^{j-1}$, $a_{ij}:=\begin{pmatrix}i\\ j-1\end{pmatrix}$, $B$, $A$ 分别为 $b_{ij}$, $a_{ij}$ 组成的下三角矩阵, 则
$$\begin{pmatrix}
a_{11}\\
a_{21}&a_{22}\\
\vdots&& \ddots\\
a_{n1}&a_{n2}&\cdots& a_{nn}
\end{pmatrix}\begin{pmatrix}
S_0\\ S_1\\\vdots\\S_k
\end{pmatrix}=\begin{pmatrix}
n\\ n^2 \\ \vdots \\n^k 
\end{pmatrix}\Rightarrow B=A^{-1}$$
下一步是把这个 $A$ 的逆求出来, 但这个显然不太现实, 实际上也没有用组合数简单表出的公式, 首先集中注意力进行一个找规律

$$\begin{align}
S_0(n)&=n\\
S_1(n)&=\frac12(n^2-\frac12\times 2n)\\
S_2(n)&=\frac13(n^3-\frac12 \times 3n^2+\frac16\times \begin{pmatrix}3\\2\end{pmatrix}n)\\
S_3(n)&=\frac14(n^4-\frac12\times 4 n^3+\frac16\times \begin{pmatrix}4\\2\end{pmatrix}n^2+0\times \begin{pmatrix}4\\3\end{pmatrix}n)\\
S_4(n)&=\frac15(n^5-\frac12\times 5n^4+\frac16\times \begin{pmatrix}5\\2\end{pmatrix}n^3+0\times \begin{pmatrix}5\\3\end{pmatrix}n^2-\frac1{30}\begin{pmatrix}5\\4\end{pmatrix}n)\\
&\cdots
\end{align}$$
可以看到, 除了一些系数, 其它项的规律是很显著的. 但是有一些比较哈人的项不能写成一些组合数的简单运算
$$\begin{matrix}
1&-\frac12&\frac16&0&-\frac1{30}&\cdots
\end{matrix}$$
这就是被称为组合数学中的圆周率的伯努利数, 其递推容易写出
$$B_p=I_{[p=0]}-\sum_{k=0}^{p-1}\begin{pmatrix}m\\ k\end{pmatrix}\frac{B_k}{m-k-1}$$
但是却没有简单的通项. 利用这个可以把 $S_m$ 写出来:
$$S_m=\frac{1}{m+1}\sum_{i=0}^{m}\begin{pmatrix}m+1\\ i\end{pmatrix}B_{i} n^{m-i+1}$$

## 生成函数定义

利用生成函数可以更容易的计算这个求和, 设
$$\begin{align}
g(z)&=\sum_{j=0}^\infty \frac{z^j}{j!}\sum_{i=0}^{n-1}i^j\xlongequal{*}\sum_{i=0}^{n-1}\sum_{j=0}^\infty \frac{(iz)^j}{j!}\\
&=\sum_{i=0}^{n-1}e^{iz}=\frac{e^{nz}-1}{e^{z}-1}\\
&=\underbrace{\frac{z}{e^{z}-1}}_{h(z)}\frac{e^{nz}-1}{z}
\end{align}$$
此处若将伯努利数定义为生成函数为 $h(z)$ 的形式幂级数的通项就能得到
$$\begin{align}
g(z)&=\sum_{p=0}^\infty\frac{B_p}{p!}\sum_{q=0}^\infty\frac{n^{q+1}z^q}{(q+1)!}=\sum_{j=0}^\infty\frac{z^j}{j!}\sum_{p=0}^j\begin{pmatrix}j+1\\ p\end{pmatrix}\frac{B_pn^{j-p+1}}{j+1}
\end{align}$$
比较二者可知
$$\sum_{i=0}^{n-1}i^j=\sum_{p=0}^j\begin{pmatrix}i+1\\ p\end{pmatrix}\frac{B_pn^{j-p+1}}{j+1}$$
这与我们在前半部分算出的结果相符

严格定义一下伯努利数

> [!def] 伯努利数
> - 是满足递归关系
> $$B_p=I_{[p=0]}-\sum_{k=0}^{p-1}\begin{pmatrix}m\\ k\end{pmatrix}\frac{B_k}{m-k-1}$$
> 且首项为 $1$ 的数列
> - 或等价的, 生成函数为
> $$\frac{z}{e^z-1}$$
> 的数列

容易观察到, 除了 $B_1=-\frac12$, 其余奇数项为 $0$

再盯着递推式看看, 可以看到某种和二项式定理很像的东西
$$(B+1)^n=B^n$$
按照二项式定理展开后, 再将上标挪到下标就能得到所需的递推式, 这也不难理解, 看看上面的递推就能发现形式差不多


## 伯努利函数

上面这个式子暗示了伯努利数的某种非常规整的结构, 利用这种把上标扔到下标的诡异运算我们还能把等幂求和公式写的更规矩一些: 定义伯努利多项式
$$B_k(x)=\downarrow(B+x)^k$$
其中 $\downarrow$ 表示把上标转下标这一操作, 在最后进行, 那么可以写出
$$S_k(n)=\frac{B_{k+1}(n)-B_{k+1}(0)}{k+1}$$
更神奇的是, 这个式子长得很像积分
$$\int_0^n x^k=\frac{n^{k+1}-0^{k+1}}{k+1}$$
也就是说
$$\sum_{x=1}^nx^k=\downarrow \frac1{k+1}[(B+n)^{k+1}-B^{k+1}]=\downarrow \int_B^{B+n}x^k\ dx$$
(但是我们上边的讨论实际上只允许把后边的东西展开写回去而不能保证其它运算后仍然有此性质, 所以这式子并没比一个简记强多少)

同时我们还可以由伯努利多项式出发得到一套伯努利数的定义, 递归地定义伯努利多项式, 首先取 $\{b_r:[0,1]\to \mathbb R\}_{r\in\mathbb N}$ :
$$\begin{align}
b_0(x)&\equiv 1\\
b_r'(x)&\equiv rb_{r-1}(x)&(r\geq1)
\end{align}$$
且
$$\begin{align}
\int_0^1 b_r(x)\ dx=0&&(r\geq1)
\end{align}$$
之所以这么写, 是考虑到高次微分也有二项式定理形状的系数, 同时上面这个多项式也有自己的生成函数:
$$f(x)=\frac{ye^{xy}}{e^y-1}$$
考虑他在 $0$ 处对 $y$ Taylor 展开, 自然满足
$$f^{(0)}(x)\xlongequal{\text{L'Hospital}}1$$
$$\begin{align}
\int_0^1\left(\frac{\partial }{\partial y}\right)^r\frac{ye^{xy}}{e^y-1}\ \partial x&\xlongequal{1}\left(\frac{\partial}{\partial y}\right)^r\int_0^1\frac{ye^{xy}}{e^y-1}\ \partial x\\
&=\left(\frac{\partial }{\partial y}\right)^r\frac{e^{xy}|_0^1}{e^y-1}=0\quad  (r>0)
\end{align}$$
1 当然有一些换序带来的实分析问题要处理, 令 $y_n\to y$, $F(y)=\int_x f(x,y)\ dx$, 则
$$F'(y)=\lim\frac{F(y_n)-F(y)}{y_n-y}=\lim\int\underbrace {\frac{f(x,y_n)-f(x,y)}{y_n-y}}_{\leq\sup_{y\in B_\varepsilon (y)}\left|\frac{\partial f}{\partial y}(x,y)\right|<\infty}\ dx$$
从而由控制收敛定理允许换序
$$\begin{align}
\left.\frac{\partial }{\partial x}\left(\frac{\partial }{\partial y}\right)^r\frac{ye^{xy}}{e^y-1}\right|_{y=0}\xlongequal{2}\left.r\left(\frac{\partial}{\partial y}\right)^{r-1}\frac{ye^{xy}}{e^y-1}\right|_{y=0}
\end{align}$$
2 来自某种递归式的观察, 当然注意力足够集中的话也可以说它是显然的, 其换序是形式化的无需证明 (话说真没有什么能简洁的把这玩应写出来的语言吗)

随后把 $B_r$ 定义为 $b_r(0)$ 即可, 不过为了方便

> [!def] 伯努利函数
> 定义 $B_r(x)$ 为在 $[0,1)$ 上取 $b_r(x)$ 的周期函数

# Euler-Maclaurin 公式

令 $f\in C^{k+1}[a,b],$ $a,b\in\mathbb Z$, 由于 $B_1(x)=\{x\}-\frac12$, 有
$$\sum_{a<n\leq b}f(n)=\int_a^bf(t)\ d[t]=\int_a^bf(t)\ dt-\int_a^bf(t)\ dB_1(t)$$
对后一项做分部积分
$$\begin{align}
\int_a^bf(t)\ dB_1(t)&=B_1(f(b)-f(a))-\int_a^b B_1 f'(t)\ dt\\
&=B_1(f(b)-f(a))-\frac1{2!}\int_a^bf'(t)\ dB_2(t)
\end{align}$$
而 $B_2(t)$ 在 $\mathbb R$ 上连续, 在 $\mathbb R\setminus\mathbb Z$ 上可微, 且在其上满足方程 $B_2'(t)=2B_1(t)$, 由类似的结构重复该过程, 就得到了著名的 E-M 公式

> [!thm] Euler-Maclaurin
> $k\geq0,f\in C^{k+1}[a,b],a,b\in\mathbb Z$
> $$\begin{align}
> \sum_{a< n\leq b}f(n)&=\int_a^b f(t)\ dt+\sum_{r=0}^k\frac{(-1)^{r+1}B_{r+1}}{(r+1)!}(f^{(r)}(b)-f^{(r)}(a))\\&+\frac{(-1)^k}{(k+1)!}\int_a^b B_{k+1}(t)f^{(k+1)}(t)\ dt
> \end{align}$$

RMK: 需要注意的是, 就算让 $k\to\infty$ 其余项也未必趋于 $0$.

# 应用

这个公式最有用之处在于可以处理不收敛的情况

> [!thm] 调和级数阶的估计
> $n\geq1$, 
> $$\sum_{i=1}^n\frac1i=\log n+\gamma+\frac1{2n}-\frac1{12n^2}+\frac{\mathscr O}{60n^4}$$
> 其中 $\gamma$ 为 Euler 常数

`BEGINPROOF`
直接带入即可
`ENDPROOF`

## Strlin 公式

对 $ln(t)$ 用 $0$ 阶 E-M 公式 (其实 $0$ 阶 E-M 公式就是内接和外切梯形估计, 所以其实有初等证明)
$$\begin{align}
\sum_{r=2}^n \ln r&=\int_1^n\ln t\ dt - B_1(\ln n-\ln 1)+\int_1^nB_1(t)\frac1t\ dt\\
&=n\ln n-n+1+\frac12\ln n+\int_1^n B_1t^{-1}\ dt\\
n!&=n^ne^{-n}\sqrt n\underbrace{\exp\left(1+\int_1^n B_1(t)t^{-1}\ dt\right)}_{(*)}
\end{align}$$
剩下的问题就是估 (\*) 的大小, 思路是先提一个常量 $\int_1^\infty B_1(t)t^{-1}\ dt$ 出来, 再处理后半部分的积分
$$\begin{align}
\int_n^\infty B_1(t)t^{-1}\ dt&=-\sum_{m=n}^\infty\int_0^1\frac{\frac12-t}{m+t}\ dt\leq -\sum_{m=n}^\infty\int_0^{\frac12}(\frac1m-\frac1{m+1})(\frac12-t)\ dt=O(\frac1n)
\end{align}$$
即有
$$n!=n^ne^{-n}\sqrt{An}\{1+O(n^{-1})\}$$
或者用估计中常用的写法
$$n!\sim n^ne^{-n}\sqrt{An}$$
其中
$$A=\exp(-2+2\int_1^\infty B_1(t)t^{-1}\ dt)$$
**下一步是研究这个 $A$,** 首先处理一下
$$\int_1^\infty \frac{B_1(t)}t\ dt=\sum_{m=1}^\infty \int_0^1\frac{t-\frac12}{m+t}\ dt=\sum_{m=1}^\infty 1-(m+\frac12)\ln(1+\frac1m)$$
发现直接求似乎不是很行得通, 那么转换思路尝试以待定系数的方式解决, 那么我们就要找一个已知的存在阶乘的估计, 这里我们采用一个来自分部积分和三角函数的结构构造阶乘: **Wallis 积分**
$$W_n:=\int_0^{\pi/2}\cos^n t\ dt$$
其满足
$$\begin{align}
W_n&=\int_0^{\pi/2}\cos^{n-1} t\ d\sin t\\
&=\cos^{n-1}t\sin t|_{0}^{\pi/2}+(n-1)\int_0^{\pi/2}\sin^2 t\cos^{n-2}t\ dt\\
&=(n-1)W_{n-2}-(n-1)W_{n}\\
\Longrightarrow nW_n&=(n-1)W_{n-2}
\end{align}$$
从而我们可以用递推的方式研究它
$$\begin{align}
W_1&=1\Rightarrow W_{2n+1}=\prod_{i=1}^n\frac{2i}{2i+1}=\frac{(2n)!!}{(2n+1)!!}\\
W_2&=\frac\pi 4\Rightarrow W_{2n}=\frac\pi 2\prod_{i=1}^n\frac{2i-1}{2i}=\frac\pi 2\frac{(2n-1)!!}{(2n)!!}
\end{align}$$
可以把带系数 $A$ 的 Strlin 公式放进去估阶
$$W_{2n+1}=\frac{2^{2n}(n!)^2}{(2n+1)!}\sim \frac{2^{2n}n^{2n}e^{-2n}An}{(2n+1)^{2n+1}e^{-2n-1}\sqrt{A(2n+1)}}\sim \frac{e}{(1+\frac1{2n})^{2n}}\sqrt{\frac{A}{8n}}\sim \sqrt{\frac{A}{8n}}$$
同理
$$W_{2n}=\frac{\pi}{2}\frac{(2n-1)!}{2^{2n}(n!)^2}\sim 
\frac\pi 2\frac{(2n)^{2n}e^{-2n}\sqrt{2An}}{2^{2n}n^{2n}e^{-2n}An}\sim \pi\sqrt{\frac{1}{2An}}$$
而我们知道这个 $W_{2n}$ 和 $W_{2n+1}$ 应该是差不多的, 因为 $W_n$ 应当是个单调的序列[^1], 从而
$$\sqrt{\frac{A}{8}}=\frac{\pi}{\sqrt{2A}}\Rightarrow A=2\pi$$
综上即可得到 Strlin 公式

> [!thm] Strlin 公式
$$n!\sim n^ne^{-n}\sqrt{2\pi n}$$

[^1]: 另外此处带入 Wallis 的通项也可以顺手拿到一个 $\pi$ 的估计: $$\frac{W_{2n+1}}{W_{2n}}=\frac2\pi\frac{((2n)!!)^2}{(2n+1)!!(2n-1)!!}\to1\Rightarrow \frac{(2n+1)!!}{(2n)!!}\frac{(2n-1)!!}{(2n)!!}\to\frac{\pi}{2}$$

> [!example] 一维简单随机游走的常反性
> $$\sum_{n=1}^\infty \binom{2n}{n}\left(\frac12\right)^{2n}\sim \sum_{n=1}^\infty\frac1{\sqrt{\pi n}}\to\infty$$
> 由 Borel-Contaili 引理立得

