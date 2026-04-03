# Type Scale

The Flavio Fusuma type scale defines 12 levels from `display-2xl` to `code`. Each level specifies size, weight, line height, letter spacing, and responsive behavior across four breakpoints.

**Typefaces**: Inter (sans-serif), JetBrains Mono (monospace)

---

## Scale Overview

| Level | Mobile (375px) | Tablet (768px) | Desktop (1024px) | Wide (1440px) | Weight | Line Height | Letter Spacing | Max Width |
|---|---|---|---|---|---|---|---|---|
| `display-2xl` | 36px / 2.25rem | 48px / 3rem | 60px / 3.75rem | 72px / 4.5rem | 800 | tight (1.1) | -0.025em | 20ch |
| `display-xl` | 30px / 1.875rem | 40px / 2.5rem | 48px / 3rem | 60px / 3.75rem | 700 | tight (1.1) | -0.02em | 24ch |
| `display-lg` | 24px / 1.5rem | 32px / 2rem | 40px / 2.5rem | 48px / 3rem | 700 | snug (1.25) | -0.015em | 28ch |
| `heading-lg` | 22px / 1.375rem | 26px / 1.625rem | 30px / 1.875rem | 36px / 2.25rem | 600 | snug (1.25) | -0.01em | 32ch |
| `heading-md` | 18px / 1.125rem | 20px / 1.25rem | 24px / 1.5rem | 28px / 1.75rem | 600 | snug (1.25) | -0.005em | 36ch |
| `heading-sm` | 16px / 1rem | 17px / 1.0625rem | 18px / 1.125rem | 20px / 1.25rem | 600 | normal (1.5) | 0em | 40ch |
| `body-lg` | 17px / 1.0625rem | 18px / 1.125rem | 18px / 1.125rem | 20px / 1.25rem | 400 | relaxed (1.625) | 0em | 65ch |
| `body-md` | 15px / 0.9375rem | 16px / 1rem | 16px / 1rem | 16px / 1rem | 400 | relaxed (1.625) | 0em | 65ch |
| `body-sm` | 14px / 0.875rem | 14px / 0.875rem | 14px / 0.875rem | 14px / 0.875rem | 400 | normal (1.5) | 0em | 65ch |
| `caption` | 12px / 0.75rem | 12px / 0.75rem | 12px / 0.75rem | 12px / 0.75rem | 400 | normal (1.5) | 0.01em | 50ch |
| `overline` | 11px / 0.6875rem | 11px / 0.6875rem | 12px / 0.75rem | 12px / 0.75rem | 600 | normal (1.5) | 0.08em | 40ch |
| `code` | 14px / 0.875rem | 14px / 0.875rem | 14px / 0.875rem | 15px / 0.9375rem | 400 | relaxed (1.625) | 0em | 80ch |

---

## Detailed Level Specifications

### display-2xl

The largest display text. Used for hero sections, landing page headlines, and key marketing statements.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 800 (Extra Bold) |
| Line height | 1.1 (tight) |
| Letter spacing | -0.025em |
| Text transform | None |
| Max width | 20ch |
| Responsive sizes | 36px -> 48px -> 60px -> 72px |

```css
.display-2xl {
  font-family: 'Inter', sans-serif;
  font-weight: 800;
  font-size: 2.25rem;     /* 36px */
  line-height: 1.1;
  letter-spacing: -0.025em;
  max-width: 20ch;
}

@media (min-width: 768px)  { .display-2xl { font-size: 3rem; } }      /* 48px */
@media (min-width: 1024px) { .display-2xl { font-size: 3.75rem; } }   /* 60px */
@media (min-width: 1440px) { .display-2xl { font-size: 4.5rem; } }    /* 72px */
```

### display-xl

Secondary display text. Used for major section headers on marketing pages, feature callouts.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 700 (Bold) |
| Line height | 1.1 (tight) |
| Letter spacing | -0.02em |
| Text transform | None |
| Max width | 24ch |
| Responsive sizes | 30px -> 40px -> 48px -> 60px |

```css
.display-xl {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  font-size: 1.875rem;    /* 30px */
  line-height: 1.1;
  letter-spacing: -0.02em;
  max-width: 24ch;
}

@media (min-width: 768px)  { .display-xl { font-size: 2.5rem; } }
@media (min-width: 1024px) { .display-xl { font-size: 3rem; } }
@media (min-width: 1440px) { .display-xl { font-size: 3.75rem; } }
```

### display-lg

Tertiary display text. Section openers, large feature titles.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 700 (Bold) |
| Line height | 1.25 (snug) |
| Letter spacing | -0.015em |
| Text transform | None |
| Max width | 28ch |
| Responsive sizes | 24px -> 32px -> 40px -> 48px |

