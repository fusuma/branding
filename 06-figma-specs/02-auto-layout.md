# Auto-Layout Specifications

> Detailed auto-layout configuration for every major component in the Flavio Fusuma Design System. These specs define direction, spacing, padding, alignment, and resizing behavior so that components render consistently in Figma and translate cleanly to CSS flexbox.

---

## Auto-Layout Fundamentals

All components in the Flavio Fusuma system are built with auto-layout as the primary layout mechanism. Auto-layout maps directly to CSS flexbox, making developer handoff predictable.

### Terminology Mapping

| Figma Term | CSS Flexbox Equivalent |
|---|---|
| Direction: Horizontal | `flex-direction: row` |
| Direction: Vertical | `flex-direction: column` |
| Spacing between items | `gap` |
| Padding | `padding` |
| Primary axis alignment | `justify-content` |
| Counter axis alignment | `align-items` |
| Hug contents | `width: fit-content` / `height: fit-content` |
| Fill container | `flex: 1` / `width: 100%` |
| Fixed | Explicit `width` / `height` value |

### Spacing Scale Reference

All spacing values come from the 8px spatial scale:

| Token | Value |
|---|---|
| `space-0.5` | 4px |
| `space-1` | 8px |
| `space-1.5` | 12px |
| `space-2` | 16px |
| `space-3` | 24px |
| `space-4` | 32px |
| `space-5` | 40px |
| `space-6` | 48px |
| `space-8` | 64px |

---

## Component Auto-Layout Specifications

### Button

Buttons use a horizontal auto-layout for the content row, wrapped in a container frame that provides padding.

#### Outer Container

| Property | sm | md | lg |
|---|---|---|---|
| Direction | Horizontal | Horizontal | Horizontal |
| Padding top | 6px | 8px | 12px |
| Padding right | 12px | 16px | 24px |
| Padding bottom | 6px | 8px | 12px |
| Padding left | 12px | 16px | 24px |
| Spacing between items | 8px | 8px | 8px |
| Primary axis alignment | Center | Center | Center |
| Counter axis alignment | Center | Center | Center |
| Width resizing | Hug contents | Hug contents | Hug contents |
| Height resizing | Fixed 32px | Fixed 40px | Fixed 48px |
| Border radius | 6px | 8px | 8px |

#### Icon-Only Button

| Property | sm | md | lg |
|---|---|---|---|
| Direction | Horizontal | Horizontal | Horizontal |
| Padding (all sides) | 6px | 8px | 12px |
| Spacing between items | 0 | 0 | 0 |
| Width resizing | Fixed 32px | Fixed 40px | Fixed 48px |
| Height resizing | Fixed 32px | Fixed 40px | Fixed 48px |

#### Full-Width Button

Same as outer container except:

| Property | Value |
|---|---|
| Width resizing | Fill container |
| Primary axis alignment | Center |

#### Layer Structure

```
button (auto-layout horizontal)
├── icon-leading (16x16 or 20x20, optional)
├── text-label (Inter SemiBold, color by variant)
└── icon-trailing (16x16 or 20x20, optional)
```

---

### Card

Cards use a vertical auto-layout. The internal sections stack vertically, while the action bar is horizontal.

#### Outer Container

| Property | Value |
|---|---|
| Direction | Vertical |
| Padding top | 0 (image extends to edge) or 24px (no image) |
| Padding right | 0 |
| Padding bottom | 0 |
| Padding left | 0 |
| Spacing between items | 0 |
| Primary axis alignment | Top |
| Counter axis alignment | Left |
| Width resizing | Fill container |
| Height resizing | Hug contents |
| Border radius | 12px |
| Clip content | Yes |

#### Card Media (image area)

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 0 |
| Width resizing | Fill container |
| Height resizing | Fixed 200px |
| Object fit | Cover |

#### Card Body

| Property | Value |
|---|---|
| Direction | Vertical |
| Padding top | 16px |
| Padding right | 24px |
| Padding bottom | 16px |
| Padding left | 24px |
| Spacing between items | 8px |
| Width resizing | Fill container |
| Height resizing | Hug contents |

#### Card Footer / Actions

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding top | 0 |
| Padding right | 24px |
| Padding bottom | 24px |
| Padding left | 24px |
| Spacing between items | 12px |
| Primary axis alignment | Right (space-between if multiple actions) |
| Counter axis alignment | Center |
| Width resizing | Fill container |
| Height resizing | Hug contents |

#### Layer Structure

