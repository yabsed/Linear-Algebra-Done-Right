# Linear Algebra Done Right (4e), Ch. 3A–3C — Condensed Self-Contained Notes

Numbering follows Axler. Facts **(B1)–(B6)** restate Ch. 1–2 results so nothing here depends on the book.

## 0. Standing Assumptions & Background

**Standing assumptions.** $\mathbf F$ denotes $\mathbf R$ or $\mathbf C$; $U, V, W$ denote vector spaces over $\mathbf F$.

**Notation.** $\mathbf F^n$: lists of length $n$; $\mathbf F^\infty$: all sequences in $\mathbf F$; $\mathcal P(\mathbf F)$: all polynomials over $\mathbf F$; $\mathcal P_m(\mathbf F)$: polynomials of degree $\le m$.

**Background facts (Ch. 1–2).**
- **(B1)** \[1.34] A subset of $V$ containing $0$, closed under addition and scalar multiplication, is a subspace.
- **(B2)** $v_1,\dots,v_n$ is a basis of $V$ $\iff$ every $v\in V$ has a **unique** representation $v=c_1v_1+\cdots+c_nv_n$, $c_k\in\mathbf F$.
- **(B3)** \[2.30] Every spanning list can be reduced to a basis of its span.
- **(B4)** \[2.32] In a finite-dimensional space, every linearly independent list extends to a basis.
- **(B5)** \[2.37] If $U$ is a subspace of finite-dimensional $V$, then $\dim U\le\dim V$.
- **(B6)** \[2.39] If moreover $\dim U=\dim V$, then $U=V$.

---

## 3A. Vector Space of Linear Maps

**3.1 Definition (linear map).** $T:V\to W$ is *linear* if for all $u,v\in V$ and $\lambda\in\mathbf F$:

$$T(u+v)=Tu+Tv \quad\text{(additivity)},\qquad T(\lambda v)=\lambda(Tv)\quad\text{(homogeneity)}.$$

Write $Tv$ or $T(v)$. Synonym: *linear transformation*.

**3.2 Notation.** $\mathcal L(V,W)$ = set of linear maps $V\to W$;  $\mathcal L(V)=\mathcal L(V,V)$.

**3.3 Examples** (each is linear — verify):
- **zero** $0\in\mathcal L(V,W)$: $0v=0$ (left $0$ = the map; right $0$ = additive identity of $W$).
- **identity** $I\in\mathcal L(V)$: $Iv=v$.
- **differentiation** $D\in\mathcal L(\mathcal P(\mathbf R))$: $Dp=p'$. Linearity $\iff (f+g)'=f'+g'$ and $(\lambda f)'=\lambda f'$.
- **integration** $T\in\mathcal L(\mathcal P(\mathbf R),\mathbf R)$: $Tp=\int_0^1 p$.
- **multiplication by $x^2$**, $T\in\mathcal L(\mathcal P(\mathbf R))$: $(Tp)(x)=x^2p(x)$.
- **backward shift** $T\in\mathcal L(\mathbf F^\infty)$: $T(x_1,x_2,x_3,\dots)=(x_2,x_3,\dots)$.
- **$\mathbf F^n\to\mathbf F^m$**: for scalars $A_{j,k}\in\mathbf F$,
$$T(x_1,\dots,x_n)=\big(A_{1,1}x_1+\cdots+A_{1,n}x_n,\ \dots,\ A_{m,1}x_1+\cdots+A_{m,n}x_n\big);$$
in fact **every** linear map $\mathbf F^n\to\mathbf F^m$ has this form.
- **composition** with fixed $q\in\mathcal P(\mathbf R)$: $(Tp)(x)=p(q(x))$ defines $T\in\mathcal L(\mathcal P(\mathbf R))$.

**3.4 Linear Map Lemma.** Suppose $v_1,\dots,v_n$ is a basis of $V$ and $w_1,\dots,w_n\in W$. Then there exists a **unique** $T\in\mathcal L(V,W)$ with

