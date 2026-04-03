# Timeline

> The Timeline component presents a chronological sequence of career milestones, work experiences, or project phases along a vertical axis, with entries alternating sides on desktop and stacking on mobile.

---

## Overview

The Timeline is a portfolio-specific component that visualizes professional experience, education, and career milestones in a vertical chronological layout. Each entry includes a date range, role title, company name, description, and optional company logo. On desktop screens, entries alternate left and right of a central vertical axis for visual balance. On mobile, entries collapse into a single column for readability. The timeline supports both ascending (oldest first) and descending (newest first) ordering.

---

## Anatomy

```
Desktop (alternating sides):
         ┌─────────────────────┐
         │ Jan 2024 - Present  │
         │ Senior Designer     │
         │ TechCorp            │
         │ Led the design...   │
         │ [logo]              │
         └──────────┬──────────┘
                    │
                ┌───●───┐
                │       │  ← center axis
                └───●───┘
                    │
┌─────────────────────┐
│ Mar 2022 - Dec 2023 │
│ Product Designer     │
│ StartupCo            │
│ Designed the core... │
│ [logo]               │
└──────────┬──────────┘
           │
       ┌───●───┐
       │       │
       └───●───┘
           │
         ┌─────────────────────┐
         │ Jun 2020 - Feb 2022 │
         │ UI/UX Designer      │
         │ AgencyCo            │
         │ Created user...     │
         │ [logo]              │
         └─────────────────────┘

Center axis detail:
    │
    ●──── Entry connector (dot + line)
    │

Mobile (single column):
┌─────────────────────────────┐
│ ● Jan 2024 - Present       │
│   Senior Designer           │
│   TechCorp [logo]           │
│   Led the design...         │
├─────────────────────────────┤
│ ● Mar 2022 - Dec 2023      │
│   Product Designer          │
│   StartupCo [logo]          │
│   Designed the core...      │
├─────────────────────────────┤
│ ● Jun 2020 - Feb 2022      │
│   UI/UX Designer            │
│   AgencyCo [logo]           │
│   Created user...           │
└─────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Full-width wrapper for the timeline |
| Axis line | Yes | Central vertical line connecting all entries |
| Entry node (dot) | Yes | Circular marker on the axis for each entry |
| Entry card | Yes | Content card for each timeline entry |
| Date range | Yes | Time period (start -- end or "Present") |
| Title | Yes | Role or milestone title |
| Company / Organization | No | Company name associated with the entry |
| Description | No | 1-3 sentence summary of responsibilities or achievements |
| Company logo | No | Small logo image for brand recognition |
| Connector line | Yes | Horizontal line from the axis dot to the entry card |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Alternating | Entries alternate left and right of center axis | Default desktop experience timeline |
| Left-aligned | All entries on the right side of a left-positioned axis | Compact layouts, sidebars |
| With logos | Includes company/organization logos in entry cards | Professional experience section |
| Compact | Reduced spacing and smaller typography | Dense timelines with many entries |
| With tags | Includes skill/technology tags per entry | Technical career timeline |

---

## States

### Entry States

| State | Appearance | Notes |
|-------|-----------|-------|
| Default | Standard card with neutral border | Past entries |
| Current | Highlighted node (blue-600 dot, blue-50 card background) | "Present" or ongoing entry |
| Hover | Subtle shadow lift on card | Interactive entries (linked to detail) |
| Focus | 2px focus ring `blue-300` on card | Keyboard navigation for linked entries |
| Loading | Skeleton placeholders | Content loading |

### Node (Dot) States

| State | Fill | Border | Size | Notes |
|-------|------|--------|------|-------|
| Default | `white` | `2px neutral-300` | 12px | Past entries |
| Current | `blue-600` | `2px blue-600` | 14px | Active / ongoing entry |
| Hover | `blue-100` | `2px blue-600` | 12px | Mouse over entry |

---

## Sizing

### Entry Card

| Size | Card Width | Title Font | Date Font | Description Font | Padding | Logo Size |
|------|-----------|-----------|-----------|-----------------|---------|-----------|
| sm | 260px | 16px, semibold | 12px | 14px | 16px | 24px |
| md | 340px | 18px, semibold | 14px | 14px | 20px | 32px |
| lg | 420px | 20px, bold | 14px | 16px | 24px | 40px |

### Axis

| Property | Value |
|----------|-------|
| Axis line width | 2px |
| Axis line color | `neutral-200` |
| Node diameter (default) | 12px |
| Node diameter (current) | 14px |
| Connector line length | 24px (from axis to card edge) |
| Connector line width | 2px |
| Connector line color | `neutral-200` |

### Spacing

| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Entry vertical gap | 48px | 40px | 32px |
| Axis to card gap | 24px | 20px | 16px |
| Date to title | 4px | 4px | 4px |
| Title to company | 4px | 4px | 2px |
| Company to description | 8px | 8px | 8px |
| Description to tags | 12px | 12px | 8px |
| Section top/bottom padding | 48px | 40px | 32px |

---

## Responsive Behavior

| Breakpoint | Layout | Axis Position |
|------------|--------|---------------|
| >= 1024px | Alternating left/right cards | Center |
| 768px -- 1023px | All cards on right, axis on left | Left (40px from edge) |
| < 768px | Single column, no visible axis line (dots inline with content) | Inline left |

### Mobile Layout

On screens below 768px, the timeline simplifies:
- The vertical axis line becomes a thin left border or is removed entirely.
- Entry nodes appear as small dots inline with the date.
- Cards span the full container width.
- All content stacks vertically without alternation.

---

## Accessibility

- **Semantic structure**: Use an ordered list (`<ol>`) for timeline entries since they are chronologically ordered. Each entry is an `<li>`.
- **Region**: Wrap the timeline in a `<section>` with `aria-label="Career timeline"` or equivalent.
- **Heading hierarchy**: Entry titles may use heading elements (`<h3>`) if the section header uses `<h2>`.
- **Date semantics**: Use `<time>` elements with `datetime` attributes for date ranges (e.g., `<time datetime="2024-01">January 2024</time>`).
- **Current entry**: Mark the current/active entry with `aria-current="true"` on its list item.
- **Logos**: Company logos must have `alt` text with the company name. If the company name is already visible as text, the logo can use `alt=""` to avoid redundancy.
- **Keyboard**: If entries are clickable/expandable, they must be focusable and activatable via Enter. Focus indicators must be visible.
- **Reading order**: The DOM order must match the visual chronological order regardless of left/right alternation. CSS handles the visual positioning.
- **Motion**: Entry entrance animations respect `prefers-reduced-motion: reduce`.
- **Color**: The current entry indicator (blue-600 dot) must not be the only way to identify it; the "Present" text label provides a non-color cue.

---

## Design Tokens

```json
{
  "timeline": {
    "axis": {
      "line-color": "{color.neutral.200}",
      "line-width": "2px",
      "node-size": "12px",
      "node-size-current": "14px",
      "node-bg": "{color.white}",
      "node-border": "2px solid {color.neutral.300}",
      "node-bg-current": "{color.primary.600}",
      "node-border-current": "2px solid {color.primary.600}",
      "connector-length": "24px",
      "connector-color": "{color.neutral.200}"
    },
    "entry": {
      "background": "{color.white}",
      "background-current": "{color.blue.50}",
      "border-color": "{color.neutral.200}",
      "border-color-current": "{color.blue.200}",
      "border-radius": "{border.radius.lg}",
      "shadow": "{shadow.sm}",
      "shadow-hover": "{shadow.md}"
    },
    "date": {
      "color": "{color.primary.600}",
      "font-size": "{typography.caption.size}",
      "font-weight": "{typography.weight.semibold}",
      "text-transform": "uppercase",
      "letter-spacing": "0.02em"
    },
    "title": {
      "color": "{color.neutral.900}",
      "font-family": "{typography.font.sans}",
      "font-weight": "{typography.weight.semibold}"
    },
    "company": {
      "color": "{color.neutral.600}",
      "font-size": "{typography.body.sm.size}"
    },
    "description": {
      "color": "{color.neutral.600}",
      "font-size": "{typography.body.sm.size}",
      "line-height": "1.6"
    },
    "logo": {
      "size-sm": "24px",
      "size-md": "32px",
      "size-lg": "40px",
      "border-radius": "{border.radius.sm}"
    },
    "spacing": {
      "entry-gap": "{space.12}",
      "entry-gap-tablet": "{space.10}",
      "entry-gap-mobile": "{space.8}",
      "axis-to-card": "{space.6}",
      "section-padding": "{space.12}"
    },
    "sizing": {
      "sm": { "card-width": "260px", "padding": "{space.4}" },
      "md": { "card-width": "340px", "padding": "{space.5}" },
      "lg": { "card-width": "420px", "padding": "{space.6}" }
    },
    "transition": "box-shadow 200ms ease, transform 200ms ease"
  }
}
```

---

## Usage Guidelines

**Do:**
- Order entries chronologically (newest first is conventional for resumes/portfolios).
- Mark the current/ongoing position with the "current" state for clear visual distinction.
- Include concise descriptions (1-3 sentences) focused on impact and achievements.
- Use company logos to add visual interest and quick recognition.
- Use the alternating layout on desktop for visual balance and engagement.
- Group related experiences (e.g., multiple roles at the same company) by nesting or visual proximity.

**Don't:**
- Include more than 8-10 entries in a single timeline; summarize early career or group by era.
- Write lengthy descriptions; the timeline is a summary, not a full resume.
- Use the alternating layout on tablet or mobile; switch to left-aligned or single column.
- Rely solely on the blue dot to indicate the current position; always include "Present" in the date.
- Mix career and project timelines in the same component instance; use separate timelines.
- Animate entry reveals on scroll without respecting `prefers-reduced-motion`.

---

## Code Example

### HTML

```html
<section class="ff-timeline" aria-label="Career timeline">
  <ol class="ff-timeline__list ff-timeline--alternating">
    <!-- Current entry -->
    <li class="ff-timeline__entry ff-timeline__entry--current ff-timeline__entry--right"
        aria-current="true">
      <div class="ff-timeline__node"></div>
      <div class="ff-timeline__connector"></div>
      <div class="ff-timeline__card ff-timeline__card--md">
        <div class="ff-timeline__header">
          <span class="ff-timeline__date">
            <time datetime="2024-01">Jan 2024</time> -- Present
          </span>
          <img src="/logos/techcorp.svg" alt="" class="ff-timeline__logo"
               width="32" height="32" loading="lazy" />
        </div>
        <h3 class="ff-timeline__title">Senior Product Designer</h3>
        <p class="ff-timeline__company">TechCorp</p>
        <p class="ff-timeline__description">
          Leading the design system initiative and mentoring a team of 4 designers.
          Shipped a component library used across 12 product teams.
        </p>
      </div>
    </li>

    <!-- Past entry -->
    <li class="ff-timeline__entry ff-timeline__entry--left">
      <div class="ff-timeline__node"></div>
      <div class="ff-timeline__connector"></div>
      <div class="ff-timeline__card ff-timeline__card--md">
        <div class="ff-timeline__header">
          <span class="ff-timeline__date">
            <time datetime="2022-03">Mar 2022</time> --
            <time datetime="2023-12">Dec 2023</time>
          </span>
          <img src="/logos/startupco.svg" alt="" class="ff-timeline__logo"
               width="32" height="32" loading="lazy" />
        </div>
        <h3 class="ff-timeline__title">Product Designer</h3>
        <p class="ff-timeline__company">StartupCo</p>
        <p class="ff-timeline__description">
          Designed the core product experience from MVP to Series A.
          Increased user retention by 28% through UX improvements.
        </p>
      </div>
    </li>

    <!-- Another past entry -->
    <li class="ff-timeline__entry ff-timeline__entry--right">
      <div class="ff-timeline__node"></div>
      <div class="ff-timeline__connector"></div>
      <div class="ff-timeline__card ff-timeline__card--md">
        <div class="ff-timeline__header">
          <span class="ff-timeline__date">
            <time datetime="2020-06">Jun 2020</time> --
            <time datetime="2022-02">Feb 2022</time>
          </span>
          <img src="/logos/agencyco.svg" alt="" class="ff-timeline__logo"
               width="32" height="32" loading="lazy" />
        </div>
        <h3 class="ff-timeline__title">UI/UX Designer</h3>
        <p class="ff-timeline__company">AgencyCo</p>
        <p class="ff-timeline__description">
          Created user interfaces for 15+ client projects across fintech,
          healthcare, and e-commerce verticals.
        </p>
      </div>
    </li>
  </ol>
