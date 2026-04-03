# Responsive Design Strategy

This document defines the Flavio Fusuma approach to responsive design: breakpoint definitions, the mobile-first methodology, container behavior, and how components and layouts adapt across viewport sizes.

---

## Core Principles

1. **Mobile-first**: Base styles target the smallest viewport. Larger viewports are handled with `min-width` media queries that add complexity.
2. **Content-driven breakpoints**: The four system breakpoints are chosen based on common device classes, but individual components may reflow within these ranges based on available space.
3. **Fluid within steps**: Between breakpoints, layouts are fluid (percentage-based columns, flexible containers). At each breakpoint, structural changes (column count, layout direction) may occur.
4. **Progressive enhancement**: Essential content and functionality are available on every viewport. Enhanced layouts and additional features appear as space permits.

---

## Breakpoint Definitions

| Name | Token | Min Width | Target Devices | Grid Columns |
|---|---|---|---|---|
| **Mobile** | `breakpoint-sm` | 0px (default) | Phones, small devices | 4 |
| **Tablet** | `breakpoint-md` | 768px | Tablets (portrait), large phones (landscape) | 8 |
| **Desktop** | `breakpoint-lg` | 1024px | Laptops, tablets (landscape), desktops | 12 |
| **Wide** | `breakpoint-xl` | 1440px | Large desktops, external monitors | 12 |

### CSS Media Queries

```css
/* Mobile-first: no media query needed for base (mobile) styles */

/* Tablet and up */
@media (min-width: 768px) { /* ... */ }

/* Desktop and up */
@media (min-width: 1024px) { /* ... */ }

/* Wide and up */
@media (min-width: 1440px) { /* ... */ }
```

### When to Use Each Breakpoint

| Breakpoint | Structural Changes |
|---|---|
| Mobile (default) | Single-column layouts, stacked content, hamburger navigation, full-width cards |
| Tablet (768px) | Two-column layouts become possible, side-by-side cards, expanded navigation (optional), wider form fields |
| Desktop (1024px) | Full 12-column grid, sidebar navigation, multi-column content, hover states become relevant |
| Wide (1440px) | Content container becomes fixed-width (1312px) and centers, font sizes reach maximum, generous whitespace |

---

## Fluid vs. Fixed

### Fluid Elements

These elements scale proportionally between breakpoints:

| Element | Behavior |
|---|---|
| Grid columns | Percentage-based within the container |
| Images and media | `max-width: 100%; height: auto` |
| Container width | 100% of viewport (minus margins) up to max-width |
| Gutters | Fixed at each breakpoint but change at breakpoint boundaries |

### Fixed Elements

These elements use fixed values that may change at breakpoints but do not scale between them:

| Element | Behavior |
|---|---|
| Font sizes | Stepped at breakpoints (see type scale) |
| Spacing tokens | Fixed values (`space-3` is always 24px) |
| Grid margins | Fixed per breakpoint (16px, 32px, 48px, auto) |
| Icon sizes | Fixed per designated size (16px, 20px, 24px) |
| Min touch targets | Always 44px minimum |

### Container Widths

| Breakpoint | Container Behavior | Max Width |
|---|---|---|
| Mobile | 100% - 32px (16px margin each side) | None |
| Tablet | 100% - 64px (32px margin each side) | None |
| Desktop | 100% - 96px (48px margin each side) | None |
| Wide | Centered, fixed max-width | 1312px |

```css
.container {
  width: 100%;
  max-width: var(--grid-max-width); /* 1312px */
  margin-left: auto;
  margin-right: auto;
  padding-left: var(--grid-margin);
  padding-right: var(--grid-margin);
}
```

---

## Mobile-First Approach

### Writing CSS

Always start with mobile styles as the default. Layer on complexity for larger screens.

