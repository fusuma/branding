# Inputs

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Text inputs are the primary form controls for collecting short-form text data from users. They support labels, placeholder text, helper messages, validation states, and prefix/suffix slots for icons or inline actions. Use inputs for single-line text entry such as names, emails, search queries, and numeric values.

---

## Anatomy

```
┌──────────────────────────────────────────────────────┐
│  [Label Text]                           [Optional *] │
│  ┌──────────────────────────────────────────────────┐│
│  │ ┌──────┐                          ┌──────────┐  ││
│  │ │Prefix│  [Input Value / Placeholder] │Suffix│  ││
│  │ └──────┘                          └──────────┘  ││
│  └──────────────────────────────────────────────────┘│
│  [Helper text / Error message]        [Character ct] │
└──────────────────────────────────────────────────────┘

Prefix/Suffix detail:
┌────────────────────────────────────────┐
│ ┌──┐                           ┌────┐ │
│ │ $ │  Amount                   │.00 │ │
│ └──┘                           └────┘ │
└────────────────────────────────────────┘

│ ┌──┐                           ┌────┐ │
│ │🔍│  Search products...       │ ✕  │ │
│ └──┘                           └────┘ │
```

| Part              | Required | Description                                           |
|-------------------|----------|-------------------------------------------------------|
| Container         | Yes      | Outer wrapper that holds all input parts               |
| Label             | Yes      | Text label above the input field (visually or via aria-label) |
| Input field       | Yes      | The interactive text entry area                        |
| Placeholder       | No       | Hint text shown when input is empty                    |
| Prefix slot       | No       | Leading element: icon, text, or symbol                 |
| Suffix slot       | No       | Trailing element: icon, clear button, or text          |
| Helper text       | No       | Guidance text below the input                          |
| Error message     | No       | Validation error shown below the input (replaces helper text) |
| Required indicator| No       | Asterisk or "(required)" text next to label            |
| Character count   | No       | Current/max character count in bottom-right corner     |

---

## Variants

| Variant   | Description                                       | Use Case                                      |
|-----------|---------------------------------------------------|-----------------------------------------------|
| Default   | White background, neutral border                   | Standard text input for forms                  |
| Filled    | Neutral-100 background, no visible border at rest  | Dense forms, settings panels, search fields    |
| Error     | Red border and error message visible               | Validation failure state                       |
| Success   | Green border, optional check icon in suffix        | Validated field with positive confirmation      |
| Disabled  | Reduced opacity, non-interactive                   | Field not available in current context          |

### Variant Visual Reference

```
Default:                          Filled:
┌────────────────────────┐        ┌────────────────────────┐
│ Email address          │        │░░░░░░░░░░░░░░░░░░░░░░░░│
│ ┌────────────────────┐ │        │░░ Email address      ░░│
│ │ user@example.com   │ │        │░░░░░░░░░░░░░░░░░░░░░░░░│
│ └────────────────────┘ │        └────────────────────────┘
│ We'll never share it   │
└────────────────────────┘

Error:                            Success:
┌────────────────────────┐        ┌────────────────────────┐
│ Email address          │        │ Email address          │
│ ┌────────────────────┐ │        │ ┌──────────────────┬─┐ │
│ │ invalid-email      │ │        │ │ user@example.com │✓│ │
│ └────────────────────┘ │        │ └──────────────────┴─┘ │
│ ⚠ Enter a valid email  │        │ ✓ Email is available    │
└────────────────────────┘        └────────────────────────┘
```

---

## States

### Default Variant States

| State    | Background    | Border         | Text           | Label Color    | Shadow           | Notes                          |
|----------|---------------|----------------|----------------|----------------|------------------|--------------------------------|
| Default  | `white`       | `neutral-300`  | `neutral-900`  | `neutral-700`  | `none`           | Resting state                  |
| Hover    | `white`       | `neutral-400`  | `neutral-900`  | `neutral-700`  | `none`           | Border darkens on hover        |
| Focus    | `white`       | `blue-600`     | `neutral-900`  | `blue-600`     | `ring-2 blue-100`| Label color changes to blue    |
| Filled   | `white`       | `neutral-300`  | `neutral-900`  | `neutral-700`  | `none`           | Has value, not focused         |
| Disabled | `neutral-50`  | `neutral-200`  | `neutral-400`  | `neutral-400`  | `none`           | Non-interactive, reduced opacity|
| Read-only| `neutral-50`  | `neutral-200`  | `neutral-900`  | `neutral-700`  | `none`           | Selectable but not editable    |

