> [!exercise]

`BEGINPROOF`
$x$ 的分布
$$f_x(x)=\frac{1}{(2\pi)^{n/2}}\exp\left( -\frac{\|x\|^2}{2} \right)$$
由于 $A$ 为一正交矩阵, $AA^T=I$, 从而 $Ax$ 的分布
$$f_{Ax}(x)=\frac{1}{(2\pi)^{n/2}}\exp\left( -\frac{\|A^Tx\|^2}{2} \right)=\frac{1}{(2\pi)^{n/2}}\exp\left( -\frac{\|x\|^2}{2} \right)$$
从而 $Ax\sim N_n(0,I_n)$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
设 $x=(x_{1},\cdots,xn)$ 通过乘正定矩阵, 不妨设 $a=(1,0,\cdots,0)^T$, $b=(0,1,0,\cdots,0)^T$, 则
$$\sqrt{ n-2 } \frac{a^Tx}{\sqrt{ \|x\|^2-(a^Tx)^2-(b^Tx)^2 }}= \frac{x_{1}}{\sqrt{ \left( \sum_{i=3}^nx_{i}^2 \right) /(n-2) }}$$
其中 $x_1\sim N(0,1)$, $\sum_{i=3}^nx_{i^2}\sim\chi_{n-2}^2$ 且由上题二者相互独立
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
$$\begin{align}
r&= \frac{s_{xy}}{\sqrt{ s_{xx}s_{yy} }}=\frac{\sum_{i=1}^n(x_{i}-\bar{x})(y_{i}-\bar{y})}{\sqrt{ \sum_{i=1}^n(x_{i}-\bar{x})^2\sum_{i=1}^n(y_{i}-\bar{y})^2 }} \\
&=\frac{\sum_{i=n_{0}+1}^{n_{0}+n_{1}} \frac{n_{0}}{n_{0}+n_{1}}\times\frac{n_{0}(y_{i}-\bar{y_{0}})+n_{1}(y_{i}-\bar{y_{1}})}{n_{0}+n_{1}}-\sum_{i=1}^{n_{0}} \frac{n_{1}}{n_{0}+n_{1}}\times\frac{n_{0}(y_{i}-\bar{y_{0}})+n_{1}(y_{i}-\bar{y_{1}})}{n_{0}+n_{1}}}{\sqrt{ \frac{n_{1}n_{0}}{n_{1}+n_{0}}\sum_{i=1}^n \left(\frac{n_{0}(y_{i}-\bar{y_{0}})+n_{1}(y_{i}-\bar{y_{1}})}{n_{0}+n_{1}}\right)^2}} \\
&=\frac{n_{0}\sum_{i=n_{0}+1}^{n_{0}+n_{1}} ({n_{0}(y_{i}-\bar{y_{0}})+n_{1}(y_{i}-\bar{y_{1}})})-n_{1}\sum_{i=1}^{n_{0}}(n_{0}(y_{i}-\bar{y_{0}})+n_{1}(y_{i}-\bar{y_{1}}))}{\sqrt{ n_{1}n_{0}(n_{1}+n_{0})\sum_{i=1}^n \left({n_{0}(y_{i}-\bar{y_{0}})+n_{1}(y_{i}-\bar{y_{1}})}\right)^2}} \\
&=\frac{\sqrt{ n_{0}n_{1} }(\bar{y}_{1}-\bar{y}_{0})}{\sqrt{s_{yy}}}
\end{align}$$
从而
$$\sqrt{ n-2 } \frac{r}{\sqrt{ 1-r^2 }}=\frac{\bar{y}_{1}-\bar{y}_{0}}{\sqrt{ \frac{s_{{yy}}-n_{0}n_{1}(\bar{y}_{1}-\bar{y}_{0})^2}{n_{0}n_{1}(n_{0}+n_{1}-2)} }}$$
即只需证
$$\frac{s_{yy}-n_{0}n_{1}(\bar{y}_{1}-\bar{y}_{0})^2}{n_{0}+n_{1}-2}=(n_{0}+n_{1})s^2$$
事实上, 这就是
$$\begin{align}
\sum_{i=1}^n \frac{(n_{0}(y_{i}-\bar{y_{0}})+n_{1}(y_{i}-\bar{y_{1}}))^2-(n_{0}+n_{1})n_{0}n_{1}(\bar{y}_{1}-\bar{y}_{0})^2}{(n_{0}+n_{1})^2} \\
=(n_{0}+n_{1})\left( \sum_{i=1}^{n_{0}}(y_{i}-\bar y_{0})^2+\sum_{i=n_{0}+1}^{n_{0}+n_{1}}(y_{i}-\bar{y}_{1})^2 \right)
\end{align}$$
展开验证显然
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
(a)
$$r_{G}=\cos\langle x,y\rangle$$
而向量的方向为均匀分布
(b)
$$\begin{align}
\mathbb P(uv=1\mid u=1)&=\mathbb P(v=1)=\frac{1}{2} \\
\mathbb P(uv=-1\mid u=1)&=\mathbb P(v=-1)=\frac{1}{2} \\
\mathbb P(uv=1\mid u=-1)&=\mathbb P(v=-1)=\frac{1}{2} \\
\mathbb P(uv=1\mid u=1)&=\mathbb P(v=1)=\frac{1}{2}
\end{align}$$
对 $u$ 同理
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
(1) 必要性显然, 下证充分性
$$\operatorname {var}(x,y)=\mathbb P(x=1,y=1)-\mathbb P(x=1)\mathbb P(y=1)=0$$
由总概率为 $1$ 容易推出
(2)
$$\begin{align}
z_{1}^2&=nr^2=n\frac{\left( a \frac{n_{0}}{n} \frac{m_{0}}{n}-b \frac{n_{0}}{n} \frac{m_{1}}{n}-c \frac{n_{1}}{n} \frac{m_{0}}{n}+d \frac{n_{0}}{n} \frac{m_{0}}{n} \right)^2}{\frac{2n_{1}^2n_{0}^2}{n^2} \frac{2m_{1}^2m_{0}^2}{n^2}}  \\
&=\frac{n(an_{0}m_{0}-bn_{0}m_{1}-cn_{1}n_{0}+dn_{0}m_{0})^2}{4n_{1}^2n_{0}^2m_{1}^2m_{0}^2} \\
&= \frac{n(ad-bc)^2}{n_{0}n_{1}m_{0}m_{1}}
\end{align}$$

`ENDPROOF`
