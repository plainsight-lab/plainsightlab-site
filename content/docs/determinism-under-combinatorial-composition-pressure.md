+++
title = "Determinism Under Combinatorial Composition Pressure"
description = "A formal treatment of determinism invariants as composable subsystems scale under adversarial and combinatorial conditions."
draft = true
doc_type = "Research Memorandum"
version = "v0.1"
status = "Draft"
effective_date = ""
derived_from = "systems-thesis"
math = true
+++

{{< abstract >}}
This memorandum formalizes the claim that determinism — as a design invariant — degrades
predictably under combinatorial composition pressure. We define the conditions under which
determinism is preserved, state the primary theorem, and derive structural implications
for governance and enforcement architecture.
{{< /abstract >}}

---

## Scope and Non-Goals

{{< non-goals >}}
- This memorandum does not address probabilistic systems or systems where
  non-determinism is a first-class design intent.
- It does not provide implementation guidance for any specific runtime or language.
- It does not treat distributed consensus as a solved problem.
{{< /non-goals >}}

**Scope:** Systems composed of individually deterministic subsystems, under adversarial
or combinatorial input pressure, where composition is the primary failure mode.

---

## Definitions

{{< definition label="Definition 1 — Deterministic Subsystem" >}}
A subsystem **S** is *deterministic* if and only if for all inputs **i**, the output
**S(i)** is identical across all executions, environments, and orderings in which
**S** is called.
{{< /definition >}}

{{< definition label="Definition 2 — Composition Pressure" >}}
*Composition pressure* is the increase in observable non-determinism that emerges
when two or more deterministic subsystems **S₁, S₂, …, Sₙ** are composed into a
system **C = S₁ ∘ S₂ ∘ … ∘ Sₙ** if the composition introduces shared state,
ordering dependencies, or ambient inputs not present in any individual **Sᵢ**.
{{< /definition >}}

---

## Formal Model

Let \\(\mathbf{S}\\) be a finite set of subsystems, each individually deterministic under
Definition 1. Let \\(C(\mathbf{S})\\) denote a composed system formed by chaining or
layering elements of \\(\mathbf{S}\\).

Define \\(\Delta(C)\\) as the entropy of observable output variation across equivalent
executions of \\(C\\) with identical inputs. For a fully deterministic composed
system, \\(\Delta(C) = 0\\).

Composition pressure \\(P\\) is the function:

\\[
P(C) = \frac{\Delta(C)}{|\mathbf{S}|}
\\]

Where \\(|\mathbf{S}|\\) is the cardinality of the composition (number of subsystems).

---

## Theorem(s)

{{< theorem label="Theorem 1 — Composition Pressure Growth" >}}
For any composed system \\(C(\mathbf{S})\\) where \\(|\mathbf{S}| \geq 2\\), if any pair
\\((S_i, S_j)\\) shares ambient state or introduces an ordering dependency not declared
in the interface contract of either subsystem, then \\(\Delta(C) > 0\\) regardless of
the individual determinism of \\(S_i\\) and \\(S_j\\).

Formally: if \\(\exists\, (S_i, S_j) \in \mathbf{S} \times \mathbf{S}\\) such that
\\(\text{implicit}(S_i, S_j) \neq \emptyset\\), then \\(\Delta(C) > 0\\).
{{< /theorem >}}

---

## Proof(s)

{{< proof label="Proof of Theorem 1" >}}
Assume for contradiction that \\(\Delta(C) = 0\\) while \\(\exists\, (S_i, S_j)\\) with
a shared implicit dependency \\(d\\).

Since \\(d\\) is implicit, it is not part of the declared input to either subsystem.
By Definition 1, determinism holds only over declared inputs. Therefore \\(d\\)
constitutes an undeclared input to \\(C\\), and any variation in \\(d\\) across
executions produces variation in \\(C(i)\\) for identical \\(i\\). This contradicts
\\(\Delta(C) = 0\\). \\(\square\\)
{{< /proof >}}

---

## Structural Implications

1. Composition contracts must be as explicit as subsystem contracts.
2. Shared state between composed subsystems must be declared and controlled
   at the composition boundary, not within individual subsystems.
3. Ambient inputs (time, locale, environment variables, execution order) must
   be injected explicitly — not observed implicitly — across all composition layers.

---

## Relationship to Prior Work

This memorandum formalizes intuitions present in the Systems Thesis regarding
reproducibility as a design constraint. The LoEC framework extends this to
enforcement: if **Δ(C) > 0**, the system cannot be reliably observed, and
enforcement through observation fails by construction.

---

## Governance and Invariant Relevance

Systems that exhibit composition pressure violate the reproducibility invariant
established in the PlainSight Lab governance framework. Any subsystem contributing
to **Δ(C) > 0** is a governance surface — it must be isolated, declared, and
subject to explicit change-control.

---

## Versioning and Amendment

This is a Draft memorandum (v0.1). It will be amended as formal proofs are
strengthened and as LoEC formalization progresses.

---

## Closing Condition

This memorandum is closed when: (a) Theorem 1 has been formally verified or
refuted, (b) structural implications have been adopted into the governance
framework, and (c) a successor memorandum addresses distributed composition.
