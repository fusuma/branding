# Grid System

The Flavio Fusuma grid system is a 12-column layout framework with four breakpoints. It provides consistent structure across all viewports while enabling a wide range of layout compositions.

---

## Grid Specifications

### Breakpoints

| Name | Token | Min Width | Columns | Gutter | Margin | Container Max Width |
|---|---|---|---|---|---|---|
| Mobile | `breakpoint-sm` | 375px | 4 | 16px | 16px | 100% |
| Tablet | `breakpoint-md` | 768px | 8 | 24px | 32px | 100% |
| Desktop | `breakpoint-lg` | 1024px | 12 | 24px | 48px | 100% |
| Wide | `breakpoint-xl` | 1440px | 12 | 32px | auto (centered) | 1312px |

### Column Behavior

- **Mobile (375px)**: 4 columns. Most content spans all 4 columns. Side-by-side layouts use 2+2.
- **Tablet (768px)**: 8 columns. Allows more complex layouts: 4+4, 3+5, 6+2, etc.
- **Desktop (1024px)**: Full 12-column grid. All layout patterns are available.
- **Wide (1440px)**: 12 columns within a centered, max-width container. Extra viewport space becomes margin.

### Column Width Calculations

Column widths are fluid within each breakpoint. The formula:

```
column-width = (container-width - (columns - 1) * gutter - 2 * margin) / columns
```

| Breakpoint | Container | Margin | Gutter | Columns | Column Width (approx) |
|---|---|---|---|---|---|
| Mobile (375px) | 375px | 16px | 16px | 4 | 73.75px |
| Tablet (768px) | 768px | 32px | 24px | 8 | 67px |
| Desktop (1024px) | 1024px | 48px | 24px | 12 | 54.67px |
| Wide (1440px) | 1312px | 0 (auto) | 32px | 12 | 80.33px |

---

## Common Layouts

### Single Column (12)

Full-width content. Used for article text, hero sections, and full-bleed media.

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
|---------------------------------------------------------------------|
|                         Content (span 12)                            |
|---------------------------------------------------------------------|
```

Mobile: spans all 4 columns.

### Two Column Equal (6 + 6)

Side-by-side content with equal weight. Comparison views, feature pairs.

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
|-------------------------------|-------------------------------|
|       Left (span 6)          |       Right (span 6)          |
|-------------------------------|-------------------------------|
```

Mobile: stacks to 4 + 4 (full width each).
Tablet: 4 + 4 columns.

### Three Column Equal (4 + 4 + 4)

Card grids, feature lists, pricing tables.

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
|-------------------|-------------------|-------------------|
|  Col A (span 4)   |  Col B (span 4)   |  Col C (span 4)   |
|-------------------|-------------------|-------------------|
```

Mobile: stacks to single column (4 each).
Tablet: 4 + 4 (two per row, third wraps).

### Sidebar + Content (3 + 9)

Navigation sidebar with main content area. Settings pages, documentation.

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
|------------|--------------------------------------------------|
| Nav (3)    |              Content (span 9)                    |
|------------|--------------------------------------------------|
```

Mobile: sidebar collapses to a hamburger menu or top nav; content spans 4.
Tablet: sidebar becomes a collapsible drawer or spans 2 columns; content spans 6.

### Content + Aside (8 + 4)

Article with sidebar. Blog posts, product pages with related items.

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
|-----------------------------------------|-------------------|
|          Content (span 8)               | Aside (span 4)    |
|-----------------------------------------|-------------------|
```

Mobile: aside moves below content; both span 4.
Tablet: content spans 5, aside spans 3.

### Centered Content (offset)

Centered article text for readability. Uses columns 3-10 (8 columns centered).

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
|     |     |-----------------------------------------|     |     |
|           |      Centered Content (span 8)          |           |
|     |     |-----------------------------------------|     |     |
```

Mobile: spans all 4 columns.
Tablet: spans all 8 columns.

---

## Nesting

Grids can be nested inside any column span. The nested grid creates a new 12-column context within its parent.

### Rules for Nesting

1. The nested grid inherits the parent's gutter size.
2. Do not nest more than 2 levels deep. If you need 3+ levels, reconsider the layout.
3. Nested grids do not add their own outer margin -- the parent column's padding provides spacing.

### Example: Cards Inside a 9-Column Content Area

```
Parent Grid (12 columns):
|--- Nav (3) ---|--- Content (9) -----------------------------------------|

Nested Grid inside Content (12 columns within the 9-column span):
                |--- Card (4) ---|--- Card (4) ---|--- Card (4) ---|
```

```css
.content-area {
  grid-column: span 9;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--grid-gutter);
}

.content-area .card {
  grid-column: span 4;
}
```

---

## CSS Grid Implementation

### Base Grid Container

```css
:root {
  --grid-columns: 12;
  --grid-gutter: 24px;
  --grid-margin: 48px;
  --grid-max-width: 1312px;
}

@media (max-width: 767px) {
  :root {
    --grid-columns: 4;
    --grid-gutter: 16px;
    --grid-margin: 16px;
  }
}

@media (min-width: 768px) and (max-width: 1023px) {
  :root {
    --grid-columns: 8;
    --grid-gutter: 24px;
    --grid-margin: 32px;
  }
}

@media (min-width: 1440px) {
  :root {
    --grid-gutter: 32px;
    --grid-margin: 0px; /* Container handles centering */
  }
}
```

### Grid Container

```css
.grid-container {
  width: 100%;
  max-width: var(--grid-max-width);
  margin-left: auto;
  margin-right: auto;
  padding-left: var(--grid-margin);
  padding-right: var(--grid-margin);
}
```

### Grid Layout

