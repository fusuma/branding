# Skeleton

## Overview

The Skeleton component provides placeholder shapes that mimic the layout of content while it loads. Skeletons reduce perceived load times by giving users an immediate visual framework, preventing layout shift and communicating that content is on its way. Use skeletons whenever asynchronous data populates a region of the page.

---

## Anatomy

```
┌──────────────────────────────────────────────┐
│  ┌────┐  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  │
│  │    │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  │  Card Skeleton
│  │ ○  │  ░░░░░░░░░░░░░░░░░                  │
│  │    │                                      │
│  └────┘  ░░░░░░░░░░░░                       │
│          ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  │
│          ░░░░░░░░░░░░░░░░░░░░░░░░           │
└──────────────────────────────────────────────┘

░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  Text line (full)
░░░░░░░░░░░░░░░░░░░░░░░░           Text line (3/4)
░░░░░░░░░░░░░░░░                    Text line (1/2)

     ┌──────┐
     │      │
     │  ○   │   Circle (avatar)
     │      │
     └──────┘

┌──────────────────────────────────────────────┐
│                                              │
│            Rectangle (image)                 │
│                                              │
└──────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Wrapper that holds one or more skeleton shapes |
| Shape | Yes | The individual placeholder element (text, circle, rectangle) |
| Animation overlay | No | Pulse or wave animation layer applied to shapes |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Text | Horizontal bars mimicking lines of text | Paragraphs, labels, headings |
| Circle | Circular placeholder | Avatars, profile images, icons |
| Rectangle | Rectangular block placeholder | Images, thumbnails, cards, banners |
| Card | Composite skeleton combining multiple shapes | Card components with image, title, and body |

---

## States

| State | Appearance | Animation | Notes |
|-------|-----------|-----------|-------|
| Loading | Neutral-200 fill with animation | Active (pulse or wave) | Default visible state |
| Loaded | Fades out, replaced by real content | Fade-out transition (200ms) | Transition to actual content |
| Error fallback | Static neutral-200 fill, no animation | None | When content fails to load, skeleton remains static |
| Reduced motion | Static neutral-200 fill, no animation | None | Respects `prefers-reduced-motion: reduce` |

---

## Animation

| Type | Description | Duration | Easing |
|------|-------------|----------|--------|
| Pulse | Opacity oscillates between 0.4 and 1.0 | 1.5s | ease-in-out, infinite |
| Wave | A shimmer gradient sweeps left to right | 1.8s | linear, infinite |

---

## Sizing

### Text Skeleton

| Size | Height | Border Radius | Spacing Between Lines |
|------|--------|---------------|-----------------------|
| sm | 12px | 4px | 8px |
| md | 16px | 4px | 8px |
| lg | 20px | 4px | 12px |
| xl | 28px | 4px | 12px |

### Circle Skeleton

| Size | Diameter |
|------|----------|
| sm | 32px |
| md | 40px |
| lg | 56px |
| xl | 80px |

### Rectangle Skeleton

| Size | Height | Width | Border Radius |
|------|--------|-------|---------------|
| sm | 80px | 100% | 8px |
| md | 160px | 100% | 8px |
| lg | 240px | 100% | 8px |
| custom | User-defined | User-defined | 8px |

### Card Skeleton

| Size | Image Height | Text Lines | Padding |
|------|-------------|------------|---------|
| sm | 120px | 2 | 16px |
| md | 180px | 3 | 16px |
| lg | 240px | 4 | 24px |

---

## Responsive Behavior

| Breakpoint | Behavior |
|------------|----------|
| < 768px | Rectangle skeletons reduce height by 25%; card skeletons stack vertically |
| 768px -- 1024px | Default sizing applies |
| > 1024px | Default sizing applies; card skeletons may appear in grid layout |

Text skeleton widths should use percentages (100%, 75%, 50%) to adapt fluidly to container width at all breakpoints.

---

## Accessibility

- **Role**: Apply `role="status"` to the skeleton container, or `aria-busy="true"` on the parent region being loaded.
- **ARIA**: Use `aria-label="Loading content"` on the skeleton container so screen readers announce the loading state.
- **Screen reader**: Provide a visually hidden live region (`aria-live="polite"`) that announces when loading completes.
- **Motion**: Disable pulse and wave animations when `prefers-reduced-motion: reduce` is active. Show a static placeholder instead.
- **Color**: Skeleton fill color must have a minimum 1.5:1 contrast ratio against its background to be perceivable.
- **Focus**: Skeletons are not focusable. Focus should move to the loaded content once it appears.

---

## Design Tokens

```json
{
  "skeleton": {
    "background": "{color.neutral.200}",
    "background-dark": "{color.neutral.700}",
    "border-radius-text": "{border.radius.sm}",
    "border-radius-rect": "{border.radius.md}",
    "border-radius-circle": "50%",
    "animation-pulse-duration": "1.5s",
    "animation-wave-duration": "1.8s",
    "wave-gradient-start": "{color.neutral.200}",
    "wave-gradient-mid": "{color.neutral.100}",
    "wave-gradient-end": "{color.neutral.200}",
    "transition-fade-out": "200ms ease-out",
    "spacing-line-gap": "{space.2}",
    "spacing-line-gap-lg": "{space.3}"
  }
}
```

---

## Usage Guidelines

**Do:**
- Use skeletons to represent the approximate shape and size of the content being loaded.
- Match skeleton layout to the final content layout to prevent layout shift.
- Combine text, circle, and rectangle skeletons to build composite loading states for cards and lists.
- Use the wave animation for prominent loading areas and pulse for smaller inline elements.
- Remove skeletons immediately once content is available; avoid artificial delays.

**Don't:**
- Use skeletons for actions that take under 300ms -- the flash of skeleton is more distracting than helpful.
- Mix skeleton animation types (pulse and wave) within the same visible region.
- Rely solely on animation to indicate loading state -- always pair with `aria-busy` or a live region.
- Use skeleton components as permanent empty-state placeholders; use a dedicated empty-state component instead.
- Apply skeleton to interactive elements like buttons or form fields; use disabled states instead.

---

## Code Example

### HTML

```html
<!-- Text skeleton -->
<div class="ff-skeleton-group" role="status" aria-label="Loading content">
  <div class="ff-skeleton ff-skeleton--text ff-skeleton--wave" style="width: 100%;"></div>
  <div class="ff-skeleton ff-skeleton--text ff-skeleton--wave" style="width: 75%;"></div>
  <div class="ff-skeleton ff-skeleton--text ff-skeleton--wave" style="width: 50%;"></div>
