# Chapter 3. Linear Maps

## 3A. Vector Space of Linear Maps

### Linear Transformation

$T : V \to W$ is a **linear transformation** :

$$
\begin{array}{rcl}
au & \xrightarrow{\;T\;} & a\,T(u) \\
+\ bv & \xrightarrow{\;T\;} & +\ b\,T(v)
\end{array}
$$

---

### Linear Map Lemma

Suppose

- $v_1, \dots, v_n$ : basis of $V$
- $w_1, \dots, w_n$ : in $W$

then there exists a **unique** linear map $T : V \to W$ with

$$v_k \;\xrightarrow{\;T\;}\; w_k$$

---

### $\mathcal{L}(V,W)$ is a vector space

$$
\begin{aligned}
(S + T)v &= Sv + Tv && \text{addition} \\
(aS)v &= a(Sv) && \text{scalar multiplication} \\
(aS + bT)v &= a(Sv) + b(Tv) && \text{operations on } \mathcal{L}(V,W) \text{ (pointwise)}
\end{aligned}
$$

$\therefore\ \mathcal{L}(V,W)$ is a vector space (additive identity $=$ the $0$ map)

---

### Product of linear maps

For linear maps $T : U \to V$ and $S : V \to W$:

$$u \xrightarrow{\;T\;} Tu \xrightarrow{\;S\;} S(Tu)
\qquad\leadsto\qquad
ST : U \to W, \quad u \xrightarrow{\;ST\;} S(Tu)$$

We need to prove that $ST$ is linear.

---

### Algebraic properties of products

$$
\begin{aligned}
\text{associativity} &: (AB)C = A(BC) \\
\text{identity} &: TI = IT = T \\
\text{distributivity} &: (A+B)C = AC + BC, \quad A(B+C) = AB + AC
\end{aligned}
$$

---

### $ST = TS$ can fail (non-commutativity)

For linear maps, $ST \ne TS$ in general.

---

### $T(0) = 0$

If $T$ is a linear map, then $T(0) = 0$.

## 3B. Null Spaces and Ranges

### Null space is a subspace

For a linear map $T : V \to W$, $\ \operatorname{null} T = \{v : Tv = 0\}$ is a subspace of $V$.

---

### Injectivity $\iff \operatorname{null} T = \{0\}$

A linear map $T : V \to W$

$$
\begin{aligned}
\text{is injective} &\iff (Tu = Tv \implies u = v) \\
&\iff (u \ne v \implies Tu \ne Tv) \\
&\iff \operatorname{null} T = \{0\}
\end{aligned}
$$

---

### Range is a subspace

For a linear map $T : V \to W$, $\ \operatorname{range} T = \{Tv\}$ is a subspace of $W$.

---

### Surjectivity

A linear map $T : V \to W$ is surjective $\iff \operatorname{range} T = W$

---

### Fundamental Theorem of Linear Maps

$$\dim V = \dim \operatorname{null} T + \dim \operatorname{range} T$$

$$
\begin{array}{lccc}
\text{basis of } \operatorname{null} T : & \{u_1 \dots u_m\} & \\
\text{basis of } V : & \{u_1 \dots u_m\} & \cup & \{v_1 \dots v_n\} \\
 & \downarrow & & \downarrow \\
\text{basis of } \operatorname{range} T : & \{\} & & \{Tv_1 \dots Tv_n\}
\end{array}
$$

---

### $\dim V > \dim W$ $\implies$ not injective

If $\dim V > \dim W$, then a linear map $T : V \to W$ is **not injective** (finite-dimensional):

$$
\begin{array}{lccc}
 & & & \small\text{“}\operatorname{null} T\text{”} \\
\text{basis of } V : & \{u_1 \dots u_m\} & \cup & \{\dots u_n\} \\
 & \downarrow & & \downarrow \\
\text{basis of } W : & \{Tu_1 \dots Tu_m\} & & \{\}
\end{array}
$$

---

### $\dim V < \dim W$ $\implies$ not surjective

If $\dim V < \dim W$, then a linear map $T : V \to W$ is **not surjective** (finite-dimensional):

$$
\begin{array}{lccc}
\text{basis of } V : & \{u_1 \dots u_m\} & \\
 & \downarrow & \\
\text{basis of } W : & \underbrace{\{Tu_1 \dots Tu_m\}}_{\text{“}\operatorname{range} T\text{”}} & \cup & \{w_{m+1} \dots w_n\}
\end{array}
$$

---

### Operators on finite-dimensional $V$

For a linear map $T : V \to V$ (finite-dimensional):

$$
\begin{aligned}
T \text{ injective} &\iff \operatorname{null} T = \{0\} \\
&\iff \dim \operatorname{range} T = \dim V \\
&\iff \operatorname{range} T = V \\
&\iff T \text{ surjective}
\end{aligned}
$$

---

### Systems of Linear Equations

