# Finite-Dimensional Vector Spaces

*Condensed, self-contained notes on Chapter 2 of Axler, **Linear Algebra Done Right** (4th ed.). Numbering follows the book. Flow: linear combinations → span → linear independence → linear dependence lemma → independent ≤ spanning → bases → dimension → dim of a sum.*

**Standing assumptions.** $\mathbf{F}$ denotes $\mathbf{R}$ or $\mathbf{C}$. $V$ denotes a vector space over $\mathbf{F}$.

**Recalled from Chapter 1** (everything below is proved from only these):

- A **list** has finite length by definition; order matters and repetitions are allowed.
- **(1.34) Subspace criterion.** $U \subseteq V$ is a subspace $\iff$ $0 \in U$, and $U$ is closed under addition and under scalar multiplication.
- The **sum** $U + W = \{u + w : u \in U,\ w \in W\}$ is the smallest subspace of $V$ containing $U$ and $W$.
- $V = U \oplus W$ (**direct sum**) means every $v \in V$ has a *unique* decomposition $v = u + w$ with $u \in U$, $w \in W$. **(1.46)** $V = U \oplus W \iff V = U + W$ and $U \cap W = \{0\}$.
- $\mathbf{F}^{\mathbf{F}}$ = the vector space of all functions $\mathbf{F} \to \mathbf{F}$ (pointwise operations).

---

## 2A · Span and Linear Independence

**2.1 Notation.** Lists of vectors are written without surrounding parentheses: $(4,1,6),(9,5,7)$ is a list of length two in $\mathbf{R}^3$.

**2.2 Definition (linear combination).** A *linear combination* of a list $v_1,\dots,v_m$ of vectors in $V$ is a vector of the form

$$a_1v_1+\cdots+a_mv_m,\qquad a_1,\dots,a_m\in\mathbf{F}.$$

**2.3 Example.** In $\mathbf{R}^3$:

$$(17,-4,2)=6(2,1,-3)+5(1,-2,4),$$

so $(17,-4,2)$ is a linear combination of $(2,1,-3),(1,-2,4)$. But $(17,-4,5)$ is not, because the system

$$17=2a_1+a_2,\qquad -4=a_1-2a_2,\qquad 5=-3a_1+4a_2$$

has no solution.

**2.4 Definition (span).**

$$\operatorname{span}(v_1,\dots,v_m)=\{a_1v_1+\cdots+a_mv_m : a_1,\dots,a_m\in\mathbf{F}\},\qquad \operatorname{span}(\ ):=\{0\}.$$

(Also called *linear span*.) Thus **(2.5)** $(17,-4,2)\in\operatorname{span}\big((2,1,-3),(1,-2,4)\big)$ while $(17,-4,5)\notin\operatorname{span}\big((2,1,-3),(1,-2,4)\big)$.

**2.6 Theorem (span is the smallest containing subspace).** $\operatorname{span}(v_1,\dots,v_m)$ is the smallest subspace of $V$ containing all of $v_1,\dots,v_m$.

**Proof.** *It is a subspace* (check 1.34):

$$0=0v_1+\cdots+0v_m;$$

$$(a_1v_1+\cdots+a_mv_m)+(c_1v_1+\cdots+c_mv_m)=(a_1{+}c_1)v_1+\cdots+(a_m{+}c_m)v_m;$$

$$\lambda(a_1v_1+\cdots+a_mv_m)=(\lambda a_1)v_1+\cdots+(\lambda a_m)v_m.$$

*It contains each $v_k$:* take $a_k=1$ and all other $a$'s $=0$ in 2.2. *Smallest:* any subspace containing each $v_k$ is closed under scalar multiplication and addition, hence contains every linear combination — i.e. contains the span. ∎

**2.7 Definition.** If $\operatorname{span}(v_1,\dots,v_m)=V$, we say the list $v_1,\dots,v_m$ **spans** $V$.

**2.8 Example.** $\mathbf{F}^n$ is spanned by the $n$ vectors having $1$ in one slot and $0$ elsewhere:

