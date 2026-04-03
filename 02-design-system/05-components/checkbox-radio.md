# Checkbox & Radio

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Checkboxes and radio buttons are selection controls that allow users to make choices from a set of options. Checkboxes support independent, multi-select choices (including an indeterminate state for partial group selection), while radio buttons enforce mutually exclusive, single-select choices within a group. Use these controls when the full set of options should be visible at a glance and the list is relatively short (typically 2-7 items).

---

## Anatomy

### Checkbox

```
┌───────────────────────────────────────────────┐
│  ┌────┐                                       │
│  │ ✓  │  [Label text]                         │
│  └────┘  [Description / helper text]          │
└───────────────────────────────────────────────┘

Indeterminate state:
┌────┐
│ —  │  Select all items
└────┘

Checkbox group:
┌───────────────────────────────────────────────┐
│  [Group Label]                                │
│  ┌────┐                                       │
│  │ ✓  │  Option A                             │
│  └────┘                                       │
│  ┌────┐                                       │
│  │    │  Option B                             │
│  └────┘                                       │
│  ┌────┐                                       │
│  │ ✓  │  Option C                             │
│  └────┘                                       │
│  [Helper text for the group]                  │
└───────────────────────────────────────────────┘
```

### Radio

```
┌───────────────────────────────────────────────┐
│  ( ● )  [Label text]                          │
│         [Description / helper text]           │
└───────────────────────────────────────────────┘

Radio group:
┌───────────────────────────────────────────────┐
│  [Group Label]                                │
│  ( ● )  Option A                              │
│  (   )  Option B                              │
│  (   )  Option C                              │
│  [Helper text for the group]                  │
└───────────────────────────────────────────────┘
```

### Anatomy Parts

| Part              | Required | Description                                               |
|-------------------|----------|-----------------------------------------------------------|
| Control           | Yes      | The checkbox square or radio circle                        |
| Check indicator   | Yes      | Checkmark (checkbox), dot (radio), or dash (indeterminate) |
| Label             | Yes      | Text label next to the control (visually or via aria-label)|
| Description       | No       | Secondary text providing additional context                |
| Group container   | No       | Wrapper for a set of related checkboxes or radios          |
| Group label       | No       | Heading text for the group (rendered as legend or heading) |
| Group helper text | No       | Guidance or error text for the entire group                |

---

## Variants

### Checkbox Variants

| Variant        | Description                                       | Use Case                                       |
|----------------|---------------------------------------------------|------------------------------------------------|
| Single         | Standalone checkbox for a boolean choice           | Terms acceptance, "Remember me", opt-ins        |
| Group          | Set of checkboxes for multi-select                 | Filter options, feature selection, preferences  |
| Indeterminate  | Dash indicator for partial group selection          | "Select all" when some children are selected    |
| With description | Checkbox with secondary descriptive text         | Settings with explanations                      |

### Radio Variants

| Variant        | Description                                       | Use Case                                       |
|----------------|---------------------------------------------------|------------------------------------------------|
| Group          | Set of radio buttons for single-select             | Payment method, shipping speed, plan selection  |
| With description | Radio with secondary descriptive text            | Plan cards, options needing explanation          |
| Horizontal     | Radio group laid out horizontally                  | 2-3 short options, gender selection             |
| Vertical       | Radio group laid out vertically (default)          | Standard form groups                            |

---

## Label Positioning

| Position | Description                     | Use Case                              |
|----------|---------------------------------|---------------------------------------|
| Right    | Label to the right of control (default) | Standard forms, settings lists  |
| Left     | Label to the left of control    | Settings panels, toggle-style layouts  |

```
Right (default):           Left:
┌────┐                              ┌────┐
│ ✓  │  Enable notifications    Enable notifications  │ ✓  │
└────┘                              └────┘
```

---

## States

### Checkbox States

