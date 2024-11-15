> [!exercise]

最短路问题可以视为任一路径的的容量都为 $1$, 代价也为 $1$, 流值为 $1$ 的最小成本流问题

对于一最大流问题, 视其每条路代价都为 $0$, 添加一条容量为 $\sum_{v\in V}c(s,v)$, 代价为 $1$ 的路径 $(s,t)$, 可视为流值为 $\sum_{v\in V}c(s,v)$ 的最小成本流问题

> [!exercise]

(a)

![[hw2-20241013084510711.webp]]

(b)

最大任务数量为 $4$

(c)
其中一个分配方式: $e_{1}:t_{1},t_{4};\quad e_{3}: t_{2},t_{3}$

(d)

![[hw2-20241013084718019.webp]]

$e_{1}:t_{1},t_{4};\quad e_{2}: t_{2};\quad e_{3}: t_{3},t_{5}$

> [!exercise]

(a) 最小代价路径: 右右下下, 最小代价: $3+1+1=5$
(b)$\binom{M+N}{N}$

> [!exercise]

记 $f(i,j)$ 为矩阵连乘 $A_{i}A_{i+1}\cdots A_{j}$ 的最小次数, 则
$$f(i,j)=\min_{i\leq m<j}(f(i,m)+f(m+1,j)+p_{i-1}p_{m}p_{j})$$
