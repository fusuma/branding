# Modals

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Modals (also called dialogs) are overlay windows that appear above the main content to capture the user's attention for a critical task, decision, or information. They interrupt the user's workflow and require interaction before returning to the underlying page. Use modals for confirmations, forms, alerts, and content that demands focused attention. Avoid modals for non-essential information that could be presented inline or in a toast.

---

## Anatomy

```
┌──────────────────────────────────────────────────────────────┐
│                       [Overlay]                              │
│                                                              │
│       ┌──────────────────────────────────────────┐           │
│       │ [Header]                          ┌────┐ │           │
│       │  [Title]                          │ ✕  │ │           │
│       │  [Subtitle]                       └────┘ │           │
│       ├──────────────────────────────────────────┤           │
│       │ [Body]                                   │           │
│       │                                          │           │
│       │  Content: text, forms, images,           │           │
│       │  tables, or any child components.        │           │
│       │                                          │           │
│       │                                          │           │
│       ├──────────────────────────────────────────┤           │
│       │ [Footer]                                 │           │
│       │            ┌──────────┐  ┌────────────┐  │           │
│       │            │  Cancel  │  │  Confirm   │  │           │
│       │            └──────────┘  └────────────┘  │           │
│       └──────────────────────────────────────────┘           │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

| Part          | Required | Description                                              |
|---------------|----------|----------------------------------------------------------|
| Overlay       | Yes      | Semi-transparent backdrop behind the modal                |
| Container     | Yes      | The modal window with background, shadow, and radius      |
| Header        | Yes      | Contains title, optional subtitle, and close button       |
| Title         | Yes      | Primary heading describing the modal's purpose            |
| Subtitle      | No       | Secondary text providing additional context                |
| Close button  | Yes      | X icon button in the top-right corner                     |
| Body          | Yes      | Main content area, scrollable when content overflows      |
| Footer        | No       | Action buttons: primary confirm and secondary cancel      |
| Dividers      | No       | Horizontal lines separating header, body, and footer      |

---

## Variants

| Variant       | Description                                         | Use Case                                        |
|---------------|-----------------------------------------------------|-------------------------------------------------|
| Default       | Standard modal with header, body, and footer         | Forms, confirmations, multi-step wizards         |
| Alert         | Compact modal for critical confirmations             | Delete confirmation, unsaved changes warning     |
| Form          | Modal optimized for form content                     | Create/edit entity, settings, data entry         |
| Full-screen   | Covers the entire viewport                           | Image preview, complex editors, mobile forms     |

---

## Sizes

| Size | Width        | Max Height         | Use Case                                      |
|------|--------------|--------------------|-----------------------------------------------|
| sm   | 400px        | 80vh               | Simple confirmations, alerts, short messages   |
| md   | 560px        | 80vh               | Forms, standard content dialogs                |
| lg   | 720px        | 85vh               | Complex forms, tables, multi-column layouts    |
| full | 100vw - 32px | 100vh - 32px       | Image viewers, rich editors, mobile screens    |

### Mobile Behavior

| Breakpoint     | Behavior                                                  |
|----------------|-----------------------------------------------------------|
| > 768px        | Modal centered horizontally and vertically with overlay    |
| <= 768px (sm/md)| Modal stretches to full width, anchored to bottom of screen (sheet behavior) |
| <= 768px (lg)  | Modal stretches to full width and near-full height         |
| <= 768px (full)| True full-screen, no overlay visible                       |

---

## States

### Modal Container States

| State      | Overlay       | Container       | Notes                                       |
|------------|---------------|-----------------|---------------------------------------------|
| Closed     | hidden        | hidden          | Modal is not rendered or visually hidden     |
| Opening    | `black/50%`   | scale(0.95) -> scale(1), opacity 0 -> 1 | 200ms ease-out entrance animation |
| Open       | `black/50%`   | scale(1), opacity 1 | Fully visible and interactive            |
| Closing    | `black/50%` -> transparent | scale(1) -> scale(0.95), opacity 1 -> 0 | 150ms ease-in exit animation |

### Close Button States

| State    | Background     | Icon Color    | Shadow            | Notes                  |
|----------|----------------|---------------|-------------------|------------------------|
| Default  | `transparent`  | `neutral-500` | `none`            | Resting                |
| Hover    | `neutral-100`  | `neutral-700` | `none`            | Mouse over             |
| Active   | `neutral-200`  | `neutral-900` | `none`            | Pressed                |
| Focus    | `transparent`  | `neutral-500` | `ring-2 blue-100` | Keyboard focus         |

### Overlay States

| State      | Background         | Cursor   | Notes                                 |
|------------|--------------------|----------|---------------------------------------|
| Default    | `black` at 50% opacity | default | Semi-transparent backdrop            |
| Hover      | `black` at 50% opacity | default | No visual change                     |
| Click      | --                 | --       | Closes modal (unless `closeOnOverlayClick` is false) |

---

## Scroll Behavior

| Scenario                     | Behavior                                                 |
|------------------------------|----------------------------------------------------------|
| Body content fits            | No scrollbar, body takes natural height                  |
| Body content overflows       | Body section scrolls independently; header and footer remain fixed |
| Background page              | `overflow: hidden` applied to `<body>` when modal is open |
| Scroll restoration           | Page scroll position restored when modal closes           |

```
Fixed header and footer with scrollable body:
┌──────────────────────────────────┐
│ Header (fixed)            [✕]   │
├──────────────────────────────────┤
│ ▲                                │
│ Body content line 1              │
│ Body content line 2              │  <- scrollable
│ Body content line 3              │
│ Body content line 4              │
│ ▼                                │
├──────────────────────────────────┤
│ Footer (fixed)     [Cancel][OK] │
└──────────────────────────────────┘
```

---

## Animation

| Phase    | Property    | From              | To                | Duration | Easing     |
|----------|-------------|-------------------|--------------------|----------|------------|
| Enter    | opacity     | 0                 | 1                  | 200ms    | ease-out   |
| Enter    | transform   | scale(0.95)       | scale(1)           | 200ms    | ease-out   |
| Enter    | overlay     | transparent       | `black/50%`        | 200ms    | ease-out   |
| Exit     | opacity     | 1                 | 0                  | 150ms    | ease-in    |
| Exit     | transform   | scale(1)          | scale(0.95)        | 150ms    | ease-in    |
| Exit     | overlay     | `black/50%`       | transparent        | 150ms    | ease-in    |

All animations respect `prefers-reduced-motion: reduce` by switching to instant show/hide (opacity only, no scale transform).

---

## Sizing Details

| Property              | sm      | md      | lg      | full         |
|-----------------------|---------|---------|---------|--------------|
| Width                 | 400px   | 560px   | 720px   | calc(100vw - 32px) |
| Max height            | 80vh    | 80vh    | 85vh    | calc(100vh - 32px) |
| Border radius         | 12px    | 12px    | 12px    | 12px (0 on mobile) |
| Header padding        | 16px 24px | 20px 24px | 24px 32px | 24px 32px  |
| Body padding          | 0 24px 16px | 0 24px 20px | 0 32px 24px | 0 32px 24px |
| Footer padding        | 16px 24px | 16px 24px | 20px 32px | 20px 32px  |
| Close button size     | 32px    | 36px    | 36px    | 40px         |
| Close icon size       | 16px    | 20px    | 20px    | 24px         |
| Title font size       | 18px    | 20px    | 24px    | 24px         |
| Footer button gap     | 8px     | 8px     | 12px    | 12px         |
| Shadow                | `xl`    | `xl`    | `2xl`   | `none`       |

---

## Accessibility

- **Role**: Use the native `<dialog>` element or apply `role="dialog"` with `aria-modal="true"`.
- **Label**: Provide `aria-labelledby` pointing to the title element's ID. If the modal has a description, add `aria-describedby` pointing to the body or a description element.
- **Focus trap**: Focus must be trapped within the modal while it is open. `Tab` and `Shift+Tab` cycle through focusable elements without escaping to the background. Use a focus-trap library or implement the trap manually.
- **Initial focus**: When the modal opens, move focus to the first focusable element in the body, or the close button if the body has no interactive elements. For destructive modals (delete confirmation), consider focusing the cancel button to prevent accidental confirmation.
- **Return focus**: When the modal closes, return focus to the element that triggered the modal.
- **Close button**: The close button must have `aria-label="Close dialog"` or `aria-label="Close [modal title]"`.
- **Keyboard**:
  - `Escape` closes the modal (unless the modal is non-dismissible, e.g., blocking confirmation).
  - `Tab` / `Shift+Tab` cycle through focusable elements within the modal.
  - `Enter` activates the focused button.
  - Do not use `Enter` to auto-submit -- it should only activate the currently focused element.
- **Background inertness**: Apply `aria-hidden="true"` or `inert` attribute to all content behind the overlay so screen readers cannot access background content.
- **Scroll lock**: Prevent background scroll and restore it when the modal closes. Use `overflow: hidden` on `<body>`.
- **Motion**: All animations respect `prefers-reduced-motion: reduce`.
- **Color contrast**: Overlay must not reduce readability of modal content. All text in the modal meets WCAG AA (4.5:1).

---

## Design Tokens

```json
{
  "modal": {
    "font-family": "{typography.font.sans}",
    "border-radius": "{border.radius.xl}",
    "bg": "{color.white}",
    "z-index": "100",
    "overlay": {
      "bg": "rgba(0, 0, 0, 0.5)",
      "z-index": "99"
    },
    "animation": {
      "enter-duration": "200ms",
      "enter-easing": "ease-out",
      "exit-duration": "150ms",
      "exit-easing": "ease-in",
      "scale-from": "0.95",
      "scale-to": "1"
    },
    "close-button": {
      "bg": "transparent",
      "bg-hover": "{color.neutral.100}",
      "bg-active": "{color.neutral.200}",
      "icon-color": "{color.neutral.500}",
      "icon-color-hover": "{color.neutral.700}",
      "border-radius": "{border.radius.md}",
      "focus-ring-color": "{color.blue.100}"
    },
    "header": {
      "title-font-weight": "600",
      "title-color": "{color.neutral.900}",
      "subtitle-font-size": "{typography.body.sm.size}",
      "subtitle-color": "{color.neutral.500}",
      "border-bottom": "1px solid {color.neutral.100}"
    },
    "body": {
      "color": "{color.neutral.700}",
      "font-size": "{typography.body.md.size}",
      "line-height": "24px",
      "overflow-y": "auto"
    },
    "footer": {
      "border-top": "1px solid {color.neutral.100}",
      "gap": "{space.2}",
      "justify": "flex-end"
    },
    "sizing": {
      "sm": {
        "width": "400px",
        "max-height": "80vh",
        "shadow": "{shadow.xl}",
        "header-padding": "{space.4} {space.6}",
        "body-padding": "0 {space.6} {space.4}",
        "footer-padding": "{space.4} {space.6}",
        "title-font-size": "18px"
      },
      "md": {
        "width": "560px",
        "max-height": "80vh",
        "shadow": "{shadow.xl}",
        "header-padding": "{space.5} {space.6}",
        "body-padding": "0 {space.6} {space.5}",
        "footer-padding": "{space.4} {space.6}",
        "title-font-size": "20px"
      },
      "lg": {
        "width": "720px",
        "max-height": "85vh",
        "shadow": "{shadow.2xl}",
        "header-padding": "{space.6} {space.8}",
        "body-padding": "0 {space.8} {space.6}",
        "footer-padding": "{space.5} {space.8}",
        "title-font-size": "24px"
      },
      "full": {
        "width": "calc(100vw - 32px)",
        "max-height": "calc(100vh - 32px)",
        "shadow": "none",
        "header-padding": "{space.6} {space.8}",
        "body-padding": "0 {space.8} {space.6}",
        "footer-padding": "{space.5} {space.8}",
        "title-font-size": "24px"
      }
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use modals for tasks that require the user's immediate attention or a focused decision (confirmations, forms, critical alerts).
- Always include a close button and support `Escape` to dismiss (unless the modal is intentionally blocking).
- Place the primary action button on the right in the footer, with the cancel/secondary action on the left.
- Use the smallest size that comfortably fits the content -- do not default to large modals.
- Implement proper focus trap and return focus to the trigger element when the modal closes.
- Provide a descriptive title that communicates the modal's purpose.
- Allow closing by clicking the overlay for informational and non-destructive modals.

**Don't:**
- Don't use modals for content that can be displayed inline, in a panel, or in a toast notification.
- Don't stack modals on top of modals -- redesign the flow if you need nested modals.
- Don't use modals for long-form content (articles, documentation) -- use a dedicated page.
- Don't auto-open modals on page load without user action (except for critical system alerts).
- Don't remove the close button or Escape key handler -- users must always have a way to dismiss.
- Don't put complex navigation (tabs, breadcrumbs) inside a modal -- it should be a self-contained task.
- Don't override token colors with hardcoded hex values.
- Don't disable overlay click-to-close without a strong UX reason (e.g., destructive confirmation).

---

## Code Example

### HTML

```html
<!-- Default modal (md size) -->
<div class="ff-modal-overlay" aria-hidden="true">
  <div
    class="ff-modal ff-modal--md"
    role="dialog"
    aria-modal="true"
    aria-labelledby="modal-title"
    aria-describedby="modal-body"
  >
    <div class="ff-modal__header">
      <div>
        <h2 class="ff-modal__title" id="modal-title">Edit Profile</h2>
        <p class="ff-modal__subtitle">Update your personal information.</p>
      </div>
      <button class="ff-modal__close" aria-label="Close dialog">
        <svg aria-hidden="true"><!-- close icon --></svg>
      </button>
    </div>
    <div class="ff-modal__body" id="modal-body">
      <div class="ff-input-field ff-input-field--md">
        <label class="ff-input-field__label" for="modal-name">Full name</label>
        <input class="ff-input" type="text" id="modal-name" value="Flavio Fusuma" />
      </div>
      <div class="ff-input-field ff-input-field--md">
        <label class="ff-input-field__label" for="modal-email">Email</label>
        <input class="ff-input" type="email" id="modal-email" value="flavio@example.com" />
      </div>
    </div>
    <div class="ff-modal__footer">
      <button class="ff-btn ff-btn--secondary ff-btn--md">Cancel</button>
      <button class="ff-btn ff-btn--primary ff-btn--md">Save Changes</button>
    </div>
  </div>
</div>

<!-- Alert / confirmation modal (sm size) -->
<div class="ff-modal-overlay">
  <div
    class="ff-modal ff-modal--sm"
    role="alertdialog"
    aria-modal="true"
    aria-labelledby="alert-title"
    aria-describedby="alert-body"
  >
    <div class="ff-modal__header">
      <h2 class="ff-modal__title" id="alert-title">Delete Project</h2>
      <button class="ff-modal__close" aria-label="Close dialog">
        <svg aria-hidden="true"><!-- close icon --></svg>
      </button>
    </div>
    <div class="ff-modal__body" id="alert-body">
      <p>Are you sure you want to delete "Design System v2"? This action cannot be undone and all associated data will be permanently removed.</p>
    </div>
    <div class="ff-modal__footer">
      <button class="ff-btn ff-btn--secondary ff-btn--md">Cancel</button>
      <button class="ff-btn ff-btn--danger ff-btn--md">Delete Project</button>
    </div>
  </div>
</div>

<!-- Full-screen modal -->
<div class="ff-modal-overlay">
  <div
    class="ff-modal ff-modal--full"
    role="dialog"
    aria-modal="true"
    aria-labelledby="full-title"
  >
    <div class="ff-modal__header">
      <h2 class="ff-modal__title" id="full-title">Image Preview</h2>
      <button class="ff-modal__close" aria-label="Close dialog">
        <svg aria-hidden="true"><!-- close icon --></svg>
      </button>
    </div>
    <div class="ff-modal__body">
      <img src="/images/full-preview.jpg" alt="Full resolution preview of uploaded image" />
    </div>
  </div>
</div>
```

### JSX

```jsx
import { Modal } from '@flavio-fusuma/ui';
import { Button, Input } from '@flavio-fusuma/ui';

// Default form modal
<Modal
  isOpen={isOpen}
  onClose={handleClose}
  size="md"
  title="Edit Profile"
  subtitle="Update your personal information."
>
  <Modal.Body>
    <Input label="Full name" value={name} onChange={setName} size="md" />
    <Input label="Email" type="email" value={email} onChange={setEmail} size="md" />
  </Modal.Body>
  <Modal.Footer>
    <Button variant="secondary" size="md" onClick={handleClose}>Cancel</Button>
    <Button variant="primary" size="md" onClick={handleSave}>Save Changes</Button>
  </Modal.Footer>
</Modal>

// Alert dialog for destructive action
<Modal
  isOpen={showDeleteConfirm}
  onClose={() => setShowDeleteConfirm(false)}
  size="sm"
  title="Delete Project"
  role="alertdialog"
  closeOnOverlayClick={false}
  initialFocus="cancel"
>
  <Modal.Body>
    <p>Are you sure you want to delete "Design System v2"? This action cannot be undone.</p>
  </Modal.Body>
  <Modal.Footer>
    <Button variant="secondary" size="md" onClick={() => setShowDeleteConfirm(false)}>
      Cancel
    </Button>
    <Button variant="danger" size="md" onClick={handleDelete}>
      Delete Project
    </Button>
  </Modal.Footer>
</Modal>

// Large modal with scrollable content
<Modal
  isOpen={isTermsOpen}
  onClose={handleCloseTerms}
  size="lg"
  title="Terms of Service"
>
  <Modal.Body>
    <div className="prose">
      {/* Long-form terms content that will scroll */}
    </div>
  </Modal.Body>
  <Modal.Footer>
    <Button variant="secondary" size="md" onClick={handleCloseTerms}>Decline</Button>
    <Button variant="primary" size="md" onClick={handleAcceptTerms}>Accept</Button>
  </Modal.Footer>
</Modal>

// Full-screen modal
<Modal
  isOpen={showPreview}
  onClose={() => setShowPreview(false)}
  size="full"
  title="Image Preview"
>
  <Modal.Body>
    <img src={imageUrl} alt="Full resolution preview" />
  </Modal.Body>
</Modal>
```

---

## Related Components

- **[Buttons](./buttons.md)** -- Modal footers contain button groups for confirm/cancel actions.
- **[Inputs](./inputs.md)** -- Form modals frequently contain text inputs, selects, and other form controls.
- **[Cards](./cards.md)** -- Cards with inline actions may trigger modals for confirmation or detail views.
- **[Tooltips](./tooltips.md)** -- Use tooltips for lightweight contextual help; modals for focused tasks.
- **[Alerts](./alerts.md)** -- For non-blocking messages, use inline alerts instead of modals.
