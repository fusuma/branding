# Navigation

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Navigation components provide the primary wayfinding structure for an application. They orient users within the information hierarchy and enable movement between top-level sections. The navigation system includes a horizontal navbar for top-level routing and a vertical sidebar for section-level or feature-level navigation. Use navigation components to establish a consistent, predictable structure across all pages.

---

## Anatomy

### Horizontal Navbar

```
┌──────────────────────────────────────────────────────────────────┐
│  ┌──────┐  ┌──────┐ ┌──────┐ ┌────────┐       ┌────┐ ┌──────┐ │
│  │ Logo │  │ Nav  │ │ Nav  │ │Dropdown│       │Bell│ │Avatar│ │
│  │      │  │Item 1│ │Item 2│ │ Item 3▼│       │Icon│ │  JD  │ │
│  └──────┘  └──────┘ └──────┘ └────────┘       └────┘ └──────┘ │
│             ════════                                            │
│            (active)                                             │
└──────────────────────────────────────────────────────────────────┘

Mobile collapsed:
┌──────────────────────────────────────┐
│  ┌──────┐                   ┌─────┐  │
│  │ Logo │                   │ === │  │
│  └──────┘                   │menu │  │
│                             └─────┘  │
├──────────────────────────────────────┤
│  Nav Item 1                          │
│  Nav Item 2                          │
│  Nav Item 3  ▶                       │
│    └ Sub Item A                      │
│    └ Sub Item B                      │
│  ─────────────                       │
│  Profile                             │
│  Sign out                            │
└──────────────────────────────────────┘
```

### Vertical Sidebar

