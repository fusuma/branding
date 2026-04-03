# Logo Usage Guidelines

## 1. Purpose

This document governs the correct and consistent application of the Flavio Fusuma logo across all media, formats, and contexts. These guidelines exist to protect the integrity of the brand identity and ensure that every touchpoint — from a 16px favicon to a conference stage backdrop — communicates the same level of craft and intentionality that defines the brand itself.

All team members, collaborators, partners, and vendors who reproduce the Flavio Fusuma logo must follow these rules without exception. When in doubt, consult the brand owner before proceeding.

---

## 2. Clear Space

Clear space is the minimum unobstructed area surrounding the logo that must remain free of all other visual elements — text, imagery, borders, edges, other logos, decorative elements, and UI components.

### Measurement Unit

Clear space is measured in **F-units**, where **1F = the cap height of the letter F in the primary mark** (or the full height of the monogram/bracket mark in icon-only usage).

For the FF Monogram (Concept A) and Code Bracket Mark (Concept C), 1F equals the full height of the symbol.
For the Fusuma Wordmark (Concept B), 1F equals the x-height of the lowercase letterforms.

### Minimum Clear Space

| Context | Clear Space |
|---------|-------------|
| **Standard usage** | 1F on all four sides |
| **Hero / primary brand moments** | 1.5F on all four sides |
| **Co-branding layouts** | 2F between the Flavio Fusuma logo and any partner logo |
| **Edge of page / screen** | 1F from any trim edge (print) or viewport edge (digital) |

### Clear Space Diagram (Conceptual)

```
                    ← 1F →
               ┌─────────────────┐
               │                 │
         1F ↕  │   ┌─────────┐  │  ↕ 1F
               │   │  LOGO   │  │
               │   └─────────┘  │
         1F ↕  │                 │
               └─────────────────┘
                    ← 1F →
```

### What Violates Clear Space

- Text (including taglines, URLs, or descriptors)
- Other logos or brand marks
- Photographic content or illustrations
- Decorative rules, borders, or keylines
- UI elements (buttons, navigation items, form fields)
- The edge of a container, card, or bounding box (unless the logo is intentionally bleeding off a surface, which requires explicit approval)

---

## 3. Minimum Sizes

Below these thresholds, the logo loses legibility and structural integrity. Never reproduce the logo smaller than the values listed.

### Digital (Screen)

| Logo Format | Minimum Width | Minimum Height | Notes |
|-------------|--------------|----------------|-------|
| **FF Monogram (icon)** | 24px | 24px | Switch to filled variant below 32px |
| **Code Bracket Mark (stroked)** | 32px | 32px | Strokes collapse below this size |
| **Code Bracket Mark (filled)** | 16px | 16px | Preferred for favicon / small icon use |
| **Full horizontal lockup** | 120px | — | Height is determined by aspect ratio |
| **Stacked lockup** | 64px | — | Height is determined by aspect ratio |
| **Wordmark only** | 120px | — | Below this, letterform details are lost |

### Print

| Logo Format | Minimum Width | Minimum Height | Notes |
|-------------|--------------|----------------|-------|
| **FF Monogram (icon)** | 8mm | 8mm | |
| **Code Bracket Mark (stroked)** | 10mm | 10mm | |
| **Code Bracket Mark (filled)** | 6mm | 6mm | |
| **Full horizontal lockup** | 30mm | — | |
| **Stacked lockup** | 18mm | — | |
| **Wordmark only** | 30mm | — | |

### Special Contexts

| Context | Minimum Size | Notes |
|---------|-------------|-------|
| **Embroidery** | 12mm height (icon) | Use filled variants only; no fine strokes |
| **Engraving / debossing** | 10mm height (icon) | Test with material vendor before production |
| **Watermark** | 48px height | Must be at ≤ 8% opacity in Fusuma Blue or white |

---

## 4. Approved Color Combinations

### Logo on Light Backgrounds

| Background | Logo Color | Status |
|------------|-----------|--------|
| White `#FFFFFF` | Fusuma Blue `#1E3A5F` | **Primary — preferred** |
| Blue-50 `#EFF6FF` | Fusuma Blue `#1E3A5F` | Approved |
| Blue-100 `#DBEAFE` | Fusuma Blue `#1E3A5F` | Approved |
| Neutral-50 `#FAFAFA` | Fusuma Blue `#1E3A5F` | Approved |
| Neutral-100 `#F5F5F5` | Fusuma Blue `#1E3A5F` | Approved |
| Amber-50 `#FFFBEB` | Fusuma Blue `#1E3A5F` | Approved — use sparingly |
| Any light tint (luminance > 85%) | Black `#000000` | Approved — monochrome fallback |

### Logo on Dark Backgrounds

