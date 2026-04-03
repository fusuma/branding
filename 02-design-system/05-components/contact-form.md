# Contact Form

> The Contact Form component provides a structured inquiry form for portfolio visitors to send messages, featuring validated input fields, accessible error handling, and clear success/error feedback.

---

## Overview

The Contact Form is a portfolio-specific component that allows visitors to submit inquiries, collaboration requests, or general messages. It includes fields for name, email, subject (select dropdown), and message (textarea), with comprehensive client-side validation, accessible error announcements, and clear submission feedback. The form manages focus throughout the user journey -- from initial entry to validation errors to submission confirmation.

---

## Anatomy

```
┌──────────────────────────────────────────────────────────────┐
│  Contact Form                                                │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Name *                                                 │  │
│  │ ┌──────────────────────────────────────────────────┐   │  │
│  │ │ Your full name                                   │   │  │
│  │ └──────────────────────────────────────────────────┘   │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Email *                                                │  │
│  │ ┌──────────────────────────────────────────────────┐   │  │
│  │ │ your@email.com                                   │   │  │
│  │ └──────────────────────────────────────────────────┘   │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Subject *                                              │  │
│  │ ┌──────────────────────────────────────────────────┐   │  │
│  │ │ Select a subject                              [v]│   │  │
│  │ └──────────────────────────────────────────────────┘   │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Message *                                              │  │
│  │ ┌──────────────────────────────────────────────────┐   │  │
│  │ │                                                  │   │  │
│  │ │ Tell me about your project...                    │   │  │
│  │ │                                                  │   │  │
│  │ │                                                  │   │  │
│  │ └──────────────────────────────────────────────────┘   │  │
│  │                                      120 / 1000 chars  │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │              [Send Message]                            │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
└──────────────────────────────────────────────────────────────┘

Error state:
┌────────────────────────────────────────────────────────────┐
│ Email *                                                    │
│ ┌──────────────────────────────────────────────────────┐   │
│ │ not-an-email                                         │   │ ← red border
│ └──────────────────────────────────────────────────────┘   │
│ ⚠ Please enter a valid email address                      │ ← error text
└────────────────────────────────────────────────────────────┘

Success state:
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│                    ┌────┐                                    │
│                    │ ✓  │                                    │
│                    └────┘                                    │
│                                                              │
│              Message Sent Successfully!                      │
│     Thank you for reaching out. I'll get back to you        │
│     within 1-2 business days.                                │
│                                                              │
│              [Send Another Message]                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘

Error (submission) state:
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ ⚠ Something went wrong. Please try again or email     │  │
│  │   me directly at hello@flaviofusuma.com               │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
│  [form fields preserved]                                     │
│                                                              │
│              [Try Again]                                     │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Form container | Yes | Wrapper `<form>` element |
| Name field | Yes | Text input for the visitor's full name |
| Email field | Yes | Email input for the visitor's email address |
| Subject field | Yes | Select dropdown for message category |
| Message field | Yes | Textarea for the message body |
| Field label | Yes | Visible `<label>` for each field |
| Required indicator | Yes | Asterisk (*) on required fields |
| Helper text | No | Optional hint text below a field |
| Error message | No | Validation error text below a field |
| Character count | No | Current/max character count for textarea |
| Submit button | Yes | Primary action button to send the form |
| Success state | Yes | Confirmation message after successful submission |
| Error banner | Yes | Error message for submission failures |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Standard | Full form with all fields visible | Dedicated contact page |
| Compact | Side-by-side name + email, reduced spacing | Inline sections, sidebar |
| With honeypot | Hidden field for spam prevention | Production forms |
| Minimal | Name, email, and message only (no subject) | Simplified contact |

---

## Fields

### Name Field

| Property | Value |
|----------|-------|
| Type | `text` |
| Required | Yes |
| Placeholder | "Your full name" |
| Min length | 2 characters |
| Max length | 100 characters |
| Autocomplete | `name` |
| Validation | Non-empty, min 2 chars |

### Email Field

| Property | Value |
|----------|-------|
| Type | `email` |
| Required | Yes |
| Placeholder | "your@email.com" |
| Max length | 254 characters |
| Autocomplete | `email` |
| Validation | Non-empty, valid email format |

### Subject Field

| Property | Value |
|----------|-------|
| Type | `<select>` |
| Required | Yes |
| Default | "Select a subject" (disabled option) |
| Options | General Inquiry, Project Collaboration, Freelance Opportunity, Speaking / Event, Feedback, Other |
| Validation | Must select a non-default option |

### Message Field

| Property | Value |
|----------|-------|
| Type | `<textarea>` |
| Required | Yes |
| Placeholder | "Tell me about your project or inquiry..." |
| Min length | 10 characters |
| Max length | 1000 characters |
| Rows | 5 (default), resizable vertically |
| Validation | Non-empty, min 10 chars |

---

## States

### Field States

| State | Border | Background | Label | Shadow | Notes |
|-------|--------|-----------|-------|--------|-------|
| Default | `neutral-300` | `white` | `neutral-700` | none | Empty, unfocused |
| Focus | `blue-600` | `white` | `blue-600` | `ring-2 blue-100` | Active input |
| Filled | `neutral-300` | `white` | `neutral-700` | none | Has value, unfocused |
| Error | `red-500` | `red-50` | `red-600` | none | Validation failed |
| Error + Focus | `red-500` | `white` | `red-600` | `ring-2 red-100` | Correcting error |
| Disabled | `neutral-200` | `neutral-50` | `neutral-400` | none | Non-interactive |

### Form States

| State | Appearance | Behavior |
|-------|-----------|----------|
| Idle | All fields empty, submit button default | Awaiting user input |
| Filling | Fields being completed | Real-time or on-blur validation |
| Validating | Inline error messages appear | Focus moves to first error on submit attempt |
| Submitting | Submit button in loading state, fields disabled | Async form submission |
| Success | Form replaced with success message | Focus moves to success heading |
| Error (submission) | Error banner above form, fields preserved | Focus moves to error banner |

---

## Sizing

### Field Sizing

| Size | Input Height | Font Size | Label Font Size | Padding (y / x) | Border Radius |
|------|-------------|-----------|----------------|-----------------|---------------|
| sm | 36px | 14px | 12px | 8px / 12px | 6px |
| md | 44px | 16px | 14px | 10px / 16px | 6px |
| lg | 52px | 16px | 14px | 14px / 16px | 8px |

### Textarea Sizing

| Property | Value |
|----------|-------|
| Min height | 120px (5 rows) |
| Max height | 320px (resizable) |
| Resize | Vertical only |

### Form Layout

| Property | Desktop | Mobile |
|----------|---------|--------|
| Max width | 560px | 100% |
| Field gap | 24px | 20px |
| Label to input gap | 6px | 6px |
| Error text margin top | 4px | 4px |
| Submit button width | Auto (min 200px) | 100% |
| Submit button margin top | 8px | 8px |

### Compact Layout

| Property | Value |
|----------|-------|
| Name + Email | Side-by-side, 50/50 split |
| Gap between side-by-side fields | 16px |
| Breakpoint to stack | < 480px |

---

## Validation

### Validation Strategy

| Type | Trigger | Behavior |
|------|---------|----------|
| On blur | User leaves a field | Validate that field, show error if invalid |
| On submit | User clicks submit | Validate all fields, focus first error |
| On change (after error) | User types in an errored field | Clear error when field becomes valid |

### Error Messages

| Field | Condition | Message |
|-------|-----------|---------|
| Name | Empty | "Please enter your name" |
| Name | Too short | "Name must be at least 2 characters" |
| Email | Empty | "Please enter your email address" |
| Email | Invalid format | "Please enter a valid email address" |
| Subject | Not selected | "Please select a subject" |
| Message | Empty | "Please enter a message" |
| Message | Too short | "Message must be at least 10 characters" |
| Message | Too long | "Message must not exceed 1000 characters" |

---

## Accessibility

- **Form landmark**: Wrap in `<form>` with `aria-label="Contact form"` or reference a visible heading with `aria-labelledby`.
- **Labels**: Every field must have a visible `<label>` element associated via `for`/`id` attributes. Do not rely on placeholder text as the label.
- **Required fields**: Mark required fields with `aria-required="true"` and a visible asterisk. Include a note at the top: "Fields marked with * are required."
- **Error announcements**: Use `aria-describedby` on each input, pointing to its error message element. Error messages should have `role="alert"` or be inside an `aria-live="assertive"` region so they are announced immediately when they appear.
- **Error summary**: On submit with errors, optionally show an error summary at the top of the form listing all errors as links to the fields. Move focus to this summary.
- **Focus management**:
  - On submit with validation errors: focus moves to the first invalid field.
  - On successful submission: focus moves to the success message heading.
  - On submission error: focus moves to the error banner.
- **Keyboard**:
  - Tab navigates between fields in logical order.
  - Enter submits the form (except when in the textarea where Enter creates a new line).
  - Escape in the subject dropdown closes the dropdown.
- **Autocomplete**: Include appropriate `autocomplete` attributes (`name`, `email`) to assist browser autofill.
- **Color**: Error states do not rely on color alone; they include an error icon and text message alongside the red border.
- **Character count**: Announce character count updates to screen readers periodically (not on every keystroke) using `aria-live="polite"` with debouncing, or provide a static description like "Maximum 1000 characters".

---

## Design Tokens

```json
{
  "contact-form": {
    "max-width": "560px",
    "field-gap": "{space.6}",
    "label": {
      "color": "{color.neutral.700}",
      "color-focus": "{color.primary.600}",
      "color-error": "{color.red.600}",
      "font-size": "{typography.body.sm.size}",
      "font-weight": "{typography.weight.medium}",
      "margin-bottom": "6px"
    },
    "input": {
      "background": "{color.white}",
      "background-error": "{color.red.50}",
      "background-disabled": "{color.neutral.50}",
      "border-color": "{color.neutral.300}",
      "border-color-focus": "{color.primary.600}",
      "border-color-error": "{color.red.500}",
      "border-color-disabled": "{color.neutral.200}",
      "border-width": "1px",
      "border-radius": "{border.radius.md}",
      "text-color": "{color.neutral.900}",
      "text-color-placeholder": "{color.neutral.400}",
      "text-color-disabled": "{color.neutral.400}",
      "font-family": "{typography.font.sans}",
      "font-size": "{typography.body.md.size}",
      "focus-ring-color": "{color.blue.100}",
      "focus-ring-width": "3px",
      "transition": "border-color 150ms ease, box-shadow 150ms ease"
    },
    "textarea": {
      "min-height": "120px",
      "max-height": "320px",
      "resize": "vertical"
    },
    "error": {
      "color": "{color.red.600}",
      "font-size": "{typography.caption.size}",
      "margin-top": "4px",
      "icon-size": "14px"
    },
    "helper": {
      "color": "{color.neutral.500}",
      "font-size": "{typography.caption.size}",
      "margin-top": "4px"
    },
    "char-count": {
      "color": "{color.neutral.400}",
      "color-warning": "{color.amber.600}",
      "color-limit": "{color.red.600}",
      "font-size": "12px"
    },
    "submit": {
      "min-width": "200px"
    },
    "success": {
      "icon-color": "{color.green.500}",
      "icon-size": "48px",
      "heading-color": "{color.neutral.900}",
      "heading-font-size": "{typography.body.lg.size}",
      "text-color": "{color.neutral.600}",
      "text-font-size": "{typography.body.md.size}"
    },
    "error-banner": {
      "background": "{color.red.50}",
      "border-color": "{color.red.200}",
      "text-color": "{color.red.700}",
      "border-radius": "{border.radius.md}",
      "padding": "{space.4}",
      "margin-bottom": "{space.4}"
    },
    "sizing": {
      "sm": { "input-height": "36px", "padding": "8px 12px", "font-size": "14px" },
      "md": { "input-height": "44px", "padding": "10px 16px", "font-size": "16px" },
      "lg": { "input-height": "52px", "padding": "14px 16px", "font-size": "16px" }
    },
    "required-indicator": {
      "color": "{color.red.500}",
      "margin-left": "2px"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Place the contact form on a dedicated contact page or as a prominent section on the portfolio homepage.
- Include a visible heading (e.g., "Get in Touch") above the form for context.
- Provide real-time validation feedback on blur, not on every keystroke.
- Preserve form data on submission errors so users do not have to re-enter everything.
- Include an alternative contact method (email link) in case the form fails.
- Use the honeypot field for spam prevention in production.
- Show a clear success message with expected response time after submission.
- Use `autocomplete` attributes to speed up form completion.

**Don't:**
- Add unnecessary fields (phone, company) that create friction; keep the form minimal.
- Use placeholder text as a substitute for labels; always provide visible labels.
- Validate on every keystroke (except after an error has been shown); this is distracting.
- Clear the form on validation error; preserve the user's input.
- Show generic error messages like "Invalid input"; be specific about what is wrong.
- Require users to solve a CAPTCHA without providing an accessible alternative.
- Submit the form without client-side validation; always validate before sending.
- Disable the submit button before the user has attempted to fill in fields; keep it enabled and validate on submit.

---

## Code Example

### HTML

```html
<section class="ff-contact-section" aria-labelledby="contact-heading">
  <h2 id="contact-heading">Get in Touch</h2>
  <p class="ff-contact-section__intro">
    Have a project in mind or want to collaborate? Send me a message
    and I'll get back to you within 1-2 business days.
  </p>

  <form class="ff-contact-form ff-contact-form--md" aria-label="Contact form"
        novalidate>
    <p class="ff-contact-form__required-note">
      Fields marked with <span aria-hidden="true">*</span>
      <span class="ff-sr-only">asterisk</span> are required.
    </p>

    <!-- Name field -->
    <div class="ff-field">
      <label for="contact-name" class="ff-field__label">
        Name <span class="ff-field__required" aria-hidden="true">*</span>
      </label>
      <input type="text" id="contact-name" name="name"
             class="ff-input ff-input--md"
             placeholder="Your full name"
             autocomplete="name"
             aria-required="true"
             aria-describedby="contact-name-error" />
      <p id="contact-name-error" class="ff-field__error" role="alert" hidden>
        Please enter your name
      </p>
    </div>

    <!-- Email field -->
    <div class="ff-field">
      <label for="contact-email" class="ff-field__label">
        Email <span class="ff-field__required" aria-hidden="true">*</span>
      </label>
      <input type="email" id="contact-email" name="email"
             class="ff-input ff-input--md"
             placeholder="your@email.com"
             autocomplete="email"
             aria-required="true"
             aria-describedby="contact-email-error" />
      <p id="contact-email-error" class="ff-field__error" role="alert" hidden>
        Please enter a valid email address
      </p>
    </div>

    <!-- Subject field -->
    <div class="ff-field">
      <label for="contact-subject" class="ff-field__label">
        Subject <span class="ff-field__required" aria-hidden="true">*</span>
      </label>
      <select id="contact-subject" name="subject"
              class="ff-select ff-select--md"
              aria-required="true"
              aria-describedby="contact-subject-error">
        <option value="" disabled selected>Select a subject</option>
        <option value="general">General Inquiry</option>
        <option value="collaboration">Project Collaboration</option>
        <option value="freelance">Freelance Opportunity</option>
        <option value="speaking">Speaking / Event</option>
        <option value="feedback">Feedback</option>
        <option value="other">Other</option>
      </select>
      <p id="contact-subject-error" class="ff-field__error" role="alert" hidden>
        Please select a subject
      </p>
    </div>

    <!-- Message field -->
    <div class="ff-field">
      <label for="contact-message" class="ff-field__label">
        Message <span class="ff-field__required" aria-hidden="true">*</span>
      </label>
      <textarea id="contact-message" name="message"
                class="ff-textarea ff-textarea--md"
                placeholder="Tell me about your project or inquiry..."
                rows="5"
                maxlength="1000"
                aria-required="true"
                aria-describedby="contact-message-error contact-message-count"></textarea>
      <div class="ff-field__meta">
        <p id="contact-message-error" class="ff-field__error" role="alert" hidden>
          Please enter a message (at least 10 characters)
        </p>
        <span id="contact-message-count" class="ff-field__char-count"
              aria-live="polite">0 / 1000</span>
      </div>
    </div>

    <!-- Honeypot (spam prevention) -->
    <div class="ff-field ff-field--honeypot" aria-hidden="true" tabindex="-1">
      <label for="contact-website">Website</label>
      <input type="text" id="contact-website" name="website" tabindex="-1"
             autocomplete="off" />
    </div>

    <!-- Submit -->
    <button type="submit" class="ff-btn ff-btn--primary ff-btn--lg ff-contact-form__submit">
      Send Message
    </button>
  </form>

  <!-- Success state (hidden by default, shown after submission) -->
  <div class="ff-contact-success" hidden role="status">
    <div class="ff-contact-success__icon" aria-hidden="true">
      <svg><!-- checkmark icon --></svg>
    </div>
    <h3 class="ff-contact-success__heading" tabindex="-1">Message Sent Successfully!</h3>
    <p class="ff-contact-success__text">
      Thank you for reaching out. I'll get back to you within 1-2 business days.
    </p>
    <button type="button" class="ff-btn ff-btn--outline ff-btn--md">
      Send Another Message
    </button>
  </div>
</section>
```

### JSX

```jsx
import { ContactForm, Field, Input, Select, Textarea, Button } from '@flaviofusuma/ui';

{/* Using the high-level component */}
<ContactForm
  heading="Get in Touch"
  intro="Have a project in mind? Send me a message."
  size="md"
  subjects={[
    { value: "general", label: "General Inquiry" },
    { value: "collaboration", label: "Project Collaboration" },
    { value: "freelance", label: "Freelance Opportunity" },
    { value: "speaking", label: "Speaking / Event" },
    { value: "feedback", label: "Feedback" },
    { value: "other", label: "Other" },
  ]}
  onSubmit={handleSubmit}
  successMessage={{
    heading: "Message Sent Successfully!",
    text: "Thank you for reaching out. I'll get back to you within 1-2 business days.",
  }}
  fallbackEmail="hello@flaviofusuma.com"
/>

{/* Using individual field components for custom layout */}
<form onSubmit={handleSubmit} noValidate aria-label="Contact form">
  <div className="ff-contact-form__row">
    <Field label="Name" required error={errors.name}>
      <Input
        name="name"
        placeholder="Your full name"
        autoComplete="name"
        value={values.name}
        onChange={handleChange}
        onBlur={handleBlur}
      />
    </Field>
    <Field label="Email" required error={errors.email}>
      <Input
        type="email"
        name="email"
        placeholder="your@email.com"
        autoComplete="email"
        value={values.email}
        onChange={handleChange}
        onBlur={handleBlur}
      />
    </Field>
  </div>

  <Field label="Subject" required error={errors.subject}>
    <Select
      name="subject"
      placeholder="Select a subject"
      options={subjectOptions}
      value={values.subject}
      onChange={handleChange}
      onBlur={handleBlur}
    />
  </Field>

  <Field label="Message" required error={errors.message}
         charCount={{ current: values.message.length, max: 1000 }}>
    <Textarea
      name="message"
      placeholder="Tell me about your project or inquiry..."
      rows={5}
      maxLength={1000}
      value={values.message}
      onChange={handleChange}
      onBlur={handleBlur}
    />
  </Field>

  <Button type="submit" variant="primary" size="lg" loading={isSubmitting}
          fullWidth={isMobile}>
    Send Message
  </Button>
</form>
```

---

## Related Components

- [Buttons](/02-design-system/05-components/buttons.md) -- Submit button follows button component specifications.
- [Alerts](/02-design-system/05-components/alerts.md) -- Error banners and success messages may use the alert component.
- [Section Header](/02-design-system/05-components/section-header.md) -- Introduces the contact section on the page.
- [Footer](/02-design-system/05-components/footer.md) -- The footer may contain a simplified contact form or link to the contact page.
- [Skeleton](/02-design-system/05-components/skeleton.md) -- Placeholder while the form or submission endpoint loads.
