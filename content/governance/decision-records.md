+++
title = "Decision Records"
description = "A durable log of governance decisions and bindings."
draft = false
status = "MVP"
+++

Governance requires memory.

This page defines what must be recorded, how records are structured, and where authoritative decision history lives.

> **If a decision is binding, it must be recorded.**  
> If it is not recorded, it is not binding.

---

## 1. What Gets Recorded

Record a Decision Record when:

- a governing document is adopted, amended, or retired
- a steward role is created, assigned, or revoked
- an exception is granted (and its expiry)
- a compliance or enforcement action is taken
- an authority boundary is clarified in a binding way

---

## 2. Where Records Live

For MVP, Decision Records are stored as:

- a dated markdown entry under a `decision-records/` directory (or equivalent)
- linked from affected pages where appropriate

The record must be durable and discoverable.

---

## 3. Required Fields

Each Decision Record must include:

- **ID**: `DR-YYYY-MM-DD-###`
- **Title**
- **Status**: Proposed / Ratified / Superseded
- **Date**
- **Author / Steward**
- **Decision**
- **Rationale**
- **Scope**
- **Impacts**
- **Links** to affected documents

---

## 4. Supersession

A new Decision Record may supersede an old one only if:

- it explicitly references the prior record
- it states what is replaced and why
- it follows the amendment process if the supersession changes canonical documents

History is preserved. Superseded records are not deleted.

---