### Error Variant States

| State    | Background    | Border         | Text           | Label Color    | Helper Color   | Shadow           |
|----------|---------------|----------------|----------------|----------------|----------------|------------------|
| Default  | `white`       | `red-500`      | `neutral-900`  | `red-600`      | `red-600`      | `none`           |
| Hover    | `white`       | `red-600`      | `neutral-900`  | `red-600`      | `red-600`      | `none`           |
| Focus    | `white`       | `red-600`      | `neutral-900`  | `red-600`      | `red-600`      | `ring-2 red-100` |

### Success Variant States

| State    | Background    | Border         | Text           | Label Color    | Helper Color   | Shadow             |
|----------|---------------|----------------|----------------|----------------|----------------|--------------------|
| Default  | `white`       | `green-500`    | `neutral-900`  | `green-600`    | `green-600`    | `none`             |
| Hover    | `white`       | `green-600`    | `neutral-900`  | `green-600`    | `green-600`    | `none`             |
| Focus    | `white`       | `green-600`    | `neutral-900`  | `green-600`    | `green-600`    | `ring-2 green-100` |

### Filled Variant States

| State    | Background     | Border         | Text           | Label Color    | Shadow           |
|----------|----------------|----------------|----------------|----------------|------------------|
| Default  | `neutral-100`  | `transparent`  | `neutral-900`  | `neutral-700`  | `none`           |
| Hover    | `neutral-100`  | `neutral-400`  | `neutral-900`  | `neutral-700`  | `none`           |
| Focus    | `white`        | `blue-600`     | `neutral-900`  | `blue-600`     | `ring-2 blue-100`|
| Disabled | `neutral-50`   | `transparent`  | `neutral-400`  | `neutral-400`  | `none`           |

---

## Sizing

| Size | Height | Padding (y / x) | Font Size | Line Height | Label Size | Helper Size | Icon Size | Border Radius |
|------|--------|------------------|-----------|-------------|------------|-------------|-----------|---------------|
| sm   | 32px   | 6px / 10px       | 14px      | 20px        | 12px       | 12px        | 16px      | `sm` (4px)    |
| md   | 40px   | 8px / 12px       | 16px      | 24px        | 14px       | 14px        | 20px      | `md` (6px)    |
| lg   | 48px   | 12px / 16px      | 16px      | 24px        | 14px       | 14px        | 20px      | `md` (6px)    |

### Spacing

| Property                   | Value  | Token       |
|----------------------------|--------|-------------|
| Label to input gap         | 6px    | --          |
| Input to helper text gap   | 4px    | `{space.1}` |
| Prefix/suffix inner padding| 12px   | `{space.3}` |
| Prefix icon to text gap    | 8px    | `{space.2}` |
| Border width               | 1px    | --          |
| Focus border width         | 2px    | --          |

---

## Accessibility

- **Label**: Every input must have a visible `<label>` element associated via `for`/`id`. If a visible label is not possible, use `aria-label` or `aria-labelledby`.
- **Required**: Mark required fields with `aria-required="true"` and display a visual indicator (asterisk or "(required)" text). Do not rely on color or the asterisk alone.
- **Error state**: Use `aria-invalid="true"` when the field has a validation error. Connect the error message to the input using `aria-describedby` pointing to the error message element ID.
- **Helper text**: Connect helper text to the input using `aria-describedby`. When both helper text and error text exist, error takes priority.
- **Keyboard**:
  - `Tab` / `Shift+Tab` to navigate to and from the input.
  - Standard text editing keys are supported natively.
  - `Escape` can optionally clear the input or close autocomplete suggestions.
