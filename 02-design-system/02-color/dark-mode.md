# Dark Mode

This document defines how the Flavio Fusuma color system adapts for dark mode. Dark mode is not a simple inversion -- it is a deliberate remapping of every color role to maintain readability, hierarchy, and brand identity on dark surfaces.

---

## Design Goals

1. **Reduce eye strain** in low-light environments.
2. **Preserve brand identity** -- primary blue and accent amber remain recognizable.
3. **Maintain contrast compliance** -- all WCAG 2.1 AA requirements are met independently in dark mode.
4. **Support elevation** through surface color rather than shadow.
5. **Minimize energy consumption** on OLED displays.

---

## Palette Mapping

### How Colors Shift

The core principle: in dark mode, lighter shades become the backgrounds and darker shades become the foreground emphasis. The mapping is not a mechanical swap (500 does not become 500 on a dark background). Instead, each role is reassigned to the shade that produces correct contrast.

### Neutral Palette Remapping

| Role | Light Mode Token | Light Hex | Dark Mode Token | Dark Hex |
|---|---|---|---|---|
| Page background | `neutral-50` | `#F9FAFB` | `neutral-900` | `#111827` |
| Card / raised surface | `white` | `#FFFFFF` | `neutral-800` | `#1F2937` |
| Sunken surface | `neutral-100` | `#F3F4F6` | `neutral-950` | `#0B0F19` |
| Subtle border | `neutral-200` | `#E5E7EB` | `neutral-700` | `#374151` |
| Default border | `neutral-300` | `#D1D5DB` | `neutral-600` | `#4B5563` |
| Tertiary text | `neutral-500` | `#6B7280` | `neutral-400` | `#9CA3AF` |
| Secondary text | `neutral-600` | `#4B5563` | `neutral-300` | `#D1D5DB` |
| Primary text | `neutral-800` | `#1F2937` | `neutral-50` | `#F9FAFB` |
| High-emphasis text | `neutral-900` | `#111827` | `white` | `#FFFFFF` |

### Primary Blue Remapping

| Role | Light Mode | Dark Mode | Notes |
|---|---|---|---|
| Primary button background | `primary-500` | `primary-400` | Lighter shade for visibility on dark surfaces |
| Primary button hover | `primary-600` | `primary-300` | Lighter on hover in dark mode |
| Primary button active | `primary-700` | `primary-500` | Returns toward base on press |
| Primary text / link | `primary-500` | `primary-300` | Needs 4.5:1 on dark backgrounds |
| Primary tinted surface | `primary-50` | `primary-900` | Very dark tinted surface |
| Primary border | `primary-200` | `primary-700` | Subtle primary border |

### Accent Amber Remapping

| Role | Light Mode | Dark Mode | Notes |
|---|---|---|---|
| Accent button background | `accent-500` | `accent-400` | Brighter to maintain energy |
| Accent text | `accent-800` | `accent-300` | Lighter for contrast on dark bg |
| Accent tinted surface | `accent-50` | `accent-950` | Very dark warm surface |
| Accent border | `accent-200` | `accent-700` | Muted amber border |

### Semantic Colors Remapping

| Semantic Role | Light Surface | Dark Surface | Light Text | Dark Text |
|---|---|---|---|---|
| Success | `#ECFDF5` | `#052E1C` | `#065F46` | `#6EE7B7` |
| Warning | `#FFFBEB` | `#3D2800` | `#92400E` | `#FCD34D` |
| Error | `#FEF2F2` | `#3B1111` | `#991B1B` | `#FCA5A5` |
| Info | `#EFF6FF` | `#172554` | `#1E40AF` | `#93C5FD` |

---

## Elevation Model

In light mode, elevation is communicated primarily through box shadows. In dark mode, shadows are nearly invisible against dark backgrounds. Instead, elevation is expressed through **surface lightness**: higher elements are lighter.

### Elevation Levels