```css
.display-lg {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  font-size: 1.5rem;      /* 24px */
  line-height: 1.25;
  letter-spacing: -0.015em;
  max-width: 28ch;
}

@media (min-width: 768px)  { .display-lg { font-size: 2rem; } }
@media (min-width: 1024px) { .display-lg { font-size: 2.5rem; } }
@media (min-width: 1440px) { .display-lg { font-size: 3rem; } }
```

### heading-lg

Page-level headings in product UI. Primary heading on dashboard pages, settings panels.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 600 (Semi Bold) |
| Line height | 1.25 (snug) |
| Letter spacing | -0.01em |
| Text transform | None |
| Max width | 32ch |
| Responsive sizes | 22px -> 26px -> 30px -> 36px |

```css
.heading-lg {
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1.375rem;    /* 22px */
  line-height: 1.25;
  letter-spacing: -0.01em;
  max-width: 32ch;
}

@media (min-width: 768px)  { .heading-lg { font-size: 1.625rem; } }
@media (min-width: 1024px) { .heading-lg { font-size: 1.875rem; } }
@media (min-width: 1440px) { .heading-lg { font-size: 2.25rem; } }
```

### heading-md

Section headings within product pages. Card titles, dialog titles, sidebar section headers.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 600 (Semi Bold) |
| Line height | 1.25 (snug) |
| Letter spacing | -0.005em |
| Text transform | None |
| Max width | 36ch |
| Responsive sizes | 18px -> 20px -> 24px -> 28px |

```css
.heading-md {
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1.125rem;    /* 18px */
  line-height: 1.25;
  letter-spacing: -0.005em;
  max-width: 36ch;
}

@media (min-width: 768px)  { .heading-md { font-size: 1.25rem; } }
@media (min-width: 1024px) { .heading-md { font-size: 1.5rem; } }
@media (min-width: 1440px) { .heading-md { font-size: 1.75rem; } }
```

### heading-sm

Sub-section headings. Form group labels, table column headers, accordion titles.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 600 (Semi Bold) |
| Line height | 1.5 (normal) |
| Letter spacing | 0em |
| Text transform | None |
| Max width | 40ch |
| Responsive sizes | 16px -> 17px -> 18px -> 20px |

```css
.heading-sm {
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1rem;         /* 16px */
  line-height: 1.5;
  letter-spacing: 0em;
  max-width: 40ch;
}

@media (min-width: 768px)  { .heading-sm { font-size: 1.0625rem; } }
@media (min-width: 1024px) { .heading-sm { font-size: 1.125rem; } }
@media (min-width: 1440px) { .heading-sm { font-size: 1.25rem; } }
```

### body-lg

Large body text. Used for introductory paragraphs, article ledes, prominent descriptions.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 400 (Regular) |
| Line height | 1.625 (relaxed) |
| Letter spacing | 0em |
| Text transform | None |
| Max width | 65ch |
| Responsive sizes | 17px -> 18px -> 18px -> 20px |

```css
.body-lg {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  font-size: 1.0625rem;   /* 17px */
  line-height: 1.625;
  letter-spacing: 0em;
  max-width: 65ch;
}

@media (min-width: 768px)  { .body-lg { font-size: 1.125rem; } }
@media (min-width: 1440px) { .body-lg { font-size: 1.25rem; } }
```

### body-md

Default body text. The workhorse of the system. Most paragraph content, list items, form descriptions.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 400 (Regular) |
| Line height | 1.625 (relaxed) |
| Letter spacing | 0em |
| Text transform | None |
| Max width | 65ch |
| Responsive sizes | 15px -> 16px -> 16px -> 16px |

```css
.body-md {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  font-size: 0.9375rem;   /* 15px */
  line-height: 1.625;
  letter-spacing: 0em;
  max-width: 65ch;
}

@media (min-width: 768px) { .body-md { font-size: 1rem; } }
```

### body-sm

Small body text. Secondary descriptions, helper text, table cell content.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 400 (Regular) |
| Line height | 1.5 (normal) |
| Letter spacing | 0em |
| Text transform | None |
| Max width | 65ch |
| Responsive sizes | 14px (all breakpoints) |

```css
.body-sm {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  font-size: 0.875rem;    /* 14px */
  line-height: 1.5;
  letter-spacing: 0em;
  max-width: 65ch;
}
```

### caption

Captions, footnotes, timestamps. The smallest text used for non-critical supplementary information.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 400 (Regular) |
| Line height | 1.5 (normal) |
| Letter spacing | 0.01em |
| Text transform | None |
| Max width | 50ch |
| Responsive sizes | 12px (all breakpoints) |

