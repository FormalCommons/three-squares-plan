# Sums of squares

Which numbers are sums of three squares? For positive rationals the answer is
local, and the only obstruction is at $2$. Over $\mathbb{Z}$, the Davenport–Cassels lemma turns a
rational representation into an integral one. Together they give Legendre's
three-square theorem, and with it Gauss's theorem on triangular numbers and
Lagrange's four-square theorem.

Throughout, $\langle 1,1,1 \rangle$ is the form $x^2+y^2+z^2$.

> [!milestone] Rational three-square theorem
> Let $a$ be a positive rational number. Then $a = x^2 + y^2 + z^2$ for some $x, y, z \in \mathbb{Q}$ if and only if $-a$ is not a square in $\mathbb{Q}_2$. For a positive integer $n$ this says: $n$ is a sum of three squares of rationals if and only if $n$ is not of the form $4^a(8b+7)$ with $a, b \in \mathbb{N}$.
>
> Sources: [@Serre1973, Ch. IV, Appendix], which reduces the integral three-square theorem to this statement and the Davenport–Cassels lemma.
>
> Proof routes: by the representation form of the Hasse–Minkowski theorem over Q, it is enough to decide where $\langle 1,1,1 \rangle$ represents $a$.
> - Over $\mathbb{R}$, it represents exactly the positive numbers.
> - Over $\mathbb{Q}_p$, a nondegenerate ternary form $f$ with discriminant $d$ and Hasse invariant $\varepsilon$ represents $a$ unless $a = -d$ in $\mathbb{Q}_p^\times/(\mathbb{Q}_p^\times)^2$ and $(-1,-d) \neq \varepsilon$ [@Serre1973, Ch. IV, §2.2, Theorem 6 and its corollary]. For $\langle 1,1,1\rangle$, $d = 1$ and $\varepsilon = 1$, and $(-1,-1)_p$ is $1$ for odd $p$ and $-1$ for $p = 2$ [@Serre1973, Ch. III, §1.2, Theorem 1]. So it represents every $a$ over $\mathbb{Q}_p$ for odd $p$, and over $\mathbb{Q}_2$ exactly the $a$ with $-a$ not a square.
> - Tau Ceti has the pieces: `QuadraticForm.notMem_unitValueSet_iff_anisotropic_and_squareClass_eq_of_finrank_eq_three` (a ternary form misses $c$ if and only if it is anisotropic and $c = -d$ up to squares), `TauCeti.hilbertSymbol_neg_one_neg_one_padicTwo`, and the Hilbert symbols of integers over $\mathbb{Q}_p$ for odd $p$, `TauCeti.Padic.hilbertSymbol_intCast_intCast_eq_one`.
> - For the integer form: $-n$ is a square in $\mathbb{Q}_2$ if and only if $n = 4^a u$ with $u$ odd and $-u \equiv 1 \pmod 8$, that is, $n = 4^a(8b+7)$. An odd $2$-adic unit is a square if and only if it is $\equiv 1 \pmod 8$; Tau Ceti has this as `TauCeti.isSquare_coe_iff_mem_unitsPrincipal_three` in `NumberTheory/Padics/SerreSigns.lean`.
>
> Lean status: Mathlib —. Tau Ceti —.

