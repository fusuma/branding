# Component Template

> This template defines the standard documentation structure for all components in the Flavio Fusuma Design System. Every component file should follow this format to ensure consistency across the library.

---

## [Component Name]

### Overview
_1–3 sentences describing what the component is, its primary use case, and when to use it._

### Anatomy

```
┌──────────────────────────────────┐
│ [Container]                       │
│  ┌────┐                          │
│  │Icon│  [Label]    [Action]     │
│  └────┘                          │
│         [Supporting text]         │
└──────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | The outer wrapper element |
| Label | Yes | Primary text content |
| Icon | No | Optional leading/trailing icon |
| Action | No | Optional interactive element |
| Supporting text | No | Secondary descriptive text |

### Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Primary | Default brand appearance | Primary actions, key interactions |
| Secondary | Subdued appearance | Supporting actions |
| Ghost | Transparent background | Tertiary actions, toolbar items |
| Danger | Error/destructive styling | Delete, remove, destructive actions |

### States

| State | Background | Border | Text | Shadow | Notes |
|-------|-----------|--------|------|--------|-------|
| Default | `{token}` | `{token}` | `{token}` | none | Resting state |
| Hover | `{token}` | `{token}` | `{token}` | none | Mouse over |
| Active/Pressed | `{token}` | `{token}` | `{token}` | none | Mouse down |
| Focus | `{token}` | `{token}` | `{token}` | focus ring | Keyboard focus |
| Disabled | `{token}` | `{token}` | `{token}` | none | Non-interactive |
| Loading | `{token}` | `{token}` | `{token}` | none | Async operation |

### Sizing

| Size | Height | Padding | Font Size | Icon Size | Min Width |
|------|--------|---------|-----------|-----------|-----------|
| sm | 32px | 8px 12px | 14px | 16px | 64px |
| md | 40px | 10px 16px | 16px | 20px | 80px |
| lg | 48px | 12px 24px | 18px | 24px | 96px |

### Accessibility

- **Role**: `role="..."` or semantic HTML element
- **ARIA**: Required ARIA attributes
- **Keyboard**: Tab order, Enter/Space behavior, Escape handling
- **Screen reader**: Announced name and state
- **Focus**: Visible focus indicator meeting WCAG 2.1
- **Color**: Does not rely on color alone to convey meaning
- **Motion**: Respects `prefers-reduced-motion`

### Design Tokens

```json
{
  "component-name": {
    "background": "{color.surface.primary}",
    "border-color": "{color.border.default}",
    "border-radius": "{border.radius.md}",
    "text-color": "{color.text.primary}",
    "font-size": "{typography.body.md.size}",
    "padding-x": "{space.4}",
    "padding-y": "{space.2}"
  }
}
```

### Usage Guidelines

**Do:**
- Use for [appropriate context]
- Pair with [complementary component]
- Limit to [recommended quantity] per view

**Don't:**
- Use for [inappropriate context]
- Nest inside [incompatible component]
- Override token values with custom colors

### Code Example

```html
<div class="ff-component ff-component--primary ff-component--md">
  <span class="ff-component__icon"><!-- icon --></span>
  <span class="ff-component__label">Label</span>
</div>
```

```jsx
<Component variant="primary" size="md" icon={<Icon />}>
  Label
</Component>
```

### Related Components
- [Related Component 1] — for similar but different use case
- [Related Component 2] — often used together