| State               | Control BG      | Border         | Check Color   | Label Color    | Shadow            | Notes                        |
|----------------------|-----------------|----------------|---------------|----------------|-------------------|------------------------------|
| Unchecked            | `white`         | `neutral-300`  | --            | `neutral-900`  | `none`            | Default empty state          |
| Unchecked + Hover    | `white`         | `neutral-400`  | --            | `neutral-900`  | `none`            | Mouse over                   |
| Unchecked + Focus    | `white`         | `blue-600`     | --            | `neutral-900`  | `ring-2 blue-100` | Keyboard focus               |
| Checked              | `blue-600`      | `blue-600`     | `white`       | `neutral-900`  | `none`            | Selected                     |
| Checked + Hover      | `blue-700`      | `blue-700`     | `white`       | `neutral-900`  | `none`            | Hover on selected            |
| Checked + Focus      | `blue-600`      | `blue-600`     | `white`       | `neutral-900`  | `ring-2 blue-100` | Focus on selected            |
| Indeterminate        | `blue-600`      | `blue-600`     | `white`       | `neutral-900`  | `none`            | Partial group selection       |
| Indeterminate + Hover| `blue-700`      | `blue-700`     | `white`       | `neutral-900`  | `none`            | Hover on indeterminate       |
| Disabled unchecked   | `neutral-100`   | `neutral-200`  | --            | `neutral-400`  | `none`            | Disabled, not selected       |
| Disabled checked     | `neutral-300`   | `neutral-300`  | `white`       | `neutral-400`  | `none`            | Disabled, selected           |
| Error unchecked      | `white`         | `red-500`      | --            | `neutral-900`  | `none`            | Validation error             |
| Error checked        | `red-600`       | `red-600`      | `white`       | `neutral-900`  | `none`            | Error on selected            |

### Radio States

| State              | Control BG     | Border         | Dot Color     | Label Color    | Shadow            | Notes                        |
|--------------------|----------------|----------------|---------------|----------------|-------------------|------------------------------|
| Unselected         | `white`        | `neutral-300`  | --            | `neutral-900`  | `none`            | Default empty state          |
| Unselected + Hover | `white`        | `neutral-400`  | --            | `neutral-900`  | `none`            | Mouse over                   |
| Unselected + Focus | `white`        | `blue-600`     | --            | `neutral-900`  | `ring-2 blue-100` | Keyboard focus               |
| Selected           | `white`        | `blue-600`     | `blue-600`    | `neutral-900`  | `none`            | Active selection             |
| Selected + Hover   | `white`        | `blue-700`     | `blue-700`    | `neutral-900`  | `none`            | Hover on selected            |
| Selected + Focus   | `white`        | `blue-600`     | `blue-600`    | `neutral-900`  | `ring-2 blue-100` | Focus on selected            |
| Disabled unselected| `neutral-100`  | `neutral-200`  | --            | `neutral-400`  | `none`            | Disabled, not selected       |
| Disabled selected  | `neutral-100`  | `neutral-300`  | `neutral-300` | `neutral-400`  | `none`            | Disabled, selected           |
| Error unselected   | `white`        | `red-500`      | --            | `neutral-900`  | `none`            | Validation error             |

---

## Sizing

### Control Size

| Size | Control W x H | Icon/Dot Size | Border Radius (checkbox) | Border Radius (radio) | Border Width |
|------|---------------|---------------|--------------------------|----------------------|--------------|
| sm   | 16px x 16px   | 10px          | `sm` (4px)               | `full` (9999px)      | 1.5px        |
| md   | 20px x 20px   | 12px          | `sm` (4px)               | `full` (9999px)      | 2px          |
| lg   | 24px x 24px   | 14px          | `sm` (4px)               | `full` (9999px)      | 2px          |

### Layout Spacing

| Property                     | Value  | Token       |
|------------------------------|--------|-------------|
| Control to label gap         | 8px    | `{space.2}` |
| Control to description gap   | 8px    | `{space.2}` |
| Label to description gap     | 2px    | --          |
| Group label to first item    | 8px    | `{space.2}` |
| Vertical gap between items   | 8px    | `{space.2}` |
| Horizontal gap between items | 24px   | `{space.6}` |
| Group to helper/error gap    | 4px    | `{space.1}` |

---

## Accessibility