$$(x_1,\dots,x_n)=x_1(1,0,\dots,0)+x_2(0,1,0,\dots,0)+\cdots+x_n(0,\dots,0,1).$$

**2.9 Definition.** $V$ is **finite-dimensional** if some list of vectors in $V$ spans $V$. (Lists are finite, so $\mathbf{F}^n$ is finite-dimensional by 2.8.)

**2.10 Definition (polynomial, $\mathcal{P}(\mathbf{F})$).** A function $p:\mathbf{F}\to\mathbf{F}$ is a *polynomial with coefficients in $\mathbf{F}$* if there exist $a_0,\dots,a_m\in\mathbf{F}$ with

$$p(z)=a_0+a_1z+a_2z^2+\cdots+a_mz^m\qquad\text{for all }z\in\mathbf{F}.$$

$\mathcal{P}(\mathbf{F})$ = the set of all such polynomials. With the usual operations it is a vector space over $\mathbf{F}$ — a subspace of $\mathbf{F}^{\mathbf{F}}$.

**Assumed fact (proved later as 4.8).** A polynomial that is identically $0$ has all coefficients $0$. Hence (subtracting two representations of the same polynomial) the coefficients of a polynomial are uniquely determined by it, so the next definition is unambiguous.

**2.11 Definition (degree).** $p\in\mathcal{P}(\mathbf{F})$ has *degree* $m$, written $\deg p=m$, if $p(z)=a_0+a_1z+\cdots+a_mz^m$ with $a_m\neq0$. Convention: $\deg 0:=-\infty$ and $-\infty<m$ for every integer $m$.

**2.12 Notation.** For a nonnegative integer $m$, $\mathcal{P}_m(\mathbf{F})=\{p\in\mathcal{P}(\mathbf{F}):\deg p\le m\}$. Then

$$\mathcal{P}_m(\mathbf{F})=\operatorname{span}(1,z,\dots,z^m)$$

(slight abuse: $z^k$ denotes the function $z\mapsto z^k$), so each $\mathcal{P}_m(\mathbf{F})$ is finite-dimensional. The convention $-\infty<m$ puts the polynomial $0$ in $\mathcal{P}_m(\mathbf{F})$.

**2.13 Definition.** $V$ is **infinite-dimensional** if it is not finite-dimensional.

**2.14 Example.** $\mathcal{P}(\mathbf{F})$ is infinite-dimensional: any list in $\mathcal{P}(\mathbf{F})$ has a highest degree $m$; every polynomial in its span has degree $\le m$; hence $z^{m+1}$ is not in the span, and no list spans $\mathcal{P}(\mathbf{F})$. ∎

### Linear Independence

**Motivation.** Let $v\in\operatorname{span}(v_1,\dots,v_m)$, say $v=a_1v_1+\cdots+a_mv_m$. If also $v=c_1v_1+\cdots+c_mv_m$, subtracting gives

$$0=(a_1-c_1)v_1+\cdots+(a_m-c_m)v_m.$$

So every vector of the span has a *unique* representation $\iff$ the only way to write $0$ as a linear combination is with all scalars $0$.

**2.15 Definition (linearly independent).** The list $v_1,\dots,v_m$ is *linearly independent* if

$$a_1v_1+\cdots+a_mv_m=0\ \Longrightarrow\ a_1=\cdots=a_m=0.$$

The empty list $(\ )$ is declared linearly independent. Equivalently (by the motivation above): each vector in $\operatorname{span}(v_1,\dots,v_m)$ has exactly one representation as a linear combination of $v_1,\dots,v_m$.

**2.17 Definition (linearly dependent).** Not linearly independent — i.e. there exist $a_1,\dots,a_m\in\mathbf{F}$, not all $0$, with $a_1v_1+\cdots+a_mv_m=0$.

**Basic facts (cf. 2.16, 2.18).**