</div>

<!-- Circle skeleton -->
<div class="ff-skeleton ff-skeleton--circle ff-skeleton--md ff-skeleton--pulse"
     role="status" aria-label="Loading avatar"></div>

<!-- Rectangle skeleton -->
<div class="ff-skeleton ff-skeleton--rect ff-skeleton--md ff-skeleton--wave"
     role="status" aria-label="Loading image"></div>

<!-- Card skeleton -->
<div class="ff-skeleton-card ff-skeleton--wave" role="status" aria-label="Loading card">
  <div class="ff-skeleton-card__image ff-skeleton ff-skeleton--rect"></div>
  <div class="ff-skeleton-card__body">
    <div class="ff-skeleton ff-skeleton--text" style="width: 60%;"></div>
    <div class="ff-skeleton ff-skeleton--text" style="width: 100%;"></div>
    <div class="ff-skeleton ff-skeleton--text" style="width: 80%;"></div>
  </div>
</div>
```

### JSX

```jsx
import { Skeleton, SkeletonGroup, SkeletonCard } from '@flaviofusuma/ui';

{/* Text skeleton */}
<SkeletonGroup animation="wave" label="Loading content">
  <Skeleton variant="text" width="100%" />
  <Skeleton variant="text" width="75%" />
  <Skeleton variant="text" width="50%" />
</SkeletonGroup>

{/* Circle skeleton */}
<Skeleton variant="circle" size="md" animation="pulse" label="Loading avatar" />

{/* Rectangle skeleton */}
<Skeleton variant="rect" size="md" animation="wave" label="Loading image" />

{/* Card skeleton */}
<SkeletonCard animation="wave" size="md" label="Loading card" lines={3} />

{/* Conditional rendering */}
{isLoading ? (
  <SkeletonGroup animation="wave" label="Loading articles">
    {Array.from({ length: 3 }).map((_, i) => (
      <SkeletonCard key={i} size="md" lines={3} />
    ))}
  </SkeletonGroup>
) : (
  <ArticleList articles={articles} />
)}
```

---

## Related Components

- [Spinner](/02-design-system/05-components/spinner.md) -- For indeterminate loading without a content preview.
- [Progress Bar](/02-design-system/05-components/progress-bar.md) -- For determinate loading with percentage feedback.
- [Empty State](/02-design-system/06-patterns/empty-state.md) -- For when content has finished loading but no results exist.
- [Project Card](/02-design-system/05-components/project-card.md) -- Commonly wrapped with a card skeleton variant.
