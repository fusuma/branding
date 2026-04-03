# Text Areas

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Text areas allow users to enter and edit multi-line text. They are used for longer-form content such as comments, descriptions, feedback, and messages. Text areas support auto-resize behavior, character counting, and configurable minimum and maximum row heights to adapt to content length while maintaining consistent form layouts.

---

## Anatomy

```
┌──────────────────────────────────────────────────────┐
│  [Label Text]                           [Optional *] │
│  ┌──────────────────────────────────────────────────┐│
│  │                                                  ││
│  │  [Input text / Placeholder]                      ││
│  │                                                  ││
│  │                                                  ││
│  │                                         ┌──────┐ ││
│  │                                         │Resize│ ││
│  └──────────────────────────────────────────┴──────┘ │
│  [Helper text / Error message]        [12 / 500]     │
└──────────────────────────────────────────────────────┘
```

| Part              | Required | Description                                              |
|-------------------|----------|----------------------------------------------------------|
| Container         | Yes      | Outer wrapper for the entire component                    |
| Label             | Yes      | Text label above the textarea (visually or via aria-label)|
| Textarea field    | Yes      | The multi-line text entry area                            |
| Placeholder       | No       | Hint text shown when the textarea is empty                |
| Helper text       | No       | Guidance text below the textarea                          |
| Error message     | No       | Validation error replacing helper text                    |
| Character count   | No       | Current / max character count, bottom-right               |
| Resize handle     | No       | Native or custom drag handle for manual resizing          |
| Required indicator| No       | Asterisk or "(required)" next to label                    |

---

## Variants

| Variant   | Description                                      | Use Case                                        |
|-----------|--------------------------------------------------|-------------------------------------------------|
| Default   | White background, neutral border, manual resize  | Standard multi-line forms                        |
| Filled    | Neutral-100 background, no border at rest        | Dense UIs, settings panels                       |
| Auto-resize | Grows/shrinks height based on content          | Chat inputs, inline editors, compact forms       |
| Error     | Red border, error message visible                | Validation failure                               |
| Disabled  | Reduced opacity, non-interactive                 | Field not editable in current context            |

### Variant Visual Reference

```
Default (manual resize):          Auto-resize (content-driven):
┌────────────────────────┐        ┌────────────────────────┐
│ Description            │        │ Comment                │
│ ┌────────────────────┐ │        │ ┌────────────────────┐ │
│ │ Enter a detailed   │ │        │ │ This textarea      │ │
│ │ description of the │ │        │ │ grows as the user  │ │
│ │ issue...           │ │        │ │ types more content │ │
│ │                    │ │        │ │ into it and it     │ │
│ │              ╱╱╱╱╱ │ │        │ │ shrinks when text  │ │
│ └────────────────────┘ │        │ │ is removed.        │ │
│ Provide as much detail │        │ └────────────────────┘ │
│ as possible.           │        │                  8/500  │
└────────────────────────┘        └────────────────────────┘
```

---

## Auto-Resize Behavior

The auto-resize variant dynamically adjusts height based on content. This avoids scrollbars within the textarea while respecting minimum and maximum constraints.

| Property         | Default Value | Description                                          |
|------------------|---------------|------------------------------------------------------|
| `minRows`        | 3             | Minimum number of visible text rows                  |
| `maxRows`        | 10            | Maximum rows before scrolling activates              |
| Resize direction | Vertical only | Horizontal resize is always disabled                 |
| Growth trigger   | Line break or wrap | Textarea grows when text wraps to a new line    |
| Shrink trigger   | Content removal | Textarea shrinks when lines are deleted             |
| Animation        | none          | Height change is instant (no transition)             |

### Row Height Calculation

```
Row height = font-size * line-height
Min height = (minRows * row-height) + padding-top + padding-bottom + border
Max height = (maxRows * row-height) + padding-top + padding-bottom + border

Example (md size, 3 min rows):
  Row height = 16px * 1.5 = 24px
  Min height = (3 * 24) + 8 + 8 + 2 = 90px
  Max height = (10 * 24) + 8 + 8 + 2 = 258px
```

---

## Character Count

| Property                | Description                                             |
|-------------------------|---------------------------------------------------------|
| Display format          | `{current} / {max}` (e.g., "128 / 500")                |
| Position                | Bottom-right corner, aligned with helper text row       |
| Warning threshold       | Text turns `amber-500` at 90% of max length             |
| Limit reached           | Text turns `red-600` at 100% of max length              |
| Over limit behavior     | Input is not blocked; the count turns red and form validation prevents submit |
| Visibility              | Only visible when `maxLength` prop is set               |

---

## States

### Default Variant States

