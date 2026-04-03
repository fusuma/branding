# Badges

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Badges are compact visual indicators that convey status, category, or count information. They appear alongside or overlaid on other elements to draw attention to a state change, label, or numeric value. Badges are non-interactive by default but can include a remove action for dismissible labels. Use badges to communicate metadata at a glance without interrupting the user's primary workflow.

---

## Anatomy

```
Standard badge:
┌──────────────────────┐
│  [Label Text]        │
└──────────────────────┘

Badge with dot indicator:
┌──────────────────────┐
│  ●  [Label Text]     │
└──────────────────────┘

Badge with remove action:
┌──────────────────────────┐
│  [Label Text]   ┌─────┐ │
│                  │  ✕  │ │
│                  └─────┘ │
└──────────────────────────┘

Badge with dot and remove:
┌──────────────────────────────┐
│  ●  [Label Text]   ┌─────┐  │
│                     │  ✕  │  │
│                     └─────┘  │
└──────────────────────────────┘

Notification badge (count overlay):
┌────────┐
│  Icon  │
│    ┌───┤
│    │ 5 │
└────┴───┘
```

| Part           | Required | Description                                              |
|----------------|----------|----------------------------------------------------------|
| Container      | Yes      | Outer wrapper with background color and border-radius     |
| Label text     | Yes      | Short text describing the status or category              |
| Dot indicator  | No       | Small colored circle reinforcing the semantic color        |
| Remove button  | No       | Close icon button for dismissible badges                   |
| Count          | No       | Numeric value for notification-style badges                |

---

## Variants

| Variant    | Background     | Text Color     | Dot Color      | Use Case                                        |
|------------|----------------|----------------|----------------|--------------------------------------------------|
| Default    | `blue-100`     | `blue-700`     | `blue-600`     | General labels, default categorization            |
| Success    | `green-100`    | `green-700`    | `green-600`    | Completed, active, published, approved            |
| Warning    | `amber-100`    | `amber-700`    | `amber-500`    | Pending, in review, needs attention               |
| Error      | `red-100`      | `red-700`      | `red-600`      | Failed, rejected, expired, critical               |
| Info       | `blue-100`     | `blue-700`     | `blue-600`     | Informational labels, metadata                    |
| Neutral    | `neutral-100`  | `neutral-700`  | `neutral-500`  | Generic labels, tags, non-semantic categorization |

### Variant Visual Reference

```
┌──────────┐  ┌──────────┐  ┌──────────┐
│ Default  │  │ Success  │  │ Warning  │
│ (blue)   │  │ (green)  │  │ (amber)  │
└──────────┘  └──────────┘  └──────────┘

┌──────────┐  ┌──────────┐  ┌──────────┐
│  Error   │  │   Info   │  │ Neutral  │
│  (red)   │  │  (blue)  │  │  (gray)  │
└──────────┘  └──────────┘  └──────────┘
```

### Sub-Variants

| Sub-Variant | Description                                      | Visual Treatment                                |
|-------------|--------------------------------------------------|-------------------------------------------------|
| Filled      | Solid light background (default)                  | Colored background, darker text                  |
| Outlined    | Transparent background with colored border         | Border matches variant color, no fill            |
| Solid       | Strong background with white text                  | Full-saturation background (e.g., `blue-600` bg, `white` text) |

---

## States

### Standard Badge (non-interactive)

| State    | Background       | Text            | Border         | Notes                       |
|----------|------------------|-----------------|----------------|-----------------------------|
| Default  | per variant      | per variant     | none           | Resting state               |

### Badge with Remove Button

| State                | Remove BG        | Remove Icon     | Notes                        |
|----------------------|------------------|-----------------|------------------------------|
| Default              | `transparent`    | variant text color | Resting state             |
| Remove hover         | variant bg (darker) | variant text (darker) | Mouse over remove button |
| Remove focus         | `transparent`    | variant text    | 2px focus ring               |
| Remove active        | variant bg (darkest) | variant text (darkest) | Pressed             |

### Detailed Remove States per Variant

| Variant  | Remove Hover BG  | Remove Active BG | Remove Icon Color |
|----------|------------------|------------------|-------------------|
| Default  | `blue-200`       | `blue-300`       | `blue-700`        |
| Success  | `green-200`      | `green-300`      | `green-700`       |
| Warning  | `amber-200`      | `amber-300`      | `amber-700`       |
| Error    | `red-200`        | `red-300`        | `red-700`         |
| Info     | `blue-200`       | `blue-300`       | `blue-700`        |
| Neutral  | `neutral-200`    | `neutral-300`    | `neutral-700`     |