```css
.grid {
  display: grid;
  grid-template-columns: repeat(var(--grid-columns), 1fr);
  gap: var(--grid-gutter);
}
```

### Column Span Utilities

```css
/* Auto-generated span classes for each breakpoint */
.col-span-1  { grid-column: span 1; }
.col-span-2  { grid-column: span 2; }
.col-span-3  { grid-column: span 3; }
.col-span-4  { grid-column: span 4; }
.col-span-5  { grid-column: span 5; }
.col-span-6  { grid-column: span 6; }
.col-span-7  { grid-column: span 7; }
.col-span-8  { grid-column: span 8; }
.col-span-9  { grid-column: span 9; }
.col-span-10 { grid-column: span 10; }
.col-span-11 { grid-column: span 11; }
.col-span-12 { grid-column: span 12; }

/* Responsive span overrides */
@media (min-width: 768px) {
  .md\:col-span-1  { grid-column: span 1; }
  .md\:col-span-2  { grid-column: span 2; }
  .md\:col-span-3  { grid-column: span 3; }
  .md\:col-span-4  { grid-column: span 4; }
  .md\:col-span-5  { grid-column: span 5; }
  .md\:col-span-6  { grid-column: span 6; }
  .md\:col-span-7  { grid-column: span 7; }
  .md\:col-span-8  { grid-column: span 8; }
}

@media (min-width: 1024px) {
  .lg\:col-span-1  { grid-column: span 1; }
  .lg\:col-span-2  { grid-column: span 2; }
  .lg\:col-span-3  { grid-column: span 3; }
  .lg\:col-span-4  { grid-column: span 4; }
  .lg\:col-span-5  { grid-column: span 5; }
  .lg\:col-span-6  { grid-column: span 6; }
  .lg\:col-span-7  { grid-column: span 7; }
  .lg\:col-span-8  { grid-column: span 8; }
  .lg\:col-span-9  { grid-column: span 9; }
  .lg\:col-span-10 { grid-column: span 10; }
  .lg\:col-span-11 { grid-column: span 11; }
  .lg\:col-span-12 { grid-column: span 12; }
}

@media (min-width: 1440px) {
  .xl\:col-span-1  { grid-column: span 1; }
  .xl\:col-span-2  { grid-column: span 2; }
  .xl\:col-span-3  { grid-column: span 3; }
  .xl\:col-span-4  { grid-column: span 4; }
  .xl\:col-span-5  { grid-column: span 5; }
  .xl\:col-span-6  { grid-column: span 6; }
  .xl\:col-span-7  { grid-column: span 7; }
  .xl\:col-span-8  { grid-column: span 8; }
  .xl\:col-span-9  { grid-column: span 9; }
  .xl\:col-span-10 { grid-column: span 10; }
  .xl\:col-span-11 { grid-column: span 11; }
  .xl\:col-span-12 { grid-column: span 12; }
}
```

### Column Start (Offset) Utilities

```css
.col-start-1  { grid-column-start: 1; }
.col-start-2  { grid-column-start: 2; }
.col-start-3  { grid-column-start: 3; }
.col-start-4  { grid-column-start: 4; }
.col-start-5  { grid-column-start: 5; }
.col-start-6  { grid-column-start: 6; }
.col-start-7  { grid-column-start: 7; }

/* Same responsive pattern with md:, lg:, xl: prefixes */
```

### Full Layout Examples

#### Sidebar + Content (Responsive)

```html
<div class="grid-container">
  <div class="grid">
    <nav class="col-span-4 lg:col-span-3">
      <!-- Sidebar navigation -->
    </nav>
    <main class="col-span-4 lg:col-span-9">
      <!-- Main content -->
    </main>
  </div>
</div>
```

```css
/* Mobile: nav and main each take full width (4/4), stack vertically */
/* Tablet: nav and main each take full width (8/8), stack vertically */
/* Desktop+: nav takes 3, main takes 9 */

@media (max-width: 1023px) {
  nav {
    grid-column: 1 / -1; /* Full width */
  }
  main {
    grid-column: 1 / -1;
  }
}
```

#### Three Cards (Responsive)

```html
<div class="grid-container">
  <div class="grid">
    <div class="col-span-4 md:col-span-4 lg:col-span-4">Card 1</div>
    <div class="col-span-4 md:col-span-4 lg:col-span-4">Card 2</div>
    <div class="col-span-4 md:col-span-8 lg:col-span-4">Card 3</div>
  </div>
</div>
```

Mobile: each card full width, stacked.
Tablet: cards 1-2 side by side (4+4), card 3 on next row (8 columns).
Desktop: all three side by side (4+4+4).

---

## Design Tokens

```css
:root {
  /* Grid */
  --grid-columns-sm: 4;
  --grid-columns-md: 8;
  --grid-columns-lg: 12;
  --grid-columns-xl: 12;

  --grid-gutter-sm: 16px;
  --grid-gutter-md: 24px;
  --grid-gutter-lg: 24px;
  --grid-gutter-xl: 32px;

  --grid-margin-sm: 16px;
  --grid-margin-md: 32px;
  --grid-margin-lg: 48px;
  --grid-margin-xl: 0px;   /* Centered with max-width */

  --grid-max-width: 1312px;
}
```

---

## Guidelines

### Do

- Use the grid for all page-level layouts.
- Let content span the full column count on mobile (4/4).
- Use `gap` for gutters; do not manually add margin between columns.
- Align content to grid lines -- not between them.

### Don't

- Do not create breakpoints outside the four defined ones.
- Do not use percentage-based widths that bypass the grid.
- Do not add extra margin or padding that conflicts with grid gutters.
- Do not nest grids more than 2 levels deep.
- Do not mix grid and flexbox for the same layout axis (use one or the other per axis).
