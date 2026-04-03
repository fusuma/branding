# Form Design Patterns

> Flavio Fusuma Design System -- Form layout strategies, validation approaches, error handling, multi-step forms, accessibility requirements, and common form templates.

---

## Overview

Forms are the primary mechanism for collecting data from users. Well-designed forms reduce friction, prevent errors, and guide users toward successful completion. Every form in the Flavio Fusuma system follows these principles:

1. **Minimize cognitive load.** Ask only for information that is necessary.
2. **Provide clear guidance.** Labels, placeholders, and helper text tell users exactly what is expected.
3. **Validate early, recover gracefully.** Catch errors close to the point of entry and provide actionable recovery instructions.
4. **Respect accessibility standards.** Every form is operable by keyboard, compatible with screen readers, and meets WCAG 2.1 AA requirements.

---

## Form Layout Patterns

### Single-Column Layout (Default)

The default form layout. Fields stack vertically in a single column. This layout is the easiest to scan and complete.

```
┌──────────────────────────────────┐
│ [Label]                          │
│ ┌──────────────────────────────┐ │
│ │ Input                        │ │
│ └──────────────────────────────┘ │
│ Helper text                      │
│                                  │
│ [Label]                          │
│ ┌──────────────────────────────┐ │
│ │ Input                        │ │
│ └──────────────────────────────┘ │
│                                  │
│ [Label]                          │
│ ┌──────────────────────────────┐ │
│ │ Textarea                     │ │
│ │                              │ │
│ └──────────────────────────────┘ │
│                                  │
│        ┌────────────────┐        │
│        │  Submit Button  │        │
│        └────────────────┘        │
└──────────────────────────────────┘
```

| Property | Value |
|---|---|
| Max width | 480px (contact forms), 640px (longer forms) |
| Field gap | 24px (`space-3`) between fields |
| Label to field gap | 4px |
| Field to helper text gap | 4px |
| Action button alignment | Left (single action), right or full-width (multiple actions) |

**When to use:** Contact forms, login, signup, any form with fewer than 8 fields.

### Two-Column Layout

Two related fields side by side. Use sparingly and only for logically paired fields (e.g., first name / last name, city / state).

```
┌─────────────────────────────────────────────┐
│ [First Name]          [Last Name]           │
│ ┌──────────────┐     ┌──────────────┐       │
│ │              │     │              │       │
│ └──────────────┘     └──────────────┘       │
│                                             │
│ [Email]                                     │
│ ┌─────────────────────────────────────────┐ │
│ │                                         │ │
│ └─────────────────────────────────────────┘ │
│                                             │
│ [City]               [State]    [Zip]       │
│ ┌──────────────┐    ┌──────┐  ┌──────┐     │
│ │              │    │      │  │      │     │
│ └──────────────┘    └──────┘  └──────┘     │
└─────────────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Column gap | 16px (`space-2`) |
| Field gap (vertical) | 24px (`space-3`) |
| Responsive behavior | Collapses to single column on mobile (<480px) |

**When to use:** Address forms, name fields, date range pickers. Never for unrelated fields.

### Inline Layout

Fields and actions arranged horizontally in a single row. Useful for simple, single-field forms.

```
┌──────────────────────────────────────────────────────┐
│ ┌─────────────────────────────────┐ ┌──────────────┐ │
│ │ Search or enter email...        │ │   Submit     │ │
│ └─────────────────────────────────┘ └──────────────┘ │
└──────────────────────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Gap between input and button | 8px (`space-1`) |
| Input width | Fill (flex: 1) |
| Button width | Hug contents |
| Responsive behavior | Stacks vertically on mobile; button becomes full-width |

**When to use:** Search bars, email subscription, quick filters.

---

## Field Grouping and Sections

### Section Headers

For forms with 5+ fields, group related fields under section headers.

```
┌──────────────────────────────────────┐
│ Personal Information                  │  ← Section title
│ ──────────────────────────────────── │  ← Divider
│                                      │
│ [First Name]                         │
│ ┌──────────────────────────────────┐ │
│ │                                  │ │
│ └──────────────────────────────────┘ │
│                                      │
│ [Last Name]                          │
│ ┌──────────────────────────────────┐ │
│ │                                  │ │
│ └──────────────────────────────────┘ │
│                                      │
│                                      │
│ Project Details                      │  ← Next section
│ ──────────────────────────────────── │
│                                      │
│ [Project Type]                       │
│ ┌──────────────────────────────────┐ │
│ │ Select...                    ▼   │ │
│ └──────────────────────────────────┘ │
└──────────────────────────────────────┘
```

| Element | Spec |
|---|---|
| Section title | Inter SemiBold, 18px (`font-size-lg`), `color-text-primary` |
| Section description (optional) | Inter Regular, 14px (`font-size-sm`), `color-text-secondary` |
| Divider | 1px `color-border-default`, full width |
| Gap between sections | 32px (`space-4`) |
| Gap between section header and first field | 16px (`space-2`) |
| Gap between fields within a section | 24px (`space-3`) |

### Fieldset and Legend

