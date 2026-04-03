# Flavio Fusuma — Brand Identity & Design System

A comprehensive, production-ready brand identity system and design framework for [flaviofusuma.com](https://flaviofusuma.com).

---

## Overview

This repository contains the complete brand identity, design system, marketing assets, and implementation specifications for the Flavio Fusuma personal brand. Every design decision is grounded in strategic thinking, accessibility compliance, and real-world implementation readiness.

## Repository Structure

```
├── 01-brand-identity/       Brand strategy, narrative, logo, color, typography
├── 02-design-system/        Design principles, components, patterns, accessibility
├── 03-design-tokens/        W3C DTCG format tokens (global, semantic, themes)
├── 04-styles/               SCSS implementation of the design token system
├── 05-marketing/            Campaign assets, email sequences, content strategy
├── 06-figma-specs/          Figma file structure, auto-layout, component specs
└── docs/                    Architecture documentation and changelog
```

## Quick Navigation

### Brand Identity
| Document | Description |
|----------|-------------|
| [Brand Strategy](01-brand-identity/01-brand-strategy.md) | Purpose, vision, mission, values, positioning |
| [Brand Narrative](01-brand-identity/02-brand-narrative.md) | Archetype, personality, origin story |
| [Tone of Voice](01-brand-identity/03-tone-of-voice.md) | Voice matrix, writing guidelines |
| [Messaging Hierarchy](01-brand-identity/04-messaging-hierarchy.md) | Tagline, elevator pitch, pillars |
| [Logo Concepts](01-brand-identity/05-logo-concepts.md) | Three logo directions with SVG specs |
| [Logo Usage](01-brand-identity/06-logo-usage-guidelines.md) | Clear space, minimum size, misuse |
| [Color System](01-brand-identity/07-color-system.md) | Full palette (Hex, RGB, CMYK, Pantone) |
| [Typography](01-brand-identity/08-typography.md) | Typeface selection and pairing |
| [Visual Direction](01-brand-identity/09-visual-direction.md) | Photography, illustration, iconography |
| [Brand Applications](01-brand-identity/10-brand-applications.md) | Business card, letterhead, social |
| [Brand Governance](01-brand-identity/11-brand-governance.md) | Approval process, versioning |

### Design System
| Document | Description |
|----------|-------------|
| [Design Principles](02-design-system/01-design-principles.md) | Core principles guiding all decisions |
| [Color System](02-design-system/02-color/color-system.md) | Usage guidelines and semantic mapping |
| [Dark Mode](02-design-system/02-color/dark-mode.md) | Dark theme palette and behavior |
| [Contrast Ratios](02-design-system/02-color/contrast-ratios.md) | WCAG AA/AAA compliance matrix |
| [Type Scale](02-design-system/03-typography/type-scale.md) | 9+ level scale with responsive behavior |
| [Grid System](02-design-system/04-layout/grid-system.md) | 12-column grid with breakpoints |
| [Spacing](02-design-system/04-layout/spacing.md) | 8px base unit framework |
| [Components](02-design-system/05-components/) | 30+ documented UI components |
| [Accessibility](02-design-system/07-accessibility.md) | Global accessibility guidelines |
| [Developer Handoff](02-design-system/08-developer-handoff.md) | Implementation guide for engineers |

### Design Tokens
| File | Description |
|------|-------------|
| [Global Tokens](03-design-tokens/global/) | Primitive values (color, type, spacing) |
| [Semantic Tokens](03-design-tokens/semantic/) | Meaningful aliases and component tokens |
| [Themes](03-design-tokens/themes/) | Light and dark theme overrides |

### Marketing
| Document | Description |
|----------|-------------|
| [Messaging Framework](05-marketing/00-messaging-framework.md) | Unified messaging strategy |
| [Google Ads](05-marketing/01-campaign-google-ads.md) | Search and display campaigns |
| [Meta Ads](05-marketing/02-campaign-meta-ads.md) | Facebook and Instagram campaigns |
| [Email Sequences](05-marketing/04-email-sequences.md) | Welcome, nurture, re-engagement |
| [Landing Page](05-marketing/05-landing-page-copy.md) | Full page copy and structure |
| [Social Content](05-marketing/06-social-media-content.md) | Content calendar and templates |

### Figma Specs
| Document | Description |
|----------|-------------|
| [File Structure](06-figma-specs/00-file-structure.md) | Page and frame hierarchy |
| [Auto-Layout](06-figma-specs/02-auto-layout.md) | Property specifications |
| [Component System](06-figma-specs/03-component-system.md) | Variant structure and naming |

## Design Token Architecture

The token system uses three layers following the W3C Design Tokens Community Group format:

```
Layer 1: Global (Primitives)     → color.blue.500 = "#1E56A0"
Layer 2: Semantic (Aliases)      → color.action.primary = "{color.blue.500}"
Layer 3: Component (Scoped)      → button.primary.bg = "{color.action.primary}"
```

Themes override semantic tokens, enabling dark mode without touching component definitions.

## Technology Stack

- **Token Format**: W3C DTCG (compatible with Style Dictionary, Figma Tokens)
- **Styles**: SCSS with CSS custom properties output
- **Typefaces**: Inter (UI) + JetBrains Mono (code)
- **Grid**: 12-column, 8px base unit
- **Accessibility**: WCAG 2.1 AA compliant (AAA where possible)

## Getting Started

1. Review the [Brand Strategy](01-brand-identity/01-brand-strategy.md) to understand the foundational positioning
2. Explore [Design Tokens](03-design-tokens/) for implementation values
3. Reference [Components](02-design-system/05-components/) for UI patterns
4. Use [SCSS Styles](04-styles/) for direct CSS implementation
5. Follow the [Developer Handoff](02-design-system/08-developer-handoff.md) guide for integration

---

**Version**: 1.0.0  
**Last Updated**: April 2026  
**Maintainer**: Flavio Fusuma
