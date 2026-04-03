# Avatar

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Avatars are visual representations of users, entities, or objects. They display a profile image, user initials, or a fallback icon within a circular or rounded container. Avatars help users quickly identify people and entities across the interface. Use avatars in user profiles, comment threads, contact lists, and anywhere a person or entity needs visual identification.

---

## Anatomy

```
Single avatar:
    ┌──────────┐
    │          │
    │  Image   │
    │   or     │
    │ Initials │
    │          │
    └──────────┘
       ┌──┐
       │ ●│  Status indicator
       └──┘

Avatar with status:
    ┌──────────┐
    │          │
    │   AB     │───┐
    │          │   ● (status dot)
    └──────────┘───┘

Avatar group (stacked):
┌────┐
│ A  ├────┐
└──┬─┤ B  ├────┐
   └──┤ C  ├────┐
      └──┤ +3 │
         └────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Circular wrapper with background color and overflow hidden |
| Image | No | Profile photo or entity logo; primary display mode |
| Initials | No | One or two capital letters derived from the user's name; first fallback |
| Icon | No | Generic person or entity icon; final fallback when no image or name exists |
| Status indicator | No | Small colored dot indicating online, offline, busy, or away status |
| Group container | No | Wrapper for stacked avatars with overlap and overflow count |

---

## Variants

| Variant | Display | Use Case |
|---------|---------|----------|
| Image | Profile photo or uploaded image | Primary representation when user has a photo |
| Initials | First letter(s) of user name on colored background | Fallback when no image is available but name is known |
| Icon | Generic person silhouette icon | Final fallback when neither image nor name is available |

### Fallback Chain

```
Image available? --> Display image
       |
       No
       |
Name available? --> Display initials (first + last initial)
       |
       No
       |
