# Component System Architecture

> Naming conventions, variant structure, component properties, composition strategies, and complete variant matrices for the Flavio Fusuma Design System in Figma.

---

## Naming Convention

### Component Naming Pattern

All components follow a three-level naming hierarchy using the `/` delimiter:

```
[Category] / [Component] / [Variant]
```

The forward slash creates Figma's nested menu structure, making components easy to discover in the assets panel and instance swap menus.

### Category Groups

| Category | Description | Examples |
|---|---|---|
| `Action` | Interactive elements that trigger operations | Button, Icon Button, FAB, Toggle |
| `Input` | Form controls for data entry | Text Input, Textarea, Select, Checkbox, Radio, Switch, Slider |
| `Display` | Elements that present information | Badge, Tag, Avatar, Tooltip, Card, Table |
| `Feedback` | System-to-user communication | Alert, Toast, Progress, Skeleton, Spinner |
| `Navigation` | Wayfinding elements | Nav Bar, Sidebar, Breadcrumb, Tab, Pagination, Link |
| `Layout` | Structural containers | Divider, Section, Container, Modal, Drawer |
| `_Utility` | Internal components not published to the library | Status Label, Annotation, Redline, Spacer |

### Full Naming Examples

```
Action / Button / Primary
Action / Button / Secondary
Action / Button / Outline
Action / Button / Ghost
Action / Button / Danger
Action / Button / Link
Action / Icon Button / Primary
Action / Toggle / Default

Input / Text Input / Default
Input / Textarea / Default
Input / Select / Default
Input / Checkbox / Default
Input / Radio / Default
Input / Switch / Default

Display / Badge / Filled
Display / Badge / Outline
Display / Tag / Default
Display / Avatar / Image
Display / Avatar / Initials
Display / Avatar / Fallback
Display / Card / Default
Display / Tooltip / Top

Feedback / Alert / Info
Feedback / Alert / Success
Feedback / Alert / Warning
Feedback / Alert / Error
Feedback / Toast / Default
Feedback / Progress / Linear
Feedback / Progress / Circular
Feedback / Skeleton / Text
Feedback / Skeleton / Rectangle

Navigation / Nav Bar / Desktop
Navigation / Nav Bar / Mobile
Navigation / Sidebar / Default
Navigation / Breadcrumb / Default
Navigation / Tab / Default
Navigation / Pagination / Default

Layout / Divider / Horizontal
Layout / Modal / Default
Layout / Drawer / Left

_Utility / Status Label
_Utility / Annotation / Spacing
_Utility / Annotation / Anatomy
```

---

## Variant Properties

### Property Types

Figma supports four component property types. Each serves a specific role in the Flavio Fusuma system.

| Property Type | Purpose | Usage |
|---|---|---|
| **Variant** | Switches between visual states | Type (primary/secondary), size (sm/md/lg), state (default/hover/focus/disabled) |
| **Boolean** | Shows or hides a layer | `hasIcon`, `hasAvatar`, `hasBadge`, `hasDescription` |
| **Text** | Exposes text for quick editing | `label`, `description`, `helperText`, `placeholder` |
| **Instance Swap** | Swaps a nested component instance | `iconLeading`, `iconTrailing`, `slotMedia`, `slotAction` |

### Naming Rules for Properties

- Variant properties: `PascalCase` (e.g., `Type`, `Size`, `State`)
- Boolean properties: `camelCase` with `has` prefix (e.g., `hasIcon`, `hasDescription`)
- Text properties: `camelCase` (e.g., `label`, `helperText`)
- Instance swap properties: `camelCase` with contextual name (e.g., `iconLeading`, `slotAction`)

### Standard Variant Properties

These properties are shared across multiple components. Using consistent names and values enables bulk editing and scripting.

| Property | Values | Used In |
|---|---|---|
| `Type` | primary, secondary, outline, ghost, danger, link | Button, Icon Button |
| `Type` | info, success, warning, error | Alert, Toast, Badge |
| `Type` | filled, outline, subtle | Badge, Tag |
| `Size` | sm, md, lg | Button, Input, Avatar, Badge, Modal |
| `State` | default, hover, focus, active, disabled | Button, Input, Checkbox, Radio, Switch, Link |
| `State` | default, error, success | Input, Textarea, Select |

---

## Variant Matrix: Button

### Properties

| Property | Type | Values |
|---|---|---|
| `Type` | Variant | primary, secondary, outline, ghost, danger, link |
| `Size` | Variant | sm, md, lg |
| `State` | Variant | default, hover, focus, active, disabled, loading |
| `hasIconLeading` | Boolean | true, false |
| `hasIconTrailing` | Boolean | true, false |
| `label` | Text | "Button" |
| `iconLeading` | Instance Swap | Icon instance (default: placeholder) |
| `iconTrailing` | Instance Swap | Icon instance (default: chevron-right) |

