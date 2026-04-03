# Select

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Select components allow users to choose one or more options from a predefined list. The system provides two fundamental variants: a native select that leverages the browser's built-in dropdown for maximum accessibility and performance, and a custom select that offers richer features including search, multi-select, and custom option rendering. Use selects when the list of choices is too long for radio buttons or checkboxes (typically more than 5 options).

---

## Anatomy

### Native Select

```
┌──────────────────────────────────────────────────────┐
│  [Label Text]                                        │
│  ┌──────────────────────────────────────────────────┐│
│  │  [Selected Value / Placeholder]       ┌────────┐ ││
│  │                                       │Chevron │ ││
│  │                                       └────────┘ ││
│  └──────────────────────────────────────────────────┘│
│  [Helper text]                                       │
└──────────────────────────────────────────────────────┘
```

### Custom Select

```
┌──────────────────────────────────────────────────────┐
│  [Label Text]                                        │
│  ┌──────────────────────────────────────────────────┐│
│  │  [Selected Value / Placeholder]       ┌────────┐ ││
│  │                                       │Chevron │ ││
│  └──────────────────────────────────────────────────┘│
│  ┌──────────────────────────────────────────────────┐│
│  │ ┌──────────────────────────────────────────────┐ ││
│  │ │ 🔍  Search options...                        │ ││
│  │ └──────────────────────────────────────────────┘ ││
│  │ ┌──────────────────────────────────────────────┐ ││
│  │ │ ☑  Option A (selected)                       │ ││
│  │ ├──────────────────────────────────────────────┤ ││
│  │ │    Option B                                  │ ││
│  │ ├──────────────────────────────────────────────┤ ││
│  │ │    Option C                                  │ ││
│  │ ├──────────────────────────────────────────────┤ ││
│  │ │    Option D                                  │ ││
│  │ └──────────────────────────────────────────────┘ ││
│  └──────────────────────────────────────────────────┘│
│  [Helper text]                                       │
└──────────────────────────────────────────────────────┘

Multi-select trigger (tags):
┌──────────────────────────────────────────────────────┐
│  [Label Text]                                        │
│  ┌──────────────────────────────────────────────────┐│
│  │ ┌──────┬─┐ ┌──────┬─┐ ┌──────┬─┐    ┌────────┐ ││
│  │ │ Tag1 │✕│ │ Tag2 │✕│ │ Tag3 │✕│    │Chevron │ ││
│  │ └──────┴─┘ └──────┴─┘ └──────┴─┘    └────────┘ ││
│  └──────────────────────────────────────────────────┘│
└──────────────────────────────────────────────────────┘
```

| Part              | Required | Description                                           |
|-------------------|----------|-------------------------------------------------------|
| Container         | Yes      | Outer wrapper for the entire component                 |
| Label             | Yes      | Text label above the trigger (visually or via aria)    |
| Trigger           | Yes      | The clickable element that opens the dropdown          |
| Selected value    | Yes      | Displays the current selection or placeholder          |
| Chevron icon      | Yes      | Down arrow indicating the dropdown affordance          |
| Dropdown panel    | No*      | The options list (* native variant uses browser UI)    |
| Search input      | No       | Filter input at the top of the dropdown (custom only)  |
| Option            | Yes      | Individual selectable item in the list                 |
| Option group      | No       | Labeled section header to group related options        |
| Check indicator   | No       | Checkmark or checkbox for selected items               |
| Tags              | No       | Removable chips showing multi-select selections        |
| Helper text       | No       | Guidance text below the trigger                        |
| Error message     | No       | Validation error text replacing helper text            |
| Clear button      | No       | Clears the current selection                           |

---

## Variants

| Variant       | Description                                          | Use Case                                     |
|---------------|------------------------------------------------------|----------------------------------------------|
| Native        | Uses the browser's built-in `<select>` element       | Simple forms, maximum accessibility, mobile   |
| Custom        | Custom-rendered dropdown with enhanced features       | Rich option rendering, search, grouping       |
| Multi-select  | Allows selecting multiple options, displayed as tags  | Filters, tag assignment, multi-choice forms   |
| Searchable    | Includes a search/filter input in the dropdown       | Long lists (10+ options), country pickers     |

### Sub-Variants

| Sub-Variant | Description                                        |
|-------------|----------------------------------------------------|
| Default     | White background, neutral border                    |
| Filled      | Neutral-100 background, no border at rest           |
| Error       | Red border, error message visible                   |
| Disabled    | Reduced opacity, non-interactive                    |

---

## States

### Trigger States