In HTML, use `<fieldset>` and `<legend>` for grouped fields. This provides semantic grouping for screen readers.

```html
<fieldset>
  <legend>Personal Information</legend>
  <!-- fields -->
</fieldset>
```

---

## Validation Strategy

### Validation Timing

| Strategy | Trigger | Best For | Trade-offs |
|---|---|---|---|
| **On blur** (default) | Field loses focus | Most text inputs | Immediate feedback without interrupting typing |
| **On change** | Value changes (with debounce) | Selects, checkboxes, radios, toggles | Instant feedback for discrete choices |
| **On submit** | Form submission | Complex interdependent fields | Batch validation; user sees all errors at once |
| **Real-time** | Each keystroke (debounced 300ms) | Password strength, username availability | Continuous feedback; can be distracting |

### Default Validation Rules

| Field Type | Validation | Error Message Template |
|---|---|---|
| Required text | Non-empty after trim | "[Field name] is required." |
| Email | Valid email pattern | "Please enter a valid email address." |
| URL | Valid URL pattern | "Please enter a valid URL (e.g., https://example.com)." |
| Phone | Valid phone pattern | "Please enter a valid phone number." |
| Min length | `value.length >= min` | "[Field name] must be at least [min] characters." |
| Max length | `value.length <= max` | "[Field name] must be no more than [max] characters." |
| Pattern match | Regex test | "[Field name] format is invalid." |
| Numeric range | `min <= value <= max` | "[Field name] must be between [min] and [max]." |
| File size | `file.size <= maxBytes` | "File must be smaller than [max size]." |
| File type | Extension / MIME check | "Accepted file types: [list]." |

### Validation Visual States

| State | Border Color | Icon | Helper Text Color | Background |
|---|---|---|---|---|
| Default | `color-border-default` | None | `color-text-secondary` | `color-bg-primary` |
| Focus | `color-border-focus` (+ focus ring) | None | `color-text-secondary` | `color-bg-primary` |
| Error | `color-border-error` | Error icon (circle-x) | `color-text-error` | `color-bg-error` (subtle) |
| Success | `color-border-success` | Check icon | `color-text-success` | `color-bg-primary` |

---

## Error Handling and Recovery

### Inline Errors (Per Field)

Each field shows its own error message directly below the input.

```
[Email Address] *
┌──────────────────────────────────┐
│ not-an-email                     │  ← red border
└──────────────────────────────────┘
⚠ Please enter a valid email address.   ← red text, error icon
```

| Element | Spec |
|---|---|
| Error border | 2px `color-border-error` |
| Error icon | 16x16, `color-text-error`, positioned before error text |
| Error text | Inter Regular, 12px, `color-text-error` |
| Transition | Appears with 200ms ease-out fade + 4px slide-up |
| Announcement | `aria-live="polite"` on error container |

### Form-Level Error Summary

For forms validated on submit, show a summary alert at the top of the form.

```
┌──────────────────────────────────────────────────────┐
│ ⚠  Please fix the following errors:                  │
│                                                      │
│  • Email address -- Please enter a valid email.      │
│  • Message -- This field is required.                │
│                                                      │
└──────────────────────────────────────────────────────┘
```

| Element | Spec |
|---|---|
| Container | Alert component, `type=error` |
| Position | Top of form, above first field |
| Links | Each error item is a link that focuses the corresponding field |
| ARIA | `role="alert"` for screen reader announcement |
| Scroll | Page scrolls to error summary if it is out of view |

### Error Recovery Flow

```
1. User submits form with errors
   ↓
2. Error summary appears at top of form
   (page scrolls to summary if needed)
   ↓
3. Each invalid field shows inline error
   ↓
4. Focus moves to first invalid field
   ↓
5. User corrects the field
   ↓
6. On blur: inline error clears if valid
   (error summary item also removes)
   ↓
7. User re-submits
   ↓
8. If all valid: success state
   If more errors: repeat from step 2
```

---

## Multi-Step Forms

### Step Indicator

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│   ● ─────── ● ─────── ○ ─────── ○                   │
│  Step 1    Step 2    Step 3    Step 4                 │
│  Details   Project   Budget    Review                 │
│                                                      │
└──────────────────────────────────────────────────────┘