### Variant Count

6 types x 3 sizes x 6 states = **108 variants** (before boolean toggles)

### Variant Matrix (Type x State, at md size)

| | default | hover | focus | active | disabled | loading |
|---|---|---|---|---|---|---|
| **primary** | blue-600 bg, white text | blue-700 bg | blue-600 bg, focus ring | blue-800 bg | blue-600 bg, 40% opacity | blue-600 bg, spinner |
| **secondary** | neutral-100 bg, neutral-900 text | neutral-200 bg | neutral-100 bg, focus ring | neutral-300 bg | neutral-100 bg, 40% opacity | neutral-100 bg, spinner |
| **outline** | transparent bg, blue-600 border+text | blue-50 bg | transparent bg, focus ring | blue-100 bg | transparent bg, 40% opacity | transparent bg, spinner |
| **ghost** | transparent bg, blue-600 text | blue-50 bg | transparent bg, focus ring | blue-100 bg | transparent bg, 40% opacity | transparent bg, spinner |
| **danger** | red-600 bg, white text | red-700 bg | red-600 bg, focus ring | red-800 bg | red-600 bg, 40% opacity | red-600 bg, spinner |
| **link** | transparent, blue-600 underline | blue-700 text | blue-600 text, focus ring | blue-800 text | 40% opacity | text replaced with spinner |

---

## Variant Matrix: Input (Text Input)

### Properties

| Property | Type | Values |
|---|---|---|
| `Size` | Variant | sm, md, lg |
| `State` | Variant | default, hover, focus, filled, disabled, error, success |
| `hasLabel` | Boolean | true, false |
| `hasHelperText` | Boolean | true, false |
| `hasPrefix` | Boolean | true, false |
| `hasSuffix` | Boolean | true, false |
| `hasCharacterCount` | Boolean | true, false |
| `isRequired` | Boolean | true, false |
| `label` | Text | "Label" |
| `placeholder` | Text | "Placeholder" |
| `helperText` | Text | "Helper text" |
| `slotPrefix` | Instance Swap | Icon or text |
| `slotSuffix` | Instance Swap | Icon, button, or text |

### Variant Count

3 sizes x 7 states = **21 variants** (before boolean toggles)

### Variant Matrix (Size x State)

| | default | hover | focus | filled | disabled | error | success |
|---|---|---|---|---|---|---|---|
| **sm** | neutral-300 border | neutral-400 border | blue-600 border, ring | neutral-300 border, dark text | neutral-200 bg, 50% opacity | red-500 border, red helper | green-500 border, green helper |
| **md** | neutral-300 border | neutral-400 border | blue-600 border, ring | neutral-300 border, dark text | neutral-200 bg, 50% opacity | red-500 border, red helper | green-500 border, green helper |
| **lg** | neutral-300 border | neutral-400 border | blue-600 border, ring | neutral-300 border, dark text | neutral-200 bg, 50% opacity | red-500 border, red helper | green-500 border, green helper |

---

## Variant Matrix: Card

### Properties

| Property | Type | Values |
|---|---|---|
| `Type` | Variant | default, elevated, outline |
| `hasMedia` | Boolean | true, false |
| `hasFooter` | Boolean | true, false |
| `hasBadge` | Boolean | true, false |
| `hasDescription` | Boolean | true, false |
| `title` | Text | "Card Title" |
| `description` | Text | "Card description text..." |
| `slotMedia` | Instance Swap | Image placeholder |
| `slotAction` | Instance Swap | Button instance |

### Variant Matrix (Type x Booleans at key combinations)

| Type | With Media | Without Media | With Footer | Without Footer |
|---|---|---|---|---|
| **default** | neutral-200 bg, border | neutral-200 bg, border | action buttons shown | content only |
| **elevated** | white bg, elevation-2 shadow | white bg, elevation-2 shadow | action buttons shown | content only |
| **outline** | white bg, neutral-300 border | white bg, neutral-300 border | action buttons shown | content only |

---

## Variant Matrix: Badge

### Properties

| Property | Type | Values |
|---|---|---|
| `Type` | Variant | filled, outline, subtle |
| `Color` | Variant | neutral, primary, success, warning, error, info |
| `Size` | Variant | sm, md, lg |
| `hasDot` | Boolean | true, false |
| `hasRemove` | Boolean | true, false |
| `label` | Text | "Badge" |

### Variant Count

3 types x 6 colors x 3 sizes = **54 variants**

### Variant Matrix (Type x Color, at md size)