$$Tv_k=w_k\qquad(k=1,\dots,n).$$

*Proof.* **Existence.** Define
$$T(c_1v_1+\cdots+c_nv_n)=c_1w_1+\cdots+c_nw_n.$$
By (B2) each $v\in V$ has a unique such representation, so $T:V\to W$ is well defined. Taking $c_k=1$ and the other $c$'s $=0$ gives $Tv_k=w_k$.
Additivity: for $u=\sum a_kv_k$, $v=\sum c_kv_k$,
$$T(u+v)=T\Big(\textstyle\sum(a_k+c_k)v_k\Big)=\sum(a_k+c_k)w_k=\sum a_kw_k+\sum c_kw_k=Tu+Tv.$$
Homogeneity:
$$T(\lambda v)=T\Big(\textstyle\sum \lambda c_kv_k\Big)=\sum\lambda c_kw_k=\lambda\sum c_kw_k=\lambda\,Tv.$$
**Uniqueness.** Suppose $T\in\mathcal L(V,W)$ with $Tv_k=w_k$. Homogeneity gives $T(c_kv_k)=c_kw_k$; additivity then forces
$$T(c_1v_1+\cdots+c_nv_n)=c_1w_1+\cdots+c_nw_n,$$
so $T$ is determined on $\operatorname{span}(v_1,\dots,v_n)=V$. $\blacksquare$

*Meaning:* a linear map can take **arbitrary** prescribed values on a basis (existence), and is **completely determined** by its values on a basis (uniqueness).

**3.5 Definition (operations on $\mathcal L(V,W)$).** For $S,T\in\mathcal L(V,W)$, $\lambda\in\mathbf F$:
$$(S+T)(v)=Sv+Tv,\qquad (\lambda T)(v)=\lambda(Tv)\qquad(v\in V).$$
$S+T$ and $\lambda T$ are again linear (routine check).

**3.6 Theorem.** With these operations, $\mathcal L(V,W)$ **is a vector space**. (Routine; the additive identity is the zero map of 3.3.)

**3.7 Definition (product of linear maps).** If $T\in\mathcal L(U,V)$ and $S\in\mathcal L(V,W)$, define $ST\in\mathcal L(U,W)$ by
$$(ST)(u)=S(Tu)\qquad(u\in U).$$
Thus $ST=S\circ T$; it is defined only when $T$ maps into the domain of $S$, and $ST$ is linear (routine).

**3.8 Theorem (algebra of products).**
- **associativity:** $(T_1T_2)T_3=T_1(T_2T_3)$ whenever the products make sense.
- **identity:** $TI=IT=T$ for $T\in\mathcal L(V,W)$ (first $I$ = identity on $V$, second = identity on $W$).
- **distributivity:** $(S_1+S_2)T=S_1T+S_2T$ and $S(T_1+T_2)=ST_1+ST_2$, for $T,T_1,T_2\in\mathcal L(U,V)$ and $S,S_1,S_2\in\mathcal L(V,W)$.

(Routine proofs.)

**3.9 Non-commutativity.** $ST=TS$ can fail. On $\mathcal P(\mathbf R)$ with $Dp=p'$ and $(Tp)(x)=x^2p(x)$:
$$\big((TD)p\big)(x)=x^2p'(x)\quad\text{but}\quad \big((DT)p\big)(x)=x^2p'(x)+2xp(x),$$
so $TD\ne DT$: differentiate-then-multiply $\ne$ multiply-then-differentiate.

**3.10 Theorem (linear maps take $0$ to $0$).** $T\in\mathcal L(V,W)\implies T(0)=0$.

*Proof.* $T(0)=T(0+0)=T(0)+T(0)$; add $-T(0)$ to both sides. $\blacksquare$