| State    | Background    | Border         | Text           | Chevron       | Shadow            | Notes                           |
|----------|---------------|----------------|----------------|---------------|-------------------|---------------------------------|
| Default  | `white`       | `neutral-300`  | `neutral-900`  | `neutral-500` | `none`            | Resting, closed state           |
| Hover    | `white`       | `neutral-400`  | `neutral-900`  | `neutral-700` | `none`            | Mouse over trigger              |
| Focus    | `white`       | `blue-600`     | `neutral-900`  | `blue-600`    | `ring-2 blue-100` | Keyboard focus                  |
| Open     | `white`       | `blue-600`     | `neutral-900`  | `blue-600`    | `ring-2 blue-100` | Dropdown is expanded            |
| Disabled | `neutral-50`  | `neutral-200`  | `neutral-400`  | `neutral-300` | `none`            | Non-interactive                 |
| Error    | `white`       | `red-500`      | `neutral-900`  | `neutral-500` | `none`            | Validation error                |

### Option States

| State       | Background     | Text           | Check Icon    | Notes                          |
|-------------|----------------|----------------|---------------|--------------------------------|
| Default     | `transparent`  | `neutral-900`  | hidden        | Resting option                 |
| Hover       | `neutral-100`  | `neutral-900`  | hidden        | Mouse over option              |
| Focus       | `blue-50`      | `neutral-900`  | hidden        | Keyboard highlighted           |
| Selected    | `blue-50`      | `blue-700`     | `blue-600`    | Currently selected option      |
| Selected + Hover | `blue-100` | `blue-700`    | `blue-600`    | Hover on selected option       |
| Disabled    | `transparent`  | `neutral-400`  | hidden        | Non-selectable option          |

---

## Sizing

| Size | Trigger Height | Padding (y / x) | Font Size | Chevron Size | Border Radius |
|------|----------------|------------------|-----------|--------------|---------------|
| sm   | 32px           | 6px / 10px       | 14px      | 16px         | `sm` (4px)    |
| md   | 40px           | 8px / 12px       | 16px      | 20px         | `md` (6px)    |
| lg   | 48px           | 12px / 16px      | 16px      | 20px         | `md` (6px)    |

### Dropdown Panel Sizing

| Property              | Value               | Token           |
|-----------------------|---------------------|-----------------|
| Max height            | 256px (~ 6.5 items) | --              |
| Min width             | Match trigger width  | --              |
| Padding               | 4px                 | `{space.1}`     |
| Border radius         | 8px                 | `{border.radius.lg}` |
| Shadow                | `lg`                | `{shadow.lg}`   |
| Border                | 1px `neutral-200`   | --              |
| Option height         | 36px                | --              |
| Option padding        | 8px 12px            | `{space.2} {space.3}` |
| Option gap            | 2px                 | --              |
| Group label height    | 32px                | --              |
| Group label padding   | 8px 12px            | `{space.2} {space.3}` |
| Search input margin   | 4px                 | `{space.1}`     |

---

## Accessibility

- **Role (native)**: Use semantic `<select>` and `<option>` elements. The browser provides full accessibility support.
- **Role (custom)**: The trigger must have `role="combobox"` with `aria-haspopup="listbox"`. The dropdown must have `role="listbox"`. Each option must have `role="option"` with `aria-selected`.
- **Multi-select**: Use `aria-multiselectable="true"` on the listbox. Selected options use `aria-selected="true"`.
- **Searchable**: The search input should have `role="combobox"` with `aria-autocomplete="list"` and `aria-controls` pointing to the listbox ID. Update `aria-activedescendant` as the user navigates options.
- **Label**: Associate the label via `for`/`id` for native selects or `aria-labelledby` for custom selects.
- **Error state**: Apply `aria-invalid="true"` on the trigger and connect error messages via `aria-describedby`.
- **Keyboard**:
  - **Native**: `Space` or `Enter` opens the native dropdown. Arrow keys navigate options.
  - **Custom trigger**: `Space`, `Enter`, or `ArrowDown` opens the dropdown. `Escape` closes it.
  - **Custom options**: `ArrowUp` / `ArrowDown` navigate options. `Enter` or `Space` selects. `Home` / `End` jump to first/last option.
  - **Searchable**: Typing filters the list. `ArrowDown` moves from search input to option list.
  - **Multi-select**: `Space` toggles selection without closing. `Enter` confirms and closes.
- **Focus management**: When the dropdown opens, focus moves to the first selected option or the first option. When it closes, focus returns to the trigger.
- **Expanded state**: The trigger must have `aria-expanded="true"` when open and `aria-expanded="false"` when closed.
- **Focus indicator**: 2px solid ring in `blue-100` with `blue-600` border on trigger and options.
- **Color contrast**: All text meets WCAG AA (4.5:1).

---

## Design Tokens

