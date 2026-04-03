# Repository Architecture

## Overview

This document explains the structural organization of the Flavio Fusuma branding repository. The repository is designed as a self-contained, production-ready brand system that serves designers, engineers, and content creators from a single source of truth.

---

## Directory Structure

```
branding/
├── README.md                          Project overview and quick navigation
├── 01-brand-identity/                 Brand strategy and visual identity
│   ├── 00-overview.md                 Brand book overview and table of contents
│   ├── 01-brand-strategy.md           Purpose, vision, mission, values, positioning
│   ├── 02-brand-narrative.md          Archetype, personality, origin story
│   ├── 03-tone-of-voice.md            Voice dimensions, tone matrix, writing rules
│   ├── 04-messaging-hierarchy.md      Tagline, elevator pitch, messaging pillars
│   ├── 05-logo-concepts.md            Three logo directions with SVG specs
│   ├── 06-logo-usage-guidelines.md    Clear space, minimum size, misuse examples
│   ├── 07-color-system.md             Full palette (Hex, RGB, CMYK, Pantone)
│   ├── 08-typography.md               Typeface selection, pairing, loading strategy
│   ├── 09-visual-direction.md         Photography, illustration, iconography, motion
│   ├── 10-brand-applications.md       Business card, letterhead, social, favicons
│   └── 11-brand-governance.md         Approval process, versioning, audit checklist
├── 02-design-system/                  Design system foundations and components
│   ├── 00-overview.md                 System purpose, principles summary, architecture
│   ├── 01-design-principles.md        Six core principles guiding all decisions
│   ├── 02-color/                      Color documentation
│   │   ├── color-system.md            Usage guidelines and semantic mapping
│   │   ├── dark-mode.md               Dark theme palette and behavior
│   │   └── contrast-ratios.md         WCAG AA/AAA compliance matrix
│   ├── 03-typography/                 Typography documentation
│   │   ├── type-scale.md              12-level type scale with responsive behavior
│   │   ├── line-heights.md            Line height system and vertical rhythm
│   │   └── accessibility.md           Text accessibility requirements
│   ├── 04-layout/                     Layout documentation
│   │   ├── grid-system.md             12-column grid with breakpoints
│   │   ├── spacing.md                 8px base unit framework
│   │   └── responsive.md              Responsive design strategy
│   ├── 05-components/                 UI component documentation
│   │   ├── 00-component-template.md   Template for documenting new components
│   │   ├── alerts.md                  Alert component spec
│   │   ├── avatar.md                  Avatar component spec
│   │   ├── buttons.md                 Button component spec
│   │   ├── divider.md                 Divider component spec
│   │   ├── inputs.md                  Input component spec
│   │   ├── skeleton.md                Skeleton loader spec
│   │   ├── table.md                   Table component spec
│   │   ├── tags.md                    Tag component spec
│   │   ├── text-areas.md              Textarea component spec
│   │   └── toast.md                   Toast notification spec
│   ├── 07-accessibility.md            Global accessibility guidelines
│   └── 08-developer-handoff.md        Implementation guide for engineers
├── 03-design-tokens/                  W3C DTCG format design tokens
│   ├── README.md                      Token system documentation
│   ├── style-dictionary.config.json   Style Dictionary configuration
│   ├── global/                        Primitive token values
│   │   ├── color.tokens.json          Color scales (blue, amber, neutral, semantic, extended)
│   │   ├── typography.tokens.json     Font families, sizes, weights, line-heights
│   │   ├── spacing.tokens.json        Spacing scale (4px sub-grid, 8px base)
│   │   ├── border.tokens.json         Border radius and width scales
│   │   ├── shadow.tokens.json         Elevation shadow system (5 levels)
│   │   ├── motion.tokens.json         Duration and easing curves
│   │   └── opacity.tokens.json        Opacity scale (0-100)
│   ├── semantic/                      Semantic token aliases
│   │   ├── color.tokens.json          Background, text, border, icon, interactive
│   │   ├── typography.tokens.json     Display, heading, body, label, caption, code
│   │   └── component.tokens.json      Component-scoped tokens
│   └── themes/                        Theme overrides
│       ├── light.tokens.json          Light theme (default)
│       └── dark.tokens.json           Dark theme
├── 04-styles/                         SCSS implementation
│   ├── README.md                      Usage guide, import order, customization
│   ├── main.scss                      Entry point (imports all partials)
│   ├── _variables.scss                CSS custom properties + SCSS variables
│   ├── _reset.scss                    Modern CSS reset
│   ├── _colors.scss                   Color utilities + dark mode overrides
│   ├── _typography.scss               Type scale and font utilities
│   ├── _spacing.scss                  Margin, padding, gap utilities
│   └── _grid.scss                     Container, 12-column grid, column spans
├── 05-marketing/                      Campaign and content assets
│   ├── 00-messaging-framework.md      Unified messaging strategy
│   └── 01-campaign-google-ads.md      Google Ads campaign specs
├── 06-figma-specs/                    Figma implementation specs
│   └── 00-file-structure.md           Page and frame hierarchy
└── docs/                              Repository documentation
    ├── architecture.md                This file
    └── changelog.md                   Version history
```

