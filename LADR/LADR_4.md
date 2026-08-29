# LADR (4e) Chapter 4 — Polynomials: Self-Contained Condensed Notes

**Scope.** Everything in Chapter 4 except the exercises. All proofs are complete. Trimmed only: the numerical example 4.3 ($z = 3+2i$ arithmetic) and the approximate-roots quintic example. This chapter's results feed the study of operators ($T\colon V \to V$) in later chapters.

**Standing assumption.** $\mathbf{F}$ denotes $\mathbf{R}$ or $\mathbf{C}$.

**Notation and imported facts** (used without proof):

1. $\mathcal{P}(\mathbf{F})$ = polynomial functions $\mathbf{F} \to \mathbf{F}$; $\mathcal{P}_n(\mathbf{F})$ = those of degree $\le n$, a vector space with $\dim \mathcal{P}_n(\mathbf{F}) = n+1$ (standard basis $1, z, \dots, z^n$).
2. (LADR 2.38) In a finite-dimensional vector space $V$, every linearly independent list of length $\dim V$ is a basis of $V$.
3. (Analysis) A continuous function from a closed disk in $\mathbf{R}^2$ to $\mathbf{R}$ attains a minimum on that disk.
4. (Polar form) Every $w \in \mathbf{C}$ can be written $w = r(\cos\theta + i\sin\theta)$ for some $r \ge 0$, $\theta \in \mathbf{R}$.

---

## 1. Complex Numbers

**4.1 (Definition: $\operatorname{Re} z$, $\operatorname{Im} z$).** For $z = a + bi$ with $a, b \in \mathbf{R}$:

$$\operatorname{Re} z := a, \qquad \operatorname{Im} z := b, \qquad \text{so} \quad z = \operatorname{Re} z + (\operatorname{Im} z)\,i.$$

**4.2 (Definition: conjugate, absolute value).** For $z \in \mathbf{C}$:

$$\bar{z} := \operatorname{Re} z - (\operatorname{Im} z)\,i, \qquad \lvert z \rvert := \sqrt{(\operatorname{Re} z)^2 + (\operatorname{Im} z)^2}.$$

**Remarks.** $z \leftrightarrow (\operatorname{Re} z, \operatorname{Im} z)$ identifies $\mathbf{C}$ with $\mathbf{R}^2$. Thus $\mathbf{C}$ is a $1$-dimensional **complex** vector space, but also (as $\mathbf{R}^2$) a $2$-dimensional **real** vector space. $\lvert z \rvert \ge 0$ is the distance from the origin to $(\operatorname{Re} z, \operatorname{Im} z)$. Also:

$$z = \bar{z} \iff z \in \mathbf{R}.$$

**4.4 (Properties of complex numbers).** For all $w, z \in \mathbf{C}$:

- **(a)** sum of $z$ and $\bar z$: $\quad z + \bar{z} = 2\operatorname{Re} z$
- **(b)** difference of $z$ and $\bar z$: $\quad z - \bar{z} = 2(\operatorname{Im} z)\,i$
- **(c)** product of $z$ and $\bar z$: $\quad z\bar{z} = \lvert z \rvert^2$
- **(d)** conjugate is additive and multiplicative: $\quad \overline{w + z} = \bar{w} + \bar{z}\,$ and $\,\overline{wz} = \bar{w}\,\bar{z}$
- **(e)** double conjugate: $\quad \bar{\bar{z}} = z$
- **(f)** $\operatorname{Re}, \operatorname{Im}$ bounded by $\lvert z \rvert$: $\quad \lvert \operatorname{Re} z \rvert \le \lvert z \rvert\,$ and $\,\lvert \operatorname{Im} z \rvert \le \lvert z \rvert$
- **(g)** absolute value of the conjugate: $\quad \lvert \bar{z} \rvert = \lvert z \rvert$
- **(h)** absolute value is multiplicative: $\quad \lvert wz \rvert = \lvert w \rvert \, \lvert z \rvert$
- **(i)** triangle inequality: $\quad \lvert w + z \rvert \le \lvert w \rvert + \lvert z \rvert$

