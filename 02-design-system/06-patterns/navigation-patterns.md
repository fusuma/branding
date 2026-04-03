# Navigation Patterns

## Overview

Navigation patterns define how users move through the flaviofusuma.com experience. Every navigation element should be predictable, accessible, and responsive — guiding users to their destination with minimal friction.

---

## 1. Top Navbar

The primary navigation pattern for the website. Persistent across all pages.

### Structure

```
┌─────────────────────────────────────────────────────────────┐
│ [Logo]          [Nav Items...]              [CTA Button]    │
└─────────────────────────────────────────────────────────────┘
```

### Specifications

| Property | Desktop (≥1024px) | Tablet (768–1023px) | Mobile (<768px) |
|----------|-------------------|---------------------|-----------------|
| Height | 64px | 56px | 56px |
| Position | `sticky`, top: 0 | `sticky`, top: 0 | `sticky`, top: 0 |
| Background | `neutral-0` / transparent | `neutral-0` | `neutral-0` |
| Shadow | On scroll: `shadow-sm` | On scroll: `shadow-sm` | `shadow-sm` |
| Z-index | 50 | 50 | 50 |
| Padding | 0 `space-6` | 0 `space-4` | 0 `space-4` |

### Nav Items

| State | Text Color | Indicator |
|-------|-----------|-----------|
| Default | `neutral-600` | None |
| Hover | `blue-600` | None |
| Active (current page) | `blue-700` | 2px bottom border `blue-600` |
| Focus | `blue-600` | Focus ring |

### Behavior

- **Scroll**: Background transitions from transparent to solid with shadow after 32px scroll
- **Active page**: Indicated by bottom border and bolder weight (600)
- **CTA**: Always visible as the rightmost element, styled as primary button (sm)
- **Logo**: Links to homepage, min-width 120px

### Responsive Transformation

```
Desktop:    [Logo]  [Work] [About] [Blog] [Contact]  [Let's Talk]
Tablet:     [Logo]  [Work] [About] [Blog]  [☰]
Mobile:     [Logo]                          [☰]
```

---

## 2. Mobile Navigation (Hamburger Menu)

### Trigger
- Hamburger icon (☰) at 24×24px, right-aligned
- Transforms to close icon (✕) when open
- Animation: 300ms ease-in-out rotation

### Overlay Panel

```
┌─────────────────────────────────┐
│ [Logo]                    [✕]   │
├─────────────────────────────────┤
│                                 │
│   Work                          │
│   About                         │
│   Blog                          │
│   Contact                       │
│                                 │
│   ┌───────────────────────┐     │
│   │    Let's Talk          │     │
│   └───────────────────────┘     │
│                                 │
│   [Social Icons]                │
└─────────────────────────────────┘
```

| Property | Value |
|----------|-------|
| Width | 100vw |
| Height | 100vh |
| Background | `neutral-0` |
| Animation | Slide in from right, 300ms ease |
| Nav item size | 24px, weight 600 |
| Nav item spacing | `space-6` between items |
| Overlay | `neutral-900` at 50% opacity (behind panel) |

### Accessibility
- Focus trap within menu when open
- `Escape` closes the menu
- `aria-expanded` on hamburger button
- `role="navigation"` on the menu container
- Focus returns to hamburger button on close

---

## 3. Sidebar Navigation

For documentation or blog sections with deep content hierarchy.

### Structure

```
┌──────────┬──────────────────────────────┐
│ Sidebar  │ Content                       │
│          │                               │
│ Section  │                               │
│  ├ Item  │                               │
│  ├ Item  │                               │
│  └ Item  │                               │
│          │                               │
│ Section  │                               │
│  ├ Item  │                               │
│  └ Item  │                               │
└──────────┴──────────────────────────────┘
```

| Property | Value |
|----------|-------|
| Width | 256px (fixed) |
| Background | `neutral-50` |
| Border right | 1px solid `neutral-200` |
| Position | `sticky`, top: 80px (below navbar) |
| Max height | `calc(100vh - 80px)` |
| Overflow | `auto` with custom scrollbar |

### Section Headers
- Font: 11px, weight 600, uppercase, letter-spacing 0.05em
- Color: `neutral-400`
- Margin bottom: `space-2`

### Nav Items
| State | Background | Text | Left Border |
|-------|-----------|------|-------------|
| Default | transparent | `neutral-600` | none |
| Hover | `neutral-100` | `neutral-800` | none |
| Active | `blue-50` | `blue-700` | 2px solid `blue-600` |
| Focus | transparent | `neutral-800` | focus ring |

### Responsive
- **<1024px**: Sidebar collapses to hamburger/drawer
- **Drawer**: Slides in from left, same overlay pattern as mobile nav

---

## 4. Breadcrumb Navigation

For hierarchical page structures (portfolio projects, blog categories).

### Structure

```
Home  /  Work  /  Project Name
```

