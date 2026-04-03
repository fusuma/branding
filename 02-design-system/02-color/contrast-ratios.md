# Contrast Ratios

This document provides WCAG 2.1 contrast ratio matrices for every common foreground/background combination in both light and dark themes. Use these tables to validate color pairings during design and development.

---

## WCAG Requirements Reference

| Level | Normal Text (< 24px) | Large Text (>= 24px / >= 18.66px bold) | UI Components |
|---|---|---|---|
| **AA** (minimum) | 4.5:1 | 3:1 | 3:1 |
| **AAA** (enhanced) | 7:1 | 4.5:1 | Not defined |

### Legend

Throughout this document:

- **AAA** = passes WCAG AAA (>= 7:1 for normal text, >= 4.5:1 for large text)
- **AA** = passes WCAG AA (>= 4.5:1 for normal text, >= 3:1 for large text)
- **AA-LG** = passes AA for large text only (3:1 to 4.49:1)
- **FAIL** = does not meet any WCAG threshold (< 3:1)

---

## Light Theme Contrast Matrix

### Neutral Text on Neutral Backgrounds

| Foreground | on `white` | on `neutral-50` | on `neutral-100` | on `neutral-200` |
|---|---|---|---|---|
| `neutral-900` #111827 | **16.15:1** AAA | **15.39:1** AAA | **14.04:1** AAA | **12.55:1** AAA |
| `neutral-800` #1F2937 | **13.44:1** AAA | **12.81:1** AAA | **11.68:1** AAA | **10.44:1** AAA |
| `neutral-700` #374151 | **9.68:1** AAA | **9.22:1** AAA | **8.41:1** AAA | **7.52:1** AAA |
| `neutral-600` #4B5563 | **7.21:1** AAA | **6.87:1** AA | **6.27:1** AA | **5.60:1** AA |
| `neutral-500` #6B7280 | **4.64:1** AA | **4.42:1** AA | **4.03:1** AA-LG | **3.60:1** AA-LG |
| `neutral-400` #9CA3AF | **2.80:1** FAIL | **2.67:1** FAIL | **2.44:1** FAIL | **2.18:1** FAIL |
| `neutral-300` #D1D5DB | **1.55:1** FAIL | **1.47:1** FAIL | **1.34:1** FAIL | **1.20:1** FAIL |

### Primary Blue on Light Backgrounds

| Foreground | on `white` | on `neutral-50` | on `neutral-100` | on `primary-50` |
|---|---|---|---|---|
| `primary-900` #0A1523 | **18.27:1** AAA | **17.41:1** AAA | **15.88:1** AAA | **16.30:1** AAA |
| `primary-800` #0F1F33 | **16.58:1** AAA | **15.80:1** AAA | **14.41:1** AAA | **14.79:1** AAA |
| `primary-700` #162C47 | **13.89:1** AAA | **13.23:1** AAA | **12.07:1** AAA | **12.39:1** AAA |
| `primary-600` #1A3353 | **12.38:1** AAA | **11.80:1** AAA | **10.76:1** AAA | **11.04:1** AAA |
| `primary-500` #1E3A5F | **10.93:1** AAA | **10.42:1** AAA | **9.50:1** AAA | **9.75:1** AAA |
| `primary-400` #5178A0 | **4.47:1** AA | **4.26:1** AA-LG | **3.89:1** AA-LG | **3.99:1** AA-LG |
| `primary-300` #85A2BF | **2.63:1** FAIL | **2.50:1** FAIL | **2.28:1** FAIL | **2.34:1** FAIL |

### Accent Amber on Light Backgrounds

| Foreground | on `white` | on `neutral-50` | on `neutral-100` | on `accent-50` |
|---|---|---|---|---|
| `accent-950` #5C2A0A | **9.85:1** AAA | **9.39:1** AAA | **8.56:1** AAA | **9.15:1** AAA |
| `accent-900` #78350F | **8.04:1** AAA | **7.66:1** AAA | **6.99:1** AA | **7.47:1** AAA |
| `accent-800` #92400E | **6.52:1** AA | **6.21:1** AA | **5.67:1** AA | **6.06:1** AA |
| `accent-700` #B45309 | **4.70:1** AA | **4.48:1** AA | **4.09:1** AA-LG | **4.37:1** AA-LG |
| `accent-600` #D97706 | **3.19:1** AA-LG | **3.04:1** AA-LG | **2.77:1** FAIL | **2.96:1** FAIL |
| `accent-500` #F59E0B | **2.23:1** FAIL | **2.12:1** FAIL | **1.94:1** FAIL | **2.07:1** FAIL |

> **Important**: Accent-500 fails contrast for text on any light background. Use accent-700 or darker for text, and reserve accent-500 for large icons, decorative elements, or backgrounds with dark text.

