# Logo Concepts

## 1. Design Philosophy

The Flavio Fusuma logomark must embody the brand's core tension: the precision of engineering and the warmth of human-centered design. Each concept below approaches this challenge from a different formal angle, but all share a common set of design principles:

- **Geometric rigor**: Every element aligns to a defined grid; no arbitrary curves or angles
- **Optical balance**: Mathematical precision is adjusted where necessary for visual harmony
- **Scalability**: Each mark must reproduce cleanly from 16px favicons to 2-meter event banners
- **Dual-context fluency**: The mark must feel native in both developer tooling (dark terminals, GitHub profiles) and design contexts (portfolios, pitch decks, conference stages)

### Design Grid

All three concepts are constructed on a **64 × 64 unit master grid** with an **8-unit baseline module**. Key construction lines fall on 8-unit increments. Curves, where present, are drawn from circles whose centers and radii snap to grid intersections. This ensures consistent reproduction across formats and prevents rasterization artifacts at small sizes.

---

## 2. Concept A — "FF Monogram"

### Description

A geometric ligature of two uppercase letterforms "F" and "F," interlocked to form a single, indivisible mark. The second F is horizontally mirrored and overlapped with the first, creating a symmetrical composition that reads as both "FF" and as an abstract, architectural form. The negative space between the two letters produces a subtle vertical channel reminiscent of a code cursor or insertion point.

### Geometry Specification

| Parameter | Value |
|-----------|-------|
| **Overall proportions** | 1:1 square bounding box (64 × 64 units) |
| **Stroke weight** | 8 units (12.5% of total width) |
| **Cap height** | 56 units (87.5% of bounding box) |
| **Vertical centering offset** | 4 units from top and bottom edges |
| **Horizontal stems** | Two per F, positioned at y = 4 (top) and y = 28 (midline) |
| **Midline position** | Optically centered at 43.75% of cap height from top (not mathematical center) |
| **Horizontal stem length** | 24 units (37.5% of bounding box width) |
| **Vertical stem height** | Full cap height, 56 units |
| **Mirror axis** | Vertical center at x = 32 |
| **Overlap zone** | 8-unit-wide shared vertical channel at center (x = 28 to x = 36) |
| **Corner treatment** | Sharp, 0-radius — no rounding |
| **Angles** | Strictly 0° and 90° — no diagonals |

### Construction Method

1. Draw the left F: vertical stem from (8, 4) to (8, 60), top horizontal from (8, 4) to (32, 4), middle horizontal from (8, 28) to (28, 28). All strokes 8 units wide.
2. Mirror the entire letterform across the vertical axis at x = 32 to produce the right F.
3. The two vertical stems overlap in the center zone (x = 28 to x = 36), merging into a single 8-unit-wide column. This shared stem is the ligature's structural joint.
4. The top horizontals extend outward in opposite directions, creating a wide horizontal bar spanning the full width.
5. The middle horizontals extend outward from the center, forming a symmetrical pair of wings.

### SVG Markup

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" width="128" height="128">
  <title>Flavio Fusuma — FF Monogram</title>
  <desc>Geometric ligature of two mirrored uppercase F letterforms in Fusuma Blue.</desc>
  <g fill="#1E3A5F" fill-rule="evenodd">
    <!-- Shared center vertical stem -->
    <rect x="28" y="4" width="8" height="56"/>
    <!-- Left vertical stem -->
    <rect x="4" y="4" width="8" height="56"/>
    <!-- Right vertical stem -->
    <rect x="52" y="4" width="8" height="56"/>
    <!-- Top horizontal bar (full width) -->
    <rect x="4" y="4" width="56" height="8"/>
    <!-- Left middle horizontal -->
    <rect x="4" y="28" width="32" height="8"/>
    <!-- Right middle horizontal -->
    <rect x="28" y="28" width="32" height="8"/>
  </g>
</svg>
```

### Proportional Grid & Clear Space

The mark sits within its 64-unit square bounding box with 4 units of internal padding on all sides. Clear space is defined as **1F** — one "F-height," equal to the full cap height of the mark (56 units in grid terms). In practice:

- **Minimum clear space**: 1F on all four sides of the bounding box
- **Preferred clear space**: 1.5F for hero placements and primary brand moments

### Variations

| Variation | Description | Use Case |
|-----------|-------------|----------|
| **Full color** | Fusuma Blue `#1E3A5F` on white `#FFFFFF` | Default usage on light backgrounds |
| **Full color, amber accent** | Fusuma Blue mark with amber `#F59E0B` middle horizontals | Feature moments, hero sections, event branding |
| **Monochrome dark** | Black `#000000` on white `#FFFFFF` | Print when color is unavailable, fax, legal |
| **Monochrome light** | White `#FFFFFF` on transparent | Dark backgrounds, overlays on photography |
| **Reversed** | White `#FFFFFF` on Fusuma Blue `#1E3A5F` | Primary reversed application |
| **Reversed amber** | Amber `#F59E0B` on Fusuma Blue `#1E3A5F` | Dark UI headers, dark mode feature areas |
| **Icon-only** | Monogram only, no wordmark | Favicons, app icons, social avatars |