Display generic icon
```

### Shape Variants

| Shape | Border Radius | Use Case |
|-------|--------------|----------|
| Circle | 50% (full round) | Default; individual users and contacts |
| Rounded square | `{border.radius.lg}` (8px) | Teams, organizations, workspaces, bots |

---

## Sizes

| Size | Dimensions | Font Size | Icon Size | Status Dot | Border Width | Use Case |
|------|-----------|-----------|-----------|-----------|-------------|----------|
| xs | 24px | 10px | 14px | 8px | 1.5px | Dense lists, inline mentions, compact tables |
| sm | 32px | 12px | 16px | 10px | 2px | Table rows, comment threads, navigation items |
| md | 40px | 14px | 20px | 12px | 2px | Default; cards, list items, chat messages |
| lg | 48px | 16px | 24px | 12px | 2.5px | Profile headers, detail panels |
| xl | 64px | 22px | 32px | 14px | 3px | Profile pages, hero sections |
| 2xl | 96px | 32px | 48px | 16px | 3px | Account settings, onboarding, large profile views |

---

## Initials Color Mapping

Initials avatars use a deterministic color mapping based on the user's name to ensure consistent colors across the application.

| Color Slot | Background | Text Color |
|-----------|-----------|-----------|
| Slot 1 | `blue-100` #DBEAFE | `blue-700` #1D4ED8 |
| Slot 2 | `green-100` #DCFCE7 | `green-700` #15803D |
| Slot 3 | `amber-100` #FEF3C7 | `amber-700` #B45309 |
| Slot 4 | `red-100` #FEE2E2 | `red-700` #B91C1C |
| Slot 5 | `purple-100` #F3E8FF | `purple-700` #7E22CE |
| Slot 6 | `teal-100` #CCFBF1 | `teal-700` #0F766E |
| Slot 7 | `pink-100` #FCE7F3 | `pink-700` #BE185D |
| Slot 8 | `indigo-100` #E0E7FF | `indigo-700` #4338CA |

---

## Status Indicator

| Status | Color | Label | Use Case |
|--------|-------|-------|----------|
| Online | `green-500` #22C55E | "Online" | User is currently active |
| Offline | `neutral-300` #CBD5E1 | "Offline" | User is not active |
| Busy | `red-500` #EF4444 | "Busy" | User is in a meeting or do-not-disturb |
| Away | `amber-500` #F59E0B | "Away" | User is idle or stepped away |

Status indicator is positioned at the bottom-right of the avatar with a white ring border (`neutral-0`) to separate it from the avatar background.

---

## Group / Stack Behavior

| Property | Value | Notes |
|----------|-------|-------|
| Overlap amount | 25% of avatar width | Each subsequent avatar overlaps the previous |
| Max visible | 5 (configurable) | Remaining count shown in "+N" overflow avatar |
| Overflow avatar | Neutral background with count text | `neutral-200` bg, `neutral-600` text |
| Stack direction | Right-to-left (LTR) | First avatar on top, last underneath |
| z-index | Decreasing from first to last | First avatar z-index highest |
| Group border | 2px `neutral-0` ring on each avatar | White ring creates visual separation |
| Hover behavior | Avatar lifts slightly, z-index raised | Shows full avatar on hover |

---

## States

### Image Avatar States

| State | Border | Shadow | Opacity | Notes |
|-------|--------|--------|---------|-------|
| Default | none | none | 100% | Resting state |
| Hover | none | `sm` | 100% | Only for interactive (clickable) avatars |
| Active | none | none | 90% | Mouse down |
| Focus | 2px `blue-600` ring, 2px offset | none | 100% | Keyboard focus |
| Loading | none | none | 100% | Skeleton pulse animation on container |
| Error | none | none | 100% | Falls back to initials or icon variant |

### Initials Avatar States

| State | Background | Text | Notes |
|-------|-----------|------|-------|
| Default | Color slot bg | Color slot text | Resting state |
| Hover | Darkened 10% | Same | Only for interactive avatars |
| Active | Darkened 15% | Same | Mouse down |
| Focus | Color slot bg + 2px `blue-600` ring | Color slot text | Keyboard focus |
| Disabled | `neutral-100` | `neutral-400` | Non-interactive |

---

## Accessibility

- **Role**: Use `<img>` with descriptive `alt` text for image avatars (e.g., `alt="Jane Doe's profile photo"`). For initials and icon variants, use `role="img"` with `aria-label`.
- **ARIA -- interactive avatars**: When clickable, wrap in `<button>` or `<a>` with appropriate `aria-label` (e.g., "View Jane Doe's profile").
- **ARIA -- status**: The status indicator should have `aria-label` describing the status (e.g., "Online") and be contained within the avatar's accessible description.
- **ARIA -- groups**: Avatar groups should use `role="group"` with `aria-label` (e.g., "Team members, 8 total"). The overflow "+N" indicator needs `aria-label="and N more"`.
- **Keyboard**:
  - Interactive avatars are focusable via `Tab`.
  - `Enter` or `Space` activates clickable avatars.
  - In avatar groups, `Tab` moves through each interactive avatar.
- **Screen reader**: Announces the user's name, the image description, and status if present.
- **Color**: Status indicator uses color plus position; tooltip on hover provides text label for the status. Initials provide text content alongside the background color.
- **Motion**: Hover animations and loading skeleton respect `prefers-reduced-motion: reduce`.

---

## Design Tokens

```json
{
  "avatar": {
    "shape": "circle",
    "border-radius-circle": "50%",
    "border-radius-square": "{border.radius.lg}",
    "font-family": "{typography.font.sans}",
    "font-weight": "600",
    "transition": "box-shadow 150ms ease, transform 150ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.600}",
    "sizing": {
      "xs": {
        "size": "24px",
        "font-size": "10px",
        "icon-size": "14px",
        "status-size": "8px",
        "group-border": "1.5px"
      },
      "sm": {
        "size": "32px",
        "font-size": "12px",
        "icon-size": "16px",
        "status-size": "10px",
        "group-border": "2px"
      },
      "md": {
        "size": "40px",
        "font-size": "14px",
        "icon-size": "20px",
        "status-size": "12px",
        "group-border": "2px"
      },
      "lg": {
        "size": "48px",
        "font-size": "16px",
        "icon-size": "24px",
        "status-size": "12px",
        "group-border": "2.5px"
      },
      "xl": {
        "size": "64px",
        "font-size": "22px",
        "icon-size": "32px",
        "status-size": "14px",
        "group-border": "3px"
      },
      "2xl": {
        "size": "96px",
        "font-size": "32px",
        "icon-size": "48px",
        "status-size": "16px",
        "group-border": "3px"
      }
    },
    "status": {
      "online": "{color.green.500}",
      "offline": "{color.neutral.300}",
      "busy": "{color.red.500}",
      "away": "{color.amber.500}",
      "ring-color": "{color.neutral.0}",
      "ring-width": "2px"
    },
    "fallback-icon": {
      "background": "{color.neutral.200}",
      "icon-color": "{color.neutral.500}"
    },
    "group": {
      "overlap": "25%",
      "max-visible": 5,
      "overflow-bg": "{color.neutral.200}",
      "overflow-text": "{color.neutral.600}",
      "border-color": "{color.neutral.0}"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Always provide meaningful `alt` text or `aria-label` that includes the person's name.
- Use the fallback chain (image > initials > icon) to ensure avatars always render appropriately.
- Use consistent sizing within a context -- all avatars in a list should be the same size.
- Include the status indicator only when real-time presence information is available and relevant.
- Use avatar groups to show collaborative ownership (e.g., assignees, participants).
- Use the rounded square shape for non-person entities like teams, organizations, or bots.

**Don't:**
- Don't display avatars without any accessible text -- every avatar must have a text alternative.
- Don't use avatars as decorative elements; they should always represent a specific entity.
- Don't mix circle and square shapes within the same context or group.
- Don't use the xl or 2xl sizes in dense layouts like tables or compact lists -- use xs or sm instead.
- Don't show status indicators on non-user entities (teams, organizations).
- Don't hardcode initials colors; always use the deterministic color mapping for consistency.

---

## Code Example

### HTML

```html
<!-- Image avatar -->
<div class="ff-avatar ff-avatar--md">
  <img class="ff-avatar__image" src="/photos/jane.jpg" alt="Jane Doe" />
</div>

<!-- Initials avatar -->
<div class="ff-avatar ff-avatar--md ff-avatar--initials" style="--avatar-bg: var(--color-blue-100); --avatar-text: var(--color-blue-700);">
  <span class="ff-avatar__initials" role="img" aria-label="Jane Doe">JD</span>
</div>

<!-- Icon fallback avatar -->
<div class="ff-avatar ff-avatar--md ff-avatar--icon" role="img" aria-label="Unknown user">
  <svg class="ff-avatar__icon" aria-hidden="true"><!-- person icon --></svg>
</div>

<!-- Avatar with status -->
<div class="ff-avatar ff-avatar--md">
  <img class="ff-avatar__image" src="/photos/jane.jpg" alt="Jane Doe" />
  <span class="ff-avatar__status ff-avatar__status--online" aria-label="Online"></span>
</div>

<!-- Avatar group -->
<div class="ff-avatar-group" role="group" aria-label="Team members, 8 total">
  <div class="ff-avatar ff-avatar--sm">
    <img class="ff-avatar__image" src="/photos/jane.jpg" alt="Jane Doe" />
  </div>
  <div class="ff-avatar ff-avatar--sm">
    <img class="ff-avatar__image" src="/photos/john.jpg" alt="John Smith" />
  </div>
  <div class="ff-avatar ff-avatar--sm">
    <span class="ff-avatar__initials" role="img" aria-label="Alice Brown">AB</span>
  </div>
  <div class="ff-avatar ff-avatar--sm ff-avatar--overflow" aria-label="and 5 more">
    <span class="ff-avatar__count">+5</span>
  </div>
</div>

<!-- Rounded square avatar (team/org) -->
<div class="ff-avatar ff-avatar--md ff-avatar--square">
  <img class="ff-avatar__image" src="/logos/team.png" alt="Design Team" />
</div>
```

### JSX

```jsx
import { Avatar, AvatarGroup } from '@flaviofusuma/ui';

{/* Image avatar */}
<Avatar size="md" src="/photos/jane.jpg" alt="Jane Doe" />

{/* Initials fallback (automatic from name) */}
<Avatar size="md" name="Jane Doe" />

{/* Icon fallback */}
<Avatar size="md" />

{/* With status indicator */}
<Avatar size="md" src="/photos/jane.jpg" alt="Jane Doe" status="online" />

{/* Rounded square for teams */}
<Avatar size="md" src="/logos/team.png" alt="Design Team" shape="square" />

{/* Large profile avatar */}
<Avatar size="2xl" src="/photos/jane.jpg" alt="Jane Doe" status="online" />

{/* Avatar group */}
<AvatarGroup size="sm" max={4} aria-label="Team members">
  <Avatar src="/photos/jane.jpg" alt="Jane Doe" />
  <Avatar src="/photos/john.jpg" alt="John Smith" />
  <Avatar name="Alice Brown" />
  <Avatar name="Bob Wilson" />
  <Avatar name="Carol Davis" />
  <Avatar name="Dan Evans" />
  <Avatar name="Eve Foster" />
  <Avatar name="Frank Green" />
</AvatarGroup>

{/* Clickable avatar */}
<Avatar
  size="md"
  src="/photos/jane.jpg"
  alt="Jane Doe"
  onClick={() => navigateToProfile('jane')}
  aria-label="View Jane Doe's profile"
/>
```

---

## Related Components

- **[Tags](/02-design-system/05-components/tags.md)** -- Often paired with avatars to show role or status labels next to a user's identity.
- **[Tooltip](/02-design-system/05-components/tooltip.md)** -- Use tooltips on avatars to show the full user name on hover, especially in avatar groups.
- **[Navigation](/02-design-system/05-components/navigation.md)** -- Navigation bars commonly include a user avatar in the top-right area.
- **[Cards](/02-design-system/05-components/cards.md)** -- User cards and profile cards typically feature an avatar as the primary visual element.
