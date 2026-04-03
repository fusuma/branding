# Section Header

> The Section Header component introduces content sections with a structured combination of overline, heading, description, and optional call-to-action.

---

## Overview

Section Headers create clear visual hierarchy within a page by labeling and describing content regions. They appear above grids, lists, and feature sections to orient users and establish context. The component supports left-aligned and centered layouts, with optional eyebrow text (overline) for categorization and an inline CTA for section-level actions.

---

## Anatomy

```
Left-aligned variant:
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│  OVERLINE TEXT                                               │
│  Main Section Heading                           [View All →] │
│  Optional description text that provides additional          │
│  context about the content in this section.                  │
│                                                              │
└──────────────────────────────────────────────────────────────┘

Centered variant:
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│                      OVERLINE TEXT                            │
│                Main Section Heading                           │
│         Optional description text that provides              │
│         additional context about the section.                │
│                                                              │
│                       [View All →]                            │
│                                                              │
└──────────────────────────────────────────────────────────────┘

With decorative accent:
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│  ████  OVERLINE TEXT                                         │
│  Main Section Heading                                        │
│  Description text here.                                      │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Wrapper element that controls alignment and spacing |
| Overline / Eyebrow | No | Small uppercase text above the heading for categorization |
| Heading | Yes | Primary section title, typically `<h2>` or `<h3>` |
| Description | No | Supporting paragraph below the heading |
| CTA | No | Optional link or button for section-level action |
| Accent bar | No | Decorative colored bar next to the overline |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Left-aligned | Text and optional CTA aligned to the left; CTA may float right | Default for most page sections |
| Centered | All elements centered; CTA placed below description | Feature showcases, testimonials sections |
| With eyebrow | Includes small overline text above the heading | Category labels, numbered sections |
| With accent | Decorative accent bar beside the overline | Brand emphasis, featured sections |
| Compact | Reduced spacing, no description | Dense layouts, card grid headers |

---

## States

| State | Appearance | Notes |
|-------|-----------|-------|
| Default | Static text rendering | Standard display |
| With CTA hover | CTA link shows underline and color shift | Interactive feedback |
| With CTA focus | CTA shows 2px focus ring `blue-300` | Keyboard navigation |
| Loading | Skeleton placeholders for heading and description | While content fetches |

---

## Sizing

### Text Sizing

| Element | Desktop | Tablet | Mobile |
|---------|---------|--------|--------|
| Overline | 12px, semibold, uppercase, `letter-spacing: 0.08em` | 12px | 12px |
| Heading (default) | 32px, bold | 28px | 24px |
| Heading (large) | 40px, bold | 32px | 28px |
| Description | 16px, regular, `line-height: 1.6` | 16px | 14px |
| CTA text | 14px, semibold | 14px | 14px |

### Spacing

| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Overline to heading | 8px | 8px | 4px |
| Heading to description | 12px | 12px | 8px |
| Description to CTA | 16px | 16px | 12px |
| Section header bottom margin | 32px | 24px | 20px |
| Description max-width (centered) | 640px | 560px | 100% |

### Accent Bar

| Property | Value |
|----------|-------|
| Width | 32px |
| Height | 3px |
| Color | `blue-600` (primary) or `amber-500` (accent) |
| Margin bottom | 12px (from overline) |
| Border radius | 2px |

---

## Accessibility

- **Heading hierarchy**: Use the correct heading level (`<h2>`, `<h3>`, etc.) based on the page outline. Do not skip levels.
- **Overline**: The overline is typically decorative/supplementary. If it conveys important context, it should be part of the heading (e.g., using `aria-label` on the heading that includes the overline text) or read before the heading by screen readers.
- **Description**: Use `<p>` for the description. It is naturally associated with the heading by proximity.
- **CTA**: If the CTA is a link, use `<a>`. If it triggers an action, use `<button>`. Include descriptive text (not just "View All" -- prefer "View all projects").
- **Decorative accent**: The accent bar is purely decorative; use `aria-hidden="true"`.
- **Keyboard**: CTA must be reachable via Tab with visible focus indicator.
- **Color**: Overline text color (`blue-600`) on white background achieves 4.6:1 contrast ratio (WCAG AA).

---

## Design Tokens

```json
{
  "section-header": {
    "overline-color": "{color.primary.600}",
    "overline-font-size": "{typography.caption.size}",
    "overline-font-weight": "{typography.weight.semibold}",
    "overline-text-transform": "uppercase",
    "overline-letter-spacing": "0.08em",
    "overline-margin-bottom": "{space.2}",
    "heading-color": "{color.neutral.900}",
    "heading-font-family": "{typography.font.sans}",
    "heading-font-weight": "{typography.weight.bold}",
    "heading-font-size": "32px",
    "heading-font-size-lg": "40px",
    "heading-line-height": "1.2",
    "heading-margin-bottom": "{space.3}",
    "description-color": "{color.neutral.600}",
    "description-font-size": "{typography.body.md.size}",
    "description-line-height": "1.6",
    "description-max-width": "640px",
    "description-margin-bottom": "{space.4}",
    "cta-color": "{color.primary.600}",
    "cta-color-hover": "{color.primary.700}",
    "cta-font-size": "{typography.body.sm.size}",
    "cta-font-weight": "{typography.weight.semibold}",
    "accent-bar-width": "32px",
    "accent-bar-height": "3px",
    "accent-bar-color": "{color.primary.600}",
    "accent-bar-radius": "2px",
    "margin-bottom": "{space.8}",
    "margin-bottom-compact": "{space.6}"
  }
}
```

---

## Usage Guidelines

**Do:**
- Use section headers consistently to introduce every major content section on a page.
- Match heading levels to the document outline (typically `<h2>` for top-level sections).
- Keep headings short (2-6 words) and descriptions to 1-2 sentences.
- Use the overline to provide category context (e.g., "Featured Work", "Experience", "Skills").
- Pair the CTA with a clear destination or action (e.g., "View all projects" not "See more").
- Use centered alignment for symmetrical sections (testimonials, features) and left-aligned for asymmetrical ones (project grids, timelines).

**Don't:**
- Skip heading levels (e.g., `<h2>` to `<h4>`).
- Use the section header inside other components (cards, modals); it is a page-level element.
- Add more than one CTA per section header; keep the action singular and clear.
- Use the large heading size for every section; reserve it for the most important sections on the page.
- Make the description longer than 3 sentences; use body content for extended explanations.
- Use the accent bar on every section header; reserve it for emphasis on 1-2 sections per page.

---

## Code Example

### HTML

```html
<!-- Left-aligned with overline and CTA -->
<div class="ff-section-header ff-section-header--left">
  <div class="ff-section-header__text">
    <span class="ff-section-header__overline">Featured Work</span>
    <h2 class="ff-section-header__heading">Recent Projects</h2>
    <p class="ff-section-header__description">
      A selection of my latest design and development work, from concept to launch.
    </p>
  </div>
  <a href="/projects" class="ff-section-header__cta ff-link">
    View all projects
    <svg class="ff-icon ff-icon--sm" aria-hidden="true"><!-- arrow icon --></svg>
  </a>