---

## Sizing

| Size | Height | Padding (y / x) | Font Size | Line Height | Dot Size | Remove Icon Size | Border Radius |
|------|--------|------------------|-----------|-------------|----------|------------------|---------------|
| sm   | 20px   | 2px / 6px        | 12px      | 16px        | 6px      | 12px             | `full` (9999px) |
| md   | 24px   | 2px / 8px        | 14px      | 20px        | 8px      | 14px             | `full` (9999px) |

### Spacing Details

| Property                     | sm      | md      | Token       |
|------------------------------|---------|---------|-------------|
| Dot to label gap             | 4px     | 6px     | `{space.1}` / `{space.1.5}` |
| Label to remove button gap   | 2px     | 4px     | --          |
| Remove button padding        | 2px     | 2px     | --          |
| Remove button border-radius  | `full`  | `full`  | `{border.radius.full}` |

### Notification Count Badge

| Property          | Value     | Notes                                    |
|-------------------|-----------|------------------------------------------|
| Min width         | 18px      | Ensures circular shape for single digit  |
| Height            | 18px      | Fixed height                             |
| Padding           | 0 4px     | Horizontal padding for multi-digit       |
| Font size         | 11px      | Compact for overlay positioning          |
| Font weight       | 600       | Bold for readability at small size       |
| Border radius     | `full`    | Pill shape                               |
| Background        | `red-600` | High-contrast for attention              |
| Text color        | `white`   | Maximum contrast on red                  |
| Border            | 2px `white` | Creates separation from parent element |
| Max value display | "99+"     | Truncate counts above 99                 |

---

## Dot Indicator

The dot indicator is a small circle that appears before the label text, reinforcing the badge's semantic meaning with a secondary visual cue.

| Property    | sm    | md    |
|-------------|-------|-------|
| Size        | 6px   | 8px   |
| Shape       | Circle| Circle|
| Color       | Matches variant accent color |
| Margin right| 4px   | 6px   |

The dot is purely decorative and should be hidden from assistive technology with `aria-hidden="true"`.

---

## Accessibility

- **Role**: Badges are static elements by default and do not require a specific ARIA role. They are announced as part of the surrounding text content.
- **Remove button**: The remove button must have an accessible label: `aria-label="Remove [badge label]"` (e.g., `aria-label="Remove Design"`). Use `<button>` element for proper semantics.
- **Keyboard**:
  - Standard badges are not focusable (they are informational).
  - Badges with a remove button: the remove button is focusable via `Tab`. `Enter` or `Space` activates removal.
- **Color**: Badges pair color with text labels so meaning is not conveyed by color alone. The dot indicator is supplementary, not the sole conveyor of meaning.
- **Contrast**: All variant text/background combinations meet WCAG AA (4.5:1). Notification count (`white` on `red-600`) meets WCAG AA.
- **Screen reader**: Badge text is read as inline content. For notification count badges, provide `aria-label` on the parent element: `aria-label="Notifications, 5 unread"`.
- **Live regions**: When badge counts update dynamically, wrap the count in `aria-live="polite"` so screen readers announce changes.
- **Motion**: Badge appearance/removal animations respect `prefers-reduced-motion: reduce`.

---

## Design Tokens

