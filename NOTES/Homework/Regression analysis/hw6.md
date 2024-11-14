> [!exercise]

拟合值
$$\hat{y}=\hat{a}+\hat{b}x$$
相关系数
$$r_{\hat{y}y}= \frac{cov(y,\hat{y})}{\sqrt{ var(y)var(\hat{y}) }}=\frac{\hat{b}}{|\hat{b}|}\frac{cov(y,x)}{\sqrt{ var(y)var(x) }}=|r_{xy}|$$

> [!exercise]

$$\mathbb E(e_{i})=\mathbb E(y_{i})-\mathbb E(\hat{a}+\hat{b}x_{i})=\bar{y}-\bar{y}+\hat{b}\bar{x}-\hat{b}\bar{x}=0$$
$$\begin{align}
var(e_{i}\mid x)&=var(y_{i}-\hat{a}-\hat{b}x\mid x) \\
&=var (a-\hat{a}+(b-\hat{b})x+\varepsilon_{i}\mid x)=\left( 1 - \frac{1}{n}- \frac{(x_{i}-\bar{x})^2}{s_{xx}} \right)\sigma^2
\end{align}$$
> [!exercise]

(a)
$$\begin{align}
(1)&=3.733 / 28.040=0.133 \\
(2)&=-0.085/0.012=7.083 \\
(3)&= 193-2=191
\end{align}$$
(b)
$$样本方差 = \frac{1.526^2}{191}=0.0122$$

(c)
$$\bar{F}=a+b\bar{P}=3.733-0.085\times 6408=3.188$$
(d)
若一个国家或地区 PPgdp 比另一个少 $1$, 其 Fertility 的期望比另一个少 $0.085$

> [!exercise]

(a)
$$\begin{align}
\hat{b}&=\frac{cov(x,y)}{var(x)}= \frac{827.3}{182.2}=4.541 \\
\hat{a}&=\bar{y}-\hat{b}\bar{x}=209.9-4.541\times{7}1.1=-112.97
\end{align}$$
由于 $b$ 是正的, 期望较短

(b)
$$\begin{align}
TSS&=\sum(y_{i}-\bar{y})^2=n\times var(y)=270\times{4}677.5 \\
RSS&=\hat{b}^2var(x)=4.541^2\times{1}82.2=3,757 \\
ESS&=TSS-RSS=1262790 \\
\hat{\sigma}^2&= \frac{1262790}{270-2}=4711.9 \\
\hat{\sigma}&=68.64
\end{align}$$
(c)
$$R^2= \frac{RSS}{TSS}=2.97e-4$$
(d)
$$200=4.541\times \hat{y}-112.97\implies \hat{y}=68.92$$
预期 $68.92$ 分钟.