**Consequences.** $f:\mathbf R\to\mathbf R$, $f(x)=mx+b$ is a linear map $\iff b=0$ (by 3.10) — high-school "linear functions" $\ne$ linear maps. Also $\cos$ is not linear: $\cos(x+y)\ne\cos x+\cos y$, $\cos 2x\ne 2\cos x$ in general.

---

## 3B. Null Spaces and Ranges

### Null space and injectivity

**3.11 Definition (null space).** For $T\in\mathcal L(V,W)$:
$$\operatorname{null} T=\{v\in V: Tv=0\}\subseteq V.$$
(Synonym: *kernel*.)

**3.12 Examples.**
- zero map $0:V\to W$: $\operatorname{null}0=V$.
- $\varphi\in\mathcal L(\mathbf C^3,\mathbf C)$, $\varphi(z_1,z_2,z_3)=z_1+2z_2+3z_3$: $\operatorname{null}\varphi=\{z\in\mathbf C^3: z_1+2z_2+3z_3=0\}$.
- differentiation $D\in\mathcal L(\mathcal P(\mathbf R))$: only constants have zero derivative, so $\operatorname{null}D=\{\text{constant functions}\}$.
- multiplication by $x^2$: $x^2p(x)\equiv0\implies p=0$, so $\operatorname{null}T=\{0\}$.
- backward shift: $T(x_1,x_2,\dots)=0\iff x_2=x_3=\cdots=0$, so $\operatorname{null}T=\{(a,0,0,\dots):a\in\mathbf F\}$.

**3.13 Theorem.** $\operatorname{null}T$ is a subspace of $V$.

*Proof.* $T(0)=0$ (3.10) $\Rightarrow 0\in\operatorname{null}T$. If $u,v\in\operatorname{null}T$: $T(u+v)=Tu+Tv=0+0=0$. If $u\in\operatorname{null}T,\ \lambda\in\mathbf F$: $T(\lambda u)=\lambda Tu=\lambda 0=0$. Now apply (B1). $\blacksquare$

**3.14 Definition (injective).** $T:V\to W$ is *injective* (*one-to-one*) if $Tu=Tv\implies u=v$; equivalently, $u\ne v\implies Tu\ne Tv$ (distinct inputs $\mapsto$ distinct outputs).

**3.15 Theorem.** For $T\in\mathcal L(V,W)$:
$$T\ \text{injective}\iff \operatorname{null}T=\{0\}.$$

*Proof.* ($\Rightarrow$) $\{0\}\subseteq\operatorname{null}T$ by 3.10. Conversely, $v\in\operatorname{null}T\Rightarrow T(v)=0=T(0)\Rightarrow v=0$ by injectivity.
($\Leftarrow$) Suppose $\operatorname{null}T=\{0\}$ and $Tu=Tv$. Then
$$0=Tu-Tv=T(u-v)\implies u-v\in\operatorname{null}T=\{0\}\implies u=v.\ \blacksquare$$

*Application:* among the maps of 3.12, only multiplication by $x^2$ is injective (the zero map is injective only in the special case $V=\{0\}$).

### Range and surjectivity

**3.16 Definition (range).** For $T\in\mathcal L(V,W)$:
$$\operatorname{range}T=\{Tv: v\in V\}\subseteq W.$$

