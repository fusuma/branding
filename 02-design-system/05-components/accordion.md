# Accordion

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Accordions organize content into collapsible sections, allowing users to expand and collapse panels to reveal or hide information progressively. They reduce visual clutter by showing only the content the user is interested in. Use accordions for FAQs, settings panels, navigation menus, and any content where users need to scan headings before diving into details.

---

## Anatomy

```
Bordered accordion:
┌───────────────────────────────────────────────────┐
│  ┌──────────────────────────────────────────────┐  │
│  │  ┌────┐                              ┌───┐  │  │
│  │  │Icon│  [Header Title]              │ ▼ │  │  │
│  │  └────┘  [Subtitle]                  └───┘  │  │
│  ├──────────────────────────────────────────────┤  │
│  │                                              │  │
│  │  Panel content goes here. It can contain     │  │
│  │  any content: text, images, forms, or        │  │
│  │  nested components.                          │  │
│  │                                              │  │
│  └──────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────┐  │
│  │  [Header Title 2]                     │ ▶ │  │  │
│  └──────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────┐  │
│  │  [Header Title 3]                     │ ▶ │  │  │
│  └──────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────┘

Flush accordion:
──────────────────────────────────────────
  [Header Title 1]                  │ ▼ │
──────────────────────────────────────────
  Panel content here.

──────────────────────────────────────────
  [Header Title 2]                  │ ▶ │
──────────────────────────────────────────
  [Header Title 3]                  │ ▶ │
──────────────────────────────────────────

Nested accordion:
┌──────────────────────────────────────────────┐
│  [Parent Header]                       │ ▼ │ │
├──────────────────────────────────────────────┤
│  Some parent content.                        │
│  ┌────────────────────────────────────────┐  │
│  │  [Nested Header A]              │ ▼ │  │  │
│  ├────────────────────────────────────────┤  │
│  │  Nested panel content A.              │  │
│  └────────────────────────────────────────┘  │
│  ┌────────────────────────────────────────┐  │
│  │  [Nested Header B]              │ ▶ │  │  │
│  └────────────────────────────────────────┘  │
└──────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Accordion container | Yes | Outer wrapper grouping all accordion items |
| Accordion item | Yes | Individual collapsible section (header + panel) |
| Header / Trigger | Yes | Clickable area that toggles the panel; contains title text |
| Title | Yes | Primary heading text describing the panel content |
| Subtitle | No | Secondary descriptive text below the title |
| Leading icon | No | Optional icon before the title for visual context |
| Expand icon | Yes | Chevron or plus/minus icon indicating expand/collapse state |
| Panel | Yes | Collapsible content area revealed when the item is expanded |

---

## Variants

| Variant | Description | Visual Treatment |
|---------|-------------|-----------------|
| Bordered | Contained items with visible borders | Each item has a border, items separated by dividers, outer container border with `border-radius.lg` |
| Flush | Borderless items separated by dividers | No outer border or background; items separated by 1px `neutral-200` dividers |
| Separated | Individually bordered items with gap | Each item is a standalone card with its own border and border-radius, 8px gap between items |

---

## Expand Behavior

| Mode | Description | Use Case |
|------|-------------|----------|
| Single expand | Only one panel open at a time; opening one closes others | Settings panels, FAQs where context switching is expected |
| Multi expand | Multiple panels can be open simultaneously | Documentation, content exploration where comparison is useful |
| Default expanded | Specific items start in the expanded state on mount | Pre-opening the most relevant or first section |
| Disabled items | Individual items can be disabled (non-expandable) | Locked or unavailable content sections |

---

## Icon Animation

| Icon Style | Collapsed State | Expanded State | Animation |
|-----------|----------------|----------------|-----------|
| Chevron (default) | `chevron-right` (▶) | `chevron-down` (▼) | 90-degree rotation, 200ms ease |
| Plus/Minus | `plus` (+) | `minus` (-) | Cross-fade, 200ms ease |
| Arrow | `arrow-down` | `arrow-up` | 180-degree rotation, 200ms ease |

---

## States

### Header / Trigger States

| State | Background | Text | Icon | Border | Notes |
|-------|-----------|------|------|--------|-------|
| Collapsed | `transparent` | `neutral-900` | `neutral-400` | `neutral-200` | Resting closed state |
| Collapsed hover | `neutral-50` | `neutral-900` | `neutral-600` | `neutral-200` | Mouse over |
| Expanded | `transparent` | `neutral-900` | `blue-600` | `neutral-200` | Panel is open |
| Expanded hover | `neutral-50` | `neutral-900` | `blue-700` | `neutral-200` | Hover while expanded |
| Focus | `transparent` | `neutral-900` | `neutral-400` | `neutral-200` | 2px focus ring `blue-600`, inset |
| Disabled | `transparent` | `neutral-300` | `neutral-200` | `neutral-100` | Not expandable |

### Panel States

| State | Description | Animation |
|-------|-------------|-----------|
| Entering | Panel expanding from 0 height | `max-height` animation, 250ms ease-out |
| Visible | Panel fully expanded | Static, no animation |
| Exiting | Panel collapsing to 0 height | `max-height` animation, 200ms ease-in |
| Hidden | Panel collapsed, not visible | `display: none` after animation completes |

---

## Sizing

| Property | Value | Token |
|----------|-------|-------|
| Header min height | 48px | -- |
| Header padding | 16px | `{space.4}` |
| Header font size | 16px / semi-bold (600) | `{typography.body.lg}` |
| Subtitle font size | 14px / regular (400) | `{typography.body.md}` |
| Subtitle color | `neutral-500` | -- |
| Leading icon size | 20px | -- |
| Expand icon size | 20px | -- |
| Icon-to-title gap | 12px | `{space.3}` |
| Title-to-icon gap (trailing) | 12px | `{space.3}` |
| Title-to-subtitle gap | 4px | `{space.1}` |
| Panel padding | 0 16px 16px 16px | `{space.4}` (with 0 top when adjacent to header) |
| Panel font size | 14px / regular (400) | `{typography.body.md}` |
| Panel text color | `neutral-600` | -- |
| Item divider | 1px `neutral-200` | -- |
| Bordered container border | 1px `neutral-200` | -- |
| Bordered container radius | 8px | `{border.radius.lg}` |
| Separated item radius | 8px | `{border.radius.lg}` |
| Separated item gap | 8px | `{space.2}` |
| Nested indent | 0 (nested uses its own padding) | -- |
| Max nesting depth | 2 levels recommended | -- |

---

## Accessibility

- **Role**: The accordion container does not require a special role. Each header/trigger is a `<button>` (or `<h3>` wrapping a `<button>`). Each panel uses `role="region"` with `aria-labelledby` pointing to the header button.
- **ARIA -- header button**: Use `aria-expanded="true/false"` and `aria-controls="[panel-id]"` on the trigger button.
- **ARIA -- panel**: Use `id` matching the trigger's `aria-controls`, and `aria-labelledby="[trigger-id]"`.
- **ARIA -- disabled**: Use `aria-disabled="true"` on disabled accordion triggers. Disabled items remain focusable for discoverability.
- **Keyboard**:
  - `Tab` / `Shift+Tab` moves focus between accordion headers.
  - `Enter` or `Space` toggles the focused accordion item.
  - `Arrow Down` moves focus to the next header.
  - `Arrow Up` moves focus to the previous header.
  - `Home` moves focus to the first header.
  - `End` moves focus to the last header.
- **Screen reader**: Announces the heading text, expanded/collapsed state, and position (e.g., "FAQ item 1, expanded, 2 of 5").
- **Focus**: Visible focus ring on the header button. Focus does not move into the panel automatically on expand.
- **Color**: Expanded state uses icon color change plus rotation; not conveyed by color alone.
- **Motion**: Expand/collapse animation respects `prefers-reduced-motion: reduce` by using instant show/hide.
- **Heading structure**: Accordion headers should use proper heading levels (`<h3>`, `<h4>`) to maintain document outline. The heading level should match the surrounding content hierarchy.

---

## Design Tokens

```json
{
  "accordion": {
    "font-family": "{typography.font.sans}",
    "transition-expand": "250ms ease-out",
    "transition-collapse": "200ms ease-in",
    "icon-rotation": "90deg",
    "focus-ring-width": "2px",
    "focus-ring-color": "{color.blue.600}",
    "header": {
      "min-height": "48px",
      "padding": "{space.4}",
      "font-size": "{typography.body.lg.size}",
      "font-weight": "600",
      "text-color": "{color.neutral.900}",
      "text-disabled": "{color.neutral.300}",
      "bg": "transparent",
      "bg-hover": "{color.neutral.50}",
      "subtitle-font-size": "{typography.body.md.size}",
      "subtitle-color": "{color.neutral.500}"
    },
    "icon": {
      "size": "20px",
      "color": "{color.neutral.400}",
      "color-hover": "{color.neutral.600}",
      "color-expanded": "{color.blue.600}",
      "color-disabled": "{color.neutral.200}",
      "gap": "{space.3}"
    },
    "panel": {
      "padding": "0 {space.4} {space.4} {space.4}",
      "font-size": "{typography.body.md.size}",
      "text-color": "{color.neutral.600}",
      "line-height": "1.6"
    },
    "bordered": {
      "border-color": "{color.neutral.200}",
      "border-width": "1px",
      "border-radius": "{border.radius.lg}",
      "divider-color": "{color.neutral.200}"
    },
    "flush": {
      "divider-color": "{color.neutral.200}"
    },
    "separated": {
      "border-color": "{color.neutral.200}",
      "border-width": "1px",
      "border-radius": "{border.radius.lg}",
      "gap": "{space.2}"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use accordions to organize lengthy content into scannable sections with clear, descriptive headings.
- Default to single-expand mode for settings and configuration panels to reduce cognitive load.
- Use multi-expand mode for reference content (FAQs, documentation) where users may want to see multiple sections.
- Keep heading text concise and descriptive -- users scan headings to find the content they need.
- Use the bordered variant for standalone accordion groups and the flush variant when embedded within other containers.
- Pre-expand the most relevant section on page load when there is a clear default.

**Don't:**
- Don't nest more than two levels of accordions; flatten the hierarchy or use a different pattern.
- Don't use accordions to hide critical content that users must see (e.g., required form fields, error messages).
- Don't use accordions with only one item; show the content directly instead.
- Don't place accordions inside other scrollable containers where the height change could cause layout confusion.
- Don't auto-collapse sections the user has opened unless using single-expand mode intentionally.
- Don't use accordions for sequential workflows; use a stepper component instead.

---

## Code Example

### HTML

```html
<!-- Bordered accordion (single expand) -->
<div class="ff-accordion ff-accordion--bordered" data-single-expand="true">
  <div class="ff-accordion__item ff-accordion__item--expanded">
    <h3 class="ff-accordion__header">
      <button class="ff-accordion__trigger" id="acc1-trigger"
              aria-expanded="true" aria-controls="acc1-panel">
        <svg class="ff-accordion__leading-icon" aria-hidden="true"><!-- icon --></svg>
        <span class="ff-accordion__title">What is your return policy?</span>
        <svg class="ff-accordion__expand-icon" aria-hidden="true"><!-- chevron --></svg>
      </button>
    </h3>
    <div class="ff-accordion__panel" id="acc1-panel" role="region" aria-labelledby="acc1-trigger">
      <div class="ff-accordion__content">
        You can return any item within 30 days of purchase for a full refund.
        Items must be in original condition with all tags attached.
      </div>
    </div>
  </div>
  <div class="ff-accordion__item">
    <h3 class="ff-accordion__header">
      <button class="ff-accordion__trigger" id="acc2-trigger"
              aria-expanded="false" aria-controls="acc2-panel">
        <span class="ff-accordion__title">How long does shipping take?</span>
        <svg class="ff-accordion__expand-icon" aria-hidden="true"><!-- chevron --></svg>
      </button>
    </h3>
    <div class="ff-accordion__panel" id="acc2-panel" role="region" aria-labelledby="acc2-trigger" hidden>
      <div class="ff-accordion__content">
        Standard shipping takes 5-7 business days. Express shipping is available
        for 2-3 business day delivery.
      </div>
    </div>
  </div>
  <div class="ff-accordion__item ff-accordion__item--disabled">
    <h3 class="ff-accordion__header">
      <button class="ff-accordion__trigger" id="acc3-trigger"
              aria-expanded="false" aria-controls="acc3-panel" aria-disabled="true">
        <span class="ff-accordion__title">International shipping (coming soon)</span>
        <svg class="ff-accordion__expand-icon" aria-hidden="true"><!-- chevron --></svg>
      </button>
    </h3>
  </div>
</div>

<!-- Flush accordion (multi expand) -->
<div class="ff-accordion ff-accordion--flush">
  <div class="ff-accordion__item">
    <h3 class="ff-accordion__header">
      <button class="ff-accordion__trigger" aria-expanded="false" aria-controls="flush-panel1">
        <span class="ff-accordion__title">General Settings</span>
        <span class="ff-accordion__subtitle">Language, timezone, and display preferences</span>
        <svg class="ff-accordion__expand-icon" aria-hidden="true"><!-- chevron --></svg>
      </button>
    </h3>
    <div class="ff-accordion__panel" id="flush-panel1" role="region" hidden>
      <div class="ff-accordion__content">
        <!-- Settings form content -->
      </div>
    </div>
  </div>
</div>
```

### JSX

```jsx
import { Accordion, AccordionItem } from '@flaviofusuma/ui';

{/* Bordered accordion, single expand */}
<Accordion variant="bordered" singleExpand defaultExpanded={['faq-1']}>
  <AccordionItem
    id="faq-1"
    title="What is your return policy?"
    icon={<ReturnIcon />}
  >
    You can return any item within 30 days of purchase for a full refund.
    Items must be in original condition with all tags attached.
  </AccordionItem>
  <AccordionItem id="faq-2" title="How long does shipping take?">
    Standard shipping takes 5-7 business days. Express shipping is available
    for 2-3 business day delivery.
  </AccordionItem>
  <AccordionItem id="faq-3" title="International shipping (coming soon)" disabled>
    Coming soon.
  </AccordionItem>
</Accordion>

{/* Flush accordion, multi expand */}
<Accordion variant="flush">
  <AccordionItem title="General Settings" subtitle="Language, timezone, and display preferences">
    {/* Settings form */}
  </AccordionItem>
  <AccordionItem title="Notifications" subtitle="Email, push, and in-app preferences">
    {/* Notification settings */}
  </AccordionItem>
</Accordion>

{/* Separated accordion with plus/minus icons */}
<Accordion variant="separated" iconStyle="plus-minus">
  <AccordionItem title="Section A">Content A</AccordionItem>
  <AccordionItem title="Section B">Content B</AccordionItem>
  <AccordionItem title="Section C">Content C</AccordionItem>
</Accordion>

{/* Nested accordion */}
<Accordion variant="bordered">
  <AccordionItem title="Parent Section">
    <p>Some parent content.</p>
    <Accordion variant="flush">
      <AccordionItem title="Nested Item A">Nested content A.</AccordionItem>
      <AccordionItem title="Nested Item B">Nested content B.</AccordionItem>
    </Accordion>
  </AccordionItem>
</Accordion>
```

---

## Related Components

- **[Tabs](/02-design-system/05-components/tabs.md)** -- For switching between views; tabs show one view at a time horizontally, accordions reveal content vertically.
- **[Navigation](/02-design-system/05-components/navigation.md)** -- Sidebar navigation can use accordion patterns for collapsible sections.
- **[Cards](/02-design-system/05-components/cards.md)** -- The separated accordion variant resembles stacked cards with expand/collapse behavior.
- **[Divider](/02-design-system/05-components/divider.md)** -- Flush accordions use dividers between items; the divider component provides consistent separator styling.