| State    | Background    | Border        | Text           | Label Color    | Shadow            | Notes                           |
|----------|---------------|---------------|----------------|----------------|-------------------|---------------------------------|
| Default  | `white`       | `neutral-300` | `neutral-900`  | `neutral-700`  | `none`            | Resting state                   |
| Hover    | `white`       | `neutral-400` | `neutral-900`  | `neutral-700`  | `none`            | Border darkens                  |
| Focus    | `white`       | `blue-600`    | `neutral-900`  | `blue-600`     | `ring-2 blue-100` | Label color changes to blue     |
| Filled   | `white`       | `neutral-300` | `neutral-900`  | `neutral-700`  | `none`            | Has content, not focused        |
| Disabled | `neutral-50`  | `neutral-200` | `neutral-400`  | `neutral-400`  | `none`            | Non-interactive                 |
| Read-only| `neutral-50`  | `neutral-200` | `neutral-900`  | `neutral-700`  | `none`            | Selectable, not editable        |

### Error Variant States

| State    | Background    | Border        | Text           | Label Color    | Helper Color   | Shadow            |
|----------|---------------|---------------|----------------|----------------|----------------|-------------------|
| Default  | `white`       | `red-500`     | `neutral-900`  | `red-600`      | `red-600`      | `none`            |
| Hover    | `white`       | `red-600`     | `neutral-900`  | `red-600`      | `red-600`      | `none`            |
| Focus    | `white`       | `red-600`     | `neutral-900`  | `red-600`      | `red-600`      | `ring-2 red-100`  |

---

## Sizing

| Size | Min Height (3 rows) | Padding (y / x) | Font Size | Line Height | Label Size | Border Radius |
|------|---------------------|------------------|-----------|-------------|------------|---------------|
| sm   | 72px                | 6px / 10px       | 14px      | 20px        | 12px       | `sm` (4px)    |
| md   | 90px                | 8px / 12px       | 16px      | 24px        | 14px       | `md` (6px)    |
| lg   | 108px               | 12px / 16px      | 16px      | 24px        | 14px       | `md` (6px)    |

### Spacing

| Property                   | Value  | Token       |
|----------------------------|--------|-------------|
| Label to textarea gap      | 6px    | --          |
| Textarea to helper gap     | 4px    | `{space.1}` |
| Border width               | 1px    | --          |
| Focus border width         | 2px    | --          |
| Resize handle size         | 16px   | --          |

---

## Accessibility

- **Label**: Every textarea must have a visible `<label>` associated via `for`/`id`. Use `aria-label` or `aria-labelledby` only when a visible label is not possible.
- **Required**: Use `aria-required="true"` and a visual indicator for required textareas.
- **Error state**: Apply `aria-invalid="true"` and connect error messages via `aria-describedby`.
- **Character count**: Announce count updates at key thresholds (90%, 100%) using `aria-live="polite"` on the counter element. Do not announce on every keystroke.
- **Keyboard**:
  - `Tab` / `Shift+Tab` to navigate to and from the textarea.
  - `Enter` creates a new line within the textarea (does not submit the form).
  - Standard text editing keys are supported natively.
- **Resize**: The resize handle must be keyboard-accessible. Auto-resize removes the need for manual resizing.
- **Focus indicator**: 2px solid ring in `blue-100` with `blue-600` border. Meets WCAG 2.1 SC 2.4.7 and SC 1.4.11.
- **Color contrast**: All text meets WCAG AA (4.5:1). Character count warning and error colors are paired with positional context so meaning is not conveyed by color alone.
- **Motion**: Auto-resize height changes respect `prefers-reduced-motion` by removing transitions (height changes are already instant by default).

---

## Design Tokens