- **Checkbox**: Use native `<input type="checkbox">` for full built-in accessibility. The label must be associated via `for`/`id` or by wrapping the input inside the `<label>`.
- **Radio**: Use native `<input type="radio">` elements with the same `name` attribute to form a group. The browser automatically manages mutual exclusivity.
- **Group**: Wrap checkbox and radio groups in a `<fieldset>` with a `<legend>` for the group label. The legend provides the accessible name for the group.
- **Indeterminate**: Set via JavaScript (`inputEl.indeterminate = true`). Announce with `aria-checked="mixed"` for screen readers.
- **Required**: Use `aria-required="true"` on the group fieldset. For individual checkboxes (e.g., terms acceptance), add `required` to the input.
- **Error state**: Apply `aria-invalid="true"` on the relevant input(s). Connect group error messages via `aria-describedby` on the fieldset.
- **Keyboard**:
  - **Checkbox**: `Tab` to navigate between checkboxes. `Space` toggles the checkbox.
  - **Radio**: `Tab` moves focus to the radio group. `ArrowUp` / `ArrowDown` (or `ArrowLeft` / `ArrowRight`) move between radios within the group and select them.
  - **Indeterminate**: `Space` toggles the indeterminate checkbox to checked (clearing the indeterminate state).
- **Focus indicator**: 2px solid ring in `blue-100` with `blue-600` border around the control. Meets WCAG 2.1 SC 2.4.7 and SC 1.4.11.
- **Color contrast**: `blue-600` on `white` background for checked state meets WCAG AA (4.5:1). Disabled states are exempt from contrast requirements.
- **Touch target**: Minimum 44x44px touch target via clickable label area, even when the control itself is 16-24px.

---

## Design Tokens

```json
{
  "checkbox": {
    "border-radius": "{border.radius.sm}",
    "transition": "background 150ms ease, border-color 150ms ease, box-shadow 150ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.100}",
    "unchecked": {
      "bg": "{color.white}",
      "border": "{color.neutral.300}",
      "border-hover": "{color.neutral.400}",
      "border-focus": "{color.blue.600}"
    },
    "checked": {
      "bg": "{color.blue.600}",
      "bg-hover": "{color.blue.700}",
      "border": "{color.blue.600}",
      "border-hover": "{color.blue.700}",
      "icon-color": "{color.white}"
    },
    "indeterminate": {
      "bg": "{color.blue.600}",
      "bg-hover": "{color.blue.700}",
      "border": "{color.blue.600}",
      "icon-color": "{color.white}"
    },
    "disabled": {
      "bg-unchecked": "{color.neutral.100}",
      "bg-checked": "{color.neutral.300}",
      "border": "{color.neutral.200}",
      "icon-color": "{color.white}",
      "label-color": "{color.neutral.400}"
    },
    "error": {
      "border": "{color.red.500}",
      "bg-checked": "{color.red.600}",
      "border-checked": "{color.red.600}"
    },
    "sizing": {
      "sm": { "size": "16px", "icon-size": "10px", "border-width": "1.5px" },
      "md": { "size": "20px", "icon-size": "12px", "border-width": "2px" },
      "lg": { "size": "24px", "icon-size": "14px", "border-width": "2px" }
    }
  },
  "radio": {
    "border-radius": "{border.radius.full}",
    "transition": "background 150ms ease, border-color 150ms ease, box-shadow 150ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.100}",
    "unselected": {
      "bg": "{color.white}",
      "border": "{color.neutral.300}",
      "border-hover": "{color.neutral.400}",
      "border-focus": "{color.blue.600}"
    },
    "selected": {
      "bg": "{color.white}",
      "border": "{color.blue.600}",
      "border-hover": "{color.blue.700}",
      "dot-color": "{color.blue.600}",
      "dot-color-hover": "{color.blue.700}"
    },
    "disabled": {
      "bg": "{color.neutral.100}",
      "border": "{color.neutral.200}",
      "dot-color": "{color.neutral.300}",
      "label-color": "{color.neutral.400}"
    },
    "error": {
      "border": "{color.red.500}"
    },
    "sizing": {
      "sm": { "size": "16px", "dot-size": "6px", "border-width": "1.5px" },
      "md": { "size": "20px", "dot-size": "8px", "border-width": "2px" },
      "lg": { "size": "24px", "dot-size": "10px", "border-width": "2px" }
    }
  },
  "selection-group": {
    "label-font-size": "14px",
    "label-font-weight": "600",
    "label-color": "{color.neutral.900}",
    "item-label-font-size": "16px",
    "item-label-font-weight": "400",
    "item-label-color": "{color.neutral.900}",
    "description-font-size": "14px",
    "description-color": "{color.neutral.500}",
    "helper-font-size": "14px",
    "helper-color": "{color.neutral.500}",
    "error-color": "{color.red.600}",
    "gap-vertical": "{space.2}",
    "gap-horizontal": "{space.6}"
  }
}
```

