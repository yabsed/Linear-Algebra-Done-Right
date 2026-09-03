# 3D. Invertibility and Isomorphisms

## Invertible Linear Maps

### Invertible / Inverse

A linear map $T : V \to W$ is **invertible**
$\iff$ there exists a linear map $S : W \to V$ (an **inverse** of $T$) with

$$
\begin{aligned}
ST &= I && \text{on } V \\
TS &= I && \text{on } W
\end{aligned}
$$

---

### Inverse is unique

The inverse of a linear map $T : V \to W$ is **unique** (written $T^{-1}$):

$$
\begin{aligned}
S_1 &= (\phantom{S_2\,} I)\, S_1 \\
&= (S_2\, T)\, S_1 \\
&= S_2\, (T\, S_1) \\
&= S_2\, (\phantom{T\,} I) = S_2
\end{aligned}
$$

---

### Invertible $\iff$ injective & surjective

For a linear map $T : V \to W$:

$$T \text{ invertible} \iff T \text{ injective \& surjective}$$

with $\dim V = \dim W$ (finite-dimensional):

$$T \text{ invertible} \iff T \text{ injective} \iff T \text{ surjective} \qquad (\because\ \text{Fundamental Theorem})$$

**Proof (⇒).** Definition of the properties (of $T$):

$$
\begin{array}{rll}
\text{invertible} : & \forall v \text{ (in } V) \xrightarrow{\;T\;} \exists w \xrightarrow{\;\text{inverse}\;} v & (\therefore\ \text{injective}) \\[0.7ex]
 & \forall w \text{ (in } W) \xrightarrow{\;\text{inverse}\;} \exists v \xrightarrow{\;T\;} w & (\therefore\ \text{surjective}) \\[0.7ex]
\text{injective} : & \ !v \xrightarrow{\;T\;} \forall w \text{ (in range } T) & \\[0.7ex]
\text{surjective} : & \exists v \xrightarrow{\;T\;} \forall w \text{ (in } W) &
\end{array}
$$

**Proof (⇐).** ($T$ is a bijection; define $S : W \to V$)

$$\exists! v \;\xrightarrow{\;T\;}\; \forall w \text{ (in } W) \;\xrightarrow{\;S\;}\; \exists! v$$

($TS = I$ on $W$)

$$\exists! v \;\xrightarrow{\;T\;}\; \forall w \text{ (in } W) \;\xrightarrow{\;S\;}\; \exists! v \;\xrightarrow{\;T\;}\; w$$

($ST = I$ on $V$) — consider $TS = I$ (on $W$):

$$
\begin{array}{r}
\forall v \text{ (in } V) \xrightarrow{\;T\;} w \xrightarrow{\;S\;} (??) \xrightarrow{\;T\;} w \\[0.5ex]
!v \xrightarrow{\;T\;} w
\end{array}
$$

($S$ is linear : additivity)

$$
\begin{array}{r}
w_1 + w_2 \xrightarrow{\;S\;} S(w_1 + w_2) \xrightarrow{\;T\;} w_1 + w_2 \\[0.5ex]
!\,(Sw_1 + Sw_2) \xrightarrow{\;T\;} w_1 + w_2
\end{array}
$$

($S$ is linear : homogeneity)

$$
\begin{array}{r}
aw \xrightarrow{\;S\;} S(aw) \xrightarrow{\;T\;} aw \\[0.5ex]
!\,(a\,Sw) \xrightarrow{\;T\;} aw
\end{array}
$$

---

### $ST = I \iff TS = I$

$\dim V = \dim W$ (finite-dimensional); linear maps $S : W \to V$ and $T : V \to W$, then

$$ST = I \text{ (on } V) \iff TS = I \text{ (on } W)$$

**Proof.** Suppose $ST = I$ (on $V$):

$$
v \;\xrightarrow[\text{null}]{\;T\;}\; 0 \;\xrightarrow[\text{zero}]{\;S\;}\; 0
\qquad\qquad
!\,0 \;\xrightarrow[\text{identity}]{\;ST\;}\; 0
$$

$$\therefore\ \operatorname{null} T = \{0\} \quad\text{---}\quad T \text{ injective \& surjective \& invertible}$$

