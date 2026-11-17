# Three squares: a formalization plan

A small formalization plan, in the shape of an atlas: the milestone results of
a piece of mathematics, where they are proved, and what a formalizer should
know. It covers the Hasse–Minkowski theorem over $\mathbb{Q}$ and its classical
applications to sums of squares, up to Legendre's three-square theorem and
Gauss's theorem that every natural number is a sum of three triangular numbers.

The formalization builds on [Tau Ceti](https://github.com/TauCetiProject/TauCeti),
which already has the local theory: Hilbert symbols, and quadratic forms over
$\mathbb{Q}_p$ and other local fields. The Hasse–Minkowski theorem over number
fields is in two of its open pull requests, TauCetiProject/TauCeti#42272 and
TauCetiProject/TauCeti#43187; a formalization of this plan should build on a
Tau Ceti commit that includes them.

This plan was written by an AI agent, Claude, for a first experiment with a
pipeline of agents that formalize a plan through GitHub issues and pull
requests ([fc-worker](https://github.com/FormalCommons/fc-worker)). It was
checked against its sources, but it has not been reviewed by experts.

| Path | Contents |
|---|---|
| [`atlas/README.md`](atlas/README.md) | The front page: scope, how the milestones depend on each other, and the state of the libraries |
| [`atlas/hasse-minkowski.md`](atlas/hasse-minkowski.md) | The Hasse–Minkowski theorem over $\mathbb{Q}$, and Meyer's theorem |
| [`atlas/sums-of-squares.md`](atlas/sums-of-squares.md) | Sums of three squares, rational and integral; triangular numbers; four squares |
| [`atlas/references.bib`](atlas/references.bib) | The sources |

The pages are Markdown, with math between `$…$` and `$$…$$`. Each milestone
is a callout whose first line is its name, `> [!milestone] Name`; the callout
gives a precise statement, the sources, routes to a proof, and the milestone's
status in Mathlib and Tau Ceti. Citations such as
`[@Serre1973, Ch. IV, §3.2, Theorem 8]` refer to entries of
`atlas/references.bib`.