```
card (auto-layout vertical, clip content)
├── card-media (auto-layout horizontal, fill × fixed 200px)
│   └── image-cover
├── card-body (auto-layout vertical, fill × hug)
│   ├── text-title (Inter SemiBold, 18px)
│   ├── text-description (Inter Regular, 14px)
│   └── tag-group (auto-layout horizontal, gap 8px, optional)
│       ├── badge instance
│       └── badge instance
└── card-footer (auto-layout horizontal, fill × hug)
    ├── spacer (fill)
    └── actions (auto-layout horizontal, gap 12px)
        ├── button-secondary instance
        └── button-primary instance
```

---

### Input (Text Field)

Inputs use a vertical stack for label + field + helper, with the field itself being a horizontal auto-layout.

#### Outer Container (field wrapper)

| Property | Value |
|---|---|
| Direction | Vertical |
| Padding | 0 |
| Spacing between items | 4px (label to field), 4px (field to helper) |
| Primary axis alignment | Top |
| Counter axis alignment | Stretch |
| Width resizing | Fill container |
| Height resizing | Hug contents |

#### Label Row

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 0 |
| Spacing between items | 4px |
| Primary axis alignment | Space between |
| Counter axis alignment | Center |
| Width resizing | Fill container |
| Height resizing | Hug contents |

#### Input Field

| Property | sm | md | lg |
|---|---|---|---|
| Direction | Horizontal | Horizontal | Horizontal |
| Padding top | 6px | 8px | 12px |
| Padding right | 12px | 12px | 16px |
| Padding bottom | 6px | 8px | 12px |
| Padding left | 12px | 12px | 16px |
| Spacing between items | 8px | 8px | 8px |
| Primary axis alignment | Left | Left | Left |
| Counter axis alignment | Center | Center | Center |
| Width resizing | Fill container | Fill container | Fill container |
| Height resizing | Fixed 32px | Fixed 40px | Fixed 48px |
| Border radius | 6px | 8px | 8px |
| Border | 1px `color-neutral-300` | 1px `color-neutral-300` | 1px `color-neutral-300` |

#### Helper Row

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 0 |
| Spacing between items | 4px |
| Primary axis alignment | Space between |
| Counter axis alignment | Center |
| Width resizing | Fill container |
| Height resizing | Hug contents |

#### Layer Structure

```
input-field (auto-layout vertical)
├── label-row (auto-layout horizontal, fill × hug)
│   ├── text-label (Inter Medium, 14px)
│   └── text-optional (Inter Regular, 12px, optional)
├── input-container (auto-layout horizontal, fill × fixed)
│   ├── slot-prefix (instance swap, optional)
│   ├── text-value (Inter Regular, fill, 14px/16px)
│   └── slot-suffix (instance swap, optional)
└── helper-row (auto-layout horizontal, fill × hug)
    ├── text-helper (Inter Regular, 12px)
    └── text-character-count (Inter Regular, 12px, optional)
```

---

### Navigation Bar (Top Nav)

The nav bar uses horizontal auto-layout with space-between to distribute the logo, navigation links, and actions.

#### Outer Container

| Property | Desktop | Mobile |
|---|---|---|
| Direction | Horizontal | Horizontal |
| Padding top | 0 | 0 |
| Padding right | 48px | 16px |
| Padding bottom | 0 | 0 |
| Padding left | 48px | 16px |
| Spacing between items | 0 (space-between) | 0 (space-between) |
| Primary axis alignment | Space between | Space between |
| Counter axis alignment | Center | Center |
| Width resizing | Fill container | Fill container |
| Height resizing | Fixed 64px | Fixed 56px |

#### Nav Left (brand area)

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 0 |
| Spacing between items | 12px |
| Counter axis alignment | Center |
| Width resizing | Hug contents |
| Height resizing | Hug contents |

#### Nav Center (link group)

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 0 |
| Spacing between items | 8px |
| Counter axis alignment | Center |
| Width resizing | Hug contents |
| Height resizing | Fill container |

#### Nav Right (actions)

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 0 |
| Spacing between items | 16px |
| Counter axis alignment | Center |
| Width resizing | Hug contents |
| Height resizing | Hug contents |

#### Nav Link Item

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding top | 0 |
| Padding right | 12px |
| Padding bottom | 0 |
| Padding left | 12px |
| Spacing between items | 8px |
| Counter axis alignment | Center |
| Width resizing | Hug contents |
| Height resizing | Fill container (to allow bottom border active indicator) |

#### Layer Structure

```
nav-bar (auto-layout horizontal, fill × fixed 64px)
├── nav-left (auto-layout horizontal, hug × hug)
│   ├── logo (32x32 or text logo)
│   └── text-brand (Inter SemiBold, 18px)
├── nav-center (auto-layout horizontal, hug × fill)
│   ├── nav-link (auto-layout horizontal, hug × fill)
│   │   ├── icon-nav (16x16, optional)
│   │   └── text-nav-label (Inter Medium, 14px)
│   ├── nav-link
│   ├── nav-link
│   └── nav-link
└── nav-right (auto-layout horizontal, hug × hug)
    ├── button-ghost (icon-only, search)
    ├── button-ghost (icon-only, theme toggle)
    └── button-primary (CTA)
```