**3.17 Examples.**
- zero map: $\operatorname{range}0=\{0\}$.
- $T\in\mathcal L(\mathbf R^2,\mathbf R^3)$, $T(x,y)=(2x,5y,x+y)$: $\operatorname{range}T=\{(2x,5y,x+y):x,y\in\mathbf R\}$.
- differentiation $D\in\mathcal L(\mathcal P(\mathbf R))$: every $q$ has an antiderivative $p$ (i.e. $p'=q$), so $\operatorname{range}D=\mathcal P(\mathbf R)$.

**3.18 Theorem.** $\operatorname{range}T$ is a subspace of $W$.

*Proof.* $0=T(0)\in\operatorname{range}T$. If $w_1=Tv_1,\ w_2=Tv_2$, then $w_1+w_2=T(v_1+v_2)\in\operatorname{range}T$. If $w=Tv,\ \lambda\in\mathbf F$, then $\lambda w=T(\lambda v)\in\operatorname{range}T$. Apply (B1). $\blacksquare$

**3.19 Definition (surjective).** $T:V\to W$ is *surjective* (*onto*) if $\operatorname{range}T=W$.

**3.20 Surjectivity depends on the target space.** $D\in\mathcal L(\mathcal P_5(\mathbf R))$, $Dp=p'$, is **not** surjective ($x^5\notin\operatorname{range}D$); but $S\in\mathcal L(\mathcal P_5(\mathbf R),\mathcal P_4(\mathbf R))$, $Sp=p'$, **is** surjective, since its range equals $\mathcal P_4(\mathbf R)$.

### Fundamental Theorem of Linear Maps

**3.21 Fundamental Theorem of Linear Maps.** If $V$ is finite-dimensional and $T\in\mathcal L(V,W)$, then $\operatorname{range}T$ is finite-dimensional and

$$\boxed{\ \dim V=\dim\operatorname{null}T+\dim\operatorname{range}T.\ }$$

*Proof.* Let $u_1,\dots,u_m$ be a basis of $\operatorname{null}T$, so $\dim\operatorname{null}T=m$. Extend (B4) to a basis
$$u_1,\dots,u_m,v_1,\dots,v_n$$
of $V$; then $\dim V=m+n$. It suffices to show $Tv_1,\dots,Tv_n$ is a basis of $\operatorname{range}T$ (then $\dim\operatorname{range}T=n$).

*Spanning.* Any $v\in V$ writes as $v=a_1u_1+\cdots+a_mu_m+b_1v_1+\cdots+b_nv_n$. Applying $T$ (each $Tu_k=0$):
$$Tv=b_1Tv_1+\cdots+b_nTv_n,$$
so $Tv_1,\dots,Tv_n$ spans $\operatorname{range}T$; in particular $\operatorname{range}T$ is finite-dimensional.

*Independence.* Suppose $c_1Tv_1+\cdots+c_nTv_n=0$. Then $T(c_1v_1+\cdots+c_nv_n)=0$, i.e.
$$c_1v_1+\cdots+c_nv_n\in\operatorname{null}T\implies c_1v_1+\cdots+c_nv_n=d_1u_1+\cdots+d_mu_m$$
for some $d_k\in\mathbf F$. Since $u_1,\dots,u_m,v_1,\dots,v_n$ is linearly independent, all $c$'s (and $d$'s) are $0$. $\blacksquare$

**3.22 Theorem (map to a lower-dimensional space is not injective).** If $V,W$ are finite-dimensional with $\dim V>\dim W$, then no $T\in\mathcal L(V,W)$ is injective.

*Proof.* For any $T\in\mathcal L(V,W)$:
$$\dim\operatorname{null}T=\dim V-\dim\operatorname{range}T\ \ge\ \dim V-\dim W\ >\ 0,$$
using 3.21, then $\operatorname{range}T\subseteq W$ with (B5). So $\operatorname{null}T\ne\{0\}$; apply 3.15. $\blacksquare$

*(E.g., no linear map $\mathbf F^4\to\mathbf F^3$ is injective — no computation needed.)*

**3.24 Theorem (map to a higher-dimensional space is not surjective).** If $\dim V<\dim W$ (both finite), then no $T\in\mathcal L(V,W)$ is surjective.

*Proof.*
$$\dim\operatorname{range}T=\dim V-\dim\operatorname{null}T\ \le\ \dim V\ <\ \dim W,$$
so $\operatorname{range}T\ne W$. $\blacksquare$

