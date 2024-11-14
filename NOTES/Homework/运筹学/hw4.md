> [!exercise]

由于
$$f(x^{k+1})=f(x^k+\alpha^kd^k)\leq f(x^k)+c\alpha^k\nabla f(x^k)d^k$$
并且
$$\infty> f(x^k)-f(x^\infty)\geq c \sum \alpha^k\nabla f(x^k)d^k=-c\sum\alpha^k\|\nabla f(x^k)\|$$
这说明 
$$\lim_{ k \to \infty } \|\alpha^k\nabla f(x)\|=0$$
从而算法收敛

> [!exercise]

直接计算
$$\begin{align}
f(x)&=\frac{1}{N}\sum \log(1+e^{-y_{i}a_{i}^Tx}) \\
f'(x) &= \frac{1}{N}\sum \frac {-y_{i}a_{i}^Te^{-y_{i}a_{i}^Tx}}{1+e^{-y_{i}a_{i}^Tx}} \\
f''(x)&= \frac{1}{N}\sum \frac{(y_{i}a_{i}^T)^2e^{y_{i}a_{i}^Tx}}{(1+e^{y_{i}a_{i}^Tx})^2}  \\
&= \frac{1}{N}\sum\frac{(y_{i}a_{i}^T)^2}{e^{-y_{i}a_{i}^Tx}+e^{y_{i}a_{i}^Tx}+2} \\
&\leq \frac{1}{4N}\sum(y_{i}a_{i}^T)^2
\end{align}$$
从而 $L\leq \frac{1}{4N}\sum(y_{i}a_{i}^T)^2$

> [!exercise]

$$\begin{align}
\nabla_{h_{3}}l&=h_{3}-t \\
\nabla_{W_{3}}l&=(\sigma'(W_{3}h_{2})\circ(h_{3}-t))h_{2}^T \\
\nabla_{h_{2}}l&=W^T(\sigma'(W_{3}h_{2})\circ(h_{3}-t)) \\
\nabla_{W_{2}}l&=(W^T(\sigma'(W_{3}h_{2})\circ \sigma'(W_{2}h_{1})\circ (h_{3}-t)))h_{1}^T \\
\nabla_{h_{1}}l&=W^T(W^T(\sigma'(W_{3}h_{2})\circ \sigma'(W_{2}h_{1})\circ (h_{3}-t))) \\
\nabla_{W_{1}}l&=(\sigma'(W_{1}x)\circ W^T(W^T(\sigma'(W_{3}h_{2})\circ \sigma'(W_{2}h_{1})\circ (h_{3}-t))))x
\end{align}$$

> [!exercise]

递归地有
$$\begin{align}
\nabla \phi(y)&=\nabla_{y} f(Ay)=A^T(\nabla f(Ay))=A^T\nabla f(x) \\
\nabla^2\phi(y)&=A^T\nabla^2 f(x) A
\end{align}$$
从而
$$\begin{align}
Ay^+&=A(y-\nabla^2\phi(y)^{-1}\nabla \phi(y)) \\
&=A(A^{-1}x-(A^T\nabla^2fA)^{-1}A^T\nabla f(x)) \\
&=x-(\nabla^2f(x))^{-1}\nabla f(x) \\
&=x^+
\end{align} $$

> [!exercise]

由于 $B_{k}=H_{k}^{-1}, B_{k+1}=H_{k+1}^{-1}$
$$B_{k+1}=B_{k}+\frac{B_{k}y_{k}y_{k}^TB_{k}}{y_{k}^TB_{k}y^k}-\frac{B_{k}s_{k}s_{k}^TB_{k}}{s_{k}^TB_{k}s_{k}}$$

> [!exercise]

(a)
设 $B_{k}^{-1}X$ 的特征值为 $\lambda_{1},\cdots,\lambda_{n}$, 则
$$Tr(B_{k}^{-1}X)-\log \det(B_{k}^{-1}X)-n=\sum(\lambda_{i}-1-\log\lambda_{i})>0$$

(b)
由于 Tr 线性, $-\log \det$ 凸, 整体是凸函数, 只需在 $B_{k+1}$ 处梯度为 $0$, 带入验证
$$B_{k}^{-1}-B_{k+1}^{-T}=0$$

