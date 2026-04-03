# Navigation Patterns

> Flavio Fusuma Design System -- Top navbar, sidebar, mobile navigation, breadcrumbs, in-page navigation, search patterns, and responsive navigation transformation.

---

## Overview

Navigation patterns define how users move through the flaviofusuma.com experience. Every navigation element should be predictable, accessible, and responsive -- guiding users to their destination with minimal friction.

### Principles

1. **Clarity.** Users always know where they are and where they can go.
2. **Consistency.** Navigation behaves the same way across every page and breakpoint.
3. **Efficiency.** Users reach any destination in three clicks or fewer.

---

## 1. Top Navbar

The primary navigation pattern for the website. Persistent across all pages.

### Structure

```
┌─────────────────────────────────────────────────────────────┐
│ [Logo]  FF     Portfolio    About    Blog    Contact  🔍 🌙 │
│                    ▬▬▬                                      │
└─────────────────────────────────────────────────────────────┘
                  ↑ active indicator (2px bottom border)
```

### Specifications

| Property | Desktop (1024px+) | Tablet (768-1023px) | Mobile (<768px) |
|---|---|---|---|
| Height | 64px | 56px | 56px |
| Position | `sticky`, top: 0 | `sticky`, top: 0 | `sticky`, top: 0 |
| Background | `color-bg-primary` / transparent | `color-bg-primary` | `color-bg-primary` |
| Shadow | On scroll: `shadow-sm` | On scroll: `shadow-sm` | `shadow-sm` |
| Z-index | 50 | 50 | 50 |
| Horizontal padding | 48px (`space-6`) | 32px (`space-4`) | 16px (`space-2`) |
| Max content width | 1128px, centered | Full width | Full width |
| Logo | 32px height, auto width | 32px height | 28px height |
| Nav link font | Inter Medium, 14px | Inter Medium, 14px | N/A (in drawer) |
| Nav link gap | 8px between links | 8px | N/A |
| Right actions gap | 16px between icons | 16px | 8px |

### Nav Item States

| State | Text Color | Background | Indicator |
|---|---|---|---|
| Default | `color-text-secondary` | transparent | None |
| Hover | `color-text-primary` | `color-bg-secondary`, radius 4px | None |
| Active (current page) | `color-text-brand` | transparent | 2px bottom border `color-bg-brand` |
| Focus | `color-text-brand` | transparent | Focus ring (2px `color-border-focus`, 2px offset) |

### Active Indicator Spec

| Property | Value |
|---|---|
| Width | Matches text width (not full padding width) |
| Height | 2px |
| Color | `color-bg-brand` |
| Position | Bottom of nav item, flush with navbar bottom edge |
| Border radius | 1px (round caps) |
| Transition | 200ms ease-in-out (slides between items on navigation) |

### Scroll Behavior

| Scroll State | Navbar Style |
|---|---|
| At top (scroll = 0) | No shadow, transparent or `color-bg-primary` |
| Scrolled (scroll > 0) | `shadow-sm` added, `color-bg-primary` (opaque) |
| Scroll direction (optional) | Hide on scroll down, reveal on scroll up |

### Responsive Transformation

```
Desktop (1024+):  [Logo]  [Portfolio] [About] [Blog] [Contact]  [🔍] [🌙] [CTA]
Tablet (768):     [Logo]  [Portfolio] [About] [Blog]  [🔍] [☰]
Mobile (375):     [Logo]                               [☰]
```

---

## 2. Mobile Navigation (Hamburger Menu)

### Trigger Button

| Property | Value |
|---|---|
| Icon | Three horizontal lines (hamburger), 24x24 |
| Touch target | 44x44px minimum |
| Position | Right side of mobile navbar |
| Transform animation | Morphs to close (X) icon, 200ms ease-in-out |
| ARIA | `aria-expanded="false/true"`, `aria-controls="mobile-nav"`, `aria-label="Menu"` |

### Overlay Panel

```
┌─────────────────────────────────┐
│ [Logo]  FF                [✕]   │
├─────────────────────────────────┤
│                                 │
│   Portfolio                     │
│   About                         │
│   Blog                          │
│   Contact                       │
│                                 │
│   ┌───────────────────────┐     │
│   │     Let's Talk         │     │
│   └───────────────────────┘     │
│                                 │
│ ─────────────────────────────── │
│                                 │
│   🔍 Search                     │
│   🌙 Dark Mode                  │
│                                 │
│                                 │
│                                 │
│ ─────────────────────────────── │
│   [Social Icons]                │
│   © 2026 Flavio Fusuma         │
└─────────────────────────────────┘
```