---

## Design Principles

### Layered Architecture

The repository follows a layered architecture where each layer builds on the one below it:

```
Layer 1: Brand Identity (01-)
    Why the brand exists, what it stands for, how it communicates.
    Pure strategy and creative direction. No implementation details.

Layer 2: Design System (02-)
    How brand decisions translate into systematic design rules.
    Principles, scales, component patterns, accessibility requirements.

Layer 3: Design Tokens (03-)
    The bridge between design and code. Machine-readable values
    in W3C DTCG format that encode every design decision as data.

Layer 4: Styles (04-)
    Production CSS implementation. SCSS files that consume
    design tokens and output utility classes and custom properties.

Layer 5: Marketing (05-)
    Campaign-specific applications of the brand system.
    Copy, ad specs, email sequences, content calendars.

Layer 6: Figma Specs (06-)
    Design tool implementation. How to build the system in Figma
    with auto-layout, variants, and design token integration.
```

### Separation of Concerns

- **Brand identity** never references implementation details (no CSS, no JSON, no pixel values in strategy docs)
- **Design tokens** are format-agnostic (W3C DTCG format, consumable by Style Dictionary, Figma Tokens, or custom tooling)
- **SCSS styles** reference tokens, not raw values (changes propagate from tokens to styles)
- **Marketing** references brand identity for messaging and design system for visual execution

### Single Source of Truth

Every design decision has exactly one canonical location:

| Decision | Canonical Source |
|----------|-----------------|
| Brand color values | `03-design-tokens/global/color.tokens.json` |
| Semantic color mapping | `03-design-tokens/semantic/color.tokens.json` |
| Dark mode overrides | `03-design-tokens/themes/dark.tokens.json` |
| Typography scale | `03-design-tokens/semantic/typography.tokens.json` |
| Spacing scale | `03-design-tokens/global/spacing.tokens.json` |
| Component behavior | `02-design-system/05-components/{component}.md` |
| Brand voice | `01-brand-identity/03-tone-of-voice.md` |
| Logo specifications | `01-brand-identity/05-logo-concepts.md` |

### Naming Conventions

| Convention | Pattern | Example |
|------------|---------|---------|
| Directory numbering | `{NN}-{name}/` | `01-brand-identity/` |
| File numbering | `{NN}-{name}.md` | `07-color-system.md` |
| SCSS partials | `_{name}.scss` | `_variables.scss` |
| Token files | `{name}.tokens.json` | `color.tokens.json` |
| CSS custom properties | `--{category}-{name}` | `--color-blue-800` |
| SCSS variables | `${name}` | `$breakpoints` |
| Utility classes | `.{property}-{value}` | `.text-primary` |

---

## Token-to-Style Pipeline

```
Token JSON                    SCSS Variables              CSS Output
─────────────                ──────────────              ──────────
color.tokens.json    --->    _variables.scss     --->    :root { --color-blue-800: #1E3A5F; }
  blue.800: #1E3A5F           --color-blue-800

semantic/color.json  --->    _variables.scss     --->    :root { --color-text-brand: var(--color-blue-800); }
  text.brand: {blue.800}      --color-text-brand

themes/dark.json     --->    _colors.scss        --->    [data-theme="dark"] { --color-text-brand: var(--color-blue-300); }
  text.brand: {blue.300}      [data-theme="dark"]

                              _colors.scss        --->    .text-brand { color: var(--color-text-brand); }
                              utility classes
```

This pipeline ensures that a single change to a token value propagates automatically through semantic aliases, theme overrides, and utility classes.

---

## Consumption Patterns

### For Web Projects (SCSS)

```scss
// Import the full system
@use 'path/to/04-styles/main';

// Or import only what you need
@use 'path/to/04-styles/variables' as *;
@use 'path/to/04-styles/grid';
```

### For JavaScript / TypeScript Projects

```js
// Import tokens directly as JSON
import colorTokens from 'path/to/03-design-tokens/global/color.tokens.json';
import semanticColors from 'path/to/03-design-tokens/semantic/color.tokens.json';
```

### For Figma

Follow the specifications in `06-figma-specs/` to build the token system using Figma variables and the Tokens Studio plugin. The token JSON files in `03-design-tokens/` are directly importable.

### For Style Dictionary

The `03-design-tokens/style-dictionary.config.json` file configures Style Dictionary to transform tokens into platform-specific outputs (CSS, SCSS, iOS, Android).

---

## Contributing

1. All changes start as issues describing the gap or improvement needed.
2. Changes to foundational tokens (Layer 3) require impact analysis across all downstream layers.
3. Changes to brand identity (Layer 1) require brand owner approval.
4. Follow the versioning strategy documented in `01-brand-identity/11-brand-governance.md`.

---

**Version**: 1.0.0
**Last Updated**: April 2026
