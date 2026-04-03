# Typography Accessibility

This document defines the accessibility requirements for all typography in the Flavio Fusuma Design System. It covers minimum sizes, contrast, readability, responsive scaling, and internationalization.

---

## Minimum Text Sizes

### Hard Minimums

| Context | Minimum Size | Rationale |
|---|---|---|
| Body text | 14px (0.875rem) | Below 14px, most users struggle to read paragraph-length text |
| Interactive labels (buttons, links, form labels) | 14px (0.875rem) | Must be legible at arm's length on mobile |
| Input text | 16px (1rem) on mobile | iOS zooms inputs below 16px, disrupting layout |
| Caption/footnote text | 12px (0.75rem) | Absolute minimum; must not carry critical information alone |
| Overline/eyebrow text | 11px (0.6875rem) | Allowed only with 600 weight and 0.08em letter spacing |
| Code text | 14px (0.875rem) | Monospace fonts read slightly smaller than proportional at same px |

### Advisory Minimums

These are not hard requirements but are strongly recommended:

- **Body text for extended reading**: 16px minimum (15px only on mobile where viewport is small).
- **Text for users 65+**: 16px minimum for all content, 18px preferred for body.
- **Text displayed on screens viewed from > 50cm** (TV, kiosk, signage): 24px minimum.

---

## WCAG Text Requirements

### 1.4.3 -- Contrast (Minimum) -- Level AA

| Text Type | Minimum Contrast Ratio |
|---|---|
| Normal text (< 24px regular, < 18.66px bold) | 4.5:1 |
| Large text (>= 24px regular, >= 18.66px bold) | 3:1 |

### 1.4.6 -- Contrast (Enhanced) -- Level AAA

| Text Type | Enhanced Contrast Ratio |
|---|---|
| Normal text | 7:1 |
| Large text | 4.5:1 |

> The Flavio Fusuma system targets AA as the minimum. AAA is recommended for primary body text and required for legal/critical text.

### 1.4.4 -- Resize Text -- Level AA

Users must be able to resize text up to 200% without loss of content or functionality. Implementation requirements:

- Use `rem` or `em` units for font sizes, never `px` on the `font-size` property in production CSS.
- Do not set a fixed `height` on text containers; use `min-height` if needed.
- Test the entire interface at browser zoom levels of 100%, 150%, and 200%.

### 1.4.8 -- Visual Presentation -- Level AAA (Advisory)

For blocks of body text:

- Line height at least 1.5x the font size (met by `line-height-normal` and above).
- Paragraph spacing at least 1.5x the line height (met by `space-3` between paragraphs).
- Line width no more than 80 characters (met by `max-width: 65ch` on body text).
- Text is not full-justified (`text-align: justify` is prohibited).
- Text can be resized up to 200% without requiring horizontal scrolling.

### 1.4.12 -- Text Spacing -- Level AA

Users must be able to override the following without breaking the layout:

| Property | Override Value |
|---|---|
| Line height | At least 1.5x the font size |
| Paragraph spacing | At least 2x the font size |
| Letter spacing | At least 0.12em |
| Word spacing | At least 0.16em |

**Implementation**: never use fixed heights on text containers. Test with the following CSS override applied:

```css
/* WCAG 1.4.12 text spacing test override */
* {
  line-height: 1.5 !important;
  letter-spacing: 0.12em !important;
  word-spacing: 0.16em !important;
}
p {
  margin-bottom: 2em !important;
}
```

If any content is clipped or overlaps, the layout is non-compliant.

---

## Dyslexia Considerations

Approximately 10-15% of the population has some degree of dyslexia. The following guidelines reduce reading barriers:

### Typeface Choice

Inter is a strong choice for accessibility:

- Clear distinction between similar characters: `I` (capital i), `l` (lowercase L), `1` (one).
- Open apertures on `c`, `e`, `a`, `s` reduce ambiguity.
- Consistent stroke width avoids visual vibration.
- No decorative features that interfere with letter recognition.

### Text Formatting Rules

| Rule | Implementation |
|---|---|
| Avoid all-caps for passages longer than a few words | Use `text-transform: uppercase` only on `overline` level |
| Avoid italic for passages longer than one sentence | Use medium weight (500) for emphasis instead |
| Left-align body text | `text-align: left` (never `justify`) |
| Use adequate letter spacing | Minimum 0em for body, positive for small/uppercase text |
| Use adequate word spacing | Default browser spacing is sufficient; do not compress |
| Avoid hyphenation | `hyphens: none` on body text |
| Use short paragraphs | Break text into chunks of 3-5 sentences |
| Use bullet lists for sequential information | Prefer `<ul>` / `<ol>` over inline comma-separated lists |

### Character Disambiguation

Verify these character pairs are visually distinct in the chosen typeface at all sizes:

| Pair | Risk |
|---|---|
| `I` / `l` / `1` | Capital I, lowercase L, and numeral 1 |
| `O` / `0` | Capital O and numeral zero |
| `b` / `d` | Mirror confusion |
| `p` / `q` | Mirror confusion |
| `rn` / `m` | Ligature confusion at small sizes |
| `cl` / `d` | Shape confusion at small sizes |

Inter handles all these pairs well at 14px and above. Below 14px, verify rendering on target devices.

---

## Contrast Requirements for Text

### Color Pairings (Quick Reference)

See `02-color/contrast-ratios.md` for the full matrix. Key requirements:

