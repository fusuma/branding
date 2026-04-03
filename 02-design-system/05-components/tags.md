# Tags

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Tags are compact, labeling elements used to categorize, filter, or describe content with keywords or attributes. They provide at-a-glance metadata and can be interactive (removable, clickable) or purely informational. Use tags when content needs categorical labels, filter indicators, or status markers that occupy minimal space.

---

## Anatomy

```
┌─────────────────────────────────┐
│  ┌────┐                ┌─────┐  │
│  │Icon│  [Label Text]  │  X  │  │
│  └────┘                └─────┘  │
└─────────────────────────────────┘
   icon     label       remove
  (opt.)   (required)   (opt.)
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Outer wrapper with background, border, and border-radius |
| Label | Yes | Primary text content describing the tag's meaning |
| Icon | No | Optional leading icon for visual reinforcement (16px / 14px depending on size) |
| Remove button | No | Optional trailing close icon to dismiss or remove the tag |

---

## Variants

| Variant | Background | Border | Text Color | Use Case |
|---------|-----------|--------|------------|----------|
| Default | `neutral-100` #F1F5F9 | `neutral-200` #E2E8F0 | `neutral-700` #334155 | General-purpose labeling, neutral metadata |
| Primary | `blue-50` #EFF6FF | `blue-200` #BFDBFE | `blue-700` #1D4ED8 | Active filters, selected states, brand-associated labels |
| Success | `green-50` #F0FDF4 | `green-200` #BBF7D0 | `green-700` #15803D | Positive statuses, completed items, approved states |
| Warning | `amber-50` #FFFBEB | `amber-200` #FDE68A | `amber-700` #B45309 | Caution indicators, pending states, needs-attention labels |
| Error | `red-50` #FEF2F2 | `red-200` #FECACA | `red-700` #B91C1C | Negative statuses, rejected items, critical labels |
| Outlined | `transparent` | `neutral-300` #CBD5E1 | `neutral-600` #475569 | Subtle labeling where filled backgrounds add too much weight |

---

## States

### Default Variant States

| State | Background | Border | Text | Notes |
|-------|-----------|--------|------|-------|
| Default | `neutral-100` | `neutral-200` | `neutral-700` | Resting state |
| Hover | `neutral-200` | `neutral-300` | `neutral-800` | Only for interactive (clickable/removable) tags |
| Active | `neutral-250` | `neutral-400` | `neutral-900` | Mouse down on interactive tags |
| Focus | `neutral-100` | `blue-600` #2563EB | `neutral-700` | 2px focus ring offset 2px, color `blue-600` |
| Disabled | `neutral-50` | `neutral-100` | `neutral-400` | 50% opacity, pointer-events none |

### Primary Variant States

| State | Background | Border | Text | Notes |
|-------|-----------|--------|------|-------|
| Default | `blue-50` | `blue-200` | `blue-700` | Resting state |
| Hover | `blue-100` | `blue-300` | `blue-800` | Interactive tags only |
| Active | `blue-150` | `blue-400` | `blue-900` | Mouse down |
| Focus | `blue-50` | `blue-600` #2563EB | `blue-700` | 2px focus ring |
| Disabled | `blue-25` | `blue-100` | `blue-300` | Reduced opacity |

### Remove Button States

| State | Icon Color | Background | Notes |
|-------|-----------|-----------|-------|
| Default | `neutral-400` | `transparent` | Resting state |
| Hover | `neutral-600` | `neutral-200` | Circular hover area |
| Active | `neutral-700` | `neutral-300` | Mouse down |
| Focus | `neutral-500` | `transparent` | Focus ring inherits tag focus style |

---

## Sizing

| Size | Height | Padding | Font Size | Line Height | Icon Size | Remove Icon | Border Radius | Gap |
|------|--------|---------|-----------|-------------|-----------|-------------|---------------|-----|
| sm | 24px | 4px 8px | 12px | 16px | 14px | 12px | `sm` 4px | 4px |
| md | 28px | 4px 10px | 14px | 20px | 16px | 14px | `md` 6px | 6px |

---

## Accessibility

- **Role**: Use `<span>` for informational tags. Use `<button>` or add `role="button"` for interactive/clickable tags.
- **ARIA -- removable tags**: The remove button must have `aria-label="Remove [tag label]"` to announce intent clearly.
- **ARIA -- groups**: Wrap tag sets in a container with `role="group"` and `aria-label="[description]"` (e.g., "Applied filters").
- **Keyboard**:
  - Interactive tags are focusable via `Tab`.
  - `Enter` or `Space` activates a clickable tag.
  - `Backspace` or `Delete` removes a removable tag when focused.
  - Focus moves to the next tag after removal, or to the previous tag if the last tag was removed.
- **Screen reader**: Announces the tag label, variant (if semantic), and available actions.
- **Color**: Each variant uses both color and a visible border so meaning is not conveyed by color alone. Pair semantic variants with an icon for reinforcement.
- **Motion**: Remove animation respects `prefers-reduced-motion: reduce`.

---

## Design Tokens

```json
{
  "tag": {
    "border-radius": "{border.radius.md}",
    "font-family": "{typography.font.sans}",
    "font-weight": "500",
    "transition": "all 150ms ease-in-out",
    "gap": "{space.1}",
    "sm": {
      "height": "24px",
      "padding-x": "{space.1}",
      "padding-y": "4px",
      "font-size": "12px",
      "icon-size": "14px",
      "border-radius": "{border.radius.sm}"
    },
    "md": {
      "height": "28px",
      "padding-x": "10px",
      "padding-y": "4px",
      "font-size": "14px",
      "icon-size": "16px",
      "border-radius": "{border.radius.md}"
    },
    "default": {
      "background": "{color.neutral.100}",
      "border-color": "{color.neutral.200}",
      "text-color": "{color.neutral.700}",
      "hover-background": "{color.neutral.200}",
      "hover-border": "{color.neutral.300}"
    },
    "primary": {
      "background": "{color.blue.50}",
      "border-color": "{color.blue.200}",
      "text-color": "{color.blue.700}",
      "hover-background": "{color.blue.100}",
      "hover-border": "{color.blue.300}"
    },
    "success": {
      "background": "{color.green.50}",
      "border-color": "{color.green.200}",
      "text-color": "{color.green.700}",
      "hover-background": "{color.green.100}",
      "hover-border": "{color.green.300}"
    },
    "warning": {
      "background": "{color.amber.50}",
      "border-color": "{color.amber.200}",
      "text-color": "{color.amber.700}",
      "hover-background": "{color.amber.100}",
      "hover-border": "{color.amber.300}"
    },
    "error": {
      "background": "{color.red.50}",
      "border-color": "{color.red.200}",
      "text-color": "{color.red.700}",
      "hover-background": "{color.red.100}",
      "hover-border": "{color.red.300}"
    },
    "outlined": {
      "background": "transparent",
      "border-color": "{color.neutral.300}",
      "text-color": "{color.neutral.600}",
      "hover-background": "{color.neutral.50}",
      "hover-border": "{color.neutral.400}"
    },
    "remove-button": {
      "size": "16px",
      "border-radius": "{border.radius.sm}",
      "hover-background": "{color.neutral.200}"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use tags to display categories, filters, or metadata alongside content.
- Keep tag labels short -- one to three words maximum.
- Use the removable variant for user-applied filters so users can undo selections.
- Group related tags together with consistent sizing.
- Combine an icon with a semantic variant (success, warning, error) to reinforce meaning beyond color.
- Use the `outlined` variant when tags appear on colored or busy backgrounds.

**Don't:**
- Don't use tags as primary action buttons -- use a Button component instead.
- Don't display more than 8-10 visible tags in a single group; use a "+N more" overflow pattern.
- Don't mix tag sizes within the same group.
- Don't use long sentences as tag labels; if more context is needed, use a Tooltip.
- Don't rely solely on the color variant to convey meaning -- always include a text label.
- Don't use the error variant for non-critical information; reserve it for genuinely negative states.

---

## Code Example

### HTML

```html
<!-- Default tag -->
<span class="ff-tag ff-tag--default ff-tag--md">
  <span class="ff-tag__label">Category</span>
</span>

<!-- Primary tag with icon -->
<span class="ff-tag ff-tag--primary ff-tag--md">
  <svg class="ff-tag__icon" aria-hidden="true"><!-- icon SVG --></svg>
  <span class="ff-tag__label">Active</span>
</span>

<!-- Removable success tag -->
<span class="ff-tag ff-tag--success ff-tag--sm" role="group">
  <span class="ff-tag__label">Approved</span>
  <button class="ff-tag__remove" aria-label="Remove Approved">
    <svg aria-hidden="true"><!-- close icon --></svg>
  </button>
</span>

<!-- Tag group with overflow -->
<div class="ff-tag-group" role="group" aria-label="Applied filters">
  <span class="ff-tag ff-tag--primary ff-tag--md">
    <span class="ff-tag__label">Design</span>
    <button class="ff-tag__remove" aria-label="Remove Design">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
  </span>
  <span class="ff-tag ff-tag--primary ff-tag--md">
    <span class="ff-tag__label">Engineering</span>
    <button class="ff-tag__remove" aria-label="Remove Engineering">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
  </span>
  <span class="ff-tag ff-tag--outlined ff-tag--md">
    <span class="ff-tag__label">+3 more</span>
  </span>
</div>
```

### JSX

```jsx
import { Tag, TagGroup } from '@flaviofusuma/ui';

{/* Simple tag */}
<Tag variant="default" size="md">Category</Tag>

{/* Primary with icon */}
<Tag variant="primary" size="md" icon={<StarIcon />}>
  Featured
</Tag>

{/* Removable tag */}
<Tag
  variant="success"
  size="sm"
  removable
  onRemove={() => handleRemove('approved')}
>
  Approved
</Tag>

{/* Tag group for filters */}
<TagGroup aria-label="Applied filters">
  {filters.map((filter) => (
    <Tag
      key={filter.id}
      variant="primary"
      size="md"
      removable
      onRemove={() => removeFilter(filter.id)}
    >
      {filter.label}
    </Tag>
  ))}
</TagGroup>
```

---

## Related Components

- **[Badge](/02-design-system/05-components/badges.md)** -- For numeric indicators and status dots; badges are non-interactive and typically smaller.
- **[Button](/02-design-system/05-components/buttons.md)** -- For primary actions; use buttons when the element triggers a significant action rather than labeling content.
- **[Checkbox](/02-design-system/05-components/checkbox.md)** -- For multi-select in forms; prefer checkboxes over clickable tags when collecting form data.
- **[Alerts](/02-design-system/05-components/alerts.md)** -- For prominent status messaging; use alerts when the semantic message needs more visibility than a tag provides.
