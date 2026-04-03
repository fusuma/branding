# Flavio Fusuma -- Design Tokens

## Token Architecture

This token system follows the **W3C Design Tokens Community Group (DTCG)** specification
and is organized into three layers:

```
global/          Primitive, raw values (colors, sizes, font stacks)
  |
semantic/        Purpose-driven aliases that reference globals
  |
themes/          Theme overrides (light / dark) that re-map semantic tokens
```

### Layer Descriptions

| Layer | Purpose | Example |
|-------|---------|---------|
| **Global** | Platform-agnostic primitives. Never used directly in components. | `color.blue.800` = `#1E3A5F` |
| **Semantic** | Meaningful aliases consumed by designers and engineers. | `color.interactive.primary` = `{color.blue.800}` |
| **Theme** | Light and dark overrides that swap semantic mappings. | `color.background.primary` changes between themes |

### File Inventory

#### Global Tokens (`global/`)

| File | Contents |
|------|----------|
| `color.tokens.json` | Full color palette -- primary (blue), accent (amber), neutrals, semantic status colors (green, red), extended palette (teal, indigo, rose, violet, emerald, cyan) |
| `typography.tokens.json` | Font families (Inter, JetBrains Mono), sizes, weights, line heights, letter spacing, paragraph spacing |
| `spacing.tokens.json` | Spacing scale based on 4 px sub-grid with 8 px base unit |
| `border.tokens.json` | Border radii (4, 6, 8, 12, 16, 9999) and border widths |
| `shadow.tokens.json` | Five elevation levels plus `none` |
| `motion.tokens.json` | Durations (instant through deliberate) and easing curves |
| `opacity.tokens.json` | Opacity scale from 0 to 100 in useful increments |

#### Semantic Tokens (`semantic/`)

| File | Contents |
|------|----------|
| `color.tokens.json` | Purpose-driven color aliases -- background, text, border, icon, interactive |
| `typography.tokens.json` | Type roles -- display, heading, body, label, caption, code, overline |
| `component.tokens.json` | Component-level tokens for button, input, card, badge, alert, avatar, toggle, tooltip |

#### Theme Tokens (`themes/`)

| File | Contents |
|------|----------|
| `light.tokens.json` | Default light theme -- maps semantic tokens to light-appropriate global values |
| `dark.tokens.json` | Dark theme -- inverts surface and text mappings for dark mode |

### Build Configuration

`style-dictionary.config.json` drives **Style Dictionary v4** and outputs:

- CSS custom properties
- SCSS variables and maps
- JavaScript ES modules
- JSON (flat)
- TypeScript declarations
- iOS Swift enums
- Android XML resources

### Token Naming Convention

Tokens follow a structured path:

```
{category}.{group}.{item}.{variant}.{state}
```

Examples:

```
color.blue.500
typography.fontSize.lg
spacing.6
shadow.elevation-3
color.interactive.primary-hover
component.button.primary.background
```

### Referencing Tokens

Cross-reference tokens via the `{token.path}` syntax:

```json
{
  "component": {
    "button": {
      "primary": {
        "background": {
          "$value": "{color.interactive.primary}",
          "$type": "color"
        }
      }
    }
  }
}
```

### Color System

| Role       | Key Swatch | Hex       |
|------------|-----------|-----------|
| Primary    | blue-800  | `#1E3A5F` |
| Accent     | amber-500 | `#F59E0B` |
| Success    | green-500 | `#22C55E` |
| Warning    | amber-500 | `#F59E0B` |
| Error      | red-500   | `#EF4444` |
| Info       | blue-500  | `#3B82F6` |

Extended palette: teal, indigo, rose, violet, emerald, cyan.

### Typography

- **Sans-serif:** Inter
- **Monospace:** JetBrains Mono

### Spacing

Based on a 4 px sub-grid with an 8 px base unit. Scale multipliers: 0, 1, 2, 3, 4, 5, 6, 8, 10, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96.

### Building

```bash
npx style-dictionary build --config 03-design-tokens/style-dictionary.config.json
```