| Background | Logo Color | Status |
|------------|-----------|--------|
| Fusuma Blue `#1E3A5F` | White `#FFFFFF` | **Primary — preferred** |
| Blue-900 `#1E3050` | White `#FFFFFF` | Approved |
| Blue-950 `#172340` | White `#FFFFFF` | Approved |
| Neutral-900 `#171717` | White `#FFFFFF` | Approved |
| Black `#000000` | White `#FFFFFF` | Approved |
| Fusuma Blue `#1E3A5F` | Amber `#F59E0B` | Approved — accent usage only |
| Any dark surface (luminance < 25%) | White `#FFFFFF` | Approved |

### Logo on Photography or Complex Backgrounds

When the logo must be placed over photographic imagery, textured surfaces, or complex visual content:

1. **Preferred**: Place the logo within a solid-color container (white or Fusuma Blue rectangle with rounded corners at 4px / 1mm radius) with 1F internal padding.
2. **Acceptable**: Apply a semi-transparent scrim (Fusuma Blue at 70% opacity or black at 50% opacity) behind the logo area before placing the white logo on top.
3. **Never**: Place the logo directly on an unmodified photograph or busy background.

### Contrast Requirements

All logo-on-background combinations must meet **WCAG 2.1 AA contrast requirements** at minimum (4.5:1 for normal text, 3:1 for large text / graphical objects). The approved combinations above all exceed 4.5:1.

---

## 5. Co-Branding Guidelines

When the Flavio Fusuma logo appears alongside other organizations' logos — on partner pages, event materials, joint projects, or open-source collaborations:

### Hierarchy

1. **Equal partnership**: Logos appear at the same optical height (not necessarily the same pixel height — match visual weight). Separate with a 1px vertical rule in Neutral-300 `#D4D4D4` or a 2F horizontal gap, whichever suits the layout.
2. **Flavio Fusuma as primary**: The Flavio Fusuma logo appears first (left in horizontal layouts, top in vertical layouts) and may be up to 125% the optical height of the partner logo.
3. **Flavio Fusuma as secondary / contributor**: The logo appears after the primary brand and matches or is slightly smaller than the primary brand's logo.

### Spacing

- **Minimum separation**: 2F between the Flavio Fusuma logo and any partner logo
- **Vertical divider**: When used, the divider is centered between the two logos with 1F of space on each side (total separation = 2F + divider width)
- **"×" or "+" connector**: When a typographic connector is used (e.g., "Flavio Fusuma × Acme Corp"), set it in Inter Medium at the x-height of the smaller logo, centered in the gap

### Rules

- Never merge, blend, interlock, or visually combine the Flavio Fusuma logo with another brand's mark
- Never alter the Flavio Fusuma logo's colors to match a partner's brand palette
- Never place the Flavio Fusuma logo inside another brand's visual container or frame
- Always maintain the minimum clear space around the Flavio Fusuma logo, even within a co-branded lockup
- If a partner's brand guidelines conflict with these rules, contact the brand owner to negotiate a mutually acceptable solution

---

## 6. Misuse Examples

The following are **strictly prohibited**. Each example describes a specific violation — these are not exhaustive but represent the most common errors.

### 6.1 — Do Not Stretch or Distort

Never apply non-uniform scaling. The logo must always maintain its original aspect ratio. Horizontally or vertically stretched marks are immediately recognizable as errors and undermine brand credibility.

### 6.2 — Do Not Rotate

The logo is designed to be read at 0° orientation. Do not rotate it to 45°, 90°, or any other angle. If a layout requires a vertical text treatment, use a separate typographic element — not the logo itself.

### 6.3 — Do Not Apply Drop Shadows or Outer Glows

The logo's power comes from its clean geometry and flat color. Drop shadows, outer glows, inner shadows, bevels, emboss effects, or any other dimensional treatment compromise its precision.

### 6.4 — Do Not Apply Gradients

The logo must be rendered in flat, solid color. Do not fill it with linear gradients, radial gradients, mesh gradients, or any color transition. The approved color options are specified in Section 4 above.

### 6.5 — Do Not Outline or Add Strokes to Filled Marks

The filled mark variants (FF Monogram, filled Code Bracket Mark) should not have additional outlines or border strokes applied around their edges. The form is already defined; adding strokes alters proportions and muddies the silhouette.

### 6.6 — Do Not Change the Typeface of the Wordmark

The Fusuma Wordmark (Concept B) uses a custom-modified version of Inter. Do not re-set it in standard Inter, Helvetica, Arial, or any other typeface. The wordmark is a logotype, not editable text.

### 6.7 — Do Not Rearrange Lockup Elements

The spatial relationships between the mark and wordmark in each lockup are precisely defined. Do not change the relative positioning, spacing, or alignment of elements within a lockup. Use only the provided lockup files.