**Corollary (previewed in the chapter intro).** If $V$ is finite-dimensional and $T\in\mathcal L(V)$, then
$$T\ \text{injective}\iff T\ \text{surjective},$$
since by 3.15 and 3.21: $\operatorname{null}T=\{0\}\iff\dim\operatorname{range}T=\dim V\iff\operatorname{range}T=V$ (last step by (B6)).

### Application: systems of linear equations

Fix $A_{j,k}\in\mathbf F$ ($j=1,\dots,m$; $k=1,\dots,n$) and define $T:\mathbf F^n\to\mathbf F^m$ by

$$T(x_1,\dots,x_n)=\Big(\sum_{k=1}^n A_{1,k}x_k,\ \dots,\ \sum_{k=1}^n A_{m,k}x_k\Big).\tag{3.25}$$

**Homogeneous case** (*homogeneous* = every constant term is $0$): the system $\sum_{k=1}^n A_{j,k}x_k=0$ ($j=1,\dots,m$) is exactly $T(x_1,\dots,x_n)=0$. It always has $x=0$; a **nonzero** solution exists $\iff\operatorname{null}T\supsetneq\{0\}\iff T$ not injective (3.15).

**3.26 Theorem.** A homogeneous system with **more variables than equations** ($n>m$) has nonzero solutions.

*Proof.* $T:\mathbf F^n\to\mathbf F^m$ with $n>m$: by 3.22, $T$ is not injective. $\blacksquare$
*(E.g., 4 homogeneous equations in 5 variables have a nonzero solution.)*

**Inhomogeneous case:** for $c_1,\dots,c_m\in\mathbf F$, the system
$$\sum_{k=1}^n A_{j,k}x_k=c_j\quad(j=1,\dots,m)\tag{3.27}$$
is exactly $Tx=(c_1,\dots,c_m)$. "No solution for **some** choice of $c$" $\iff\operatorname{range}T\ne\mathbf F^m\iff T$ not surjective.

**3.28 Theorem.** A system with **more equations than variables** ($m>n$) has no solution for some choice of the constant terms.

*Proof.* $n<m$: by 3.24, $T$ is not surjective, so some $c\notin\operatorname{range}T$. $\blacksquare$
*(E.g., 5 equations in 4 variables are unsolvable for some constants.)*

*(3.26 and 3.28 can also be proved via Gaussian elimination; the abstract route above is cleaner.)*

---

## 3C. Matrices

### Matrix of a linear map

**3.29 Definition (matrix).** An *$m$-by-$n$ matrix* $A$ is a rectangular array of elements of $\mathbf F$ with $m$ rows and $n$ columns:
$$A=\begin{pmatrix}A_{1,1}&\cdots&A_{1,n}\\ \vdots&&\vdots\\ A_{m,1}&\cdots&A_{m,n}\end{pmatrix},$$
where $A_{j,k}$ = entry in row $j$, column $k$. **Convention: first index = row, second index = column.**

**3.31 Definition (matrix of a linear map, $\mathcal M(T)$).** Suppose $T\in\mathcal L(V,W)$, with basis $v_1,\dots,v_n$ of $V$ and basis $w_1,\dots,w_m$ of $W$. Then $\mathcal M(T)$ is the $m$-by-$n$ matrix whose entries $A_{j,k}$ are defined by

$$Tv_k=A_{1,k}w_1+\cdots+A_{m,k}w_m=\sum_{j=1}^m A_{j,k}\,w_j.$$

So: **column $k$ of $\mathcal M(T)$ = the coordinates of $Tv_k$ with respect to $w_1,\dots,w_m$.** If the bases are not clear from context, write $\mathcal M\big(T,(v_1,\dots,v_n),(w_1,\dots,w_m)\big)$; $\mathcal M(T)$ depends on the bases as well as on $T$. If $T$ maps an $n$-dimensional space to an $m$-dimensional space, then $\mathcal M(T)$ is $m$-by-$n$.