1. Removing vectors from a linearly independent list leaves a linearly independent list.
2. The standard list of 2.8 is independent in $\mathbf{F}^n$: $a_1(1,0,\dots,0)+\cdots+a_n(0,\dots,0,1)=(a_1,\dots,a_n)=0$ forces $a_1=\cdots=a_n=0$.
3. $1,z,\dots,z^m$ is independent in $\mathcal{P}(\mathbf{F})$: if $a_0+a_1z+\cdots+a_mz^m=0$ for all $z\in\mathbf{F}$, then all $a_k=0$ by the assumed fact (4.8).
4. A list of length one is independent $\iff$ its vector is $\neq 0$.
5. A list of length two is independent $\iff$ neither vector is a scalar multiple of the other.
6. If some vector in the list is a linear combination of the others, the list is dependent (move that vector across the equation; it acquires coefficient $-1\neq0$). In particular, every list containing $0$ is dependent.
7. Concrete: $2(2,3,1)+3(1,-1,2)+(-1)(7,3,8)=(0,0,0)$, so $(2,3,1),(1,-1,2),(7,3,8)$ is dependent in $\mathbf{F}^3$.

**2.19 Linear Dependence Lemma (LDL).** If $v_1,\dots,v_m$ is a linearly dependent list in $V$, then there exists $k\in\{1,\dots,m\}$ such that

$$v_k\in\operatorname{span}(v_1,\dots,v_{k-1}).$$

Moreover, for any such $k$, removing the $k$-th term does not change the span:

$$\operatorname{span}(v_1,\dots,v_{k-1},v_{k+1},\dots,v_m)=\operatorname{span}(v_1,\dots,v_m).$$

**Proof.** Choose $a_1,\dots,a_m\in\mathbf{F}$, not all $0$, with $a_1v_1+\cdots+a_mv_m=0$, and let $k$ be the **largest** index with $a_k\neq0$. Then

$$v_k=-\frac{a_1}{a_k}v_1-\cdots-\frac{a_{k-1}}{a_k}v_{k-1}\in\operatorname{span}(v_1,\dots,v_{k-1}).$$

For the second claim, write

$$v_k=b_1v_1+\cdots+b_{k-1}v_{k-1}.\tag{2.20}$$

If $u=c_1v_1+\cdots+c_mv_m$ is any element of the span, replace $v_k$ by the right side of (2.20): this exhibits $u$ as a linear combination of the list with $v_k$ removed. ∎

**Remarks.** If $k=1$, the condition reads $v_1\in\operatorname{span}(\ )=\{0\}$, i.e. $v_1=0$ (and the proof needs slight modification when $k=1$). From here on, trivial special cases — length-$0$ lists, the subspace $\{0\}$, etc. — remain true but may need slightly different proofs; check them yourself.

**2.21 Example (smallest $k$ in the LDL).** The list $(1,2,3),(6,5,4),(15,16,17),(8,9,7)$ in $\mathbf{R}^3$ is dependent (by 2.23 below). $k=1$ fails: $(1,2,3)\neq0$. $k=2$ fails: $(6,5,4)\neq c(1,2,3)$ for every $c\in\mathbf{R}$. $k=3$ works:

$$(15,16,17)=3(1,2,3)+2(6,5,4).$$

**2.22 Theorem (independent $\le$ spanning).** In a finite-dimensional vector space, the length of every linearly independent list is $\le$ the length of every spanning list.

**Proof.** Let $u_1,\dots,u_m$ be independent in $V$ and let $w_1,\dots,w_n$ span $V$; we prove $m\le n$ by an $m$-step process. Each step adds one $u$, removes one $w$, and keeps a spanning list $B$ of length $n$.

*Step 1.* Let $B=w_1,\dots,w_n$ (spans $V$). Since $u_1\in\operatorname{span}(w_1,\dots,w_n)$, the list

$$u_1,w_1,\dots,w_n$$

