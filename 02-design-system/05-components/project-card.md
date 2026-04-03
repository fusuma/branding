# Project Card

> The Project Card component showcases portfolio projects with a thumbnail, title, description, technology tags, and link, designed for both grid and list layouts.

---

## Overview

Project Cards are the primary building blocks of the portfolio's work showcase. Each card presents a project with a visual thumbnail, descriptive text, and technology tags, linking through to a detailed case study or project page. Cards support hover effects (image zoom, color overlay) to encourage interaction. The component adapts between grid view (visual-heavy) and list view (text-heavy) depending on the layout context and user preference.

---

## Anatomy

```
Grid view card:
┌──────────────────────────────────┐
│  ┌──────────────────────────────┐│
│  │                              ││
│  │        Thumbnail Image       ││
│  │        (hover: zoom +        ││
│  │         overlay)             ││
│  │                              ││
│  └──────────────────────────────┘│
│                                  │
│  Project Title                   │
│  Short description of the        │
│  project goes here.              │
│                                  │
│  [React] [TypeScript] [Figma]   │
│                                  │
│  View Project →                  │
└──────────────────────────────────┘

List view card:
┌──────────────────────────────────────────────────────────────┐
│  ┌────────────┐                                              │
│  │            │  Project Title                                │
│  │ Thumbnail  │  Short description of the project.           │
│  │            │                                              │
│  │            │  [React] [TypeScript] [Figma]  View Project →│
│  └────────────┘                                              │
└──────────────────────────────────────────────────────────────┘

Hover state (grid):
┌──────────────────────────────────┐
│  ┌──────────────────────────────┐│
│  │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓││
│  │▓▓▓   Image zoomed (1.05)  ▓▓││
│  │▓▓▓   + blue-800/50 overlay ▓▓││
│  │▓▓▓   [View Project →]     ▓▓││
│  │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓││
│  └──────────────────────────────┘│
│                                  │
│  Project Title                   │  ← title color shifts
│  Description text.               │
│                                  │
│  [React] [TypeScript] [Figma]   │
└──────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Card wrapper with border radius and optional shadow |
| Thumbnail | Yes | Project screenshot or visual (image or video poster) |
| Image overlay | No | Semi-transparent overlay on hover with optional CTA |
| Title | Yes | Project name as a heading |
| Description | No | 1-2 sentence summary of the project |
| Tech tags | No | Technology/tool badges displayed as a tag list |
| Link / CTA | Yes | Navigation to the project detail or case study page |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Grid (default) | Vertical card with stacked thumbnail, text, and tags | Portfolio grid, homepage showcase |
| List | Horizontal card with thumbnail left, text right | Blog-style listing, compact project directory |
| Featured | Larger card spanning 2 grid columns with bigger thumbnail | Highlighting top projects |
| Compact | Grid card without description, only thumbnail + title + tags | Dense grids, sidebar "more projects" |

---

## States

| State | Thumbnail | Title | Shadow | Border | Notes |
|-------|----------|-------|--------|--------|-------|
| Default | Static image | `neutral-900` | `sm` | `neutral-200` | Resting state |
| Hover | Zoom 1.05x + overlay | `blue-600` | `md` | `neutral-200` | Mouse over the card |
| Focus | 2px focus ring `blue-300` on card | `blue-600` | `md` | `blue-300` | Keyboard navigation |
| Active | Zoom 1.02x + darker overlay | `blue-800` | `sm` | `neutral-200` | Mouse down |
| Loading | Skeleton rectangle + text placeholders | Skeleton | `sm` | `neutral-200` | Content loading |
| Error | Fallback placeholder image | Normal | `sm` | `neutral-200` | Image failed to load |

---

## Sizing

### Grid View

| Size | Card Width | Thumbnail Height | Title Font | Description Font | Padding |
|------|-----------|-----------------|------------|-----------------|---------|
| sm | 280px min | 160px | 16px, semibold | 14px | 16px |
| md | 320px min | 200px | 18px, semibold | 14px | 20px |
| lg | 400px min | 240px | 20px, semibold | 16px | 24px |

### List View

| Size | Thumbnail Width | Thumbnail Height | Title Font | Description Font | Padding |
|------|----------------|-----------------|------------|-----------------|---------|
| sm | 120px | 80px | 16px, semibold | 14px | 16px |
| md | 180px | 120px | 18px, semibold | 14px | 20px |
| lg | 240px | 160px | 20px, semibold | 16px | 24px |

### Featured Card

| Property | Value |
|----------|-------|
| Span | 2 grid columns |
| Thumbnail height | 320px |
| Title font size | 24px, bold |
| Description font size | 16px |
| Padding | 24px |

### Tags

| Property | Value |
|----------|-------|
| Tag font size | 12px |
| Tag padding | 4px 8px |
| Tag gap | 8px |
| Tag border radius | 4px |
| Max visible tags | 5 (overflow: "+3 more") |

### Grid Layout

| Breakpoint | Columns | Gap |
|------------|---------|-----|
| >= 1200px | 3 | 24px |
| 768px -- 1199px | 2 | 20px |
| < 768px | 1 | 16px |

---

## Hover Effects

| Effect | Property | Value | Duration | Easing |
|--------|----------|-------|----------|--------|
| Image zoom | `transform: scale()` | 1.0 -> 1.05 | 300ms | ease-out |
| Overlay fade | `opacity` | 0 -> 1 | 250ms | ease-in-out |
| Shadow lift | `box-shadow` | sm -> md | 200ms | ease |
| Title color | `color` | neutral-900 -> blue-600 | 150ms | ease |
| Card lift | `transform: translateY()` | 0 -> -2px | 200ms | ease |

---

## Accessibility

- **Semantic structure**: Each card should be an `<article>` element within a container `<section>` or `<ul>`.
- **Heading**: The project title uses an appropriate heading level (`<h3>` if under an `<h2>` section header).
- **Link**: The entire card can be clickable by wrapping it in an `<a>` tag or using a stretched link pattern. Avoid wrapping block elements inside `<a>` in HTML; use CSS pseudo-element stretching instead.
- **Image alt text**: Thumbnails must have descriptive `alt` text (e.g., "Screenshot of the Dashboard Redesign project showing the analytics view").
- **Tags**: Tech tags are informational. If using a `<ul>`, set `aria-label="Technologies used"` on the list.
- **Keyboard**: Cards must be focusable and activatable via Enter. Focus indicator must be visible (2px `blue-300` ring).
- **Hover overlay**: The overlay CTA text ("View Project") should not be the only way to access the link; the card title itself should also be linked.
- **Motion**: Image zoom and card lift respect `prefers-reduced-motion: reduce` by disabling transforms.
- **Screen reader**: Announce the card as a group: the link text should include the project name (e.g., "View Dashboard Redesign project").

---

## Design Tokens

```json
{
  "project-card": {
    "background": "{color.white}",
    "border-color": "{color.neutral.200}",
    "border-radius": "{border.radius.lg}",
    "shadow": "{shadow.sm}",
    "shadow-hover": "{shadow.md}",
    "transition": "box-shadow 200ms ease, transform 200ms ease",
    "thumbnail": {
      "border-radius": "{border.radius.md}",
      "aspect-ratio": "16 / 10",
      "object-fit": "cover",
      "zoom-scale": "1.05",
      "zoom-duration": "300ms",
      "overlay-color": "rgba(30, 58, 95, 0.55)",
      "overlay-text-color": "{color.white}",
      "fallback-bg": "{color.neutral.100}"
    },
    "title": {
      "color": "{color.neutral.900}",
      "color-hover": "{color.primary.600}",
      "font-family": "{typography.font.sans}",
      "font-weight": "{typography.weight.semibold}",
      "transition": "color 150ms ease"
    },
    "description": {
      "color": "{color.neutral.600}",
      "font-size": "{typography.body.sm.size}",
      "line-height": "1.5",
      "line-clamp": "2"
    },
    "tag": {
      "background": "{color.neutral.100}",
      "color": "{color.neutral.700}",
      "font-size": "12px",
      "font-family": "{typography.font.mono}",
      "padding": "4px 8px",
      "border-radius": "{border.radius.sm}",
      "gap": "{space.2}"
    },
    "link": {
      "color": "{color.primary.600}",
      "color-hover": "{color.primary.700}",
      "font-size": "{typography.body.sm.size}",
      "font-weight": "{typography.weight.semibold}"
    },
    "sizing": {
      "sm": { "padding": "{space.4}", "thumbnail-height": "160px" },
      "md": { "padding": "{space.5}", "thumbnail-height": "200px" },
      "lg": { "padding": "{space.6}", "thumbnail-height": "240px" }
    },
    "grid": {
      "gap": "{space.6}",
      "columns-lg": "3",
      "columns-md": "2",
      "columns-sm": "1"
    },
    "focus-ring-color": "{color.blue.300}",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px"
  }
}
```

---

## Usage Guidelines

**Do:**
- Use high-quality, consistently sized thumbnails across all project cards.
- Write concise descriptions (1-2 sentences) that highlight the outcome or unique aspect.
- Limit tech tags to the 3-5 most relevant technologies per project.
- Use the featured variant for 1-2 flagship projects at the top of the grid.
- Ensure every card links to a detail page or case study.
- Use the list view for secondary project listings (blog sidebar, "more work" sections).

**Don't:**
- Mix grid and list view cards in the same section without a view toggle.
- Use thumbnails with inconsistent aspect ratios; enforce a consistent ratio (16:10 recommended).
- Write descriptions that exceed 2 lines; truncate with ellipsis if necessary.
- Include more than 5 visible tech tags; use "+N more" for overflow.
- Make the hover overlay the only way to access the project link.
- Use project cards for non-project content (blog posts, services); use dedicated card components instead.
- Disable hover effects entirely; they provide critical interactive feedback.

---

## Code Example

### HTML

```html
<!-- Grid container -->
<section aria-label="Projects">
  <ul class="ff-project-grid ff-project-grid--3col" role="list">
    <!-- Grid view card -->
    <li class="ff-project-card ff-project-card--grid ff-project-card--md">
      <article>
        <div class="ff-project-card__thumbnail">
          <img src="/projects/dashboard.webp"
               alt="Analytics dashboard showing charts and data tables"
               class="ff-project-card__image" width="640" height="400" loading="lazy" />
          <div class="ff-project-card__overlay" aria-hidden="true">
            <span class="ff-project-card__overlay-text">View Project</span>
          </div>
        </div>
        <div class="ff-project-card__body">
          <h3 class="ff-project-card__title">
            <a href="/projects/dashboard" class="ff-project-card__link">
              Dashboard Redesign
            </a>
          </h3>
          <p class="ff-project-card__description">
            A complete redesign of the analytics dashboard that improved user engagement by 42%.
          </p>
          <ul class="ff-project-card__tags" aria-label="Technologies used">
            <li class="ff-tag ff-tag--sm">React</li>
            <li class="ff-tag ff-tag--sm">TypeScript</li>
            <li class="ff-tag ff-tag--sm">D3.js</li>
          </ul>
        </div>
      </article>
    </li>

    <!-- Featured card -->
    <li class="ff-project-card ff-project-card--featured ff-project-card--md">
      <article>
        <div class="ff-project-card__thumbnail">
          <img src="/projects/ecommerce.webp"
               alt="E-commerce checkout flow showing payment step"
               class="ff-project-card__image" width="960" height="400" loading="lazy" />
          <div class="ff-project-card__overlay" aria-hidden="true">
            <span class="ff-project-card__overlay-text">View Project</span>
          </div>
        </div>
        <div class="ff-project-card__body">
          <h3 class="ff-project-card__title">
            <a href="/projects/ecommerce" class="ff-project-card__link">
              E-Commerce Checkout Redesign
            </a>
          </h3>
          <p class="ff-project-card__description">
            Streamlined the checkout experience, increasing conversion rates by 34%.
          </p>
          <ul class="ff-project-card__tags" aria-label="Technologies used">
            <li class="ff-tag ff-tag--sm">Next.js</li>
            <li class="ff-tag ff-tag--sm">Stripe</li>
            <li class="ff-tag ff-tag--sm">Figma</li>
          </ul>
        </div>
      </article>
    </li>
  </ul>
