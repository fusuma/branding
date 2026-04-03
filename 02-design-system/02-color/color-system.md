# Color System

The Flavio Fusuma color system is built on a primary blue, an accent amber, and an 11-step neutral scale. Every color has a defined role, and every combination has been validated for WCAG 2.1 AA contrast compliance.

---

## Color Palette

### Primary -- Blue

The primary blue palette anchors the brand identity. It is used for primary actions, key UI elements, and brand-forward surfaces.

| Token | Hex | RGB | Usage |
|---|---|---|---|
| `color-primary-50` | `#EBF0F5` | 235, 240, 245 | Tinted backgrounds, hover states on light surfaces |
| `color-primary-100` | `#C9D6E3` | 201, 214, 227 | Light fills, selected row backgrounds |
| `color-primary-200` | `#A7BCD1` | 167, 188, 209 | Borders on primary elements, secondary indicators |
| `color-primary-300` | `#85A2BF` | 133, 162, 191 | Placeholder text on dark surfaces |
| `color-primary-400` | `#5178A0` | 81, 120, 160 | Icons paired with primary text |
| `color-primary-500` | `#1E3A5F` | 30, 58, 95 | **Base primary** -- buttons, links, active states |
| `color-primary-600` | `#1A3353` | 26, 51, 83 | Hover state for primary buttons |
| `color-primary-700` | `#162C47` | 22, 44, 71 | Active/pressed state for primary buttons |
| `color-primary-800` | `#0F1F33` | 15, 31, 51 | High-contrast text on light backgrounds |
| `color-primary-900` | `#0A1523` | 10, 21, 35 | Near-black primary for maximum contrast |
| `color-primary-950` | `#060D16` | 6, 13, 22 | Darkest primary, used sparingly |

### Accent -- Amber

Amber provides energy and draws attention. It is reserved for calls to action that need to stand out from the primary palette, status indicators, and highlights.

| Token | Hex | RGB | Usage |
|---|---|---|---|
| `color-accent-50` | `#FFFBEB` | 255, 251, 235 | Subtle highlight backgrounds |
| `color-accent-100` | `#FEF3C7` | 254, 243, 199 | Warning surface backgrounds |
| `color-accent-200` | `#FDE68A` | 253, 230, 138 | Highlight fill |
| `color-accent-300` | `#FCD34D` | 252, 211, 77 | Badge backgrounds, progress indicators |
| `color-accent-400` | `#FBBF24` | 251, 191, 36 | Icons, secondary CTAs |
| `color-accent-500` | `#F59E0B` | 245, 158, 11 | **Base accent** -- featured CTAs, highlights |
| `color-accent-600` | `#D97706` | 217, 119, 6 | Hover on accent elements |
| `color-accent-700` | `#B45309` | 180, 83, 9 | Active/pressed on accent elements |
| `color-accent-800` | `#92400E` | 146, 64, 14 | Accent text on light backgrounds |
| `color-accent-900` | `#78350F` | 120, 53, 15 | High-contrast accent text |
| `color-accent-950` | `#5C2A0A` | 92, 42, 10 | Darkest accent |

### Neutrals

The neutral scale provides text colors, backgrounds, borders, and subtle UI surfaces. It is intentionally large (11 steps) to handle the full range from white-adjacent to near-black.

| Token | Hex | RGB | Usage |
|---|---|---|---|
| `color-neutral-50` | `#F9FAFB` | 249, 250, 251 | Page backgrounds, card backgrounds (light mode) |
| `color-neutral-100` | `#F3F4F6` | 243, 244, 246 | Alternate row backgrounds, input backgrounds |
| `color-neutral-150` | `#EBEDF0` | 235, 237, 240 | Divider lines, subtle borders |
| `color-neutral-200` | `#E5E7EB` | 229, 231, 235 | Borders, separators |
| `color-neutral-300` | `#D1D5DB` | 209, 213, 219 | Disabled text, placeholder text |
| `color-neutral-400` | `#9CA3AF` | 156, 163, 175 | Secondary icons, muted text |
| `color-neutral-500` | `#6B7280` | 107, 114, 128 | Body text (secondary), captions |
| `color-neutral-600` | `#4B5563` | 75, 85, 99 | Body text (primary on light backgrounds) |
| `color-neutral-700` | `#374151` | 55, 65, 81 | Headings on light backgrounds |
| `color-neutral-800` | `#1F2937` | 31, 41, 55 | High-emphasis text on light backgrounds |
| `color-neutral-900` | `#111827` | 17, 24, 39 | Maximum contrast text, near-black |

### Semantic Colors

Semantic colors communicate status. Each semantic color has a surface (background), default (icon/border), and emphasis (text) variant.