| Property | Value |
|----------|-------|
| Font size | 14px (body-sm) |
| Font weight | 400 (current page: 500) |
| Separator | `/` in `neutral-300` |
| Item color | `blue-600` (link) / `neutral-600` (current) |
| Spacing | `space-2` between items |
| Padding | `space-3` 0 |

### Truncation
For deep paths (>4 levels):
```
Home  /  ...  /  Parent  /  Current Page
```
- Ellipsis (`...`) is a dropdown showing hidden levels
- Always show: first item, last two items

### Accessibility
- Wrapped in `<nav aria-label="Breadcrumb">`
- Uses `<ol>` for ordered list semantics
- Current page has `aria-current="page"`

---

## 5. In-Page Navigation (Anchor Links)

For long-form content pages (case studies, about page sections).

### Structure

```
┌──────────────────┐
│ On This Page      │
│                   │
│ • Introduction    │
│ • The Challenge   │
│ • Approach        │ ← active
│ • Results         │
│ • Testimonial     │
└──────────────────┘
```

| Property | Value |
|----------|-------|
| Position | `sticky`, right sidebar on desktop |
| Top offset | 96px |
| Width | 200px |
| Font size | 14px |
| Active indicator | Left border 2px `blue-600` |
| Active text | `blue-700`, weight 500 |
| Default text | `neutral-500`, weight 400 |

### Behavior
- Auto-highlights based on scroll position (Intersection Observer)
- Smooth scroll on click (`scroll-behavior: smooth`)
- Offset for sticky navbar: `scroll-margin-top: 80px`
- Hidden on mobile — content flows linearly

---

## 6. Footer Navigation

### Structure

```
┌─────────────────────────────────────────────────────────────┐
│ [Logo]                                                       │
│                                                              │
│ Navigation        Resources         Connect                 │
│ Work              Blog              GitHub                   │
│ About             Uses              LinkedIn                 │
│ Contact           RSS               Twitter/X                │
│                                                              │
│ ────────────────────────────────────────────────────────     │
│ © 2026 Flavio Fusuma                   [Back to top ↑]      │
└─────────────────────────────────────────────────────────────┘
```

| Property | Value |
|----------|-------|
| Background | `blue-900` |
| Text color | `neutral-300` |
| Link hover | `neutral-0` |
| Padding | `space-16` vertical, `space-6` horizontal |
| Column gap | `space-12` |

### Responsive
- **Desktop**: 3-column grid
- **Tablet**: 3-column, reduced gap
- **Mobile**: Single column, stacked sections with `space-8` between

---

## 7. Search Pattern

### Trigger
- Keyboard shortcut: `⌘/Ctrl + K`
- Search icon in navbar (optional)

### Modal Search

```
┌──────────────────────────────────────┐
│ 🔍  Search...                    ⌘K  │
├──────────────────────────────────────┤
│ Recent                               │
│ ┌──────────────────────────────────┐ │
│ │ 📄 Building Design Systems       │ │
│ │ 💼 Project: Dashboard Redesign   │ │
│ └──────────────────────────────────┘ │
│                                      │
│ Results update as you type...        │
└──────────────────────────────────────┘
```

| Property | Value |
|----------|-------|
| Width | 640px max |
| Background | `neutral-0` |
| Border | 1px solid `neutral-200` |
| Shadow | `shadow-xl` |
| Border radius | `radius-xl` (12px) |
| Input height | 48px |
| Result item height | 44px |

### Behavior
- Debounced search (200ms)
- Keyboard navigation (↑↓ to select, Enter to go, Esc to close)
- Show recent searches when empty
- Categorized results (pages, blog posts, projects)
- Focus trap within modal

### Accessibility
- `role="dialog"`, `aria-label="Search"`
- `role="combobox"` on input
- `role="listbox"` on results
- `aria-activedescendant` for keyboard navigation
- Announce result count to screen readers

---

## Navigation Decision Tree

```
Is the user navigating between main sections?
  → Top Navbar

Is the user navigating within a content section with hierarchy?
  → Sidebar Navigation

Is the user navigating within a single long page?
  → In-Page Anchor Navigation

Does the user need to know where they are in a hierarchy?
  → Breadcrumbs

Is the user looking for specific content across the site?
  → Search (⌘K)

Is the user at the bottom of a page looking for more?
  → Footer Navigation
```

---

## Accessibility Checklist for Navigation

- [ ] All navigation regions have `role="navigation"` or `<nav>` with unique `aria-label`
- [ ] Current page/section indicated with `aria-current="page"`
- [ ] Skip-to-content link as first focusable element
- [ ] Keyboard navigable with visible focus indicators
- [ ] Mobile menu has focus trap and Escape to close
- [ ] Dropdown menus accessible via keyboard (Enter/Space to open, Arrow keys to navigate)
- [ ] Search modal announced to screen readers
- [ ] Reduced motion respected for all animations
- [ ] Sufficient color contrast for all navigation states (4.5:1 minimum)
