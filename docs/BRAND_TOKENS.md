# Brand Tokens Reference

This document maps the PlainSight Lab brand guide to CSS design tokens.

## Overview

Design tokens are defined in `assets/css/tokens.css` within the `@layer tokens` block. They override the theme's default tokens to apply PlainSight Lab's brand identity.

**Single Source of Truth:**
```
Public_Brand_Guide.md → tokens.css → components.css
```

## Color Palette

### Primary Colors

| Brand Name | Hex | Token | Usage |
|------------|-----|-------|-------|
| Charcoal | `#1a1a1a` | `--theme-charcoal` | Primary text, headers, code bg |
| Off-White | `#e8e6e1` | `--theme-offwhite` | Primary background, code text |
| Slate | `#4a5568` | `--theme-slate` | Secondary text, borders, dividers |

### Accent Colors

| Brand Name | Hex | Token | Usage |
|------------|-----|-------|-------|
| Steel Blue | `#2c5f7e` | `--theme-steel-blue` | Links, interactive elements |
| Crimson | `#8b1e1e` | `--theme-crimson` | Warnings, alerts, status (sparingly) |
| Frost | `#c1d5e0` | `--theme-frost` | Code blocks, data tables, alt surfaces |

### Semantic Color Mappings

These map brand colors to semantic purposes:

```css
--color-bg: var(--theme-offwhite);
--color-fg: var(--theme-charcoal);
--color-muted: var(--theme-slate);
--color-border: var(--theme-slate);
--color-accent: var(--theme-steel-blue);
--color-surface-alt: var(--theme-frost);
--color-code-bg: var(--theme-charcoal);
--color-code-fg: var(--theme-offwhite);
--color-danger: var(--theme-crimson);
--color-warning: var(--theme-crimson);
```

## Typography

### Font Families

```css
--font-sans: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
--font-mono: "JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, ...;
```

**Usage:**
- `--font-sans` - All body text, headings, navigation, UI
- `--font-mono` - Code blocks, technical specs, data output

### Font Weights

| Token | Value | Brand Usage |
|-------|-------|-------------|
| `--font-weight-regular` | 400 | Body text |
| `--font-weight-medium` | 500 | Emphasis, subheadings |
| `--font-weight-semibold` | 600 | Section headers |
| `--font-weight-bold` | 700 | Primary headers |

### Type Scale

| Element | Token | Size | Weight | Brand Guide |
|---------|-------|------|--------|-------------|
| Hero | `--text-hero` | 3.5rem (56px) | Bold | Hero |
| H1 | `--text-3xl` | 2.5rem (40px) | Bold | H1 |
| H2 | `--text-2xl` | 2rem (32px) | Semibold | H2 |
| H3 | `--text-xl` | 1.5rem (24px) | Semibold | H3 |
| H4 | `--text-lg` | 1.25rem (20px) | Medium | H4 |
| Body | `--text-md` | 1rem (16px) | Regular | Body |
| Small | `--text-sm` | 0.875rem (14px) | Regular | Small |
| Caption | `--text-xs` | 0.75rem (12px) | Regular | Caption |

### Line Heights

```css
--line-tight: 1.2;   /* Headers */
--line-normal: 1.6;  /* Body text */
--line-code: 1.5;    /* Code blocks */
```

## Spacing Scale

| Token | Value | Brand Guide |
|-------|-------|-------------|
| `--space-2xs` | 4px | xs |
| `--space-xs` | 4px | xs |
| `--space-sm` | 8px | sm |
| `--space-md` | 16px | md |
| `--space-lg` | 24px | lg |
| `--space-xl` | 32px | xl |
| `--space-2xl` | 48px | 2xl |
| `--space-3xl` | 64px | 3xl |

**Usage Pattern:**
```css
/* Good: Use tokens */
.my-component {
  padding: var(--space-md);
  gap: var(--space-lg);
}

/* Bad: Hardcode values */
.my-component {
  padding: 16px;  /* Don't do this! */
}
```

## Layout Constraints

```css
--container-max: 1264px;           /* Max content width */
--container: min(1264px, 92vw);    /* Responsive container */
--page-gutter: var(--space-xl);    /* 32px */
```

From brand guide:
- Max content width: 1264px
- Default container: `min(1264px, 92vw)`
- Content centered with generous margins

## Border & Radius

```css
--radius-sm: 4px;   /* Buttons, cards, inputs */
--radius-md: 4px;   /* Larger components */
--shadow-sm: 0 1px 0 rgba(26, 26, 26, 0.12);  /* Minimal shadow */
```

**Brand Guide:**
- Border radius: 4px
- No pill shapes
- Minimal shadow only if needed for separation

## Changing Brand Colors

To update the brand color palette:

1. **Update brand guide** (`Public_Brand_Guide.md`)
2. **Update tokens** (`assets/css/tokens.css`):
   ```css
   @layer tokens {
     :root {
       --theme-charcoal: #new-color;  /* Update here */
     }
   }
   ```
3. **Rebuild site:** `hugo --gc`
4. **Visual check** all page types

**Do NOT change colors in:**
- `components.css` (use tokens instead)
- `layout.css` (use tokens instead)
- Template files (use CSS classes)

## Callout Variants

### Theme Callouts

These use theme's default token system:

```css
/* Defined by theme, overridden in tokens.css */
--callout-info-bg: var(--color-notice-bg);
--callout-info-border: var(--color-notice);
--callout-warning-bg: var(--theme-crimson);     /* Brand override */
--callout-warning-border: var(--theme-crimson); /* Brand override */
```

### Brand Callout Extension

Frost callout is PlainSight-specific, defined in `components.css`:

```css
@layer components {
  .callout--frost {
    --callout-bg: var(--theme-frost);
    --callout-border: var(--theme-frost);
  }
}
```

## Token Usage Guidelines

### ✓ Do This

```css
/* Use semantic tokens */
color: var(--color-fg);
background: var(--color-bg);
padding: var(--space-md);

/* Use brand tokens for specific colors */
border-color: var(--theme-crimson);
```

### ✗ Don't Do This

```css
/* Don't hardcode colors */
color: #1a1a1a;

/* Don't hardcode spacing */
padding: 16px;

/* Don't duplicate token definitions */
--my-custom-charcoal: #1a1a1a;  /* Use --theme-charcoal! */
```

## Adding New Tokens

If you need a new design token:

1. **Check if it exists** in theme or brand tokens
2. **Add to `tokens.css`** if brand-specific:
   ```css
   @layer tokens {
     :root {
       --theme-new-color: #value;
       --color-semantic-name: var(--theme-new-color);
     }
   }
   ```
3. **Update this document** with the new token
4. **Update brand guide** if it's a new brand color

## Reference

- Brand Guide: `/Public_Brand_Guide.md`
- Tokens File: `/assets/css/tokens.css`
- Components File: `/assets/css/components.css`
- Theme Integration: `/docs/THEME_INTEGRATION.md`
