# Line Heights

The Flavio Fusuma line height system defines five named values that control vertical spacing within text blocks. Combined with the type scale, these values establish a consistent vertical rhythm across the entire interface.

---

## Line Height Scale

| Token | Name | Value | Computed at 16px | Primary Use |
|---|---|---|---|---|
| `line-height-tight` | Tight | 1.1 | 17.6px | Display text, large headings |
| `line-height-snug` | Snug | 1.25 | 20px | Headings, short multi-line text |
| `line-height-normal` | Normal | 1.5 | 24px | Small body text, captions, UI labels |
| `line-height-relaxed` | Relaxed | 1.625 | 26px | Body text, long-form reading |
| `line-height-loose` | Loose | 1.75 | 28px | Body text with inline code, dense UIs needing air |

---

## When to Use Each

### Tight (1.1)

Use tight line height for large display text where each line is a single visual unit. At display sizes (36px+), the default browser line height creates too much vertical space, making headlines feel disconnected.

**Appropriate for:**
- `display-2xl`, `display-xl`, `display-lg`
- Single-line hero headlines
- Large numerals in data dashboards
- Logotype lockups

**Not appropriate for:**
- Any text that wraps to more than 2-3 lines
- Body copy at any size
- Text below 24px (descenders may clip or collide)

```css
.display-2xl {
  font-size: 4.5rem;
  line-height: 1.1; /* 79.2px at 72px font size */
}
```

### Snug (1.25)

Use snug line height for headings and short text blocks that may wrap to 2-3 lines. Tighter than body text but loose enough to remain readable across multiple lines.

**Appropriate for:**
- `heading-lg`, `heading-md`
- Card titles that wrap to two lines
- Navigation items
- Button text (single line)
- List items with short content

**Not appropriate for:**
- Paragraphs longer than 3 lines
- Display text above 40px (use tight)
- Dense data tables (use normal)

```css
.heading-md {
  font-size: 1.5rem;
  line-height: 1.25; /* 30px at 24px font size */
}
```

### Normal (1.5)

The standard web line height. Provides adequate spacing for most UI text that does not involve long-form reading. This is the default when no specific line height is assigned.

**Appropriate for:**
- `heading-sm`, `body-sm`, `caption`, `overline`
- Form labels and input text
- Table cell content
- Tooltip text
- Breadcrumbs and metadata

**Not appropriate for:**
- Long paragraphs (use relaxed for comfort)
- Display headings (use tight or snug)

```css
.body-sm {
  font-size: 0.875rem;
  line-height: 1.5; /* 21px at 14px font size */
}
```

### Relaxed (1.625)

Optimized for extended reading. The extra vertical space reduces visual density and improves line tracking, which is critical for paragraphs of 4+ lines.

**Appropriate for:**
- `body-lg`, `body-md`, `code`
- Article paragraphs
- Help documentation
- Email body content
- Any text block exceeding 3 lines

**Not appropriate for:**
- Headings (too airy, weakens visual weight)
- Single-line UI elements (wastes space)
- Compact data displays

```css
.body-md {
  font-size: 1rem;
  line-height: 1.625; /* 26px at 16px font size */
}
```

### Loose (1.75)

Maximum breathing room. Use sparingly for situations where visual density is high and text needs maximum separation from surrounding elements.

**Appropriate for:**
- Body text with frequent inline code snippets (the extra height accommodates code background boxes)
- Dense reference documentation
- Text inside narrow columns (under 40ch) where limited measure increases cognitive load
- Interfaces for users with low vision (configurable via accessibility settings)

**Not appropriate for:**
- Default body text (too much whitespace for normal reading)
- Headings
- Compact or data-dense layouts

```css
.body-with-code {
  font-size: 1rem;
  line-height: 1.75; /* 28px at 16px font size */
}
```

---

## Vertical Rhythm

### The 8px Rhythm Grid

All line heights are designed to produce computed values that align to the 8px spacing grid when paired with their designated type scale levels. This creates a consistent vertical rhythm where baselines and element edges fall on predictable grid lines.

| Type Level | Font Size | Line Height | Computed Line Height | Nearest 8px Multiple |
|---|---|---|---|---|
| `display-2xl` (wide) | 72px | 1.1 | 79.2px | 80px |
| `display-xl` (wide) | 60px | 1.1 | 66px | 64px |
| `display-lg` (wide) | 48px | 1.25 | 60px | 56px |
| `heading-lg` (desktop) | 30px | 1.25 | 37.5px | 40px |
| `heading-md` (desktop) | 24px | 1.25 | 30px | 32px |
| `heading-sm` (desktop) | 18px | 1.5 | 27px | 24px |
| `body-lg` (desktop) | 18px | 1.625 | 29.25px | 32px |
| `body-md` (desktop) | 16px | 1.625 | 26px | 24px |
| `body-sm` | 14px | 1.5 | 21px | 24px |
| `caption` | 12px | 1.5 | 18px | 16px |
| `overline` | 12px | 1.5 | 18px | 16px |
| `code` | 14px | 1.625 | 22.75px | 24px |

> Not every computed line height lands perfectly on an 8px multiple. The vertical rhythm is maintained through spacing tokens (margins and padding) that compensate for fractional differences.

### Spacing Between Text Blocks

The space between consecutive text blocks follows these rules:

| Relationship | Spacing Rule | Token |
|---|---|---|
| Heading followed by body text | 1x the body line height | `space-3` (24px) or `space-4` (32px) |
| Body paragraph followed by body paragraph | 1x the body line height | `space-3` (24px) |
| Heading followed by heading (section + subsection) | 0.5x the larger heading's line height | `space-2` (16px) |
| Body text followed by heading (new section) | 2x the body line height | `space-6` (48px) or `space-8` (64px) |
| Caption/overline followed by heading | 0.5x the caption line height | `space-1` (8px) |

### Consistent Spacing Pattern

```css
/* Standard article content flow */
.article h2 + p   { margin-top: 1.5rem; }   /* 24px -- heading to body */
.article p + p     { margin-top: 1.5rem; }   /* 24px -- paragraph to paragraph */
.article p + h2    { margin-top: 3rem; }     /* 48px -- body to new section */
.article h2 + h3   { margin-top: 1rem; }    /* 16px -- heading to subheading */
```

---

## Implementation

### CSS Custom Properties

```css
:root {
  --line-height-tight: 1.1;
  --line-height-snug: 1.25;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.625;
  --line-height-loose: 1.75;
}
```

### Utility Classes

```css
.leading-tight   { line-height: var(--line-height-tight); }
.leading-snug    { line-height: var(--line-height-snug); }
.leading-normal  { line-height: var(--line-height-normal); }
.leading-relaxed { line-height: var(--line-height-relaxed); }
.leading-loose   { line-height: var(--line-height-loose); }
```

### Never Override Without Reason

Line heights are bound to type scale levels by default. Override only when:

1. The type level is used in an unusual context (e.g., `body-md` inside a tight data table row).
2. Accessibility requirements demand a looser setting.
3. Inline elements (code, badges) within a line require additional vertical clearance.

Document any override with a comment explaining the reason.
