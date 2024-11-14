> [!exercise]

$$\begin{align}
\sigma_{xy}&=\operatorname{var}(z)=\sigma^2 \\
\sigma_{xy\cdot z}&=\sigma_{xy}-\sigma_{xz}\sigma_{zz}^{-1}\sigma_{zy}=\sigma^2-\sigma^2=0
\end{align}$$
从而偏相关系数为 $0$

> [!exercise]

不妨设 $x,y,x$ 方差均为 $1$
$$\begin{align}
\rho_{yx\cdot z}&= \frac{\sigma_{xy\cdot z}}{\sqrt{ \sigma_{x x \cdot z}\sigma_{yy\cdot z} }}=\frac{\sigma_{xy}-\sigma_{xz}\sigma_{zz}^{-1}\sigma_{zy}}{\sqrt{ (\sigma_{x x}-\sigma_{zx}\sigma_{zz}^{-1}\sigma_{zx})(\sigma_{yy}-\sigma_{zy}\sigma_{zz}^{-1}\sigma_{zy}) }} \\
&=\sqrt{ \frac{(\sigma_{xy}-\sigma_{xz}\sigma_{zy})^2}{(1-\sigma_{zx}^2)(1-\sigma_{zy}^2)} }=\sqrt{ \frac{\sigma_{xy}^2+2\sigma _{xy}\sigma_{yz}\sigma_{xz}}{1-\sigma_{zy}^2} } \\
&=\sqrt{ \frac{R^2_{y\sim (x,z)}-R^2_{y\sim z}}{1-R^2_{y\sim z}} }
\end{align}$$
可以粗略解释为
$$y\ 被\ x\ 决定的部分=\frac{y\ 被 \ xz\ 共同决定的部分-y\ 被 z\ 决定的部分}{1-y\ 被\ z\ 决定的部分}$$

> [!exercise]

`BEGINPROOF`
由于
$$\det(I+ab^T)=1+b^Ta$$
$$\det(A+uv^T)=\det(A)\det(I+Auv^T)=(1+v^TAu)\det(A)$$

$$\begin{align}
\left( A^{-1}-\frac{A^{-1}uv^TA^{-1}}{1+v^TA^{-1}u} \right)(A+uv^T)&=1-\frac{A^{-1}uv^T}{1+v^TA^{-1}u}+A^{-1}uv^T- \frac{A^{-1}uv^TA^{-1}uv^T}{1+v^TA^{-1}u}  \\
&=1+\frac{A^{-1}uv^T+(A^{-1}uv^T)^2-A^{-1}uv^T-(A^{-1}uv^T)^2}{1+v^TA^{-1}u}b \\
&=1
\end{align}$$
`ENDPROOF`

> [!exercise]

`BEGINPROOF`
取定理 2 中 $q=1$ 的特殊情况得到
$$x_{1}\mid x_{-1}\sim N\left( \mu_{1}+\Sigma_{12}\Sigma_{22}^{-1}(x_{2}-\mu_{2}),\sigma_{11\cdot{2}} \right)=N\left( \mu_{1}-\sum_{j\neq1} \frac{w_{1j}}{w_{11}}(x_{j}-\mu_{j}),w_{11}^{-1} \right)$$
其余情况做初等变换立得.

$$\rho_{xy\mid z}= \frac{\Sigma_{xy\cdot z}}{\sqrt{ \Sigma_{xx\cdot z}\Sigma_{yy\cdot z} }}=\rho_{xy\cdot z}$$
$$w_{ij}=0\iff \rho_{xy\mid z}=0\iff x⫫y\mid z$$
`ENDPROOF`