### 6.8 — Do Not Place on Low-Contrast Backgrounds

Never place the blue logo on a medium-blue background, the white logo on a light gray background, or any combination that fails to meet the 3:1 minimum contrast ratio for graphical elements. If in doubt, test with a contrast checker.

### 6.9 — Do Not Crop or Mask the Logo

The logo must always appear in its entirety. Do not crop it with a circle, rounded rectangle, or any other clipping mask that removes parts of the mark. The only exception is platform-imposed avatar cropping (e.g., circular avatars on social platforms), for which a dedicated icon-only variant is provided.

### 6.10 — Do Not Animate Without Approved Motion Specs

If the logo appears in motion contexts (video intros, loading animations, scroll-triggered effects), it must follow the approved motion specification (to be defined in a future motion guidelines document). Do not apply bouncing, spinning, pulsing, morphing, or particle effects to the logo.

### 6.11 — Do Not Add Taglines or Descriptors Within Clear Space

Taglines, URLs, titles, or descriptive text must not intrude into the logo's defined clear space. If a tagline must accompany the logo, it is placed outside the clear space boundary, typeset in Inter Regular at a size no larger than 40% of the wordmark height.

### 6.12 — Do Not Recreate the Logo

Never attempt to redraw, re-trace, or re-create the logo from memory or description. Always use the official asset files. This includes "approximating" the logo in presentation software by arranging shapes or text boxes.

---

## 7. File Format Guide

### Provided Formats

| Format | Extension | Color Mode | Usage |
|--------|-----------|-----------|-------|
| **SVG** | `.svg` | RGB | Web, digital products, responsive interfaces, CSS embedding, animation. The primary digital format — scalable, searchable, and editable. |
| **PDF** | `.pdf` | CMYK + RGB | Print production, presentation decks, documents. Contains vector paths and preserves color profiles. |
| **PNG** | `.png` | RGB, sRGB | Digital contexts where SVG is unsupported — email signatures, social media uploads, bitmap composites. Exported at 1×, 2×, and 4× resolutions. |
| **PNG (transparent)** | `.png` | RGB, sRGB | Same as above but with transparent background. Required for overlays on colored or photographic backgrounds. |
| **EPS** | `.eps` | CMYK | Legacy print workflows. Provided for vendor compatibility but PDF is preferred. |
| **ICO** | `.ico` | RGB | Windows favicon. Contains 16×16, 32×32, and 48×48 sizes. |
| **WEBP** | `.webp` | RGB, sRGB | High-performance web usage where bitmap is required. Exported at 1×, 2×, and 4× resolutions. |

### File Naming Convention

```
ff-logo-{concept}-{lockup}-{variation}-{size}.{ext}
```

**Examples:**
- `ff-logo-monogram-icon-blue-on-white-1x.png`
- `ff-logo-monogram-horizontal-reversed-white.svg`
- `ff-logo-bracket-icon-filled-blue.svg`
- `ff-logo-wordmark-full-accent-initial.pdf`
- `ff-logo-monogram-stacked-monochrome-dark-2x.png`

### When to Use Which Format

| Scenario | Recommended Format |
|----------|-------------------|
| Website header / navigation | SVG |
| Email signature | PNG (2×, transparent) |
| Social media avatar | PNG (1×, opaque, platform-specific dimensions) |
| Business card | PDF (CMYK) |
| Slide deck | SVG or PNG (2×) |
| Favicon | SVG (modern browsers) + ICO (fallback) |
| Mobile app icon | PNG (platform-specific sizes: iOS 1024×1024, Android 512×512) |
| Large-format print (banner, poster) | PDF (CMYK, vector) |
| Merchandise (t-shirt, sticker) | PDF or EPS (CMYK, vector) |
| Open Graph / social sharing image | PNG (1200×630 @ 1×) |
| Dark mode interface | SVG (white or amber variant) |

---

## 8. Responsive Logo Behavior

The logo system is designed to adapt gracefully across viewport widths and container sizes. The following cascade defines which logo format to use at each breakpoint.

### Cascade Rules

```
Full horizontal lockup  →  Stacked lockup  →  Abbreviated  →  Icon only
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
                                                                        
≥ 768px container width    ≥ 480px           ≥ 240px         < 240px    
      or                        or               or              or     
≥ 120px logo width         ≥ 80px            ≥ 48px          < 48px     
```

### Level 1 — Full Horizontal Lockup

**When**: Container width ≥ 768px and available logo width ≥ 120px.

**What**: The complete mark + wordmark in horizontal arrangement. This is the most complete expression of the brand and should be used whenever space permits.

**Specification**: Mark height = target height. Wordmark baseline-aligned to mark vertical center. 0.75F gap between mark and wordmark.

### Level 2 — Stacked Lockup

