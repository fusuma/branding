# Tabs

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Tabs organize content into separate views where only one view is visible at a time. They allow users to switch between related groups of content without navigating to a new page. Use tabs when content can be logically divided into parallel sections that users will switch between frequently.

---

## Anatomy

### Underline Tabs (default)

```
┌─────────────────────────────────────────────────────────┐
│  [Tab 1]    [Tab 2]    [Tab 3]    [Tab 4]              │
│  ════════                                               │
│  (active)                                               │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Tab panel content                                      │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

### Contained Tabs

```
┌─────────────────────────────────────────────────────────┐
│  ┌─────────┐┌─────────┐┌─────────┐┌─────────┐          │
│  │ Tab 1   ││ Tab 2   ││ Tab 3   ││ Tab 4   │          │
│  │(active) ││         ││         ││         │          │
│  │█████████││░░░░░░░░░││░░░░░░░░░││░░░░░░░░░│          │
│  └─────────┘└─────────┘└─────────┘└─────────┘          │
├─────────────────────────────────────────────────────────┤
│  Tab panel content                                      │
└─────────────────────────────────────────────────────────┘
```

### Pill Tabs

```
┌─────────────────────────────────────────────────────────┐
│  ┌──────────────────────────────────────────────────┐   │
│  │ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ │   │
│  │ │(Tab 1) │ │ Tab 2   │ │ Tab 3   │ │ Tab 4   │ │   │
│  │ │████████│ │         │ │         │ │         │ │   │
│  │ └─────────┘ └─────────┘ └─────────┘ └─────────┘ │   │
│  └──────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────┤
│  Tab panel content                                      │
└─────────────────────────────────────────────────────────┘
```

### Vertical Tabs

```
┌──────────────┬──────────────────────────────────┐
│  ┌──────────┐│                                  │
│  │ Tab 1    ││  Tab panel content               │
│  │ (active) ││                                  │
│  │══════════││                                  │
│  └──────────┘│                                  │
│  ┌──────────┐│                                  │
│  │ Tab 2    ││                                  │
│  └──────────┘│                                  │
│  ┌──────────┐│                                  │
│  │ Tab 3    ││                                  │
│  └──────────┘│                                  │
└──────────────┴──────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Tab list | Yes | Container holding all tab triggers; `role="tablist"` |
| Tab trigger | Yes | Individual clickable tab; `role="tab"` |
| Active indicator | Yes | Visual marker on the selected tab (underline, background, or pill highlight) |
| Tab icon | No | Optional leading icon within a tab trigger |
| Tab badge/count | No | Optional trailing count or badge indicator |
| Tab panel | Yes | Content area associated with each tab; `role="tabpanel"` |
| Overflow controls | No | Scroll arrows or "more" button when tabs exceed available width |

---

## Variants

| Variant | Description | Active Indicator | Use Case |
|---------|-------------|-----------------|----------|
| Underline | Minimal; text tabs with a bottom border indicator | 2px bottom border in `blue-600` | Default; most contexts, clean appearance |
| Contained | Segmented appearance with filled active tab | `neutral-0` background, elevated above siblings | Settings pages, form sections, grouped options |
| Pill | Rounded capsule for the active tab within a tinted track | `neutral-0` filled pill with shadow | Compact toggles, filters, view switches |

---

## Orientation

| Orientation | Tab List Direction | Active Indicator | Overflow | Use Case |
|-------------|-------------------|-----------------|----------|----------|
| Horizontal | Left to right row | Bottom border (underline) or background fill | Horizontal scroll with arrow buttons | Default; most layouts |
| Vertical | Top to bottom column | Left border (underline) or background fill | Vertical scroll | Side-panel navigation, settings pages, long tab lists |

---

## States

### Underline Tab States

| State | Text Color | Indicator | Background | Notes |
|-------|-----------|-----------|-----------|-------|
| Default | `neutral-600` | none | `transparent` | Resting state |
| Hover | `neutral-900` | faint `neutral-300` underline | `transparent` | Mouse over |
| Active (selected) | `blue-600` | 2px `blue-600` underline | `transparent` | Currently selected tab |
| Focus | `neutral-600` | none | `transparent` | 2px focus ring `blue-600`, 2px offset |
| Disabled | `neutral-300` | none | `transparent` | Non-interactive, skipped in tab order |