> [!milestone] Davenport–Cassels lemma
> Let $f(x) = \sum_{i,j} a_{ij} x_i x_j$ be a positive definite quadratic form in $n$ variables, where $(a_{ij})$ is a symmetric matrix with integer entries. Suppose that for every $x \in \mathbb{Q}^n$ there is $y \in \mathbb{Z}^n$ with $f(x - y) < 1$. Then every integer that $f$ represents over $\mathbb{Q}$ is represented by $f$ over $\mathbb{Z}$.
>
> Sources: [@Serre1973, Ch. IV, Appendix, Lemma B]; [@Clark2012, Theorem 1], which also traces the history back to Aubry, and treats the more general class of "Euclidean" forms.
>
> Proof routes: Serre's proof is elementary and self-contained. Write a rational solution as $x = z/t$ with $z \in \mathbb{Z}^n$ and $t \geq 1$ minimal, pick $y \in \mathbb{Z}^n$ with $f(x-y) < 1$, and intersect the line through $x$ and $y$ with the quadric $f = m$. The second intersection point has a denominator strictly smaller than $t$, so descent on $t$ ends with $t = 1$. It needs nothing else from this plan, so it can be done alongside the other milestones.
>
> Formalization notes: state it for a symmetric integer matrix $A$ with $f(x) = x^{\mathsf T} A x$, rather than for an abstract quadratic form, since the hypothesis and the conclusion are about the lattice $\mathbb{Z}^n$. For $\langle 1,1,1\rangle$ the hypothesis holds by rounding each coordinate to a nearest integer: then $f(x - y) \leq 3/4$.
>
> Lean status: Mathlib —. Tau Ceti —.

> [!milestone] Legendre's three-square theorem
> A natural number $n$ is a sum of three squares of integers if and only if $n$ is not of the form $4^a(8b+7)$ with $a, b \in \mathbb{N}$.
>
> Sources: [@Serre1973, Ch. IV, Appendix], where it is attributed to Gauss and stated as "not of the form $4^a(8b-1)$"; [@Clark2012, Corollary 2].
>
> Proof routes:
> - "Only if" is elementary. A square is $0$, $1$ or $4$ modulo $8$, so a sum of three squares is never $7$ modulo $8$; and if $4$ divides $x^2+y^2+z^2$, then $x$, $y$ and $z$ are even, so one can divide by $4$.
> - "If" follows from the rational three-square theorem and the Davenport–Cassels lemma for $\langle 1,1,1\rangle$. The rational theorem needs a positive number, so treat $n = 0 = 0^2+0^2+0^2$ separately.
>
> > [!warning]
> > The excluded numbers are not just those $\equiv 7 \pmod 8$: $28 = 4 \cdot 7$ is not a sum of three squares either. A statement with the condition "$n \not\equiv 7 \pmod 8$" is false.
>
> Lean status: Mathlib —; it has sums of two squares (`Nat.eq_sq_add_sq_iff`) and of four (`Nat.sum_four_squares`). Tau Ceti —.

> [!milestone] Sums of three triangular numbers
> Every natural number $n$ is a sum of three triangular numbers: $n = T_i + T_j + T_k$ for some $i, j, k \in \mathbb{N}$, where $T_m = m(m+1)/2$.
>
> Sources: Gauss's mathematical diary, entry 18, 10 July 1796: "ΕΥΡΗΚΑ num $= \Delta + \Delta + \Delta$" [@Gray1984]. The deduction below is standard.
>
> Proof routes: $8n + 3$ is not of the form $4^a(8b+7)$: it is odd, which rules out $a \geq 1$, and it is $3$ modulo $8$, which rules out $a = 0$. So by Legendre's three-square theorem $8n+3 = u^2 + v^2 + w^2$. Squares are $0$, $1$ or $4$ modulo $8$, and only $1 + 1 + 1$ gives $3$, so $u$, $v$ and $w$ are odd: $u = 2i+1$, $v = 2j+1$, $w = 2k+1$, with $i, j, k \in \mathbb{N}$ after changing signs. Then $8n + 3 = 8(T_i + T_j + T_k) + 3$.
>
> Lean status: Mathlib —. Tau Ceti —.

> [!milestone] Lagrange's four-square theorem
> Every natural number is a sum of four squares of integers.
>
> Sources: it is a short corollary of Legendre's three-square theorem: if $n = 4^a(8b+7)$, then $n - 4^a = 4^a(8b+6)$ is a sum of three squares, so $n$ is $(2^a)^2$ plus three squares [@Serre1973, Ch. IV, Appendix].
>
> Lean status: Mathlib **full**: `Nat.sum_four_squares`, by a direct proof. Tau Ceti uses Mathlib's.