$$
\begin{aligned}
(ST)(T^{-1}) &= (I)(T^{-1}) \\
S &= T^{-1}
\end{aligned}
$$

---

### Isomorphic vector spaces

1. An **isomorphism** is an invertible linear map
2. $V \cong W$ (**isomorphic**) $\iff$ some isomorphism $V \to W$ exists

---

### $V \cong W \iff \dim V = \dim W$

(finite-dimensional $V$, $W$ over $F$)

$$
\begin{aligned}
V \cong W &\iff \text{invertible } (= \text{bijective}) \text{ linear map } V \to W \text{ exists} \\
&\iff \dim V = \dim W
\end{aligned}
$$

**Proof (⇒).** Fundamental Theorem for an isomorphism $T$:

$$
\begin{aligned}
\dim V &= \dim \operatorname{null} T + \dim \operatorname{range} T \\
\dim V &= \underset{\text{(injective)}}{0} \; + \; \underset{\text{(surjective)}}{\dim W}
\end{aligned}
$$

**Proof (⇐).**

- $\{v_1 \dots v_n\}$ : basis of $V$
- $\{w_1 \dots w_n\}$ : basis of $W$

define a linear map $T : V \to W$ (the isomorphism):

$$v_k \;\xrightarrow{\;T\;}\; w_k$$