---

### Modal / Dialog

Modals use vertical auto-layout with clearly separated header, body, and footer sections.

#### Overlay Background

Not auto-layout. A fill frame set to `#000000` at 50% opacity, with constraints set to left + right + top + bottom (full screen coverage).

#### Modal Container

| Property | sm (480px) | md (640px) | lg (800px) |
|---|---|---|---|
| Direction | Vertical | Vertical | Vertical |
| Padding | 0 | 0 | 0 |
| Spacing between items | 0 | 0 | 0 |
| Primary axis alignment | Top | Top | Top |
| Counter axis alignment | Center | Center | Center |
| Width resizing | Fixed 480px | Fixed 640px | Fixed 800px |
| Height resizing | Hug contents | Hug contents | Hug contents |
| Max height | 90vh (annotated) | 90vh | 90vh |
| Border radius | 12px | 12px | 16px |
| Clip content | Yes | Yes | Yes |

#### Modal Header

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 24px |
| Spacing between items | 16px |
| Primary axis alignment | Space between |
| Counter axis alignment | Center |
| Width resizing | Fill container |
| Height resizing | Hug contents |
| Border bottom | 1px `color-neutral-200` |

#### Modal Body

| Property | Value |
|---|---|
| Direction | Vertical |
| Padding | 24px |
| Spacing between items | 16px |
| Primary axis alignment | Top |
| Counter axis alignment | Stretch |
| Width resizing | Fill container |
| Height resizing | Hug contents (scrollable in implementation) |

#### Modal Footer

| Property | Value |
|---|---|
| Direction | Horizontal |
| Padding | 16px 24px |
| Spacing between items | 12px |
| Primary axis alignment | Right |
| Counter axis alignment | Center |
| Width resizing | Fill container |
| Height resizing | Hug contents |
| Border top | 1px `color-neutral-200` |

#### Layer Structure

```
modal-overlay (fill frame, not auto-layout)
├── bg-overlay (#000 50%)
└── modal-container (auto-layout vertical, fixed width × hug, centered)
    ├── modal-header (auto-layout horizontal, fill × hug)
    │   ├── header-content (auto-layout vertical, fill × hug)
    │   │   ├── text-title (Inter SemiBold, 18px)
    │   │   └── text-description (Inter Regular, 14px, optional)
    │   └── button-close (icon-only ghost button, 32x32)
    ├── modal-body (auto-layout vertical, fill × hug)
    │   └── [content slot]
    └── modal-footer (auto-layout horizontal, fill × hug)
        ├── spacer (fill)
        ├── button-secondary (Cancel)
        └── button-primary (Confirm)
```

---

### List Item

List items are horizontal auto-layout frames used inside vertical list containers.

#### List Container

| Property | Value |
|---|---|
| Direction | Vertical |
| Padding | 0 |
| Spacing between items | 0 (items separated by dividers or 1px border) |
| Width resizing | Fill container |
| Height resizing | Hug contents |

#### List Item

| Property | sm | md | lg |
|---|---|---|---|
| Direction | Horizontal | Horizontal | Horizontal |
| Padding top | 8px | 12px | 16px |
| Padding right | 16px | 16px | 24px |
| Padding bottom | 8px | 12px | 16px |
| Padding left | 16px | 16px | 24px |
| Spacing between items | 12px | 12px | 16px |
| Primary axis alignment | Left | Left | Left |
| Counter axis alignment | Center | Center | Center |
| Width resizing | Fill container | Fill container | Fill container |
| Height resizing | Hug contents | Hug contents | Hug contents |
| Min height | 40px | 48px | 56px |

#### Layer Structure

```
list-container (auto-layout vertical, fill × hug)
├── list-item (auto-layout horizontal, fill × hug)
│   ├── slot-leading (avatar, icon, or checkbox; fixed)
│   ├── content (auto-layout vertical, fill × hug)
│   │   ├── text-primary (Inter Medium, 14px/16px)
│   │   └── text-secondary (Inter Regular, 12px/14px, optional)
│   └── slot-trailing (auto-layout horizontal, hug × hug)
│       ├── text-meta (Inter Regular, 12px, optional)
│       └── icon-chevron (16x16, optional)
├── divider (1px, fill width, color-neutral-200)
├── list-item
├── divider
└── list-item
```

---

## Nested Auto-Layout Patterns

### Pattern 1: Horizontal Group Inside Vertical Stack

Common in: cards, modals, form sections.