- **Autocomplete**: Use the `autocomplete` attribute (e.g., `autocomplete="email"`, `autocomplete="given-name"`) to help browsers and assistive technologies autofill fields.
- **Focus indicator**: 2px solid ring in `blue-100` with `blue-600` border. Meets WCAG 2.1 SC 2.4.7 and SC 1.4.11.
- **Color contrast**: All text/background combinations meet WCAG AA (4.5:1). Placeholder text in `neutral-400` on white meets 3:1 minimum for non-text elements.
- **Error identification**: Error messages are announced to screen readers via `aria-live="polite"` or by the `aria-describedby` association when the user revisits the field.

---

## Design Tokens

```json
{
  "input": {
    "border-radius": {
      "sm": "{border.radius.sm}",
      "md": "{border.radius.md}",
      "lg": "{border.radius.md}"
    },
    "font-family": "{typography.font.sans}",
    "transition": "border-color 150ms ease, box-shadow 150ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "0px",
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
    "filled": {
      "bg": "{color.neutral.100}",
      "bg-focus": "{color.white}",
      "bg-disabled": "{color.neutral.50}",
      "border": "transparent",
      "border-hover": "{color.neutral.400}",
      "border-focus": "{color.blue.600}"
    },
    "error": {
      "border": "{color.red.500}",
      "border-focus": "{color.red.600}",
      "label-color": "{color.red.600}",
      "helper-color": "{color.red.600}",
      "focus-ring-color": "{color.red.100}"
    },
    "success": {
      "border": "{color.green.500}",
      "border-focus": "{color.green.600}",
      "label-color": "{color.green.600}",
      "helper-color": "{color.green.600}",
      "focus-ring-color": "{color.green.100}"
    },
    "label": {
      "font-size-sm": "12px",
      "font-size-md": "14px",
      "font-weight": "500",
      "color": "{color.neutral.700}",
      "color-focus": "{color.blue.600}",
      "color-disabled": "{color.neutral.400}"
    },
    "helper": {
      "font-size": "14px",
      "font-weight": "400",
      "color": "{color.neutral.500}",
      "color-error": "{color.red.600}",
      "color-success": "{color.green.600}"
    },
    "sizing": {
      "sm": {
        "height": "32px",
        "padding-x": "{space.2.5}",
        "padding-y": "{space.1.5}",
        "font-size": "{typography.body.sm.size}",
        "icon-size": "16px"
      },
      "md": {
        "height": "40px",
        "padding-x": "{space.3}",
        "padding-y": "{space.2}",
        "font-size": "{typography.body.md.size}",
        "icon-size": "20px"
      },
      "lg": {
        "height": "48px",
        "padding-x": "{space.4}",
        "padding-y": "{space.3}",
        "font-size": "{typography.body.md.size}",
        "icon-size": "20px"
      }
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Always provide a visible label for every input field -- labels above the field are preferred for readability.
- Use placeholder text as a supplementary hint, never as a replacement for a label.
- Validate on blur or on submit, not on every keystroke -- real-time validation may be used for password strength or username availability.
- Show error messages inline directly below the input that has the error.
- Use the prefix slot for currency symbols, country codes, or search icons.
- Use the suffix slot for clear buttons, visibility toggles (password), or unit labels.
- Group related inputs together with consistent spacing (16px vertical gap between fields).

**Don't:**
- Don't use placeholder text as the only label -- it disappears when the user starts typing.
- Don't rely on color alone to communicate error or success state -- always include a text message and/or icon.
- Don't disable the entire form when only one field is invalid -- disable only the submit button.
- Don't use inputs for long-form text -- use the TextArea component instead.
- Don't override token values with hardcoded hex colors.
- Don't add validation messages before the user has interacted with the field.

---

## Code Example

### HTML

```html
<!-- Default input with label and helper text -->
<div class="ff-input-field ff-input-field--md">
  <label class="ff-input-field__label" for="email">
    Email address
  </label>
  <div class="ff-input-field__wrapper">
    <input
      class="ff-input"
      type="email"
      id="email"
      name="email"
      placeholder="you@example.com"
      aria-describedby="email-helper"
    />
  </div>
  <p class="ff-input-field__helper" id="email-helper">
    We'll never share your email with anyone else.
  </p>
</div>

