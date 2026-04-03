# Buttons

> Buttons are the primary interactive elements in the Flavio Fusuma Design System. They trigger actions, submit forms, and navigate users through workflows. Use buttons to communicate what will happen when the user interacts with them.

---

## Overview

Buttons allow users to take actions and make choices with a single tap or click. They communicate the importance and hierarchy of actions on a page. Every screen should have a clear primary action; secondary, outline, ghost, danger, and link variants support the visual hierarchy around that primary action.

---

## Anatomy

```
┌─────────────────────────────────────────┐
│  Button Container                       │
│  ┌──────┐                               │
│  │ Icon │  [Label Text]  [Trailing Icon] │
│  └──────┘                               │
│         ┌──────────────┐                │
│         │ Loading Spinner │              │
│         └──────────────┘                │
└─────────────────────────────────────────┘

Icon-only variant:
┌────────┐
│  ┌──┐  │
│  │🔍│  │
│  └──┘  │
└────────┘
```

| Part            | Required | Description                                        |
|-----------------|----------|----------------------------------------------------|
| Container       | Yes      | The outer button element with background and border |
| Label Text      | Yes*     | Primary text describing the action (* not required for icon-only) |
| Leading Icon    | No       | Optional icon before the label text                 |
| Trailing Icon   | No       | Optional icon after the label text                  |
| Loading Spinner | No       | Replaces content during loading state               |

---

## Variants

| Variant     | Description                                | Use Case                                     |
|-------------|--------------------------------------------|----------------------------------------------|
| Primary     | Solid blue-600 background, white text      | Main call-to-action per section or page       |
| Secondary   | Solid neutral-100 background, neutral-900 text | Supporting actions alongside a primary button |
| Outline     | Transparent background, blue-600 border and text | Alternative secondary actions, form actions   |
| Ghost       | Transparent background, no border, blue-600 text | Tertiary actions, toolbar items, inline actions |
| Danger      | Solid red-600 background, white text       | Destructive actions: delete, remove, revoke   |
| Link        | No background/border, underlined text      | Navigation-style actions, inline text actions |
| Icon-only   | Any variant above, square aspect ratio     | Toolbars, compact UIs, icon-driven actions    |

### Variant Visual Reference

```
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│   PRIMARY    │  │  SECONDARY   │  │   OUTLINE    │
│  ██████████  │  │  ░░░░░░░░░░  │  │  ┌────────┐  │
│  ██ Save ██  │  │  ░░ Edit ░░  │  │  │ Cancel │  │
│  ██████████  │  │  ░░░░░░░░░░  │  │  └────────┘  │
└──────────────┘  └──────────────┘  └──────────────┘

┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│    GHOST     │  │    DANGER    │  │     LINK     │
│              │  │  ▓▓▓▓▓▓▓▓▓▓  │  │              │
│    More      │  │  ▓ Delete ▓  │  │  Learn more  │
│              │  │  ▓▓▓▓▓▓▓▓▓▓  │  │  __________  │
└──────────────┘  └──────────────┘  └──────────────┘
```

---

## States

### Primary Button States

| State    | Background       | Border           | Text           | Shadow             | Notes                          |
|----------|------------------|------------------|----------------|--------------------|--------------------------------|
| Default  | `blue-600`       | `transparent`    | `white`        | `none`             | Resting state                  |
| Hover    | `blue-700`       | `transparent`    | `white`        | `sm`               | Slight darkening + lift        |
| Active   | `blue-800`       | `transparent`    | `white`        | `none`             | Pressed down                   |
| Focus    | `blue-600`       | `transparent`    | `white`        | `ring-2 blue-300`  | 2px focus ring, 2px offset     |
| Disabled | `blue-300`       | `transparent`    | `white/60%`    | `none`             | Reduced opacity, no pointer    |
| Loading  | `blue-600`       | `transparent`    | `transparent`  | `none`             | Spinner replaces label         |

### Secondary Button States

| State    | Background       | Border           | Text            | Shadow             |
|----------|------------------|------------------|-----------------|--------------------|
| Default  | `neutral-100`    | `transparent`    | `neutral-900`   | `none`             |
| Hover    | `neutral-200`    | `transparent`    | `neutral-900`   | `sm`               |
| Active   | `neutral-300`    | `transparent`    | `neutral-900`   | `none`             |
| Focus    | `neutral-100`    | `transparent`    | `neutral-900`   | `ring-2 blue-300`  |
| Disabled | `neutral-50`     | `transparent`    | `neutral-400`   | `none`             |
| Loading  | `neutral-100`    | `transparent`    | `transparent`   | `none`             |

### Outline Button States