### Minimum Sizes

| Context | Minimum Size |
|---------|-------------|
| **Digital (screen)** | 24 × 24 px |
| **Print** | 8 mm × 8 mm |
| **Embroidery / engraving** | 12 mm × 12 mm |

---

## 3. Concept B — "Fusuma Wordmark"

### Description

A custom-lettered wordmark reading **"flavio fusuma"** in lowercase, set in a style derived from Inter but with deliberate, hand-crafted modifications. The defining feature is a bespoke treatment of the lowercase **"f"** — the only letter that appears three times in the full name, and the shared initial of both first and last names.

### Letterform Modifications

#### The Custom "f"

The standard Inter lowercase "f" has a modest, curved hook at the top and a simple horizontal crossbar. The Fusuma "f" introduces three key modifications:

1. **Extended crossbar**: The crossbar extends leftward beyond the vertical stem by 50% of its rightward length, creating asymmetry that references a code cursor or text-editing caret. In the standard Inter "f," the crossbar is nearly symmetrical; here, the left extension reaches 6 units past the stem while the right extends 4 units.

2. **Angular terminal**: The top hook is straightened into a 45° angular cut rather than a rounded terminal. This references the precision of geometric construction and echoes the angle brackets used in code (`<`, `>`). The cut begins at the apex of the ascender and descends at exactly 45° for 4 units before meeting the vertical stem.

3. **Baseline notch**: A small 2-unit notch is cut from the bottom-left corner of the vertical stem at the baseline, creating a subtle visual anchor that distinguishes the letter in small sizes and adds a detail that rewards close inspection.

#### Other Modifications