<!-- Input with prefix icon and suffix clear button -->
<div class="ff-input-field ff-input-field--md">
  <label class="ff-input-field__label" for="search">Search</label>
  <div class="ff-input-field__wrapper">
    <span class="ff-input-field__prefix" aria-hidden="true">
      <svg><!-- search icon --></svg>
    </span>
    <input
      class="ff-input"
      type="search"
      id="search"
      name="search"
      placeholder="Search products..."
    />
    <button class="ff-input-field__suffix ff-input-field__clear" aria-label="Clear search">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
  </div>
</div>

<!-- Error state -->
<div class="ff-input-field ff-input-field--md ff-input-field--error">
  <label class="ff-input-field__label" for="username">
    Username <span aria-hidden="true">*</span>
  </label>
  <div class="ff-input-field__wrapper">
    <input
      class="ff-input"
      type="text"
      id="username"
      name="username"
      value="ab"
      aria-required="true"
      aria-invalid="true"
      aria-describedby="username-error"
    />
  </div>
  <p class="ff-input-field__error" id="username-error" role="alert">
    Username must be at least 3 characters.
  </p>
</div>

<!-- Success state -->
<div class="ff-input-field ff-input-field--md ff-input-field--success">
  <label class="ff-input-field__label" for="username-ok">Username</label>
  <div class="ff-input-field__wrapper">
    <input
      class="ff-input"
      type="text"
      id="username-ok"
      name="username"
      value="flaviofusuma"
      aria-describedby="username-ok-helper"
    />
    <span class="ff-input-field__suffix" aria-hidden="true">
      <svg><!-- check icon --></svg>
    </span>
  </div>
  <p class="ff-input-field__helper ff-input-field__helper--success" id="username-ok-helper">
    Username is available.
  </p>
</div>

<!-- Disabled input -->
<div class="ff-input-field ff-input-field--md ff-input-field--disabled">
  <label class="ff-input-field__label" for="org">Organization</label>
  <div class="ff-input-field__wrapper">
    <input
      class="ff-input"
      type="text"
      id="org"
      name="org"
      value="Flavio Fusuma Inc."
      disabled
    />
  </div>
</div>

<!-- Filled variant -->
<div class="ff-input-field ff-input-field--md ff-input-field--filled">
  <label class="ff-input-field__label" for="city">City</label>
  <div class="ff-input-field__wrapper">
    <input
      class="ff-input"
      type="text"
      id="city"
      name="city"
      placeholder="Enter your city"
    />
  </div>
</div>
```

### JSX

```jsx
import { Input } from '@flavio-fusuma/ui';
import { SearchIcon, CloseIcon, CheckIcon } from '@flavio-fusuma/icons';

// Default input
<Input
  label="Email address"
  type="email"
  placeholder="you@example.com"
  helperText="We'll never share your email with anyone else."
  size="md"
/>

// Input with prefix and suffix
<Input
  label="Search"
  type="search"
  placeholder="Search products..."
  size="md"
  prefix={<SearchIcon />}
  suffix={<CloseIcon onClick={handleClear} aria-label="Clear search" />}
/>

// Error state
<Input
  label="Username"
  value="ab"
  size="md"
  required
  error="Username must be at least 3 characters."
/>

// Success state
<Input
  label="Username"
  value="flaviofusuma"
  size="md"
  success="Username is available."
  suffix={<CheckIcon />}
/>

// Disabled
<Input
  label="Organization"
  value="Flavio Fusuma Inc."
  size="md"
  disabled
/>

// Filled variant
<Input
  label="City"
  variant="filled"
  placeholder="Enter your city"
  size="md"
/>

// With character count
<Input
  label="Display name"
  size="md"
  maxLength={30}
  showCharacterCount
/>
```

---

## Related Components

- **[TextArea](./text-areas.md)** -- For multi-line text entry; use instead of Input when content exceeds a single line.
- **[Select](./select.md)** -- For choosing from a predefined list of options rather than free-text entry.
- **[Buttons](./buttons.md)** -- Often paired with inputs in form layouts for submit and cancel actions.
- **[Checkbox & Radio](./checkbox-radio.md)** -- For selection controls; use when the user must pick from a fixed set of choices.
- **[Tooltips](./tooltips.md)** -- Can provide additional context on hover for input fields with complex requirements.