| State    | Background       | Border           | Text            | Shadow             |
|----------|------------------|------------------|-----------------|--------------------|
| Default  | `transparent`    | `blue-600`       | `blue-600`      | `none`             |
| Hover    | `blue-50`        | `blue-700`       | `blue-700`      | `none`             |
| Active   | `blue-100`       | `blue-800`       | `blue-800`      | `none`             |
| Focus    | `transparent`    | `blue-600`       | `blue-600`      | `ring-2 blue-300`  |
| Disabled | `transparent`    | `neutral-300`    | `neutral-400`   | `none`             |
| Loading  | `transparent`    | `blue-600`       | `transparent`   | `none`             |

### Ghost Button States

| State    | Background       | Border           | Text            | Shadow             |
|----------|------------------|------------------|-----------------|--------------------|
| Default  | `transparent`    | `transparent`    | `blue-600`      | `none`             |
| Hover    | `blue-50`        | `transparent`    | `blue-700`      | `none`             |
| Active   | `blue-100`       | `transparent`    | `blue-800`      | `none`             |
| Focus    | `transparent`    | `transparent`    | `blue-600`      | `ring-2 blue-300`  |
| Disabled | `transparent`    | `transparent`    | `neutral-400`   | `none`             |
| Loading  | `transparent`    | `transparent`    | `transparent`   | `none`             |

### Danger Button States

| State    | Background       | Border           | Text            | Shadow             |
|----------|------------------|------------------|-----------------|--------------------|
| Default  | `red-600`        | `transparent`    | `white`         | `none`             |
| Hover    | `red-700`        | `transparent`    | `white`         | `sm`               |
| Active   | `red-800`        | `transparent`    | `white`         | `none`             |
| Focus    | `red-600`        | `transparent`    | `white`         | `ring-2 red-300`   |
| Disabled | `red-300`        | `transparent`    | `white/60%`     | `none`             |
| Loading  | `red-600`        | `transparent`    | `transparent`   | `none`             |

### Link Button States

| State    | Background       | Border           | Text            | Text Decoration    |
|----------|------------------|------------------|-----------------|--------------------|
| Default  | `transparent`    | `transparent`    | `blue-600`      | `underline`        |
| Hover    | `transparent`    | `transparent`    | `blue-700`      | `underline`        |
| Active   | `transparent`    | `transparent`    | `blue-800`      | `underline`        |
| Focus    | `transparent`    | `transparent`    | `blue-600`      | `ring-2 blue-300`  |
| Disabled | `transparent`    | `transparent`    | `neutral-400`   | `underline`        |

---

## Sizing

| Size | Height | Padding (y / x) | Font Size | Line Height | Icon Size | Border Radius | Min Width |
|------|--------|------------------|-----------|-------------|-----------|---------------|-----------|
| sm   | 32px   | 6px / 12px       | 14px      | 20px        | 16px      | `sm` (4px)    | 64px      |
| md   | 40px   | 8px / 16px       | 16px      | 24px        | 20px      | `md` (6px)    | 80px      |
| lg   | 48px   | 12px / 24px      | 16px      | 24px        | 20px      | `md` (6px)    | 96px      |
| xl   | 56px   | 16px / 32px      | 18px      | 28px        | 24px      | `lg` (8px)    | 120px     |

### Icon-Only Button Sizing

| Size | Width x Height | Icon Size | Border Radius |
|------|---------------|-----------|---------------|
| sm   | 32px x 32px   | 16px      | `sm` (4px)    |
| md   | 40px x 40px   | 20px      | `md` (6px)    |
| lg   | 48px x 48px   | 20px      | `md` (6px)    |
| xl   | 56px x 56px   | 24px      | `lg` (8px)    |

### Icon + Label Gap

| Size | Gap Between Icon and Label |
|------|---------------------------|
| sm   | 4px                       |
| md   | 8px                       |
| lg   | 8px                       |
| xl   | 8px                       |

---

## Accessibility

- **Role**: Use the semantic `<button>` element. If using an anchor (`<a>`), add `role="button"` and handle `Enter` and `Space` keypress.
- **aria-disabled**: Use `aria-disabled="true"` instead of the native `disabled` attribute when you need the button to remain focusable (e.g., to show a tooltip explaining why it is disabled). When using `aria-disabled`, prevent the click handler in JavaScript.
- **aria-busy**: Set `aria-busy="true"` on the button during loading state. Pair with `aria-live="polite"` on a nearby status region to announce when loading completes.
- **aria-label**: Required for icon-only buttons. The label must describe the action, not the icon (e.g., `aria-label="Delete item"` not `aria-label="Trash icon"`).
- **aria-expanded**: Add when the button controls a collapsible section, dropdown, or popover.
- **aria-haspopup**: Add when the button opens a menu, dialog, or listbox.
- **Keyboard**:
  - `Tab` / `Shift+Tab` to move focus to and from the button.
  - `Enter` or `Space` to activate the button.
  - Disabled buttons using `disabled` attribute are removed from tab order. Buttons using `aria-disabled` remain in tab order.