- **Tracking**: Set at −10 (tighter than Inter's default) to create a more cohesive word-shape
- **"v" ligature**: The crossbar of the first "f" in "flavio" optionally connects to the top of the "l," forming a subtle ligature at display sizes (40px+)
- **Word space**: The space between "flavio" and "fusuma" is set at 60% of a standard word space, binding the two words into a single visual unit

### SVG — Custom "f" Character

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 64" width="80" height="128">
  <title>Flavio Fusuma — Custom "f" Letterform</title>
  <desc>Bespoke lowercase f with extended crossbar, angular terminal, and baseline notch.</desc>
  <g fill="#1E3A5F">
    <!-- Vertical stem -->
    <rect x="12" y="12" width="6" height="48"/>
    <!-- Extended crossbar (asymmetric) -->
    <rect x="2" y="28" width="28" height="5"/>
    <!-- Angular terminal (45° cut at top) -->
    <polygon points="18,4 26,4 26,8 18,12"/>
    <!-- Top hook connection to stem -->
    <rect x="18" y="8" width="8" height="6"/>
    <!-- Baseline notch (subtractive — rendered as two rects replacing bottom of stem) -->
    <rect x="14" y="56" width="4" height="4" fill="#FFFFFF"/>
  </g>
  <!-- Re-render stem bottom-right to preserve form after notch -->
  <rect x="14" y="56" width="4" height="4" fill="#FFFFFF"/>
</svg>
```

> **Note**: The SVG above is a schematic representation of the custom "f" for specification purposes. Final production files will be produced as fully outlined vector paths in a type design application (Glyphs, FontForge, or RoboFont) and exported as a complete SVG wordmark.

### Full Wordmark Specification

| Parameter | Value |
|-----------|-------|
| **Overall proportions** | Approximately 7.2:1 width-to-height ratio |
| **x-height** | 32 units |
| **Ascender height** | 48 units |
| **Cap height** | N/A (all lowercase) |
| **Baseline** | y = 56 |
| **Descender depth** | 8 units below baseline (for eventual "g," "p," "y" alternates) |
| **Tracking** | −10 units |
| **Word space** | 60% of standard (≈ 12 units) |
| **Stroke contrast** | Low; consistent with Inter's humanist monolinear design |

### Proportional Grid & Clear Space

- **Clear space**: 1x (one x-height) on all sides of the wordmark bounding box
- **Preferred clear space**: 1.5x for primary placements
- The wordmark should never be placed closer than 1x to any other visual element, rule, or edge

### Variations

| Variation | Description | Use Case |
|-----------|-------------|----------|
| **Full color** | Fusuma Blue `#1E3A5F` on white | Primary usage |
| **Accent initial** | First "f" of each word in amber `#F59E0B`, remainder in Fusuma Blue | Feature placements, about pages, signatures |
| **Monochrome dark** | Black `#000000` on white | Single-color print |
| **Monochrome light** | White `#FFFFFF` on transparent | Dark backgrounds |
| **Reversed** | White on Fusuma Blue | Reversed contexts |
| **Stacked** | "flavio" above "fusuma," left-aligned, with the "f" letters vertically aligned | Narrow-format contexts (mobile headers, vertical banners) |

### Minimum Sizes

| Context | Minimum Size |
|---------|-------------|
| **Digital (screen)** | 120px wide (full wordmark); 48px wide (stacked) |
| **Print** | 30mm wide (full wordmark); 15mm wide (stacked) |

---

## 4. Concept C — "Code Bracket Mark"

### Description

An abstract symbol that merges **angle brackets** (`<` and `>`) — the universal signifiers of code — with the **letter F**, creating a mark that reads simultaneously as a code fragment and a personal initial. The left angle bracket serves double duty as the diagonal strokes of an uppercase F whose horizontals have been rotated into chevrons.

### Geometry Specification

| Parameter | Value |
|-----------|-------|
| **Overall proportions** | 1:1 square bounding box (64 × 64 units) |
| **Stroke weight** | 6 units |
| **Angle of chevrons** | 60° from horizontal (forming equilateral-triangle-based geometry) |
| **Left bracket vertex** | x = 8, y = 32 (pointing left, centered vertically) |
| **Right bracket vertex** | x = 56, y = 32 (pointing right, centered vertically) |
| **Bracket arm length** | 28 units along the hypotenuse |
| **F vertical stem** | x = 24, from y = 8 to y = 56 (48 units tall, 6 units wide) |
| **F top arm** | Replaced by the upper arm of the right angle bracket, extending from (24, 8) to (56, 32) at 60° — visually completing the F's top horizontal as a diagonal |
| **F middle arm** | A horizontal stroke from (24, 32) to (42, 32), 6 units tall — the only purely horizontal element, grounding the mark in letterform convention |
| **Corner treatment** | Mitered joins at chevron vertices; no rounding |

### Construction Method

1. Draw the left angle bracket: two strokes meeting at (8, 32), the upper arm extending to (22, 8) and the lower arm extending to (22, 56), each 6 units wide.
2. Draw the F's vertical stem: a 6-unit-wide rectangle from (24, 8) to (30, 56).
3. Draw the F's middle arm: a 6-unit-wide rectangle from (24, 29) to (42, 35).
4. Draw the right angle bracket's upper arm: from (30, 8) extending at 60° down to (56, 32), 6 units wide. This arm doubles as the F's top stroke.
5. Draw the right angle bracket's lower arm: from (56, 32) extending at 60° down to (30, 56), 6 units wide. This arm closes the bracket and frames the F.
6. The result: a left angle bracket, a vertical stem, a centered horizontal bar, and a right angle bracket whose arms originate from the top and bottom of the vertical stem. The composite reads as `<F>`.

### SVG Markup

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" width="128" height="128">
  <title>Flavio Fusuma — Code Bracket Mark</title>
  <desc>Abstract mark combining angle brackets with the letter F, symbolizing code and identity.</desc>
  <g fill="none" stroke="#1E3A5F" stroke-width="6" stroke-linecap="square" stroke-linejoin="miter">
    <!-- Left angle bracket -->
    <polyline points="22,8 8,32 22,56"/>
    <!-- F vertical stem -->
    <line x1="27" y1="8" x2="27" y2="56"/>
    <!-- F middle arm (horizontal) -->
    <line x1="27" y1="32" x2="42" y2="32"/>
    <!-- Right angle bracket (upper arm doubles as F top) -->
    <polyline points="30,8 56,32 30,56"/>
  </g>
</svg>
```

### Alternate Filled Version

For icon and favicon contexts, a filled variant collapses the stroked construction into solid shapes:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" width="128" height="128">
  <title>Flavio Fusuma — Code Bracket Mark (Filled)</title>
  <g fill="#1E3A5F" fill-rule="evenodd">
    <!-- Left bracket -->
    <polygon points="22,4 8,32 22,60 16,60 2,32 16,4"/>
    <!-- F vertical stem -->
    <rect x="24" y="4" width="6" height="56"/>
    <!-- F middle arm -->
    <rect x="24" y="29" width="18" height="6"/>
    <!-- Right bracket -->
    <polygon points="30,4 56,32 30,60 36,60 62,32 36,4"/>
  </g>
</svg>
```

### Proportional Grid & Clear Space

- **Clear space**: 1B (one bracket height, equal to the full mark height of 48 units in grid terms) on all sides
- **Preferred clear space**: 1.5B for hero and primary contexts
- The mark has inherent horizontal "air" due to the open bracket forms; do not reduce clear space to compensate

### Variations

| Variation | Description | Use Case |
|-----------|-------------|----------|
| **Full color** | Fusuma Blue `#1E3A5F` on white | Default usage |
| **Accent arm** | F middle arm and left bracket in amber `#F59E0B`, remainder in Fusuma Blue | Feature moments, developer-audience contexts |
| **Monochrome dark** | Black `#000000` on white | Single-color print |
| **Monochrome light** | White `#FFFFFF` on transparent | Dark backgrounds, terminal-style contexts |
| **Reversed** | White on Fusuma Blue | Reversed applications |
| **Reversed amber** | Amber on Fusuma Blue | Dark UI, dark mode |
| **Stroked** | 6-unit stroked version (primary) | General use |
| **Filled** | Solid filled version | Favicons, app icons, small sizes |

### Minimum Sizes

| Context | Minimum Size |
|---------|-------------|
| **Digital — stroked version** | 32 × 32 px |
| **Digital — filled version** | 16 × 16 px |
| **Print — stroked version** | 10 mm × 10 mm |
| **Print — filled version** | 6 mm × 6 mm |

---

## 5. Lockup System

Each concept supports a system of lockups — predetermined arrangements of mark + wordmark for different spatial contexts.

### Lockup Formats

| Lockup | Layout | Recommended Concept |
|--------|--------|-------------------|
| **Horizontal** | Mark left, wordmark right, vertically centered | All three |
| **Stacked** | Mark above, wordmark below, center-aligned | A, C |
| **Stacked left** | Mark above, wordmark below, left-aligned | B (natural text alignment) |
| **Mark only** | Symbol without wordmark | A, C |
| **Wordmark only** | Text without symbol | B |
| **Inline** | Mark at same optical size as text, used within running copy or UI | A, C (at small sizes) |

### Lockup Spacing

In horizontal lockups, the space between the mark and the wordmark is defined as **0.75F** (75% of the mark's height). This value ensures optical separation without disconnection.

In stacked lockups, the space between the mark's bottom edge and the wordmark's cap line (or ascender line for lowercase) is **0.5F**.

---

## 6. Concept Comparison

| Criterion | A: FF Monogram | B: Fusuma Wordmark | C: Code Bracket Mark |
|-----------|---------------|-------------------|---------------------|
| **Memorability** | High — symmetrical, iconic | Medium — relies on custom "f" detail | High — unique conceptual merge |
| **Scalability** | Excellent — simple geometry | Good — needs width for legibility | Very good — reads at small sizes (filled) |
| **Conceptual depth** | Initials as architecture | Name as craft object | Code as identity |
| **Versatility** | Works as icon and in lockups | Best as standalone wordmark | Works as icon and in lockups |
| **Developer audience resonance** | Moderate — abstract | Moderate — typographic | Strong — directly references code syntax |
| **Design audience resonance** | Strong — geometric, Bauhaus-adjacent | Strong — letterform craft | Moderate — leans technical |
| **Production complexity** | Low | Medium (requires type design) | Low |

### Recommendation

**Primary mark**: Concept A (FF Monogram) — for its versatility, memorability, and ability to function across the widest range of contexts from favicons to billboards.

**Secondary mark**: Concept C (Code Bracket Mark) — for developer-facing contexts, technical content, and situations where the code-identity connection should be explicit.

**Tertiary / signature**: Concept B (Fusuma Wordmark) — for formal contexts, email signatures, document headers, and anywhere the full name must be present as a designed element rather than set type.

---

## 7. Next Steps

1. **Refinement**: Advance the recommended primary concept (A) into high-fidelity vector production with precise optical corrections
2. **Testing**: Render all three concepts at target minimum sizes and on target backgrounds to validate legibility and reproduction
3. **Motion**: Define a simple animation sequence for the primary mark (entry, idle, exit) for use in video intros, loading states, and presentations
4. **User testing**: Present the three concepts to a representative sample of the target audience (CTOs, engineering managers, design leads) for qualitative feedback
5. **Finalization**: Produce the full lockup system, all variations, and all file formats as specified in `06-logo-usage-guidelines.md`
