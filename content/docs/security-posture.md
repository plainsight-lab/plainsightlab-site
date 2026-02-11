+++
title = "Security Posture"
description = "Principles governing how PlainSight Lab approaches security, safety, and adversarial risk."
draft = false
doc_type = "Governance"
version = "v1.0"
status = "Active"
effective_date = "2026-02-09"
+++

## Purpose

This document defines the security posture of PlainSight Lab.

It describes how security is treated as a **systems property**, not a checklist, and how adversarial risk is addressed through structure rather than reaction.

---

## Core Assumptions

PlainSight Lab operates under the following assumptions:

- Adversarial behavior is normal, not exceptional.
- Security failures compound faster than they are corrected.
- Disclosure and correction costs matter as much as exploitability.
- Trust must be earned through structure, not assertion.

Security is therefore a governance concern, not merely a technical one.

---

## Design Principles

Security posture is shaped by the following principles:

### 1. Governance Before Hardening

Security mechanisms are effective only when authority and responsibility are explicit.

Unowned systems cannot be secured.

---

### 2. Constraints Before Detection

Preventing invalid states is preferred over detecting them after execution.

Security is enforced as early as possible in system flows.

---

### 3. Adversarial Modeling by Default

Systems are evaluated assuming:
- probing will occur,
- incentives will be exploited,
- ambiguity will be weaponized.

Good faith is not a security control.

---

### 4. Human Authority at Decision Boundaries

Automated systems may assist but may not exercise final authority.

Security decisions that affect invariants require explicit human accountability.

---

## Scope of Responsibility

PlainSight Lab:
- stewards security posture for canonical specifications and governance artifacts,
- evaluates derivative entities for compliance with defined constraints,
- and refuses participation in systems that violate invariants.

Implementation-level security controls are the responsibility of derivative entities, subject to oversight.

---

## Incident Reality

Security incidents are treated as:
- signals of structural weakness,
- opportunities to reduce correction cost,
- and inputs to governance evolution.

Blame assignment is secondary to containment and correction.

---

## Transparency and Disclosure

Security-related disclosures are governed by the **Responsible Disclosure Policy**.

Disclosure is balanced against exploitation risk and correction readiness.

---

## Closing

Security is not a feature.

It is the emergent property of correct authority, constrained execution, and adversarial realism.

PlainSight Lab exists to ensure those conditions hold.

---