---

## Usage Guidelines

**Do:**
- Use checkboxes when users can select zero, one, or multiple options from a list.
- Use radio buttons when users must select exactly one option from a list.
- Always provide a visible label for each control -- clicking the label should toggle the control.
- Group related checkboxes or radios inside a `<fieldset>` with a descriptive `<legend>`.
- Use the indeterminate state for "select all" checkboxes that reflect partial group selection.
- Pre-select a default option in radio groups when there is a sensible default.
- Place descriptions below the label to explain complex options (e.g., pricing plan details).

**Don't:**
- Don't use a single radio button -- radios require at least two options. Use a checkbox for boolean toggles.
- Don't use checkboxes or radios for lists longer than 7 items -- use a Select component instead.
- Don't mix checkboxes and radios in the same visual group -- they represent different selection models.
- Don't leave radio groups without a default selection unless "no selection" is a valid state.
- Don't use horizontal layout for more than 3 radio or checkbox items -- it becomes hard to scan.
- Don't override token colors with hardcoded hex values.
- Don't rely on color alone to indicate the checked state -- the checkmark and dot provide shape-based indication.

---

## Code Example

### HTML

```html
<!-- Single checkbox -->
<label class="ff-checkbox ff-checkbox--md">
  <input type="checkbox" class="ff-checkbox__input" name="terms" required />
  <span class="ff-checkbox__control" aria-hidden="true">
    <svg class="ff-checkbox__icon"><!-- check icon --></svg>
  </span>
  <span class="ff-checkbox__label">I agree to the Terms of Service</span>
</label>

<!-- Checkbox with description -->
<label class="ff-checkbox ff-checkbox--md">
  <input type="checkbox" class="ff-checkbox__input" name="marketing" />
  <span class="ff-checkbox__control" aria-hidden="true">
    <svg class="ff-checkbox__icon"><!-- check icon --></svg>
  </span>
  <span class="ff-checkbox__content">
    <span class="ff-checkbox__label">Marketing emails</span>
    <span class="ff-checkbox__description">Receive updates about new features and promotions.</span>
  </span>
</label>

<!-- Checkbox group with indeterminate "select all" -->
<fieldset class="ff-checkbox-group">
  <legend class="ff-checkbox-group__label">Permissions</legend>

  <label class="ff-checkbox ff-checkbox--md">
    <input type="checkbox" class="ff-checkbox__input" aria-checked="mixed" />
    <span class="ff-checkbox__control ff-checkbox__control--indeterminate" aria-hidden="true">
      <svg class="ff-checkbox__icon"><!-- dash icon --></svg>
    </span>
    <span class="ff-checkbox__label">Select all</span>
  </label>

  <div class="ff-checkbox-group__items">
    <label class="ff-checkbox ff-checkbox--md">
      <input type="checkbox" class="ff-checkbox__input" name="perm" value="read" checked />
      <span class="ff-checkbox__control" aria-hidden="true">
        <svg class="ff-checkbox__icon"><!-- check icon --></svg>
      </span>
      <span class="ff-checkbox__label">Read</span>
    </label>

    <label class="ff-checkbox ff-checkbox--md">
      <input type="checkbox" class="ff-checkbox__input" name="perm" value="write" />
      <span class="ff-checkbox__control" aria-hidden="true">
        <svg class="ff-checkbox__icon"><!-- check icon --></svg>
      </span>
      <span class="ff-checkbox__label">Write</span>
    </label>

    <label class="ff-checkbox ff-checkbox--md">
      <input type="checkbox" class="ff-checkbox__input" name="perm" value="admin" checked />
      <span class="ff-checkbox__control" aria-hidden="true">
        <svg class="ff-checkbox__icon"><!-- check icon --></svg>
      </span>
      <span class="ff-checkbox__label">Admin</span>
    </label>
  </div>

  <p class="ff-checkbox-group__helper">Choose the permissions for this role.</p>
</fieldset>

<!-- Radio group -->
<fieldset class="ff-radio-group">
  <legend class="ff-radio-group__label">Shipping speed</legend>

  <label class="ff-radio ff-radio--md">
    <input type="radio" class="ff-radio__input" name="shipping" value="standard" checked />
    <span class="ff-radio__control" aria-hidden="true"></span>
    <span class="ff-radio__content">
      <span class="ff-radio__label">Standard (5-7 days)</span>
      <span class="ff-radio__description">Free shipping on all orders.</span>
    </span>
  </label>

  <label class="ff-radio ff-radio--md">
    <input type="radio" class="ff-radio__input" name="shipping" value="express" />
    <span class="ff-radio__control" aria-hidden="true"></span>
    <span class="ff-radio__content">
      <span class="ff-radio__label">Express (2-3 days)</span>
      <span class="ff-radio__description">$9.99 flat rate.</span>
    </span>
  </label>

  <label class="ff-radio ff-radio--md">
    <input type="radio" class="ff-radio__input" name="shipping" value="overnight" />
    <span class="ff-radio__control" aria-hidden="true"></span>
    <span class="ff-radio__content">
      <span class="ff-radio__label">Overnight (next day)</span>
      <span class="ff-radio__description">$24.99 flat rate.</span>
    </span>
  </label>
</fieldset>

<!-- Disabled radio -->
<label class="ff-radio ff-radio--md ff-radio--disabled">
  <input type="radio" class="ff-radio__input" name="plan" value="enterprise" disabled />
  <span class="ff-radio__control" aria-hidden="true"></span>
  <span class="ff-radio__label">Enterprise (contact sales)</span>
</label>
```