**Default bases.** For $T:\mathbf F^n\to\mathbf F^m$: standard bases ($e_k$ = 1 in slot $k$, 0 elsewhere); then column $k$ of $\mathcal M(T)$ is $Te_k$ written as a column. For $\mathcal P_m(\mathbf F)$: standard basis $1,x,x^2,\dots,x^m$.

**3.32–3.33 Examples.**
- $T\in\mathcal L(\mathbf F^2,\mathbf F^3)$, $T(x,y)=(x+3y,\,2x+5y,\,7x+9y)$: since $T(1,0)=(1,2,7)$, $T(0,1)=(3,5,9)$,
$$\mathcal M(T)=\begin{pmatrix}1&3\\2&5\\7&9\end{pmatrix}.$$
- $D\in\mathcal L(\mathcal P_3(\mathbf R),\mathcal P_2(\mathbf R))$, $Dp=p'$: since $(x^n)'=nx^{n-1}$,
$$\mathcal M(D)=\begin{pmatrix}0&1&0&0\\0&0&2&0\\0&0&0&3\end{pmatrix}.$$

### Addition and scalar multiplication of matrices

*(Below, assume bases have been fixed for $U,V,W$, the same ones for all maps involved.)*

**3.34 / 3.36 Definitions.** For matrices of the same size, entrywise:
$$(A+C)_{j,k}=A_{j,k}+C_{j,k},\qquad (\lambda A)_{j,k}=\lambda A_{j,k}.$$

**3.35 / 3.38 Theorems.** For $S,T\in\mathcal L(V,W)$ and $\lambda\in\mathbf F$:
$$\mathcal M(S+T)=\mathcal M(S)+\mathcal M(T),\qquad \mathcal M(\lambda T)=\lambda\,\mathcal M(T).$$
(Both follow directly from the definitions — the matrix operations were defined precisely to make these hold.)

**3.39 Notation.** $\mathbf F^{m,n}$ = set of all $m$-by-$n$ matrices with entries in $\mathbf F$.

**3.40 Theorem.** With the operations above, $\mathbf F^{m,n}$ is a vector space and
$$\dim\mathbf F^{m,n}=mn.$$
*Proof.* (Vector-space axioms: routine; additive identity = the zero matrix.) The $mn$ distinct matrices with $1$ in one entry and $0$ elsewhere form a basis. $\blacksquare$

### Matrix multiplication

**Derivation (this is also the proof of 3.43).** Let $u_1,\dots,u_p$ be a basis of $U$; $v_1,\dots,v_n$ of $V$; $w_1,\dots,w_m$ of $W$. Let $T\in\mathcal L(U,V)$, $S\in\mathcal L(V,W)$, $\mathcal M(S)=A$, $\mathcal M(T)=B$. For $1\le k\le p$:

$$(ST)u_k=S\Big(\sum_{r=1}^n B_{r,k}v_r\Big)=\sum_{r=1}^n B_{r,k}\,Sv_r
=\sum_{r=1}^n B_{r,k}\sum_{j=1}^m A_{j,r}w_j
=\sum_{j=1}^m\Big(\sum_{r=1}^n A_{j,r}B_{r,k}\Big)w_j.$$

So $\mathcal M(ST)$ is the $m$-by-$p$ matrix whose $(j,k)$ entry is $\sum_{r=1}^n A_{j,r}B_{r,k}$. Define matrix multiplication to make $\mathcal M(ST)=\mathcal M(S)\mathcal M(T)$ hold:

**3.41 Definition (matrix multiplication).** For $A$ $m$-by-$n$ and $B$ $n$-by-$p$, $AB$ is the $m$-by-$p$ matrix with

$$(AB)_{j,k}=\sum_{r=1}^n A_{j,r}B_{r,k}.$$

