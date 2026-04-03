# Brand Typography

## 1. Typeface Strategy

The Flavio Fusuma typographic system uses two typeface families chosen for their quality, versatility, and alignment with the brand personality: technically precise yet warm and approachable.

### Selection Criteria
- **Open-source**: Free to use commercially, no licensing concerns
- **Variable font support**: Single file, multiple weights — performance optimized
- **Excellent legibility**: Optimized for screen reading at all sizes
- **Broad language support**: Latin Extended, supporting Portuguese and other Latin-based languages
- **Active maintenance**: Regularly updated with improvements and expanded character sets

## 2. Primary Typeface: Inter

**Role**: All UI text, headings, body copy, navigation, and marketing materials

| Property | Value |
|----------|-------|
| **Family** | Inter |
| **Classification** | Humanist sans-serif |
| **Designer** | Rasmus Andersson |
| **License** | SIL Open Font License 1.1 |
| **Variable axes** | Weight (100–900), Italic |
| **Source** | [Google Fonts](https://fonts.google.com/specimen/Inter) |

### Why Inter
- **Precision**: Designed specifically for computer screens with meticulous optical adjustments at small sizes — aligns with the "craftsmanship" value
- **Versatility**: 9 weights from Thin to Black cover every typographic need from delicate captions to bold display headings
- **Readability**: Tall x-height, open apertures, and distinct letterforms ensure excellent legibility even at 12px
- **Variable font**: Single ~300KB file replaces 18 static files (9 weights × 2 styles), improving page performance
- **Tabular figures**: Built-in support for aligned numbers in data tables and dashboards

### Brand Weights

| Weight | Name | CSS Value | Usage |
|--------|------|-----------|-------|
| 400 | Regular | `font-weight: 400` | Body text, paragraphs, descriptions |
| 500 | Medium | `font-weight: 500` | UI labels, navigation, emphasized text |
| 600 | SemiBold | `font-weight: 600` | Subheadings, card titles, strong emphasis |
| 700 | Bold | `font-weight: 700` | Page headings, hero text, CTAs |
| 800 | ExtraBold | `font-weight: 800` | Display text, impact statements (rare) |

**Note**: Weights 100–300 and 900 are available in the variable font but are not part of the standard brand usage. Reserve them for special design contexts (e.g., large decorative display text).

## 3. Monospace Typeface: JetBrains Mono

**Role**: Code blocks, technical content, terminal output, code-related UI elements

| Property | Value |
|----------|-------|
| **Family** | JetBrains Mono |
| **Classification** | Monospaced |
| **Designer** | Philipp Nurullin, Konstantin Bulenkov |
| **License** | SIL Open Font License 1.1 |
| **Variable axes** | Weight (100–800), Italic |
| **Source** | [Google Fonts](https://fonts.google.com/specimen/JetBrains+Mono) |

### Why JetBrains Mono
- **Developer identity**: Designed by JetBrains for developers — directly aligns with the brand's audience and identity
- **Code ligatures**: Optional ligatures for common programming symbols (=>, !=, ===) enhance readability in code contexts
- **Increased height**: 1.5x height of standard monospace fonts improves readability of code blocks
- **Distinct characters**: Clear differentiation between similar characters (0/O, 1/l/I) reduces code-reading errors

### Brand Weights

| Weight | Name | CSS Value | Usage |
|--------|------|-----------|-------|
| 400 | Regular | `font-weight: 400` | Code blocks, inline code |
| 500 | Medium | `font-weight: 500` | Code headings, file names |
| 700 | Bold | `font-weight: 700` | Code emphasis, key terms in technical content |

## 4. Typeface Pairing Rationale

Inter and JetBrains Mono are complementary:

| Dimension | Inter | JetBrains Mono |
|-----------|-------|----------------|
| **Role** | Human communication | Technical communication |
| **Feel** | Warm, professional | Precise, technical |
| **x-height** | Tall (harmonizes with Mono) | Tall (harmonizes with Inter) |
| **Letterform style** | Humanist, open | Geometric, structured |
| **Weight range** | 100–900 | 100–800 |

The pairing creates a clear visual distinction between prose/UI and code/technical content while maintaining harmonious proportions.

## 5. Font Loading Strategy

### Recommended Implementation

```html
<!-- Preconnect for performance -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Variable fonts — single request, all weights -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
```

### CSS Font Stack

```css
/* Primary — UI and body text */
--font-family-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;

/* Monospace — code and technical content */
--font-family-mono: 'JetBrains Mono', 'Fira Code', 'Cascadia Code', 'SF Mono', Menlo, Consolas, monospace;
```

### Font Display Strategy
- Use `font-display: swap` to ensure text is visible during font loading
- System fonts in the stack provide a visually similar fallback
- Prioritize loading Inter Regular (400) and Bold (700) first — these cover 80% of use cases

## 6. Typographic Hierarchy Preview

### Light Theme

| Level | Font | Weight | Size | Color | Usage |
|-------|------|--------|------|-------|-------|
| Display | Inter | 800 | 48–72px | `#1E3A5F` | Hero headlines |
| H1 | Inter | 700 | 36–48px | `#1E3A5F` | Page titles |
| H2 | Inter | 700 | 28–36px | `#1E293B` | Section headers |
| H3 | Inter | 600 | 22–28px | `#1E293B` | Subsection headers |
| H4 | Inter | 600 | 18–22px | `#334155` | Card titles |
| H5 | Inter | 600 | 16–18px | `#334155` | Widget headers |
| Body Large | Inter | 400 | 18px | `#475569` | Lead paragraphs |
| Body | Inter | 400 | 16px | `#475569` | Default body text |
| Body Small | Inter | 400 | 14px | `#64748B` | Secondary text |
| Caption | Inter | 500 | 12px | `#64748B` | Labels, metadata |
| Overline | Inter | 600 | 11px | `#94A3B8` | Category labels (uppercase, tracked) |
| Code Block | JetBrains Mono | 400 | 14px | `#1E293B` | Code samples |
| Code Inline | JetBrains Mono | 400 | 14px | `#1E3A5F` | Inline code references |

## 7. Usage Guidelines

### Do's
- Use Inter for all non-code text, from navigation to body copy to headings
- Use JetBrains Mono only for actual code, file paths, terminal commands, or technical identifiers
- Maintain the defined weight hierarchy — don't use Bold for body text or Regular for headings
- Allow sufficient line-height for readability (see Design System typography docs)
- Use the variable font format for web — it's smaller and more flexible

### Don'ts
- Don't substitute Inter with other sans-serif fonts in brand materials
- Don't use more than 3 weights in a single layout (it creates visual noise)
- Don't use JetBrains Mono for headings, buttons, or non-code UI elements
- Don't track (letter-space) body text — Inter is already optimized for screen reading
- Don't use font weights below 400 for body text — they're too light for comfortable reading
- Don't use all-caps for more than a single line of text (overline/labels only)

## 8. Fallback and Print Typography

### Digital Fallback
When brand fonts cannot be loaded (email clients, third-party platforms):
1. **Primary fallback**: System font stack (`-apple-system, BlinkMacSystemFont, 'Segoe UI'`)
2. **Secondary fallback**: `Arial, Helvetica, sans-serif`
3. **Monospace fallback**: `Menlo, Consolas, 'Courier New', monospace`

### Print Materials
For print materials where web fonts aren't applicable:
- **Primary**: Inter (install locally from Google Fonts)
- **Monospace**: JetBrains Mono (install locally)
- **Fallback**: Helvetica Neue (widely available on print systems)
