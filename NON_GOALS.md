# NON_GOALS.md

**PlainSight Lab — Public Hugo Theme Substrate**

**Status:** Binding execution constraints
**Audience:** Human contributors and automated agents
**Applies to:**
- `hugo-theme-aperture`
- `hugo-theme-invariant`
- `hugo-theme-operator`

---

## Purpose of This Document

These Hugo themes are **infrastructure**, not products, brands, or narratives.

This document defines what these themes **must not do**, even if doing so would appear helpful,
convenient, or aesthetically pleasing.

Violations of these non-goals constitute **design drift**, not improvement.

This document is intended to be referenced by `AGENTS.md` and enforced during both human and
automated contributions.

---

## Global Non-Goals (All Themes)

The following are explicitly out of scope for **all** themes.

### 1. Themes must not encode brand identity

Themes must **not** contain:

- Logos or logomarks
- Exact brand colors or hex values
- Taglines, slogans, or mission statements
- Brand-specific iconography
- Institutional language tied to PlainSight Lab or any derivative entity

Themes may support **semantic tokens** (e.g. `accent`, `warning`, `authority`) but must not assign
brand-specific values.

> Branding is a **site-level concern**, not a theme concern.

---

### 2. Themes must not imply authority, legitimacy, or endorsement

Themes must not:

- Assert or imply governance authority
- Suggest canonical truth
- Convey institutional legitimacy by default
- Imply first-party status for any site using the theme

Use of a theme must never be interpreted as endorsement, certification, or governance alignment.

---

### 3. Themes must not contain product, protocol, or domain logic

Themes must not include:

- Domain-specific assumptions (finance, AI, compliance, safety, etc.)
- Protocol semantics
- Workflow logic
- Business rules
- Validation logic beyond presentation-level accessibility

Themes are **presentation substrates only**.

---

### 4. Themes must not optimize for growth, conversion, or persuasion

Themes must not include:

- Marketing funnels
- Conversion optimization patterns
- Growth-oriented UX
- Engagement dark patterns
- Persuasive copy defaults
- Emotional manipulation cues

Clarity is permitted. Persuasion is not.

---

### 5. Themes must not assume friendliness or informality

Themes must not default to:

- Casual tone
- Friendly language
- Playful affordances
- Social-media-style layouts
- Trend-driven aesthetics

Neutral, structured, and professional is the maximum permitted tone.

---

### 6. Themes must not depend on JavaScript-heavy frameworks

Themes must not:

- Require client-side frameworks (React, Vue, etc.)
- Depend on build-time JavaScript pipelines
- Assume runtime JavaScript availability for core navigation or reading

Progressive enhancement is allowed. Dependency is not.

---

### 7. Themes must not sacrifice legibility for aesthetics

Themes must not:

- Reduce contrast for stylistic reasons
- Obscure hierarchy for visual novelty
- Use decorative typography at the expense of clarity
- Hide structure behind animation or effects

Readability is non-negotiable.

---

## Theme-Specific Non-Goals

### A. `hugo-theme-aperture`

*(Institutional / Governance Surface)*

This theme must **not**:

- Behave like a marketing or startup site
- Emphasize founders, personalities, or narratives
- Include testimonials, quotes, or social proof
- Use aspirational or inspirational framing
- Present itself as a product landing page

This theme exists to support **institutional explanation**, not promotion.

---

### B. `hugo-theme-invariant`

*(Specifications / Canonical Truth Surface)*

This theme must **not**:

- Optimize for casual reading
- Simplify or editorialize specifications
- Hide complexity for accessibility
- Reframe content for persuasion or adoption
- Add narrative interpretation to source material

This theme prioritizes:
- precision over comfort
- correctness over approachability

---

### C. `hugo-theme-operator`

*(Product / Tool Surface)*

This theme must **not**:

- Imply automation replaces human authority
- Present AI systems as autonomous actors
- Hide decision boundaries
- Over-abstract operational controls
- Use “magic” metaphors (agents, brains, copilots, etc.)

Operator clarity is required. Automation mystique is forbidden.

---

## Explicitly Rejected Patterns

The following patterns are **always invalid**:

- “AI-native” framing
- “Next-generation” language
- Trend-driven UI metaphors
- Gamification
- Emotional urgency without mechanism
- Visual branding baked into themes
- Authority implied by aesthetics alone

---

## Enforcement Rule (For Agents)

When modifying or extending a theme:

> If a change would make the theme *feel more like a brand, a product, or an authority*
> without site-level overrides, the change is invalid.

When in doubt:
- prefer less
- prefer neutral
- prefer explicit structure over cleverness

---

## Closing Constraint

These themes are designed to **outlive** any single site, organization, or phase.

They must remain:
- reusable without endorsement
- expressive without authority
- structured without persuasion

Anything that violates those properties is out of scope.