| Property | Value |
|---|---|
| Width | 100vw (full screen) or 280px (side drawer) |
| Height | 100vh |
| Background | `color-bg-primary` |
| Overlay | `color-surface-overlay` (black 50%) on background area |
| Open animation | Move In from right, 300ms, ease-out |
| Close animation | Move Out to right, 250ms, ease-in |
| Close triggers | Close button (X), tap overlay, swipe right, Escape key |

### Mobile Nav Item

| Property | Value |
|---|---|
| Height | 56px |
| Padding | 16px horizontal |
| Font | Inter Medium, 18px |
| Color default | `color-text-primary` |
| Color active | `color-text-brand` |
| Border bottom | 1px `color-border-default` |
| Touch target | Full width, 56px height |
| Icon (optional) | 24x24, 16px gap from text |

### Accessibility

- Focus trap within menu when open
- `Escape` closes the menu
- `aria-expanded` on hamburger button
- Wrapped in `<nav aria-label="Main navigation">`
- Focus returns to hamburger button on close
- First focus target: close button or first nav item

---

## 3. Bottom Tab Bar (Mobile Alternative)

For app-like experiences with 3-5 primary destinations.

```
┌──────────────────────────────────────────────┐
│                                              │
│              Page Content                    │
│                                              │
├──────────────────────────────────────────────┤
│   🏠      📁      ✉️      👤                  │
│  Home   Work   Contact  About                │
└──────────────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Height | 64px (plus safe area inset on iOS) |
| Background | `color-bg-primary` |
| Border top | 1px `color-border-default` |
| Position | Fixed bottom, z-index 50 |
| Max items | 5 |
| Item width | Equal distribution (`flex: 1`) |
| Icon size | 24x24 |
| Label font | Inter Regular, 10px |
| Active icon + text | `color-text-brand` |
| Inactive icon + text | `color-text-tertiary` |
| Active indicator | 3px top bar, `color-bg-brand`, 24px width, rounded |
| Touch target | Each tab: full height, equal width share |

### When to Use Bottom Tabs vs. Hamburger

| Criteria | Bottom Tabs | Hamburger Menu |
|---|---|---|
| Number of top-level destinations | 3-5 | 5+ |
| Frequency of switching | High (users switch often) | Low (users pick a section and stay) |
| Content type | App-like, dashboard | Content site, portfolio |
| Platform convention | Mobile apps | Mobile websites |

**Flavio Fusuma default:** Hamburger menu for the portfolio website. Bottom tabs reserved for future app-like products.

---

## 4. Sidebar Navigation

For documentation, settings, and dashboard-style pages.

### Layout

```
┌───────────────┬──────────────────────────────────────┐
│ Sidebar       │ Main Content                         │
│ (280px fixed) │ (fluid)                              │
│               │                                      │
│ SECTION       │                                      │
│ ─────────     │                                      │
│ ● Overview    │                                      │
│   Components  │                                      │
│   Patterns    │                                      │
│   Tokens      │                                      │
│               │                                      │
│ SECTION       │                                      │
│ ─────────     │                                      │
│   Settings    │                                      │
│   Help        │                                      │
│               │                                      │
│ ─────────     │                                      │
│ 👤 Profile    │                                      │
└───────────────┴──────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Width | 280px fixed |
| Background | `color-bg-secondary` |
| Border right | 1px `color-border-default` |
| Position | `sticky`, top: 64px (below navbar) |
| Max height | `calc(100vh - 64px)` |
| Padding | 16px top, 12px horizontal, 16px bottom |
| Overflow | `overflow-y: auto` (independent scroll) |

### Section Headers

| Property | Value |
|---|---|
| Font | Inter SemiBold, 11px, uppercase, `letter-spacing: 0.05em` |
| Color | `color-text-tertiary` |
| Padding | 8px 12px |
| Margin top | 16px between sections |

### Nav Item States

