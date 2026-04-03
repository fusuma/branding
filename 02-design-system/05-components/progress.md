# Progress

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Progress indicators communicate the status of ongoing processes such as file uploads, form submissions, data loading, or multi-step workflows. They set user expectations by showing either a known completion percentage (determinate) or that work is happening without a specific endpoint (indeterminate). Use progress indicators when an operation takes longer than one second and the user benefits from knowing the system is working.

---

## Anatomy

### Progress Bar (Linear)

```
With label and percentage:
┌──────────────────────────────────────────┐
│  Uploading files...              65%     │
│  ┌───────────────────────────────────┐   │
│  │████████████████████░░░░░░░░░░░░░░│   │
│  └───────────────────────────────────┘   │
└──────────────────────────────────────────┘

Indeterminate bar:
┌──────────────────────────────────────────┐
│  Loading...                              │
│  ┌───────────────────────────────────┐   │
│  │░░░░░████████░░░░░░░░░░░░░░░░░░░░░│   │
│  └───────────────────────────────────┘   │
│          ← sliding animation →           │
└──────────────────────────────────────────┘

Segmented bar (multi-step):
┌──────────────────────────────────────────┐
│  Step 2 of 4                             │
│  ┌────────┬────────┬────────┬────────┐   │
│  │████████│████████│░░░░░░░░│░░░░░░░░│   │
│  └────────┴────────┴────────┴────────┘   │
└──────────────────────────────────────────┘
```

### Progress Circle (Circular)

