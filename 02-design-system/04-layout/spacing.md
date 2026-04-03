# Spacing System

The Flavio Fusuma spacing system is built on an 8px base unit. Every margin, padding, and gap value in the system is derived from this base, producing a consistent visual rhythm across all components and layouts.

---

## Spacing Scale

The scale provides 25 named tokens from `space-0` to `space-24`, covering values from 0 to 192px. Steps are linear at the small end and progressively larger at the high end.

| Token | Multiplier | Value (px) | Value (rem) | Common Use |
|---|---|---|---|---|
| `space-0` | 0x | 0px | 0rem | Reset spacing, zero-gap layouts |
| `space-px` | -- | 1px | 0.0625rem | Hairline borders, subtle offsets |
| `space-0.5` | 0.5x | 4px | 0.25rem | Inline icon-to-text gap, tight badge padding |
| `space-1` | 1x | 8px | 0.5rem | Compact element padding, icon spacing |
| `space-1.5` | 1.5x | 12px | 0.75rem | Small padding, tight form field gaps |
| `space-2` | 2x | 16px | 1rem | Standard small padding, input padding, tight card padding |
| `space-2.5` | 2.5x | 20px | 1.25rem | Medium-small gap |
| `space-3` | 3x | 24px | 1.5rem | Standard gap, paragraph spacing, card padding |
| `space-3.5` | 3.5x | 28px | 1.75rem | Medium gap |
| `space-4` | 4x | 32px | 2rem | Large card padding, section gap (small) |
| `space-5` | 5x | 40px | 2.5rem | Section padding (compact) |
| `space-6` | 6x | 48px | 3rem | Section padding (standard) |
| `space-7` | 7x | 56px | 3.5rem | Large section gap |
| `space-8` | 8x | 64px | 4rem | Page section padding |
| `space-9` | 9x | 72px | 4.5rem | Large page section gap |
| `space-10` | 10x | 80px | 5rem | Major section divider |
| `space-11` | 11x | 88px | 5.5rem | Large section padding |
| `space-12` | 12x | 96px | 6rem | Hero section padding |
| `space-14` | 14x | 112px | 7rem | Extra-large section gap |
| `space-16` | 16x | 128px | 8rem | Page-level vertical spacing |
| `space-18` | 18x | 144px | 9rem | Major layout gap |
| `space-20` | 20x | 160px | 10rem | Hero/banner padding |
| `space-22` | 22x | 176px | 11rem | Extra-large layout gap |
| `space-24` | 24x | 192px | 12rem | Maximum defined spacing |

---

## Usage Guidelines

### Padding

Padding creates internal space within a component.

| Component Type | Recommended Padding | Token |
|---|---|---|
| Inline badge, tag | 4px vertical, 8px horizontal | `space-0.5` / `space-1` |
| Small button | 8px vertical, 16px horizontal | `space-1` / `space-2` |
| Default button | 10px vertical, 20px horizontal | `space-1.5` / `space-2.5` |
| Large button | 12px vertical, 24px horizontal | `space-1.5` / `space-3` |
| Input field | 10px vertical, 12px horizontal | `space-1.5` |
| Card (compact) | 16px all sides | `space-2` |
| Card (standard) | 24px all sides | `space-3` |
| Card (spacious) | 32px all sides | `space-4` |
| Modal body | 24px horizontal, 24px vertical | `space-3` |
| Page section | 48px vertical, grid margin horizontal | `space-6` |
| Hero section | 96px vertical | `space-12` |

### Margin

Margin creates external space between components. Prefer gap in flex/grid layouts; use margin for stacking outside of grid contexts.

| Relationship | Recommended Margin | Token |
|---|---|---|
| Between inline elements (icon + text) | 8px | `space-1` |
| Between form fields | 16px | `space-2` |
| Between a label and its input | 8px | `space-1` |
| Between paragraphs | 24px | `space-3` |
| Between a heading and its body text | 16px-24px | `space-2` / `space-3` |
| Between cards in a grid | Use grid gap | `space-3` or `space-4` |
| Between page sections | 48px-96px | `space-6` to `space-12` |
| Between a section heading and section edge | 32px-48px | `space-4` / `space-6` |

### Gap (Flex and Grid)

The `gap` property is the preferred way to space children in flex and grid layouts. It replaces margin-based spacing between siblings.

| Layout Type | Recommended Gap | Token |
|---|---|---|
| Icon bar / action group | 8px | `space-1` |
| Horizontal button group | 12px | `space-1.5` |
| Form fields (vertical stack) | 16px | `space-2` |
| Card grid | 24px | `space-3` |
| Page-level grid gutter | 24px-32px | `space-3` / `space-4` |
| Section stack (vertical) | 48px-64px | `space-6` / `space-8` |

---

## Spacing Application Guide

### Component Anatomy

This guide shows how spacing tokens map to the anatomy of common UI patterns.

#### Card

```
+------------------------------------------------------+
|  space-3 (24px padding)                              |
|  +--------------------------------------------------+|
|  |  [Overline]                                      ||
|  |  space-1 (8px)                                   ||
|  |  [Heading]                                       ||
|  |  space-2 (16px)                                  ||
|  |  [Body text paragraph that may wrap to           ||
|  |   multiple lines with relaxed line height]       ||
|  |  space-3 (24px)                                  ||
|  |  [Button]          [Secondary Button]            ||
|  |          space-1.5 (12px gap between buttons)    ||
|  +--------------------------------------------------+|
|                                                      |
+------------------------------------------------------+
```

