# Tooltips

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Tooltips are small, floating labels that appear on hover or focus to provide supplementary information about an element. They help explain icons, abbreviations, truncated text, or controls that benefit from additional context without cluttering the interface. Tooltips are informational only and must not contain interactive content. For interactive overlays, use the Popover component instead.

---

## Anatomy

```
                    ┌─────────────────────────┐
                    │  [Tooltip Content]       │
                    │  Explanatory text that   │
                    │  describes the element.  │
                    └────────────┬────────────┘
                                 │ (arrow)
                                 ▼
                          ┌────────────┐
                          │  [Trigger]  │
                          │   Element   │
                          └────────────┘

Placement variations:

       ┌───────┐
       │Tooltip│
       └───┬───┘     Top (default)
           ▼
       [Trigger]

       [Trigger]
           ▲
       ┌───┴───┐     Bottom
       │Tooltip│
       └───────┘

[Trigger] ► ┌───────┐     Right
             │Tooltip│
             └───────┘

┌───────┐ ◄ [Trigger]     Left
│Tooltip│
└───────┘
```

| Part         | Required | Description                                           |
|--------------|----------|-------------------------------------------------------|
| Trigger      | Yes      | The element that the tooltip describes (button, icon, text) |
| Container    | Yes      | The floating tooltip box with background and padding    |
| Content      | Yes      | Text string or short content inside the tooltip         |
| Arrow        | No       | Triangular pointer connecting the tooltip to the trigger|

---

## Variants

| Variant    | Description                                     | Use Case                                         |
|------------|-------------------------------------------------|--------------------------------------------------|
| Default    | Dark background, light text                      | Standard informational tooltips                   |
| Light      | Light background, dark text, subtle border       | Interfaces with dark backgrounds or themes        |

### Variant Visual Reference

```
Default (dark):                    Light:
┌───────────────────┐              ┌───────────────────┐
│ ████████████████  │              │                   │
│ ██ Tooltip text █ │              │  Tooltip text     │
│ ████████████████  │              │                   │
└─────────┬─────────┘              └─────────┬─────────┘
          ▼                                  ▼
    [Trigger]                          [Trigger]
```

---

## Placement

| Placement    | Description                                  | Fallback                           |
|--------------|----------------------------------------------|------------------------------------|
| top          | Centered above the trigger (default)          | bottom if not enough space above   |
| top-start    | Above, aligned to the start (left in LTR)    | bottom-start                       |
| top-end      | Above, aligned to the end (right in LTR)     | bottom-end                         |
| bottom       | Centered below the trigger                    | top                                |
| bottom-start | Below, aligned to the start                   | top-start                          |
| bottom-end   | Below, aligned to the end                     | top-end                            |
| right        | Centered to the right of the trigger          | left                               |
| right-start  | Right, aligned to the top                     | left-start                         |
| right-end    | Right, aligned to the bottom                  | left-end                           |
| left         | Centered to the left of the trigger           | right                              |
| left-start   | Left, aligned to the top                      | right-start                        |
| left-end     | Left, aligned to the bottom                   | right-end                          |

### Auto-Flip Behavior

Tooltips automatically flip to the opposite side when there is not enough space in the preferred direction. This is handled by a positioning engine (e.g., Floating UI / Popper) and requires no manual configuration.

---

## Trigger Types

| Trigger  | Show Event          | Hide Event            | Use Case                                |
|----------|---------------------|-----------------------|-----------------------------------------|
| Hover    | `mouseenter`        | `mouseleave`          | Desktop users, most common trigger       |
| Focus    | `focus`             | `blur`                | Keyboard users, accessible by default    |
| Click    | `click` (toggle)    | `click` outside / `Escape` | Touch devices, persistent tooltips  |

By default, tooltips respond to both hover and focus events simultaneously. The click trigger is an alternative mode for touch-first interfaces.

---

## Delay and Timing

| Property        | Default Value | Description                                            |
|-----------------|---------------|--------------------------------------------------------|
| Show delay      | 300ms         | Delay before tooltip appears after trigger activation   |
| Hide delay      | 150ms         | Delay before tooltip disappears after trigger deactivation |
| Enter animation | 100ms         | Fade-in duration                                        |
| Exit animation  | 75ms          | Fade-out duration                                       |
| Group delay     | 0ms           | When moving between tooltips in a group, show instantly  |

### Timing Rationale

- The 300ms show delay prevents tooltips from appearing during casual mouse movement.
- The 150ms hide delay allows users to move their cursor from the trigger to the tooltip (useful for reading longer text).
- Group delay of 0ms means once a user has seen one tooltip, subsequent tooltips in the same group appear instantly.

---

## States