```json
{
  "select": {
    "font-family": "{typography.font.sans}",
    "transition": "border-color 150ms ease, box-shadow 150ms ease",
    "trigger": {
      "bg": "{color.white}",
      "bg-disabled": "{color.neutral.50}",
      "border": "{color.neutral.300}",
      "border-hover": "{color.neutral.400}",
      "border-focus": "{color.blue.600}",
      "border-error": "{color.red.500}",
      "border-disabled": "{color.neutral.200}",
      "text": "{color.neutral.900}",
      "text-placeholder": "{color.neutral.400}",
      "text-disabled": "{color.neutral.400}",
      "chevron-color": "{color.neutral.500}",
      "chevron-color-focus": "{color.blue.600}",
      "focus-ring-color": "{color.blue.100}",
      "border-radius": {
        "sm": "{border.radius.sm}",
        "md": "{border.radius.md}",
        "lg": "{border.radius.md}"
      }
    },
    "dropdown": {
      "bg": "{color.white}",
      "border": "{color.neutral.200}",
      "border-radius": "{border.radius.lg}",
      "shadow": "{shadow.lg}",
      "max-height": "256px",
      "padding": "{space.1}",
      "z-index": "50"
    },
    "option": {
      "bg": "transparent",
      "bg-hover": "{color.neutral.100}",
      "bg-focus": "{color.blue.50}",
      "bg-selected": "{color.blue.50}",
      "bg-selected-hover": "{color.blue.100}",
      "text": "{color.neutral.900}",
      "text-selected": "{color.blue.700}",
      "text-disabled": "{color.neutral.400}",
      "check-color": "{color.blue.600}",
      "height": "36px",
      "padding": "{space.2} {space.3}",
      "border-radius": "{border.radius.sm}"
    },
    "group-label": {
      "font-size": "12px",
      "font-weight": "600",
      "color": "{color.neutral.500}",
      "text-transform": "uppercase",
      "letter-spacing": "0.05em"
    },
    "tag": {
      "bg": "{color.blue.100}",
      "text": "{color.blue.700}",
      "border-radius": "{border.radius.sm}",
      "remove-hover-bg": "{color.blue.200}",
      "height": "24px",
      "font-size": "12px",
      "padding": "2px 6px"
    },
    "search": {
      "bg": "{color.neutral.50}",
      "border": "{color.neutral.200}",
      "border-focus": "{color.blue.600}",
      "text": "{color.neutral.900}",
      "placeholder": "{color.neutral.400}",
      "border-radius": "{border.radius.sm}"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use native select for simple forms with fewer than 15 options and no need for search or custom rendering.
- Use custom select when you need search, multi-select, option grouping, or custom option rendering (icons, descriptions).
- Always include a label -- even if visually hidden, it must be available to assistive technology.
- Provide a meaningful placeholder like "Select a country" instead of generic "Select...".
- Use option groups to organize long lists logically (e.g., group countries by continent).
- Enable search for lists with more than 10 options.
- Show selected items as removable tags in multi-select for clear visual feedback.

**Don't:**
- Don't use a select for fewer than 3 options -- use radio buttons instead.
- Don't use a custom select when a native select works fine -- native selects have better accessibility and mobile support out of the box.
- Don't mix native and custom selects in the same form -- maintain consistency.
- Don't allow the dropdown to extend beyond the viewport without scroll management.
- Don't override token colors with hardcoded hex values.
- Don't disable individual options without explaining why they are unavailable.
- Don't use multi-select for mutually exclusive choices -- use radio buttons or a single-select instead.

---

## Code Example

### HTML

```html
<!-- Native select -->
<div class="ff-select-field ff-select-field--md">
  <label class="ff-select-field__label" for="country">Country</label>
  <div class="ff-select-field__wrapper">
    <select class="ff-select ff-select--native" id="country" name="country">
      <option value="" disabled selected>Select a country</option>
      <optgroup label="North America">
        <option value="us">United States</option>
        <option value="ca">Canada</option>
        <option value="mx">Mexico</option>
      </optgroup>
      <optgroup label="Europe">
        <option value="uk">United Kingdom</option>
        <option value="de">Germany</option>
        <option value="fr">France</option>
      </optgroup>
    </select>
    <svg class="ff-select-field__chevron" aria-hidden="true"><!-- chevron --></svg>
  </div>
  <p class="ff-select-field__helper">Choose your country of residence.</p>
</div>

<!-- Custom single select -->
<div class="ff-select-field ff-select-field--md">
  <label class="ff-select-field__label" id="role-label">Role</label>
  <button
    class="ff-select__trigger"
    role="combobox"
    aria-expanded="false"
    aria-haspopup="listbox"
    aria-labelledby="role-label"
    aria-controls="role-listbox"
  >
    <span class="ff-select__value">Select a role</span>
    <svg class="ff-select-field__chevron" aria-hidden="true"><!-- chevron --></svg>
  </button>
  <ul class="ff-select__dropdown" id="role-listbox" role="listbox" aria-labelledby="role-label">
    <li class="ff-select__option" role="option" aria-selected="false">Admin</li>
    <li class="ff-select__option" role="option" aria-selected="false">Editor</li>
    <li class="ff-select__option ff-select__option--selected" role="option" aria-selected="true">
      <svg class="ff-select__check" aria-hidden="true"><!-- check --></svg>
      Viewer
    </li>
    <li class="ff-select__option ff-select__option--disabled" role="option" aria-disabled="true">
      Owner (assigned)
    </li>
  </ul>
