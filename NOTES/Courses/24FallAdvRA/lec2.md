# Lec 2

...来晚了少听一节

set function $\emptyset\in\mathcal C$, $u:\mathcal C\to[0,\infty]$, we call it
- finitely additive: $A_{i}\in \mathcal C$, $\sum_{i=1}^nA_{i}\in\mathcal C\implies \sum_{i=1}^n\mu(A_{i})=\mu\left( \sum_{i=1}^n A_{i} \right)$
- countably additive: $A_i\in\mathcal C$ $\sum_{i=1}^\infty A_{i}\in\mathcal C\implies \sum_{i=1}^\infty\mu(A_{i})=\mu\left( \sum_{i=1}^\infty A_{i} \right)$
- simi $\sigma$-additive: $A_i\in\mathcal C$ $\bigcup_{i=1}^\infty A_{i}\in\mathcal C\implies \sum_{i=1}^\infty\mu(A_{i})\geq \mu\left( \bigcup _{i=1}^\infty A_{i} \right)$
- continue from below: $\mathcal C\ni A_{i}\uparrow A\implies\lim_{ n \to \infty }\mu(A_{i})=\mu(\lim_{ n \to \infty }A_{i})$
- continue from above: $\mathcal C\ni A_{i}\downarrow A\implies\lim_{ n \to \infty }\mu(A_{i})=\mu(\lim_{ n \to \infty }A_{i})$

> [!proposition]
> let $\mathcal C$ be a simi-ring: $\sigma$-additive $\iff$ finitely additive and simi $\sigma$-additive

`BEGINPROOF`
$\Longrightarrow$ obvious
$\Longleftarrow$: $A_n\in\mathcal C$ disjoint, $\sum_nA_n=A\in\mathcal C$, for simi-ring $\sum_{i=1}^nA_i=A\setminus \sum_{i=n}^\infty A_{i}\in\mathcal C_{\Sigma f}$
Set $\sum_{i=n+1}^\infty A_i=\sum_{i=1}^k C_{i}$ for finite-additive: 
$$\mu(A)=\sum_{i=1}^n\mu(A_i)+\sum_{i=1}^k \mu (C_i)\geq \sum_{i=1}^n \mu(A_{i})$$
let $n\to\infty$, $\mu(A)\geq\sum_{i=1}^\infty A_i$.
On the other hand, for simi $\sigma$-additive $\mu(A)\leq \sum_{i=1}^\infty A_i$
`ENDPROOF`
## 1.4 outer measure

