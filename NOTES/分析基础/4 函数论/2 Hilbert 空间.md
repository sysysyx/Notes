# Hilbert 空间

若已知一个内积显然能得到范数, 但是哪些范数能被写成内积呢, 由于
$$\langle x,y\rangle =\frac14(\langle x+y,x+y\rangle-\langle x+y,x+y\rangle+i\langle x+iy,x+iy\rangle -i\langle x-iy,x-iy\rangle)$$
想到可以定义
$$\langle x,y\rangle =\frac14(\|x+y\|^2-\|x-y\|^2+i\|x+iy\|^2-i\|x-iy\|^2)$$
其自然满足正定性和交换性, 但是问题在于线性性, 我们想要
$$\langle x,y_1+y_2\rangle\stackrel ?=\langle x,y_1\rangle +\langle x,y_2\rangle$$
其充要条件是平行四边形法则
$$\|x+y\|^2+\|x-y\|^2=2\|x\|^2+2\|y\|^2$$
必要性就是本节第一个式子, 充分性:
$$\begin{align}
&\|x+y_1\|^2-\|x-y_1\|^2+\|x+y_2\|^2-\|x-y_2\|^2\\
=&2\|x+\frac{y_1+y_2}2\|^2+2\|\frac{y_1-y_2}2\|^2-2\|x-\frac{y_1+y_2}{2}\|^2-2\|\frac{y_1-y_2}{2}\|^2\\
=&2\|x+\frac{y_1+y_2}2\|^2+2\|\frac{y_1+y_2}2\|^2-2\|x-\frac{y_1+y_2}{2}\|^2-2\|\frac{y_1+y_2}{2}\|^2\\
=&\|x+\frac{y_1+y_2}{2}+\frac{y_1+y_2}{2}\|^2+\|x\|^2-\|x-\frac{y_1+y_2}{2}-\frac{y_1+y_2}{2}\|^2-\|x\|^2
\end{align}$$

ps: 平行四边形法则中的等号可以改成不等号, 因为令 $x'=\frac{x+y}2$, $y'=\frac{x-y}2$ 就会得到相反的式子, 不过我觉得这个变形除了让人困惑毫无意义