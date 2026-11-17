# Hasse–Minkowski over Q

A quadratic form over $\mathbb{Q}$ is *isotropic* if it has a nonzero zero, and
*anisotropic* otherwise. The places of $\mathbb{Q}$ are the primes $p$, with
completions $\mathbb{Q}_p$, and the real place, with completion $\mathbb{R}$.
The Hasse–Minkowski theorem says that a quadratic form over $\mathbb{Q}$ is
isotropic as soon as it is isotropic over every completion.

Tau Ceti's open pull requests (see the Lean status below) state the
local–global principle for any number field $K$, in terms of the places of $K$
and the completions `v.adicCompletion K`. This page asks
for it over $\mathbb{Q}$ in its classical form, with $\mathbb{Q}_p$ and
$\mathbb{R}$, so that later milestones need no number-field vocabulary.

> [!milestone] Hasse–Minkowski theorem over Q
> Let $f$ be a nondegenerate quadratic form over $\mathbb{Q}$. Then $f$ is isotropic over $\mathbb{Q}$ if and only if it is isotropic over $\mathbb{R}$ and over $\mathbb{Q}_p$ for every prime $p$. Consequently, for $a \in \mathbb{Q}^\times$, $f$ represents $a$ over $\mathbb{Q}$ if and only if it represents $a$ over $\mathbb{R}$ and over every $\mathbb{Q}_p$.
>
> Sources: [@Serre1973, Ch. IV, §3.2, Theorem 8] for isotropy, and its Corollary 1 for representation. The representation statement follows from the isotropy statement applied to $f \oplus \langle -a \rangle$, since a nondegenerate form represents $a \neq 0$ if and only if $f \oplus \langle -a\rangle$ is isotropic [@Serre1973, Ch. IV, §1].
>
> Proof routes:
> - Specialize the number-field theorem from Tau Ceti's open pull requests to $K = \mathbb{Q}$. Mathlib identifies the finite places of $\mathbb{Q}$ with the primes (`Rat.HeightOneSpectrum.primesEquiv`) and their completions with $\mathbb{Q}_p$ (`Rat.HeightOneSpectrum.adicCompletion.padicEquiv`), and $\mathbb{Q}$ has a single infinite place, which is real. Anisotropy has to be transported along these isomorphisms; Tau Ceti's `NumberTheory/QuadraticForm/Global/TernaryObstruction.lean` does such a transport for one form.
> - Serre's own proof over $\mathbb{Q}$, by induction on the rank, needs Dirichlet's theorem on primes in arithmetic progressions for rank 4. Do not reprove the theorem here: Tau Ceti's version is the intended route.
>
> Formalization notes: state the milestone for Mathlib's `QuadraticForm ℚ V` on a finite-dimensional space, with "isotropic over $\mathbb{Q}_p$" as `¬ (Q.baseChange ℚ_[p]).Anisotropic` and likewise over $\mathbb{R}$. Tau Ceti's `atFinitePlace` and `atRealPlace` are base changes too, to the completions of a number field.
>
> Lean status: Mathlib —. Tau Ceti: over number fields, in the open pull requests TauCetiProject/TauCeti#42272 (ternary and quaternary forms) and TauCetiProject/TauCeti#43187 (all ranks, with the representation version `QuadraticForm.represents_iff_locallyRepresentsScalar`, where `Represents Q a` means `∃ v, Q v = a`); on `main` at `0642eae` only rank at most 2, and the induction steps for ranks 4 and at least 5. Not specialized to $\mathbb{Q}$.

> [!milestone] Meyer's theorem
> A nondegenerate quadratic form over $\mathbb{Q}$ of rank at least 5 is isotropic if and only if it is indefinite, that is, neither positive definite nor negative definite.
>
> Sources: [@Serre1973, Ch. IV, §3.2, Corollary 2 to Theorem 8].
>
> Proof routes: by the Hasse–Minkowski theorem over Q, it is enough to check every completion.
> - Over $\mathbb{Q}_p$, every quadratic form of rank at least 5 is isotropic [@Serre1973, Ch. IV, §2.2, Theorem 6]. Tau Ceti has this for nonarchimedean local fields: `QuadraticForm.not_anisotropic_of_five_le_finrank`.
> - Over $\mathbb{R}$, a form is anisotropic if and only if it is positive or negative definite. Tau Ceti has `QuadraticForm.anisotropic_iff_posDef_or_negDef` in `LinearAlgebra/QuadraticForm/Real.lean`, stated as `Q.Anisotropic ↔ Q.PosDef ∨ (-Q).PosDef`. Neither library has a `NegDef`, so write negative definiteness as `(-Q).PosDef` throughout.
> - Both directions need only one link between $\mathbb{Q}$ and $\mathbb{R}$: if the form is positive (or negative) definite over $\mathbb{R}$, it is so over $\mathbb{Q}$, since its values on rational vectors are among its real values. So an indefinite form over $\mathbb{Q}$ is isotropic over $\mathbb{R}$; and an isotropic form is indefinite, by definition. This small lemma about restriction is not in either library.
>
> Lean status: Mathlib —. Tau Ceti —.
