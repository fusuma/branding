# Flavio Fusuma Design System

## Overview

The Flavio Fusuma Design System is a shared vocabulary of visual language, interaction patterns, and implementation guidelines that ensures consistency, accessibility, and quality across every product and touchpoint. It serves as the single source of truth for designers, engineers, and content creators building within the Flavio Fusuma ecosystem.

This documentation covers the foundational layers of the system -- color, typography, layout, spacing, and the principles that bind them. Component-level documentation builds on these foundations and lives in the `05-components` directory.

---

## Purpose

| Goal | What It Means |
|---|---|
| **Consistency** | Every surface looks and behaves like part of the same product family, regardless of which team built it. |
| **Speed** | Predefined tokens, scales, and patterns eliminate repetitive decision-making so teams ship faster. |
| **Accessibility** | WCAG 2.1 AA compliance is built into every default, not bolted on as an afterthought. |
| **Scalability** | The system accommodates new products, themes, and platforms without ad-hoc overrides. |
| **Shared Language** | Designers and engineers reference the same token names, the same scale steps, and the same principles. |

---

## How to Use This Documentation

### For Designers

1. Start with **01-design-principles.md** to understand the philosophy behind every decision.
2. Reference the **color system** and **type scale** when creating compositions.
3. Use the **grid system** and **spacing** docs to structure layouts.
4. Validate accessibility with the **contrast-ratios** and **typography accessibility** references.

### For Engineers

1. Map every value in these docs to the corresponding **design tokens** in `03-design-tokens/`.
2. Use token names (e.g., `color-primary-500`, `space-4`, `font-size-body-md`) rather than raw values.
3. Follow the **responsive** strategy and **grid system** for layout implementation.
4. Reference **dark-mode.md** when implementing theme switching.

### For Content Creators

1. Review **Content First** in the design principles.
2. Use the **type scale** to understand how content hierarchy works.
3. Reference **typography accessibility** for language and readability guidance.

---

## System Architecture

The design system is organized in layers, from abstract to concrete:

```
Principles          Why we make the choices we make
    |
Foundations          Color, typography, layout, spacing, motion
    |
Tokens              Named values that encode every foundation decision
    |
Components          Reusable UI elements built from tokens
    |
Patterns            Compositions of components solving common UX problems
```

### Directory Structure

```
02-design-system/
  00-overview.md              <-- You are here
  01-design-principles.md     Core philosophy
  02-color/
    color-system.md           Full color palette and usage
    dark-mode.md              Dark theme implementation
    contrast-ratios.md        WCAG compliance matrix
  03-typography/
    type-scale.md             12-level type scale
    line-heights.md           Line height system and vertical rhythm
    accessibility.md          Text accessibility requirements
  04-layout/
    grid-system.md            12-column grid
    spacing.md                8px-based spacing scale
    responsive.md             Responsive design strategy
  05-components/              Component documentation (separate)
  06-patterns/                Pattern documentation (separate)
```

---

## Design Principles (Summary)

The system is governed by six core principles. Each is documented in full in `01-design-principles.md`.

| # | Principle | Summary |
|---|---|---|
| 1 | **Clarity Over Cleverness** | Choose the obvious solution. If a user has to think about the interface, the interface has failed. |
| 2 | **Accessible By Default** | Every default meets WCAG 2.1 AA. Accessibility is a baseline, not a feature. |
| 3 | **Systematic Flexibility** | Provide structured options, not open-ended freedom. Constrain choices to those that produce good outcomes. |
| 4 | **Content First** | Design around real content. The interface exists to serve the content, not the other way around. |
| 5 | **Purposeful Motion** | Every animation communicates something. If it does not, remove it. |
| 6 | **Honest Interfaces** | The UI should never mislead. States, affordances, and feedback must be truthful. |

---

## Key Specifications at a Glance

| Foundation | Key Value |
|---|---|
| Primary color | `#1E3A5F` (Blue) |
| Accent color | `#F59E0B` (Amber) |
| Neutral scale | 11 steps (50--950) |
| Sans-serif typeface | Inter |
| Monospace typeface | JetBrains Mono |
| Type scale levels | 12 (display-2xl through code) |
| Grid columns | 12 |
| Spacing base unit | 8px |
| Breakpoints | 375px, 768px, 1024px, 1440px |
| Accessibility target | WCAG 2.1 AA minimum |

---

## Versioning and Updates

This design system follows semantic versioning:

- **Major** (e.g., 2.0.0) -- Breaking changes to tokens, scales, or component APIs.
- **Minor** (e.g., 1.1.0) -- New tokens, components, or patterns that do not break existing usage.
- **Patch** (e.g., 1.0.1) -- Bug fixes, documentation corrections, accessibility improvements.

All changes are tracked in a changelog at the root of the design system repository. Teams consuming the system should pin to a major version and review minor/patch updates before adoption.

---

## Contributing

1. Open an issue describing the gap or improvement.
2. Reference the relevant design principle that supports the change.
3. Provide before/after examples and accessibility impact analysis.
4. Changes to foundational tokens require review from both design and engineering leads.