| Level | Name | Light Mode | Dark Mode Surface | Dark Mode Hex |
|---|---|---|---|---|
| 0 | Base | Page background + no shadow | `neutral-900` | `#111827` |
| 1 | Raised | 1px shadow | `neutral-800` | `#1F2937` |
| 2 | Floating | 4px shadow | `neutral-750` | `#283548` |
| 3 | Overlay | 8px shadow | `neutral-700` | `#374151` |
| 4 | Modal | 16px shadow | `neutral-650` | `#3F4D63` |
| 5 | Top | 24px shadow | `neutral-600` | `#4B5563` |

Each elevation level adds approximately 4-6% lightness to the surface. This creates a subtle but perceptible stacking order.

### Elevation CSS Implementation

```css
[data-theme="dark"] {
  --surface-base: #111827;
  --surface-raised: #1F2937;
  --surface-floating: #283548;
  --surface-overlay: #374151;
  --surface-modal: #3F4D63;
  --surface-top: #4B5563;
}

/* Component usage */
.card {
  background: var(--surface-raised);
}

.dropdown-menu {
  background: var(--surface-floating);
}

.modal {
  background: var(--surface-overlay);
}

.toast {
  background: var(--surface-modal);
}
```

### Shadow Adjustments

Shadows in dark mode shift from transparent gray to transparent black, and opacity increases to remain barely perceptible:

```css
[data-theme="light"] {
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.07);
  --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);
}

[data-theme="dark"] {
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.4);
  --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.5);
}
```

---

## Surface Colors

### Background Surfaces

| Surface | Light Mode | Dark Mode | Usage |
|---|---|---|---|
| `color-surface-base` | `#F9FAFB` | `#111827` | Page-level background |
| `color-surface-raised` | `#FFFFFF` | `#1F2937` | Cards, panels, sidebars |
| `color-surface-sunken` | `#F3F4F6` | `#0B0F19` | Inset wells, code blocks |
| `color-surface-overlay` | `rgba(17,24,39,0.5)` | `rgba(0,0,0,0.6)` | Backdrop behind modals |
| `color-surface-primary` | `#EBF0F5` | `#0A1523` | Primary-tinted sections |
| `color-surface-accent` | `#FFFBEB` | `#3D2800` | Accent-tinted sections |

### Input Surfaces

| Surface | Light Mode | Dark Mode |
|---|---|---|
| Input background (default) | `#FFFFFF` | `#1F2937` |
| Input background (disabled) | `#F3F4F6` | `#111827` |
| Input background (focused) | `#FFFFFF` | `#1F2937` |
| Input border (default) | `#D1D5DB` | `#4B5563` |
| Input border (focused) | `#1E3A5F` | `#5178A0` |
| Input border (error) | `#EF4444` | `#FCA5A5` |

---

## Component Adjustments

### Buttons

| Variant | Property | Light Mode | Dark Mode |
|---|---|---|---|
| Primary | Background | `primary-500` | `primary-400` |
| Primary | Text | `white` | `neutral-900` |
| Primary | Hover bg | `primary-600` | `primary-300` |
| Secondary | Background | `white` | `neutral-800` |
| Secondary | Border | `neutral-300` | `neutral-600` |
| Secondary | Text | `neutral-700` | `neutral-200` |
| Ghost | Background | `transparent` | `transparent` |
| Ghost | Text | `primary-500` | `primary-300` |
| Ghost | Hover bg | `primary-50` | `primary-900` |
| Destructive | Background | `error-default` | `#DC2626` |
| Destructive | Text | `white` | `white` |

### Cards

```css
[data-theme="dark"] .card {
  background: var(--surface-raised);
  border: 1px solid var(--color-border-default);
  /* No box-shadow -- elevation handled by surface color */
}
```

### Badges and Tags

Badges shift to lower-saturation backgrounds in dark mode to avoid visual heaviness:

| Badge Type | Light Background | Dark Background | Light Text | Dark Text |
|---|---|---|---|---|
| Success | `#ECFDF5` | `#052E1C` | `#065F46` | `#6EE7B7` |
| Warning | `#FFFBEB` | `#3D2800` | `#92400E` | `#FCD34D` |
| Error | `#FEF2F2` | `#3B1111` | `#991B1B` | `#FCA5A5` |
| Info | `#EFF6FF` | `#172554` | `#1E40AF` | `#93C5FD` |
| Neutral | `#F3F4F6` | `#374151` | `#374151` | `#D1D5DB` |

