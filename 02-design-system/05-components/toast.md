# Toast

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Toasts are transient, non-blocking notification messages that appear temporarily to provide feedback about an action or system event. They float above the interface in a fixed position and auto-dismiss after a set duration. Use toasts for lightweight confirmations, background process updates, and non-critical alerts that do not require user action.

---

## Anatomy

```
┌───────────────────────────────────────────────────────┐
│  ┌────┐                                    ┌───────┐  │
│  │Icon│  [Title]                           │Dismiss│  │
│  └────┘  [Description text]                └───────┘  │
│                                                        │
│          ┌──────────────┐                              │
│          │ Action Button│                              │
│          └──────────────┘                              │
│  ┌────────────────────────────────────────────────┐    │
│  │ Progress Bar                                   │    │
│  └────────────────────────────────────────────────┘    │
└───────────────────────────────────────────────────────┘

Stacked toasts:
┌─────────────────────────┐
│  Toast 3 (newest)       │
└─────────────────────────┘
┌─────────────────────────┐
│  Toast 2                │
└─────────────────────────┘
┌─────────────────────────┐
│  Toast 1 (oldest)       │
└─────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Outer wrapper with background, border, shadow, and border-radius |
| Icon | No | Leading icon reinforcing the toast variant semantics |
| Title | No | Bold heading text summarizing the notification |
| Description | Yes | Body text with the notification message |
| Dismiss button | No | Close icon button to manually remove the toast |
| Action button | No | Optional CTA for the user to respond (e.g., "Undo") |
| Progress bar | No | Visual countdown indicator showing time until auto-dismiss |

---

## Variants

| Variant | Icon | Background | Border | Text Color | Accent Color | Use Case |
|---------|------|-----------|--------|------------|-------------|----------|
| Info | Info circle | `neutral-0` #FFFFFF | `neutral-200` #E2E8F0 | `neutral-800` #1E293B | `blue-600` #2563EB | General confirmations, neutral updates |
| Success | Check circle | `neutral-0` #FFFFFF | `neutral-200` #E2E8F0 | `neutral-800` #1E293B | `green-600` #16A34A | Completed actions, saved states |
| Warning | Warning triangle | `neutral-0` #FFFFFF | `neutral-200` #E2E8F0 | `neutral-800` #1E293B | `amber-500` #F59E0B | Non-critical caution, degraded states |
| Error | X circle | `neutral-0` #FFFFFF | `neutral-200` #E2E8F0 | `neutral-800` #1E293B | `red-600` #DC2626 | Failed actions, recoverable errors |

---

## Position Options

| Position | CSS Value | Use Case |
|----------|-----------|----------|
| Top-right | `top: 16px; right: 16px` | Default; standard for LTR interfaces |
| Top-center | `top: 16px; left: 50%; transform: translateX(-50%)` | Centered emphasis, narrow viewports |
| Top-left | `top: 16px; left: 16px` | RTL interfaces, secondary position |
| Bottom-right | `bottom: 16px; right: 16px` | Actions near bottom of screen |
| Bottom-center | `bottom: 16px; left: 50%; transform: translateX(-50%)` | Mobile-first layouts |
| Bottom-left | `bottom: 16px; left: 16px` | Less common, specific layouts |

---

## Stacking Behavior

| Property | Value | Notes |
|----------|-------|-------|
| Max visible toasts | 5 | Older toasts are removed when limit is exceeded |
| Stack direction | Newest on top (top positions) or newest on bottom (bottom positions) | Follows gravity logic |
| Stack gap | 8px (`{space.2}`) | Spacing between stacked toasts |
| Enter animation | Slide in + fade (300ms ease-out) | From the edge nearest to the position |
| Exit animation | Fade out + collapse (200ms ease-in) | Height collapses to close gap smoothly |
| Queue behavior | FIFO | First in, first out for auto-dismiss |

---

## Auto-Dismiss Timing

| Variant | Default Duration | Pausable | Notes |
|---------|-----------------|----------|-------|
| Info | 5000ms | Yes | Pauses on hover and focus |
| Success | 5000ms | Yes | Pauses on hover and focus |
| Warning | 8000ms | Yes | Longer due to higher importance |
| Error | 10000ms | Yes | Longest; can be set to persistent |

---

## States

### Info Variant States

| State | Background | Border | Shadow | Progress Bar | Notes |
|-------|-----------|--------|--------|-------------|-------|
| Default | `neutral-0` | `neutral-200` | `lg` | `blue-600` animating | Visible and counting down |
| Hover | `neutral-0` | `neutral-200` | `xl` | `blue-600` paused | Timer pauses, slight shadow lift |
| Focus-within | `neutral-0` | `blue-600` | `lg` | `blue-600` paused | Timer pauses on keyboard focus |
| Dismissing | `neutral-0` | `neutral-200` | `lg` | -- | Fade out + collapse 200ms |

### Error Variant States

| State | Background | Border | Shadow | Progress Bar | Notes |
|-------|-----------|--------|--------|-------------|-------|
| Default | `neutral-0` | `neutral-200` | `lg` | `red-600` animating | Visible and counting down |
| Hover | `neutral-0` | `neutral-200` | `xl` | `red-600` paused | Timer pauses |
| Focus-within | `neutral-0` | `red-600` | `lg` | `red-600` paused | Keyboard focus |
| Dismissing | `neutral-0` | `neutral-200` | `lg` | -- | Fade out + collapse 200ms |

### Dismiss Button States

| State | Icon Color | Background | Notes |
|-------|-----------|-----------|-------|
| Default | `neutral-400` | `transparent` | Resting |
| Hover | `neutral-600` | `neutral-100` | Circular hover area |
| Active | `neutral-700` | `neutral-200` | Mouse down |
| Focus | `neutral-500` | `transparent` | 2px focus ring `blue-600` |

---

## Sizing

| Property | Value | Token |
|----------|-------|-------|
| Width | 360px (min 280px, max 420px) | -- |
| Min height | 48px | -- |
| Padding | 16px | `{space.4}` |
| Border radius | 8px | `{border.radius.lg}` |
| Left accent border | 4px | -- |
| Icon size | 20px | -- |
| Icon-to-content gap | 12px | `{space.3}` |
| Title font size | 14px / semi-bold (600) | `{typography.body.md}` |
| Description font size | 14px / regular (400) | `{typography.body.md}` |
| Title-to-description gap | 4px | `{space.1}` |
| Dismiss button size | 32px touch target | -- |
| Dismiss icon size | 16px | -- |
| Progress bar height | 3px | -- |
| Shadow | `0 4px 12px rgba(0,0,0,0.15)` | `{shadow.lg}` |
| Viewport offset | 16px | `{space.4}` |

---

## Accessibility

- **Role**: Use `role="status"` with `aria-live="polite"` for info and success toasts. Use `role="alert"` with `aria-live="assertive"` for error toasts. Warning toasts use `aria-live="polite"`.
- **ARIA**: Include `aria-atomic="true"` so the entire toast is announced as a unit. Add `aria-label` to the toast region container (e.g., "Notifications").
- **Dismiss button**: Must have `aria-label="Dismiss notification"` or `aria-label="Close [toast title]"`.
- **Keyboard**:
  - `Tab` moves focus into the toast (dismiss and action buttons are focusable).
  - `Enter` or `Space` activates dismiss or action button.
  - `Escape` dismisses the currently focused toast.
  - Auto-dismiss timer pauses when any element within the toast has focus.
- **Screen reader**: Announces toast content when it appears. Does not re-announce on dismiss.
- **Color**: Each variant uses an icon and accent color so meaning is not conveyed by color alone.
- **Motion**: Enter and exit animations respect `prefers-reduced-motion: reduce` by switching to instant show/hide. Progress bar animation also stops.
- **Pause on hover**: Timer pauses on `mouseenter` and resumes on `mouseleave` to give users time to read.

---

## Design Tokens

```json
{
  "toast": {
    "width": "360px",
    "min-width": "280px",
    "max-width": "420px",
    "border-radius": "{border.radius.lg}",
    "border-width": "1px",
    "accent-border-width": "4px",
    "padding": "{space.4}",
    "gap": "{space.3}",
    "stack-gap": "{space.2}",
    "viewport-offset": "{space.4}",
    "shadow": "{shadow.lg}",
    "font-family": "{typography.font.sans}",
    "title-font-weight": "600",
    "title-font-size": "{typography.body.md.size}",
    "description-font-size": "{typography.body.md.size}",
    "description-font-weight": "400",
    "icon-size": "20px",
    "dismiss-icon-size": "16px",
    "dismiss-target-size": "32px",
    "progress-bar-height": "3px",
    "enter-duration": "300ms",
    "enter-easing": "ease-out",
    "exit-duration": "200ms",
    "exit-easing": "ease-in",
    "background": "{color.neutral.0}",
    "border-color": "{color.neutral.200}",
    "title-color": "{color.neutral.800}",
    "description-color": "{color.neutral.600}",
    "info": {
      "accent-color": "{color.blue.600}",
      "icon-color": "{color.blue.600}",
      "progress-color": "{color.blue.600}",
      "duration": "5000ms"
    },
    "success": {
      "accent-color": "{color.green.600}",
      "icon-color": "{color.green.600}",
      "progress-color": "{color.green.600}",
      "duration": "5000ms"
    },
    "warning": {
      "accent-color": "{color.amber.500}",
      "icon-color": "{color.amber.500}",
      "progress-color": "{color.amber.500}",
      "duration": "8000ms"
    },
    "error": {
      "accent-color": "{color.red.600}",
      "icon-color": "{color.red.600}",
      "progress-color": "{color.red.600}",
      "duration": "10000ms"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use toasts for transient feedback that does not require user action (e.g., "Item saved", "Email sent").
- Keep toast messages short -- one sentence maximum for the description.
- Include an "Undo" action button for reversible operations (e.g., deleting an item).
- Position toasts consistently throughout the application; top-right is the recommended default.
- Pause the auto-dismiss timer on hover and keyboard focus to give users time to read.
- Use the progress bar to set user expectations about when the toast will disappear.

**Don't:**
- Don't use toasts for critical errors that require user action -- use an inline Alert or Modal instead.
- Don't stack more than five toasts simultaneously; consolidate or queue messages.
- Don't use toasts for form validation feedback -- use field-level errors and page-level alerts.
- Don't auto-dismiss error toasts with durations under 8 seconds; users need time to read error details.
- Don't place interactive content (links, multi-step forms) inside toasts; keep actions to a single button.
- Don't trigger toasts on page load for non-critical information; use an Alert component for persistent messages.

---

## Code Example

### HTML

```html
<!-- Toast container (placed once in the document) -->
<div class="ff-toast-region ff-toast-region--top-right" role="region" aria-label="Notifications">

  <!-- Success toast with progress bar -->
  <div class="ff-toast ff-toast--success" role="status" aria-live="polite" aria-atomic="true">
    <div class="ff-toast__accent"></div>
    <svg class="ff-toast__icon" aria-hidden="true"><!-- check icon --></svg>
    <div class="ff-toast__content">
      <p class="ff-toast__title">Changes saved</p>
      <p class="ff-toast__description">Your profile has been updated successfully.</p>
    </div>
    <button class="ff-toast__dismiss" aria-label="Dismiss notification">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
    <div class="ff-toast__progress" aria-hidden="true">
      <div class="ff-toast__progress-bar"></div>
    </div>
  </div>

  <!-- Error toast with action -->
  <div class="ff-toast ff-toast--error" role="alert" aria-live="assertive" aria-atomic="true">
    <div class="ff-toast__accent"></div>
    <svg class="ff-toast__icon" aria-hidden="true"><!-- error icon --></svg>
    <div class="ff-toast__content">
      <p class="ff-toast__title">Upload failed</p>
      <p class="ff-toast__description">The file could not be uploaded. Please try again.</p>
      <div class="ff-toast__actions">
        <button class="ff-btn ff-btn--sm ff-btn--ghost">Retry</button>
      </div>
    </div>
    <button class="ff-toast__dismiss" aria-label="Dismiss notification">
      <svg aria-hidden="true"><!-- close icon --></svg>
    </button>
  </div>

</div>
```

### JSX

```jsx
import { Toast, ToastProvider, useToast } from '@flaviofusuma/ui';

// Wrap app in provider
<ToastProvider position="top-right" maxVisible={5}>
  <App />
</ToastProvider>

// Trigger toasts from anywhere
function SaveButton() {
  const { addToast } = useToast();

  const handleSave = async () => {
    try {
      await saveData();
      addToast({
        variant: 'success',
        title: 'Changes saved',
        description: 'Your profile has been updated successfully.',
        duration: 5000,
        showProgress: true,
      });
    } catch (error) {
      addToast({
        variant: 'error',
        title: 'Save failed',
        description: 'Could not save your changes. Please try again.',
        duration: 10000,
        action: { label: 'Retry', onClick: handleSave },
      });
    }
  };

  return <Button onClick={handleSave}>Save</Button>;
}

// Toast with undo action
addToast({
  variant: 'info',
  description: 'Item moved to trash.',
  action: { label: 'Undo', onClick: handleUndo },
  duration: 8000,
});
```

---

## Related Components

- **[Alert](/02-design-system/05-components/alerts.md)** -- For persistent, inline messages; use alerts when feedback must remain visible until the user acts.
- **[Modal](/02-design-system/05-components/modal.md)** -- For blocking, critical messages that require acknowledgment before proceeding.
- **[Progress](/02-design-system/05-components/progress.md)** -- Can be used in combination with toasts for long-running background operations.
- **[Tags](/02-design-system/05-components/tags.md)** -- For status metadata on content items; use tags for persistent labeling rather than transient feedback.
