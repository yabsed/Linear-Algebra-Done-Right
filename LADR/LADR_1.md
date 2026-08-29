# Ch. 1 Vector Spaces — Final Pass

## 1A. $\mathbf{R}^n$ and $\mathbf{C}^n$

**1.1** $\mathbf{C}=\{a+bi: a,b\in\mathbf{R}\}$, with

$$(a+bi)+(c+di)=(a+c)+(b+d)i,\qquad (a+bi)(c+di)=(ac-bd)+(ad+bc)i.$$

$\mathbf{R}\subseteq\mathbf{C}$ via $a\leftrightarrow a+0i$; write $bi,\,i$. Rule for $\cdot$ is forced by $i^2=-1$ + usual arithmetic (rederive, don't memorize).

**1.3** For all $\alpha,\beta,\lambda\in\mathbf{C}$: commutativity ($\alpha+\beta=\beta+\alpha$, $\alpha\beta=\beta\alpha$); associativity; identities ($\lambda+0=\lambda$, $\lambda1=\lambda$); unique additive inverse; unique multiplicative inverse for $\alpha\neq0$; distributivity $\lambda(\alpha+\beta)=\lambda\alpha+\lambda\beta$. (All checked coordinatewise from properties of $\mathbf{R}$.)

**1.5** $-\alpha$: the additive inverse; $\beta-\alpha:=\beta+(-\alpha)$. For $\alpha\neq0$: $1/\alpha$: the multiplicative inverse; $\beta/\alpha:=\beta(1/\alpha)$.

**1.6** $\mathbf{F}:=\mathbf{R}$ or $\mathbf{C}$ (both fields). Elements of $\mathbf{F}$ = **scalars**. Powers: $\alpha^m=\alpha\cdots\alpha$; $(\alpha^m)^n=\alpha^{mn}$, $(\alpha\beta)^m=\alpha^m\beta^m$.

**1.8** A **list of length $n$** ($n\ge0$): ordered collection of $n$ elements. Equal $\iff$ same length + same elements in same order. Length is finite; $(\,)$ allowed. **1.9** In lists, order & repetition matter: $(3,5)\neq(5,3)$, $(4,4)\neq(4,4,4)$ — unlike sets.

**1.11** Fix $n\in\mathbf{Z}^{+}$.

$$\mathbf{F}^n=\{(x_1,\dots,x_n): x_k\in\mathbf{F}\};\quad x_k=k\text{-th coordinate}.$$

**1.13** $(x_1,\dots,x_n)+(y_1,\dots,y_n)=(x_1+y_1,\dots,x_n+y_n)$.

**1.14** $x+y=y+x$ in $\mathbf{F}^n$. *Pf:* $(x_1+y_1,\dots)=(y_1+x_1,\dots)$ by commutativity in $\mathbf{F}$. $\blacksquare$

**1.15** $0:=(0,\dots,0)$ — same symbol as the number; context decides.

**1.17** $-x=(-x_1,\dots,-x_n)$, the unique vector with $x+(-x)=0$.

**1.18** $\lambda(x_1,\dots,x_n)=(\lambda x_1,\dots,\lambda x_n)$. (Vector$\times$vector coordinatewise mult.: not useful, not used. Scalar$\times$vector is central.)

*Field:* set with distinct $0,1$ and $+,\cdot$ satisfying 1.3 (e.g. $\mathbf{R},\mathbf{C},\mathbf{Q}$, $\{0,1\}$ with $1+1=0$). Most of the book works over any field.

## 1B. Vector Spaces

**1.19** Addition on $V$: function $(u,v)\mapsto u+v\in V$. Scalar multiplication: $(\lambda,v)\mapsto\lambda v\in V$, $\lambda\in\mathbf{F}$.

**1.20 (Definition: vector space).** Set $V$ + addition + scalar multiplication with:

- commutativity: $u+v=v+u$
- associativity: $(u+v)+w=u+(v+w)$, $(ab)v=a(bv)$
- additive identity: $\exists\,0\in V:\ v+0=v\ \forall v$
- additive inverse: $\forall v\ \exists w:\ v+w=0$
- multiplicative identity: $1v=v$
- distributivity: $a(u+v)=au+av$, $(a+b)v=av+bv$

Elements: **vectors** (points). Over $\mathbf{R}$/$\mathbf{C}$: real/complex vector space. $\mathbf{F}^n$ is a VS over $\mathbf{F}$; smallest VS: $\{0\}$.

**1.23** $\mathbf{F}^\infty=\{(x_1,x_2,\dots):x_k\in\mathbf{F}\}$, coordinatewise ops: a VS; identity $(0,0,\dots)$.

**1.24–1.25** $\mathbf{F}^S=\{f:S\to\mathbf{F}\}$ with pointwise ops

$$(f+g)(x)=f(x)+g(x),\qquad(\lambda f)(x)=\lambda f(x).$$

For $S\neq\varnothing$: a VS; identity $0(x)\equiv0$; $(-f)(x)=-f(x)$. Note $\mathbf{F}^n=\mathbf{F}^{\{1,\dots,n\}}$, $\mathbf{F}^\infty=\mathbf{F}^{\{1,2,\dots\}}$.

**1.26 (unique additive identity).** $0'=0'+0=0+0'=0$. $\blacksquare$

**1.27 (unique additive inverse).** $w=w+0=w+(v+w')=(w+v)+w'=0+w'=w'$. $\blacksquare$

**1.28–1.29** $-v$ := the additive inverse; $w-v:=w+(-v)$. Henceforth $V$ = VS over $\mathbf{F}$.

**1.30** $0v=0$ $\forall v\in V$. *Pf:* $0v=(0+0)v=0v+0v$; add $-(0v)$. $\blacksquare$ (Distributivity is essential — the only axiom linking $\cdot$ and $+$.)

**1.31** $a0=0$ $\forall a\in\mathbf{F}$. *Pf:* $a0=a(0+0)=a0+a0$. $\blacksquare$

**1.32** $(-1)v=-v$. *Pf:* $v+(-1)v=(1+(-1))v=0v=0$, so $(-1)v$ is the (unique) inverse. $\blacksquare$

## 1C. Subspaces

**1.33** $U\subseteq V$ is a **subspace** if $U$ is a VS with the same $0$, $+$, $\cdot$ as $V$.

**1.34 (Subspace test).** $U$ is a subspace $\iff$

1. $0\in U$
2. $u,w\in U\Rightarrow u+w\in U$
3. $a\in\mathbf{F},u\in U\Rightarrow au\in U$

*Pf ($\Leftarrow$):* (2),(3) make ops well-defined on $U$; inverses: $-u=(-1)u\in U$ by (3)+1.32; all other axioms are inherited from $V$. $\blacksquare$ ((1) may be replaced by $U\neq\varnothing$, since $0=0u$.)

*Examples:* $\{x\in\mathbf{F}^4: x_3=5x_4+b\}$ subspace $\iff b=0$; continuous fns $\subseteq\mathbf{R}^{[0,1]}$; differentiable fns $\subseteq\mathbf{R}^{\mathbf{R}}$; limit-$0$ sequences $\subseteq\mathbf{C}^\infty$.

*Facts:* $\{0\}$ smallest, $V$ largest subspace; $\varnothing$ is not one. Subspaces of $\mathbf{R}^2$: $\{0\}$, lines through $0$, $\mathbf{R}^2$; of $\mathbf{R}^3$: also planes through $0$.

**1.36 (Sum).** For subspaces $V_1,\dots,V_m$:

$$V_1+\cdots+V_m=\{v_1+\cdots+v_m: v_k\in V_k\}.$$

**1.40** $V_1+\cdots+V_m$ is the **smallest** subspace containing all $V_k$. *Pf:* contains $0$, closed under $+,\cdot$ termwise $\Rightarrow$ subspace (1.34); $V_k\subseteq$ sum (other terms $=0$); any subspace $\supseteq$ each $V_k$ contains all finite sums. $\blacksquare$ (Sum of subspaces $\leftrightarrow$ union of subsets.)

**1.41 (Direct sum).** $V_1+\cdots+V_m$ is **direct** if every element has a *unique* representation $v_1+\cdots+v_m$, $v_k\in V_k$; write $V_1\oplus\cdots\oplus V_m$.

*Example:* $V_k=\{x\in\mathbf{F}^n: x_j=0\ \forall j\neq k\}\Rightarrow \mathbf{F}^n=V_1\oplus\cdots\oplus V_n$.

**1.44 (Nonexample).** $V_1=\{(x,y,0)\}$, $V_2=\{(0,0,z)\}$, $V_3=\{(0,y,y)\}$ in $\mathbf{F}^3$: their sum is $\mathbf{F}^3$, but not direct —

$$(0,0,0)=(0,1,0)+(0,0,1)+(0,-1,-1)=0+0+0.$$

**1.45 (Test via 0).** $V_1+\cdots+V_m$ direct $\iff$ $0=v_1+\cdots+v_m$ ($v_k\in V_k$) forces all $v_k=0$.

*Pf ($\Leftarrow$):* $v=v_1+\cdots+v_m=u_1+\cdots+u_m\Rightarrow 0=(v_1-u_1)+\cdots+(v_m-u_m)$, each $v_k-u_k\in V_k$ (subspace!) $\Rightarrow v_k=u_k$. $\blacksquare$

**1.46 (Two subspaces).**

$$U+W\text{ direct}\iff U\cap W=\{0\}.$$

*Pf:* ($\Rightarrow$) $v\in U\cap W\Rightarrow 0=v+(-v)$, $v\in U$, $-v\in W$; uniqueness $\Rightarrow v=0$.
($\Leftarrow$) $0=u+w\Rightarrow u=-w\in U\cap W=\{0\}\Rightarrow u=w=0$; apply 1.45. $\blacksquare$

**Warning ($m\ge3$).** Pairwise $\cap=\{0\}$ is *not* enough: in 1.44, $V_i\cap V_j=\{0\}$ for all $i\neq j$, yet the sum isn't direct. Use 1.45. (Direct sum $\leftrightarrow$ disjoint union; "disjoint" becomes $\cap=\{0\}$, valid only for two subspaces.)