*Proof.* (a)–(h) are direct computations from $z = a + bi$, $w = c + di$ with the definitions above. For (i):

$$
\begin{aligned}
\lvert w+z \rvert^2 &= (w+z)\overline{(w+z)} = (w+z)(\bar w + \bar z) && \text{by (c), (d)}\\
&= w\bar w + z\bar z + w\bar z + z\bar w \\
&= \lvert w \rvert^2 + \lvert z \rvert^2 + w\bar z + \overline{w\bar z} && \text{since } z\bar w = \bar w\,\bar{\bar z} = \overline{w\bar z} \text{ by (d), (e)}\\
&= \lvert w \rvert^2 + \lvert z \rvert^2 + 2\operatorname{Re}(w\bar z) && \text{by (a)}\\
&\le \lvert w \rvert^2 + \lvert z \rvert^2 + 2\lvert w\bar z \rvert && \text{by (f)}\\
&= \lvert w \rvert^2 + \lvert z \rvert^2 + 2\lvert w \rvert\,\lvert z \rvert && \text{by (h), (g)}\\
&= (\lvert w \rvert + \lvert z \rvert)^2.
\end{aligned}
$$

Taking square roots gives $\lvert w+z \rvert \le \lvert w \rvert + \lvert z \rvert$. (Geometric meaning: each side of a triangle is at most the sum of the other two sides.) $\blacksquare$

---

## 2. Zeros of Polynomials

**Definition (polynomial of degree $m$).** A function $p\colon \mathbf{F} \to \mathbf{F}$ is a *polynomial of degree $m$* if there exist $a_0, \dots, a_m \in \mathbf{F}$ with $a_m \ne 0$ such that

$$p(z) = a_0 + a_1 z + \cdots + a_m z^m \qquad \forall z \in \mathbf{F}.$$

A priori $p$ could have more than one degree if this representation were not unique; the Corollary after 4.8 rules this out.

**4.5 (Definition: zero).** $\lambda \in \mathbf{F}$ is a *zero* (or *root*) of $p \in \mathcal{P}(\mathbf{F})$ if $p(\lambda) = 0$.

**4.6 (Each zero corresponds to a degree-one factor).** Let $m \ge 1$, $\deg p = m$, $\lambda \in \mathbf{F}$. Then

$$p(\lambda) = 0 \iff \exists\, q \in \mathcal{P}(\mathbf{F}) \text{ with } \deg q = m-1 \text{ and } p(z) = (z - \lambda)q(z) \ \ \forall z \in \mathbf{F}.$$

*Proof.* ($\Rightarrow$) Write $p(z) = \sum_{k=0}^{m} a_k z^k$, $a_m \ne 0$. Since $p(\lambda) = 0$,

$$p(z) = p(z) - p(\lambda) = \sum_{k=1}^{m} a_k\,(z^k - \lambda^k). \qquad \text{(4.7)}$$

Key telescoping identity, for each $k \in \{1, \dots, m\}$:

$$z^k - \lambda^k = (z - \lambda)\sum_{j=1}^{k} \lambda^{\,j-1} z^{\,k-j},$$

i.e. $z^k - \lambda^k$ is $(z-\lambda)$ times a polynomial of degree $k-1$. Substituting into (4.7):

$$p(z) = (z-\lambda)\,q(z), \qquad q(z) := \sum_{k=1}^{m} a_k \sum_{j=1}^{k} \lambda^{\,j-1} z^{\,k-j}.$$

The coefficient of $z^{m-1}$ in $q$ comes only from $(k, j) = (m, 1)$ and equals $a_m \ne 0$, so $\deg q = m - 1$.

($\Leftarrow$) $p(\lambda) = (\lambda - \lambda)q(\lambda) = 0$. $\blacksquare$