| Text Role | Light Mode Pairing | Dark Mode Pairing | Minimum Ratio |
|---|---|---|---|
| Primary text | `neutral-800` on `white` | `neutral-50` on `neutral-900` | 7:1 (AAA target) |
| Secondary text | `neutral-600` on `white` | `neutral-300` on `neutral-900` | 4.5:1 (AA) |
| Tertiary text | `neutral-500` on `white` | `neutral-400` on `neutral-900` | 4.5:1 (AA) |
| Link text | `primary-500` on `white` | `primary-300` on `neutral-900` | 4.5:1 (AA) |
| Disabled text | `neutral-400` on `white` | `neutral-500` on `neutral-900` | 3:1 (WCAG 1.4.11) |
| Error text | `error-emphasis` on `white` | `#FCA5A5` on `neutral-900` | 4.5:1 (AA) |
| Text on primary bg | `white` on `primary-500` | `white` on `primary-400` | 4.5:1 (AA) |
| Text on accent bg | `neutral-900` on `accent-500` | `neutral-900` on `accent-400` | 4.5:1 (AA) |

### Placeholder Text

Placeholder text inside inputs must meet 4.5:1 contrast. If the default browser placeholder color fails, override it:

```css
::placeholder {
  color: var(--color-neutral-500); /* 4.64:1 on white */
  opacity: 1; /* Firefox reduces opacity by default */
}
```

### Text Over Images

Text placed over images must use one of:

1. A solid or semi-transparent overlay between the image and text.
2. A text shadow or background box behind the text.
3. A gradient overlay that guarantees contrast in the text region.

Verify contrast against the lightest (or darkest, for dark text) region of the image where text appears.

---

## Responsive Text Scaling

### Approach

Text scales at defined breakpoints (not fluid) to maintain predictability. See `type-scale.md` for the full responsive table.

### Key Rules

1. **Never shrink text below hard minimums** at any breakpoint, including mobile at 375px.
2. **Body text changes minimally** across breakpoints (15px to 16px). Drastic body size changes disrupt the reading experience.
3. **Display and heading text scales aggressively** to take advantage of larger viewports without overwhelming small screens.
4. **Use `rem` units** so that user font-size preferences in browser settings are respected.

### Zoom and Pinch-to-Zoom

- Never set `maximum-scale=1` or `user-scalable=no` in the viewport meta tag.
- The correct viewport meta tag:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

- Test that all content remains accessible at 200% browser zoom.

### Dynamic Type / System Font Scaling

On platforms that support system-level font scaling (iOS Dynamic Type, Android font size settings):

- Respect the user's system preference where technically feasible.
- Set minimum and maximum bounds to prevent layout breakage:
  - Minimum: 12px equivalent
  - Maximum: 2x the default size

---

## Language and Internationalization

### Script-Specific Considerations

| Script Family | Considerations |
|---|---|
| Latin (English, French, German, etc.) | Inter is optimized for Latin; no adjustments needed. |
| CJK (Chinese, Japanese, Korean) | Requires a dedicated CJK typeface. Inter does not cover CJK glyphs. Use Noto Sans CJK or system default. Line height may need increase to 1.7+. |
| Arabic / Hebrew (RTL) | Requires RTL layout (`dir="rtl"`). Use Noto Sans Arabic or equivalent. Letter spacing must be 0 (Arabic is cursive). |
| Devanagari / Thai / other complex scripts | Require dedicated typefaces with proper shaping. Line height of 1.75+ is recommended due to tall ascenders/descenders. |
| Cyrillic / Greek | Inter supports both natively. No adjustments needed. |

### String Expansion

Translated strings can be significantly longer than English originals:

| Target Language | Typical Expansion | Example |
|---|---|---|
| German | +30% | "Settings" (8) -> "Einstellungen" (14) |
| French | +20% | "Save" (4) -> "Enregistrer" (12) |
| Finnish | +30-40% | "Delete" (6) -> "Poista kohde" (12) |
| Chinese | -30% (fewer chars but wider) | "Settings" (8) -> "设置" (2, but wider glyphs) |
| Arabic | +25% | Varies; accounts for diacritics |

**Implementation rules:**

- Never set fixed widths on text containers. Use `min-width` if alignment is needed.
- Buttons must accommodate text expansion without truncation. Use padding, not fixed width.
- Test layouts with pseudolocalization (e.g., `[!!Sëttïñgs!!]`) to reveal overflow before real translations are available.
- Navigation items should be tested with the longest expected translation.

### Font Fallback Chains

```css
/* Latin (default) */
--font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI',
             Roboto, 'Helvetica Neue', Arial, sans-serif;

/* CJK (override per locale) */
--font-sans-cjk: 'Inter', 'Noto Sans CJK SC', 'PingFang SC',
                 'Hiragino Sans GB', 'Microsoft YaHei', sans-serif;

/* Arabic (override per locale) */
--font-sans-ar: 'Noto Sans Arabic', 'Inter', 'Segoe UI',
                Tahoma, sans-serif;
```

### Vertical Text (CJK)

For Japanese vertical writing mode (`writing-mode: vertical-rl`), the type scale applies to the vertical axis. Line height controls horizontal spacing between columns. Use `line-height-relaxed` (1.625) minimum for vertical text.

---

## Testing Checklist

### Automated

- [ ] All text uses `rem` or `em` units (lint rule).
- [ ] No viewport meta disables zoom (`maximum-scale`, `user-scalable`).
- [ ] axe-core or similar reports zero contrast violations.
- [ ] No fixed-height text containers (lint rule for `height` on elements containing text).

### Manual

- [ ] Interface is functional and readable at 200% browser zoom.
- [ ] WCAG 1.4.12 text spacing override does not clip or overlap content.
- [ ] Screen reader announces all text in logical reading order.
- [ ] All text is selectable (no user-select: none on readable content).
- [ ] Placeholder text meets 4.5:1 contrast.
- [ ] Character pairs `I/l/1` and `O/0` are distinguishable at smallest used size.
- [ ] Layouts accommodate 40% string expansion without horizontal scroll.
- [ ] RTL layout mirrors correctly for Arabic/Hebrew content.
