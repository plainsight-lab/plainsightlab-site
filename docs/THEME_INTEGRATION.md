# Theme Integration Guide

This document explains how PlainSight Lab site integrates with the `hugo-theme-aperture` theme.

## Architecture Overview

The site uses a **layered override system** that respects the theme's architecture while applying brand-specific customizations.

### CSS Layer System

CSS is organized using CSS `@layer` for proper cascade control:

```
Theme (main.css) → Tokens → Layout → Components
```

**Layer Hierarchy:**
1. **@layer tokens** - Design tokens (colors, typography, spacing)
2. **@layer layout** - Layout structure and overrides
3. **@layer components** - Component-specific styling

### CSS Files

| File | Layer | Purpose |
|------|-------|---------|
| `themes/.../main.css` | All | Theme's base styles |
| `assets/css/tokens.css` | tokens | PlainSight brand tokens |
| `assets/css/layout.css` | layout | Layout customizations |
| `assets/css/components.css` | components | Brand components |

**Load Order (hugo.toml):**
```toml
customCSS = ["css/tokens.css", "css/layout.css", "css/components.css"]
```

## Template Overrides

### Partials

PlainSight Lab overrides these theme partials:

| Partial | Override Reason |
|---------|----------------|
| `layouts/partials/header.html` | Custom logo, active nav indicators |
| `layouts/partials/footer.html` | Multi-column footer layout |

All other partials use theme defaults.

### Custom Partials

Site-specific partials live in `layouts/partials/components/`:

| Partial | Purpose |
|---------|---------|
| `doc-card.html` | Reusable document card with status |
| `gov-card.html` | Reusable governance card |
| `doc-meta.html` | Document metadata panel |
| `canonical-callout.html` | View layer callout |

**Usage Example:**
```hugo
{{ partial "components/doc-card.html" (dict "title" "My Doc" "slug" "my-doc") }}
```

## Shortcodes

### Callout

PlainSight Lab uses the **theme's callout shortcode** (not overridden).

**Available Types:**
- `note` - Default informational
- `info` - Steel blue accent
- `warning` - Crimson warning (brand override)
- `danger` - Crimson danger
- `frost` - Frost blue (brand extension)

**Usage:**
```hugo
{{< callout type="warning" title="Important" >}}
This is a warning callout.
{{< /callout >}}
```

## Component Patterns

### Card Status Indicator

Cards with left-border status indicators use `.card--status-indicator`:

```html
<article class="card card--status-indicator doc-card doc-card--published">
  <!-- Card content -->
</article>
```

**CSS Pattern:**
- Base: `.card--status-indicator` provides 3px left border structure
- Variants: `.doc-card::before`, `.gov-card::before` set border color

## Brand Integration

### Design Tokens

All brand-specific values are defined in `assets/css/tokens.css` and map to the brand guide:

| Brand Guide | Token | Usage |
|-------------|-------|-------|
| Charcoal (#1a1a1a) | `--theme-charcoal` | Primary text, headers |
| Off-White (#e8e6e1) | `--theme-offwhite` | Background |
| Slate (#4a5568) | `--theme-slate` | Secondary text |
| Steel Blue (#2c5f7e) | `--theme-steel-blue` | Links, accents |
| Crimson (#8b1e1e) | `--theme-crimson` | Warnings, status |
| Frost (#c1d5e0) | `--theme-frost` | Code blocks, alt surfaces |

### Typography

```css
--font-sans: "Inter", -apple-system, ...;
--font-mono: "JetBrains Mono", ui-monospace, ...;
```

Font weights, sizes, and line heights match the brand guide exactly.

## Extending the Theme

### Adding a New Component

1. **Define CSS in `assets/css/components.css`:**
   ```css
   @layer components {
     .my-component {
       /* Use tokens, not hardcoded values */
       color: var(--color-fg);
       padding: var(--space-md);
     }
   }
   ```

2. **Create partial in `layouts/partials/components/`:**
   ```hugo
   {{/* my-component.html */}}
   <div class="my-component">
     {{ .content }}
   </div>
   ```

3. **Use in layouts:**
   ```hugo
   {{ partial "components/my-component.html" (dict "content" "Hello") }}
   ```

### Overriding Theme Styles

**Prefer tokens over components:**
- Override tokens in `tokens.css` for global changes
- Override components in `components.css` for specific changes
- Never hardcode colors/spacing

**Example - Change accent color:**
```css
/* Good: Override token */
@layer tokens {
  :root {
    --color-accent: #new-color;
  }
}

/* Bad: Override component */
@layer components {
  .button {
    background: #new-color; /* Hardcoded! */
  }
}
```

## Theme Updates

When updating `hugo-theme-aperture`:

1. Review theme's `CHANGELOG.md` for breaking changes
2. Check if new CSS variables added (update `tokens.css` if needed)
3. Check if overridden partials changed (header, footer)
4. Test build: `hugo --quiet`
5. Visual regression test all page types

## Troubleshooting

### Styles not applying

1. Check CSS load order in `hugo.toml`
2. Verify correct `@layer` in CSS file
3. Check browser DevTools for cascade order
4. Ensure Hugo build completed: `hugo --gc`

### Partial not found

1. Check path: `layouts/partials/components/name.html`
2. Verify partial name in template matches filename
3. Check theme partials: `themes/.../layouts/partials/`

### Build errors

```bash
# Verbose build output
hugo --verbose

# Check for template errors
hugo --templateMetrics
```

## Reference

- Theme repo: `themes/hugo-theme-aperture/`
- Brand guide: `Public_Brand_Guide.md`
- Hugo docs: https://gohugo.io/documentation/
