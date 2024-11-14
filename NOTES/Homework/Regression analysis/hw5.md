> [!exercise]

$$\hat{\mu}=\operatorname{arcmin}\sum_{i=1}^n(y_{i}-\mu)^2=\operatorname{arcmin}\left( n\mu^2-2\mu\sum y_{i}\right)=\bar{y}$$
$$\mathbb E(\hat{\mu}^2)-\mathbb E^2(\hat{\mu})=\frac{\sigma^2}{n}$$
定义
$$\hat{y}_{i}=\hat{\mu},\quad e_{i}=y_{i}-\bar{y}$$
> [!exercise]

同上计算可知
$$\hat{b}= \frac{\sum_{i=1}^nx_{i}y_{i}}{\sum_{i=1}^nx_{i}^2}$$
方差
$$var(\hat{b})= \frac{\sigma^2}{\sum_{i=1}^n x_{i}^2}$$

> [!exercise]

方差
$$var(\hat{b})= \frac{\sigma^2}{s_{xx}}= \frac{\sigma^2}{\sum(x-\bar{x})^2}$$
$m=\frac{n}{2}$ 时, 上式最小, 所以均衡设计下比较的结果最稳定

> [!exercise]

(1)
依定义 $\hat{a}=\bar{y}-\hat{b}\bar{x}$
(2)
$$\mathbb E(\tilde{b})=\sum\mathbb E\left( w_{i} \frac{y_{i}-\bar{y}}{x_{i}-\bar{x}} \right)=\sum\mathbb E \frac{s_{xy}}{s_{xx}}=\sum w_{0i}k_{i}=\hat{b}$$