is dependent. By the LDL some vector in it lies in the span of the previous ones; it is not $u_1$, because $u_1\neq0$ (independence) and $\operatorname{span}(\ )=\{0\}$. So it is some $w$, which we remove: the new $B$ ($u_1$ plus the remaining $w$'s) has length $n$ and spans $V$.

*Step $k$ ($k=2,\dots,m$).* The list $B$ from step $k{-}1$ spans $V$, so $u_k\in\operatorname{span}(B)$, and inserting $u_k$ just after $u_1,\dots,u_{k-1}$ gives a dependent list of length $n{+}1$. By the LDL some vector lies in the span of the previous ones; it cannot be a $u$, because $u_1,\dots,u_k$ is independent. Hence at least one $w$ still remains, and we may remove a $w$ that is a linear combination of the previous vectors: the new $B$ ($u_1,\dots,u_k$ plus the remaining $w$'s) has length $n$ and spans $V$.

After step $m$ all $u$'s have been added; each step removed a distinct $w$; hence $n\ge m$. ∎

**2.23–2.24 Consequences (no computation needed).**

- $(1,0,0),(0,1,0),(0,0,1)$ spans $\mathbf{R}^3$ ⇒ no list of length $\ge4$ — e.g. $(1,2,3),(4,5,8),(9,6,7),(-3,2,8)$ — is linearly independent in $\mathbf{R}^3$.
- $(1,0,0,0),(0,1,0,0),(0,0,1,0),(0,0,0,1)$ is independent in $\mathbf{R}^4$ ⇒ no list of length $\le3$ — e.g. $(1,2,3,-5),(4,5,8,3),(9,6,7,-1)$ — spans $\mathbf{R}^4$.

**2.25 Theorem.** Every subspace of a finite-dimensional vector space is finite-dimensional.

**Proof.** Let $U$ be a subspace of a finite-dimensional $V$. Construct:

*Step 1:* if $U=\{0\}$, done. Else choose $u_1\in U$ with $u_1\neq0$.
*Step $k$:* if $U=\operatorname{span}(u_1,\dots,u_{k-1})$, done. Else choose $u_k\in U$ with $u_k\notin\operatorname{span}(u_1,\dots,u_{k-1})$.

As long as the process runs, no vector of the constructed list is in the span of the previous ones, so each list is linearly independent (LDL). By 2.22 an independent list cannot be longer than a spanning list of $V$, so the process terminates — i.e. $U$ equals the span of a finite list. ∎

---

## 2B · Bases

**2.26 Definition.** A **basis** of $V$ is a list of vectors in $V$ that is linearly independent and spans $V$.

**2.27 Examples.**

- (a) The **standard basis** of $\mathbf{F}^n$: $(1,0,\dots,0),(0,1,0,\dots,0),\dots,(0,\dots,0,1)$.
- (b) $(1,2),(3,5)$ is a basis of $\mathbf{F}^2$ — and so is $(7,5),(-4,9)$: bases are not unique.
- (c) $(1,2,-4),(7,-5,6)$ is independent in $\mathbf{F}^3$ but does not span $\mathbf{F}^3$ ⇒ not a basis.
- (d) $(1,2),(3,5),(4,13)$ spans $\mathbf{F}^2$ but is dependent ⇒ not a basis.
- (e) $(1,1,0),(0,0,1)$ is a basis of $\{(x,x,y)\in\mathbf{F}^3:x,y\in\mathbf{F}\}$.
- (f) $(1,-1,0),(1,0,-1)$ is a basis of $\{(x,y,z)\in\mathbf{F}^3:x+y+z=0\}$.
- (g) $1,z,\dots,z^m$ is the **standard basis** of $\mathcal{P}_m(\mathbf{F})$.

**2.28 Theorem (criterion for basis).** $v_1,\dots,v_n$ is a basis of $V$ $\iff$ every $v\in V$ can be written **uniquely** in the form

$$v=a_1v_1+\cdots+a_nv_n,\qquad a_1,\dots,a_n\in\mathbf{F}.\tag{2.29}$$

**Proof.** ($\Rightarrow$) Spanning gives existence of (2.29). If also $v=c_1v_1+\cdots+c_nv_n$, subtracting gives

$$0=(a_1-c_1)v_1+\cdots+(a_n-c_n)v_n,$$

and independence forces $a_k=c_k$ for every $k$: uniqueness.
($\Leftarrow$) Existence for every $v$ means the list spans $V$. Uniqueness applied to $v=0$ means $0=a_1v_1+\cdots+a_nv_n$ only for $a_1=\cdots=a_n=0$: independence. ∎

**2.30 Theorem (every spanning list contains a basis).** Every spanning list in a vector space can be reduced to a basis by deleting some (possibly none) of its vectors.

**Proof.** Suppose $v_1,\dots,v_n$ spans $V$. Start with $B=v_1,\dots,v_n$ and run:

*Step 1:* if $v_1=0$, delete $v_1$ from $B$.
*Step $k$:* if $v_k\in\operatorname{span}(v_1,\dots,v_{k-1})$, delete $v_k$ from $B$.

Stop after step $n$. The final $B$ still spans $V$: only vectors already in the span of the previous ones were discarded (second part of the LDL). The process ensures no vector of $B$ is in the span of the previous ones, so $B$ is independent (LDL). Hence $B$ is a basis. ∎

**Example.** Applied to $(1,2),(3,6),(4,7),(5,9)$ in $\mathbf{F}^2$, the procedure deletes the 2nd and 4th vectors, leaving the basis $(1,2),(4,7)$.

**2.31 Corollary.** Every finite-dimensional vector space has a basis.

**Proof.** By definition it has a spanning list; reduce it via 2.30. ∎

**2.32 Theorem (every independent list extends to a basis).** Every linearly independent list in a finite-dimensional vector space can be extended (possibly by nothing) to a basis of the space. *(Dual of 2.30.)*

**Proof.** Let $u_1,\dots,u_m$ be independent in $V$, and let $w_1,\dots,w_n$ span $V$. Then

$$u_1,\dots,u_m,w_1,\dots,w_n$$

spans $V$; apply the procedure of 2.30. No $u$ gets deleted: $u_k\in\operatorname{span}(u_1,\dots,u_{k-1})$ would make $u_1,\dots,u_k$ dependent, contradicting independence (fact 1). The resulting basis consists of $u_1,\dots,u_m$ and some of the $w$'s. ∎

**Example.** In $\mathbf{F}^3$, extending the independent list $(2,3,4),(9,6,8)$ with the standard basis as the $w$'s produces the basis $(2,3,4),(9,6,8),(0,1,0)$.

**2.33 Theorem (every subspace is a direct summand).** If $V$ is finite-dimensional and $U$ is a subspace of $V$, then there is a subspace $W$ of $V$ such that

$$V=U\oplus W.$$

*(With more advanced tools, the finite-dimensionality hypothesis can be dropped.)*

**Proof.** $U$ is finite-dimensional (2.25), so it has a basis $u_1,\dots,u_m$ (2.31). This list is independent in $V$, hence extends to a basis $u_1,\dots,u_m,w_1,\dots,w_n$ of $V$ (2.32). Put $W=\operatorname{span}(w_1,\dots,w_n)$. By 1.46 it suffices to show $V=U+W$ and $U\cap W=\{0\}$.

*$V=U+W$:* the full list spans $V$, so every $v\in V$ is

$$v=\underbrace{a_1u_1+\cdots+a_mu_m}_{u\,\in\,U}+\underbrace{b_1w_1+\cdots+b_nw_n}_{w\,\in\,W},$$

i.e. $v=u+w\in U+W$.

*$U\cap W=\{0\}$:* if $v\in U\cap W$, then

$$v=a_1u_1+\cdots+a_mu_m=b_1w_1+\cdots+b_nw_n$$

for some scalars, so

$$a_1u_1+\cdots+a_mu_m-b_1w_1-\cdots-b_nw_n=0,$$

and independence of $u_1,\dots,u_m,w_1,\dots,w_n$ forces all $a$'s and $b$'s to be $0$; hence $v=0$. ∎

---

## 2C · Dimension

A reasonable definition should give $\dim\mathbf{F}^n=n$, and the standard basis of $\mathbf{F}^n$ has length $n$ — suggesting "dimension = length of a basis." This makes sense only if all bases of a space have the same length:

**2.34 Theorem (basis length does not depend on basis).** Any two bases of a finite-dimensional vector space have the same length.

**Proof.** Let $B_1,B_2$ be bases of $V$. $B_1$ is independent and $B_2$ spans, so $\operatorname{length}(B_1)\le\operatorname{length}(B_2)$ by 2.22. Interchanging the roles of $B_1$ and $B_2$ gives the reverse inequality. ∎

**2.35 Definition.** The **dimension** of a finite-dimensional vector space $V$, denoted $\dim V$, is the length of any basis of $V$.

**2.36 Examples.**

$$\dim\mathbf{F}^n=n,\qquad \dim\mathcal{P}_m(\mathbf{F})=m+1,$$

$$\dim\{(x,x,y)\in\mathbf{F}^3:x,y\in\mathbf{F}\}=2,\qquad \dim\{(x,y,z)\in\mathbf{F}^3:x+y+z=0\}=2,$$

with bases exhibited in 2.27 (a), (g), (e), (f) respectively.

Every subspace of a finite-dimensional space is finite-dimensional (2.25) and so has a dimension. Moreover:

**2.37 Theorem (dimension of a subspace).** If $V$ is finite-dimensional and $U$ is a subspace of $V$, then $\dim U\le\dim V$.

**Proof.** A basis of $U$ is an independent list in $V$; a basis of $V$ is a spanning list in $V$; apply 2.22. ∎

**Warning (the field matters).** $\dim_{\mathbf{R}}\mathbf{R}^2=2$ but $\dim_{\mathbf{C}}\mathbf{C}=1$, although $\mathbf{R}^2$ can be identified with $\mathbf{C}$ as a set, with the same addition and the same multiplication by real scalars. The choice of $\mathbf{F}$ cannot be neglected.

By definition, a basis must satisfy two properties: independence and spanning. If the list already has length $\dim V$, checking either one suffices:

**2.38 Theorem (independent list of the right length).** If $V$ is finite-dimensional, then every linearly independent list in $V$ of length $\dim V$ is a basis of $V$.

**Proof.** Let $n=\dim V$ and let $v_1,\dots,v_n$ be independent. It extends to a basis of $V$ (2.32); every basis has length $n$, so the extension adjoins nothing — $v_1,\dots,v_n$ is already a basis. ∎

**2.39 Theorem (subspace of full dimension).** If $U$ is a subspace of a finite-dimensional $V$ with $\dim U=\dim V$, then $U=V$.

**Proof.** A basis $u_1,\dots,u_n$ of $U$ is an independent list in $V$ of length $\dim V$, hence a basis of $V$ (2.38). So every $v\in V$ is a linear combination of $u_1,\dots,u_n\in U$, giving $v\in U$. ∎

**2.40 Example.** $(5,7),(4,3)$ is independent in $\mathbf{F}^2$ (neither vector is a scalar multiple of the other) and has length $2=\dim\mathbf{F}^2$, hence is a basis of $\mathbf{F}^2$ — no need to check spanning.

**2.41 Example (basis of a subspace via dimension).** Let

$$U=\{p\in\mathcal{P}_3(\mathbf{R}):p'(5)=0\}.$$

Each of $1,\ (x-5)^2,\ (x-5)^3$ lies in $U$. Independence: if

$$a+b(x-5)^2+c(x-5)^3=0\qquad\text{for all }x\in\mathbf{R},$$

then the left side has $x^3$-coefficient $c$, so $c=0$; then its $x^2$-coefficient is $b$, so $b=0$; then $a=0$. Hence $3\le\dim U$, and by 2.37,

$$3\le\dim U\le\dim\mathcal{P}_3(\mathbf{R})=4.$$

The polynomial $x$ is not in $U$ (its derivative is the constant $1$), so $U\neq\mathcal{P}_3(\mathbf{R})$ and thus $\dim U\neq4$ (2.39). Therefore $\dim U=3$, and the independent list $1,(x-5)^2,(x-5)^3$ in $U$, having length $\dim U$, is a basis of $U$ (2.38).

**2.42 Theorem (spanning list of the right length).** If $V$ is finite-dimensional, then every spanning list of length $\dim V$ is a basis of $V$.

**Proof.** Let $n=\dim V$ and suppose $v_1,\dots,v_n$ spans $V$. It reduces to a basis (2.30); every basis has length $n$, so nothing is deleted — $v_1,\dots,v_n$ is already a basis. ∎

**2.43 Theorem (dimension of a sum).** If $V_1$ and $V_2$ are subspaces of a finite-dimensional vector space, then

$$\dim(V_1+V_2)=\dim V_1+\dim V_2-\dim(V_1\cap V_2).$$

*(Analogue of inclusion–exclusion for finite sets: $\#(S_1\cup S_2)=\#S_1+\#S_2-\#(S_1\cap S_2)$.)*

**Proof.** Let $v_1,\dots,v_m$ be a basis of $V_1\cap V_2$, so $\dim(V_1\cap V_2)=m$. It is independent in $V_1$ and in $V_2$, hence extends (2.32) to bases

$$v_1,\dots,v_m,u_1,\dots,u_j\ \text{ of }V_1,\qquad v_1,\dots,v_m,w_1,\dots,w_k\ \text{ of }V_2,$$

so $\dim V_1=m+j$ and $\dim V_2=m+k$. It suffices to show that

$$v_1,\dots,v_m,\,u_1,\dots,u_j,\,w_1,\dots,w_k\tag{2.44}$$

is a basis of $V_1+V_2$, for then

$$\dim(V_1+V_2)=m+j+k=(m+j)+(m+k)-m=\dim V_1+\dim V_2-\dim(V_1\cap V_2).$$

*Spanning.* The list (2.44) is contained in $V_1\cup V_2\subseteq V_1+V_2$, and its span contains $V_1$ and contains $V_2$; hence its span equals $V_1+V_2$ (the smallest subspace containing both).

*Independence.* Suppose

$$a_1v_1+\cdots+a_mv_m+b_1u_1+\cdots+b_ju_j+c_1w_1+\cdots+c_kw_k=0.$$

Rewrite this as

$$c_1w_1+\cdots+c_kw_k=-a_1v_1-\cdots-a_mv_m-b_1u_1-\cdots-b_ju_j\in V_1,\tag{2.45}$$

while the left side also lies in $V_2$; hence $c_1w_1+\cdots+c_kw_k\in V_1\cap V_2$, so

$$c_1w_1+\cdots+c_kw_k=d_1v_1+\cdots+d_mv_m$$

for some scalars $d_1,\dots,d_m$. But $v_1,\dots,v_m,w_1,\dots,w_k$ is independent (a basis of $V_2$), so all the $c$'s (and $d$'s) equal $0$. Then (2.45) becomes

$$a_1v_1+\cdots+a_mv_m+b_1u_1+\cdots+b_ju_j=0,$$

and independence of $v_1,\dots,v_m,u_1,\dots,u_j$ (a basis of $V_1$) forces all the $a$'s and $b$'s to $0$. ∎

**Sets ↔ vector spaces analogy.** For a finite set $S$, let $\#S$ be its number of elements.

| finite sets | finite-dimensional vector spaces |
|---|---|
| $\#S$ | $\dim V$ |
| union $S_1\cup S_2$ = smallest subset containing $S_1,S_2$ | sum $V_1+V_2$ = smallest subspace containing $V_1,V_2$ |
| $\#(S_1\cup S_2)=\#S_1+\#S_2-\#(S_1\cap S_2)$ | $\dim(V_1+V_2)=\dim V_1+\dim V_2-\dim(V_1\cap V_2)$ |
| $\#(S_1\cup S_2)=\#S_1+\#S_2\iff S_1\cap S_2=\varnothing$ | $\dim(V_1+V_2)=\dim V_1+\dim V_2\iff V_1\cap V_2=\{0\}$ |
| $S_1\cup\cdots\cup S_m$ disjoint $\iff \#(S_1\cup\cdots\cup S_m)=\#S_1+\cdots+\#S_m$ | $V_1+\cdots+V_m$ direct $\iff \dim(V_1+\cdots+V_m)=\dim V_1+\cdots+\dim V_m$ *(proved later, 3.94)* |