| State | Background | Text | Left Indicator |
|---|---|---|---|
| Default | transparent | `color-text-secondary`, Inter Regular 14px | None |
| Hover | `color-bg-tertiary`, radius 6px | `color-text-primary` | None |
| Active | `color-bg-brand-subtle`, radius 6px | `color-text-brand`, Inter Medium 14px | 3px bar, `color-bg-brand`, rounded |
| Focus | transparent | `color-text-primary` | Focus ring |

### Collapsible Sections

```
▾ COMPONENTS          ← click to toggle
  ● Buttons
    Inputs
    Cards

▸ PATTERNS            ← collapsed
```

| Property | Value |
|---|---|
| Toggle icon | Chevron (▾ expanded, ▸ collapsed), 16x16, `color-text-tertiary` |
| Animation | 200ms ease-out, height collapses with `overflow: hidden` |
| Default | Expanded for current section, collapsed for others |
| ARIA | `aria-expanded` on section header button |

### Responsive Behavior

| Breakpoint | Sidebar State |
|---|---|
| Desktop (1024px+) | Visible, fixed 280px |
| Tablet (768-1023px) | Off-canvas drawer, triggered by hamburger |
| Mobile (<768px) | Off-canvas drawer, triggered by hamburger |

---

## 5. Breadcrumb Navigation

Shows the user's position in the page hierarchy. Used on interior pages (not the homepage).

### Structure

```
Home  >  Portfolio  >  Project Name
 ↑ link    ↑ link      ↑ current (not a link)
```

| Property | Value |
|---|---|
| Container height | 40px (auto-layout horizontal, centered vertically) |
| Font | Inter Regular, 14px |
| Link color | `color-text-link` |
| Link hover | Underline |
| Current page | `color-text-primary`, `font-weight: 500` |
| Separator | Chevron-right icon, 16x16, `color-text-tertiary` |
| Separator spacing | 8px on each side |
| Position | Below navbar, above page title |
| Margin | 16px below nav, 8px above page content |

### Truncation (Deep Hierarchies)

For paths deeper than 3 levels:

```
Home  >  ...  >  Parent Page  >  Current Page
         ↑
    Clicking "..." shows a dropdown with the full path
```

Rules: Always show first item and last two items.

### Responsive Behavior

| Breakpoint | Behavior |
|---|---|
| Desktop | Full breadcrumb trail visible |
| Tablet | Full trail if it fits; truncate middle if needed |
| Mobile | Show only "< Back to [Parent]" link |

### Accessibility

- Wrapped in `<nav aria-label="Breadcrumb">`
- Uses `<ol>` with `<li>` for ordered list semantics
- Current page has `aria-current="page"`
- Separator icons are `aria-hidden="true"`

---

## 6. In-Page Navigation (Anchor Links)

For long-form content pages (case studies, project details, documentation).

### Sticky Table of Contents

