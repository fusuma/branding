# Design Tokens Setup in Figma

> Configuration guide for the Figma Tokens plugin (Tokens Studio), variable collections, token structure, mode configuration, and sync workflows for the Flavio Fusuma Design System.

---

## Token Architecture Overview

The Flavio Fusuma token system uses a three-tier architecture that maps directly to Figma's variable collections.

```
┌─────────────────────────────────────┐
│          Component Tokens           │  button-primary-bg, input-border-default
│    (references semantic tokens)     │
├─────────────────────────────────────┤
│          Semantic Tokens            │  color-bg-primary, color-border-default
│    (references global tokens)       │
├─────────────────────────────────────┤
│          Global / Primitive         │  blue-600, neutral-300, space-4
│       Tokens (raw values)           │
└─────────────────────────────────────┘
```

### Tier Definitions

| Tier | Purpose | Example Token | Resolves To |
|---|---|---|---|
| **Global / Primitive** | Raw, context-free values. Color palette, spacing scale, type scale, radii, shadows. | `blue-600` | `#2563EB` |
| **Semantic** | Contextual meaning. Maps primitives to roles (background, text, border, etc.) | `color-bg-primary` | `{blue-600}` |
| **Component** | Per-component overrides. Only created when a component needs values that differ from the semantic default. | `button-primary-bg` | `{color-bg-primary}` |

---

## Figma Variable Collections

Figma variables (native, not plugin) are organized into collections. Each collection maps to one token tier.

### Collection 1: Primitives

Contains raw values with no semantic meaning. These never change between modes.