**When**: Container width is between 480px and 767px, or available logo width is between 80px and 119px.

**What**: Mark centered above wordmark. Used in narrow navigation bars, mobile headers in landscape orientation, and sidebar contexts.

**Specification**: Mark centered above wordmark. 0.5F gap between mark bottom and wordmark ascender line. Total width equals the wider of mark or wordmark.

### Level 3 — Abbreviated Mark

**When**: Container width is between 240px and 479px, or available logo width is between 48px and 79px.

**What**: The monogram or bracket mark only, without the wordmark. For the wordmark-only concept (B), this level uses a truncated version reading "FF" in the custom letterforms.

**Specification**: Mark at full fidelity, centered in available space. For the FF Monogram, this is the same as the icon. For the Code Bracket Mark, use the stroked version above 32px, filled version at or below 32px.

### Level 4 — Icon Only

**When**: Container width < 240px, or available logo width < 48px, or explicitly icon-sized contexts (favicons, app icons, notification badges, tab bars).

**What**: The simplest possible rendition of the mark. FF Monogram or filled Code Bracket Mark only. No wordmark, no additional elements.

**Specification**: Use the filled variant of whichever concept is in play. Ensure the icon version has been optically adjusted for the target size (pixel-hinted if necessary at 16px and 32px).

### Implementation Notes

- **CSS**: Use `<picture>` elements or CSS `content` properties with media queries to swap between logo levels. Alternatively, use a single SVG with embedded media queries or JavaScript-controlled `viewBox` swapping.
- **Frameworks**: In React, Vue, or similar frameworks, create a `<BrandLogo />` component that accepts a `size` or `variant` prop and renders the appropriate level.
- **Do not scale down**: Never take the full horizontal lockup and shrink it to icon size. Each level is a distinct, purpose-designed asset — not a resized version of the level above.

### Responsive Logo Decision Tree

```
START
  │
  ├─ Is the context a favicon, app icon, or avatar?
  │   └─ YES → Level 4 (Icon Only)
  │
  ├─ Is the available width < 48px?
  │   └─ YES → Level 4 (Icon Only)
  │
  ├─ Is the available width < 80px?
  │   └─ YES → Level 3 (Abbreviated Mark)
  │
  ├─ Is the available width < 120px?
  │   └─ YES → Level 2 (Stacked Lockup)
  │
  └─ Otherwise → Level 1 (Full Horizontal Lockup)
```

---

## 9. Special Contexts

### Dark Mode

When the interface or medium operates in a dark color scheme:

- Switch to the white or amber-on-blue variant of the logo
- Never use the Fusuma Blue logo on dark backgrounds — it will lack sufficient contrast
- If implementing programmatic dark mode, ensure the logo variant swaps alongside other theme tokens

### Print on Uncoated Paper

Uncoated paper absorbs more ink, causing colors to appear darker and details to fill in:

- Use the filled variants of the monogram and bracket mark
- Increase the minimum size by 25% over the standard print minimums
- Request a press proof before approving any print run featuring the logo

### Embroidery and Physical Goods

Thread-based reproduction cannot render fine details:

- Use only the FF Monogram (filled) or the filled Code Bracket Mark
- Minimum embroidery height: 12mm
- Reduce the stroke count by removing the F's middle arm in the bracket mark if the embroidery vendor cannot maintain clarity at the target size
- Always request a physical sample before approving a production run

### Video and Motion

- The logo must hold static for a minimum of 2 seconds in any video appearance to ensure readability
- Entry animations should complete within 0.6 seconds; exit animations within 0.4 seconds
- The logo should never be obscured by lower thirds, captions, or other overlaid content during its hold time
- Use the full horizontal lockup for video end cards; use the icon for persistent watermarks

---

## 10. Governance

### Who Approves Logo Usage?

All non-standard logo applications — those not explicitly covered by the rules in this document — require written approval from Flavio Fusuma (brand owner) before production. "Non-standard" includes but is not limited to:

- New color combinations not listed in Section 4
- Placement on backgrounds not covered by Section 4
- Sizes below the minimums in Section 3
- Co-branding arrangements with new partners
- Physical merchandise or environmental applications
- Animated or interactive logo treatments

### Version Control

- Logo assets are versioned using semantic versioning (e.g., `v1.0.0`)
- The current version is always available in the brand assets repository
- Outdated versions must be retired from all active touchpoints within 30 days of a new version release
- This guidelines document is versioned in lockstep with the logo assets

### Contact

For questions, requests, or clarification on any guideline in this document, contact the brand owner directly. Do not interpret ambiguous cases independently — the cost of a misapplied logo far exceeds the cost of a brief conversation.

---

*Document version: 1.0.0*
*Last updated: 2026-04-03*
*Companion document: `05-logo-concepts.md`*