```
Determinate circle:        Indeterminate circle:
   ┌─────────┐                ┌─────────┐
   │  ╭───╮  │                │  ╭───╮  │
   │ ╱     ╲ │                │ ╱  ╲  ╲ │
   │ │ 65% │ │                │ │    │ │ │
   │ ╲     ╱ │                │ ╲     ╱ │
   │  ╰───╯  │                │  ╰───╯  │
   └─────────┘                └─────────┘
   ████ filled track          rotating arc
   ░░░░ empty track

With icon (complete):
   ┌─────────┐
   │  ╭───╮  │
   │ ╱     ╲ │
   │ │  ✓  │ │
   │ ╲     ╱ │
   │  ╰───╯  │
   └─────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Track (background) | Yes | The unfilled portion of the progress indicator |
| Fill (value) | Yes | The filled portion representing completion progress |
| Label | No | Text describing the process (e.g., "Uploading files...") |
| Percentage | No | Numeric representation of completion (e.g., "65%") |
| Description | No | Additional detail text (e.g., "3 of 12 files uploaded") |
| Center content (circle) | No | Text, percentage, or icon displayed in the center of a circular indicator |

---

## Variants

### Shape Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Bar (linear) | Horizontal progress bar | File uploads, form completion, page loading, data processing |
| Circle (circular) | Ring/donut progress indicator | Dashboard stats, profile completeness, single-metric display |

### Mode Variants

| Mode | Description | Visual Behavior |
|------|-------------|----------------|
| Determinate | Known completion percentage (0-100%) | Fill grows proportionally from left to right (bar) or clockwise (circle) |
| Indeterminate | Unknown completion; work is in progress | Animated sliding segment (bar) or rotating arc (circle) |

### Color Variants (Semantic)

| Color | Fill Color | Track Color | Use Case |
|-------|-----------|-------------|----------|
| Default | `blue-600` #2563EB | `neutral-200` #E2E8F0 | Standard progress, neutral operations |
| Success | `green-600` #16A34A | `green-100` #DCFCE7 | Completed processes, positive metrics |
| Warning | `amber-500` #F59E0B | `amber-100` #FEF3C7 | Approaching limits, caution states |
| Error | `red-600` #DC2626 | `red-100` #FEE2E2 | Failed processes, over-limit indicators |

---

## States

### Determinate Progress States

| State | Fill Color | Track Color | Animation | Notes |
|-------|-----------|-------------|-----------|-------|
| In progress (0-99%) | Semantic color | Track color | Fill width/arc animates smoothly | Value updates with transition |
| Complete (100%) | `green-600` | `green-100` | Fill completes, optional check animation | Can auto-switch to success color |
| Error | `red-600` | `red-100` | Fill stops at current position | Combined with error message |
| Paused | Semantic color (50% opacity) | Track color | No animation | Optional pulse animation |

### Indeterminate Progress States

| State | Fill Color | Track Color | Animation | Notes |
|-------|-----------|-------------|-----------|-------|
| Loading | Semantic color | Track color | Sliding (bar) or rotating (circle) continuously | Loops indefinitely |
| Complete | Transition to determinate 100% | Track color | Fill animates to full | Then optionally hides |
| Error | `red-600` | `red-100` | Animation stops | Display error state |

### Bar Fill Animation

| Property | Value | Notes |
|----------|-------|-------|
| Determinate transition | `width 400ms ease-in-out` | Smooth fill on value change |
| Indeterminate animation | `2s ease-in-out infinite` | Sliding back and forth |
| Indeterminate segment width | 40% of track width | Animated segment |
| Complete animation | Optional scale bounce | Brief 100ms scale to 1.02 then back |

### Circle Animation

| Property | Value | Notes |
|----------|-------|-------|
| Determinate transition | `stroke-dashoffset 400ms ease-in-out` | SVG stroke animation |
| Indeterminate animation | `1.5s linear infinite` | Continuous rotation |
| Start angle | 12 o'clock (top) | Progress starts from top |
| Direction | Clockwise | Standard reading direction |

---

## Sizing

### Bar Sizing

| Size | Track Height | Border Radius | Label Font Size | Percentage Font Size |
|------|-------------|---------------|----------------|---------------------|
| sm | 4px | 2px | 12px | 12px |
| md | 8px | 4px (`{border.radius.sm}`) | 14px | 14px |
| lg | 12px | 6px (`{border.radius.md}`) | 14px | 16px |

### Circle Sizing

| Size | Diameter | Stroke Width | Center Font Size | Use Case |
|------|----------|-------------|-----------------|----------|
| sm | 32px | 3px | 10px | Inline indicators, table cells |
| md | 48px | 4px | 14px | Card metrics, compact dashboards |
| lg | 64px | 5px | 18px | Default; standalone indicators |
| xl | 96px | 6px | 24px | Hero metrics, dashboard widgets |
| 2xl | 128px | 8px | 32px | Large profile completeness, feature displays |

### Label Positioning

| Position | Bar | Circle |
|----------|-----|--------|
| Above | Label left-aligned, percentage right-aligned above the track | N/A |
| Below | Label left-aligned, percentage right-aligned below the track | Label below the circle |
| Inside (lg only) | Percentage centered inside the track (lg bars only) | Percentage or icon centered inside the circle |
| None | No label or percentage displayed | No label displayed |

---

## Accessibility

- **Role**: Use `role="progressbar"` on the progress element.
- **ARIA -- determinate**: Include `aria-valuenow`, `aria-valuemin="0"`, and `aria-valuemax="100"`. Update `aria-valuenow` as progress changes.
- **ARIA -- indeterminate**: Omit `aria-valuenow` when the value is unknown. The absence signals indeterminate mode to assistive technology.
- **ARIA -- label**: Add `aria-label` (e.g., "File upload progress") or `aria-labelledby` pointing to the visible label element.
- **ARIA -- live**: Wrap the progress component in an `aria-live="polite"` region so screen readers announce progress updates. Throttle announcements to avoid excessive verbosity (announce at 25%, 50%, 75%, and 100%).
- **Keyboard**: Progress indicators are non-interactive and not focusable. If the user can pause or cancel the operation, those controls must be separate focusable buttons.
- **Screen reader**: Announces the label, current percentage (determinate), or "loading" (indeterminate). Announces completion when reaching 100%.
- **Color**: Semantic color variants are paired with labels and percentage text; color is not the sole indicator of status.
- **Motion**: Indeterminate animations respect `prefers-reduced-motion: reduce` by switching to a static or reduced-motion indicator (e.g., pulsing opacity instead of sliding).

---

## Design Tokens

```json
{
  "progress": {
    "font-family": "{typography.font.sans}",
    "transition": "width 400ms ease-in-out",
    "bar": {
      "sm": {
        "height": "4px",
        "border-radius": "2px",
        "label-font-size": "12px"
      },
      "md": {
        "height": "8px",
        "border-radius": "{border.radius.sm}",
        "label-font-size": "{typography.body.md.size}"
      },
      "lg": {
        "height": "12px",
        "border-radius": "{border.radius.md}",
        "label-font-size": "{typography.body.md.size}"
      }
    },
    "circle": {
      "sm": {
        "diameter": "32px",
        "stroke-width": "3px",
        "font-size": "10px"
      },
      "md": {
        "diameter": "48px",
        "stroke-width": "4px",
        "font-size": "{typography.body.md.size}"
      },
      "lg": {
        "diameter": "64px",
        "stroke-width": "5px",
        "font-size": "18px"
      },
      "xl": {
        "diameter": "96px",
        "stroke-width": "6px",
        "font-size": "24px"
      },
      "2xl": {
        "diameter": "128px",
        "stroke-width": "8px",
        "font-size": "32px"
      }
    },
    "default": {
      "fill": "{color.blue.600}",
      "track": "{color.neutral.200}"
    },
    "success": {
      "fill": "{color.green.600}",
      "track": "{color.green.100}"
    },
    "warning": {
      "fill": "{color.amber.500}",
      "track": "{color.amber.100}"
    },
    "error": {
      "fill": "{color.red.600}",
      "track": "{color.red.100}"
    },
    "label": {
      "color": "{color.neutral.700}",
      "font-weight": "500"
    },
    "percentage": {
      "color": "{color.neutral.900}",
      "font-weight": "600"
    },
    "description": {
      "color": "{color.neutral.500}",
      "font-size": "{typography.body.sm.size}"
    },
    "indeterminate": {
      "bar-animation": "2s ease-in-out infinite",
      "bar-segment-width": "40%",
      "circle-animation": "1.5s linear infinite"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use determinate progress when you can calculate or estimate the completion percentage accurately.
- Use indeterminate progress when the duration is unknown (e.g., waiting for a server response).
- Include a text label describing what is happening (e.g., "Uploading files...", "Processing payment...").
- Show the percentage for determinate progress bars to set clear expectations.
- Transition from indeterminate to determinate when the total becomes known during the process.
- Use the success color variant and a check icon when the operation completes successfully.

**Don't:**
- Don't use a progress indicator for operations under one second; they cause unnecessary visual noise.
- Don't show fake progress that does not reflect actual completion (this erodes trust).
- Don't use a circular progress indicator for multi-step or multi-segment processes; use a segmented bar.
- Don't auto-hide the progress indicator on completion without giving users time to see the 100% state (show for at least 500ms).
- Don't use the error color variant during normal progress; only switch to error when the operation has actually failed.
- Don't combine indeterminate bars with percentage labels; an unknown process should not show a false number.

---

## Code Example

### HTML

```html
<!-- Determinate progress bar with label -->
<div class="ff-progress ff-progress--bar ff-progress--md">
  <div class="ff-progress__header">
    <span class="ff-progress__label" id="upload-label">Uploading files...</span>
    <span class="ff-progress__percentage" aria-hidden="true">65%</span>
  </div>
  <div class="ff-progress__track" role="progressbar"
       aria-valuenow="65" aria-valuemin="0" aria-valuemax="100"
       aria-labelledby="upload-label">
    <div class="ff-progress__fill" style="width: 65%"></div>
  </div>
  <span class="ff-progress__description">3 of 12 files uploaded</span>
</div>

<!-- Indeterminate progress bar -->
<div class="ff-progress ff-progress--bar ff-progress--md ff-progress--indeterminate">
  <span class="ff-progress__label">Loading data...</span>
  <div class="ff-progress__track" role="progressbar" aria-label="Loading data">
    <div class="ff-progress__fill ff-progress__fill--indeterminate"></div>
  </div>
</div>

<!-- Success progress bar (complete) -->
<div class="ff-progress ff-progress--bar ff-progress--md ff-progress--success">
  <div class="ff-progress__header">
    <span class="ff-progress__label">Upload complete</span>
    <span class="ff-progress__percentage" aria-hidden="true">100%</span>
  </div>
  <div class="ff-progress__track" role="progressbar"
       aria-valuenow="100" aria-valuemin="0" aria-valuemax="100"
       aria-label="Upload complete">
    <div class="ff-progress__fill" style="width: 100%"></div>
  </div>
</div>

<!-- Warning progress bar -->
<div class="ff-progress ff-progress--bar ff-progress--md ff-progress--warning">
  <div class="ff-progress__header">
    <span class="ff-progress__label">Storage used</span>
    <span class="ff-progress__percentage" aria-hidden="true">85%</span>
  </div>
  <div class="ff-progress__track" role="progressbar"
       aria-valuenow="85" aria-valuemin="0" aria-valuemax="100"
       aria-label="Storage used, 85 percent">
    <div class="ff-progress__fill" style="width: 85%"></div>
  </div>
</div>

<!-- Circular progress (determinate) -->
<div class="ff-progress ff-progress--circle ff-progress--lg">
  <svg class="ff-progress__circle" viewBox="0 0 64 64"
       role="progressbar" aria-valuenow="65" aria-valuemin="0" aria-valuemax="100"
       aria-label="Profile completeness">
    <circle class="ff-progress__circle-track" cx="32" cy="32" r="28" />
    <circle class="ff-progress__circle-fill" cx="32" cy="32" r="28"
            stroke-dasharray="175.93" stroke-dashoffset="61.58" />
  </svg>
  <span class="ff-progress__center-text" aria-hidden="true">65%</span>
</div>

<!-- Circular progress (indeterminate) -->
<div class="ff-progress ff-progress--circle ff-progress--md ff-progress--indeterminate">
  <svg class="ff-progress__circle ff-progress__circle--spinning" viewBox="0 0 48 48"
       role="progressbar" aria-label="Loading">
    <circle class="ff-progress__circle-track" cx="24" cy="24" r="20" />
    <circle class="ff-progress__circle-fill" cx="24" cy="24" r="20" />
  </svg>
</div>
```

### JSX

```jsx
import { ProgressBar, ProgressCircle } from '@flaviofusuma/ui';

{/* Determinate progress bar */}
<ProgressBar
  value={65}
  size="md"
  label="Uploading files..."
  description="3 of 12 files uploaded"
  showPercentage
/>

{/* Indeterminate progress bar */}
<ProgressBar
  indeterminate
  size="md"
  label="Loading data..."
/>

{/* Success (complete) */}
<ProgressBar
  value={100}
  size="md"
  color="success"
  label="Upload complete"
  showPercentage
/>

{/* Warning progress */}
<ProgressBar
  value={85}
  size="md"
  color="warning"
  label="Storage used"
  showPercentage
/>

{/* Error progress */}
<ProgressBar
  value={42}
  size="md"
  color="error"
  label="Upload failed"
  showPercentage
/>

{/* Circular determinate */}
<ProgressCircle
  value={65}
  size="lg"
  label="Profile completeness"
  showPercentage
/>

{/* Circular indeterminate */}
<ProgressCircle
  indeterminate
  size="md"
  label="Loading"
/>

{/* Circular with icon on complete */}
<ProgressCircle
  value={100}
  size="lg"
  color="success"
  centerContent={<CheckIcon />}
  label="Complete"
/>

{/* Small inline progress */}
<ProgressBar value={30} size="sm" color="default" />
```

---

## Related Components

- **[Skeleton](/02-design-system/05-components/skeleton.md)** -- For content placeholder loading; use skeletons when the layout shape is known but data is pending, and progress bars when showing operation completion.
- **[Toast](/02-design-system/05-components/toast.md)** -- Toasts can include a progress bar for auto-dismiss countdown or to show background operation status.
- **[Alerts](/02-design-system/05-components/alerts.md)** -- Pair alerts with progress indicators to communicate process status and outcome messages.
- **[Buttons](/02-design-system/05-components/buttons.md)** -- Button loading state shows inline progress; use standalone progress for longer or background operations.