| State       | Opacity | Transform           | Duration | Notes                              |
|-------------|---------|---------------------|----------|------------------------------------|
| Hidden      | 0       | scale(0.95)         | --       | Not visible, not in DOM or hidden  |
| Entering    | 0 -> 1  | scale(0.95) -> (1)  | 100ms    | Fade in with slight scale          |
| Visible     | 1       | scale(1)            | --       | Fully visible                      |
| Exiting     | 1 -> 0  | scale(1) -> (0.95)  | 75ms     | Fade out                           |

---

## Sizing

| Property          | Value           | Token                  |
|-------------------|-----------------|------------------------|
| Max width         | 240px           | --                     |
| Min width         | none            | --                     |
| Padding           | 6px 10px        | `{space.1.5} {space.2.5}` |
| Border radius     | 6px             | `{border.radius.md}`   |
| Font size         | 14px            | `{typography.body.sm.size}` |
| Line height       | 20px            | --                     |
| Font weight       | 400             | --                     |
| Arrow size        | 6px             | --                     |
| Offset from trigger| 8px            | `{space.2}`            |
| Shadow            | `md`            | `{shadow.md}`          |

---

## Accessibility

- **ARIA**: The trigger element must have `aria-describedby` pointing to the tooltip's ID. This ensures the tooltip text is announced by screen readers when the trigger receives focus.
- **Role**: The tooltip container must have `role="tooltip"` and a unique `id`.
- **Trigger requirements**: The trigger element must be focusable (natively or via `tabindex="0"`). Tooltips on non-interactive elements (e.g., a `<span>`) require `tabindex="0"` on the trigger.
- **No interactive content**: Tooltips must not contain links, buttons, or other interactive elements. If interactive content is needed, use a Popover instead.
- **Keyboard**:
  - Tooltip appears when the trigger receives focus via `Tab`.
  - Tooltip hides when focus leaves the trigger.
  - `Escape` hides the tooltip while keeping focus on the trigger.
- **Screen reader**: The tooltip text is announced as a description of the trigger element (via `aria-describedby`). It is not announced on hover alone -- only on focus or when the trigger element is navigated to.
- **Touch devices**: On touch devices, tooltips should appear on long-press or tap (click trigger mode). They should not rely on hover, which is unavailable on mobile.
- **Color contrast**: Default (dark) variant: white text on `neutral-900` background exceeds 15:1 contrast. Light variant: `neutral-900` text on white meets 15:1.
- **Motion**: Animations respect `prefers-reduced-motion: reduce` by switching to instant show/hide.

---

## Design Tokens

```json
{
  "tooltip": {
    "font-family": "{typography.font.sans}",
    "font-size": "{typography.body.sm.size}",
    "font-weight": "400",
    "line-height": "20px",
    "max-width": "240px",
    "padding": "{space.1.5} {space.2.5}",
    "border-radius": "{border.radius.md}",
    "offset": "{space.2}",
    "arrow-size": "6px",
    "shadow": "{shadow.md}",
    "z-index": "60",
    "default": {
      "bg": "{color.neutral.900}",
      "text": "{color.white}",
      "arrow-color": "{color.neutral.900}"
    },
    "light": {
      "bg": "{color.white}",
      "text": "{color.neutral.900}",
      "border": "1px solid {color.neutral.200}",
      "arrow-color": "{color.white}",
      "arrow-border-color": "{color.neutral.200}"
    },
    "animation": {
      "show-delay": "300ms",
      "hide-delay": "150ms",
      "enter-duration": "100ms",
      "exit-duration": "75ms",
      "enter-easing": "ease-out",
      "exit-easing": "ease-in",
      "scale-from": "0.95",
      "scale-to": "1",
      "group-delay": "0ms"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use tooltips to describe icon-only buttons, abbreviations, or truncated text.
- Keep tooltip text concise -- one or two short sentences maximum.
- Use the default (dark) variant in light interfaces and the light variant on dark backgrounds.
- Always pair icon-only buttons with tooltips to clarify meaning.
- Ensure the trigger is keyboard-focusable so the tooltip is accessible to all users.
- Allow the arrow to point to the trigger for clear visual connection.
- Set appropriate max-width to prevent tooltips from becoming too wide.

**Don't:**
- Don't put interactive elements (links, buttons) inside tooltips -- use a Popover instead.
- Don't use tooltips for essential information that users must see -- it should be supplementary.
- Don't use tooltips on disabled elements unless the disabled element is still focusable (`aria-disabled`).
- Don't use tooltips to display error messages -- use inline validation messages.
- Don't override the show delay to 0ms -- the delay prevents tooltip flicker during casual mouse movement.
- Don't create tooltips with more than 2-3 lines of text -- use a Popover for longer content.
- Don't override token colors with hardcoded hex values.
- Don't use tooltips on touch devices without a fallback trigger (tap or long-press).

---

## Code Example

### HTML

```html
<!-- Basic tooltip on an icon button -->
<div class="ff-tooltip-wrapper">
  <button
    class="ff-btn ff-btn--ghost ff-btn--md ff-btn--icon-only"
    aria-label="Delete item"
    aria-describedby="tooltip-delete"
  >
    <svg aria-hidden="true"><!-- trash icon --></svg>
  </button>
  <div class="ff-tooltip ff-tooltip--top" id="tooltip-delete" role="tooltip">
    Delete item
    <span class="ff-tooltip__arrow"></span>
  </div>