### Dividers and Borders

Borders become lighter (higher neutral step) in dark mode but remain subtle:

- Default border: `neutral-200` (light) to `neutral-700` (dark)
- Strong border: `neutral-400` (light) to `neutral-500` (dark)
- Subtle divider: `neutral-150` (light) to `neutral-800` (dark)

---

## Implementation Approach

### Strategy: CSS Custom Properties with Data Attribute

The recommended approach uses CSS custom properties scoped to a `data-theme` attribute on the `<html>` element. This provides instant switching without page reload.

```css
/* Base (light mode) tokens */
:root,
[data-theme="light"] {
  --color-text-primary: #1F2937;
  --color-text-secondary: #4B5563;
  --color-text-tertiary: #6B7280;
  --color-surface-base: #F9FAFB;
  --color-surface-raised: #FFFFFF;
  --color-border-default: #D1D5DB;
  --color-interactive-default: #1E3A5F;
  --color-interactive-hover: #1A3353;
}

/* Dark mode tokens */
[data-theme="dark"] {
  --color-text-primary: #F9FAFB;
  --color-text-secondary: #D1D5DB;
  --color-text-tertiary: #9CA3AF;
  --color-surface-base: #111827;
  --color-surface-raised: #1F2937;
  --color-border-default: #4B5563;
  --color-interactive-default: #5178A0;
  --color-interactive-hover: #85A2BF;
}
```

### Respecting System Preferences

Use `prefers-color-scheme` as the default, allow user override, and persist the choice:

```css
/* System default when no data-theme is set */
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --color-text-primary: #F9FAFB;
    --color-surface-base: #111827;
    /* ... all dark mode tokens ... */
  }
}
```

```javascript
// Theme switcher logic
function setTheme(theme) {
  if (theme === 'system') {
    document.documentElement.removeAttribute('data-theme');
  } else {
    document.documentElement.setAttribute('data-theme', theme);
  }
  localStorage.setItem('theme-preference', theme);
}

// On page load
const saved = localStorage.getItem('theme-preference');
if (saved && saved !== 'system') {
  document.documentElement.setAttribute('data-theme', saved);
}
```

### Preventing Flash of Wrong Theme

Add a blocking script in `<head>` before any CSS loads:

```html
<script>
  (function() {
    var saved = localStorage.getItem('theme-preference');
    if (saved === 'dark') {
      document.documentElement.setAttribute('data-theme', 'dark');
    } else if (saved === 'light') {
      document.documentElement.setAttribute('data-theme', 'light');
    }
  })();
</script>
```

### Images and Media

- Provide dark-mode variants for illustrations and diagrams where backgrounds are visible.
- Use `<picture>` with `prefers-color-scheme` media queries for automatic switching.
- Apply subtle transparency reductions to images on dark backgrounds to prevent glare.

```html
<picture>
  <source srcset="hero-dark.webp" media="(prefers-color-scheme: dark)">
  <img src="hero-light.webp" alt="Hero illustration">
</picture>
```

### Testing Checklist

- [ ] All text meets 4.5:1 contrast on dark surfaces.
- [ ] Large text (24px+) meets 3:1 contrast.
- [ ] UI components (borders, icons) meet 3:1 contrast.
- [ ] Focus indicators are visible on all dark surfaces.
- [ ] Semantic colors (success, warning, error, info) are distinguishable.
- [ ] Elevation hierarchy is perceptible across all surface levels.
- [ ] No pure black (`#000000`) is used for surfaces (causes halation on OLED).
- [ ] No pure white (`#FFFFFF`) text on pure black backgrounds (use `neutral-50` on `neutral-900`).
- [ ] Images and illustrations adapt or remain legible.
- [ ] Switching between themes does not flash the wrong theme on reload.