| Part | Property | Token | Value |
|---|---|---|---|
| Card outer padding | padding | `space-3` | 24px |
| Overline to heading | margin-top | `space-1` | 8px |
| Heading to body | margin-top | `space-2` | 16px |
| Body to action row | margin-top | `space-3` | 24px |
| Between action buttons | gap | `space-1.5` | 12px |

#### Form Field

```
[Label]                     <- heading-sm or body-sm weight 500
  space-1 (8px)
+----------------------------+
|  space-1.5 (12px padding)  |  <- Input field
+----------------------------+
  space-0.5 (4px)
[Helper text or error]       <- caption
  space-2 (16px)
[Next field label]
```

| Part | Property | Token | Value |
|---|---|---|---|
| Label to input | margin-bottom | `space-1` | 8px |
| Input internal padding | padding | `space-1.5` | 12px |
| Input to helper text | margin-top | `space-0.5` | 4px |
| Field to next field | margin-bottom | `space-2` | 16px |

#### Navigation Bar

```
+--------------------------------------------------------------+
|  space-2 (16px vertical padding)                             |
|  [Logo]  space-4 (32px)  [Nav Item]  space-3 (24px)  [Nav]  |
+--------------------------------------------------------------+
```

| Part | Property | Token | Value |
|---|---|---|---|
| Navbar vertical padding | padding-y | `space-2` | 16px |
| Logo to first nav item | gap / margin | `space-4` | 32px |
| Between nav items | gap | `space-3` | 24px |

#### Modal Dialog

```
+-----------------------------------------+
|  space-3 (24px)                         |
|  [Title]               [Close button]   |
|  space-2 (16px)                         |
|  -------- divider --------              |
|  space-3 (24px)                         |
|  [Body content]                         |
|  space-3 (24px)                         |
|  -------- divider --------              |
|  space-2 (16px)                         |
|  [Cancel]                    [Confirm]  |
|            space-1.5 (12px)             |
|  space-3 (24px)                         |
+-----------------------------------------+
```

| Part | Property | Token | Value |
|---|---|---|---|
| Modal padding (all sides) | padding | `space-3` | 24px |
| Title to divider | margin-bottom | `space-2` | 16px |
| Divider to body | margin-top | `space-3` | 24px |
| Body to footer divider | margin-bottom | `space-3` | 24px |
| Divider to action buttons | margin-top | `space-2` | 16px |
| Between action buttons | gap | `space-1.5` | 12px |

#### Page Section

```
                    space-8 (64px) to space-12 (96px)
+--------------------------------------------------------------+
|  space-6 (48px vertical padding)                             |
|                                                              |
|  [Section Heading]                                           |
|  space-3 (24px)                                              |
|  [Section content / card grid]                               |
|                                                              |
|  space-6 (48px vertical padding)                             |
+--------------------------------------------------------------+
                    space-8 (64px) to space-12 (96px)
```

---

## Responsive Spacing

Spacing tokens remain constant across breakpoints -- `space-3` is always 24px. However, the _choice_ of which token to use may change at different breakpoints.

### Common Responsive Adjustments

| Element | Mobile Token | Desktop Token | Rationale |
|---|---|---|---|
| Page section padding (vertical) | `space-6` (48px) | `space-12` (96px) | Less padding needed on small screens |
| Card padding | `space-2` (16px) | `space-3` (24px) | Conserve horizontal space on mobile |
| Card grid gap | `space-2` (16px) | `space-3` (24px) | Tighter grid on mobile |
| Modal padding | `space-2` (16px) | `space-3` (24px) | Modal is smaller on mobile |
| Section heading to content | `space-2` (16px) | `space-3` (24px) | Proportional to section size |

### Implementation

```css
.page-section {
  padding-top: var(--space-6);     /* 48px */
  padding-bottom: var(--space-6);
}

@media (min-width: 1024px) {
  .page-section {
    padding-top: var(--space-12);  /* 96px */
    padding-bottom: var(--space-12);
  }
}
```

---

## CSS Custom Properties

```css
:root {
  --space-0: 0px;
  --space-px: 1px;
  --space-0-5: 0.25rem;   /* 4px */
  --space-1: 0.5rem;      /* 8px */
  --space-1-5: 0.75rem;   /* 12px */
  --space-2: 1rem;        /* 16px */
  --space-2-5: 1.25rem;   /* 20px */
  --space-3: 1.5rem;      /* 24px */
  --space-3-5: 1.75rem;   /* 28px */
  --space-4: 2rem;        /* 32px */
  --space-5: 2.5rem;      /* 40px */
  --space-6: 3rem;        /* 48px */
  --space-7: 3.5rem;      /* 56px */
  --space-8: 4rem;        /* 64px */
  --space-9: 4.5rem;      /* 72px */
  --space-10: 5rem;       /* 80px */
  --space-11: 5.5rem;     /* 88px */
  --space-12: 6rem;       /* 96px */
  --space-14: 7rem;       /* 112px */
  --space-16: 8rem;       /* 128px */
  --space-18: 9rem;       /* 144px */
  --space-20: 10rem;      /* 160px */
  --space-22: 11rem;      /* 176px */
  --space-24: 12rem;      /* 192px */
}
```

---

## Guidelines

### Do

- Always use spacing tokens; never hard-code pixel values.
- Use `gap` instead of margin for spacing children in flex/grid containers.
- Keep spacing proportional: larger elements get larger spacing.
- Use consistent padding within component variants (all cards should use the same padding at the same size).

### Don't

- Don't use values between scale steps (e.g., 18px, 22px, 36px).
- Don't mix margin and gap on the same axis in the same container.
- Don't use negative margins as a layout mechanism (use grid offsets or positioning instead).
- Don't reduce spacing below `space-0.5` (4px) between interactive elements -- touch targets need clearance.