### Contained Tab States

| State | Text Color | Background | Border | Notes |
|-------|-----------|-----------|--------|-------|
| Default | `neutral-600` | `neutral-50` | `neutral-200` | Resting, within segmented track |
| Hover | `neutral-900` | `neutral-100` | `neutral-200` | Mouse over |
| Active (selected) | `neutral-900` | `neutral-0` | `neutral-200` | Elevated active, `shadow-sm` |
| Focus | `neutral-600` | `neutral-50` | 2px `blue-600` ring | Keyboard focus |
| Disabled | `neutral-300` | `neutral-50` | `neutral-200` | Non-interactive |

### Pill Tab States

| State | Text Color | Background | Notes |
|-------|-----------|-----------|-------|
| Default | `neutral-600` | `transparent` | Within tinted track `neutral-100` |
| Hover | `neutral-900` | `neutral-50` | Mouse over |
| Active (selected) | `neutral-900` | `neutral-0` | Pill shape, `shadow-sm`, full border-radius |
| Focus | `neutral-600` | `transparent` | 2px focus ring `blue-600` |
| Disabled | `neutral-300` | `transparent` | Non-interactive |

---

## Sizing

| Size | Tab Height | Padding | Font Size | Icon Size | Gap (icon-label) | Indicator Height |
|------|-----------|---------|-----------|-----------|------------------|-----------------|
| sm | 36px | 6px 12px | 13px | 16px | 6px | 2px |
| md | 40px | 8px 16px | 14px | 18px | 8px | 2px |
| lg | 48px | 12px 20px | 16px | 20px | 8px | 3px |

### Contained / Pill Track Sizing

| Property | Value | Token |
|----------|-------|-------|
| Track padding | 4px | `{space.1}` |
| Track border-radius (contained) | `{border.radius.lg}` (8px) | -- |
| Track border-radius (pill) | 9999px (full round) | -- |
| Track background | `neutral-100` | -- |

---

## Overflow Behavior

| Property | Value | Notes |
|----------|-------|-------|
| Scroll type | Horizontal scroll (CSS `overflow-x: auto`) | Smooth scroll behavior |
| Scroll arrows | Appear on hover at edges when content overflows | Fade gradient mask at edges |
| Arrow button size | 32px | Ghost button with chevron icon |
| Scroll amount | One tab width per click | Smooth animated scroll |
| Fade gradient width | 32px | Linear gradient from opaque to transparent |
| Mobile behavior | Free horizontal scroll, no arrows | Native scroll with momentum |

---

## Accessibility

- **Role**: Tab list uses `role="tablist"`. Each tab trigger uses `role="tab"`. Each content panel uses `role="tabpanel"`.
- **ARIA**: Each tab has `aria-selected="true/false"`, `aria-controls="[panel-id]"`, and `id` matching the panel's `aria-labelledby`. Panels use `aria-labelledby="[tab-id]"`.
- **ARIA -- orientation**: Add `aria-orientation="horizontal"` or `aria-orientation="vertical"` to the tablist.
- **Keyboard**:
  - `Tab` moves focus into the tab list (landing on the active tab), then to the tab panel.
  - `Arrow Left` / `Arrow Right` (horizontal) or `Arrow Up` / `Arrow Down` (vertical) moves focus between tabs.
  - `Home` moves focus to the first tab; `End` moves focus to the last tab.
  - `Enter` or `Space` activates the focused tab (if using manual activation).
  - Arrow keys activate tabs immediately in automatic activation mode (recommended).
- **Activation mode**: Automatic activation (arrow keys change selection) is recommended for most cases. Manual activation (arrows move focus, Enter/Space selects) is for expensive tab panel loads.
- **Screen reader**: Announces tab name, position ("tab 2 of 4"), and selected state.
- **Focus**: Visible focus ring on the focused tab. Only the active tab is in the tab sequence; other tabs are navigated via arrow keys.
- **Color**: Active state uses color plus a visual indicator (underline, background, pill) so it is not conveyed by color alone.
- **Motion**: Indicator slide animation and panel transitions respect `prefers-reduced-motion: reduce`.