```css
/* Mobile: single column, stacked */
.feature-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-2); /* 16px */
}

/* Tablet: two columns */
@media (min-width: 768px) {
  .feature-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: var(--space-3); /* 24px */
  }
}

/* Desktop: three columns */
@media (min-width: 1024px) {
  .feature-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

### Decision Framework

When designing a component or layout, answer these questions in order:

1. **What is essential on mobile?** Start here. This is the base.
2. **What can be added with more horizontal space?** Side-by-side layouts, additional columns, sidebar panels.
3. **What benefits from even more space?** Increased font sizes, more generous whitespace, additional content visible without scrolling.
4. **Is anything mobile-only?** Bottom navigation bars, swipe interactions, hamburger menus that convert to full nav on desktop.

---

## Component Responsive Behavior

### Navigation

| Breakpoint | Behavior |
|---|---|
| Mobile | Hamburger icon triggers a full-screen or slide-in overlay menu. Logo and 1-2 action icons visible. |
| Tablet | Hamburger may persist, or primary nav items become visible. Secondary items in overflow menu. |
| Desktop | Full horizontal navigation bar. All primary and secondary items visible. Dropdowns on hover/click. |
| Wide | Same as desktop with increased spacing between items. |

### Cards

| Breakpoint | Behavior |
|---|---|
| Mobile | Full-width cards, stacked vertically. Padding: `space-2` (16px). |
| Tablet | Two cards per row. Padding: `space-3` (24px). |
| Desktop | Three or four cards per row depending on content. Padding: `space-3` (24px). |
| Wide | Same column count as desktop, increased gutters. Padding: `space-4` (32px). |

### Tables

| Breakpoint | Behavior |
|---|---|
| Mobile | Convert to stacked card layout (each row becomes a card) or enable horizontal scroll. |
| Tablet | Show essential columns; hide secondary columns behind an expand/detail action. |
| Desktop | Full table with all columns visible. |
| Wide | Same as desktop; extra space absorbed by the widest or last column. |

```css
/* Mobile: stacked cards */
.data-table {
  display: block;
}
.data-table tr {
  display: block;
  padding: var(--space-2);
  border-bottom: 1px solid var(--color-border-subtle);
}
.data-table td {
  display: flex;
  justify-content: space-between;
  padding: var(--space-0-5) 0;
}
.data-table td::before {
  content: attr(data-label);
  font-weight: 600;
}

/* Desktop: standard table */
@media (min-width: 1024px) {
  .data-table {
    display: table;
  }
  .data-table tr {
    display: table-row;
    padding: 0;
  }
  .data-table td {
    display: table-cell;
    padding: var(--space-1-5) var(--space-2);
  }
  .data-table td::before {
    display: none;
  }
}
```

### Forms

| Breakpoint | Behavior |
|---|---|
| Mobile | Single-column form. Full-width inputs. Labels above inputs. |
| Tablet | Optional two-column layout for short fields (first name + last name). |
| Desktop | Wider form with max-width (~640px). Two-column layout for related short fields. |
| Wide | Same as desktop, centered in content area. |

### Modals and Dialogs

| Breakpoint | Behavior |
|---|---|
| Mobile | Full-screen overlay (100vw x 100vh). Slide up from bottom. |
| Tablet | Centered modal, max-width 560px, vertical margin auto. |
| Desktop | Centered modal, max-width 640px. |
| Wide | Same as desktop. |

### Sidebars

| Breakpoint | Behavior |
|---|---|
| Mobile | Hidden by default. Accessible via hamburger or swipe gesture. Overlays content when open. |
| Tablet | Collapsible sidebar (icon-only rail at 64px, expanded at 240px). |
| Desktop | Persistent sidebar at 240px-280px. Content area fills remaining space. |
| Wide | Same as desktop; sidebar may expand to 300px if content warrants it. |

---

## Layout Patterns Per Breakpoint

### Mobile (0 - 767px)

```
+---------------------------+
|  [Logo]    [Menu] [Action]|  <- Top bar, compact
+---------------------------+
|                           |
|  [Full-width content]     |  <- Single column
|                           |
|  [Card]                   |  <- Stacked cards
|  [Card]                   |
|  [Card]                   |
|                           |
+---------------------------+
|  [Tab Bar / Bottom Nav]   |  <- Mobile navigation (optional)
+---------------------------+
```

### Tablet (768px - 1023px)

```
+-------------------------------------------+
|  [Logo]   [Nav Item] [Nav Item]   [Action]|  <- Expanded top nav
+-------------------------------------------+
|                                           |
|  [Card]          [Card]                   |  <- Two-column cards
|  [Card]          [Card]                   |
|                                           |
|  [Full-width content section]             |
|                                           |
+-------------------------------------------+
```

### Desktop (1024px - 1439px)

```
+----------------------------------------------------------+
|  [Logo]  [Nav] [Nav] [Nav] [Nav]           [Search] [User]|
+----------------------------------------------------------+
|  [Sidebar]  |  [Main Content Area]                        |
|  [Nav]      |  [Card]  [Card]  [Card]                     |
|  [Nav]      |                                             |
|  [Nav]      |  [Content section]                          |
|             |                                             |
+----------------------------------------------------------+
```

### Wide (1440px+)

```
                    |<-- 1312px max-width container -->|