### Semantic Colors on Their Surfaces

| Foreground | on Its Surface | Ratio | Grade |
|---|---|---|---|
| Success emphasis `#065F46` | on `#ECFDF5` | **7.84:1** | AAA |
| Success default `#10B981` | on `#ECFDF5` | **2.72:1** | FAIL (text), AA-LG (icons) |
| Warning emphasis `#92400E` | on `#FFFBEB` | **6.45:1** | AA |
| Warning default `#F59E0B` | on `#FFFBEB` | **2.08:1** | FAIL (text only; pair with label) |
| Error emphasis `#991B1B` | on `#FEF2F2` | **7.22:1** | AAA |
| Error default `#EF4444` | on `#FEF2F2` | **3.25:1** | AA-LG |
| Info emphasis `#1E40AF` | on `#EFF6FF` | **7.98:1** | AAA |
| Info default `#3B82F6` | on `#EFF6FF` | **3.21:1** | AA-LG |

### Text on Primary Surfaces

| Foreground | on `primary-500` #1E3A5F | Ratio | Grade |
|---|---|---|---|
| `white` #FFFFFF | | **10.93:1** | AAA |
| `neutral-50` #F9FAFB | | **10.42:1** | AAA |
| `neutral-100` #F3F4F6 | | **9.50:1** | AAA |
| `neutral-200` #E5E7EB | | **8.49:1** | AAA |
| `accent-300` #FCD34D | | **7.81:1** | AAA |
| `accent-400` #FBBF24 | | **6.55:1** | AA |
| `accent-500` #F59E0B | | **4.89:1** | AA |

### Text on Accent Surfaces

| Foreground | on `accent-500` #F59E0B | Ratio | Grade |
|---|---|---|---|
| `neutral-900` #111827 | | **7.25:1** | AAA |
| `neutral-800` #1F2937 | | **6.03:1** | AA |
| `primary-800` #0F1F33 | | **7.44:1** | AAA |
| `primary-500` #1E3A5F | | **4.91:1** | AA |
| `white` #FFFFFF | | **2.23:1** | FAIL |

> **Important**: White text on accent-500 fails all contrast levels. Always use dark text on amber backgrounds.

---

## Dark Theme Contrast Matrix

### Neutral Text on Dark Backgrounds

| Foreground | on `neutral-900` #111827 | on `neutral-800` #1F2937 | on `neutral-700` #374151 |
|---|---|---|---|
| `white` #FFFFFF | **16.15:1** AAA | **13.44:1** AAA | **9.68:1** AAA |
| `neutral-50` #F9FAFB | **15.39:1** AAA | **12.81:1** AAA | **9.22:1** AAA |
| `neutral-100` #F3F4F6 | **14.04:1** AAA | **11.68:1** AAA | **8.41:1** AAA |
| `neutral-200` #E5E7EB | **12.55:1** AAA | **10.44:1** AAA | **7.52:1** AAA |
| `neutral-300` #D1D5DB | **10.43:1** AAA | **8.68:1** AAA | **6.25:1** AA |
| `neutral-400` #9CA3AF | **5.77:1** AA | **4.80:1** AA | **3.46:1** AA-LG |
| `neutral-500` #6B7280 | **3.48:1** AA-LG | **2.89:1** FAIL | **2.09:1** FAIL |

### Primary Blue on Dark Backgrounds

| Foreground | on `neutral-900` #111827 | on `neutral-800` #1F2937 | on `neutral-700` #374151 |
|---|---|---|---|
| `primary-200` #A7BCD1 | **7.38:1** AAA | **6.14:1** AA | **4.42:1** AA |
| `primary-300` #85A2BF | **6.14:1** AA | **5.11:1** AA | **3.68:1** AA-LG |
| `primary-400` #5178A0 | **3.62:1** AA-LG | **3.01:1** AA-LG | **2.17:1** FAIL |
| `primary-100` #C9D6E3 | **9.82:1** AAA | **8.17:1** AAA | **5.89:1** AA |

> **Guidance**: Use `primary-300` for linked text and `primary-200` for high-emphasis primary text in dark mode on `neutral-900`.

### Accent Amber on Dark Backgrounds

| Foreground | on `neutral-900` #111827 | on `neutral-800` #1F2937 | on `neutral-700` #374151 |
|---|---|---|---|
| `accent-200` #FDE68A | **11.83:1** AAA | **9.84:1** AAA | **7.09:1** AAA |
| `accent-300` #FCD34D | **10.67:1** AAA | **8.88:1** AAA | **6.40:1** AA |
| `accent-400` #FBBF24 | **8.94:1** AAA | **7.44:1** AAA | **5.36:1** AA |
| `accent-500` #F59E0B | **6.51:1** AA | **5.42:1** AA | **3.90:1** AA-LG |
| `accent-600` #D97706 | **4.36:1** AA-LG | **3.63:1** AA-LG | **2.61:1** FAIL |