---

## Design Tokens

```json
{
  "tabs": {
    "font-family": "{typography.font.sans}",
    "font-weight": "500",
    "transition": "all 200ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.600}",
    "underline": {
      "indicator-height": "2px",
      "indicator-color": "{color.blue.600}",
      "text-color": "{color.neutral.600}",
      "text-hover": "{color.neutral.900}",
      "text-active": "{color.blue.600}",
      "text-disabled": "{color.neutral.300}",
      "border-bottom": "1px solid {color.neutral.200}"
    },
    "contained": {
      "track-bg": "{color.neutral.100}",
      "track-border-radius": "{border.radius.lg}",
      "track-padding": "{space.1}",
      "tab-bg": "transparent",
      "tab-bg-hover": "{color.neutral.100}",
      "tab-bg-active": "{color.neutral.0}",
      "tab-shadow-active": "{shadow.sm}",
      "tab-border-radius": "{border.radius.md}",
      "text-color": "{color.neutral.600}",
      "text-active": "{color.neutral.900}"
    },
    "pill": {
      "track-bg": "{color.neutral.100}",
      "track-border-radius": "9999px",
      "track-padding": "{space.1}",
      "pill-bg-active": "{color.neutral.0}",
      "pill-shadow-active": "{shadow.sm}",
      "pill-border-radius": "9999px",
      "text-color": "{color.neutral.600}",
      "text-active": "{color.neutral.900}"
    },
    "sizing": {
      "sm": {
        "height": "36px",
        "padding-x": "{space.3}",
        "padding-y": "{space.1.5}",
        "font-size": "13px",
        "icon-size": "16px",
        "gap": "{space.1.5}"
      },
      "md": {
        "height": "40px",
        "padding-x": "{space.4}",
        "padding-y": "{space.2}",
        "font-size": "{typography.body.md.size}",
        "icon-size": "18px",
        "gap": "{space.2}"
      },
      "lg": {
        "height": "48px",
        "padding-x": "{space.5}",
        "padding-y": "{space.3}",
        "font-size": "{typography.body.lg.size}",
        "icon-size": "20px",
        "gap": "{space.2}"
      }
    },
    "overflow": {
      "arrow-size": "32px",
      "gradient-width": "32px"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use tabs to organize related content that users will switch between frequently on the same page.
- Label tabs with short, descriptive nouns or noun phrases (e.g., "Overview", "Activity", "Settings").
- Pre-select the most commonly used tab as the default.
- Use the underline variant as the default for most contexts.
- Use the pill variant for compact view toggles (e.g., "Grid / List" or "Day / Week / Month").
- Ensure tab panels are immediately accessible without a page reload.

**Don't:**
- Don't use tabs for sequential workflows or wizard-style flows -- use a stepper component instead.
- Don't use more than seven tabs in a single tab list; consolidate or use a different navigation pattern.
- Don't use tabs as page-level navigation -- use the Navigation component for cross-page routing.
- Don't nest tab components inside other tab components; flatten the hierarchy or use a different pattern.
- Don't dynamically add or remove tabs while the user is interacting with them.
- Don't use tabs to compare content side-by-side; all panels should be independent.

---

## Code Example

### HTML

```html
<!-- Underline tabs (horizontal) -->
<div class="ff-tabs ff-tabs--underline ff-tabs--md">
  <div class="ff-tabs__list" role="tablist" aria-label="Account settings" aria-orientation="horizontal">
    <button class="ff-tabs__tab ff-tabs__tab--active" role="tab" id="tab-profile"
            aria-selected="true" aria-controls="panel-profile">
      Profile
    </button>
    <button class="ff-tabs__tab" role="tab" id="tab-security"
            aria-selected="false" aria-controls="panel-security" tabindex="-1">
      Security
    </button>
    <button class="ff-tabs__tab" role="tab" id="tab-billing"
            aria-selected="false" aria-controls="panel-billing" tabindex="-1">
      Billing
    </button>
    <button class="ff-tabs__tab" role="tab" id="tab-disabled"
            aria-selected="false" aria-disabled="true" tabindex="-1" disabled>
      Advanced
    </button>
  </div>
  <div class="ff-tabs__panel" role="tabpanel" id="panel-profile" aria-labelledby="tab-profile">
    <!-- Profile content -->
  </div>
  <div class="ff-tabs__panel" role="tabpanel" id="panel-security" aria-labelledby="tab-security" hidden>
    <!-- Security content -->
  </div>
  <div class="ff-tabs__panel" role="tabpanel" id="panel-billing" aria-labelledby="tab-billing" hidden>
    <!-- Billing content -->
  </div>