| Role | Surface | Default | Emphasis | Usage |
|---|---|---|---|---|
| **Success** | `#ECFDF5` | `#10B981` | `#065F46` | Confirmations, positive indicators |
| **Warning** | `#FFFBEB` | `#F59E0B` | `#92400E` | Caution states, non-blocking issues |
| **Error** | `#FEF2F2` | `#EF4444` | `#991B1B` | Validation errors, destructive actions |
| **Info** | `#EFF6FF` | `#3B82F6` | `#1E40AF` | Informational banners, tips |

Semantic color tokens:

```
color-success-surface, color-success-default, color-success-emphasis
color-warning-surface, color-warning-default, color-warning-emphasis
color-error-surface,   color-error-default,   color-error-emphasis
color-info-surface,    color-info-default,     color-info-emphasis
```

---

## Color Roles

Every color in the system has a defined role. Using a color outside its role breaks the visual language and confuses users.

### Surfaces

Surfaces are background colors. They establish visual hierarchy through layering.

| Token | Role | Example |
|---|---|---|
| `color-surface-base` | Page background | `neutral-50` in light mode |
| `color-surface-raised` | Cards, modals, popovers | `white` in light mode |
| `color-surface-overlay` | Overlays, backdrops | `neutral-900` at 50% opacity |
| `color-surface-sunken` | Inset areas, wells | `neutral-100` in light mode |
| `color-surface-primary` | Primary-tinted surfaces | `primary-50` |
| `color-surface-accent` | Accent-tinted surfaces | `accent-50` |

### Text

| Token | Role | Contrast Minimum |
|---|---|---|
| `color-text-primary` | Headings, high-emphasis text | 7:1 (AAA preferred) |
| `color-text-secondary` | Body text, descriptions | 4.5:1 (AA required) |
| `color-text-tertiary` | Captions, placeholders | 4.5:1 (AA required) |
| `color-text-disabled` | Disabled labels | 3:1 (WCAG 1.4.11) |
| `color-text-inverse` | Text on dark/primary surfaces | 4.5:1 (AA required) |
| `color-text-link` | Hyperlinks | 4.5:1 (AA required) |
| `color-text-on-primary` | Text on `color-primary-500` bg | 4.5:1 (AA required) |
| `color-text-on-accent` | Text on `color-accent-500` bg | 4.5:1 (AA required) |

### Borders

| Token | Role |
|---|---|
| `color-border-default` | Standard borders (inputs, cards) |
| `color-border-strong` | Emphasized borders (focused inputs) |
| `color-border-subtle` | Dividers, separators |
| `color-border-disabled` | Disabled element borders |

### Interactive

| Token | Role |
|---|---|
| `color-interactive-default` | Default state of interactive elements |
| `color-interactive-hover` | Hover state |
| `color-interactive-active` | Pressed/active state |
| `color-interactive-focus` | Focus ring color |
| `color-interactive-disabled` | Disabled interactive elements |

---

## Combining Colors

### Allowed Combinations

Not every palette color can be combined freely. The following table defines sanctioned pairings.

| Background | Allowed Foregrounds | Notes |
|---|---|---|
| `neutral-50` (page bg) | `neutral-600` through `neutral-900`, `primary-500`+ | Standard light-mode reading |
| `neutral-100` (card bg) | `neutral-600` through `neutral-900`, `primary-500`+ | Slightly elevated surface |
| `white` | `neutral-600` through `neutral-900`, `primary-500`+ | Cards, modals |
| `primary-500` | `white`, `neutral-50`, `accent-300`+ | Buttons, banners |
| `primary-800`+ | `white`, `neutral-50`, `neutral-100` | Dark headers, footers |
| `accent-500` | `neutral-800`+, `primary-800`+ | Accent buttons (use dark text) |
| `accent-50` | `accent-800`+, `neutral-700`+ | Warning/highlight surfaces |
| Semantic surfaces | Corresponding emphasis color, `neutral-700`+ | Status banners |

### Forbidden Combinations

These combinations fail contrast requirements or create visual confusion:

- **Accent-500 text on primary-500 background** -- insufficient contrast and color vibration.
- **Neutral-400 text on neutral-50 background** -- fails AA contrast (3.04:1).
- **Primary-300 text on white** -- fails AA contrast.
- **Accent-300 on white** -- fails AA contrast for text.
- **Red text on green background (or vice versa)** -- inaccessible to color-blind users.

---

## Usage Guidelines

### Brand Expression

- Use `primary-500` as the dominant brand color on marketing surfaces (hero sections, CTAs, navigation).
- Use accent amber sparingly: it should draw the eye, not dominate. A good ratio is 80% primary to 20% accent on any given surface.
- Neutrals carry the majority of the interface. Most product UI should be 70%+ neutral.