```json
{
  "badge": {
    "font-family": "{typography.font.sans}",
    "font-weight": "500",
    "border-radius": "{border.radius.full}",
    "transition": "background 150ms ease, opacity 150ms ease",
    "default": {
      "bg": "{color.blue.100}",
      "text": "{color.blue.700}",
      "dot": "{color.blue.600}",
      "remove-hover-bg": "{color.blue.200}",
      "remove-active-bg": "{color.blue.300}"
    },
    "success": {
      "bg": "{color.green.100}",
      "text": "{color.green.700}",
      "dot": "{color.green.600}",
      "remove-hover-bg": "{color.green.200}",
      "remove-active-bg": "{color.green.300}"
    },
    "warning": {
      "bg": "{color.amber.100}",
      "text": "{color.amber.700}",
      "dot": "{color.amber.500}",
      "remove-hover-bg": "{color.amber.200}",
      "remove-active-bg": "{color.amber.300}"
    },
    "error": {
      "bg": "{color.red.100}",
      "text": "{color.red.700}",
      "dot": "{color.red.600}",
      "remove-hover-bg": "{color.red.200}",
      "remove-active-bg": "{color.red.300}"
    },
    "info": {
      "bg": "{color.blue.100}",
      "text": "{color.blue.700}",
      "dot": "{color.blue.600}",
      "remove-hover-bg": "{color.blue.200}",
      "remove-active-bg": "{color.blue.300}"
    },
    "neutral": {
      "bg": "{color.neutral.100}",
      "text": "{color.neutral.700}",
      "dot": "{color.neutral.500}",
      "remove-hover-bg": "{color.neutral.200}",
      "remove-active-bg": "{color.neutral.300}"
    },
    "outlined": {
      "bg": "transparent",
      "border-width": "1px"
    },
    "solid": {
      "default-bg": "{color.blue.600}",
      "success-bg": "{color.green.600}",
      "warning-bg": "{color.amber.500}",
      "error-bg": "{color.red.600}",
      "info-bg": "{color.blue.600}",
      "neutral-bg": "{color.neutral.600}",
      "text": "{color.white}"
    },
    "notification": {
      "bg": "{color.red.600}",
      "text": "{color.white}",
      "font-size": "11px",
      "font-weight": "600",
      "min-width": "18px",
      "height": "18px",
      "padding": "0 4px",
      "border": "2px solid {color.white}",
      "border-radius": "{border.radius.full}",
      "max-display": "99+"
    },
    "dot": {
      "sm": "6px",
      "md": "8px"
    },
    "sizing": {
      "sm": {
        "height": "20px",
        "padding-x": "{space.1.5}",
        "padding-y": "2px",
        "font-size": "12px",
        "line-height": "16px",
        "remove-icon-size": "12px",
        "dot-gap": "{space.1}"
      },
      "md": {
        "height": "24px",
        "padding-x": "{space.2}",
        "padding-y": "2px",
        "font-size": "{typography.body.sm.size}",
        "line-height": "20px",
        "remove-icon-size": "14px",
        "dot-gap": "{space.1.5}"
      }
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use badges to communicate status (active, pending, failed), category (design, engineering), or counts (3 new messages).
- Keep badge labels short -- one or two words maximum.
- Use semantic colors consistently: green for positive/active, red for errors/critical, amber for warnings/pending.
- Pair the dot indicator with the label when you want to reinforce the status color.
- Use the remove action for user-generated tags, filters, or selections that can be dismissed.
- Use the notification count badge on icons (bell, inbox) to indicate unread items.
- Truncate notification counts above 99 with "99+".

**Don't:**
- Don't use badges for primary actions or navigation -- they are informational indicators.
- Don't use more than 3-4 badges in a single row -- it creates visual noise and reduces scanning efficiency.
- Don't use long text in badges -- if you need more than two words, consider a different component (alert, tag, or label).
- Don't rely on badge color alone to convey meaning -- always include a text label.
- Don't place remove actions on badges that represent immutable system states (e.g., "Admin" role badge).
- Don't override token colors with hardcoded hex values.
- Don't use badges to replace proper form validation messages.
- Don't mix badge sizes within the same context -- maintain consistency.

---

## Code Example

### HTML

```html
<!-- Default badge -->
<span class="ff-badge ff-badge--default ff-badge--md">
  Design
</span>

<!-- Success badge with dot -->
<span class="ff-badge ff-badge--success ff-badge--md">
  <span class="ff-badge__dot" aria-hidden="true"></span>
  Active
</span>

<!-- Warning badge -->
<span class="ff-badge ff-badge--warning ff-badge--sm">
  Pending Review
</span>

<!-- Error badge -->
<span class="ff-badge ff-badge--error ff-badge--md">
  Failed
</span>

<!-- Info badge -->
<span class="ff-badge ff-badge--info ff-badge--md">
  New
</span>

<!-- Neutral badge -->
<span class="ff-badge ff-badge--neutral ff-badge--md">
  Draft
</span>

<!-- Badge with remove action -->
<span class="ff-badge ff-badge--default ff-badge--md ff-badge--removable">
  Frontend
  <button class="ff-badge__remove" aria-label="Remove Frontend">
    <svg aria-hidden="true"><!-- close icon --></svg>
  </button>
</span>

<!-- Badge with dot and remove -->
<span class="ff-badge ff-badge--success ff-badge--md ff-badge--removable">
  <span class="ff-badge__dot" aria-hidden="true"></span>
  Published
  <button class="ff-badge__remove" aria-label="Remove Published filter">
    <svg aria-hidden="true"><!-- close icon --></svg>
  </button>
</span>

<!-- Outlined badge -->
<span class="ff-badge ff-badge--default ff-badge--md ff-badge--outlined">
  v2.1.0
