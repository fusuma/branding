# Changelog

All notable changes to the Flavio Fusuma brand system are documented in this file.

This project follows [Semantic Versioning](https://semver.org/):
- **Major** (x.0.0) — Breaking changes to tokens, visual identity, or system architecture
- **Minor** (1.x.0) — New additions that do not break existing usage
- **Patch** (1.0.x) — Bug fixes, corrections, documentation improvements

---

## [1.0.0] — 2026-04-03

### Initial Release

The complete Flavio Fusuma brand identity and design system, production-ready for implementation across web, print, and marketing channels.

### Brand Identity

- **Brand Strategy** (`01-brand-strategy.md`) — Purpose, vision, mission, five core values (Craftsmanship, Clarity, Collaboration, Curiosity, Impact), positioning statement, target audience mapping, brand promise, key differentiators, and brand essence.
- **Brand Narrative** (`02-brand-narrative.md`) — The Creator archetype with Sage supporting archetype. Five personality traits (Precise, Approachable, Confident, Curious, Intentional). Origin story and three narrative pillars (The Craft, The Bridge, The Community). Emotional mapping across touchpoints.
- **Tone of Voice** (`03-tone-of-voice.md`) — Four voice dimensions (Clear not Simplistic, Confident not Arrogant, Warm not Casual, Intentional not Verbose). Tone matrix across contexts. Writing guidelines with do/don't examples.
- **Messaging Hierarchy** (`04-messaging-hierarchy.md`) — Brand tagline, elevator pitch, messaging pillars with proof points.
- **Logo Concepts** (`05-logo-concepts.md`) — Three logo directions: FF Monogram (Concept A, primary), Fusuma Wordmark (Concept B, tertiary), Code Bracket Mark (Concept C, secondary). Full geometry specifications, SVG markup, construction methods, variations, and minimum sizes. Lockup system and concept comparison.
- **Logo Usage Guidelines** (`06-logo-usage-guidelines.md`) — Clear space rules, placement guidelines, misuse examples, file format specifications.
- **Color System** (`07-color-system.md`) — Primary blue (#1E3A5F) with 11-step scale. Accent amber (#F59E0B) with 11-step scale. 12-step neutral scale with blue undertone. Semantic colors (success, warning, error, info). Extended palette (teal, indigo, rose, violet, emerald, cyan). Usage guidelines, ratio recommendations, print CMYK and Pantone specifications.
- **Typography** (`08-typography.md`) — Inter (primary, humanist sans-serif) and JetBrains Mono (monospace). Weight selection, pairing rationale, font loading strategy, typographic hierarchy preview, fallback specifications.
- **Visual Direction** (`09-visual-direction.md`) — Photography style (mood, subjects, treatment, do/don't). Illustration system (geometric, line-based, brand color). Iconography (24x24 grid, stroke-based, 5 sizes). Graphic elements (patterns, textures, decorative elements). Motion and animation direction with timing specifications.
- **Brand Applications** (`10-brand-applications.md`) — Business card (3.5" x 2", front/back layouts, print specs). Letterhead (A4, header/footer, continuation page). Email signature (HTML structure, 500px max width). Social media profiles (LinkedIn, Twitter/X, GitHub dimensions and layouts). Presentation template (16:9, four slide layouts). Favicon and app icons (16, 32, 180, 192, 512px with HTML implementation).
- **Brand Governance** (`11-brand-governance.md`) — Approval workflows for internal and third-party usage. Semantic versioning strategy. Brand audit checklist (visual, digital, print, content, accessibility). Third-party usage rules and press kit contents. Asset distribution channels and deprecation policy.
- **Brand Book Overview** (`00-overview.md`) — 20-page brand book table of contents with page-by-page outline. Usage guide for brand owners, designers, engineers, and partners.

### Design System

- **Design Principles** (`01-design-principles.md`) — Six core principles: Clarity Over Cleverness, Accessible By Default, Systematic Flexibility, Content First, Purposeful Motion, Honest Interfaces.
- **Color System** (`02-color/`) — Full color usage documentation, dark mode implementation guide, WCAG AA/AAA contrast ratio compliance matrix.
- **Typography** (`03-typography/`) — 12-level type scale with responsive behavior, line height system, typography accessibility guidelines.
- **Layout** (`04-layout/`) — 12-column CSS Grid system with four breakpoints (375, 768, 1024, 1440px), 8px-based spacing scale, responsive design strategy.
- **Components** (`05-components/`) — 10 documented UI components: alerts, avatar, buttons, divider, inputs, skeleton, table, tags, text areas, toast. Each with anatomy, variants, states, accessibility requirements, and design token mappings.
- **Accessibility** (`07-accessibility.md`) — Global accessibility guidelines targeting WCAG 2.1 AA.
- **Developer Handoff** (`08-developer-handoff.md`) — Implementation guide for engineers.

### Design Tokens

- **Global Tokens** — Color primitives (11 palettes with full scales), typography (font families, 14 sizes, 9 weights, 6 line heights, 6 letter spacings), spacing (19 steps from 0 to 384px), border (7 radius values, 5 widths), shadow (5 elevation levels), motion (9 durations, 6 easing curves), opacity (17 steps).
- **Semantic Tokens** — Color aliases (background, text, border, icon, interactive categories with 10-16 variants each), typography roles (display, heading, body, label, caption, overline, code), component tokens.
- **Theme Tokens** — Light theme (default) and dark theme with complete semantic color remapping and shadow adjustments.
- **Style Dictionary** — Configuration file for multi-platform token transformation.

### SCSS Styles

- **Variables** (`_variables.scss`) — All design tokens as CSS custom properties on `:root`. SCSS variables for breakpoints, container widths, grid settings, spacing scale, and z-index. Breakpoint mixin.
- **Reset** (`_reset.scss`) — Modern CSS reset with box-sizing, margin removal, form normalization, media element defaults, reduced-motion support, focus-visible styling.
- **Colors** (`_colors.scss`) — Semantic color utilities (`.text-*`, `.bg-*`, `.border-*`), primitive scale utilities, dark mode overrides via `[data-theme="dark"]`.
- **Typography** (`_typography.scss`) — Type scale classes (display, heading, body, label, caption, overline, code), font family and weight utilities, text alignment, responsive font sizing, truncation utilities.
- **Spacing** (`_spacing.scss`) — Margin (`.m-*`, `.mx-*`, `.my-*`, `.mt-*`, `.mr-*`, `.mb-*`, `.ml-*`), padding (`.p-*`, `.px-*`, `.py-*`, `.pt-*`, `.pr-*`, `.pb-*`, `.pl-*`), gap (`.gap-*`), auto utilities, responsive variants.
- **Grid** (`_grid.scss`) — Container classes (default, fluid, narrow), 12-column CSS Grid, column span classes (`.col-{n}`), responsive columns (`.col-{bp}-{n}`), column start, row span, alignment utilities, common layout patterns.
- **Entry Point** (`main.scss`) — Imports all partials in dependency order.

### Marketing

- **Messaging Framework** (`00-messaging-framework.md`) — Unified messaging strategy.
- **Google Ads Campaign** (`01-campaign-google-ads.md`) — Search and display campaign specifications.

### Figma Specs

- **File Structure** (`00-file-structure.md`) — Page and frame hierarchy for Figma implementation.

### Documentation

- **Repository README** — Project overview, directory structure, quick navigation tables, technology stack, getting started guide.
- **Architecture** (`docs/architecture.md`) — Layered architecture explanation, separation of concerns, single source of truth mapping, naming conventions, token-to-style pipeline, consumption patterns.
- **Changelog** (`docs/changelog.md`) — This file.

---

## Unreleased

_No unreleased changes._

---

## Planned

- **1.1.0** — Additional UI components (modal, dropdown, navigation, card, badge, tooltip, progress bar). Email template designs. Social media post templates.
- **1.2.0** — npm package for design tokens. Style Dictionary build pipeline automation. Storybook integration documentation.
- **2.0.0** — Reserved for any breaking changes to the token structure, color system, or typography scale.