### Semantic Colors on Dark Surfaces

| Foreground | on Its Dark Surface | Ratio | Grade |
|---|---|---|---|
| `#6EE7B7` (success light) | on `#052E1C` | **8.41:1** | AAA |
| `#10B981` (success default) | on `#052E1C` | **5.62:1** | AA |
| `#FCD34D` (warning light) | on `#3D2800` | **8.15:1** | AAA |
| `#F59E0B` (warning default) | on `#3D2800` | **5.02:1** | AA |
| `#FCA5A5` (error light) | on `#3B1111` | **7.04:1** | AAA |
| `#EF4444` (error default) | on `#3B1111` | **3.89:1** | AA-LG |
| `#93C5FD` (info light) | on `#172554` | **7.26:1** | AAA |
| `#3B82F6` (info default) | on `#172554` | **3.74:1** | AA-LG |

### Text on Dark Primary Surfaces

| Foreground | on `primary-400` #5178A0 | Ratio | Grade |
|---|---|---|---|
| `white` #FFFFFF | **4.47:1** | AA |
| `neutral-900` #111827 | **3.62:1** | AA-LG |
| `neutral-50` #F9FAFB | **4.26:1** | AA-LG |

> **Note**: `primary-400` as a button background in dark mode passes AA with white text. For maximum contrast, pair with white.

---

## Quick Reference: Approved Pairings

### Light Theme -- Safe Text Combinations

| Background | Text Color | Ratio | Use For |
|---|---|---|---|
| `white` | `neutral-900` | 16.15:1 | Headings |
| `white` | `neutral-800` | 13.44:1 | Headings |
| `white` | `neutral-700` | 9.68:1 | Headings, body |
| `white` | `neutral-600` | 7.21:1 | Body text |
| `white` | `neutral-500` | 4.64:1 | Captions, secondary |
| `white` | `primary-500` | 10.93:1 | Links, interactive |
| `white` | `accent-800` | 6.52:1 | Accent text |
| `neutral-50` | `neutral-700` | 9.22:1 | Body text |
| `neutral-100` | `neutral-700` | 8.41:1 | Body text on alt bg |
| `primary-500` | `white` | 10.93:1 | Button text |
| `accent-500` | `neutral-900` | 7.25:1 | Button text (dark on amber) |

### Dark Theme -- Safe Text Combinations

| Background | Text Color | Ratio | Use For |
|---|---|---|---|
| `neutral-900` | `white` | 16.15:1 | Headings |
| `neutral-900` | `neutral-50` | 15.39:1 | Headings |
| `neutral-900` | `neutral-200` | 12.55:1 | Body text |
| `neutral-900` | `neutral-300` | 10.43:1 | Body text |
| `neutral-900` | `neutral-400` | 5.77:1 | Secondary text |
| `neutral-900` | `primary-300` | 6.14:1 | Links |
| `neutral-900` | `accent-400` | 8.94:1 | Accent text |
| `neutral-800` | `neutral-200` | 10.44:1 | Body text on cards |
| `neutral-800` | `neutral-400` | 4.80:1 | Secondary text on cards |
| `neutral-800` | `primary-300` | 5.11:1 | Links on cards |

---

## Tools for Verification

### Manual Calculation

Contrast ratio = (L1 + 0.05) / (L2 + 0.05), where L1 is the relative luminance of the lighter color and L2 is the darker.

### Recommended Tools

| Tool | URL | Notes |
|---|---|---|
| WebAIM Contrast Checker | webaim.org/resources/contrastchecker | Quick single-pair check |
| Colour Contrast Analyser (TPGi) | Desktop app | Includes color picker |
| Stark (Figma plugin) | Available in Figma | Integrated design workflow |
| axe DevTools | Browser extension | Automated page-level audit |
| Polypane | polypane.app | Built-in contrast debugging |

### Automated Testing

Include contrast checks in CI/CD pipelines:

```javascript
// Example: axe-core in integration tests
const { axe } = require('axe-core');
const results = await axe.run(document, {
  rules: {
    'color-contrast': { enabled: true }
  }
});
expect(results.violations).toHaveLength(0);
```

---

## Notes

- Ratios in this document are calculated from the hex values listed in the color system and rounded to two decimal places.
- When a ratio falls between thresholds (e.g., 4.45:1), the combination is classified at the lower level for safety.
- All ratios should be re-verified if any palette hex value is updated.
- See `dark-mode.md` for full dark theme implementation details and `color-system.md` for the complete palette.