</span>

<!-- Solid badge -->
<span class="ff-badge ff-badge--error ff-badge--sm ff-badge--solid">
  Critical
</span>

<!-- Notification count badge on an icon -->
<button class="ff-btn ff-btn--ghost ff-btn--md ff-btn--icon-only" aria-label="Notifications, 5 unread">
  <svg aria-hidden="true"><!-- bell icon --></svg>
  <span class="ff-badge ff-badge--notification" aria-hidden="true">5</span>
</button>

<!-- Notification count badge (99+) -->
<button class="ff-btn ff-btn--ghost ff-btn--md ff-btn--icon-only" aria-label="Messages, more than 99 unread">
  <svg aria-hidden="true"><!-- inbox icon --></svg>
  <span class="ff-badge ff-badge--notification" aria-hidden="true">99+</span>
</button>

<!-- Badge group (e.g., filter tags) -->
<div class="ff-badge-group" role="list" aria-label="Active filters">
  <span class="ff-badge ff-badge--default ff-badge--md ff-badge--removable" role="listitem">
    Design
    <button class="ff-badge__remove" aria-label="Remove Design filter">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
  </span>
  <span class="ff-badge ff-badge--default ff-badge--md ff-badge--removable" role="listitem">
    In Progress
    <button class="ff-badge__remove" aria-label="Remove In Progress filter">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
  </span>
  <span class="ff-badge ff-badge--default ff-badge--md ff-badge--removable" role="listitem">
    High Priority
    <button class="ff-badge__remove" aria-label="Remove High Priority filter">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
  </span>
</div>

<!-- Status badge in a table row -->
<td>
  <span class="ff-badge ff-badge--success ff-badge--sm">
    <span class="ff-badge__dot" aria-hidden="true"></span>
    Active
  </span>
</td>
```

### JSX

```jsx
import { Badge, BadgeGroup } from '@flavio-fusuma/ui';
import { Button } from '@flavio-fusuma/ui';
import { BellIcon } from '@flavio-fusuma/icons';

// Default badge
<Badge variant="default" size="md">Design</Badge>

// Success badge with dot
<Badge variant="success" size="md" dot>Active</Badge>

// Warning badge
<Badge variant="warning" size="sm">Pending Review</Badge>

// Error badge
<Badge variant="error" size="md">Failed</Badge>

// Neutral badge
<Badge variant="neutral" size="md">Draft</Badge>

// Badge with remove action
<Badge variant="default" size="md" onRemove={() => handleRemove('frontend')}>
  Frontend
</Badge>

// Badge with dot and remove
<Badge variant="success" size="md" dot onRemove={() => handleRemove('published')}>
  Published
</Badge>

// Outlined sub-variant
<Badge variant="default" size="md" appearance="outlined">v2.1.0</Badge>

// Solid sub-variant
<Badge variant="error" size="sm" appearance="solid">Critical</Badge>

// Notification count badge
<Button variant="ghost" size="md" iconOnly aria-label="Notifications, 5 unread">
  <BellIcon />
  <Badge variant="notification" count={5} />
</Button>

// Notification count badge (overflow)
<Button variant="ghost" size="md" iconOnly aria-label="Messages, more than 99 unread">
  <InboxIcon />
  <Badge variant="notification" count={142} maxCount={99} />
</Button>

// Badge group (filter tags)
<BadgeGroup label="Active filters">
  {filters.map(filter => (
    <Badge
      key={filter.id}
      variant="default"
      size="md"
      onRemove={() => removeFilter(filter.id)}
    >
      {filter.label}
    </Badge>
  ))}
</BadgeGroup>

// Dynamic status badge
<Badge
  variant={status === 'active' ? 'success' : status === 'pending' ? 'warning' : 'error'}
  size="sm"
  dot
>
  {status}
</Badge>
```

---

## Related Components

- **[Buttons](./buttons.md)** -- Badges may appear adjacent to buttons or within button labels to show counts.
- **[Cards](./cards.md)** -- Badges are used in card headers and overlays to indicate status or category.
- **[Tags](./tags.md)** -- Tags are similar to badges but are typically larger, always interactive, and used for content categorization.
- **[Tooltips](./tooltips.md)** -- Tooltips can provide additional context when badge labels are abbreviated or ambiguous.
- **[Alerts](./alerts.md)** -- For page-level status messages, use alerts instead of badges.
- **[Toggle](./toggle.md)** -- For active/inactive states that the user can control, use a toggle rather than a badge.