**4.8 (Degree $m$ implies at most $m$ zeros).** If $m \ge 1$ and $\deg p = m$, then $p$ has at most $m$ zeros in $\mathbf{F}$.

*Proof.* Induction on $m$. Base $m = 1$: $p = a_0 + a_1 z$ with $a_1 \ne 0$ has exactly one zero, $-a_0/a_1$. Step: let $m > 1$ and assume the result for $m-1$. If $p$ has no zeros, done. Otherwise let $\lambda$ be a zero; by 4.6,

$$p(z) = (z-\lambda)q(z) \ \ \forall z, \qquad \deg q = m-1.$$

This equation shows $\{\text{zeros of } p\} = \{\text{zeros of } q\} \cup \{\lambda\}$. By induction $q$ has at most $m-1$ zeros, so $p$ has at most $m$. $\blacksquare$

**Corollary (coefficients and degree are unique).** If $\sum_k a_k z^k = \sum_k b_k z^k$ for all $z \in \mathbf{F}$, then $a_k = b_k$ for every $k$. Indeed, subtracting gives a polynomial $\sum_k (a_k - b_k) z^k$ that vanishes on all of $\mathbf{F}$ — infinitely many points, since $\mathbf{F} \in \{\mathbf{R}, \mathbf{C}\}$ is infinite. If some coefficient were nonzero, this polynomial would have a degree $d$: a nonzero constant ($d = 0$) has no zeros, and a polynomial of degree $d \ge 1$ has at most $d$ zeros by 4.8 — contradiction either way. In particular, **the degree of a polynomial is well defined**.

**Convention.** $\deg 0 := -\infty$, with the arithmetic $-\infty < m$ and $-\infty + m = -\infty$ for every integer $m$. Purpose: results like

$$\deg(pq) = \deg p + \deg q$$

then hold with no exceptional cases.

---

## 3. Division Algorithm for Polynomials

Integer model: for nonnegative integers $p, s$ with $s \ne 0$, there exist $q, r \ge 0$ with $p = sq + r$ and $r < s$. The polynomial analogue (a result, not literally an algorithm):

**4.9 (Division algorithm).** Let $p, s \in \mathcal{P}(\mathbf{F})$ with $s \ne 0$. Then there exist **unique** $q, r \in \mathcal{P}(\mathbf{F})$ such that

$$p = sq + r \qquad \text{and} \qquad \deg r < \deg s.$$

*Proof.* Let $n = \deg p$, $m = \deg s$.

**Case $n < m$.** Existence: take $q = 0$, $r = p$. Uniqueness: if $p = sq + r$ with $\deg r < m$ and $q \ne 0$, then $\deg(sq) = m + \deg q \ge m > \deg r$, hence $\deg p = \deg(sq + r) = \deg(sq) \ge m > n$ — contradiction. So $q = 0$, forcing $r = p$.

**Case $n \ge m$.** The list

$$1,\ z,\ \dots,\ z^{m-1},\ \ s,\ zs,\ \dots,\ z^{\,n-m}s \qquad \text{(4.10)}$$

is linearly independent in $\mathcal{P}_n(\mathbf{F})$, because its entries have pairwise distinct degrees $0, 1, \dots, m-1, m, m+1, \dots, n$. Its length is $m + (n-m+1) = n+1 = \dim \mathcal{P}_n(\mathbf{F})$, so by imported fact 2 (LADR 2.38) it is a **basis** of $\mathcal{P}_n(\mathbf{F})$. Since $p \in \mathcal{P}_n(\mathbf{F})$, there exist unique $a_0, \dots, a_{m-1}, b_0, \dots, b_{n-m} \in \mathbf{F}$ with

$$p = \underbrace{a_0 + a_1 z + \cdots + a_{m-1}z^{m-1}}_{=:\ r} \;+\; s\,\underbrace{(b_0 + b_1 z + \cdots + b_{n-m}z^{\,n-m})}_{=:\ q}. \qquad \text{(4.11)}$$

This gives existence with $\deg r \le m - 1 < \deg s$.