</section>

<!-- List view card -->
<article class="ff-project-card ff-project-card--list ff-project-card--md">
  <div class="ff-project-card__thumbnail">
    <img src="/projects/dashboard-thumb.webp"
         alt="Dashboard project thumbnail"
         class="ff-project-card__image" width="180" height="120" loading="lazy" />
  </div>
  <div class="ff-project-card__body">
    <h3 class="ff-project-card__title">
      <a href="/projects/dashboard" class="ff-project-card__link">Dashboard Redesign</a>
    </h3>
    <p class="ff-project-card__description">
      A complete redesign of the analytics dashboard.
    </p>
    <div class="ff-project-card__meta">
      <ul class="ff-project-card__tags" aria-label="Technologies used">
        <li class="ff-tag ff-tag--sm">React</li>
        <li class="ff-tag ff-tag--sm">TypeScript</li>
      </ul>
      <a href="/projects/dashboard" class="ff-link ff-link--sm">View Project &rarr;</a>
    </div>
  </div>
</article>
```

### JSX

```jsx
import { ProjectCard, ProjectGrid } from '@flaviofusuma/ui';

{/* Grid layout */}
<ProjectGrid columns={3} label="Projects">
  <ProjectCard
    variant="grid"
    size="md"
    thumbnail={{ src: "/projects/dashboard.webp", alt: "Analytics dashboard" }}
    title="Dashboard Redesign"
    description="A complete redesign improving user engagement by 42%."
    tags={["React", "TypeScript", "D3.js"]}
    href="/projects/dashboard"
  />
  <ProjectCard
    variant="featured"
    size="md"
    thumbnail={{ src: "/projects/ecommerce.webp", alt: "E-commerce checkout flow" }}
    title="E-Commerce Checkout Redesign"
    description="Streamlined checkout increasing conversion by 34%."
    tags={["Next.js", "Stripe", "Figma"]}
    href="/projects/ecommerce"
  />
  <ProjectCard
    variant="grid"
    size="md"
    thumbnail={{ src: "/projects/mobile.webp", alt: "Mobile app screens" }}
    title="Fitness Tracker App"
    description="Native mobile app for daily fitness tracking."
    tags={["React Native", "Firebase"]}
    href="/projects/fitness"
  />
</ProjectGrid>

{/* List layout */}
<ProjectGrid variant="list" label="More Projects">
  <ProjectCard
    variant="list"
    size="md"
    thumbnail={{ src: "/projects/dashboard-thumb.webp", alt: "Dashboard thumbnail" }}
    title="Dashboard Redesign"
    description="A complete redesign of the analytics dashboard."
    tags={["React", "TypeScript"]}
    href="/projects/dashboard"
  />
</ProjectGrid>
```

---

## Related Components

- [Skeleton](/02-design-system/05-components/skeleton.md) -- Card skeleton variant for loading state.
- [Tags](/02-design-system/05-components/tags.md) -- Technology tags within the card.
- [Skill Badge](/02-design-system/05-components/skill-badge.md) -- Related technology display component.
- [Section Header](/02-design-system/05-components/section-header.md) -- Introduces the project grid section.
- [Hero](/02-design-system/05-components/hero.md) -- Often precedes the project card section on the homepage.