- **Focus indicator**: 2px solid ring in `blue-300`, offset 2px from the button edge. Meets WCAG 2.1 SC 2.4.7 (Focus Visible) and SC 1.4.11 (Non-text Contrast, 3:1 ratio).
- **Color contrast**: All text/background combinations meet WCAG AA (4.5:1 for normal text). Primary (`white` on `blue-600`) achieves 4.68:1.
- **Touch target**: Minimum 44x44px touch target for sm size buttons (achieved via padding or hit area expansion).
- **Motion**: Loading spinner respects `prefers-reduced-motion: reduce` by switching to a static indicator.

---

## Design Tokens

```json
{
  "button": {
    "border-radius": {
      "sm": "{border.radius.sm}",
      "md": "{border.radius.md}",
      "lg": "{border.radius.md}",
      "xl": "{border.radius.lg}"
    },
    "font-family": "{typography.font.sans}",
    "font-weight": "{typography.weight.semibold}",
    "transition": "background 150ms ease, box-shadow 150ms ease, transform 100ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.300}",
    "primary": {
      "bg": "{color.blue.600}",
      "bg-hover": "{color.blue.700}",
      "bg-active": "{color.blue.800}",
      "bg-disabled": "{color.blue.300}",
      "text": "{color.white}",
      "text-disabled": "rgba(255, 255, 255, 0.6)"
    },
    "secondary": {
      "bg": "{color.neutral.100}",
      "bg-hover": "{color.neutral.200}",
      "bg-active": "{color.neutral.300}",
      "bg-disabled": "{color.neutral.50}",
      "text": "{color.neutral.900}",
      "text-disabled": "{color.neutral.400}"
    },
    "outline": {
      "bg": "transparent",
      "bg-hover": "{color.blue.50}",
      "bg-active": "{color.blue.100}",
      "border": "{color.blue.600}",
      "border-hover": "{color.blue.700}",
      "border-disabled": "{color.neutral.300}",
      "text": "{color.blue.600}",
      "text-disabled": "{color.neutral.400}"
    },
    "ghost": {
      "bg": "transparent",
      "bg-hover": "{color.blue.50}",
      "bg-active": "{color.blue.100}",
      "text": "{color.blue.600}",
      "text-disabled": "{color.neutral.400}"
    },
    "danger": {
      "bg": "{color.red.600}",
      "bg-hover": "{color.red.700}",
      "bg-active": "{color.red.800}",
      "bg-disabled": "{color.red.300}",
      "text": "{color.white}",
      "text-disabled": "rgba(255, 255, 255, 0.6)",
      "focus-ring-color": "{color.red.300}"
    },
    "link": {
      "text": "{color.blue.600}",
      "text-hover": "{color.blue.700}",
      "text-active": "{color.blue.800}",
      "text-disabled": "{color.neutral.400}"
    },
    "sizing": {
      "sm": {
        "height": "32px",
        "padding-x": "{space.3}",
        "padding-y": "{space.1.5}",
        "font-size": "{typography.body.sm.size}",
        "icon-size": "16px",
        "gap": "{space.1}"
      },
      "md": {
        "height": "40px",
        "padding-x": "{space.4}",
        "padding-y": "{space.2}",
        "font-size": "{typography.body.md.size}",
        "icon-size": "20px",
        "gap": "{space.2}"
      },
      "lg": {
        "height": "48px",
        "padding-x": "{space.6}",
        "padding-y": "{space.3}",
        "font-size": "{typography.body.md.size}",
        "icon-size": "20px",
        "gap": "{space.2}"
      },
      "xl": {
        "height": "56px",
        "padding-x": "{space.8}",
        "padding-y": "{space.4}",
        "font-size": "{typography.body.lg.size}",
        "icon-size": "24px",
        "gap": "{space.2}"
      }
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use one primary button per section or visible viewport to establish a clear hierarchy.
- Write concise, action-oriented labels: "Save changes", "Delete account", "Send invite".
- Use the danger variant for irreversible or destructive actions and pair with a confirmation dialog.
- Place the primary action on the right in button groups (following LTR reading order).
- Use loading state when the action triggers an async operation lasting more than 300ms.
- Provide `aria-label` on every icon-only button.

**Don't:**
- Don't use multiple primary buttons in the same section — promote one and demote others to secondary or outline.
- Don't use vague labels like "Click here", "Submit", or "OK" without context.
- Don't disable buttons without explaining why — use a tooltip or helper text.
- Don't use the link variant for actions that do not navigate; use ghost instead.
- Don't override token colors with hardcoded hex values.
- Don't wrap critical actions in ghost buttons — they lack sufficient visual weight.
- Don't place destructive actions in prominent positions without safeguards.

---

## Code Example

### HTML

```html
<!-- Primary button -->
<button class="ff-btn ff-btn--primary ff-btn--md" type="button">
  Save Changes
