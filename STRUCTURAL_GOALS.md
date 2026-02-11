# STRUCTURAL_GOALS.md

**PlainSight Lab — Hugo Theme Structural Constraints**

**Status:** Binding
**Audience:** Human contributors and automated agents
**Scope:** All public Hugo themes stewarded by PlainSight Lab

---

## Purpose

This document defines the **structural goals and implementation opinions** that all PlainSight
Labs–governed Hugo themes must follow.

These goals exist to:
- prevent CSS and template drift,
- ensure themes remain override-friendly,
- eliminate cascade conflicts,
- and preserve long-term maintainability.

These are **positive constraints**: they define *how* themes must be constructed.

This document is authoritative alongside `NON_GOALS.md` and `AGENTS.md`.

---

## Core Structural Invariants

### 1. No `!important` anywhere

Use of `!important` is **strictly prohibited**.

If a change appears to require `!important`, this indicates:
- incorrect selector strategy,
- excessive specificity,
- or improper tokenization.

The correct fix is to restructure selectors or introduce a semantic token.

There are **no exceptions**.

---

### 2. All design decisions must be expressed as CSS variables

The following must be expressed via CSS variables:

- colors
- typography (font families, sizes, weights, line heights)
- spacing
- borders and radii
- shadows
- z-index layers

Variables must be defined at the theme level and overridden at the site level.

Hard-coded values inside component rules are not permitted except for:
- layout math (e.g., `min()`, `max()`, `clamp()`)
- reset-level defaults

---

### 3. Semantic tokens only (never brand tokens)

Tokens must describe **role**, not identity.

**Allowed:**
```css
--color-bg
--color-fg
--color-muted
--color-border
--color-accent
--font-sans
--font-mono
--space-md
```

**Forbidden:**
```css
--plainsight-charcoal
--brand-blue
--ledger-green
```

Themes must be brand-capable, not brand-encoded.

### 4. Low specificity by default

Selectors should remain easy to override.

Preferred:
- single-class selectors (.card)
- component + modifier (.button--primary)
- attribute hooks when needed ([data-state="active"])

Avoid:
- IDs
- deep descendant chains
- element-qualified classes (div.card)
- :nth-child layout hacks

If overriding a rule feels difficult, the selector is too specific.

### 5. Explicit component boundaries

Themes must define a small, explicit set of composable primitives:
- layout primitives (container, grid, stack)
- typography primitives (prose, heading, code)
- navigation primitives (nav, toc, breadcrumbs)
- content primitives (card, callout, notice)

Component styles must not depend on page context.

Page-specific CSS is strongly discouraged.

### 6. Single stylesheet entrypoint with intentional layering

Each theme must expose a single primary stylesheet entrypoint.

Conceptual layering must be clear and documented, for example:
- design tokens
- base / reset
- typography
- layout primitives
- components
- limited utilities

Use of native CSS layering (@layer) is encouraged where supported.

### 7. Overrides must be predictable and stable

A site integrating a theme must be able to override behavior by:
1. overriding CSS variables
2. overriding Hugo partials
3. appending site-level CSS

Themes must not rely on:
- implicit ordering
- undocumented cascade behavior
- side effects from template execution order

### 8. Dark mode and variants are token-driven

Any variant (dark mode, high contrast, etc.) must be implemented by:
- swapping CSS variables
- toggling a root attribute or media query

Component CSS must not be duplicated per variant.

---

### 9. Hugo template logic must remain simple and inspectable

Templates should:
- favor clarity over cleverness
- use partials with explicit inputs
- avoid hidden dependencies on global state
- make data flow obvious

If behavior cannot be understood by reading the template, it is too implicit.

---

### 10. No external runtime dependencies for core behavior

Themes must function correctly without:
- external JavaScript frameworks
- external CSS frameworks
- external font CDNs

Hooks for optional enhancements are permitted. Core behavior must remain deterministic and local.

---

## Structural Philosophy

These themes optimize for:
- composability over convenience
- clarity over cleverness
- explicit structure over stylistic freedom
- long-term survivability over short-term polish

A theme should feel boring to modify and predictable to override.

---

## Enforcement Rule

Before accepting any change, contributors and agents must answer:

Does this improve structural clarity, or does it merely make the theme easier to style in the
moment?

If the latter, the change is out of scope.

---

## Closing Constraint

These structural goals exist to ensure that:
- branding lives at the site layer,
- authority lives in governance documents,
- and themes remain neutral infrastructure.

Any change that compromises those properties must be rejected.
