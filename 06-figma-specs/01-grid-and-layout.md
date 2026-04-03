# Grid and Layout

> Figma grid configuration, frame sizes, responsive behavior, and layout strategy for the Flavio Fusuma Design System.

---

## Breakpoints and Frame Sizes

All designs target four breakpoints. Each breakpoint has a corresponding Figma frame width. Frame heights are set to "Hug contents" unless creating a fixed-viewport prototype.

| Breakpoint | Token Name | Frame Width | Min Viewport | Max Viewport | Typical Device |
|---|---|---|---|---|---|
| Mobile | `breakpoint-sm` | 375px | 320px | 479px | iPhone SE / 14 / 15 |
| Tablet | `breakpoint-md` | 768px | 480px | 1023px | iPad Mini / Air |
| Desktop | `breakpoint-lg` | 1024px | 1024px | 1439px | Laptop / small monitor |
| Desktop Wide | `breakpoint-xl` | 1440px | 1440px | -- | Large monitor / iMac |

### Additional Frame Sizes

| Purpose | Width | Notes |
|---|---|---|
| Social preview (OG image) | 1200x630 | Used in `FF - Brand & Marketing` |
| Favicon artboard | 512x512 | Master favicon; exported at 16, 32, 180, 192, 512 |
| Icon grid | 24x24 | Standard icon canvas at 1x |
| Presentation slide | 1920x1080 | Stakeholder decks |

---

## Grid System

The Flavio Fusuma design system uses a 12-column grid across all breakpoints with adjusted gutters and margins.

### Column Grid Configuration

| Breakpoint | Columns | Column Width | Gutter | Margin (each side) | Content Width |
|---|---|---|---|---|---|
| Mobile (375px) | 4 | Fluid (fill) | 16px | 16px | 343px |
| Tablet (768px) | 8 | Fluid (fill) | 24px | 32px | 704px |
| Desktop (1024px) | 12 | Fluid (fill) | 24px | 48px | 928px |
| Desktop Wide (1440px) | 12 | 72px (fixed) | 24px | 156px | 1128px |

### Figma Layout Grid Setup

Apply layout grids to each top-level frame. In Figma, open the frame properties panel and add a layout grid with these settings.

#### Mobile (375px)

```
Type:        Columns
Count:       4
Width:       Fill (stretch)
Gutter:      16
Margin:      16
Alignment:   Stretch
Color:       #2563EB at 10% opacity
```

#### Tablet (768px)

```
Type:        Columns
Count:       8
Width:       Fill (stretch)
Gutter:      24
Margin:      32
Alignment:   Stretch
Color:       #2563EB at 10% opacity
```

#### Desktop (1024px)

```
Type:        Columns
Count:       12
Width:       Fill (stretch)
Gutter:      24
Margin:      48
Alignment:   Stretch
Color:       #2563EB at 10% opacity
```

#### Desktop Wide (1440px)

```
Type:        Columns
Count:       12
Width:       72 (fixed)
Gutter:      24
Margin:      156
Alignment:   Center
Color:       #2563EB at 10% opacity
```

### Baseline Grid (Optional Overlay)

For vertical rhythm verification, add a secondary row grid:

```
Type:        Rows
Height:      8
Gutter:      0
Offset:      0
Color:       #F59E0B at 5% opacity
```

This 8px baseline grid overlay confirms that all spacing adheres to the 8px spatial scale.

---

## Responsive Column Mapping

Components span different column counts depending on the breakpoint. This table defines the most common content-width patterns.

### Full-Width Content

| Breakpoint | Columns Spanned | Effective Width |
|---|---|---|
| Mobile | 4 / 4 | 343px |
| Tablet | 8 / 8 | 704px |
| Desktop | 12 / 12 | 928px |
| Desktop Wide | 12 / 12 | 1128px |

### Two-Column Layout (equal)

| Breakpoint | Left Columns | Right Columns | Gap |
|---|---|---|---|
| Mobile | 4 (stacked) | 4 (stacked) | 24px vertical |
| Tablet | 4 | 4 | 24px |
| Desktop | 6 | 6 | 24px |
| Desktop Wide | 6 | 6 | 24px |

### Sidebar + Main Content

| Breakpoint | Sidebar | Main | Gap |
|---|---|---|---|
| Mobile | Hidden (off-canvas) | 4 | -- |
| Tablet | Hidden (off-canvas) | 8 | -- |
| Desktop | 3 | 9 | 24px |
| Desktop Wide | 3 | 9 | 24px |

### Three-Column Card Grid

| Breakpoint | Cards Per Row | Columns Per Card | Gap |
|---|---|---|---|
| Mobile | 1 | 4 | 24px vertical |
| Tablet | 2 | 4 | 24px |
| Desktop | 3 | 4 | 24px |
| Desktop Wide | 3 | 4 | 24px |

---

## Max-Width Container

All page content lives inside a max-width container to prevent content from stretching too wide on large screens.

| Property | Value |
|---|---|
| Max width | 1128px |
| Horizontal centering | `margin: 0 auto` (CSS) / Center alignment in Figma |
| Background | Full-bleed (extends behind max-width container) |

In Figma, create a frame named `container` inside each breakpoint frame. Set its width constraint to "Fill container" with a max width of 1128px and alignment set to center.

---

## Constraints and Responsive Behavior

### Constraint Rules

Constraints define how layers behave when their parent frame is resized. Use these rules when auto-layout is not applicable.