```
parent (vertical)
├── header-row (horizontal, fill × hug)
│   ├── text-title (fill)
│   └── actions (hug)
├── content (vertical, fill × hug)
│   ├── paragraph (fill)
│   └── paragraph (fill)
└── footer-row (horizontal, fill × hug)
    ├── spacer (fill)
    └── button-group (horizontal, hug × hug, gap 12px)
```

### Pattern 2: Badge/Tag Group Wrapping

Figma does not support `flex-wrap` natively. Use the "Wrap" feature in auto-layout (available in Figma since 2023).

```
tag-group (horizontal, wrap, fill × hug)
├── badge (hug × hug)
├── badge (hug × hug)
├── badge (hug × hug)
├── badge (hug × hug)
└── badge (hug × hug)

Config:
  Direction:      Horizontal
  Wrap:           Enabled
  Spacing:        8px (horizontal), 8px (vertical)
  Width resizing: Fill container
  Height resizing: Hug contents
```

### Pattern 3: Sidebar + Main Content

```
page-body (horizontal, fill × fill)
├── sidebar (vertical, fixed 280px × fill)
│   ├── nav-section (vertical, fill × hug, gap 4px)
│   │   ├── text-section-label
│   │   ├── nav-item (horizontal, fill × hug)
│   │   ├── nav-item
│   │   └── nav-item
│   ├── nav-section
│   └── spacer (fill, pushes bottom items down)
│       └── nav-item-bottom (settings)
└── main-content (vertical, fill × hug)
    ├── page-header (vertical, fill × hug, padding 32px)
    ├── content-section (vertical, fill × hug, padding 0 32px)
    └── content-section
```

### Pattern 4: Form Layout (Stacked Fields)

```
form (vertical, fill × hug, gap 24px)
├── form-section (vertical, fill × hug, gap 16px)
│   ├── text-section-title (Inter SemiBold, 16px)
│   ├── field-row (horizontal, fill × hug, gap 16px)
│   │   ├── input-field (fill × hug)  -- first name
│   │   └── input-field (fill × hug)  -- last name
│   ├── input-field (fill × hug)       -- email (full width)
│   └── text-area (fill × hug)         -- message
├── form-section
└── form-actions (horizontal, fill × hug, gap 12px)
    ├── spacer (fill)
    ├── button-secondary (hug)
    └── button-primary (hug)
```

### Pattern 5: Responsive Card Grid (Using Wrap)

```
card-grid (horizontal, wrap, fill × hug)
├── card (fill, min-width 280px × hug)
├── card (fill, min-width 280px × hug)
├── card (fill, min-width 280px × hug)
├── card (fill, min-width 280px × hug)
├── card (fill, min-width 280px × hug)
└── card (fill, min-width 280px × hug)

Config:
  Direction:        Horizontal
  Wrap:             Enabled
  Spacing:          24px (horizontal), 24px (vertical)
  Width resizing:   Fill container
  Height resizing:  Hug contents

Note: At different breakpoints, designers should show the
actual column count explicitly in template frames. The wrap
behavior documents the intended responsive behavior for
developers.
```

---

## Resizing Behavior Quick Reference

| Resizing Mode | When to Use | Figma Behavior |
|---|---|---|
| **Fixed** | Exact dimensions required (icons, avatars, fixed-height headers) | Size does not change when parent resizes |
| **Hug contents** | Content determines size (buttons, badges, tooltips) | Shrinks to tightly fit children |
| **Fill container** | Element should stretch to fill available space (inputs, main content, card width) | Expands or contracts with parent |

### Common Resizing Combinations

| Component | Width | Height |
|---|---|---|
| Button (default) | Hug | Fixed |
| Button (full-width) | Fill | Fixed |
| Input field | Fill | Fixed |
| Card | Fill | Hug |
| Badge | Hug | Hug |
| Modal | Fixed | Hug (with max-height) |
| Nav bar | Fill | Fixed |
| List item | Fill | Hug (with min-height) |
| Avatar | Fixed | Fixed |
| Divider | Fill | Fixed (1px) |
| Sidebar | Fixed | Fill |
| Main content area | Fill | Hug or Fill |
| Spacer (push items apart) | Fill or Fixed 0px × Fill | Used to create space-between behavior |

---

## Alignment Quick Reference

| Scenario | Primary Axis | Counter Axis |
|---|---|---|
| Centered button text | Center | Center |
| Left-aligned form labels | Left | Top |
| Right-aligned modal actions | Right | Center |
| Nav bar logo and actions | Space between | Center |
| Stacked card content | Top | Stretch |
| Centered modal on overlay | Center | Center |
| List item with icon and text | Left | Center |
| Badge inside avatar | (use constraints, not AL) | -- |