Fix $A_{j,k} \in F$ and define $T : F^n \to F^m$:

$$
\sum_k x_k e_k \;\xrightarrow{\;T\;}\;
\sum_k x_k \begin{bmatrix} A_{1,k} \\ \vdots \\ A_{m,k} \end{bmatrix}
= \begin{bmatrix} \sum_k A_{1,k}\, x_k \\ \vdots \\ \sum_k A_{m,k}\, x_k \end{bmatrix},
\qquad
e_k \;\xrightarrow{\;T\;}\; \begin{bmatrix} A_{1,k} \\ \vdots \\ A_{m,k} \end{bmatrix}
$$

$$\{0\} \subseteq \operatorname{null} T$$

$$
\begin{aligned}
\text{nonzero solution exists} \quad &\iff T \text{ not injective} \\
&\iff \{0\} \subsetneq \operatorname{null} T \\[2ex]
\text{no solution for some choice of } c \quad &\iff T \text{ not surjective} \\
&\iff \operatorname{range} T \subsetneq F^m
\end{aligned}
$$

$$
\begin{aligned}
\text{more variables than equations } (n > m) \ &\longrightarrow\ \text{nonzero solution exists} \\
\text{more equations than variables } (m > n) \ &\longrightarrow\ \text{no solution for some choice of } c
\end{aligned}
$$

## 3C. Matrices

### Matrix of a linear map

**$m$-by-$n$ matrix $A$ in $F$:**

$$
A = \begin{bmatrix}
A_{1,1} & \cdots & A_{1,n} \\
 & \vdots & \\
A_{m,1} & \cdots & A_{m,n}
\end{bmatrix}
$$

$A_{j,k}$ = entry in row $j$, column $k$

---

### Definition of $\mathcal{M}(T)$

Linear map $T : V \to W$, with

- basis of $V = \{v_1, \dots, v_n\}$
- basis of $W = \{w_1, \dots, w_m\}$

$\mathcal{M}(T)$ is the $m$-by-$n$ matrix defined by

$$
v_k \;\xrightarrow{\;T\;}\; A_{1,k}\, w_1 + \cdots + A_{m,k}\, w_m
\qquad\longrightarrow\qquad
\begin{bmatrix} A_{1,k} \\ \vdots \\ A_{m,k} \end{bmatrix} = \text{column } k \text{ of } \mathcal{M}(T)
$$

$\mathcal{M}(T)$ depends on the **bases** as well as on $T$.

---

### Entrywise operations

For matrices of the same size, entrywise:

$$
\begin{aligned}
(A+C)_{j,k} &= A_{j,k} + C_{j,k} && \text{addition} \\
(aA)_{j,k} &= a\,A_{j,k} && \text{scalar multiplication}
\end{aligned}
$$

For linear maps $S, T : V \to W$ and $k \in F$:

$$
\begin{aligned}
\mathcal{M}(S+T) &= \mathcal{M}(S) + \mathcal{M}(T) && \text{addition} \\
\mathcal{M}(kT) &= k\,\mathcal{M}(T) && \text{scalar multiplication}
\end{aligned}
$$

---

### $\dim F^{m,n} = mn$

Let $F^{m,n} = \{m\text{-by-}n \text{ matrices on } F\}$; then $\dim F^{m,n} = mn$.

---

### Rows, columns, and products

For an $m$-by-$n$ matrix $A$:

$$
\begin{aligned}
A_{j,\cdot} &= \text{row } j \text{ of } A && 1\text{-by-}n \text{ matrix} \\
A_{\cdot,k} &= \text{column } k \text{ of } A && m\text{-by-}1 \text{ matrix}
\end{aligned}
$$

---

### Matrix of a composition

- basis of $U = \{u_1, \dots, u_p\}$
- basis of $V = \{v_1, \dots, v_n\}$
- basis of $W = \{w_1, \dots, w_m\}$

Linear maps $U \xrightarrow{\;T\;} V \xrightarrow{\;S\;} W$ with $\mathcal{M}(S) = A$, $\mathcal{M}(T) = B$:

$$u_k \;\xrightarrow{\;T\;}\; B_{1,k}\, v_1 + \cdots + B_{n,k}\, v_n$$

$$\Big\downarrow\ S$$

$$
\begin{array}{rcl}
A_{1,1} B_{1,k}\, w_1 + \cdots + A_{1,n} B_{n,k}\, w_1 & \longrightarrow & \phantom{+\ } (AB)_{1,k}\, w_1 \\
\quad \vdots & & \quad \vdots \\
+\ A_{j,1} B_{1,k}\, w_j + \cdots + A_{j,n} B_{n,k}\, w_j & \longrightarrow & +\ (AB)_{j,k}\, w_j \\
\quad \vdots & & \quad \vdots \\
+\ A_{m,1} B_{1,k}\, w_m + \cdots + A_{m,n} B_{n,k}\, w_m & \longrightarrow & +\ (AB)_{m,k}\, w_m
\end{array}
$$