```
┌──────────────────┐
│  ┌──────────┐    │
│  │   Logo   │    │
│  └──────────┘    │
│                  │
│  ┌──┐            │
│  │☰ │ Dashboard  │  ◄ active
│  └──┘ ═══════    │
│  ┌──┐            │
│  │☰ │ Projects   │
│  └──┘            │
│  ┌──┐            │
│  │☰ │ Analytics ▼│
│  └──┘            │
│    └ Overview    │
│    └ Reports     │
│                  │
│  ── section ──   │
│                  │
│  ┌──┐            │
│  │☰ │ Settings   │
│  └──┘            │
│                  │
│  ┌──────────┐    │
│  │  JD User │    │
│  └──────────┘    │
└──────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Outer wrapper; `<nav>` element with appropriate ARIA |
| Logo slot | Yes | Brand logo or wordmark; links to home/dashboard |
| Nav items | Yes | Primary navigation links or buttons |
| Active indicator | Yes | Visual marker showing the current page or section |
| Dropdown menu | No | Expandable sub-navigation for grouped pages |
| Utility area | No | Right-aligned icons (notifications, search) and user avatar |
| Hamburger button | No | Mobile toggle button that reveals the navigation drawer |
| Section divider | No | Visual separator between navigation groups |
| User section | No | Avatar + name at the bottom of sidebar or right of navbar |

---

## Variants

| Variant | Layout | Use Case |
|---------|--------|----------|
| Horizontal navbar | Fixed top bar, full width | Top-level page routing, marketing sites, simple apps |
| Vertical sidebar | Fixed left panel, full height | Complex applications, dashboards, admin panels |
| Sidebar collapsed | Icon-only vertical bar, expandable | Space-constrained layouts, user-toggled compact mode |

### Navbar Sub-Variants

| Sub-Variant | Description | Visual Difference |
|-------------|-------------|-------------------|
| Transparent | Transparent background over hero content | No background, white or dark text depending on context |
| Filled | Solid background color | `neutral-0` background with bottom border |
| Elevated | Filled with shadow | `neutral-0` background with `shadow-sm` |

### Sidebar Sub-Variants

| Sub-Variant | Description | Visual Difference |
|-------------|-------------|-------------------|
| Light | Light background | `neutral-0` bg, right border `neutral-200` |
| Dark | Dark background | `neutral-900` bg, light text |
| Bordered | Light with visible border | `neutral-0` bg, 1px right border `neutral-200` |

---

## Sticky Behavior

| Property | Navbar | Sidebar |
|----------|--------|---------|
| Position | `position: sticky; top: 0` | `position: fixed; left: 0; top: 0; height: 100vh` |
| Z-index | `z-index: 40` | `z-index: 30` |
| Scroll behavior | Optionally hides on scroll-down, shows on scroll-up | Always visible; content scrolls within sidebar if overflow |
| Shadow on scroll | Adds `shadow-sm` when page is scrolled past 0 | N/A |
| Backdrop blur | Optional `backdrop-filter: blur(8px)` for transparent variant | N/A |

---

## States

### Nav Item States

| State | Background | Text | Indicator | Notes |
|-------|-----------|------|-----------|-------|
| Default | `transparent` | `neutral-600` | none | Resting state |
| Hover | `neutral-50` | `neutral-900` | none | Mouse over |
| Active (current) | `blue-50` | `blue-600` | 2px bottom border (navbar) or left border (sidebar) in `blue-600` | Current page |
| Focus | `transparent` | `neutral-600` | 2px focus ring `blue-600` | Keyboard focus |
| Disabled | `transparent` | `neutral-300` | none | Non-navigable item |

### Dropdown Menu States

| State | Background | Border | Shadow | Notes |
|-------|-----------|--------|--------|-------|
| Closed | -- | -- | -- | Not rendered or hidden |
| Open | `neutral-0` | `neutral-200` | `shadow-lg` | Visible dropdown panel |
| Item hover | `neutral-50` | -- | -- | Individual menu item hover |
| Item active | `blue-50` | -- | -- | Current page within dropdown |

### Mobile Hamburger States

| State | Icon | Background | Notes |
|-------|------|-----------|-------|
| Closed | Three-line hamburger | `transparent` | Menu is hidden |
| Open | X close icon | `transparent` | Menu is visible, icon transitions |
| Focus | Three-line or X | 2px ring `blue-600` | Keyboard focus |

---

## Sizing

### Horizontal Navbar

| Property | Value | Token |
|----------|-------|-------|
| Height | 64px | -- |
| Padding horizontal | 24px (desktop), 16px (mobile) | `{space.6}` / `{space.4}` |
| Logo max height | 32px | -- |
| Nav item padding | 8px 16px | `{space.2}` `{space.4}` |
| Nav item font size | 14px / medium (500) | `{typography.body.md}` |
| Nav item gap | 4px | `{space.1}` |
| Active indicator height | 2px | -- |
| Dropdown min width | 200px | -- |
| Hamburger button size | 40px | -- |
| Breakpoint (mobile) | 768px | `{breakpoint.md}` |

### Vertical Sidebar

| Property | Value | Token |
|----------|-------|-------|
| Width (expanded) | 256px | -- |
| Width (collapsed) | 64px | -- |
| Padding | 16px | `{space.4}` |
| Logo area height | 64px | -- |
| Nav item height | 40px | -- |
| Nav item padding | 8px 12px | `{space.2}` `{space.3}` |
| Nav item font size | 14px / medium (500) | `{typography.body.md}` |
| Nav item icon size | 20px | -- |
| Nav item gap | 4px | `{space.1}` |
| Section divider margin | 16px 0 | `{space.4}` |
| Active indicator width | 3px | -- |
| Nested item indent | 36px left padding | -- |

---

## Accessibility

- **Role**: Use the `<nav>` element. Add `aria-label="Primary navigation"` for the main nav and `aria-label="Sidebar navigation"` for secondary navigation. If multiple `<nav>` elements exist, each must have a unique `aria-label`.
- **ARIA -- current page**: Mark the active nav item with `aria-current="page"`.
- **ARIA -- dropdowns**: Use `aria-expanded="true/false"` on the dropdown trigger, `aria-haspopup="true"`, and `aria-controls="[dropdown-id]"`.
- **ARIA -- mobile**: The hamburger button needs `aria-expanded`, `aria-controls`, and `aria-label="Open main menu"` / `"Close main menu"`.
- **Keyboard**:
  - `Tab` / `Shift+Tab` moves through nav items.
  - `Enter` or `Space` activates a link or toggles a dropdown.
  - `Escape` closes an open dropdown and returns focus to its trigger.
  - `Arrow Down` / `Arrow Up` navigates within an open dropdown.
  - On mobile overlay, `Escape` closes the menu and returns focus to the hamburger button.
- **Screen reader**: Announces navigation landmarks, current page, and expanded/collapsed state of dropdowns.
- **Focus**: Visible focus indicators on all interactive elements. Focus is trapped within mobile overlay when open.
- **Color**: Active state uses both color and a visual indicator (border/underline) so it is not conveyed by color alone.
- **Motion**: Dropdown, sidebar collapse, and mobile overlay animations respect `prefers-reduced-motion: reduce`.
- **Skip link**: Include a "Skip to main content" link as the first focusable element in the page.

---

## Design Tokens

```json
{
  "navigation": {
    "font-family": "{typography.font.sans}",
    "font-weight": "500",
    "font-size": "{typography.body.md.size}",
    "transition": "all 200ms ease",
    "focus-ring-width": "2px",
    "focus-ring-color": "{color.blue.600}",
    "navbar": {
      "height": "64px",
      "background": "{color.neutral.0}",
      "border-color": "{color.neutral.200}",
      "border-width": "1px",
      "padding-x": "{space.6}",
      "z-index": "40",
      "shadow-on-scroll": "{shadow.sm}",
      "logo-max-height": "32px"
    },
    "sidebar": {
      "width": "256px",
      "width-collapsed": "64px",
      "background": "{color.neutral.0}",
      "border-color": "{color.neutral.200}",
      "border-width": "1px",
      "padding": "{space.4}",
      "z-index": "30"
    },
    "sidebar-dark": {
      "background": "{color.neutral.900}",
      "text-color": "{color.neutral.300}",
      "text-hover": "{color.neutral.0}",
      "active-bg": "rgba(255,255,255,0.1)",
      "active-text": "{color.neutral.0}"
    },
    "nav-item": {
      "height": "40px",
      "padding-x": "{space.4}",
      "padding-y": "{space.2}",
      "gap": "{space.1}",
      "border-radius": "{border.radius.md}",
      "text-color": "{color.neutral.600}",
      "text-hover": "{color.neutral.900}",
      "bg-hover": "{color.neutral.50}",
      "active-text": "{color.blue.600}",
      "active-bg": "{color.blue.50}",
      "active-indicator": "{color.blue.600}",
      "disabled-text": "{color.neutral.300}",
      "icon-size": "20px"
    },
    "dropdown": {
      "min-width": "200px",
      "background": "{color.neutral.0}",
      "border-color": "{color.neutral.200}",
      "border-radius": "{border.radius.lg}",
      "shadow": "{shadow.lg}",
      "padding": "{space.1}",
      "item-padding": "{space.2} {space.3}",
      "item-border-radius": "{border.radius.md}"
    },
    "mobile": {
      "breakpoint": "768px",
      "overlay-bg": "rgba(0,0,0,0.5)",
      "drawer-width": "80vw",
      "max-drawer-width": "320px",
      "hamburger-size": "40px"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use the horizontal navbar for top-level routing with five or fewer primary destinations.
- Use the vertical sidebar for applications with deep navigation hierarchies or many sections.
- Always highlight the current page with `aria-current="page"` and visual active state.
- Include a "Skip to main content" link as the first focusable element.
- Ensure the mobile navigation is fully accessible with focus trapping and escape-to-close.
- Group related navigation items with section dividers and clear labels.
- Keep the logo as a link to the home page or dashboard.

**Don't:**
- Don't use more than two levels of nesting in navigation; deep hierarchies should use separate page layouts.
- Don't hide critical navigation behind a hamburger on desktop viewports.
- Don't mix navbar and sidebar in the same layout unless one is clearly secondary (e.g., sidebar for section nav below a global navbar).
- Don't use navigation items as action triggers (e.g., "Delete", "Submit"); use buttons instead.
- Don't omit the mobile hamburger menu on viewports below the breakpoint.
- Don't auto-collapse the sidebar without providing a toggle control for the user.

---

## Code Example

### HTML

```html
<!-- Horizontal navbar -->
<header class="ff-navbar" role="banner">
  <a href="#main" class="ff-skip-link">Skip to main content</a>
  <nav class="ff-navbar__container" aria-label="Primary navigation">
    <a href="/" class="ff-navbar__logo">
      <img src="/logo.svg" alt="Flavio Fusuma" height="32" />
    </a>
    <ul class="ff-navbar__nav" role="menubar">
      <li role="none">
        <a href="/dashboard" class="ff-navbar__item" role="menuitem" aria-current="page">Dashboard</a>
      </li>
      <li role="none">
        <a href="/projects" class="ff-navbar__item" role="menuitem">Projects</a>
      </li>
      <li role="none">
        <button class="ff-navbar__item ff-navbar__item--dropdown" role="menuitem"
                aria-expanded="false" aria-haspopup="true" aria-controls="nav-dropdown">
          More
          <svg class="ff-navbar__chevron" aria-hidden="true"><!-- chevron --></svg>
        </button>
        <ul id="nav-dropdown" class="ff-dropdown" role="menu" hidden>
          <li role="none"><a href="/analytics" class="ff-dropdown__item" role="menuitem">Analytics</a></li>
          <li role="none"><a href="/settings" class="ff-dropdown__item" role="menuitem">Settings</a></li>
        </ul>
      </li>
    </ul>
    <div class="ff-navbar__utility">
      <button class="ff-btn ff-btn--ghost ff-btn--icon-only" aria-label="Notifications">
        <svg aria-hidden="true"><!-- bell icon --></svg>
      </button>
      <div class="ff-avatar ff-avatar--sm">
        <img src="/photos/user.jpg" alt="User menu" />
      </div>
    </div>
    <button class="ff-navbar__hamburger" aria-expanded="false" aria-controls="mobile-nav" aria-label="Open main menu">
      <svg aria-hidden="true"><!-- hamburger icon --></svg>
    </button>
  </nav>
</header>

<!-- Vertical sidebar -->
<aside class="ff-sidebar" aria-label="Sidebar navigation">
  <div class="ff-sidebar__logo">
    <img src="/logo.svg" alt="Flavio Fusuma" height="32" />
  </div>
  <nav class="ff-sidebar__nav">
    <ul class="ff-sidebar__list">
      <li>
        <a href="/dashboard" class="ff-sidebar__item ff-sidebar__item--active" aria-current="page">
          <svg class="ff-sidebar__icon" aria-hidden="true"><!-- dashboard icon --></svg>
          <span class="ff-sidebar__label">Dashboard</span>
        </a>
      </li>
      <li>
        <button class="ff-sidebar__item" aria-expanded="false">
          <svg class="ff-sidebar__icon" aria-hidden="true"><!-- analytics icon --></svg>
          <span class="ff-sidebar__label">Analytics</span>
          <svg class="ff-sidebar__chevron" aria-hidden="true"><!-- chevron --></svg>
        </button>
        <ul class="ff-sidebar__submenu" hidden>
          <li><a href="/analytics/overview" class="ff-sidebar__item ff-sidebar__item--nested">Overview</a></li>
          <li><a href="/analytics/reports" class="ff-sidebar__item ff-sidebar__item--nested">Reports</a></li>
        </ul>
      </li>
    </ul>
    <div class="ff-sidebar__divider" role="separator"></div>
    <ul class="ff-sidebar__list">
      <li>
        <a href="/settings" class="ff-sidebar__item">
          <svg class="ff-sidebar__icon" aria-hidden="true"><!-- settings icon --></svg>
          <span class="ff-sidebar__label">Settings</span>
        </a>
      </li>
    </ul>
  </nav>
</aside>
```

### JSX

```jsx
import { Navbar, Sidebar, NavItem, NavDropdown, NavGroup } from '@flaviofusuma/ui';
import { DashboardIcon, AnalyticsIcon, SettingsIcon } from '@flaviofusuma/icons';

{/* Horizontal navbar */}
<Navbar
  logo={<img src="/logo.svg" alt="Flavio Fusuma" />}
  utility={
    <>
      <IconButton icon={<BellIcon />} aria-label="Notifications" />
      <Avatar size="sm" src="/photos/user.jpg" alt="Jane Doe" />
    </>
  }
>
  <NavItem href="/dashboard" active>Dashboard</NavItem>
  <NavItem href="/projects">Projects</NavItem>
  <NavDropdown label="More">
    <NavItem href="/analytics">Analytics</NavItem>
    <NavItem href="/settings">Settings</NavItem>
  </NavDropdown>
</Navbar>

{/* Vertical sidebar */}
<Sidebar
  logo={<img src="/logo.svg" alt="Flavio Fusuma" />}
  collapsible
  defaultCollapsed={false}
>
  <NavItem href="/dashboard" icon={<DashboardIcon />} active>
    Dashboard
  </NavItem>
  <NavGroup label="Analytics" icon={<AnalyticsIcon />} defaultExpanded={false}>
    <NavItem href="/analytics/overview">Overview</NavItem>
    <NavItem href="/analytics/reports">Reports</NavItem>
  </NavGroup>
  <NavGroup label="Settings" separated>
    <NavItem href="/settings" icon={<SettingsIcon />}>Settings</NavItem>
  </NavGroup>
</Sidebar>
```

---

## Related Components

- **[Tabs](/02-design-system/05-components/tabs.md)** -- For switching between views within a single page; use tabs for in-page navigation rather than top-level routing.
- **[Breadcrumbs](/02-design-system/05-components/breadcrumbs.md)** -- For showing the user's position in the hierarchy; often used alongside sidebar navigation.
- **[Avatar](/02-design-system/05-components/avatar.md)** -- Commonly placed in the navbar utility area to represent the logged-in user.
- **[Buttons](/02-design-system/05-components/buttons.md)** -- Navigation items look like links; use buttons for actions (not navigation destinations).