```css
.caption {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  font-size: 0.75rem;     /* 12px */
  line-height: 1.5;
  letter-spacing: 0.01em;
  max-width: 50ch;
}
```

### overline

Category labels, eyebrow text, metadata labels. Always uppercase or small-caps.

| Property | Value |
|---|---|
| Typeface | Inter |
| Weight | 600 (Semi Bold) |
| Line height | 1.5 (normal) |
| Letter spacing | 0.08em |
| Text transform | uppercase |
| Max width | 40ch |
| Responsive sizes | 11px -> 11px -> 12px -> 12px |

```css
.overline {
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 0.6875rem;   /* 11px */
  line-height: 1.5;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  max-width: 40ch;
}

@media (min-width: 1024px) { .overline { font-size: 0.75rem; } }
```

### code

Inline code, code blocks, technical values. Uses the monospace typeface.

| Property | Value |
|---|---|
| Typeface | JetBrains Mono |
| Weight | 400 (Regular) |
| Line height | 1.625 (relaxed) |
| Letter spacing | 0em |
| Text transform | None |
| Max width | 80ch |
| Responsive sizes | 14px -> 14px -> 14px -> 15px |

```css
.code {
  font-family: 'JetBrains Mono', monospace;
  font-weight: 400;
  font-size: 0.875rem;    /* 14px */
  line-height: 1.625;
  letter-spacing: 0em;
  max-width: 80ch;
}

@media (min-width: 1440px) { .code { font-size: 0.9375rem; } }
```

---

## Responsive Scaling Strategy

### Approach: Stepped, Not Fluid

The type scale uses stepped sizes at each breakpoint rather than fluid `clamp()` values. This provides:

- Predictable rendering at every viewport width.
- Easier QA (only four sizes to verify per level).
- Alignment with the grid system's discrete breakpoints.

### Breakpoint Summary

| Breakpoint | Name | Min Width | Primary Typeface Size | Notes |
|---|---|---|---|---|
| Default | Mobile | 0px | `body-md` at 15px | Mobile-first base |
| `sm` | Tablet | 768px | `body-md` at 16px | Slight size bump |
| `md` | Desktop | 1024px | `body-md` at 16px | Display sizes increase significantly |
| `lg` | Wide | 1440px | `body-md` at 16px | Display sizes reach maximum |

### Size Progression Ratios

Display and heading sizes scale more aggressively than body text:

- **Display levels**: ~1.3x to 2x increase from mobile to wide.
- **Heading levels**: ~1.2x to 1.6x increase from mobile to wide.
- **Body levels**: 1x to 1.07x increase (minimal change to preserve readability).
- **Utility levels** (caption, overline, code): No change or minimal change.

---

## Font Loading

### Performance Strategy

```html
<!-- Preload critical fonts -->
<link rel="preload" href="/fonts/inter-var.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="/fonts/jetbrains-mono-var.woff2" as="font" type="font/woff2" crossorigin>
```

```css
/* Font-face declarations with fallback chain */
@font-face {
  font-family: 'Inter';
  src: url('/fonts/inter-var.woff2') format('woff2');
  font-weight: 100 900;
  font-display: swap;
}

@font-face {
  font-family: 'JetBrains Mono';
  src: url('/fonts/jetbrains-mono-var.woff2') format('woff2');
  font-weight: 100 800;
  font-display: swap;
}
```

### Fallback Stack

```css
--font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
             'Helvetica Neue', Arial, sans-serif;
--font-mono: 'JetBrains Mono', 'SF Mono', 'Fira Code', 'Fira Mono',
             'Roboto Mono', 'Courier New', monospace;
```

---

## Usage Guidelines

### Pairing Levels

| Context | Heading Level | Body Level |
|---|---|---|
| Marketing hero | `display-2xl` or `display-xl` | `body-lg` |
| Marketing section | `display-lg` | `body-lg` or `body-md` |
| Product page header | `heading-lg` | `body-md` |
| Product section | `heading-md` | `body-md` |
| Card / compact module | `heading-sm` | `body-sm` |
| Metadata / label | `overline` | `caption` |
| Code documentation | `heading-md` | `code` |

### Weight Variants

Each level has a defined default weight. Additional weights are available for emphasis within body text:

| Purpose | Weight | Token |
|---|---|---|
| Regular body text | 400 | `font-weight-regular` |
| Emphasized body text | 500 | `font-weight-medium` |
| Strong body text | 600 | `font-weight-semibold` |
| Headings (sm/md/lg) | 600 | `font-weight-semibold` |
| Display text | 700--800 | `font-weight-bold` / `font-weight-extrabold` |

Do not use weights below 400 (light/thin) for any text that must be readable at small sizes. Reserve 300 or lighter for decorative display text at 48px or above only.
