---
title: "Discrete Causal Model"
description: "A discrete matrix-algebraic model of the universe — space as index structure, time as unitary evolution, physics as the rule for constructing the evolution operator."
weight: 1
---

## Discrete Causal Model

A theoretical physics research program proposing that the universe is a **discrete matrix algebra** operating on a growing index space. There is no fundamental "space" — only indices in a matrix. What we call space is the index structure of a Fock space; time is a sequence of unitary matrix multiplications; and physics is the rule for constructing the evolution operator *U*(*t*).

Every analytical result is backed by Python numerical verification and, where applicable, formal proofs in Lean 4.

{{< spacer >}}

## Central Equation

The state of the universe at time T is given by:

**|Ψ(*T*)⟩ = *U*(*T*−1) · *U*(*T*−2) · … · *U*(1) · *U*(0) · |Ψ(0)⟩**

where *U*(*t*) is the unitary evolution operator at each Planck-scale time step and the orbital index space *N*(*t*) grows — encoding the expansion of the universe.

{{< spacer >}}

## Key Ideas

{{< cards count=3 >}}
{{< card >}}
### Running Alpha
The fine-structure constant α(*t*) evolves in the ultra-early universe and freezes after charged-particle threshold crossing. Late-time acceleration is modeled by a separate vacuum-like channel.
{{< /card >}}
{{< card >}}
### Causal Gravity
Gravity emerges as a retarded potential from the past light cone — a non-Markovian delta-kernel construction. No background spacetime is assumed.
{{< /card >}}
{{< card >}}
### Holographic Bounds
Entropy is bounded by the index space (*S* ≤ *N* ln 2 for fermions). The vacuum expansion rate *H*<sub>Λ</sub> is derived from holographic entropy bounds.
{{< /card >}}
{{< /cards >}}

{{< spacer >}}

## Research Topics

- **Quantum Gravity / Foundations of Physics** — discrete causal substrate, Planck-scale time updates, growing orbital index space
- **Cosmology** — redshift from growing *N*(*t*), dark energy from index space expansion, CMB predictions
- **Decoherence** — novel α-mismatch mechanism (no consciousness or observer required)
- **Holographic Principle** — 3D universe from a fundamentally 2D boundary description, explicit implementation in the data structure
- **Initial State** — *T*₀ uniqueness theorem (for *N* ≤ 4), no fine-tuning needed

{{< spacer >}}

## Verification Approach

Results are verified through two complementary methods:

- **Python numerical simulations** — Fock space evolution, gravity, light cones, parameter scans, and alpha-history simulations using NumPy and SciPy.
- **Lean 4 formal proofs** — Machine-checked proofs covering holographic entropy bounds, *T*₀ uniqueness, conservation laws, and causal structure properties.

Every claim in the research is tagged with its epistemic status: established physics, derived, assumption, numerically verified, Lean-proved, or open question.

{{< spacer >}}

## Status

The Discrete Causal Model is an active research program with 13+ papers covering foundations, gravity, conservation laws, cosmology, quantum mechanics, holography, and particle ontology. The papers are not yet published.