| Group | Token Examples | Value Type |
|---|---|---|
| `color/blue` | `blue-50` through `blue-950` | Color |
| `color/neutral` | `neutral-50` through `neutral-950` | Color |
| `color/red` | `red-50` through `red-950` | Color |
| `color/green` | `green-50` through `green-950` | Color |
| `color/amber` | `amber-50` through `amber-950` | Color |
| `color/sky` | `sky-50` through `sky-950` | Color |
| `color/brand` | `brand-navy` (#1E3A5F), `brand-blue` (#2563EB), `brand-amber` (#F59E0B) | Color |
| `color/static` | `white` (#FFFFFF), `black` (#000000), `transparent` | Color |
| `space` | `space-0.5` (4px) through `space-24` (192px) | Number |
| `radius` | `radius-none` (0) through `radius-full` (9999px) | Number |
| `font-size` | `font-size-xs` (12px) through `font-size-4xl` (36px) | Number |
| `line-height` | `line-height-tight` (1.25) through `line-height-relaxed` (1.75) | Number |
| `font-weight` | `font-weight-regular` (400) through `font-weight-bold` (700) | Number |
| `shadow` | `shadow-sm` through `shadow-2xl` | Shadow (effect variable) |
| `opacity` | `opacity-disabled` (0.4), `opacity-overlay` (0.5) | Number |

### Collection 2: Themes (Semantic)

Maps primitives to semantic roles. This collection has two modes: Light and Dark.

| Group | Token | Light Mode Value | Dark Mode Value |
|---|---|---|---|
| **Background** | `color-bg-primary` | `{white}` | `{neutral-950}` |
| | `color-bg-secondary` | `{neutral-50}` | `{neutral-900}` |
| | `color-bg-tertiary` | `{neutral-100}` | `{neutral-800}` |
| | `color-bg-inverse` | `{neutral-900}` | `{white}` |
| | `color-bg-brand` | `{blue-600}` | `{blue-500}` |
| | `color-bg-brand-subtle` | `{blue-50}` | `{blue-950}` |
| | `color-bg-accent` | `{amber-500}` | `{amber-400}` |
| | `color-bg-accent-subtle` | `{amber-50}` | `{amber-950}` |
| | `color-bg-success` | `{green-50}` | `{green-950}` |
| | `color-bg-warning` | `{amber-50}` | `{amber-950}` |
| | `color-bg-error` | `{red-50}` | `{red-950}` |
| | `color-bg-info` | `{sky-50}` | `{sky-950}` |
| **Text** | `color-text-primary` | `{neutral-900}` | `{neutral-50}` |
| | `color-text-secondary` | `{neutral-600}` | `{neutral-400}` |
| | `color-text-tertiary` | `{neutral-500}` | `{neutral-500}` |
| | `color-text-inverse` | `{white}` | `{neutral-900}` |
| | `color-text-brand` | `{blue-600}` | `{blue-400}` |
| | `color-text-accent` | `{amber-600}` | `{amber-400}` |
| | `color-text-on-brand` | `{white}` | `{white}` |
| | `color-text-on-accent` | `{neutral-900}` | `{neutral-900}` |
| | `color-text-success` | `{green-700}` | `{green-400}` |
| | `color-text-warning` | `{amber-700}` | `{amber-400}` |
| | `color-text-error` | `{red-600}` | `{red-400}` |
| | `color-text-link` | `{blue-600}` | `{blue-400}` |
| | `color-text-disabled` | `{neutral-400}` | `{neutral-600}` |
| **Border** | `color-border-default` | `{neutral-300}` | `{neutral-700}` |
| | `color-border-strong` | `{neutral-400}` | `{neutral-600}` |
| | `color-border-brand` | `{blue-600}` | `{blue-500}` |
| | `color-border-error` | `{red-500}` | `{red-400}` |
| | `color-border-success` | `{green-500}` | `{green-400}` |
| | `color-border-focus` | `{blue-600}` | `{blue-400}` |
| **Surface** | `color-surface-primary` | `{white}` | `{neutral-900}` |
| | `color-surface-elevated` | `{white}` | `{neutral-800}` |
| | `color-surface-overlay` | `{black}` at 50% | `{black}` at 60% |
| **Interactive** | `color-interactive-default` | `{blue-600}` | `{blue-500}` |
| | `color-interactive-hover` | `{blue-700}` | `{blue-400}` |
| | `color-interactive-active` | `{blue-800}` | `{blue-300}` |
| | `color-interactive-disabled` | `{neutral-300}` | `{neutral-700}` |

### Collection 3: Components

Per-component token overrides. Only populated when the component value differs from the semantic default. Most component tokens simply alias semantic tokens.

| Component | Token | Light Value | Dark Value |
|---|---|---|---|
| **Button (Primary)** | `button-primary-bg` | `{color-bg-brand}` | `{color-bg-brand}` |
| | `button-primary-text` | `{color-text-on-brand}` | `{color-text-on-brand}` |
| | `button-primary-bg-hover` | `{color-interactive-hover}` | `{color-interactive-hover}` |
| | `button-primary-bg-active` | `{color-interactive-active}` | `{color-interactive-active}` |
| | `button-primary-bg-disabled` | `{color-interactive-disabled}` | `{color-interactive-disabled}` |
| **Button (Secondary)** | `button-secondary-bg` | `{color-bg-tertiary}` | `{color-bg-tertiary}` |
| | `button-secondary-text` | `{color-text-primary}` | `{color-text-primary}` |
| **Input** | `input-bg` | `{color-bg-primary}` | `{color-bg-secondary}` |
| | `input-border` | `{color-border-default}` | `{color-border-default}` |
| | `input-border-hover` | `{color-border-strong}` | `{color-border-strong}` |
| | `input-border-focus` | `{color-border-focus}` | `{color-border-focus}` |
| | `input-border-error` | `{color-border-error}` | `{color-border-error}` |
| | `input-text` | `{color-text-primary}` | `{color-text-primary}` |
| | `input-placeholder` | `{color-text-tertiary}` | `{color-text-tertiary}` |
| **Card** | `card-bg` | `{color-surface-primary}` | `{color-surface-elevated}` |
| | `card-border` | `{color-border-default}` | `{color-border-default}` |
| | `card-shadow` | `{shadow-sm}` | `{shadow-none}` |
| **Nav** | `nav-bg` | `{color-bg-primary}` | `{color-bg-primary}` |
| | `nav-border` | `{color-border-default}` | `{color-border-default}` |
| | `nav-link-text` | `{color-text-secondary}` | `{color-text-secondary}` |
| | `nav-link-text-active` | `{color-text-brand}` | `{color-text-brand}` |

---

## Mode Configuration

### Modes in Figma Variables

Each variable collection can have multiple modes. The Flavio Fusuma system uses modes at the Themes (semantic) level.

| Collection | Mode 1 | Mode 2 | Notes |
|---|---|---|---|
| Primitives | (single mode) | -- | Raw values do not change |
| Themes | Light | Dark | All semantic tokens resolve differently |
| Components | (inherits from Themes) | -- | References theme tokens, so mode switches automatically |

### Applying Modes in Figma

1. Select the top-level frame (e.g., `Homepage / Desktop Wide (1440)`).
2. In the right panel under "Layer" section, find "Variable modes."
3. Set the Themes collection to "Light" or "Dark."
4. All child layers referencing theme variables update automatically.

### Side-by-Side Theme Preview

To show light and dark side by side:

1. Duplicate the template frame.
2. Set one to Light mode, the other to Dark mode.
3. Name them: `Homepage / Desktop Wide (1440) / Light` and `Homepage / Desktop Wide (1440) / Dark`.

---

## Tokens Studio (Figma Tokens Plugin) Configuration

If using Tokens Studio for advanced token management and code sync, configure the plugin as follows.

### Token Set Structure

```
tokens/
├── global/
│   ├── colors.json          # All color primitives
│   ├── spacing.json         # 8px scale
│   ├── typography.json      # Font sizes, weights, line heights
│   ├── radii.json           # Border radii
│   ├── shadows.json         # Elevation shadows
│   └── opacity.json         # Opacity values
├── semantic/
│   ├── light.json           # Light theme semantic mappings
│   └── dark.json            # Dark theme semantic mappings
└── component/
    ├── button.json           # Button-specific tokens
    ├── input.json            # Input-specific tokens
    ├── card.json             # Card-specific tokens
    └── nav.json              # Navigation-specific tokens
```

### Token JSON Format

Tokens Studio uses a specific JSON structure. All references use `{}` notation.

```json
{
  "color": {
    "blue": {
      "50":  { "value": "#EFF6FF", "type": "color" },
      "100": { "value": "#DBEAFE", "type": "color" },
      "200": { "value": "#BFDBFE", "type": "color" },
      "300": { "value": "#93C5FD", "type": "color" },
      "400": { "value": "#60A5FA", "type": "color" },
      "500": { "value": "#3B82F6", "type": "color" },
      "600": { "value": "#2563EB", "type": "color" },
      "700": { "value": "#1D4ED8", "type": "color" },
      "800": { "value": "#1E3A5F", "type": "color" },
      "900": { "value": "#1E3A8A", "type": "color" },
      "950": { "value": "#172554", "type": "color" }
    }
  }
}
```

Semantic token referencing a primitive:

```json
{
  "color": {
    "bg": {
      "brand": {
        "value": "{color.blue.600}",
        "type": "color",
        "description": "Primary brand background color"
      }
    }
  }
}
```

### Naming: Figma Variables vs. JSON Tokens

| Figma Variable Name | JSON Token Path | CSS Custom Property |
|---|---|---|
| `color/blue/600` | `color.blue.600` | `--ff-color-blue-600` |
| `color/bg/primary` | `color.bg.primary` | `--ff-color-bg-primary` |
| `color/text/brand` | `color.text.brand` | `--ff-color-text-brand` |
| `space/4` | `space.4` | `--ff-space-4` |
| `radius/md` | `radius.md` | `--ff-radius-md` |
| `shadow/sm` | `shadow.sm` | `--ff-shadow-sm` |
| `button/primary/bg` | `component.button.primary.bg` | `--ff-button-primary-bg` |

Convention: Figma uses `/` as the group delimiter. JSON uses `.` (dot notation). CSS uses `-` (kebab-case) with the `--ff-` prefix.

---

## Sync Workflow

### Direction: Tokens to Figma

This is the primary direction. Tokens are the source of truth; Figma consumes them.

```
1. Engineer or design system lead updates token JSON files
   (in Git repository under 03-design-tokens/)

2. Tokens Studio plugin syncs from Git (or local file)
   Plugin > Settings > Sync > Git provider (GitHub)
   Repository: [org]/flavio-fusuma-tokens
   Branch: main
   File path: tokens/

3. Plugin reads JSON, creates/updates Figma variables
   - New tokens create new variables
   - Changed values update existing variables
   - Deleted tokens flag for manual removal

4. Designer reviews changes in Figma
   - Verify visual correctness
   - Check light/dark mode rendering
   - Validate component appearance

5. Designer publishes updated library
   Figma menu > Libraries > Publish changes
```

### Direction: Figma to Tokens (Secondary)

When designers need to prototype a new token before committing to code:

```
1. Designer creates a new variable in Figma
   (clearly named, with description)

2. Export via Tokens Studio
   Plugin > Export > JSON

3. Engineer reviews exported JSON
   - Validates naming convention
   - Ensures it fits the tier architecture
   - Adds to the correct token set file

4. Engineer commits to Git
   PR with token changes for review

5. CI pipeline generates CSS/SCSS/JS output
   from the token JSON (using Style Dictionary or similar)
```

### Conflict Resolution

| Scenario | Resolution |
|---|---|
| Token exists in JSON but not in Figma | Plugin creates the Figma variable on next sync |
| Token exists in Figma but not in JSON | Flag for review; likely a local experiment that should be formalized or removed |
| Values differ between JSON and Figma | JSON wins (source of truth). Designer re-syncs to pull the canonical value. |
| Token renamed in JSON | Old Figma variable is orphaned; manually delete and re-link usages |

---

## Variable Scoping

Figma allows scoping variables to specific property types. Configure scoping to prevent misuse.

| Variable Group | Scoped To |
|---|---|
| `color/bg/*` | Fill color |
| `color/text/*` | Text color |
| `color/border/*` | Stroke color |
| `space/*` | Gap, padding, width, height |
| `radius/*` | Corner radius |
| `shadow/*` | Drop shadow, inner shadow |
| `opacity/*` | Layer opacity |
| `font-size/*` | Font size |

This ensures that when a designer selects a fill color, only background color tokens appear in the variable picker -- not text or border colors.

---

## Audit and Validation Checklist

Run this checklist quarterly or after major token updates:

- [ ] All Figma variables resolve correctly (no broken references)
- [ ] Light and dark modes render as expected for all semantic tokens
- [ ] No raw hex values used anywhere; all fills, strokes, and text colors reference variables
- [ ] All spacing values reference `space/*` variables
- [ ] All corner radii reference `radius/*` variables
- [ ] Component tokens correctly alias semantic tokens (not primitives directly)
- [ ] JSON token files and Figma variables are in sync (run diff via plugin)
- [ ] Token descriptions are populated for all semantic and component tokens
- [ ] Variable scoping is configured correctly for each group
- [ ] Published library is up to date with latest variable values