</div>

<!-- Custom multi-select with tags and search -->
<div class="ff-select-field ff-select-field--md">
  <label class="ff-select-field__label" id="tags-label">Tags</label>
  <div
    class="ff-select__trigger ff-select__trigger--multi"
    role="combobox"
    aria-expanded="false"
    aria-haspopup="listbox"
    aria-labelledby="tags-label"
    aria-controls="tags-listbox"
  >
    <span class="ff-select__tag">
      Design <button aria-label="Remove Design" class="ff-select__tag-remove">✕</button>
    </span>
    <span class="ff-select__tag">
      Frontend <button aria-label="Remove Frontend" class="ff-select__tag-remove">✕</button>
    </span>
    <svg class="ff-select-field__chevron" aria-hidden="true"><!-- chevron --></svg>
  </div>
  <div class="ff-select__dropdown" id="tags-listbox" role="listbox" aria-multiselectable="true">
    <div class="ff-select__search">
      <input type="text" placeholder="Search tags..." aria-label="Search tags" />
    </div>
    <ul>
      <li role="option" aria-selected="true">Design</li>
      <li role="option" aria-selected="true">Frontend</li>
      <li role="option" aria-selected="false">Backend</li>
      <li role="option" aria-selected="false">DevOps</li>
    </ul>
  </div>
</div>

<!-- Error state -->
<div class="ff-select-field ff-select-field--md ff-select-field--error">
  <label class="ff-select-field__label" for="priority">Priority</label>
  <select
    class="ff-select ff-select--native"
    id="priority"
    name="priority"
    aria-invalid="true"
    aria-describedby="priority-error"
  >
    <option value="" disabled selected>Select priority</option>
    <option value="low">Low</option>
    <option value="medium">Medium</option>
    <option value="high">High</option>
  </select>
  <p class="ff-select-field__error" id="priority-error" role="alert">
    Please select a priority level.
  </p>
</div>
```

### JSX

```jsx
import { Select, NativeSelect } from '@flavio-fusuma/ui';

// Native select
<NativeSelect
  label="Country"
  placeholder="Select a country"
  helperText="Choose your country of residence."
  size="md"
  options={[
    { group: 'North America', items: [
      { value: 'us', label: 'United States' },
      { value: 'ca', label: 'Canada' },
    ]},
    { group: 'Europe', items: [
      { value: 'uk', label: 'United Kingdom' },
      { value: 'de', label: 'Germany' },
    ]},
  ]}
/>

// Custom single select
<Select
  label="Role"
  placeholder="Select a role"
  size="md"
  options={[
    { value: 'admin', label: 'Admin' },
    { value: 'editor', label: 'Editor' },
    { value: 'viewer', label: 'Viewer' },
    { value: 'owner', label: 'Owner (assigned)', disabled: true },
  ]}
  value="viewer"
  onChange={handleChange}
/>

// Custom searchable select
<Select
  label="Country"
  placeholder="Search for a country..."
  size="md"
  searchable
  options={countries}
  onChange={handleCountryChange}
/>

// Multi-select with tags
<Select
  label="Tags"
  placeholder="Select tags..."
  size="md"
  multiple
  searchable
  options={tagOptions}
  value={['design', 'frontend']}
  onChange={handleTagsChange}
/>

// Error state
<Select
  label="Priority"
  placeholder="Select priority"
  size="md"
  error="Please select a priority level."
  options={[
    { value: 'low', label: 'Low' },
    { value: 'medium', label: 'Medium' },
    { value: 'high', label: 'High' },
  ]}
/>

// Disabled
<Select
  label="Department"
  value="engineering"
  size="md"
  disabled
  options={departments}
/>
```

---

## Related Components

- **[Inputs](./inputs.md)** -- For free-text entry; use Input when the user needs to type a custom value not from a predefined list.
- **[Checkbox & Radio](./checkbox-radio.md)** -- For fewer than 5 options, use radio buttons (single) or checkboxes (multiple) instead of a select.
- **[Buttons](./buttons.md)** -- Often paired with selects in form layouts.
- **[Tags](./tags.md)** -- Multi-select uses tags to display selected values; see Tags documentation for styling details.
- **[Tooltips](./tooltips.md)** -- Use tooltips to explain disabled options in custom selects.
