---
title: "Oloid Geometry"
description: "The generalized oloid — exact closed-form properties for the convex hull of two linked circles at arbitrary dihedral angle."
weight: 2
---

## Oloid Geometry

The **oloid** is a geometric solid formed as the convex hull of two linked circles. This research generalizes the classical construction, deriving exact closed-form results for an entire one-parameter family of oloids.

Every theorem is backed by Python code verifying results to machine precision (12+ decimal places, some to 80 digits), and key results carry formal proofs in Lean 4.

{{< spacer >}}

## The Generalized Oloid

*Geometry of the Convex Hull of Two Linked Circles at Variable Dihedral Angle*

Takes the classical oloid (where the two circle planes are perpendicular) and generalizes it to an arbitrary dihedral angle, deriving exact closed-form results for the entire one-parameter family. Key findings include angle-independent structural invariants, a conservation law for ruling lengths, a clean volume scaling law, and closed-form surface area via complete elliptic integrals.

Contains 14 original theorems and propositions, extending foundational work by Dirnbock and Stachel (1997).

{{< spacer >}}

## Research Topics

- **Computational and Differential Geometry** — convex hulls, ruled surfaces, developable surfaces
- **Algebraic Geometry** — elliptic curves, genus classification, moduli spaces
- **Elliptic Integrals** — complete elliptic integrals, Legendre parameters
- **Conformal Geometry** — cross-Gram matrices, conformal moduli, Mobius invariants
- **High-Precision Numerical Verification** — 80-digit computations, convergence analysis

{{< spacer >}}

## Verification Approach

Results are verified through two complementary methods:

- **Python numerical verification** — Every theorem is accompanied by runnable code using NumPy, SciPy, SymPy, and mpmath, verifying results to machine precision and beyond (up to 80 digits).
- **Lean 4 formal proofs** — Key results carry machine-checked proofs in Lean 4, covering the ruling formula, genus classification, and conservation laws.

The paper is bilingual (English and Polish) and transparently acknowledges AI-assisted derivation where applicable.

{{< spacer >}}

## License

Released under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.
