<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./plainsight-labs-logo-dark.svg" />
    <img src="./plainsight-labs-logo.svg" alt="PlainSight Lab" width="160" />
  </picture>
</p>

<h1 align="center">PlainSight Lab</h1>

<p align="center">
  <strong>Trust through Transparency</strong><br>
  Governance-first systems for adversarial, AI-amplified environments
</p>

<p align="center">
  <a href="https://plainsightlab.com">plainsightlab.com</a>
</p>

---

## About

PlainSight Lab operates at the substrate layer of high-risk systems. It produces canonical governance frameworks, threat models, and institutional design patterns for systems where:

- **E<sub>correction</sub> < E<sub>propagation</sub>** — Correction cost must remain lower than propagation cost before scale
- **Constraint precedes acceleration** — Authority must be bound before expansion
- **Truth must be explicit** — Specifications are singular, explicit, and publicly accessible

This repository contains the source code for the PlainSight Lab public-facing site, built with [Hugo](https://gohugo.io) and deployed via Cloudflare Workers.

## Local Development

### Prerequisites

- [Hugo](https://gohugo.io/installation/) v0.154.2 or later (extended version)
- Git

### Setup

1. Clone the repository with submodules:
   ```bash
   git clone --recurse-submodules https://github.com/plainsight-lab/plainsight-lab-site.git
   cd plainsight-lab-site
   ```

2. If you've already cloned without submodules, initialize them:
   ```bash
   git submodule update --init --recursive
   ```

3. Run the development server:
   ```bash
   hugo server -D
   ```

4. Open [http://localhost:1313](http://localhost:1313) in your browser.

### Project Structure

```
.
├── assets/           # CSS overrides and custom assets
├── content/          # Markdown content
├── layouts/          # Template overrides and custom layouts
├── static/           # Static files (images, fonts, etc.)
└── themes/
    └── hugo-theme-aperture/  # Theme submodule
```

## Theme

The site uses the [`hugo-theme-aperture`](https://github.com/plainsight-lab/hugo-theme-aperture) theme as a git submodule. The theme is designed to be brand-capable without brand defaults—all visual decisions are expressed as semantic CSS tokens and can be overridden at the site level.

Brand-specific overrides are located in:
- `assets/css/tokens.css` — Brand design tokens
- `assets/css/layout.css` — Layout-specific overrides
- `assets/css/components.css` — Component-level customizations

## Deployment

The site is automatically deployed to Cloudflare Workers Static Assets via GitHub Actions on every push to the `main` branch.

### Deployment Architecture

- **Build**: Hugo generates static files to `./public`
- **Deploy**: Wrangler deploys assets to Cloudflare Workers
- **CI/CD**: GitHub Actions workflow (`.github/workflows/deploy.yaml`)

### Required Secrets

The following GitHub repository secrets must be configured:

- `CLOUDFLARE_API_TOKEN` — Cloudflare API token with Workers deploy permissions
- `CLOUDFLARE_ACCOUNT_ID` — Cloudflare account ID

## License

Copyright © 2026 PlainSight Lab. All rights reserved.

The content, documentation, and governance artifacts in this repository are licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

The source code (theme, build configuration, templates) is licensed under the [MIT License](LICENSE).

**Attribution Requirement**: When referencing, forking, or adapting content from this repository, you must provide clear attribution to PlainSight Lab and link to the original source.

## Contributing

PlainSight Lab is a transparency-first organization. Contributions are governed by the [Internal Constitution](https://plainsightlab.com/docs/internal-constitution/) and must align with the [Governance Framework](https://plainsightlab.com/docs/governance-framework/).

For security disclosures, see the [Responsible Disclosure Policy](https://plainsightlab.com/docs/responsible-disclosure-policy/).

## Contact

- **Website**: [plainsightlab.com](https://plainsightlab.com)
- **Governance**: [plainsightlab.com/governance](https://plainsightlab.com/governance/)
- **Documentation**: [plainsightlab.com/docs](https://plainsightlab.com/docs/)
- **Contact Form**: [plainsightlab.com/contact](https://plainsightlab.com/contact/)

---

<p align="center">
  <strong>Systems whose constraints, authority, and invariants hold under the hardest conditions.</strong>
</p>