### JSX

```jsx
import { Checkbox, CheckboxGroup, Radio, RadioGroup } from '@flavio-fusuma/ui';

// Single checkbox
<Checkbox name="terms" required size="md">
  I agree to the Terms of Service
</Checkbox>

// Checkbox with description
<Checkbox name="marketing" size="md" description="Receive updates about new features and promotions.">
  Marketing emails
</Checkbox>

// Checkbox group with select all
<CheckboxGroup
  label="Permissions"
  helperText="Choose the permissions for this role."
  selectAll="Select all"
  value={['read', 'admin']}
  onChange={handlePermChange}
>
  <Checkbox value="read">Read</Checkbox>
  <Checkbox value="write">Write</Checkbox>
  <Checkbox value="admin">Admin</Checkbox>
</CheckboxGroup>

// Radio group
<RadioGroup
  label="Shipping speed"
  name="shipping"
  value="standard"
  onChange={handleShippingChange}
>
  <Radio value="standard" description="Free shipping on all orders.">
    Standard (5-7 days)
  </Radio>
  <Radio value="express" description="$9.99 flat rate.">
    Express (2-3 days)
  </Radio>
  <Radio value="overnight" description="$24.99 flat rate.">
    Overnight (next day)
  </Radio>
</RadioGroup>

// Horizontal radio group
<RadioGroup
  label="Gender"
  name="gender"
  direction="horizontal"
  onChange={handleGenderChange}
>
  <Radio value="male">Male</Radio>
  <Radio value="female">Female</Radio>
  <Radio value="other">Other</Radio>
</RadioGroup>

// Error state
<RadioGroup
  label="Payment method"
  name="payment"
  error="Please select a payment method."
>
  <Radio value="card">Credit card</Radio>
  <Radio value="paypal">PayPal</Radio>
  <Radio value="bank">Bank transfer</Radio>
</RadioGroup>

// Disabled checkbox
<Checkbox name="feature" disabled checked size="md">
  Advanced analytics (included in Pro plan)
</Checkbox>
```

---

## Related Components

- **[Toggle](./toggle.md)** -- For binary on/off settings with immediate effect; use instead of a single checkbox when the action takes effect immediately.
- **[Select](./select.md)** -- For lists longer than 7 items; use a select dropdown instead of checkboxes or radios.
- **[Inputs](./inputs.md)** -- For free-text entry alongside selection controls in forms.
- **[Buttons](./buttons.md)** -- Typically paired with selection controls for form submission.
- **[Cards](./cards.md)** -- Radio-style selection can be represented as selectable cards for richer option layouts.