| | neutral | primary | success | warning | error | info |
|---|---|---|---|---|---|---|
| **filled** | neutral-600 bg, white text | blue-600 bg, white text | green-600 bg, white text | amber-500 bg, neutral-900 text | red-600 bg, white text | sky-600 bg, white text |
| **outline** | neutral-600 border+text | blue-600 border+text | green-600 border+text | amber-500 border+text | red-600 border+text | sky-600 border+text |
| **subtle** | neutral-100 bg, neutral-700 text | blue-50 bg, blue-700 text | green-50 bg, green-700 text | amber-50 bg, amber-700 text | red-50 bg, red-700 text | sky-50 bg, sky-700 text |

---

## Variant Matrix: Alert

### Properties

| Property | Type | Values |
|---|---|---|
| `Type` | Variant | info, success, warning, error |
| `hasTitle` | Boolean | true, false |
| `hasDescription` | Boolean | true, false |
| `hasDismiss` | Boolean | true, false |
| `hasAction` | Boolean | true, false |
| `title` | Text | "Alert title" |
| `description` | Text | "Alert description message..." |
| `actionLabel` | Text | "Action" |

### Variant Matrix (Type x Structure)

| | With Title + Description | Title Only | Description Only |
|---|---|---|---|
| **info** | blue-50 bg, blue-600 icon, blue-800 title, blue-700 body | blue-50 bg, blue-800 title | blue-50 bg, blue-700 body |
| **success** | green-50 bg, green-600 icon, green-800 title, green-700 body | green-50 bg, green-800 title | green-50 bg, green-700 body |
| **warning** | amber-50 bg, amber-600 icon, amber-800 title, amber-700 body | amber-50 bg, amber-800 title | amber-50 bg, amber-700 body |
| **error** | red-50 bg, red-600 icon, red-800 title, red-700 body | red-50 bg, red-800 title | red-50 bg, red-700 body |

---

## Base Component vs. Composed Component Strategy

### Base Components

Base components are the atomic building blocks. They are self-contained, fully variant-ized, and published to the shared library.

| Base Component | Published | Variants | Notes |
|---|---|---|---|
| Button | Yes | 108+ | All types, sizes, states |
| Icon Button | Yes | 54+ | Square variant of button |
| Input | Yes | 21+ | All sizes, states |
| Textarea | Yes | 21+ | Mirrors input variants |
| Select | Yes | 21+ | Mirrors input variants |
| Checkbox | Yes | 12+ | Sizes, states, indeterminate |
| Radio | Yes | 9+ | Sizes, states |
| Switch | Yes | 12+ | Sizes, states |
| Badge | Yes | 54+ | Types, colors, sizes |
| Tag | Yes | 36+ | Types, colors, sizes |
| Avatar | Yes | 15+ | Types, sizes |
| Tooltip | Yes | 8+ | Directions |
| Divider | Yes | 2 | Horizontal, vertical |
| Spinner | Yes | 3 | Sizes |
| Skeleton | Yes | 4 | Types |

### Composed Components

Composed components combine multiple base components into higher-order UI elements. They use instance swap slots to accept different base components.

| Composed Component | Composed From | Published |
|---|---|---|
| Card | Image + Text + Badge + Button | Yes |
| Alert | Icon + Text + Button (dismiss) | Yes |
| Toast | Icon + Text + Button + Progress | Yes |
| Modal | Text + Button + Divider + (body slot) | Yes |
| Drawer | Nav items + Divider + Avatar | Yes |
| Nav Bar | Logo + Nav Link + Button + Avatar | Yes |
| Sidebar | Nav items + Divider + Badge | Yes |
| Breadcrumb | Link + Icon (separator) | Yes |
| Tab Group | Tab items + Divider | Yes |
| Table Row | Checkbox + Text + Badge + Button | Yes |
| Pagination | Button + Text | Yes |
| Form Field | Label + Input/Select/Textarea + Helper | Yes |
| List Item | Avatar/Icon + Text + Badge + Icon | Yes |
| Search | Input + Button | Yes |
| Menu | List Items + Dividers | Yes |
| Dropdown | Button (trigger) + Menu | Yes |

---

## Slot Pattern for Flexible Composition

Slots are instance-swap properties that allow designers to inject different components into predefined positions.

### Slot Naming Convention

```
slot-[position]-[purpose]
```

| Slot Name | Used In | Accepts |
|---|---|---|
| `slotLeading` | List item, Nav item | Icon, Avatar, Checkbox |
| `slotTrailing` | List item, Nav item | Badge, Icon, Switch |
| `slotMedia` | Card | Image, Video placeholder, Illustration |
| `slotAction` | Card footer, Alert, Toast | Button, Link, Icon Button |
| `slotPrefix` | Input, Select | Icon, Text |
| `slotSuffix` | Input, Select | Icon, Button, Text |
| `slotBody` | Modal, Drawer | Any composed content |
| `slotHeader` | Card, Modal | Custom header content |
| `slotFooter` | Card, Modal | Button group, link row |
| `iconLeading` | Button, Nav link, Menu item | Any icon |
| `iconTrailing` | Button, Nav link, Menu item | Any icon |