### Data Visualization

For charts and graphs, use a dedicated data visualization palette that provides maximum perceptual distance between values:

| Data Series | Token | Hex |
|---|---|---|
| Series 1 | `color-data-1` | `#1E3A5F` (primary-500) |
| Series 2 | `color-data-2` | `#F59E0B` (accent-500) |
| Series 3 | `color-data-3` | `#10B981` (success) |
| Series 4 | `color-data-4` | `#8B5CF6` (purple) |
| Series 5 | `color-data-5` | `#EC4899` (pink) |
| Series 6 | `color-data-6` | `#06B6D4` (cyan) |

Always supplement color with pattern, shape, or label for accessibility.

### Color and Meaning

Never use color as the sole indicator of meaning. Pair colors with:

- **Icons** -- a checkmark with green, an X with red.
- **Text labels** -- "Success", "Error", "Warning".
- **Patterns** -- hatching, borders, or shape differences in charts.

---

## Accessibility Considerations

### Contrast Requirements

| Content Type | Minimum Ratio | WCAG Criterion |
|---|---|---|
| Normal text (< 24px / < 18.66px bold) | 4.5:1 | 1.4.3 AA |
| Large text (>= 24px / >= 18.66px bold) | 3:1 | 1.4.3 AA |
| UI components and graphical objects | 3:1 | 1.4.11 AA |
| Enhanced contrast (AAA) | 7:1 / 4.5:1 | 1.4.6 AAA |

### Testing

- Use the contrast matrices in `contrast-ratios.md` to validate every combination.
- Test with simulated color vision deficiencies: protanopia, deuteranopia, tritanopia, achromatopsia.
- Verify dark mode contrast separately -- see `dark-mode.md`.

### Focus Indicators

Focus indicators use `color-interactive-focus` (mapped to `primary-400` in light mode) with a 2px solid outline offset by 2px. This provides:

- 3:1 contrast against adjacent colors (WCAG 2.4.7 AA).
- Clear visibility on both light and dark surfaces.
- Consistent appearance across all interactive elements.

---

## Implementation

### CSS Custom Properties

```css
:root {
  /* Primary */
  --color-primary-50: #EBF0F5;
  --color-primary-100: #C9D6E3;
  --color-primary-200: #A7BCD1;
  --color-primary-300: #85A2BF;
  --color-primary-400: #5178A0;
  --color-primary-500: #1E3A5F;
  --color-primary-600: #1A3353;
  --color-primary-700: #162C47;
  --color-primary-800: #0F1F33;
  --color-primary-900: #0A1523;
  --color-primary-950: #060D16;

  /* Accent */
  --color-accent-50: #FFFBEB;
  --color-accent-100: #FEF3C7;
  --color-accent-200: #FDE68A;
  --color-accent-300: #FCD34D;
  --color-accent-400: #FBBF24;
  --color-accent-500: #F59E0B;
  --color-accent-600: #D97706;
  --color-accent-700: #B45309;
  --color-accent-800: #92400E;
  --color-accent-900: #78350F;
  --color-accent-950: #5C2A0A;

  /* Neutrals */
  --color-neutral-50: #F9FAFB;
  --color-neutral-100: #F3F4F6;
  --color-neutral-150: #EBEDF0;
  --color-neutral-200: #E5E7EB;
  --color-neutral-300: #D1D5DB;
  --color-neutral-400: #9CA3AF;
  --color-neutral-500: #6B7280;
  --color-neutral-600: #4B5563;
  --color-neutral-700: #374151;
  --color-neutral-800: #1F2937;
  --color-neutral-900: #111827;

  /* Semantic */
  --color-success-surface: #ECFDF5;
  --color-success-default: #10B981;
  --color-success-emphasis: #065F46;

  --color-warning-surface: #FFFBEB;
  --color-warning-default: #F59E0B;
  --color-warning-emphasis: #92400E;

  --color-error-surface: #FEF2F2;
  --color-error-default: #EF4444;
  --color-error-emphasis: #991B1B;

  --color-info-surface: #EFF6FF;
  --color-info-default: #3B82F6;
  --color-info-emphasis: #1E40AF;
}
```

### Using Tokens in Code

Always reference tokens, never raw hex values:

```css
/* Correct */
.button-primary {
  background-color: var(--color-primary-500);
  color: var(--color-text-on-primary);
}

/* Incorrect */
.button-primary {
  background-color: #1E3A5F;
  color: #ffffff;
}
```

### Figma Usage

In Figma, all colors are available as shared styles and variables under the `Flavio Fusuma / Color` library. Use variables (not raw hex values) so that theme switching works automatically.
