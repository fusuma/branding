# Alerts

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Alerts are prominent, inline messages that communicate important information to users. They convey status, feedback, or contextual guidance using semantic color coding and optional icons. Alerts remain visible until the user dismisses them or the triggering condition resolves. Use alerts for page-level or section-level messages that require user awareness but not necessarily immediate action.

---

## Anatomy

```
┌───────────────────────────────────────────────────────┐
│  ┌────┐                                    ┌───────┐  │
│  │Icon│  [Title]                           │Dismiss│  │
│  └────┘  [Description text that can span   └───────┘  │
│           multiple lines of content]                   │
│                                                        │
│          ┌──────────────┐  ┌────────────┐              │
│          │ Action Button│  │ Secondary  │              │
│          └──────────────┘  └────────────┘              │
└───────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Outer wrapper with variant background, border, and border-radius |
| Icon | No | Leading icon that reinforces the alert variant semantics |
| Title | No | Bold heading text summarizing the alert (recommended) |
| Description | Yes | Body text providing detail about the alert condition |
| Dismiss button | No | Close icon button to remove the alert from view |
| Action button(s) | No | One or two call-to-action buttons for the user to respond |

---

## Variants

| Variant | Icon | Background | Border | Text Color | Accent Color | Use Case |
|---------|------|-----------|--------|------------|-------------|----------|
| Info | Info circle | `blue-50` #EFF6FF | `blue-200` #BFDBFE | `blue-800` #1E40AF | `blue-600` #2563EB | Neutral information, tips, announcements |
| Success | Check circle | `green-50` #F0FDF4 | `green-200` #BBF7D0 | `green-800` #166534 | `green-600` #16A34A | Completed actions, positive confirmations |
| Warning | Warning triangle | `amber-50` #FFFBEB | `amber-200` #FDE68A | `amber-800` #92400E | `amber-500` #F59E0B | Caution, non-blocking issues, degraded states |
| Error | X circle | `red-50` #FEF2F2 | `red-200` #FECACA | `red-800` #991B1B | `red-600` #DC2626 | Failures, blocking errors, critical issues |

---

## Sub-Variants

| Sub-Variant | Description | Visual Difference |
|-------------|-------------|-------------------|
| Standard | Full container with background fill | Background, left accent border (4px), rounded corners |
| Minimal | Reduced visual weight | No background fill, left accent border only |
| Banner | Full-width, no border-radius | Spans container width, used at top of page or section |

---

## States

### Info Variant States

| State | Background | Border | Text | Accent | Notes |
|-------|-----------|--------|------|--------|-------|
| Default | `blue-50` | `blue-200` | `blue-800` | `blue-600` 4px left border | Resting visible state |
| Hover (dismiss) | `blue-50` | `blue-200` | `blue-800` | Dismiss icon gets `blue-100` bg | Dismiss button hover |
| Focus (dismiss) | `blue-50` | `blue-200` | `blue-800` | 2px focus ring `blue-600` | Keyboard focus on dismiss |
| Dismissing | `blue-50` | `blue-200` | `blue-800` | opacity 0, height 0 | Exit animation 200ms ease-out |

### Error Variant States

| State | Background | Border | Text | Accent | Notes |
|-------|-----------|--------|------|--------|-------|
| Default | `red-50` | `red-200` | `red-800` | `red-600` 4px left border | Resting visible state |
| Hover (dismiss) | `red-50` | `red-200` | `red-800` | Dismiss icon gets `red-100` bg | Dismiss button hover |
| Focus (dismiss) | `red-50` | `red-200` | `red-800` | 2px focus ring `blue-600` | Keyboard focus on dismiss |
| Dismissing | `red-50` | `red-200` | `red-800` | opacity 0, height 0 | Exit animation 200ms ease-out |

---

## Sizing

| Property | Value | Token |
|----------|-------|-------|
| Min height | 48px | -- |
| Padding | 16px | `{space.4}` |
| Border radius | 8px | `{border.radius.lg}` |
| Left accent border | 4px | -- |
| Icon size | 20px | -- |
| Icon-to-content gap | 12px | `{space.3}` |
| Title font size | 14px / semi-bold (600) | `{typography.body.md}` |
| Description font size | 14px / regular (400) | `{typography.body.md}` |
| Title-to-description gap | 4px | `{space.1}` |
| Content-to-actions gap | 12px | `{space.3}` |
| Action button gap | 8px | `{space.2}` |
| Dismiss button size | 32px touch target | -- |
| Dismiss icon size | 16px | -- |
| Max width | 100% of parent container | -- |

---

## Accessibility

- **Role**: Use `role="alert"` for error and warning alerts that need immediate attention (live region). Use `role="status"` for info and success alerts. For non-urgent information, use `role="region"` with `aria-label`.
- **ARIA**: Add `aria-live="assertive"` for errors, `aria-live="polite"` for info and success. Include `aria-atomic="true"` so the entire alert is announced.
- **Dismiss button**: Must have `aria-label="Dismiss alert"` or `aria-label="Close [alert title]"`.
- **Keyboard**:
  - Dismiss button is focusable via `Tab`.
  - `Enter` or `Space` activates dismiss.
  - `Escape` dismisses the alert when focus is within it.
  - After dismissal, focus moves to the next logical element in the document flow.
- **Screen reader**: Announces the alert variant (via `role`), title, and description upon appearance.
- **Color**: Each variant pairs color with a distinct icon so meaning is not conveyed by color alone.
- **Motion**: Dismiss animation respects `prefers-reduced-motion: reduce` by using instant removal.

---

## Design Tokens

```json
{
  "alert": {
    "border-radius": "{border.radius.lg}",
    "border-width": "1px",
    "accent-border-width": "4px",
    "padding": "{space.4}",
    "gap": "{space.3}",
    "font-family": "{typography.font.sans}",
    "title-font-weight": "600",
    "title-font-size": "{typography.body.md.size}",
    "description-font-size": "{typography.body.md.size}",
    "description-font-weight": "400",
    "icon-size": "20px",
    "dismiss-icon-size": "16px",
    "dismiss-target-size": "32px",
    "transition-duration": "200ms",
    "transition-easing": "ease-out",
    "info": {
      "background": "{color.blue.50}",
      "border-color": "{color.blue.200}",
      "accent-color": "{color.blue.600}",
      "icon-color": "{color.blue.600}",
      "title-color": "{color.blue.800}",
      "description-color": "{color.blue.700}"
    },
    "success": {
      "background": "{color.green.50}",
      "border-color": "{color.green.200}",
      "accent-color": "{color.green.600}",
      "icon-color": "{color.green.600}",
      "title-color": "{color.green.800}",
      "description-color": "{color.green.700}"
    },
    "warning": {
      "background": "{color.amber.50}",
      "border-color": "{color.amber.200}",
      "accent-color": "{color.amber.500}",
      "icon-color": "{color.amber.500}",
      "title-color": "{color.amber.800}",
      "description-color": "{color.amber.700}"
    },
    "error": {
      "background": "{color.red.50}",
      "border-color": "{color.red.200}",
      "accent-color": "{color.red.600}",
      "icon-color": "{color.red.600}",
      "title-color": "{color.red.800}",
      "description-color": "{color.red.700}"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use alerts for important, contextual information that relates to the current page or section.
- Include a clear, concise title that summarizes the alert -- users scan titles before reading descriptions.
- Place alerts near the content they relate to, or at the top of the page for global messages.
- Use the dismiss action for informational and success alerts that do not require ongoing visibility.
- Provide an action button when the user can take a concrete step to resolve the alert condition.
- Stack multiple alerts vertically with 8px spacing between them, ordered by severity (error first).

**Don't:**
- Don't use alerts for inline form validation -- use field-level error messages instead.
- Don't use more than three alerts simultaneously on a single page; consider consolidating messages.
- Don't make error alerts dismissible if the underlying issue has not been resolved.
- Don't use the warning variant for purely informational messages -- match the variant to the actual severity.
- Don't place action buttons in alerts that can be dismissed, as the action would be lost.
- Don't auto-dismiss error alerts -- use the Toast component for transient success feedback instead.

---

## Code Example

### HTML

```html
<!-- Info alert with icon, title, description, and dismiss -->
<div class="ff-alert ff-alert--info" role="status" aria-live="polite" aria-atomic="true">
  <div class="ff-alert__accent"></div>
  <svg class="ff-alert__icon" aria-hidden="true"><!-- info icon --></svg>
  <div class="ff-alert__content">
    <p class="ff-alert__title">New feature available</p>
    <p class="ff-alert__description">
      You can now export reports in PDF format. Check the export menu for the new option.
    </p>
  </div>
  <button class="ff-alert__dismiss" aria-label="Dismiss alert">
    <svg aria-hidden="true"><!-- close icon --></svg>
  </button>
</div>

<!-- Error alert with action button -->
<div class="ff-alert ff-alert--error" role="alert" aria-live="assertive" aria-atomic="true">
  <div class="ff-alert__accent"></div>
  <svg class="ff-alert__icon" aria-hidden="true"><!-- error icon --></svg>
  <div class="ff-alert__content">
    <p class="ff-alert__title">Payment failed</p>
    <p class="ff-alert__description">
      Your payment method was declined. Please update your billing information to continue.
    </p>
    <div class="ff-alert__actions">
      <button class="ff-button ff-button--sm ff-button--error">Update billing</button>
      <button class="ff-button ff-button--sm ff-button--ghost">Contact support</button>
    </div>
  </div>
</div>

<!-- Minimal success alert -->
<div class="ff-alert ff-alert--success ff-alert--minimal" role="status" aria-live="polite">
  <div class="ff-alert__accent"></div>
  <svg class="ff-alert__icon" aria-hidden="true"><!-- check icon --></svg>
  <div class="ff-alert__content">
    <p class="ff-alert__description">Your changes have been saved successfully.</p>
  </div>
  <button class="ff-alert__dismiss" aria-label="Dismiss alert">
    <svg aria-hidden="true"><!-- close icon --></svg>
  </button>
</div>
```

### JSX

```jsx
import { Alert } from '@flaviofusuma/ui';

{/* Info alert with all features */}
<Alert
  variant="info"
  title="New feature available"
  icon={<InfoIcon />}
  dismissible
  onDismiss={() => setShowAlert(false)}
>
  You can now export reports in PDF format. Check the export menu for the new option.
</Alert>

{/* Error alert with actions */}
<Alert
  variant="error"
  title="Payment failed"
  icon={<ErrorIcon />}
  actions={[
    { label: 'Update billing', onClick: handleBilling, variant: 'error' },
    { label: 'Contact support', onClick: handleSupport, variant: 'ghost' },
  ]}
>
  Your payment method was declined. Please update your billing information.
</Alert>

{/* Success alert -- minimal */}
<Alert variant="success" subVariant="minimal" dismissible>
  Your changes have been saved successfully.
</Alert>

{/* Warning alert -- banner */}
<Alert variant="warning" subVariant="banner" icon={<WarningIcon />} title="Scheduled maintenance">
  The platform will be unavailable on Saturday from 2:00 AM to 4:00 AM UTC.
</Alert>
```

---

## Related Components

- **[Toast](/02-design-system/05-components/toast.md)** -- For transient, non-blocking feedback; use toasts for brief confirmations that auto-dismiss.
- **[Tags](/02-design-system/05-components/tags.md)** -- For inline status labels; use tags when the status is metadata on a content item rather than a standalone message.
- **[Modal](/02-design-system/05-components/modal.md)** -- For critical, blocking messages that require user acknowledgment before proceeding.
- **[Progress](/02-design-system/05-components/progress.md)** -- Often paired with alerts to show ongoing processes or upload states.