</div>

<!-- Centered with overline -->
<div class="ff-section-header ff-section-header--centered">
  <span class="ff-section-header__overline">What People Say</span>
  <h2 class="ff-section-header__heading">Testimonials</h2>
  <p class="ff-section-header__description">
    Feedback from clients and colleagues I have had the pleasure of working with.
  </p>
</div>

<!-- With accent bar -->
<div class="ff-section-header ff-section-header--left ff-section-header--accent">
  <div class="ff-section-header__accent-bar" aria-hidden="true"></div>
  <span class="ff-section-header__overline">Career</span>
  <h2 class="ff-section-header__heading">Experience</h2>
  <p class="ff-section-header__description">
    My professional journey in design and engineering.
  </p>
</div>

<!-- Compact (no description) -->
<div class="ff-section-header ff-section-header--left ff-section-header--compact">
  <h3 class="ff-section-header__heading">Related Articles</h3>
  <a href="/blog" class="ff-section-header__cta ff-link">See all</a>
</div>
```

### JSX

```jsx
import { SectionHeader } from '@flaviofusuma/ui';
import { ArrowRightIcon } from '@flaviofusuma/icons';

{/* Left-aligned with overline and CTA */}
<SectionHeader
  align="left"
  overline="Featured Work"
  heading="Recent Projects"
  headingLevel="h2"
  description="A selection of my latest design and development work, from concept to launch."
  cta={{ label: "View all projects", href: "/projects", icon: <ArrowRightIcon /> }}
/>

{/* Centered */}
<SectionHeader
  align="center"
  overline="What People Say"
  heading="Testimonials"
  headingLevel="h2"
  description="Feedback from clients and colleagues I have had the pleasure of working with."
/>

{/* With accent bar */}
<SectionHeader
  align="left"
  accent
  overline="Career"
  heading="Experience"
  headingLevel="h2"
  description="My professional journey in design and engineering."
/>

{/* Compact */}
<SectionHeader
  align="left"
  compact
  heading="Related Articles"
  headingLevel="h3"
  cta={{ label: "See all", href: "/blog" }}
/>

{/* Large heading */}
<SectionHeader
  align="center"
  size="lg"
  overline="About Me"
  heading="Designer, Developer, Creator"
  headingLevel="h2"
  description="I combine design thinking with technical expertise to build meaningful products."
/>
```

---

## Related Components

- [Hero](/02-design-system/05-components/hero.md) -- The hero serves a similar introductory role but at the page level; section headers introduce sub-sections.
- [Divider](/02-design-system/05-components/divider.md) -- Often used below or above section headers for additional visual separation.
- [Buttons](/02-design-system/05-components/buttons.md) -- The CTA within a section header follows button or link patterns.
- [Project Card](/02-design-system/05-components/project-card.md) -- Section headers commonly appear above project card grids.
- [Timeline](/02-design-system/05-components/timeline.md) -- The experience timeline section is typically introduced by a section header.