```json
{
  "textarea": {
    "border-radius": {
      "sm": "{border.radius.sm}",
      "md": "{border.radius.md}",
      "lg": "{border.radius.md}"
    },
    "font-family": "{typography.font.sans}",
    "transition": "border-color 150ms ease, box-shadow 150ms ease",
    "resize": "vertical",
    "default": {
      "bg": "{color.white}",
      "bg-disabled": "{color.neutral.50}",
      "border": "{color.neutral.300}",
      "border-hover": "{color.neutral.400}",
      "border-focus": "{color.blue.600}",
      "border-disabled": "{color.neutral.200}",
      "text": "{color.neutral.900}",
      "text-disabled": "{color.neutral.400}",
      "text-placeholder": "{color.neutral.400}",
      "focus-ring-color": "{color.blue.100}"
    },
    "error": {
      "border": "{color.red.500}",
      "border-focus": "{color.red.600}",
      "label-color": "{color.red.600}",
      "helper-color": "{color.red.600}",
      "focus-ring-color": "{color.red.100}"
    },
    "character-count": {
      "color": "{color.neutral.500}",
      "color-warning": "{color.amber.500}",
      "color-error": "{color.red.600}",
      "font-size": "12px"
    },
    "label": {
      "font-weight": "500",
      "color": "{color.neutral.700}",
      "color-focus": "{color.blue.600}",
      "color-disabled": "{color.neutral.400}"
    },
    "sizing": {
      "sm": {
        "min-rows": 3,
        "padding-x": "{space.2.5}",
        "padding-y": "{space.1.5}",
        "font-size": "{typography.body.sm.size}",
        "line-height": "20px"
      },
      "md": {
        "min-rows": 3,
        "padding-x": "{space.3}",
        "padding-y": "{space.2}",
        "font-size": "{typography.body.md.size}",
        "line-height": "24px"
      },
      "lg": {
        "min-rows": 3,
        "padding-x": "{space.4}",
        "padding-y": "{space.3}",
        "font-size": "{typography.body.md.size}",
        "line-height": "24px"
      }
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use textareas for any input expected to exceed one line -- descriptions, comments, messages, bio text.
- Set a sensible `maxLength` and display the character count when there is a meaningful limit.
- Use auto-resize for conversational UIs (chat inputs, comment boxes) to reduce visual clutter.
- Set appropriate `minRows` so the textarea communicates "multi-line" at a glance (minimum 3 rows recommended).
- Provide clear placeholder text that shows the expected format or tone.
- Place the label above the textarea, left-aligned, for optimal readability.

**Don't:**
- Don't use textareas for short, single-line data (names, emails) -- use Input instead.
- Don't allow horizontal resize -- it breaks form layouts and column widths.
- Don't disable the textarea without explaining why the field is unavailable.
- Don't set `maxRows` too low on auto-resize textareas -- this forces early scrolling and frustrates users.
- Don't use character counts without a `maxLength` value -- a counter with no limit is meaningless.
- Don't override token colors with hardcoded hex values.

---

## Code Example

### HTML

```html
<!-- Default textarea with label, helper, and character count -->
<div class="ff-textarea-field ff-textarea-field--md">
  <label class="ff-textarea-field__label" for="description">
    Description
  </label>
  <textarea
    class="ff-textarea"
    id="description"
    name="description"
    rows="4"
    maxlength="500"
    placeholder="Describe the issue in detail..."
    aria-describedby="desc-helper desc-count"
  ></textarea>
  <div class="ff-textarea-field__footer">
    <p class="ff-textarea-field__helper" id="desc-helper">
      Include steps to reproduce the problem.
    </p>
    <span class="ff-textarea-field__count" id="desc-count" aria-live="polite">
      0 / 500
    </span>
  </div>
</div>

<!-- Auto-resize textarea -->
<div class="ff-textarea-field ff-textarea-field--md ff-textarea-field--auto-resize">
  <label class="ff-textarea-field__label" for="comment">Comment</label>
  <textarea
    class="ff-textarea ff-textarea--auto-resize"
    id="comment"
    name="comment"
    rows="3"
    data-min-rows="3"
    data-max-rows="10"
    placeholder="Write a comment..."
  ></textarea>
</div>

<!-- Error state -->
<div class="ff-textarea-field ff-textarea-field--md ff-textarea-field--error">
  <label class="ff-textarea-field__label" for="feedback">
    Feedback <span aria-hidden="true">*</span>
  </label>
  <textarea
    class="ff-textarea"
    id="feedback"
    name="feedback"
    rows="4"
    aria-required="true"
    aria-invalid="true"
    aria-describedby="feedback-error"
  ></textarea>
  <div class="ff-textarea-field__footer">
    <p class="ff-textarea-field__error" id="feedback-error" role="alert">
      Feedback is required. Please share your thoughts.
    </p>
  </div>
</div>

<!-- Disabled textarea -->
<div class="ff-textarea-field ff-textarea-field--md ff-textarea-field--disabled">
  <label class="ff-textarea-field__label" for="notes">Notes</label>
  <textarea
    class="ff-textarea"
    id="notes"
    name="notes"
    rows="3"
    disabled
  >This field is managed by an administrator.</textarea>
</div>
```

### JSX

```jsx
import { TextArea } from '@flavio-fusuma/ui';

// Default textarea with character count
<TextArea
  label="Description"
  placeholder="Describe the issue in detail..."
  helperText="Include steps to reproduce the problem."
  size="md"
  rows={4}
  maxLength={500}
  showCharacterCount
/>

// Auto-resize textarea
<TextArea
  label="Comment"
  placeholder="Write a comment..."
  size="md"
  autoResize
  minRows={3}
  maxRows={10}
/>

// Error state
<TextArea
  label="Feedback"
  size="md"
  rows={4}
  required
  error="Feedback is required. Please share your thoughts."
/>

// Disabled
<TextArea
  label="Notes"
  size="md"
  rows={3}
  disabled
  value="This field is managed by an administrator."
/>

// Filled variant
<TextArea
  label="Bio"
  variant="filled"
  size="md"
  placeholder="Tell us about yourself..."
  maxLength={300}
  showCharacterCount
/>
```

---

## Related Components

- **[Inputs](./inputs.md)** -- For single-line text entry; use Input when content is short (names, emails, numbers).
- **[Select](./select.md)** -- For choosing from predefined options rather than free-text entry.
- **[Buttons](./buttons.md)** -- Typically paired with textareas for form submission.
- **[Cards](./cards.md)** -- Textareas often appear inside card body sections for inline editing.
- **[Modals](./modals.md)** -- Textareas in modal forms should be mindful of the modal's max-height and scroll behavior.