+------+------------+----------------------------------+-----+------+
|      |  [Sidebar] |  [Main Content Area]             |     |      |
| auto |  240px     |  [Card]   [Card]   [Card]        |     | auto |
|margin|            |                                  |     |margin|
|      |            |  [Spacious content section]      |     |      |
+------+------------+----------------------------------+-----+------+
```

---

## Images and Media

### Responsive Images

```html
<picture>
  <source media="(min-width: 1024px)" srcset="hero-desktop.webp">
  <source media="(min-width: 768px)" srcset="hero-tablet.webp">
  <img src="hero-mobile.webp" alt="Hero image" loading="lazy">
</picture>
```

### Aspect Ratio Containers

Use `aspect-ratio` to maintain proportions across breakpoints:

```css
.media-container {
  width: 100%;
  aspect-ratio: 16 / 9;
  overflow: hidden;
}

.media-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

### Video Embeds

```css
.video-embed {
  width: 100%;
  aspect-ratio: 16 / 9;
}

.video-embed iframe {
  width: 100%;
  height: 100%;
  border: 0;
}
```

---

## Touch and Interaction Considerations

### Touch Targets

All interactive elements must have a minimum touch target of 44x44 CSS pixels on all viewports. This applies even if the visible element is smaller (use padding or `min-height` / `min-width`).

```css
.touch-target {
  min-height: 44px;
  min-width: 44px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}
```

### Hover vs. Touch

- **Mobile/Tablet**: No hover states. Interactions are tap-based. Dropdowns open on tap, not hover.
- **Desktop/Wide**: Hover states provide visual feedback. Dropdowns can open on hover (with click fallback).

```css
/* Hover only on devices that support it */
@media (hover: hover) and (pointer: fine) {
  .button:hover {
    background-color: var(--color-interactive-hover);
  }
}
```

### Scroll Behavior

- Smooth scroll for anchor links within a page.
- Overscroll containment on modals and drawers to prevent background scrolling.

```css
html {
  scroll-behavior: smooth;
}

.modal-body {
  overscroll-behavior: contain;
}
```

---

## Testing Requirements

### Viewport Testing Matrix

| Viewport | Width | Represents |
|---|---|---|
| Small phone | 320px | iPhone SE, older Android |
| Standard phone | 375px | iPhone 12/13/14, Pixel |
| Large phone | 428px | iPhone 14 Pro Max |
| Small tablet | 768px | iPad Mini, standard tablets |
| Large tablet | 1024px | iPad Pro, surface |
| Laptop | 1280px | Common laptop resolution |
| Desktop | 1440px | Standard external monitor |
| Large desktop | 1920px | Full HD monitor |

### Checklist

- [ ] Content is accessible and readable at every viewport from 320px to 1920px.
- [ ] No horizontal scrollbar appears at any viewport width (except intentional horizontal scroll regions).
- [ ] Touch targets are at least 44x44px on mobile and tablet viewports.
- [ ] Navigation is accessible on all viewports (hamburger on mobile, full nav on desktop).
- [ ] Tables are usable on mobile (stacked cards or horizontal scroll with visual indicator).
- [ ] Forms are usable on mobile (full-width inputs, labels above fields).
- [ ] Modals do not overflow the viewport on any screen size.
- [ ] Images scale appropriately and do not cause layout shift (use `aspect-ratio` or explicit dimensions).
- [ ] Text remains readable at 200% browser zoom on all breakpoints.
- [ ] No content is hidden permanently on mobile -- it must be accessible via interaction (expand, scroll, navigate).
