# AGENTS.md  
**PlainSight Lab — Hugo Theme Governance**

**Status:** Binding  
**Audience:** Automated agents and human contributors  
**Scope:** All public Hugo themes stewarded by PlainSight Lab

---

## Purpose

This file defines **mandatory execution constraints** for any agent or human modifying, extending, or generating code, templates, styles, or documentation for PlainSight Lab–governed Hugo themes.

These themes are **infrastructure substrates**, not products, brands, or authorities.

Agents must treat these constraints as **hard rules**, not guidelines.

Failure to comply constitutes **governance drift**, not creative variance.

---

## Canonical Governance Documents

Agents MUST treat the following documents as authoritative and binding:

- `NON_GOALS.md` — Explicit exclusions and prohibitions  
- `STRUCTURAL_GOALS` - Structural goals and implementation opinions
- `AGENTS.md` — This document  

If a proposed change conflicts with any of the documents, the change is invalid and must not be applied.

---

## Global Execution Rules (All Themes)

### 1. Themes are substrate, not identity

Agents must NOT introduce:

- Brand identity
- Institutional voice
- Claims of authority or legitimacy
- Narrative positioning
- Product marketing language

Themes must remain **neutral containers** capable of expressing many sites without implying endorsement or governance.

---

### 2. Do not infer intent beyond structure

Agents must NOT:

- Infer business goals
- Optimize for conversion, growth, or engagement
- Add persuasive UX patterns
- Introduce emotional framing

If intent is not **explicitly encoded in structure**, it must not be added.

---

### 3. Prefer explicit structure over abstraction

Agents should:

- Favor clear templates over clever indirection
- Prefer semantic HTML over abstraction layers
- Expose hierarchy visibly
- Avoid “magic” behaviors

If a behavior cannot be understood by reading the template, it is too implicit.

---

### 4. Accessibility and legibility are non-negotiable

Agents must NOT:

- Reduce contrast for aesthetics
- Hide hierarchy
- Trade clarity for minimalism
- Use motion or animation to convey essential meaning

Accessibility is a correctness requirement, not a feature.

---

### 5. JavaScript is optional, never required

Agents must NOT:

- Introduce JS dependencies for core navigation or reading
- Require client-side frameworks
- Assume JS availability

Progressive enhancement is permitted.  
Dependency is prohibited.

---

### 6. Do not embed branding or authority via defaults

Agents must NOT hardcode:

- Colors tied to PlainSight Lab
- Logos or marks
- Taglines or slogans
- Authority-signaling language

Themes may expose **semantic hooks** only (e.g., CSS variables, layout slots).

All branding belongs at the **site override layer**.

---

### 7. When uncertain, choose restraint

If an agent is unsure whether a change is allowed:

- Choose the less expressive option
- Choose the more neutral option
- Choose the option that exposes structure without interpretation

Agents must never “fill in gaps” with assumptions.

---

## Theme-Specific Guidance Section (Template)

Each theme repository **may include additional constraints**, but only in the section below.

This section must:
- Apply **only** to the specific theme
- Never contradict `NON_GOALS.md`
- Never relax global constraints
- Be clearly scoped

### ⬇️ PLACE SPECIFIC THEME GUIDANCE BELOW ⬇️

```markdown
## Theme-Specific Agent Guidance — <THEME NAME>

**Theme:** <e.g. hugo-theme-aperture>  
**Scope:** This theme only

### Additional Constraints

- <Explicit constraint>
- <Explicit constraint>

### Explicit Non-Goals (Theme-Specific)

- <What this theme must never do>
- <What this theme must not imply>

### Notes for Agents

- <Clarifications to prevent misinterpretation>

### ⬆️ END THEME-SPECIFIC GUIDANCE ⬆️

No other sections may be added for theme-specific rules.

## Enforcement Rule

Agents must evaluate every proposed change against this question:

> Does this make the theme feel more like a brand, a product, or an authority without site-level overrides?

If yes, the change is invalid.

## Final Constraint

These themes are designed to outlive:
- PlainSight Lab
- Any derivative entity
- Any specific product
- Any current governance phase

Agents must optimize for:
- durability
- neutrality
- explicit structure
- future reuse without endorsement

**Anything that compromises those properties is out of scope.**