```
┌──────────────────┬─────────────────────────────────────┐
│ On This Page     │                                     │
│                  │  # Section One                      │
│ ● Section One    │                                     │
│   Section Two    │  Content...                         │
│   Section Three  │                                     │
│   Section Four   │  # Section Two                      │
│                  │                                     │
│                  │  Content...                         │
└──────────────────┴─────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Width | 200px fixed |
| Position | Sticky, top: 80px (below navbar + spacing) |
| Title | "On This Page", Inter SemiBold, 12px, uppercase, `color-text-tertiary` |
| Link font | Inter Regular, 14px, `color-text-secondary` |
| Active link | Inter Medium, `color-text-brand`, left border 2px `color-bg-brand` |
| Link padding | 8px left (12px for active, including border) |
| Link spacing | 4px vertical gap between items |
| Scroll tracking | Active link updates via Intersection Observer |
| Smooth scroll | `scroll-behavior: smooth`, offset: `scroll-margin-top: 80px` |

### Jump-to-Top Button

| Property | Value |
|---|---|
| Size | 40x40px |
| Position | Fixed, bottom-right (24px from edges) |
| Style | Ghost button, `color-bg-primary` fill, `shadow-md` |
| Icon | Arrow-up, 20x20 |
| Show trigger | Scroll position > 500px |
| Show animation | Fade in, 200ms, ease-out |
| Hide animation | Fade out, 150ms, ease-in |
| Click behavior | `scrollTo({ top: 0, behavior: 'smooth' })` |

### Responsive Behavior

| Breakpoint | TOC State |
|---|---|
| Desktop (1024px+) | Sticky sidebar (right of content) |
| Tablet (768-1023px) | Collapsible dropdown above content |
| Mobile (<768px) | Hidden; rely on jump-to-top button |

---

## 7. Footer Navigation

### Structure

```
┌──────────────────────────────────────────────────────────────────┐
│ [Logo]                                                           │
│ A brief tagline or description.                                  │
│                                                                  │
│ Navigation        Resources         Connect                     │
│ Portfolio         Blog              GitHub                       │
│ About             Uses              LinkedIn                     │
│ Contact           RSS               Twitter/X                    │
│                                     Email                        │
│                                                                  │
│ ─────────────────────────────────────────────────────────────── │
│ © 2026 Flavio Fusuma. All rights reserved.       [Back to top ↑]│
└──────────────────────────────────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Background | `brand-navy` (#1E3A5F) |
| Text color | `neutral-300` (body), `white` (headings) |
| Link color default | `neutral-300` |
| Link color hover | `white` |
| Padding vertical | 64px (`space-8`) top, 32px (`space-4`) bottom |
| Padding horizontal | Matches page container (48px desktop, 16px mobile) |
| Column gap | 48px (`space-6`) |
| Column heading font | Inter SemiBold, 14px, uppercase, `letter-spacing: 0.05em`, `white` |
| Link font | Inter Regular, 14px |
| Link vertical gap | 12px |
| Divider | 1px `neutral-700` (20% opacity white) |
| Copyright font | Inter Regular, 12px, `neutral-400` |

### Responsive Layout

| Breakpoint | Columns | Behavior |
|---|---|---|
| Desktop (1024px+) | 3 link columns + logo column (4 total) | Horizontal grid |
| Tablet (768-1023px) | 3 link columns, logo above | Logo full-width above, 3 columns below |
| Mobile (<768px) | 1 column | All sections stacked vertically, 32px gap |

---

## 8. Search Patterns

### Search Trigger

| Property | Value |
|---|---|
| Desktop trigger | Search icon in navbar + keyboard shortcut `Cmd/Ctrl + K` |
| Mobile trigger | Search icon in navbar or search item in mobile drawer |
| Icon | Magnifying glass, 20x20 |
| Button style | Ghost button, 40x40px touch target |

### Search Overlay (Spotlight / Command Palette Style)

```
┌──────────────────────────────────────────────────────┐
│ 🔍  Search projects, pages, and more...          ⌘K  │
├──────────────────────────────────────────────────────┤
│                                                      │
│ Recent Searches                                      │
│ ───────────────                                      │
│ ● React Dashboard                                    │
│ ● Mobile App Redesign                                │
│                                                      │
│ Quick Links                                          │
│ ───────────                                          │
│ → Portfolio                                          │
│ → Contact                                            │
│ → About                                              │
│                                                      │
│                              ⌘K to toggle · Esc      │
└──────────────────────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Width | 640px max (full width minus 32px on mobile) |
| Position | Centered, 20% from top of viewport |
| Background | `color-surface-elevated` |
| Border | 1px `color-border-default` |
| Border radius | 12px (`radius-lg`) |
| Shadow | `shadow-xl` |
| Overlay | `color-surface-overlay` (black 50%) |
| Open animation | Dissolve + scale from 95% to 100%, 200ms, ease-out |
| Close animation | Dissolve + scale to 95%, 150ms, ease-in |
| Close triggers | Escape key, click overlay |

### Search Input

| Property | Value |
|---|---|
| Height | 48px |
| Font | Inter Regular, 16px |
| Placeholder | "Search projects, pages, and more..." |
| Icon | Magnifying glass, 20x20, `color-text-tertiary` |
| Border bottom | 1px `color-border-default` |
| Shortcut hint | `⌘K` badge, right-aligned, `color-text-tertiary` |
| Debounce | 200ms after keystroke |

### Search Results

```
┌──────────────────────────────────────────────────────┐
│ 🔍  react dashboard                                  │
├──────────────────────────────────────────────────────┤
│                                                      │
│ PROJECTS                                             │
│ ┌──────────────────────────────────────────────────┐ │
│ │ 📁 React Dashboard Redesign                      │ │
│ │    Web Application · 2025                        │ │
│ └──────────────────────────────────────────────────┘ │
│ ┌──────────────────────────────────────────────────┐ │
│ │ 📁 React Component Library                       │ │
│ │    Open Source · 2024                            │ │
│ └──────────────────────────────────────────────────┘ │
│                                                      │
│ PAGES                                                │
│ ┌──────────────────────────────────────────────────┐ │
│ │ 📄 About -- React experience section             │ │
│ └──────────────────────────────────────────────────┘ │
│                                                      │
│                                      3 results       │
└──────────────────────────────────────────────────────┘
```

| Element | Spec |
|---|---|
| Result item height | Hug contents, min 48px |
| Result item padding | 12px 16px |
| Result item hover | `color-bg-secondary` background |
| Category header | Inter SemiBold, 11px, uppercase, `color-text-tertiary`, `letter-spacing: 0.05em` |
| Result title | Inter Medium, 14px, `color-text-primary` |
| Result subtitle | Inter Regular, 12px, `color-text-secondary` |
| Max visible results | 8 (scrollable beyond that) |
| Empty state | "No results for '[query]'" with suggestion links |
| Keyboard navigation | Arrow up/down between results, Enter to select, Escape to close |

### Search Accessibility

- Dialog uses `role="dialog"`, `aria-label="Search"`
- Input uses `role="combobox"`, `aria-autocomplete="list"`
- Results list uses `role="listbox"`
- Active result uses `aria-activedescendant`
- Result count announced via `aria-live="polite"` region
- Focus trap within search dialog

---

## Responsive Navigation Transformation Matrix

| Element | Mobile (<768px) | Tablet (768-1023px) | Desktop (1024px+) |
|---|---|---|---|
| Top navbar | Logo + hamburger only | Logo + links + compact actions | Full navbar |
| Nav links | Inside hamburger drawer | Visible in navbar | Visible in navbar |
| Search | Inside drawer or separate overlay | Icon in navbar | Icon in navbar |
| Theme toggle | Inside drawer | Icon in navbar | Icon in navbar |
| CTA button | Inside drawer (full width) | Compact in navbar | In navbar |
| Sidebar | Off-canvas left drawer | Off-canvas left drawer | Visible, 280px |
| Breadcrumbs | "< Back" link | Full or truncated trail | Full trail |
| In-page TOC | Hidden | Collapsible dropdown | Sticky sidebar |
| Bottom tabs | Visible (if app pattern) | Hidden | Hidden |
| Footer | Single column stacked | 3-column grid | 4-column grid |

---

## Navigation Decision Tree

```
Is the user navigating between main site sections?
  → Top Navbar

Is the user navigating within a section with deep hierarchy?
  → Sidebar Navigation

Is the user navigating within a single long page?
  → In-Page Anchor Navigation (Table of Contents)

Does the user need to know their position in a hierarchy?
  → Breadcrumbs

Is the user searching for specific content?
  → Search (Cmd/Ctrl + K)

Is the user at the bottom of a page?
  → Footer Navigation

Is this a mobile app-like experience with frequent section switching?
  → Bottom Tab Bar
```

---

## Navigation Accessibility Checklist

- [ ] All navigation regions use `<nav>` with unique `aria-label` values (e.g., "Main navigation", "Breadcrumb", "Sidebar navigation", "Footer navigation")
- [ ] Current page/section indicated with `aria-current="page"`
- [ ] Skip-to-content link is the first focusable element on every page
- [ ] Hamburger button has `aria-expanded`, `aria-controls`, and `aria-label="Menu"`
- [ ] Mobile drawer uses focus trap when open
- [ ] Focus returns to trigger element when drawer/menu closes
- [ ] All interactive elements have minimum 44x44px touch targets on mobile
- [ ] Keyboard: Tab moves between nav items; Enter/Space activates links
- [ ] Keyboard: Escape closes open menus, drawers, and search overlay
- [ ] Dropdown menus use `aria-haspopup` and `aria-expanded`
- [ ] Search dialog uses proper ARIA combobox pattern
- [ ] Color contrast meets 4.5:1 for nav text and 3:1 for active indicators/icons
- [ ] All animations respect `prefers-reduced-motion: reduce`
- [ ] Navigation remains usable at 200% browser zoom
- [ ] Breadcrumb separators are decorative (`aria-hidden="true"`)