Uniqueness: suppose $p = s\tilde q + \tilde r$ with $\deg \tilde r < m$. First, $\deg \tilde q \le n - m$; otherwise $\deg(s\tilde q) = m + \deg \tilde q > n$ while $\deg \tilde r < m \le \deg(s\tilde q)$, so $\deg p = \deg(s\tilde q) > n$ — contradiction. Hence $\tilde r$ is a combination of $1, \dots, z^{m-1}$ and $s\tilde q$ is a combination of $s, zs, \dots, z^{\,n-m}s$, i.e. $(\tilde q, \tilde r)$ is encoded by coordinates of $p$ in the basis (4.10). Coordinates with respect to a basis are unique, so $(\tilde q, \tilde r) = (q, r)$. $\blacksquare$

---

## 4. Factorization of Polynomials over C

**Remarks.** The fundamental theorem of algebra (FTA) is a pure *existence* theorem — its proof gives no method for finding zeros. Explicit root formulas exist for degree $2$ (quadratic formula) and, more complicated, for degrees $3$ and $4$; **no such formulas exist for degree $\ge 5$** (numerical methods can still approximate zeros to any accuracy). Every proof of the FTA must use some analysis: the statement is *false* if $\mathbf{C}$ is replaced by $\{c + di : c, d \in \mathbf{Q}\}$. The analysis used below is imported fact 3 (minimum attained on a closed disk).

**4.12 (FTA, first version).** Every nonconstant polynomial with complex coefficients has a zero in $\mathbf{C}$.

*Proof.*