</button>

<!-- Primary button with leading icon -->
<button class="ff-btn ff-btn--primary ff-btn--md" type="button">
  <svg class="ff-btn__icon ff-btn__icon--leading" aria-hidden="true"><!-- icon --></svg>
  <span class="ff-btn__label">Save Changes</span>
</button>

<!-- Secondary button -->
<button class="ff-btn ff-btn--secondary ff-btn--md" type="button">
  Cancel
</button>

<!-- Outline button -->
<button class="ff-btn ff-btn--outline ff-btn--lg" type="button">
  Export Report
</button>

<!-- Ghost button -->
<button class="ff-btn ff-btn--ghost ff-btn--sm" type="button">
  View All
</button>

<!-- Danger button -->
<button class="ff-btn ff-btn--danger ff-btn--md" type="button">
  Delete Account
</button>

<!-- Link button -->
<button class="ff-btn ff-btn--link ff-btn--md" type="button">
  Learn more
</button>

<!-- Icon-only button -->
<button class="ff-btn ff-btn--primary ff-btn--md ff-btn--icon-only" type="button" aria-label="Search">
  <svg class="ff-btn__icon" aria-hidden="true"><!-- search icon --></svg>
</button>

<!-- Disabled button -->
<button class="ff-btn ff-btn--primary ff-btn--md" type="button" disabled>
  Save Changes
</button>

<!-- Disabled but focusable (for tooltip explanation) -->
<button class="ff-btn ff-btn--primary ff-btn--md ff-btn--disabled" type="button" aria-disabled="true">
  Save Changes
</button>

<!-- Loading button -->
<button class="ff-btn ff-btn--primary ff-btn--md ff-btn--loading" type="button" aria-busy="true">
  <span class="ff-btn__spinner" aria-hidden="true"></span>
  <span class="ff-btn__label ff-btn__label--hidden">Save Changes</span>
</button>

<!-- Button group -->
<div class="ff-btn-group" role="group" aria-label="Form actions">
  <button class="ff-btn ff-btn--secondary ff-btn--md" type="button">Cancel</button>
  <button class="ff-btn ff-btn--primary ff-btn--md" type="submit">Save Changes</button>
</div>
```

### JSX

```jsx
import { Button, ButtonGroup } from '@flavio-fusuma/ui';
import { SaveIcon, TrashIcon, SearchIcon } from '@flavio-fusuma/icons';

// Primary button
<Button variant="primary" size="md">
  Save Changes
</Button>

// Primary with leading icon
<Button variant="primary" size="md" leadingIcon={<SaveIcon />}>
  Save Changes
</Button>

// Secondary
<Button variant="secondary" size="md">
  Cancel
</Button>

// Outline
<Button variant="outline" size="lg">
  Export Report
</Button>

// Ghost
<Button variant="ghost" size="sm">
  View All
</Button>

// Danger
<Button variant="danger" size="md">
  Delete Account
</Button>

// Link
<Button variant="link" size="md">
  Learn more
</Button>

// Icon-only
<Button variant="primary" size="md" iconOnly aria-label="Search">
  <SearchIcon />
</Button>

// Disabled
<Button variant="primary" size="md" disabled>
  Save Changes
</Button>

// Loading
<Button variant="primary" size="md" loading>
  Save Changes
</Button>

// Button group
<ButtonGroup>
  <Button variant="secondary" size="md">Cancel</Button>
  <Button variant="primary" size="md" type="submit">Save Changes</Button>
</ButtonGroup>

// Full-width button
<Button variant="primary" size="lg" fullWidth>
  Continue to Checkout
</Button>
```

---

## Related Components

- **[Inputs](./inputs.md)** — Often placed alongside buttons in form layouts.
- **[Modals](./modals.md)** — Modal footers typically contain button groups for confirm/cancel actions.
- **[Cards](./cards.md)** — Card action slots frequently contain buttons.
- **[Tooltips](./tooltips.md)** — Use tooltips on icon-only buttons to clarify meaning, and on disabled buttons to explain why.
- **[Badges](./badges.md)** — Badges may appear inside or adjacent to buttons to show counts or status.
