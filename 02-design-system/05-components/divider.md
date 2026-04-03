# Divider

## Overview

The Divider component creates a visual separation between content sections or list items. It helps establish hierarchy and grouping by providing a thin rule that can be horizontal or vertical, and optionally include a centered label or icon. Use dividers sparingly to avoid visual clutter -- whitespace alone is often sufficient.

---

## Anatomy

```
Horizontal (plain):
──────────────────────────────────────────────

Horizontal (with label):
──────────────────  Label  ──────────────────

Horizontal (with icon):
──────────────────  [icon]  ──────────────────

Vertical:
    │
    │
    │
    │

Vertical (with label):
    │
  Label
    │
```

| Part | Required | Description |
|------|----------|-------------|
| Rule | Yes | The visible line element (horizontal or vertical) |
| Label | No | Optional text centered on the divider |
| Icon | No | Optional icon centered on the divider |
| Container | Yes | Wrapper element that controls orientation and spacing |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Horizontal | Full-width horizontal rule | Separating stacked content sections |
| Vertical | Full-height vertical rule | Separating side-by-side elements (toolbars, panels) |
| With label | Divider with centered text | "OR" separators, section labels, "Read more" breaks |
| With icon | Divider with centered icon | Decorative breaks, themed section separators |
| Inset | Horizontal rule with left/right margin | List item separators that align with content, not edge |

---

## Styles

| Style | Description | Border Value | Use Case |
|-------|-------------|-------------|----------|
| Solid | Continuous line | `1px solid` | Default for most separations |
| Dashed | Evenly spaced dashes | `1px dashed` | Lighter visual weight, secondary separations |
| Dotted | Evenly spaced dots | `1px dotted` | Subtle separation, decorative contexts |
| Thick | Heavier solid line | `2px solid` | Strong section breaks, footer separation |

---

## States

| State | Appearance | Notes |
|-------|-----------|-------|
| Default | Neutral-300 rule | Standard resting state |
| Muted | Neutral-200 rule | Reduced emphasis for dense layouts |
| Accent | Primary blue-600 rule | Branded or highlighted section breaks |
| Dark mode | Neutral-600 rule | Adjusted for dark backgrounds |

---

## Sizing

### Horizontal

| Spacing | Margin Top/Bottom | Use Case |
|---------|-------------------|----------|
| none | 0 | Tight layouts, list items |
| sm | 8px | Between closely related items |
| md | 16px | Default section separation |
| lg | 24px | Major section breaks |
| xl | 32px | Page-level content separation |

### Vertical

| Spacing | Margin Left/Right | Min Height |
|---------|-------------------|------------|
| none | 0 | 100% of parent |
| sm | 8px | 16px |
| md | 16px | 24px |
| lg | 24px | 32px |

### Inset

| Inset | Left Margin | Right Margin |
|-------|-------------|--------------|
| start | 16px | 0 |
| end | 0 | 16px |
| both | 16px | 16px |
| icon-aligned | 56px | 0 |

### Label

| Property | Value |
|----------|-------|
| Font size | 12px (caption) |
| Font weight | 500 (medium) |
| Font family | Inter |
| Text color | neutral-500 |
| Horizontal padding | 16px (space between rule and label) |
| Text transform | uppercase (optional) |

---

## Accessibility

- **Role**: Use `role="separator"` for decorative dividers. For dividers with labels that convey meaning, use `role="separator"` with an `aria-label` or let the visible text serve as the accessible name.
- **ARIA**: When vertical, include `aria-orientation="vertical"`. Horizontal is the default orientation and does not require explicit declaration.
- **Semantic HTML**: Prefer the `<hr>` element for horizontal dividers; it carries implicit `role="separator"`.
- **Screen reader**: Decorative dividers (pure visual separation) may use `aria-hidden="true"` if the separation is already conveyed through heading hierarchy or whitespace.
- **Color**: The divider rule must have at least 3:1 contrast ratio against its background to meet WCAG non-text contrast requirements.
- **Focus**: Dividers are not focusable and should not appear in the tab order.

---

## Design Tokens

```json
{
  "divider": {
    "color-default": "{color.neutral.300}",
    "color-muted": "{color.neutral.200}",
    "color-accent": "{color.primary.600}",
    "color-dark": "{color.neutral.600}",
    "width": "1px",
    "width-thick": "2px",
    "style": "solid",
    "spacing-none": "0",
    "spacing-sm": "{space.2}",
    "spacing-md": "{space.4}",
    "spacing-lg": "{space.6}",
    "spacing-xl": "{space.8}",
    "label-font-size": "{typography.caption.size}",
    "label-font-weight": "500",
    "label-color": "{color.neutral.500}",
    "label-padding-x": "{space.4}",
    "inset-start": "{space.4}",
    "inset-icon-aligned": "56px"
  }
}
```

---

## Usage Guidelines

**Do:**
- Use horizontal dividers to separate distinct content groups within a page section.
- Use vertical dividers in toolbars, navigation bars, or inline element groups.
- Use the label variant for "OR" separators in authentication forms or logical breaks in content.
- Pair divider spacing with the layout spacing scale for consistency.
- Prefer the inset variant for list items so the rule aligns with text, not leading icons.

**Don't:**
- Use dividers between every element -- rely on whitespace and grouping first.
- Stack multiple dividers without content between them.
- Use accent-colored dividers for purely decorative separation; reserve color for meaning.
- Place dividers inside components that already have clear visual boundaries (cards, modals).
- Use thick dividers for list items; reserve thick style for major section breaks only.

---

## Code Example

### HTML

```html
<!-- Basic horizontal divider -->
<hr class="ff-divider" />

<!-- Horizontal with spacing -->
<hr class="ff-divider ff-divider--spacing-md" />

<!-- Dashed style -->
<hr class="ff-divider ff-divider--dashed ff-divider--spacing-lg" />

<!-- With label -->
<div class="ff-divider ff-divider--label ff-divider--spacing-md" role="separator">
  <span class="ff-divider__rule"></span>
  <span class="ff-divider__label">OR</span>
  <span class="ff-divider__rule"></span>
</div>

<!-- Vertical divider -->
<div class="ff-divider ff-divider--vertical ff-divider--spacing-sm"
     role="separator" aria-orientation="vertical"></div>

<!-- Inset divider for lists -->
<li class="ff-list-item">Item one</li>
<hr class="ff-divider ff-divider--inset-start" />
<li class="ff-list-item">Item two</li>
```

### JSX

```jsx
import { Divider } from '@flaviofusuma/ui';

{/* Basic horizontal */}
<Divider />

{/* With spacing and style */}
<Divider spacing="md" style="dashed" />

{/* With label */}
<Divider spacing="md" label="OR" />

{/* With icon */}
<Divider spacing="lg" icon={<StarIcon />} />

{/* Vertical */}
<Divider orientation="vertical" spacing="sm" />

{/* Accent color, thick */}
<Divider color="accent" weight="thick" spacing="xl" />

{/* Inset for list context */}
<List>
  <ListItem>Item one</ListItem>
  <Divider inset="start" />
  <ListItem>Item two</ListItem>
</List>
```

---

## Related Components

- [Section Header](/02-design-system/05-components/section-header.md) -- Often used above or below a divider to introduce new content sections.
- [Card](/02-design-system/05-components/project-card.md) -- Cards provide built-in visual separation; avoid adding dividers between cards.
- [List](/02-design-system/05-components/list.md) -- Lists commonly use inset dividers between items.
- [Footer](/02-design-system/05-components/footer.md) -- Thick dividers may appear above the footer to separate it from page content.