</div>

<!-- Tooltip with light variant -->
<div class="ff-tooltip-wrapper">
  <button
    class="ff-btn ff-btn--primary ff-btn--sm"
    aria-describedby="tooltip-info"
  >
    Publish
  </button>
  <div class="ff-tooltip ff-tooltip--bottom ff-tooltip--light" id="tooltip-info" role="tooltip">
    This will make the page visible to all users.
    <span class="ff-tooltip__arrow"></span>
  </div>
</div>

<!-- Tooltip on a non-interactive element (requires tabindex) -->
<div class="ff-tooltip-wrapper">
  <span
    class="ff-text--truncated"
    tabindex="0"
    aria-describedby="tooltip-full-text"
  >
    This is a very long text that gets tru...
  </span>
  <div class="ff-tooltip ff-tooltip--top" id="tooltip-full-text" role="tooltip">
    This is a very long text that gets truncated in the interface.
    <span class="ff-tooltip__arrow"></span>
  </div>
</div>

<!-- Tooltip on disabled button (using aria-disabled) -->
<div class="ff-tooltip-wrapper">
  <button
    class="ff-btn ff-btn--primary ff-btn--md ff-btn--disabled"
    aria-disabled="true"
    aria-describedby="tooltip-disabled"
  >
    Submit
  </button>
  <div class="ff-tooltip ff-tooltip--top" id="tooltip-disabled" role="tooltip">
    Complete all required fields before submitting.
    <span class="ff-tooltip__arrow"></span>
  </div>
</div>

<!-- Tooltip placements -->
<div class="ff-tooltip-wrapper">
  <button aria-describedby="tooltip-right">Right tooltip</button>
  <div class="ff-tooltip ff-tooltip--right" id="tooltip-right" role="tooltip">
    Positioned to the right
    <span class="ff-tooltip__arrow"></span>
  </div>
</div>

<div class="ff-tooltip-wrapper">
  <button aria-describedby="tooltip-left">Left tooltip</button>
  <div class="ff-tooltip ff-tooltip--left" id="tooltip-left" role="tooltip">
    Positioned to the left
    <span class="ff-tooltip__arrow"></span>
  </div>
</div>
```

### JSX

```jsx
import { Tooltip } from '@flavio-fusuma/ui';
import { Button } from '@flavio-fusuma/ui';
import { TrashIcon, InfoIcon } from '@flavio-fusuma/icons';

// Tooltip on an icon-only button
<Tooltip content="Delete item" placement="top">
  <Button variant="ghost" size="md" iconOnly aria-label="Delete item">
    <TrashIcon />
  </Button>
</Tooltip>

// Tooltip with custom placement
<Tooltip content="This will make the page visible to all users." placement="bottom">
  <Button variant="primary" size="sm">Publish</Button>
</Tooltip>

// Light variant
<Tooltip content="Click to copy the link" placement="right" variant="light">
  <Button variant="ghost" size="sm" iconOnly aria-label="Copy link">
    <CopyIcon />
  </Button>
</Tooltip>

// Tooltip on disabled button
<Tooltip content="Complete all required fields before submitting." placement="top">
  <Button variant="primary" size="md" aria-disabled="true">
    Submit
  </Button>
</Tooltip>

// Tooltip with custom delay
<Tooltip
  content="Keyboard shortcut: Ctrl+S"
  placement="bottom"
  showDelay={500}
  hideDelay={100}
>
  <Button variant="primary" size="md">Save</Button>
</Tooltip>

// Tooltip without arrow
<Tooltip content="Settings" placement="bottom" arrow={false}>
  <Button variant="ghost" size="md" iconOnly aria-label="Settings">
    <GearIcon />
  </Button>
</Tooltip>

// Click-triggered tooltip (touch-friendly)
<Tooltip content="Copied to clipboard!" trigger="click" placement="top">
  <Button variant="outline" size="sm">Copy Code</Button>
</Tooltip>

// Tooltip on non-interactive text
<Tooltip content="Created on March 15, 2026 at 2:30 PM UTC" placement="top">
  <span tabIndex={0} className="ff-text--muted">3 weeks ago</span>
</Tooltip>
```

---

## Related Components

- **[Buttons](./buttons.md)** -- Icon-only buttons should always have tooltips to clarify their meaning.
- **[Badges](./badges.md)** -- Tooltips can explain badge labels or status indicators.
- **[Inputs](./inputs.md)** -- Use helper text for input guidance; reserve tooltips for supplementary icon explanations.
- **[Modals](./modals.md)** -- For content requiring interaction, use a modal instead of a tooltip.
- **[Cards](./cards.md)** -- Tooltips can explain truncated card metadata or action icons.