---

### Definition of Matrix multiplication

$A$ : $m$-by-$n$, $\quad B$ : $n$-by-$p$, then $AB$ is the $m$-by-$p$ matrix,

defined iff $(\#\text{ columns of } A) = (\#\text{ rows of } B)$, with

$$
(AB)_{j,k} = \sum_r A_{j,r} B_{r,k}
\quad\text{---}\quad \text{row } j \text{ of } A,\ \text{column } k \text{ of } B
$$

$$
\phantom{(AB)_{j,k}} = A_{j,\cdot}\, B_{\cdot,k}
\quad\text{---}\quad \text{row times column}
$$

$$\therefore\ \mathcal{M}(ST) = \mathcal{M}(S)\, \mathcal{M}(T)$$

---

### Columns and rows of a product

$$(AB)_{\cdot,k} = A\, B_{\cdot,k}, \qquad (AB)_{j,\cdot} = A_{j,\cdot}\, B$$

$$
\begin{aligned}
Ab &= b_1\, A_{\cdot,1} + \cdots + b_n\, A_{\cdot,n} \\
aB &= a_1\, B_{1,\cdot} + \cdots + a_n\, B_{n,\cdot}
\end{aligned}
$$

Matrix multiplication is **not commutative** ($AB \ne BA$),
but it **is distributive and associative**.

---

### $Ab$ = linear combination of columns

$A$ : $m$-by-$n$; $\ b = \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix}$, then

$$
Ab
= \begin{bmatrix} \sum_k A_{1,k}\, b_k \\ \vdots \\ \sum_k A_{m,k}\, b_k \end{bmatrix}
= \underbrace{\begin{bmatrix} A_{1,1} \\ \vdots \\ A_{m,1} \end{bmatrix}}_{A_{\cdot,1}} b_1
+ \cdots +
\underbrace{\begin{bmatrix} A_{1,n} \\ \vdots \\ A_{m,n} \end{bmatrix}}_{A_{\cdot,n}} b_n
$$

$\therefore$ linear combination of columns

---

### Product as linear combinations of Columns or Rows

$C$ : $m$-by-$c$, $\quad R$ : $c$-by-$n$, then

$$
\begin{aligned}
(CR)_{\cdot,k} &= C\, R_{\cdot,k} \\
&= R_{1,k}\, C_{\cdot,1} + \cdots + R_{c,k}\, C_{\cdot,c} && \text{combination of columns} \\[1ex]
(CR)_{j,\cdot} &= C_{j,\cdot}\, R \\
&= C_{j,1}\, R_{1,\cdot} + \cdots + C_{j,c}\, R_{c,\cdot} && \text{combination of rows}
\end{aligned}
$$

---

### Column-Row factorization and Rank

1. **column rank** : $\dim \operatorname{span}\{A_{\cdot,1}, \dots, A_{\cdot,n}\}$ in $F^{m,1}$
2. **row rank** : $\dim \operatorname{span}\{A_{1,\cdot}, \dots, A_{m,\cdot}\}$ in $F^{1,n}$

$$
\begin{aligned}
\text{column rank} &\le n && \text{(only } n \text{ columns)} \\
&\le m && \text{(subspace of } F^{m,1}\text{)}
\end{aligned}
$$

---

### Transpose

$A$ : $m$-by-$n$ $\leadsto$ $A^t$ : $n$-by-$m$ (transpose) with $(A^t)_{k,j} = A_{j,k}$

1. $(A+B)^t = A^t + B^t$
2. $(kA)^t = k\,A^t$
3. $(AC)^t = C^t A^t$

---

### Column-Row factorization

Suppose

1. $m$-by-$n$ matrix $A$ (in $F$)
2. column rank of $A \ge 1$

then there exist an $m$-by-$c$ matrix $C$ (in $F$) and a $c$-by-$n$ matrix $R$ (in $F$) with

$$A = CR$$

**Step 1. Construct $C$** — reduce the columns $A_{\cdot,1}, \dots, A_{\cdot,n}$ into a basis of their span;
the basis has length $c$ — column rank.

**Step 2. Construct $R$** — each $A_{\cdot,k}$ is a linear combination of the columns of $C$:

$$A_{\cdot,k} = C\, R_{\cdot,k} \quad\text{---}\quad R_{\cdot,k} = \text{coefficients of the linear combination}$$

---

### Rank

$$\operatorname{rank} A := \text{column rank of } A = \text{row rank of } A$$

**Proof.** Consider $A = CR$ (assume $A \ne 0$):

$$\text{row rank } A \le c = \text{column rank } A$$

because every row of $A$ is a linear combination of the $c$ rows of $R$

$$
\begin{aligned}
\text{column rank } A &= \text{row rank } A^t \\
&\le \text{column rank } A^t \\
&= \text{row rank } A
\end{aligned}
$$

$\blacksquare$