**Step 1 (De Moivre's theorem).** For every positive integer $k$ and $\theta \in \mathbf{R}$:

$$(\cos\theta + i\sin\theta)^k = \cos k\theta + i \sin k\theta.$$

Induction on $k$ using the angle-addition formulas:

$$(\cos k\theta + i\sin k\theta)(\cos\theta + i\sin\theta) = (\cos k\theta\cos\theta - \sin k\theta\sin\theta) + i(\sin k\theta\cos\theta + \cos k\theta\sin\theta),$$

which equals $\cos(k+1)\theta + i\sin(k+1)\theta$.

**Step 2 (every $w \in \mathbf{C}$ has a $k$-th root).** Write $w = r(\cos\theta + i\sin\theta)$, $r \ge 0$ (imported fact 4). By Step 1,

$$\Bigl(r^{1/k}\bigl(\cos\tfrac{\theta}{k} + i\sin\tfrac{\theta}{k}\bigr)\Bigr)^{k} = w.$$

**Step 3 ($\lvert p \rvert$ attains a global minimum).** Let $p$ be nonconstant with highest-order nonzero term $c_m z^m$ ($m \ge 1$). Since

$$\frac{p(z)}{z^m} = c_m + \frac{c_{m-1}}{z} + \cdots + \frac{c_0}{z^m} \longrightarrow c_m \quad \text{as } \lvert z \rvert \to \infty,$$

we get $\lvert p(z) \rvert / \lvert z \rvert^m \to \lvert c_m \rvert \ne 0$, hence $\lvert p(z) \rvert \to \infty$ as $\lvert z \rvert \to \infty$. Choose $R$ with $\lvert p(z) \rvert > \lvert p(0) \rvert$ for all $\lvert z \rvert > R$; on the closed disk $\lvert z \rvert \le R$ the continuous function $z \mapsto \lvert p(z) \rvert$ attains a minimum (imported fact 3), and that minimum value is $\le \lvert p(0) \rvert$, hence is a **global** minimum. Let it be attained at $\zeta \in \mathbf{C}$.

**Step 4 (setup for contradiction).** Suppose $p(\zeta) \ne 0$. Define

$$q(z) := \frac{p(z + \zeta)}{p(\zeta)}.$$

Then $z \mapsto \lvert q(z) \rvert$ has global minimum **value $1$**, attained at $z = 0$ (and $q(0) = 1$). Write

$$q(z) = 1 + a_k z^k + \cdots + a_m z^m,$$

where $k$ is the smallest positive integer whose coefficient is nonzero, i.e. $a_k \ne 0$.

**Step 5 (a descent direction).** By Step 2 choose $\beta \in \mathbf{C}$ with

$$\beta^k = -\frac{1}{a_k}, \qquad \text{so} \quad 1 + a_k t^k \beta^k = 1 - t^k.$$

Set $c := 1 + \sum_{j=k+1}^{m} \lvert a_j \rvert\,\lvert \beta \rvert^j > 1$. For $t \in (0,1)$ we have $t^j \le t^{k+1}$ whenever $j \ge k+1$, so

$$\lvert q(t\beta) \rvert \le \lvert 1 + a_k t^k\beta^k \rvert + \sum_{j=k+1}^{m} \lvert a_j \rvert\,\lvert \beta \rvert^j t^j \le (1 - t^k) + t^{k+1}c = 1 - t^k(1 - tc).$$

**Step 6 (contradiction).** Take $t = \tfrac{1}{2c} \in (0,1)$: then $1 - tc = \tfrac{1}{2}$, so

$$\lvert q(t\beta) \rvert \le 1 - \tfrac{t^k}{2} < 1,$$

contradicting that the global minimum of $\lvert q \rvert$ is $1$. Hence $p(\zeta) = 0$. $\blacksquare$

**4.13 (FTA, second version: factorization over C).** If $p \in \mathcal{P}(\mathbf{C})$ is nonconstant with $m = \deg p$, then $p$ has a factorization

$$p(z) = c\,(z - \lambda_1)\cdots(z - \lambda_m), \qquad c, \lambda_1, \dots, \lambda_m \in \mathbf{C},$$

**unique** except for the order of the factors. The zeros of $p$ are exactly $\lambda_1, \dots, \lambda_m$ (the only points where the right side vanishes).

*Proof.* Induction on $m$. Base $m = 1$: $p = a_1 z + a_0 = a_1\bigl(z - (-a_0/a_1)\bigr)$; existence and uniqueness are clear. Step: assume $m > 1$ and the result for degree $m-1$.

*Existence.* By 4.12, $p$ has a zero $\lambda \in \mathbf{C}$; by 4.6, $p(z) = (z - \lambda)q(z)$ with $\deg q = m - 1$. The induction hypothesis factors $q$; substituting gives the factorization of $p$.

*Uniqueness.* $c$ is forced: it is the coefficient of $z^m$ in $p$. So suppose

$$(z - \lambda_1)\cdots(z - \lambda_m) = (z - \tau_1)\cdots(z - \tau_m) \qquad \forall z \in \mathbf{C}.$$

Setting $z = \lambda_1$ makes the left side $0$, so some $\tau_j = \lambda_1$; relabel so $\tau_1 = \lambda_1$. For $z \ne \lambda_1$, divide both sides by $z - \lambda_1$:

$$(z - \lambda_2)\cdots(z - \lambda_m) = (z - \tau_2)\cdots(z - \tau_m) \qquad \forall z \ne \lambda_1.$$

In fact this holds for **all** $z \in \mathbf{C}$: otherwise the difference of the two sides would be a *nonzero* polynomial with infinitely many zeros (all $z \ne \lambda_1$), contradicting 4.8. Now the induction hypothesis gives that $\lambda_2, \dots, \lambda_m$ agree with $\tau_2, \dots, \tau_m$ up to order. $\blacksquare$

---

## 5. Factorization of Polynomials over R

A real polynomial may have **no** real zeros — e.g. $1 + x^2$. (This failure of the FTA over $\mathbf{R}$ is the source of the differences between real and complex linear algebra in later chapters.) To factor over $\mathbf{R}$, we route through the factorization over $\mathbf{C}$.

**4.14 (Nonreal zeros come in conjugate pairs).** Let $p \in \mathcal{P}(\mathbf{C})$ have **real** coefficients. If $\lambda \in \mathbf{C}$ is a zero of $p$, then so is $\bar\lambda$.

*Proof.* Write $p(z) = a_0 + a_1 z + \cdots + a_m z^m$ with all $a_j \in \mathbf{R}$. Suppose

$$a_0 + a_1\lambda + \cdots + a_m\lambda^m = 0.$$

Conjugate both sides. By 4.4(d), conjugation passes through sums and products; $\bar{a_j} = a_j$ (real) and $\bar{0} = 0$. Hence

$$a_0 + a_1\bar\lambda + \cdots + a_m\bar\lambda^{\,m} = 0,$$

i.e. $p(\bar\lambda) = 0$. $\blacksquare$

**4.15 (Real factorization of a monic quadratic).** Let $b, c \in \mathbf{R}$. Then

$$x^2 + bx + c = (x - \lambda_1)(x - \lambda_2) \text{ for some } \lambda_1, \lambda_2 \in \mathbf{R} \iff b^2 \ge 4c.$$

*Proof.* Complete the square:

$$x^2 + bx + c = \Bigl(x + \frac{b}{2}\Bigr)^2 + \Bigl(c - \frac{b^2}{4}\Bigr).$$

If $b^2 < 4c$: the right side is $\ge c - \tfrac{b^2}{4} > 0$ for every $x \in \mathbf{R}$, so $x^2 + bx + c$ has no real zeros — hence no factorization $(x-\lambda_1)(x-\lambda_2)$ with $\lambda_1, \lambda_2 \in \mathbf{R}$ (the $\lambda_i$ would be real zeros).

If $b^2 \ge 4c$: choose $d \in \mathbf{R}$ with $d^2 = \tfrac{b^2}{4} - c$. Then

$$x^2 + bx + c = \Bigl(x + \frac{b}{2}\Bigr)^2 - d^2 = \Bigl(x + \frac{b}{2} + d\Bigr)\Bigl(x + \frac{b}{2} - d\Bigr). \qquad \blacksquare$$

**Pairing idea (and one subtlety).** For nonreal $\lambda$, multiplying the conjugate pair of linear factors gives a real quadratic:

$$(x - \lambda)(x - \bar\lambda) = x^2 - 2(\operatorname{Re}\lambda)\,x + \lvert \lambda \rvert^2,$$

whose discriminant is $4(\operatorname{Re}\lambda)^2 - 4\lvert \lambda \rvert^2 = -4(\operatorname{Im}\lambda)^2 < 0$ — i.e. exactly of the type $b^2 < 4c$. **Caution:** 4.14 guarantees that $\bar\lambda$ appears in the complex factorization when $\lambda$ does, but *not* that they appear with the same multiplicity. The proof of 4.16 works around this by peeling off one conjugate pair at a time and showing the quotient stays real.

**4.16 (Factorization over R).** If $p \in \mathcal{P}(\mathbf{R})$ is nonconstant, then $p$ has a factorization

$$p(x) = c\,(x - \lambda_1)\cdots(x - \lambda_m)\,(x^2 + b_1 x + c_1)\cdots(x^2 + b_M x + c_M),$$

where $c, \lambda_1, \dots, \lambda_m, b_1, \dots, b_M, c_1, \dots, c_M \in \mathbf{R}$ with $b_k^2 < 4c_k$ for each $k$, **unique** except for the order of the factors. Here $m$ or $M$ may be $0$, and $\lambda_1, \dots, \lambda_m$ are precisely the **real** zeros of $p$ (the only real points where the right side vanishes).

*Proof.*

**Existence** — strong induction on $n = \deg p$. View $p$ as an element of $\mathcal{P}(\mathbf{C})$.

*Case 1: every complex zero of $p$ is real.* Then 4.13 gives $p = c(x - \lambda_1)\cdots(x - \lambda_n)$ with each $\lambda_i \in \mathbf{R}$ and $c$ = the coefficient of $x^n$, which is real. Done with $M = 0$.

*Case 2: $p$ has a zero $\lambda \in \mathbf{C}\setminus\mathbf{R}$.* By 4.14, $\bar\lambda$ is also a zero. Apply 4.6 at $\lambda$: $p = (x - \lambda)q_1$ with $\deg q_1 = n - 1$. Evaluate at $\bar\lambda$: $0 = p(\bar\lambda) = (\bar\lambda - \lambda)q_1(\bar\lambda)$ and $\bar\lambda \ne \lambda$, so $q_1(\bar\lambda) = 0$; apply 4.6 again: $q_1 = (x - \bar\lambda)q$. Hence

$$p(x) = (x-\lambda)(x-\bar\lambda)\,q(x) = \bigl(x^2 - 2(\operatorname{Re}\lambda)x + \lvert \lambda \rvert^2\bigr)\,q(x), \qquad q \in \mathcal{P}(\mathbf{C}),\ \deg q = n - 2.$$

*Claim: $q$ has real coefficients.* For $x \in \mathbf{R}$ the quadratic equals $(x - \operatorname{Re}\lambda)^2 + (\operatorname{Im}\lambda)^2 > 0$ (as $\operatorname{Im}\lambda \ne 0$), so we may solve:

$$q(x) = \frac{p(x)}{x^2 - 2(\operatorname{Re}\lambda)x + \lvert \lambda \rvert^2} \in \mathbf{R} \qquad \forall x \in \mathbf{R}.$$

Write $q(x) = a_0 + a_1 x + \cdots + a_{n-2}x^{\,n-2}$ with $a_j \in \mathbf{C}$. For real $x$,

$$0 = \operatorname{Im} q(x) = (\operatorname{Im} a_0) + (\operatorname{Im} a_1)x + \cdots + (\operatorname{Im} a_{n-2})x^{\,n-2} \qquad \forall x \in \mathbf{R}.$$

A polynomial vanishing at infinitely many points must have all coefficients $0$ (by 4.8, as in the Corollary of Section 2). Hence every $\operatorname{Im} a_j = 0$, i.e. $q \in \mathcal{P}(\mathbf{R})$.

If $\deg q = 0$, then $q$ is a real constant — the leading coefficient $c$ — and $p = c\,\bigl(x^2 - 2(\operatorname{Re}\lambda)x + \lvert \lambda \rvert^2\bigr)$ is of the required form (its discriminant is $< 0$, as computed above). If $\deg q \ge 1$, apply the induction hypothesis to $q$ and multiply by the quadratic factor. Existence is proved.

**Uniqueness.** Any factor $x^2 + b_k x + c_k$ with $b_k^2 < 4c_k$ can be written **uniquely** as $(x - \lambda_k)(x - \bar\lambda_k)$ with $\lambda_k \in \mathbf{C}\setminus\mathbf{R}$: by the quadratic formula its complex roots are the conjugate pair

$$-\frac{b_k}{2} \pm i\sqrt{c_k - \frac{b_k^2}{4}},$$

determined by $(b_k, c_k)$. Hence every factorization of $p$ of the stated real form expands to a factorization of $p$ as an element of $\mathcal{P}(\mathbf{C})$ of the form 4.13. Two *different* real factorizations would therefore yield two *different* complex factorizations of $p$, contradicting the uniqueness in 4.13. $\blacksquare$

---

## Dependency map (logical skeleton)

- 4.4 ⇒ 4.14.
- 4.6 ⇒ 4.8 ⇒ coefficient/degree uniqueness, and the "vanishes at infinitely many points ⇒ zero polynomial" steps inside 4.13 and 4.16.
- $\dim \mathcal{P}_n(\mathbf{F}) = n+1$ together with LADR 2.38 ⇒ 4.9.
- De Moivre + minimum attainment ⇒ 4.12.
- 4.12 + 4.6 ⇒ 4.13.
- 4.13 + 4.14 (+ the pairing computation behind 4.15) ⇒ 4.16.
