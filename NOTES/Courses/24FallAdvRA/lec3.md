## 1.5 Borel measure

> [!lem]
> $$\forall E\subset M_{\mu}, \mu(E)=\inf\left\{ \sum_{j=1}^\infty \mu(a_{j},b_{j}):E\subset \bigcup_{j=1}^\infty (a_{j},b_{j})\right\}$$

> [!thm]
> metric space $X$, measure space $(X,M,\mu)$, $\mu$ is an open $\sigma$-finite Borel-regular measure
> Then $\mu(A)=\inf\{\mu(U):A\subset U\text{ open}\}=\sup\{\mu(C):C\subset A,C\text{ closed}\}$

open $\sigma$-finite: $\exists X=\bigcup_{j\in\mathbb N}V_{j}$ $V_j$ open and $\mu(V_{j})<\infty$
Borel regular: $\forall A\in M,\mu(A)=\inf\{\mu(B):A\subset B \text{ Borel}\}$

# 2 Measure function

Given 2 measure space $(X,M)$, $(Y,N)$, a function $f:X\to Y$ is calles $(M,N)$-measureable if $f^{-1}(N)\subset M$

An important propertie:

> [!proposition]
> $f$ measureable, then $f^{-1}(\sigma(C))=\sigma(f^{-1}(C))$

$$f^{-1}(C)\subset f^{-1}(\sigma(C))\text{ sigma alg}\implies\sigma (f^{-1}(C))\subset f^{-1}(\sigma(C))$$
$$\sigma(C)\subset f(\sigma(f^{-1}(\mathcal C)))\text{ sigma alg}\implies f^{-1}(\sigma(C))\subset \sigma(f^{-1}(\mathcal C))$$
rmk: $f^{-1}:2^N\to 2^M$ is a function
