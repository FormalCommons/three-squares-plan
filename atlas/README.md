# Three squares

Which natural numbers are sums of three squares? Legendre's answer, that
exactly those not of the form $4^a(8b+7)$ are, is a classical application of
the Hasse–Minkowski theorem: the local–global principle for quadratic forms
over $\mathbb{Q}$. This plan leads from that theorem to Legendre's three-square
theorem, and on to Gauss's theorem that every natural number is a sum of three
triangular numbers. It follows the appendix "Sums of three squares" to
Chapter IV of Serre's *A Course in Arithmetic* [@Serre1973].

## Scope

In scope: the Hasse–Minkowski theorem over $\mathbb{Q}$ in its classical form,
with the real numbers and the fields $\mathbb{Q}_p$; Meyer's theorem; sums of
three squares of rationals and of integers; the Davenport–Cassels lemma; sums
of three triangular numbers.

Out of scope: the local theory over $\mathbb{Q}_p$ (Hilbert symbols, the
classification of quadratic forms over $\mathbb{Q}_p$), which Tau Ceti has;
the Hasse–Minkowski theorem over number fields, which is in Tau Ceti's open
pull requests (see below); and counting representations, such as Gauss's
formula for the number of representations by three squares.

## Milestones

- [Hasse–Minkowski over $\mathbb{Q}$](hasse-minkowski.md):
  - **Hasse–Minkowski theorem over Q**
  - **Meyer's theorem**, which depends on the Hasse–Minkowski theorem over Q
- [Sums of squares](sums-of-squares.md):
  - **Rational three-square theorem**, which depends on the Hasse–Minkowski theorem over Q
  - **Davenport–Cassels lemma**, which depends on nothing in this plan
  - **Legendre's three-square theorem**, which depends on the rational
    three-square theorem and the Davenport–Cassels lemma
  - **Sums of three triangular numbers**, which depends on Legendre's
    three-square theorem
  - **Lagrange's four-square theorem**, which depends on nothing in this plan

## The libraries

As of 17 November 2026, at Tau Ceti commit `0642eae` and the Mathlib commit it
pins, `048fffa`:

- **Mathlib** has quadratic forms over fields, with diagonalization,
  isometry, `QuadraticMap.Anisotropic` and Sylvester's law over $\mathbb{R}$;
  $\mathbb{Q}_p$ and $\mathbb{Z}_p$ with Hensel's lemma; quadratic reciprocity
  and the Legendre and Jacobi symbols; the identification of the completions of
  $\mathbb{Q}$ at its finite places with the $\mathbb{Q}_p$; and the sums of two
  and of four squares.
- **Tau Ceti** has the Hilbert symbol over any field, its explicit values over
  $\mathbb{Q}_p$ including $p = 2$, and the classification of quadratic forms
  over nonarchimedean local fields. Over number fields it has the local–global
  principle for forms of rank at most 2, and the induction steps for ranks 4
  and at least 5. The ternary case and the full theorem are in open pull
  requests: TauCetiProject/TauCeti#42272 (ternary and quaternary forms) and
  TauCetiProject/TauCeti#43187 (all ranks). A formalization of this plan
  should build on a Tau Ceti commit that includes them.

None of the milestones here, apart from Lagrange's four-square theorem, is in
either library.

## Sources

The main source is Serre [@Serre1973]: Chapters III and IV for Hilbert
symbols and quadratic forms, and the appendix to Chapter IV for sums of three
squares. Theorem 8 in Ch. IV, §3.2 and Lemma B in the appendix were checked
against a published guide to the book and against seminar notes that follow it;
the numbering of the corollaries to Theorem 8 was checked only against the
seminar notes, not against the book itself. Clark [@Clark2012] gives a modern
treatment of the Davenport–Cassels lemma and of the three-square theorem.
