# Breadcrumbs

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Breadcrumbs are a secondary navigation pattern that displays the user's current location within the application hierarchy. They provide a trail of links from the root page to the current page, allowing users to orient themselves and navigate back to parent sections. Use breadcrumbs in hierarchical structures with three or more levels of depth.

---

## Anatomy

```
Standard breadcrumbs:
┌───────────────────────────────────────────────────────────────┐
│  Home  /  Projects  /  Design System  /  Components           │
│  ────     ────────     ─────────────     (current page)      │
│  link     link         link              plain text           │
└───────────────────────────────────────────────────────────────┘

With icons:
┌───────────────────────────────────────────────────────────────┐
│  🏠  /  📁 Projects  /  📁 Design System  /  Components       │
└───────────────────────────────────────────────────────────────┘

Truncated (deep paths):
┌───────────────────────────────────────────────────────────────┐
│  Home  /  ...  /  Components  /  Buttons                      │
│  ────     ───     ──────────     (current page)              │
│  link   dropdown   link          plain text                   │
└───────────────────────────────────────────────────────────────┘

Responsive collapse (mobile):
┌────────────────────────────┐
│  ← Components              │
│    (back to parent link)   │
└────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Outer `<nav>` wrapper with `aria-label="Breadcrumb"` |
| Breadcrumb item | Yes | Individual link in the breadcrumb trail |
| Current page | Yes | Last item; not a link, represents the current page |
| Separator | Yes | Visual divider between breadcrumb items (default: `/`) |
| Home icon | No | Optional house icon replacing the "Home" text for the first item |
| Truncation indicator | No | Ellipsis (`...`) replacing middle items in deep hierarchies |
| Truncation dropdown | No | Dropdown menu revealing the hidden middle items |

---

## Separator Options

| Separator | Character | Use Case |
|-----------|-----------|----------|
| Slash (default) | `/` | Standard; clear hierarchical divider |
| Chevron | `>` or `›` | Slightly more directional than slash |
| Arrow | `→` | Explicit directional flow |
| Custom icon | SVG chevron-right | Polished; recommended for production |

---

## Variants

| Variant | Description | Visual Treatment |
|---------|-------------|-----------------|
| Default | Standard text links with separator | `neutral-500` links, `neutral-900` current page |
| With icons | Each item can have a leading icon | 16px icons before each label |
| Compact | Reduced padding and font size | Smaller text, tighter spacing for dense UIs |

---

## Truncation Behavior

Breadcrumbs automatically truncate when the path exceeds a configurable maximum depth.

| Property | Value | Notes |
|----------|-------|-------|
| Max visible items | 4 (configurable) | First item + ellipsis + last 2 items |
| Truncation trigger | Path depth > max visible items | Middle items are collapsed |
| Ellipsis behavior | Clickable; opens dropdown with hidden items | Dropdown lists collapsed items as links |
| Dropdown position | Below the ellipsis, left-aligned | Standard dropdown styling |
| Dropdown max-height | 240px with scroll | For extremely deep hierarchies |

### Truncation Example

Full path: `Home > Products > Electronics > Laptops > Gaming > ASUS ROG`

Truncated: `Home > ... > Gaming > ASUS ROG`

Dropdown on `...`: `Products`, `Electronics`, `Laptops`

---

## Responsive Collapse

| Viewport | Behavior | Display |
|----------|----------|---------|
| Desktop (>768px) | Full breadcrumb trail | All items visible (or truncated if deep) |
| Tablet (480-768px) | Truncated to first + last 2 items | Always shows ellipsis for 4+ items |
| Mobile (<480px) | Collapses to back-to-parent link | Arrow icon + parent page name only |

---

## States

### Breadcrumb Link States

| State | Text Color | Text Decoration | Background | Notes |
|-------|-----------|-----------------|-----------|-------|
| Default | `neutral-500` | none | `transparent` | Resting state |
| Hover | `blue-600` | underline | `transparent` | Mouse over |
| Active | `blue-700` | underline | `transparent` | Mouse down |
| Focus | `neutral-500` | none | `transparent` | 2px focus ring `blue-600`, rounded |
| Visited | `neutral-500` | none | `transparent` | No visited styling; always same as default |

### Current Page State

| State | Text Color | Font Weight | Notes |
|-------|-----------|------------|-------|
| Current | `neutral-900` | 500 (medium) | Not a link; plain text |

### Separator State

| Property | Value | Notes |
|----------|-------|-------|
| Color | `neutral-300` | Lower contrast than link text |
| Size | 14px (font-size) or 12px (icon) | Slightly smaller than breadcrumb text |
| Margin | 0 8px | Horizontal spacing on each side |

### Truncation Ellipsis States

| State | Text Color | Background | Notes |
|-------|-----------|-----------|-------|
| Default | `neutral-400` | `transparent` | Three dots |
| Hover | `neutral-600` | `neutral-50` | Clickable indicator |
| Active | `neutral-700` | `neutral-100` | Mouse down, opens dropdown |
| Focus | `neutral-400` | `transparent` | 2px focus ring `blue-600` |

---

## Sizing

| Size | Height | Font Size | Icon Size | Separator Size | Padding (item) | Gap |
|------|--------|-----------|-----------|---------------|---------------|-----|
| sm | 28px | 12px | 14px | 10px | 4px 4px | 4px |
| md | 32px | 14px | 16px | 12px | 4px 6px | 8px |
| lg | 36px | 16px | 18px | 14px | 4px 8px | 8px |

---

## Accessibility

- **Role**: Use `<nav>` with `aria-label="Breadcrumb"`. The breadcrumb list uses `<ol>` with list items `<li>`.
- **ARIA -- current page**: The last item (current page) uses `aria-current="page"` and is not a link.
- **ARIA -- truncation**: The ellipsis button uses `aria-label="Show hidden breadcrumbs"` and `aria-expanded="true/false"` with `aria-haspopup="true"`.
- **Keyboard**:
  - `Tab` / `Shift+Tab` moves through breadcrumb links.
  - `Enter` activates a breadcrumb link.
  - `Enter` or `Space` opens the truncation dropdown.
  - `Escape` closes the truncation dropdown.
  - `Arrow Down` / `Arrow Up` navigates within the dropdown.
- **Screen reader**: Announces "Breadcrumb navigation" landmark. Each item is announced with its position in the list. The current page is announced as "current page".
- **Separator**: Separators are decorative and hidden from screen readers with `aria-hidden="true"`.
- **Focus**: Visible focus ring on all interactive elements.
- **Color**: Links are distinguishable from non-link current page via color contrast and styling differences (not color alone).

---

## Design Tokens

```json
{
  "breadcrumbs": {
    "font-family": "{typography.font.sans}",
    "font-weight": "400",
    "current-font-weight": "500",
    "transition": "color 150ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.600}",
    "link": {
      "text-color": "{color.neutral.500}",
      "text-hover": "{color.blue.600}",
      "text-active": "{color.blue.700}",
      "text-decoration-hover": "underline"
    },
    "current": {
      "text-color": "{color.neutral.900}"
    },
    "separator": {
      "color": "{color.neutral.300}",
      "margin-x": "{space.2}"
    },
    "truncation": {
      "text-color": "{color.neutral.400}",
      "text-hover": "{color.neutral.600}",
      "bg-hover": "{color.neutral.50}",
      "dropdown-bg": "{color.neutral.0}",
      "dropdown-border": "{color.neutral.200}",
      "dropdown-shadow": "{shadow.lg}",
      "dropdown-border-radius": "{border.radius.lg}",
      "dropdown-max-height": "240px"
    },
    "sizing": {
      "sm": {
        "height": "28px",
        "font-size": "12px",
        "icon-size": "14px",
        "separator-size": "10px",
        "item-padding": "4px",
        "gap": "{space.1}"
      },
      "md": {
        "height": "32px",
        "font-size": "{typography.body.md.size}",
        "icon-size": "16px",
        "separator-size": "12px",
        "item-padding": "4px 6px",
        "gap": "{space.2}"
      },
      "lg": {
        "height": "36px",
        "font-size": "{typography.body.lg.size}",
        "icon-size": "18px",
        "separator-size": "14px",
        "item-padding": "4px 8px",
        "gap": "{space.2}"
      }
    },
    "responsive": {
      "collapse-breakpoint": "480px",
      "truncate-breakpoint": "768px"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use breadcrumbs for hierarchical navigation with three or more levels of depth.
- Always include the home/root page as the first breadcrumb item.
- Mark the current page with `aria-current="page"` and display it as plain (non-clickable) text.
- Truncate long paths using the ellipsis pattern to keep breadcrumbs scannable.
- Collapse to a back-to-parent link on mobile viewports for simplicity.
- Place breadcrumbs above the page title, below the primary navigation.

**Don't:**
- Don't use breadcrumbs for flat site structures with only one or two levels.
- Don't make the current page item a clickable link -- it should be static text.
- Don't use breadcrumbs as a replacement for primary navigation; they are supplementary.
- Don't display breadcrumbs with more than six visible items; use truncation for deeper paths.
- Don't style visited breadcrumb links differently; consistency is more important than visited-state styling.
- Don't use breadcrumbs for multi-step workflows or wizard progress indicators -- use a stepper component.

---

## Code Example

### HTML

```html
<!-- Standard breadcrumbs -->
<nav class="ff-breadcrumbs ff-breadcrumbs--md" aria-label="Breadcrumb">
  <ol class="ff-breadcrumbs__list">
    <li class="ff-breadcrumbs__item">
      <a href="/" class="ff-breadcrumbs__link">Home</a>
      <span class="ff-breadcrumbs__separator" aria-hidden="true">/</span>
    </li>
    <li class="ff-breadcrumbs__item">
      <a href="/projects" class="ff-breadcrumbs__link">Projects</a>
      <span class="ff-breadcrumbs__separator" aria-hidden="true">/</span>
    </li>
    <li class="ff-breadcrumbs__item">
      <a href="/projects/design-system" class="ff-breadcrumbs__link">Design System</a>
      <span class="ff-breadcrumbs__separator" aria-hidden="true">/</span>
    </li>
    <li class="ff-breadcrumbs__item">
      <span class="ff-breadcrumbs__current" aria-current="page">Components</span>
    </li>
  </ol>
</nav>

<!-- Breadcrumbs with home icon and truncation -->
<nav class="ff-breadcrumbs ff-breadcrumbs--md" aria-label="Breadcrumb">
  <ol class="ff-breadcrumbs__list">
    <li class="ff-breadcrumbs__item">
      <a href="/" class="ff-breadcrumbs__link ff-breadcrumbs__link--icon" aria-label="Home">
        <svg aria-hidden="true"><!-- home icon --></svg>
      </a>
      <span class="ff-breadcrumbs__separator" aria-hidden="true">/</span>
    </li>
    <li class="ff-breadcrumbs__item">
      <button class="ff-breadcrumbs__truncation" aria-label="Show hidden breadcrumbs"
              aria-expanded="false" aria-haspopup="true">
        ...
      </button>
      <div class="ff-breadcrumbs__dropdown" hidden>
        <a href="/products" class="ff-breadcrumbs__dropdown-item">Products</a>
        <a href="/products/electronics" class="ff-breadcrumbs__dropdown-item">Electronics</a>
        <a href="/products/electronics/laptops" class="ff-breadcrumbs__dropdown-item">Laptops</a>
      </div>
      <span class="ff-breadcrumbs__separator" aria-hidden="true">/</span>
    </li>
    <li class="ff-breadcrumbs__item">
      <a href="/products/electronics/laptops/gaming" class="ff-breadcrumbs__link">Gaming</a>
      <span class="ff-breadcrumbs__separator" aria-hidden="true">/</span>
    </li>
    <li class="ff-breadcrumbs__item">
      <span class="ff-breadcrumbs__current" aria-current="page">ASUS ROG</span>
    </li>
  </ol>
</nav>

<!-- Mobile back-to-parent -->
<nav class="ff-breadcrumbs ff-breadcrumbs--mobile" aria-label="Breadcrumb">
  <a href="/projects/design-system" class="ff-breadcrumbs__back">
    <svg aria-hidden="true"><!-- arrow-left icon --></svg>
    Design System
  </a>
</nav>
```

### JSX

```jsx
import { Breadcrumbs, BreadcrumbItem } from '@flaviofusuma/ui';

{/* Standard breadcrumbs */}
<Breadcrumbs size="md" separator="/">
  <BreadcrumbItem href="/">Home</BreadcrumbItem>
  <BreadcrumbItem href="/projects">Projects</BreadcrumbItem>
  <BreadcrumbItem href="/projects/design-system">Design System</BreadcrumbItem>
  <BreadcrumbItem current>Components</BreadcrumbItem>
</Breadcrumbs>

{/* With home icon */}
<Breadcrumbs size="md" separator="chevron" homeIcon={<HomeIcon />}>
  <BreadcrumbItem href="/">Home</BreadcrumbItem>
  <BreadcrumbItem href="/projects">Projects</BreadcrumbItem>
  <BreadcrumbItem current>Design System</BreadcrumbItem>
</Breadcrumbs>

{/* With truncation */}
<Breadcrumbs size="md" maxItems={4} separator="/">
  <BreadcrumbItem href="/">Home</BreadcrumbItem>
  <BreadcrumbItem href="/products">Products</BreadcrumbItem>
  <BreadcrumbItem href="/products/electronics">Electronics</BreadcrumbItem>
  <BreadcrumbItem href="/products/electronics/laptops">Laptops</BreadcrumbItem>
  <BreadcrumbItem href="/products/electronics/laptops/gaming">Gaming</BreadcrumbItem>
  <BreadcrumbItem current>ASUS ROG</BreadcrumbItem>
</Breadcrumbs>

{/* With custom items and icons */}
<Breadcrumbs size="lg" separator={<ChevronIcon />}>
  <BreadcrumbItem href="/" icon={<HomeIcon />}>Home</BreadcrumbItem>
  <BreadcrumbItem href="/projects" icon={<FolderIcon />}>Projects</BreadcrumbItem>
  <BreadcrumbItem current icon={<FileIcon />}>Document</BreadcrumbItem>
</Breadcrumbs>
```

---

## Related Components

- **[Navigation](/02-design-system/05-components/navigation.md)** -- Primary navigation for top-level routing; breadcrumbs supplement this with hierarchical context.
- **[Tabs](/02-design-system/05-components/tabs.md)** -- For switching views within a page; breadcrumbs show position in hierarchy, not content sections.
- **[Pagination](/02-design-system/05-components/pagination.md)** -- For navigating through sequential pages of data; breadcrumbs show hierarchical paths, not sequences.
- **[Buttons](/02-design-system/05-components/buttons.md)** -- The truncation ellipsis and mobile back link use button-like interactions.