| Element Type | Left | Right | Top | Bottom | Notes |
|---|---|---|---|---|---|
| Full-width content | ✓ | ✓ | ✓ | -- | Stretches horizontally |
| Centered content | Center | Center | ✓ | -- | Stays centered on resize |
| Fixed sidebar | ✓ | -- | ✓ | ✓ | Left-pinned, full height |
| Sticky header | ✓ | ✓ | ✓ | -- | Top-pinned, full width |
| FAB (floating action button) | -- | ✓ | -- | ✓ | Bottom-right corner |
| Modal overlay | Center | Center | Center | Center | Always centered |
| Background image | ✓ | ✓ | ✓ | ✓ | Fill (scale) with "Fill" fit |

### Resizing Behavior by Component

| Component | Width | Height | Notes |
|---|---|---|---|
| Button | Hug or Fixed | Fixed (by size token) | Hug for text-driven width; fixed for icon-only |
| Input | Fill container | Fixed (by size token) | Always stretches to parent |
| Card | Fill container | Hug contents | Width determined by grid column; height by content |
| Navigation bar | Fill container | Fixed 64px | Full width, fixed height |
| Modal | Fixed (480px / 640px) | Hug contents | Centered with max-height constraint |
| Sidebar | Fixed 280px | Fill container | Fixed width, stretches vertically |
| Badge | Hug contents | Hug contents | Sized by text content |
| Avatar | Fixed | Fixed | Always square (32/40/48/64/96px) |

---

## Auto-Layout vs. Constraints Decision Guide

Choose auto-layout as the default approach. Fall back to constraints only when auto-layout cannot express the behavior.

### Use Auto-Layout When

- Content flows in a single direction (row or column)
- Items need consistent spacing between them
- The container should grow or shrink with its content
- You need padding inside a container
- The component will be reused and needs predictable behavior
- Building any component (buttons, cards, inputs, list items, nav bars)

### Use Constraints When

- An element must be pinned to a specific corner or edge
- An element floats over other content (FAB, tooltip arrow, badge on avatar)
- Background layers need to fill the frame on resize
- Decorative elements must maintain a fixed position relative to an edge
- Building full-page layouts with overlapping layers

### Hybrid Approach

For templates and page-level frames, use a hybrid:

1. **Outer frame**: Constraints for pinning the header, sidebar, and FAB.
2. **Content containers inside the outer frame**: Auto-layout for stacking sections.
3. **Components inside content containers**: Auto-layout for internal spacing.

```
Template Frame (constraints)
├── header (left+right+top constraint)
│   └── header-content (auto-layout horizontal)
├── sidebar (left+top+bottom constraint, fixed width)
│   └── nav-items (auto-layout vertical)
├── main-content (left=sidebar-width, right, top=header-height, bottom)
│   └── content-stack (auto-layout vertical)
│       ├── hero-section (auto-layout vertical)
│       ├── card-grid (auto-layout horizontal, wrap)
│       └── footer (auto-layout vertical)
└── fab (right+bottom constraint)
```

---

## Spacing Integration

All spacing values in grids and layouts reference the 8px spatial scale:

| Token | Value | Usage in Grid/Layout |
|---|---|---|
| `space-2` | 16px | Mobile gutter, mobile margin |
| `space-3` | 24px | Tablet/desktop gutter, card gap, section stacking (small) |
| `space-4` | 32px | Tablet margin |
| `space-6` | 48px | Desktop margin |
| `space-8` | 64px | Section vertical spacing (medium) |
| `space-10` | 80px | Sub-section spacing in Figma documentation |
| `space-12` | 96px | Page-level section spacing |
| `space-16` | 128px | Hero section vertical padding |
| `space-20` | 160px | Section spacing in Figma documentation (between component sections) |

---

## Figma Layout Grid Styles

Save the following as shared layout grid styles in the `FF - Foundations` library so designers can apply them with a single click.

| Style Name | Configuration |
|---|---|
| `Grid / Mobile / 4-col` | 4 columns, 16px gutter, 16px margin, stretch |
| `Grid / Tablet / 8-col` | 8 columns, 24px gutter, 32px margin, stretch |
| `Grid / Desktop / 12-col` | 12 columns, 24px gutter, 48px margin, stretch |
| `Grid / Desktop Wide / 12-col` | 12 columns, 24px gutter, center, 72px fixed width |
| `Grid / Baseline / 8px` | Rows, 8px height, 0 gutter, 0 offset |

---

## Common Layout Templates

These frame templates should be available as library components for quick page scaffolding.

### Single-Column Centered

```
┌─────────────────────────────────────────────┐
│ margin │         content          │ margin  │
│        │     (max 1128px)         │         │
│        │     centered             │         │
└─────────────────────────────────────────────┘
```

### Two-Column Equal

```
┌──────────────────────────────────────────────┐
│ margin │  col-left  │ gutter │ col-right │ m │
│        │  (6 cols)  │  24px  │ (6 cols)  │   │
└──────────────────────────────────────────────┘
```

### Sidebar + Main

```
┌────────────────────────────────────────────────────┐
│ margin │ sidebar │ gutter │     main      │ margin │
│        │ (3 col) │  24px  │   (9 col)     │        │
│        │ fixed   │        │   fluid       │        │
└────────────────────────────────────────────────────┘
```

### Three-Column Card Grid

```
┌──────────────────────────────────────────────────────────┐
│ margin │ card-1  │ gap │ card-2  │ gap │ card-3  │ margin│
│        │ (4 col) │24px │ (4 col) │24px │ (4 col) │       │
└──────────────────────────────────────────────────────────┘
```