$$
\begin{array}{rl}
T \text{ is well-defined \& linear} & \text{---}\quad v\text{'s form a basis of } V \\
T \text{ is surjective} & \text{---}\quad w\text{'s span } W \\
T \text{ is injective} & \text{---}\quad w\text{'s are independent}
\end{array}
$$

---

### Every finite-dimensional $V \cong F^{\dim V}$

$$
\begin{aligned}
\text{every fin-dim } V &\cong F^{\dim V} \\
\mathcal{P}_m(F) &\cong F^{m+1}
\end{aligned}
$$

---

### $\mathcal{L}(V,W) \cong F^{m,n}$

- $\{v_1, \dots, v_n\}$ : basis of $V$ (fixed)
- $\{w_1, \dots, w_m\}$ : basis of $W$ (fixed)

$$\mathcal{L}(V,W) \;\xrightarrow{\;\mathcal{M}\;}\; F^{m,n} \qquad \mathcal{M} \text{ is an isomorphism}$$

$$\therefore\ \mathcal{L}(V,W) \cong F^{m,n}, \qquad \dim \mathcal{L}(V,W) = (\dim V)(\dim W)$$

**Proof.**

$$
\begin{array}{rl}
\text{(linear)} & \mathcal{M}(S+T) = \mathcal{M}(S) + \mathcal{M}(T), \qquad \mathcal{M}(aT) = a\,\mathcal{M}(T) \\[1ex]
\text{(injective)} & \mathcal{M}(T) = 0 \;\implies\; T(v_k) = 0 \text{ for all } k \text{ (bases)} \;\implies\; \operatorname{null} \mathcal{M} = \{0\} \\[1ex]
\text{(surjective)} & v_k \;\xrightarrow{\;T\;}\;
\begin{array}{l}
\phantom{+\ } A_{1,k}\, w_1 \\
\quad \vdots \\
+\ A_{m,k}\, w_m
\end{array}
\;\implies\; \mathcal{M}(T) = A
\end{array}
$$

## Linear maps as matrix multiplication

### Matrix of a vector

If ($v_1, \dots, v_n$ : basis of $V$)

$$
v =
\begin{array}{l}
\phantom{+\ } b_1\, v_1 \\
\quad \vdots \\
+\ b_n\, v_n
\end{array}
\qquad\text{then}\qquad
\mathcal{M}(v) = \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix} \in F^{n,1}
$$

$\therefore$ **matrix of a vector**

---

### $\mathcal{M} : V \to F^{n,1}$ is an isomorphism

$$V \;\xrightarrow{\;\mathcal{M}\;}\; F^{n,1} \text{ is an isomorphism}$$

**because** (linear, by uniqueness of coordinates)

$$
\begin{array}{l}
\phantom{+\ } v = \sum b_k\, v_k \\
+\ u = \sum c_k\, v_k
\end{array}
\qquad\quad
av = \sum (a\,b_k)\, v_k
$$

(bijective)

$$
\begin{array}{l}
\phantom{+\ } b_1\, v_1 \\
\quad \vdots \\
+\ b_n\, v_n
\end{array}
\;\longleftrightarrow\;
\begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix}
$$

---

### $\mathcal{M}(T)_{\cdot,k} = \mathcal{M}(T v_k)$

$$\mathcal{M}(T)_{\cdot,k} = \mathcal{M}(T v_k)$$

**because**

$$
\begin{array}{l}
\phantom{+\ } \mathcal{M}(T)_{1,k}\, w_1 \\
\quad \vdots \\
+\ \mathcal{M}(T)_{m,k}\, w_m
\end{array}
= \ T(v_k)
$$

apply $\mathcal{M}$ to both sides.

---

### $\mathcal{M}(Tv) = \mathcal{M}(T)\,\mathcal{M}(v)$

$$\forall v : \underbrace{\mathcal{M}(Tv)}_{\text{linear map}} = \underbrace{\mathcal{M}(T)\,\mathcal{M}(v)}_{\text{matrix multiplication}}$$

**Proof.**

$$
v =
\begin{array}{l}
\phantom{+\ } b_1\, v_1 \\
\quad \vdots \\
+\ b_n\, v_n
\end{array}
\qquad\quad
Tv =
\begin{array}{l}
\phantom{+\ } b_1\, T(v_1) \\
\quad \vdots \\
+\ b_n\, T(v_n)
\end{array}
$$

$$
\mathcal{M}(Tv) =
\begin{array}{l}
\phantom{+\ } b_1\, \mathcal{M}(Tv_1) \\
\quad \vdots \\
+\ b_n\, \mathcal{M}(Tv_n)
\end{array}
=
\begin{array}{l}
\phantom{+\ } b_1\, \mathcal{M}(T)_{\cdot,1} \\
\quad \vdots \\
+\ b_n\, \mathcal{M}(T)_{\cdot,n}
\end{array}
= \ \mathcal{M}(T)\,\mathcal{M}(v)
$$

---

### $\dim \operatorname{range} T$ = column rank of $\mathcal{M}(T)$

Linear map $T : V \to W$ ($V$, $W$ finite-dimensional):

$$\dim \operatorname{range} T = \text{column rank of } \mathcal{M}(T)$$

— same for every choice of bases, since $\operatorname{range} T$ is basis-free.

**Proof.**

$$\text{isomorphism} : W \;\xrightarrow{\;\mathcal{M}\;}\; F^{m,1}$$

$$
\text{isomorphism} :
\underbrace{\operatorname{span}(Tv_1, \dots, Tv_n)}_{=\ \operatorname{range} T}
\;\xrightarrow{\;\mathcal{M}\;}\;
\underbrace{\operatorname{span}(\mathcal{M}(Tv_1), \dots, \mathcal{M}(Tv_n))}_{=\ \operatorname{span}(\text{columns of } \mathcal{M}(T))}
$$

isomorphic spaces have equal dimension. $\blacksquare$

## Change of basis

### One basis, used twice

Linear map $T : V \to V$ and one basis used twice:

$$\mathcal{M}(T,\, (v_1 \dots v_n)) := \mathcal{M}(T,\, (v_1 \dots v_n),\, (v_1 \dots v_n))$$

---

### Identity matrix

$$I \in F^{n,n} \qquad\text{with}\qquad I_{j,k} = \begin{cases} 1 & j = k \\ 0 & j \ne k \end{cases}$$

For any square $A$ of the same size:

$$AI = IA = A$$

- the symbol $I$ denotes **both** the identity operator and the identity matrix
- for any single basis of $V$ : $\mathcal{M}(I) = I$

---

### Invertible matrix

A square matrix $A$ is **invertible** $\iff$ there exists a square $B$ (same size) with

$$AB = BA = I$$

such $B$ is unique — written $A^{-1}$.

---

### Properties of the matrix inverse

1. $(A^{-1})^{-1} = A$, since $(A^{-1})(A) = A(A^{-1}) = I$

2. $A$, $C$ invertible of the same size $\implies$ $AC$ invertible with $(AC)^{-1} = C^{-1} A^{-1}$ :

$$
\begin{aligned}
(AC)(C^{-1} A^{-1}) &= A\,(C\, C^{-1})\, A^{-1} \\
&= A\,(\phantom{C\, C^{-1}} \llap{I}\,)\, A^{-1} \\
&= A\, A^{-1} = I
\end{aligned}
$$

likewise $(C^{-1} A^{-1})(AC) = I$

---

### Matrix of a product

- $u_1 \dots u_m$ : basis of $U$
- $v_1 \dots v_n$ : basis of $V$ ; linear map $T : U \to V$
- $w_1 \dots w_p$ : basis of $W$ ; linear map $S : V \to W$

$$
\begin{aligned}
&\phantom{=\ } \mathcal{M}(ST,\ u_1 \dots u_m,\ w_1 \dots w_p) \\
&= \mathcal{M}(S,\ v_1 \dots v_n,\ w_1 \dots w_p)\ \mathcal{M}(T,\ u_1 \dots u_m,\ v_1 \dots v_n)
\end{aligned}
$$

$\because\ \mathcal{M}(ST) = \mathcal{M}(S)\,\mathcal{M}(T)$

---

### Identity operator w.r.t. two bases

- $u_1 \dots u_n$ : basis of $V$
- $v_1 \dots v_n$ : basis of $V$

then $\mathcal{M}(I,\,(u),\,(v))$ and $\mathcal{M}(I,\,(v),\,(u))$ are invertible and are **inverses of each other**:

$$\text{column } k \text{ of } \mathcal{M}(I,(u),(v)) = \text{coordinates of } u_k \text{ in the basis } v_1 \dots v_n$$

**because**

$$
\begin{aligned}
I = \mathcal{M}(I,(u),(u)) &= \mathcal{M}(I,(v),(u))\ \mathcal{M}(I,(u),(v)) \\
I = \mathcal{M}(I,(v),(v)) &= \mathcal{M}(I,(u),(v))\ \mathcal{M}(I,(v),(u))
\end{aligned}
$$

---

### Example

$$
\mathcal{M}\big(I,\ ((4,2),(5,3)),\ ((1,0),(0,1))\big) = \begin{bmatrix} 4 & 5 \\ 2 & 3 \end{bmatrix}
$$

$$
\mathcal{M}\big(I,\ ((1,0),(0,1)),\ ((4,2),(5,3))\big) = \begin{bmatrix} 4 & 5 \\ 2 & 3 \end{bmatrix}^{-1} = \begin{bmatrix} 3/2 & -5/2 \\ -1 & 2 \end{bmatrix}
$$

---

### Change-of-basis Formula

Linear map $T : V \to V$ ;

- $u_1 \dots u_n$ : basis of $V$
- $v_1 \dots v_n$ : basis of $V$

$$A = \mathcal{M}(T,(u)), \qquad B = \mathcal{M}(T,(v)), \qquad C = \mathcal{M}(I,(u),(v))$$

then

$$A = C^{-1}(BC)$$

**Proof.**

$$
\begin{aligned}
A &= \mathcal{M}(IT,(u),(u)) \\
&= \mathcal{M}(I,(v),(u))\ \mathcal{M}(T,(u),(v)) \\
&= C^{-1}\ \mathcal{M}(TI,(u),(v)) \\
&= C^{-1}\ \mathcal{M}(T,(v),(v))\ \mathcal{M}(I,(u),(v)) \\
&= C^{-1}\ B\ C
\end{aligned}
$$

---

### Matrix of inverse $=$ inverse of Matrix

Invertible linear map $T : V \to V$ ; $\ v_1 \dots v_n$ : basis of $V$, then

$$\mathcal{M}(T^{-1}) = \big(\mathcal{M}(T)\big)^{-1}$$

**Proof.**

$$
\begin{aligned}
\mathcal{M}(T^{-1})\, \mathcal{M}(T) &= \mathcal{M}(T^{-1}\, T) = \mathcal{M}(I) = I \\
\mathcal{M}(T)\, \mathcal{M}(T^{-1}) &= \mathcal{M}(T\, T^{-1}) = I
\end{aligned}
$$