● = Completed (blue-600 fill)
● = Current (blue-600 fill, focus ring)
○ = Upcoming (neutral-300 stroke)
── = Completed connector (blue-600)
── = Upcoming connector (neutral-300)
```

| Property | Value |
|---|---|
| Step circle size | 32px diameter |
| Connector line | 2px height, stretches between circles |
| Step label | Inter Medium, 14px, below circle |
| Gap between circle and label | 8px |
| Mobile behavior | Show only current step number and total: "Step 2 of 4" |

### Step Navigation

```
┌──────────────────────────────────────────────────────┐
│                  Step Content                         │
│                                                      │
│  [Form fields for current step]                      │
│                                                      │
│                                                      │
├──────────────────────────────────────────────────────┤
│  ← Back                          [Next Step →]       │
│                                                      │
│  Or: [Save as Draft]                                 │
└──────────────────────────────────────────────────────┘
```

| Element | Spec |
|---|---|
| Back button | Ghost button, left-aligned |
| Next button | Primary button, right-aligned |
| Submit button (final step) | Primary button, label changes to "Submit" or "Send" |
| Save draft link | Link style, centered or left-aligned |
| Validation | Validate current step on "Next" before advancing |
| Transition | Smart Animate between steps (300ms, ease in-out) |

### Multi-Step Data Persistence

- Save form data to local state (or session storage) after each step.
- If the user navigates back, pre-fill fields with previously entered data.
- Show a confirmation/review step as the final step.

### Review Step

The final step displays a read-only summary of all entered data:

```
┌──────────────────────────────────────────────────────┐
│ Review Your Information                               │
│                                                      │
│ Personal Details                        [Edit]       │
│ ─────────────────────────────────────────────        │
│ Name:     Flavio Fusuma                              │
│ Email:    flavio@example.com                         │
│                                                      │
│ Project Details                         [Edit]       │
│ ─────────────────────────────────────────────        │
│ Type:     Web Application                            │
│ Budget:   $10,000 - $25,000                          │
│ Timeline: 3 months                                   │
│                                                      │
│              ┌──────────────────┐                    │
│              │  Submit Request   │                    │
│              └──────────────────┘                    │
└──────────────────────────────────────────────────────┘
```

Each section has an "Edit" link that returns the user to the corresponding step.

---

## Accessibility for Forms

### Label Requirements

- Every input **must** have a visible label. Do not rely on placeholder text as the only label.
- Labels are associated with inputs via `for`/`id` attributes in HTML.
- Required fields are indicated with an asterisk (*) and the form includes a legend: "* indicates required field."

### Error Announcement

- Error messages use `aria-live="polite"` so screen readers announce them when they appear.
- Error summary uses `role="alert"` for immediate announcement.
- Each error message is linked to its field via `aria-describedby`.

### Keyboard Navigation

| Key | Behavior |
|---|---|
| `Tab` | Moves focus to next form control |
| `Shift + Tab` | Moves focus to previous form control |
| `Enter` | Submits the form (when focus is on submit button or input) |
| `Space` | Toggles checkboxes, activates buttons |
| `Arrow Up/Down` | Navigates radio groups and select options |
| `Escape` | Closes dropdown menus, cancels modal forms |

### Focus Management

- On form submission error, focus moves to the error summary (or first invalid field if no summary).
- On successful submission, focus moves to the success message.
- In multi-step forms, focus moves to the first field of the new step after navigation.

### Touch Targets

- All form controls have a minimum touch target of 44x44px.
- Checkboxes and radio buttons include the label in the touch target.
- "Padding" extends the clickable area if the visual element is smaller than 44px.

### Field Descriptions

- Use `aria-describedby` to associate helper text and error messages with their inputs.
- Character counters use `aria-live="polite"` to announce updates.

---

## Common Form Templates

### Contact Form

```
Fields:
  1. Name (text, required)
  2. Email (email, required)
  3. Subject (select: General, Project, Support, Other)
  4. Message (textarea, required, max 2000 characters)
  5. Privacy checkbox (required)

Layout: Single column, max-width 480px
Validation: On blur
Submit: "Send Message" primary button, full width
Success: Inline success alert replacing the form
```

### Signup / Registration Form

```
Fields:
  1. Full Name (text, required)
  2. Email (email, required, unique check on blur)
  3. Password (password, required, min 8, strength indicator)
  4. Confirm Password (password, required, must match)
  5. Terms checkbox (required)

Layout: Single column, max-width 400px
Validation: Real-time for password strength, on blur for others
Submit: "Create Account" primary button, full width
Success: Redirect to dashboard or email verification page
Additional: "Already have an account? Log in" link below form
```

### Search Form

```
Fields:
  1. Search query (text, placeholder: "Search projects...")

Layout: Inline (input + button)
Validation: None (empty search shows all results)
Submit: Icon button (search icon) or Enter key
Behavior: Results update on submit; optional: live results on keystroke (debounced 300ms)
```

### Newsletter Subscription

```
Fields:
  1. Email (email, required)

Layout: Inline, max-width 480px
Validation: On submit
Submit: "Subscribe" primary button
Success: Input and button replaced with success message
Error: Inline error below input
```

### Project Inquiry (Multi-Step)

```
Step 1 -- About You:
  1. Name (text, required)
  2. Email (email, required)
  3. Company (text, optional)

Step 2 -- Project Details:
  4. Project type (select: Website, Web App, Mobile App, Other)
  5. Description (textarea, required, max 3000)
  6. Timeline (select: < 1 month, 1-3 months, 3-6 months, 6+ months)

Step 3 -- Budget:
  7. Budget range (radio: <$5K, $5K-$15K, $15K-$50K, $50K+)
  8. Additional notes (textarea, optional)

Step 4 -- Review:
  Summary of all fields with edit links

Layout: Single column, max-width 640px, step indicator at top
Validation: Per-step on "Next"
Submit: "Submit Inquiry" on review step
Success: Confirmation page with summary and expected response time
```