Defined **only** when (# columns of $A$) = (# rows of $B$). Entry $(j,k)$: take row $j$ of $A$ and column $k$ of $B$, multiply corresponding entries, sum.

**3.43 Theorem.** If $T\in\mathcal L(U,V)$ and $S\in\mathcal L(V,W)$ (with the same basis of $V$ used for both, same basis of $W$ for $S$ and $ST$, same basis of $U$ for $T$ and $ST$), then
$$\mathcal M(ST)=\mathcal M(S)\,\mathcal M(T).$$
*Proof.* The derivation above. $\blacksquare$

**Properties.** Matrix multiplication is **not commutative** ($AB\ne BA$ in general, even when both are defined), but it **is** distributive and associative.

### Rows, columns, and products

**3.44 Notation.** For $A$ an $m$-by-$n$ matrix:
- $A_{j,\cdot}$ = row $j$ of $A$ (a $1$-by-$n$ matrix), $1\le j\le m$;
- $A_{\cdot,k}$ = column $k$ of $A$ (an $m$-by-$1$ matrix), $1\le k\le n$.

**Convention:** identify a $1$-by-$1$ matrix with its entry.

**3.46 Theorem (entry of product = row times column).** For $A$ $m$-by-$n$, $B$ $n$-by-$p$, $1\le j\le m$, $1\le k\le p$:
$$(AB)_{j,k}=A_{j,\cdot}\,B_{\cdot,k}.$$
*Proof.* By definition,
$$(AB)_{j,k}=A_{j,1}B_{1,k}+\cdots+A_{j,n}B_{n,k},\tag{3.47}$$
and the product of the $1$-by-$n$ matrix $A_{j,\cdot}$ with the $n$-by-$1$ matrix $B_{\cdot,k}$ is the $1$-by-$1$ matrix whose entry is exactly the right side of (3.47). $\blacksquare$

**3.48 Theorem (column of product = matrix times column).** For $1\le k\le p$:
$$(AB)_{\cdot,k}=A\,B_{\cdot,k}.$$
*Proof.* Both sides are $m$-by-$1$. For each $1\le j\le m$, the row-$j$ entry of $(AB)_{\cdot,k}$ is the left side of (3.47), and the row-$j$ entry of $AB_{\cdot,k}$ is the right side of (3.47). $\blacksquare$

**3.49 Example.**
$$\begin{pmatrix}1&2\\3&4\\5&6\end{pmatrix}\begin{pmatrix}5\\1\end{pmatrix}
=\begin{pmatrix}7\\19\\31\end{pmatrix}
=5\begin{pmatrix}1\\3\\5\end{pmatrix}+1\begin{pmatrix}2\\4\\6\end{pmatrix},$$
i.e. the product is a linear combination of the columns, with scalars from the column vector. In general:

**3.50 Theorem (linear combination of columns).** For $A$ $m$-by-$n$ and $b=\begin{pmatrix}b_1\\ \vdots\\ b_n\end{pmatrix}$:
$$Ab=b_1A_{\cdot,1}+\cdots+b_nA_{\cdot,n}.$$
*Proof.* For each $k\in\{1,\dots,m\}$, the row-$k$ entry of $Ab$ is
$$A_{k,1}b_1+\cdots+A_{k,n}b_n,$$
which is also the row-$k$ entry of $b_1A_{\cdot,1}+\cdots+b_nA_{\cdot,n}$. Equal entries in every row $\Rightarrow$ equal matrices. $\blacksquare$

**Row versions** (proved by the same pattern, swapping the roles of rows and columns):
$$(AB)_{j,\cdot}=A_{j,\cdot}\,B,\qquad
aB=a_1B_{1,\cdot}+\cdots+a_nB_{n,\cdot}\quad\text{for } a=\begin{pmatrix}a_1&\cdots&a_n\end{pmatrix}.$$

**3.51 Theorem (product as linear combinations of columns or rows).** Suppose $C$ is $m$-by-$c$ and $R$ is $c$-by-$n$.
- **(a)** For $k\in\{1,\dots,n\}$: column $k$ of $CR$ is a linear combination of the **columns of $C$**, with coefficients from column $k$ of $R$:
$$(CR)_{\cdot,k}=C\,R_{\cdot,k}=R_{1,k}\,C_{\cdot,1}+\cdots+R_{c,k}\,C_{\cdot,c}.$$
- **(b)** For $j\in\{1,\dots,m\}$: row $j$ of $CR$ is a linear combination of the **rows of $R$**, with coefficients from row $j$ of $C$:
$$(CR)_{j,\cdot}=C_{j,\cdot}\,R=C_{j,1}\,R_{1,\cdot}+\cdots+C_{j,c}\,R_{c,\cdot}.$$

*Proof.* (a): first equality by 3.48, second by 3.50. (b): same pattern using the row versions. $\blacksquare$

### Column–row factorization and rank

**3.52 Definition (column rank, row rank).** For $A\in\mathbf F^{m,n}$:
- **column rank** of $A$ $=\dim\operatorname{span}(A_{\cdot,1},\dots,A_{\cdot,n})$ in $\mathbf F^{m,1}$;
- **row rank** of $A$ $=\dim\operatorname{span}(A_{1,\cdot},\dots,A_{m,\cdot})$ in $\mathbf F^{1,n}$.

Both are $\le\min\{m,n\}$: e.g. column rank $\le n$ (only $n$ columns) and $\le m$ (since $\dim\mathbf F^{m,1}=m$, use (B5)).

**3.54 Definition (transpose).** $A^{\mathrm t}$ = matrix obtained by interchanging rows and columns: if $A$ is $m$-by-$n$, then $A^{\mathrm t}$ is $n$-by-$m$ with
$$(A^{\mathrm t})_{k,j}=A_{j,k}.$$
**Properties:** $(A+B)^{\mathrm t}=A^{\mathrm t}+B^{\mathrm t}$, $(\lambda A)^{\mathrm t}=\lambda A^{\mathrm t}$, and $(AC)^{\mathrm t}=C^{\mathrm t}A^{\mathrm t}$ (transpose of a product = product of transposes in the **opposite order**).

**3.56 Theorem (column–row factorization).** Suppose $A$ is $m$-by-$n$ with entries in $\mathbf F$ and column rank $c\ge1$. Then there exist an $m$-by-$c$ matrix $C$ and a $c$-by-$n$ matrix $R$, both with entries in $\mathbf F$, such that
$$A=CR.$$

*Proof.* The list of columns $A_{\cdot,1},\dots,A_{\cdot,n}$ (each in $\mathbf F^{m,1}$) reduces to a basis of its span by (B3); this basis has length $c$ by definition of column rank. Assemble these $c$ columns into $C$. For each $k$, column $k$ of $A$ is a linear combination of the columns of $C$; make its coefficients column $k$ of $R$. Then $A=CR$ by 3.51(a). $\blacksquare$

**3.57 Theorem (column rank = row rank).** For every $A\in\mathbf F^{m,n}$:
$$\text{column rank of }A=\text{row rank of }A.$$

*Proof.* Let $c$ = column rank of $A$. If $c=0$, then $A=0$ and the row rank is also $0$. So assume $c\ge1$ and write $A=CR$ as in 3.56 ($C$: $m$-by-$c$, $R$: $c$-by-$n$). By 3.51(b), every row of $A$ is a linear combination of the $c$ rows of $R$; hence
$$\text{row rank }A\ \le\ c\ =\ \text{column rank }A.$$
Applying this inequality to $A^{\mathrm t}$ (transposing swaps columns and rows):
$$\text{column rank }A=\text{row rank }A^{\mathrm t}\ \le\ \text{column rank }A^{\mathrm t}=\text{row rank }A.$$
The two inequalities give equality. $\blacksquare$

**3.58 Definition (rank).** Since the two notions coincide, define
$$\operatorname{rank}A:=\text{column rank of }A\;(=\text{row rank of }A).$$
