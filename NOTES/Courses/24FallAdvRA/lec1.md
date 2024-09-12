先修课程: 点集拓扑, 泛函分析, 实变函数
教材: Real analysis Folland
参考书:
- 测度论部分: 
	- 测度论讲义 严加安
	- 测度论与概率论基础 程士宏
	- Measure theory and fine property of functions, Evans (管外测度叫测度, 名词巨大不兼容)
	- Integration and Probobility, Mlliarin (随即分析开创者)
课程内容:
- 上半学期: 测度论基础, $L^p$ 空间理论, Radon 测度
- 下半学期: 基本 Fourier 分析 ($\overline T$ 情形 (技巧较多), $H^S$ 空间, Littlewood-Poley 理论(偏微分经典理论)), 广义函数论初步

# Introduction

## Sets and measure

Consider a nonempty set $X$ and its power set $2^X$. Let $\mathcal C$ be a family of subsets of X. We have 2 main operations:
$$\bigcup\mathcal C=\{x\in X, \exists C\in\mathcal C. x\in C\}\qquad \bigcap\mathcal C=\{x\in X, \forall C\in\mathcal C. x\in C\}$$
They could be regard as "plus" and "times' in set theory, and have corresponding
- Communicative laws: $A\cap B=B\cap A$, $A\cup B=B\cup A$
- Distribution laws: $A\cap (\bigcup_{k}B_{k})=\bigcup_{k}(A\cap B_{k})$, $A\cup(\bigcap _{k}B_{k})=\bigcap_{k} (A\cup B_{k})$
- Associative laws: $(A\cap B)\cap C=A\cap(b\cap C)$, $(A\cup B)\cup C=A\cup(B\cup C)$
additionally
- de Morgan's laws: $(\bigcap_{k} A_{k})^c=\bigcup_{k}A_{k}^c$, $(\bigcup_{k}A_{k})^c=\bigcap_{k}A_{k}^c$.
Also we can define limits in set theory
$$\begin{align}
\limsup A_{n}=\bigcap_{n}\bigcup_{j\geq n}A_{j} \\
\liminf A_{n}=\bigcup_{n}\bigcap_{j\geq n}A_{j} 
\end{align}$$
## Mapping

We first build **relation** between sets $X$ and $Y$ as a subset of  $X\times Y$, and define **mapping**  $f:X\to Y$ as a relation between $X$ and $Y$ satisfying: forall $x\in X$ there is a unique $y\in Y$ such that $(x,y)\in f$ or $y=f(x)$.

> [!proposition]
> for $f:X\to Y$ be a mapping
> - $A_1\subset A_2 \subset X\implies f(A_{1})\subset f(A_{2})$
> - $B_1\subset B_2\subset Y\implies f^{-1}(B_1)\subset f^{-1}(B_2)$
> - $A\subset X$, $B\subset Y$, $f^{-1}(A)\subset B\implies A\subset f^{-1}(B)$
> - $A\subset X$, $B\subset Y$, $A\subset f^{-1}\circ f(A)$, $B\in f\circ f^{-1}f(B)$
> - $\{A_{i}\}_{i\in I}\subset P(X)\implies f(\bigcup A_{i})=\bigcup(f(A_{i}))$
> - $\{B_{i}\}_{i\in I}\subset P(Y)\implies f^{-1}(\bigcup B_{i})=\bigcup(f^{-1}(B_{i}))$, $f^{-1}(\bigcap B_{i})=\bigcap (f^{-1}(B_{i}))$
> - $\forall B\subset Y$ $\implies$ $f^{-1}(Y\setminus B)=X\setminus f^{-1}(B)$

# Measure

## sigma-algebra

... skip some repeating definations, ref [[1 测度与积分#预备工具 集类和单调类定理]]

som additional information:
- usually we build our theory first from simi-rings
- In a Ring, we can regard $\triangle$ as "$+$" and $\cap$ as "$\times$", thats why we want cup and setminus be closed. And in such a ring, $0$ is $\emptyset$ and $1$ is $\Omega$
- In set theory algebra is not so-called "algebra" in algebra
- $\lambda$-systerm is a descripation of $\{B\in X\mid \mu_{1}(B)=\mu_{2}(B)\}$

**Exercise**: for any simifing $\mathcal C$, let $R$ be set of all finite disjoint unions of members of $\mathcal C$, prove $R$ is a ring.

