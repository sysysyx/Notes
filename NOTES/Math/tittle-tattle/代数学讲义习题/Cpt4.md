**1. (i)**
不妨设 $V_1\triangle V_2\neq\emptyset$ (否则 $V_1\subset V_2\subsetneq V$ 或 $V_2\subset V_1\subsetneq V$), 取
$$0\neq v_1\in V_1\setminus V_2,\qquad 0\neq v_2\in V_2\setminus V_1$$
往证 $v_1+v_2\not\in V_1\cup V_2$: 

反设 $v_1+v_2\in V_1$, 则
$$v_1+v_2\in V_1\Rightarrow v_2=v_1+v_2-v_1\in V_1$$
得到矛盾, 同理 $v_1+v_2\not\in V_2$`ENDPROOF`

**(ii)** $V=\mathbb F_2^2$, $V_1=\{(0,0),(1,0)\}$, $V_2=\{(0,0),(1,1)\}$, $V_3=\{(0,0),(0,1)\}$

**(iii)** 直接证 $F$ 为无穷集的情形, 通过删去多余的 $V_i$, 不妨设
$$0\neq v_1\in V_1\setminus (V_2\cup\cdots\cup V_k)\neq\emptyset,\quad 0\neq v_2\in V_2\setminus (V_1\cup V_3\cup\cdots\cup V_k)$$
从而
$$W=\{v_1+av_2:a\in F\setminus \{0\}\}\in V\setminus (V_1\cup V_2)$$
断言对任意 $i>2$, $\sharp\{W\cap V_i\}<2$, 反证
$$\begin{align}
&v_1+k_1v_2\in V_i,\quad v_1+k_2v_2\in V_1,\quad k_1\neq k_2\\
&\Rightarrow(k_1-k_2)v_2\in V_i\Rightarrow v_2\in V_i
\end{align}$$
与假设矛盾, 而 $W$ 为一无穷集合, 从而
$$V\setminus (\bigcup V_j)\supset W\setminus (\bigcup V_i)\neq\emptyset$$
`ENDPROOF`
**3.**
$$\begin{pmatrix}
\lambda^n&
\begin{pmatrix}n\\1\end{pmatrix}\lambda^{n-1}&
\cdots&\begin{pmatrix}n\\n-1\end{pmatrix}\lambda\\
&\ddots&\ddots&\vdots\\
&&\ddots& \begin{pmatrix}n\\1\end{pmatrix}\lambda^{n-1}&\\
&&&\lambda^n
\end{pmatrix}$$