</div>

<!-- Tab with icon -->
<button class="ff-tabs__tab" role="tab" aria-selected="false" tabindex="-1">
  <svg class="ff-tabs__icon" aria-hidden="true"><!-- icon --></svg>
  <span class="ff-tabs__label">Activity</span>
</button>

<!-- Pill tabs -->
<div class="ff-tabs ff-tabs--pill ff-tabs--sm">
  <div class="ff-tabs__list ff-tabs__track" role="tablist" aria-label="View toggle">
    <button class="ff-tabs__tab ff-tabs__tab--active" role="tab" aria-selected="true">Grid</button>
    <button class="ff-tabs__tab" role="tab" aria-selected="false" tabindex="-1">List</button>
  </div>
</div>
```

### JSX

```jsx
import { Tabs, TabList, Tab, TabPanel } from '@flaviofusuma/ui';

{/* Underline tabs */}
<Tabs variant="underline" size="md" defaultTab="profile">
  <TabList aria-label="Account settings">
    <Tab id="profile" icon={<UserIcon />}>Profile</Tab>
    <Tab id="security">Security</Tab>
    <Tab id="billing">Billing</Tab>
    <Tab id="advanced" disabled>Advanced</Tab>
  </TabList>
  <TabPanel tabId="profile">
    {/* Profile content */}
  </TabPanel>
  <TabPanel tabId="security">
    {/* Security content */}
  </TabPanel>
  <TabPanel tabId="billing">
    {/* Billing content */}
  </TabPanel>
</Tabs>

{/* Contained tabs */}
<Tabs variant="contained" size="md" defaultTab="overview">
  <TabList aria-label="Dashboard views">
    <Tab id="overview">Overview</Tab>
    <Tab id="analytics">Analytics</Tab>
    <Tab id="reports">Reports</Tab>
  </TabList>
  <TabPanel tabId="overview">{/* content */}</TabPanel>
  <TabPanel tabId="analytics">{/* content */}</TabPanel>
  <TabPanel tabId="reports">{/* content */}</TabPanel>
</Tabs>

{/* Pill tabs for view toggle */}
<Tabs variant="pill" size="sm" defaultTab="grid">
  <TabList aria-label="View toggle">
    <Tab id="grid">Grid</Tab>
    <Tab id="list">List</Tab>
  </TabList>
  <TabPanel tabId="grid">{/* Grid view */}</TabPanel>
  <TabPanel tabId="list">{/* List view */}</TabPanel>
</Tabs>

{/* Vertical tabs */}
<Tabs variant="underline" size="md" orientation="vertical" defaultTab="general">
  <TabList aria-label="Settings categories">
    <Tab id="general">General</Tab>
    <Tab id="notifications">Notifications</Tab>
    <Tab id="integrations">Integrations</Tab>
  </TabList>
  <TabPanel tabId="general">{/* content */}</TabPanel>
  <TabPanel tabId="notifications">{/* content */}</TabPanel>
  <TabPanel tabId="integrations">{/* content */}</TabPanel>
</Tabs>
```

---

## Related Components

- **[Navigation](/02-design-system/05-components/navigation.md)** -- For page-level routing; use tabs for within-page content switching, not cross-page navigation.
- **[Breadcrumbs](/02-design-system/05-components/breadcrumbs.md)** -- For hierarchical position; breadcrumbs show where you are, tabs show what you are looking at.
- **[Accordion](/02-design-system/05-components/accordion.md)** -- For content that benefits from progressive disclosure; accordions show content vertically while tabs switch views.
- **[Buttons](/02-design-system/05-components/buttons.md)** -- Segmented button groups can look similar to contained tabs but trigger actions rather than switching views.