</section>
```

### JSX

```jsx
import { Timeline, TimelineEntry } from '@flaviofusuma/ui';

<Timeline variant="alternating" size="md" label="Career timeline">
  <TimelineEntry
    current
    dateStart="Jan 2024"
    dateEnd="Present"
    title="Senior Product Designer"
    company="TechCorp"
    logo="/logos/techcorp.svg"
    description="Leading the design system initiative and mentoring a team of 4 designers."
  />
  <TimelineEntry
    dateStart="Mar 2022"
    dateEnd="Dec 2023"
    title="Product Designer"
    company="StartupCo"
    logo="/logos/startupco.svg"
    description="Designed the core product experience from MVP to Series A."
  />
  <TimelineEntry
    dateStart="Jun 2020"
    dateEnd="Feb 2022"
    title="UI/UX Designer"
    company="AgencyCo"
    logo="/logos/agencyco.svg"
    description="Created user interfaces for 15+ client projects."
    tags={["Figma", "Sketch", "CSS"]}
  />
</Timeline>

{/* Left-aligned variant */}
<Timeline variant="left" size="sm" label="Education">
  <TimelineEntry
    dateStart="2016"
    dateEnd="2020"
    title="BSc Computer Science"
    company="University of Design"
    description="Focused on human-computer interaction and visual computing."
  />
</Timeline>
```

---

## Related Components

- [Section Header](/02-design-system/05-components/section-header.md) -- Introduces the timeline section on the page.
- [Skill Badge](/02-design-system/05-components/skill-badge.md) -- Technology tags within timeline entries link to the skill badge component.
- [Tags](/02-design-system/05-components/tags.md) -- Inline tags for technologies used at each role.
- [Divider](/02-design-system/05-components/divider.md) -- May separate timeline from adjacent page sections.
- [Skeleton](/02-design-system/05-components/skeleton.md) -- Loading placeholder for timeline entries.