### Creating a Slot in Figma

1. Create a placeholder component: `_Utility / Slot / [Name]` (e.g., a 24x24 rectangle with a dashed border).
2. Place the placeholder instance inside the parent component where the slot belongs.
3. Name the layer matching the slot name (e.g., `slot-leading`).
4. Add an instance swap property to the parent component, targeting the slot layer.
5. Set the preferred values for the instance swap to limit suggestions to relevant components.

### Slot Placeholder Visual

```
┌ ─ ─ ─ ─ ┐
│  24x24   │   Dashed border, color-neutral-300
│   Slot   │   Used to indicate swappable area
└ ─ ─ ─ ─ ┘
```

---

## Component Property Configuration Examples

### Button: Complete Property List

```yaml
Properties:
  - name: Type
    type: Variant
    values: [primary, secondary, outline, ghost, danger, link]
    default: primary

  - name: Size
    type: Variant
    values: [sm, md, lg]
    default: md

  - name: State
    type: Variant
    values: [default, hover, focus, active, disabled, loading]
    default: default

  - name: hasIconLeading
    type: Boolean
    default: false

  - name: hasIconTrailing
    type: Boolean
    default: false

  - name: label
    type: Text
    default: "Button"
    layer: text-label

  - name: iconLeading
    type: Instance Swap
    default: _Utility / Slot / Icon
    layer: icon-leading
    preferredValues: [Icon / *]

  - name: iconTrailing
    type: Instance Swap
    default: _Utility / Slot / Icon
    layer: icon-trailing
    preferredValues: [Icon / *]
```

### Input: Complete Property List

```yaml
Properties:
  - name: Size
    type: Variant
    values: [sm, md, lg]
    default: md

  - name: State
    type: Variant
    values: [default, hover, focus, filled, disabled, error, success]
    default: default

  - name: hasLabel
    type: Boolean
    default: true

  - name: hasHelperText
    type: Boolean
    default: false

  - name: hasPrefix
    type: Boolean
    default: false

  - name: hasSuffix
    type: Boolean
    default: false

  - name: hasCharacterCount
    type: Boolean
    default: false

  - name: isRequired
    type: Boolean
    default: false

  - name: label
    type: Text
    default: "Label"
    layer: text-label

  - name: placeholder
    type: Text
    default: "Placeholder"
    layer: text-placeholder

  - name: helperText
    type: Text
    default: "Helper text"
    layer: text-helper

  - name: slotPrefix
    type: Instance Swap
    default: _Utility / Slot / Prefix
    layer: slot-prefix

  - name: slotSuffix
    type: Instance Swap
    default: _Utility / Slot / Suffix
    layer: slot-suffix
```

---

## Component Organization in the Assets Panel

When published, components appear in the assets panel grouped by category. The `/` delimiter creates the folder structure.

```
Assets Panel
├── Action
│   ├── Button
│   │   ├── Primary
│   │   ├── Secondary
│   │   ├── Outline
│   │   ├── Ghost
│   │   ├── Danger
│   │   └── Link
│   ├── Icon Button
│   │   ├── Primary
│   │   └── ...
│   ├── FAB
│   └── Toggle
├── Input
│   ├── Text Input
│   ├── Textarea
│   ├── Select
│   ├── Checkbox
│   ├── Radio
│   ├── Switch
│   └── Slider
├── Display
│   ├── Avatar
│   ├── Badge
│   ├── Card
│   ├── Tag
│   ├── Tooltip
│   └── Table
├── Feedback
│   ├── Alert
│   ├── Toast
│   ├── Progress
│   ├── Skeleton
│   └── Spinner
├── Navigation
│   ├── Nav Bar
│   ├── Sidebar
│   ├── Breadcrumb
│   ├── Tab
│   ├── Pagination
│   └── Link
└── Layout
    ├── Divider
    ├── Modal
    ├── Drawer
    └── Section
```

Components prefixed with `_` (e.g., `_Utility / Status Label`) are not published to the library and remain local to the file.

---

## Component Documentation in Figma

Every component set in Figma should include a description field. Use this format:

```
[One-line description]

Variants: [list variant properties]
Slots: [list instance swap properties]
Tokens: [list key tokens used]

See: 02-design-system/05-components/[component].md
```

Example for Button:

```
Primary interactive element for triggering actions.

Variants: Type (primary/secondary/outline/ghost/danger/link), Size (sm/md/lg), State (default/hover/focus/active/disabled/loading)
Slots: iconLeading, iconTrailing
Tokens: color-primary-*, radius-md, font-weight-semibold

See: 02-design-system/05-components/buttons.md
```
