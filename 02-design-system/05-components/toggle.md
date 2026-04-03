# Toggle

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Toggles (also known as switches) are controls that allow users to turn a setting on or off with immediate effect. Unlike checkboxes, which often require a form submission to apply, toggles communicate instant state changes -- like enabling dark mode, activating notifications, or toggling a feature flag. Use toggles for binary settings where the change takes effect as soon as the user interacts with the control.

---

## Anatomy

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│  [Label text]                     ┌──────────────────┐   │
│  [Description text]               │  ┌────┐          │   │
│                                   │  │    │  ░░░░░░░ │   │
│                                   │  └────┘          │   │
│                                   └──────────────────┘   │
│                                          OFF             │
│                                                          │
│  [Label text]                     ┌──────────────────┐   │
│  [Description text]               │  ░░░░░░░  ┌────┐ │   │
│                                   │  ░░░░░░░  │    │ │   │
│                                   │  ░░░░░░░  └────┘ │   │
│                                   └──────────────────┘   │
│                                          ON              │
│                                                          │
└──────────────────────────────────────────────────────────┘

Detailed toggle anatomy:
        OFF state                    ON state
┌──────────────────┐        ┌──────────────────┐
│ ┌────┐           │        │           ┌────┐ │
│ │Knob│   [Track] │        │  [Track]  │Knob│ │
│ └────┘           │        │           └────┘ │
└──────────────────┘        └──────────────────┘
```

| Part            | Required | Description                                              |
|-----------------|----------|----------------------------------------------------------|
| Track           | Yes      | The horizontal channel that the knob slides along         |
| Knob (thumb)    | Yes      | The circular handle that moves between on and off         |
| Label           | Yes      | Text describing what the toggle controls                  |
| Description     | No       | Secondary text providing additional context                |
| Status text     | No       | "On" / "Off" text next to the toggle for explicit state   |

---

## Variants

| Variant             | Description                                     | Use Case                                        |
|---------------------|------------------------------------------------ |-------------------------------------------------|
| Default             | Standard toggle with label on the left           | Settings pages, preference panels               |
| With description    | Toggle with secondary descriptive text           | Complex settings needing explanation             |
| With status text    | Displays "On" or "Off" next to the toggle        | When the state needs explicit textual confirmation|
| Compact             | Smaller toggle without label, icon optional       | Inline data tables, dense admin UIs              |

### Label Positioning

| Position | Description                                  | Use Case                              |
|----------|----------------------------------------------|---------------------------------------|
| Left     | Label on the left, toggle on the right (default) | Settings pages, list layouts       |
| Right    | Label on the right, toggle on the left       | Compact layouts, table rows            |

```
Left (default):                    Right:
┌──────────────────────────┐       ┌──────────────────────────┐
│ Enable notifications  ○══│       │ ══● Enable notifications │
└──────────────────────────┘       └──────────────────────────┘
```

---

## States

### On/Off States

| State            | Track BG       | Knob BG    | Knob Border   | Label Color   | Shadow         | Notes                         |
|------------------|----------------|------------|---------------|---------------|----------------|-------------------------------|
| Off              | `neutral-200`  | `white`    | `neutral-300` | `neutral-900` | `sm` on knob   | Default off position          |
| Off + Hover      | `neutral-300`  | `white`    | `neutral-400` | `neutral-900` | `sm` on knob   | Mouse over off toggle         |
| Off + Focus      | `neutral-200`  | `white`    | `blue-600`    | `neutral-900` | `ring-2 blue-100` | Keyboard focus on off      |
| Off + Active     | `neutral-300`  | `white`    | `neutral-400` | `neutral-900` | `sm` on knob   | Mouse down on off toggle      |
| On               | `blue-600`     | `white`    | `transparent` | `neutral-900` | `sm` on knob   | Active on position            |
| On + Hover       | `blue-700`     | `white`    | `transparent` | `neutral-900` | `sm` on knob   | Mouse over on toggle          |
| On + Focus       | `blue-600`     | `white`    | `blue-300`    | `neutral-900` | `ring-2 blue-100` | Keyboard focus on on       |
| On + Active      | `blue-800`     | `white`    | `transparent` | `neutral-900` | `sm` on knob   | Mouse down on on toggle       |
| Disabled Off     | `neutral-100`  | `neutral-50`| `neutral-200`| `neutral-400` | `none`         | Disabled, off position        |
| Disabled On      | `blue-200`     | `white`    | `transparent` | `neutral-400` | `none`         | Disabled, on position         |

### Transition Animation

| Property      | Duration | Easing        | Notes                                          |
|---------------|----------|---------------|-------------------------------------------------|
| Knob position | 200ms    | ease-in-out   | Horizontal slide between off and on positions   |
| Track color   | 150ms    | ease          | Background color transition                     |
| Knob scale    | 100ms    | ease          | Slight scale-up (1.1x) on active/press state   |

---

## Sizing

| Size | Track W x H  | Knob Diameter | Knob Offset | Label Size | Description Size |
|------|--------------|---------------|-------------|------------|------------------|
| sm   | 36px x 20px  | 16px          | 2px         | 14px       | 12px             |
| md   | 44px x 24px  | 20px          | 2px         | 16px       | 14px             |
| lg   | 52px x 28px  | 24px          | 2px         | 16px       | 14px             |

### Layout Spacing

| Property                     | Value  | Token       |
|------------------------------|--------|-------------|
| Label to toggle gap          | 12px   | `{space.3}` |
| Label to description gap     | 2px    | --          |
| Toggle to status text gap    | 8px    | `{space.2}` |
| Vertical gap between toggles | 16px   | `{space.4}` |

---

## Accessibility

- **Role**: Use `role="switch"` on the toggle element. The `aria-checked` attribute must reflect the on/off state (`"true"` or `"false"`).
- **Label**: Associate the label via `aria-labelledby` or provide `aria-label` for toggles without visible labels. The label must describe the setting, not the state (e.g., "Dark mode" not "Turn on dark mode").
- **Description**: Connect descriptive text via `aria-describedby`.
- **State announcement**: Screen readers announce "on" or "off" via the `aria-checked` attribute. The `role="switch"` ensures the screen reader communicates the toggle pattern correctly.
- **Keyboard**:
  - `Tab` / `Shift+Tab` to navigate to and from the toggle.
  - `Space` or `Enter` to toggle the state.
  - Do not use `ArrowLeft` / `ArrowRight` -- those are reserved for radio patterns.
- **Disabled**: Use `aria-disabled="true"` when the toggle should remain focusable (e.g., with a tooltip explaining why it is disabled). Use the native `disabled` attribute to remove it from tab order.
- **Focus indicator**: 2px solid ring in `blue-100` around the track. Meets WCAG 2.1 SC 2.4.7 and SC 1.4.11.
- **Color contrast**: The track color difference between on (`blue-600`) and off (`neutral-200`) provides at least 3:1 contrast against the background. The knob provides additional shape-based indication of state.
- **Motion**: Knob slide animation respects `prefers-reduced-motion: reduce` by switching to an instant state change.
- **Touch target**: Minimum 44x44px touch area for all sizes (expanded via padding or hit area).

---

## Design Tokens

```json
{
  "toggle": {
    "transition-duration": "200ms",
    "transition-easing": "ease-in-out",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.100}",
    "track": {
      "off-bg": "{color.neutral.200}",
      "off-bg-hover": "{color.neutral.300}",
      "off-bg-active": "{color.neutral.300}",
      "off-bg-disabled": "{color.neutral.100}",
      "on-bg": "{color.blue.600}",
      "on-bg-hover": "{color.blue.700}",
      "on-bg-active": "{color.blue.800}",
      "on-bg-disabled": "{color.blue.200}",
      "border-radius": "{border.radius.full}"
    },
    "knob": {
      "bg": "{color.white}",
      "bg-disabled": "{color.neutral.50}",
      "border-off": "{color.neutral.300}",
      "border-off-hover": "{color.neutral.400}",
      "border-on": "transparent",
      "shadow": "{shadow.sm}",
      "shadow-disabled": "none",
      "border-radius": "{border.radius.full}",
      "active-scale": "1.1"
    },
    "label": {
      "font-weight": "400",
      "color": "{color.neutral.900}",
      "color-disabled": "{color.neutral.400}"
    },
    "description": {
      "font-weight": "400",
      "color": "{color.neutral.500}",
      "color-disabled": "{color.neutral.400}"
    },
    "status-text": {
      "font-size": "12px",
      "font-weight": "500",
      "color-on": "{color.blue.600}",
      "color-off": "{color.neutral.500}",
      "color-disabled": "{color.neutral.400}"
    },
    "sizing": {
      "sm": {
        "track-width": "36px",
        "track-height": "20px",
        "knob-size": "16px",
        "knob-offset": "2px",
        "label-font-size": "{typography.body.sm.size}",
        "description-font-size": "12px"
      },
      "md": {
        "track-width": "44px",
        "track-height": "24px",
        "knob-size": "20px",
        "knob-offset": "2px",
        "label-font-size": "{typography.body.md.size}",
        "description-font-size": "{typography.body.sm.size}"
      },
      "lg": {
        "track-width": "52px",
        "track-height": "28px",
        "knob-size": "24px",
        "knob-offset": "2px",
        "label-font-size": "{typography.body.md.size}",
        "description-font-size": "{typography.body.sm.size}"
      }
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use toggles for binary settings where the effect is immediate -- no "Save" button required.
- Write labels that describe the setting being controlled, not the current state (e.g., "Dark mode" not "Dark mode is off").
- Place toggles in settings pages, preference panels, and admin dashboards where users configure their experience.
- Add descriptive text below the label when the setting's impact is not immediately obvious.
- Use the status text variant ("On" / "Off") in contexts where the visual state of the toggle alone is insufficient.
- Maintain consistent label positioning (left or right) within the same form or settings section.

**Don't:**
- Don't use toggles for choices that require a form submission -- use checkboxes instead.
- Don't use toggles for mutually exclusive options with more than two states -- use radio buttons.
- Don't use a toggle when the effect is not immediate and reversible -- use a checkbox with a save action.
- Don't change the label text based on the toggle state (e.g., don't switch between "Enable" and "Disable").
- Don't mix left-positioned and right-positioned labels in the same settings section.
- Don't override token colors with hardcoded hex values.
- Don't use toggles in forms that have a "Submit" or "Save" button -- checkboxes are more appropriate in that context.

---

## Code Example

### HTML

```html
<!-- Basic toggle -->
<label class="ff-toggle ff-toggle--md">
  <span class="ff-toggle__label">Dark mode</span>
  <button
    class="ff-toggle__switch"
    role="switch"
    aria-checked="false"
    aria-labelledby="toggle-dark-label"
  >
    <span class="ff-toggle__track">
      <span class="ff-toggle__knob"></span>
    </span>
  </button>
</label>

<!-- Toggle with description (on state) -->
<div class="ff-toggle ff-toggle--md">
  <div class="ff-toggle__content">
    <span class="ff-toggle__label" id="toggle-notif-label">Push notifications</span>
    <span class="ff-toggle__description" id="toggle-notif-desc">
      Receive push notifications for new messages and updates.
    </span>
  </div>
  <button
    class="ff-toggle__switch ff-toggle__switch--on"
    role="switch"
    aria-checked="true"
    aria-labelledby="toggle-notif-label"
    aria-describedby="toggle-notif-desc"
  >
    <span class="ff-toggle__track">
      <span class="ff-toggle__knob"></span>
    </span>
  </button>
</div>

<!-- Toggle with status text -->
<div class="ff-toggle ff-toggle--md">
  <span class="ff-toggle__label" id="toggle-auto-label">Auto-save</span>
  <div class="ff-toggle__group">
    <button
      class="ff-toggle__switch ff-toggle__switch--on"
      role="switch"
      aria-checked="true"
      aria-labelledby="toggle-auto-label"
    >
      <span class="ff-toggle__track">
        <span class="ff-toggle__knob"></span>
      </span>
    </button>
    <span class="ff-toggle__status" aria-hidden="true">On</span>
  </div>
</div>

<!-- Disabled toggle -->
<div class="ff-toggle ff-toggle--md ff-toggle--disabled">
  <span class="ff-toggle__label">Two-factor authentication</span>
  <button
    class="ff-toggle__switch"
    role="switch"
    aria-checked="false"
    aria-disabled="true"
  >
    <span class="ff-toggle__track">
      <span class="ff-toggle__knob"></span>
    </span>
  </button>
</div>

<!-- Settings list with multiple toggles -->
<div class="ff-toggle-list" role="group" aria-label="Notification preferences">
  <div class="ff-toggle ff-toggle--md">
    <div class="ff-toggle__content">
      <span class="ff-toggle__label">Email notifications</span>
      <span class="ff-toggle__description">Daily digest of activity.</span>
    </div>
    <button class="ff-toggle__switch ff-toggle__switch--on" role="switch" aria-checked="true">
      <span class="ff-toggle__track"><span class="ff-toggle__knob"></span></span>
    </button>
  </div>
  <div class="ff-toggle ff-toggle--md">
    <div class="ff-toggle__content">
      <span class="ff-toggle__label">SMS alerts</span>
      <span class="ff-toggle__description">Urgent notifications via text.</span>
    </div>
    <button class="ff-toggle__switch" role="switch" aria-checked="false">
      <span class="ff-toggle__track"><span class="ff-toggle__knob"></span></span>
    </button>
  </div>
</div>
```

### JSX

```jsx
import { Toggle, ToggleGroup } from '@flavio-fusuma/ui';

// Basic toggle
<Toggle
  label="Dark mode"
  size="md"
  checked={isDarkMode}
  onChange={setIsDarkMode}
/>

// Toggle with description
<Toggle
  label="Push notifications"
  description="Receive push notifications for new messages and updates."
  size="md"
  checked={pushEnabled}
  onChange={setPushEnabled}
/>

// Toggle with status text
<Toggle
  label="Auto-save"
  size="md"
  checked={autoSave}
  onChange={setAutoSave}
  showStatus
/>

// Disabled toggle
<Toggle
  label="Two-factor authentication"
  size="md"
  checked={false}
  disabled
/>

// Label on the right
<Toggle
  label="Airplane mode"
  size="md"
  labelPosition="right"
  checked={airplaneMode}
  onChange={setAirplaneMode}
/>

// Small toggle in a table row
<Toggle
  size="sm"
  aria-label="Enable user account"
  checked={user.active}
  onChange={(val) => toggleUser(user.id, val)}
/>

// Settings group
<ToggleGroup label="Notification preferences">
  <Toggle
    label="Email notifications"
    description="Daily digest of activity."
    checked={emailNotifs}
    onChange={setEmailNotifs}
  />
  <Toggle
    label="SMS alerts"
    description="Urgent notifications via text."
    checked={smsAlerts}
    onChange={setSmsAlerts}
  />
  <Toggle
    label="In-app notifications"
    description="Real-time notifications in the app."
    checked={inAppNotifs}
    onChange={setInAppNotifs}
  />
</ToggleGroup>
```

---

## Related Components

- **[Checkbox & Radio](./checkbox-radio.md)** -- Use checkboxes instead of toggles when the change requires a form submission. Use radios for mutually exclusive choices with more than two options.
- **[Buttons](./buttons.md)** -- For triggering one-time actions rather than toggling persistent settings.
- **[Cards](./cards.md)** -- Toggles frequently appear in card-based settings layouts.
- **[Inputs](./inputs.md)** -- Often appear alongside toggles in settings forms.
- **[Tooltips](./tooltips.md)** -- Use tooltips on disabled toggles to explain why the setting is unavailable.
