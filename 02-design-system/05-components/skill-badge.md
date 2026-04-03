# Skill Badge

> The Skill Badge component displays individual technologies, tools, or skills as compact labeled elements, optionally with icons and proficiency indicators, organized in grid layouts for portfolio skill showcases.

---

## Overview

Skill Badges represent individual competencies in the portfolio, such as programming languages, frameworks, design tools, and methodologies. They can appear as simple labels, icon-and-label pairs, or include a proficiency indicator showing mastery level. Badges are typically displayed in categorized groups (e.g., "Frontend", "Backend", "Design") using a grid layout. The component supports both interactive (filterable) and static (display-only) modes.

---

## Anatomy

```
Icon + label variant:
┌───────────────────────┐
│  ┌────┐               │
│  │icon│  Skill Name   │
│  └────┘               │
└───────────────────────┘

Label only variant:
┌───────────────────────┐
│     Skill Name        │
└───────────────────────┘

With proficiency indicator:
┌───────────────────────────────────┐
│  ┌────┐                           │
│  │icon│  Skill Name               │
│  └────┘  ████████████░░░░  80%    │
└───────────────────────────────────┘

Grouped layout:
┌──────────────────────────────────────────────────┐
│  FRONTEND                                        │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│  │ ⚛ React  │ │ TS TypeS │ │ 🎨 CSS   │        │
│  └──────────┘ └──────────┘ └──────────┘        │
│  ┌──────────┐ ┌──────────┐                      │
│  │ Next.js  │ │ Tailwind │                      │
│  └──────────┘ └──────────┘                      │
│                                                  │
│  BACKEND                                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│  │ Node.js  │ │ Python   │ │ PostgreSQL│        │
│  └──────────┘ └──────────┘ └──────────┘        │
│                                                  │
│  DESIGN                                          │
│  ┌──────────┐ ┌──────────┐                      │
│  │ Figma    │ │ Sketch   │                      │
│  └──────────┘ └──────────┘                      │
└──────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Badge wrapper element |
| Icon | No | Technology or tool icon (SVG or image) |
| Label | Yes | Skill/technology name |
| Proficiency bar | No | Horizontal progress bar showing mastery level |
| Proficiency text | No | Percentage or level label (Beginner, Intermediate, Expert) |
| Group container | No | Wrapper for a category of badges with a heading |
| Group heading | No | Category label (e.g., "Frontend", "Backend") |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Icon + label | Icon on the left, text label on the right | Primary skill display with visual recognition |
| Label only | Text label without icon | Simple lists, inline mentions, lesser-known tools |
| With proficiency | Badge with a progress bar or level indicator | Detailed skills section showing mastery levels |
| Grouped | Badges organized under category headings | Full skills section of the portfolio |
| Compact | Smaller badges for inline use | Tags within project cards or timeline entries |
| Interactive | Clickable badges that filter related content | Skills that filter project cards on the portfolio |

---

## States

| State | Background | Border | Text | Notes |
|-------|-----------|--------|------|-------|
| Default | `neutral-50` | `neutral-200` | `neutral-800` | Resting display |
| Hover | `blue-50` | `blue-200` | `blue-700` | Interactive variant only |
| Focus | `blue-50` | `2px blue-300` ring | `blue-700` | Keyboard focus (interactive) |
| Active / Selected | `blue-600` | `blue-600` | `white` | Currently filtering by this skill |
| Disabled | `neutral-50` | `neutral-100` | `neutral-400` | Non-interactive |

### Proficiency Levels

| Level | Bar Fill | Fill Color | Label |
|-------|----------|-----------|-------|
| Beginner | 25% | `amber-500` | "Beginner" or "Learning" |
| Intermediate | 50% | `blue-400` | "Intermediate" |
| Advanced | 75% | `blue-600` | "Advanced" |
| Expert | 100% | `blue-800` | "Expert" |

---

## Sizing

### Badge Sizes

| Size | Height | Padding (y / x) | Font Size | Icon Size | Border Radius | Gap |
|------|--------|-----------------|-----------|-----------|---------------|-----|
| sm | 28px | 4px / 8px | 12px | 14px | 4px | 4px |
| md | 36px | 6px / 12px | 14px | 18px | 6px | 8px |
| lg | 44px | 10px / 16px | 16px | 22px | 8px | 8px |

### Proficiency Bar

| Property | Value |
|----------|-------|
| Height | 4px (sm), 6px (md), 8px (lg) |
| Width | 80px (sm), 100px (md), 120px (lg) |
| Border radius | 2px |
| Track color | `neutral-200` |
| Gap from label | 8px |

### Grid Layout

| Breakpoint | Columns | Gap | Badge size |
|------------|---------|-----|-----------|
| >= 1024px | Auto-fill, min 140px | 12px | md |
| 768px -- 1023px | Auto-fill, min 120px | 10px | md |
| < 768px | Auto-fill, min 100px | 8px | sm |

### Group Spacing

| Property | Value |
|----------|-------|
| Group heading margin bottom | 16px |
| Between groups | 32px (desktop), 24px (mobile) |
| Group heading font size | 12px, semibold, uppercase |
| Group heading color | `neutral-500` |
| Group heading letter spacing | 0.08em |

---

## Accessibility

- **Semantic structure**: Use `<ul>` with `<li>` for badge lists. Grouped badges use nested lists or `role="group"` with `aria-label` for each category.
- **Group headings**: Category headings should be associated with their group via `aria-labelledby` on the list or group container.
- **Interactive badges**: When badges act as filters, use `role="checkbox"` or `aria-pressed` to communicate toggle state. Active/selected badges announce "React, selected" to screen readers.
- **Icons**: Skill icons are decorative when accompanied by a text label; use `aria-hidden="true"` on the icon. If the badge is icon-only (rare), provide `aria-label` with the skill name.
- **Proficiency**: Proficiency bars must have a text equivalent. Use `aria-label="React: Advanced, 75%"` on the proficiency indicator or provide visible percentage text.
- **Keyboard**: Interactive badges are focusable via Tab. Toggle with Enter or Space. Focus indicator is a 2px `blue-300` ring.
- **Color**: Proficiency levels must not rely on bar color alone; include text labels or percentages.
- **Screen reader**: For grouped layouts, announce category transitions. A screen reader should encounter "Frontend skills: React, TypeScript, CSS... Backend skills: Node.js, Python..."

---

## Design Tokens

```json
{
  "skill-badge": {
    "background": "{color.neutral.50}",
    "background-hover": "{color.blue.50}",
    "background-active": "{color.primary.600}",
    "border-color": "{color.neutral.200}",
    "border-color-hover": "{color.blue.200}",
    "border-color-active": "{color.primary.600}",
    "border-width": "1px",
    "text-color": "{color.neutral.800}",
    "text-color-hover": "{color.blue.700}",
    "text-color-active": "{color.white}",
    "font-family": "{typography.font.sans}",
    "font-weight": "{typography.weight.medium}",
    "icon-color": "{color.neutral.600}",
    "icon-color-hover": "{color.blue.600}",
    "icon-color-active": "{color.white}",
    "transition": "background 150ms ease, border-color 150ms ease, color 150ms ease",
    "proficiency": {
      "track-color": "{color.neutral.200}",
      "fill-beginner": "{color.amber.500}",
      "fill-intermediate": "{color.blue.400}",
      "fill-advanced": "{color.primary.600}",
      "fill-expert": "{color.blue.800}",
      "bar-height": "6px",
      "bar-radius": "2px",
      "bar-width": "100px",
      "label-font-size": "12px",
      "label-color": "{color.neutral.500}"
    },
    "group": {
      "heading-color": "{color.neutral.500}",
      "heading-font-size": "{typography.caption.size}",
      "heading-font-weight": "{typography.weight.semibold}",
      "heading-text-transform": "uppercase",
      "heading-letter-spacing": "0.08em",
      "heading-margin-bottom": "{space.4}",
      "gap-between-groups": "{space.8}"
    },
    "sizing": {
      "sm": {
        "height": "28px",
        "padding": "4px 8px",
        "font-size": "12px",
        "icon-size": "14px",
        "border-radius": "{border.radius.sm}",
        "gap": "4px"
      },
      "md": {
        "height": "36px",
        "padding": "6px 12px",
        "font-size": "{typography.body.sm.size}",
        "icon-size": "18px",
        "border-radius": "{border.radius.md}",
        "gap": "{space.2}"
      },
      "lg": {
        "height": "44px",
        "padding": "10px 16px",
        "font-size": "{typography.body.md.size}",
        "icon-size": "22px",
        "border-radius": "{border.radius.md}",
        "gap": "{space.2}"
      }
    },
    "grid": {
      "gap": "{space.3}",
      "min-column-width": "140px"
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
- Group skills into logical categories (Frontend, Backend, Design, Tools, Methodologies).
- Use recognizable icons for major technologies (React, TypeScript, Figma, etc.).
- Include proficiency indicators only when they add genuine value; be honest about skill levels.
- Use the compact (sm) size for badges within project cards or timeline entries.
- Limit displayed skills to 15-25 across all categories to keep the section scannable.
- Use the interactive variant to allow visitors to filter projects by technology.

**Don't:**
- List every technology or tool ever used; curate to the most relevant and current.
- Use proficiency percentages without meaningful calibration (e.g., "95% JavaScript" is meaningless).
- Mix icon + label and label-only badges within the same group; be consistent per category.
- Use more than 5-6 category groups; consolidate where possible.
- Make non-interactive badges look clickable; avoid hover effects on display-only badges.
- Use skill badges as a substitute for detailed experience descriptions; they complement the timeline and project cards, not replace them.

---

## Code Example

### HTML

```html
<!-- Grouped skill badges -->
<section class="ff-skill-section" aria-label="Skills and technologies">
  <!-- Category group -->
  <div class="ff-skill-group" role="group" aria-labelledby="skills-frontend">
    <h3 class="ff-skill-group__heading" id="skills-frontend">Frontend</h3>
    <ul class="ff-skill-grid" role="list">
      <li>
        <span class="ff-skill-badge ff-skill-badge--md">
          <svg class="ff-skill-badge__icon" aria-hidden="true"><!-- react icon --></svg>
          <span class="ff-skill-badge__label">React</span>
        </span>
      </li>
      <li>
        <span class="ff-skill-badge ff-skill-badge--md">
          <svg class="ff-skill-badge__icon" aria-hidden="true"><!-- ts icon --></svg>
          <span class="ff-skill-badge__label">TypeScript</span>
        </span>
      </li>
      <li>
        <span class="ff-skill-badge ff-skill-badge--md">
          <span class="ff-skill-badge__label">Next.js</span>
        </span>
      </li>
    </ul>
  </div>

  <!-- Category group with proficiency -->
  <div class="ff-skill-group" role="group" aria-labelledby="skills-design">
    <h3 class="ff-skill-group__heading" id="skills-design">Design</h3>
    <ul class="ff-skill-grid ff-skill-grid--proficiency" role="list">
      <li>
        <div class="ff-skill-badge ff-skill-badge--md ff-skill-badge--proficiency"
             aria-label="Figma: Expert, 95%">
          <svg class="ff-skill-badge__icon" aria-hidden="true"><!-- figma icon --></svg>
          <span class="ff-skill-badge__label">Figma</span>
          <div class="ff-skill-badge__proficiency">
            <div class="ff-skill-badge__bar">
              <div class="ff-skill-badge__fill ff-skill-badge__fill--expert"
                   style="width: 95%;"></div>
            </div>
            <span class="ff-skill-badge__level">Expert</span>
          </div>
        </div>
      </li>
      <li>
        <div class="ff-skill-badge ff-skill-badge--md ff-skill-badge--proficiency"
             aria-label="Sketch: Advanced, 75%">
          <svg class="ff-skill-badge__icon" aria-hidden="true"><!-- sketch icon --></svg>
          <span class="ff-skill-badge__label">Sketch</span>
          <div class="ff-skill-badge__proficiency">
            <div class="ff-skill-badge__bar">
              <div class="ff-skill-badge__fill ff-skill-badge__fill--advanced"
                   style="width: 75%;"></div>
            </div>
            <span class="ff-skill-badge__level">Advanced</span>
          </div>
        </div>
      </li>
    </ul>
  </div>
</section>

<!-- Interactive skill badges (filter) -->
<div class="ff-skill-filter" role="group" aria-label="Filter projects by technology">
  <button class="ff-skill-badge ff-skill-badge--md ff-skill-badge--interactive"
          aria-pressed="true">
    <svg class="ff-skill-badge__icon" aria-hidden="true"><!-- react icon --></svg>
    <span class="ff-skill-badge__label">React</span>
  </button>
  <button class="ff-skill-badge ff-skill-badge--md ff-skill-badge--interactive"
          aria-pressed="false">
    <svg class="ff-skill-badge__icon" aria-hidden="true"><!-- vue icon --></svg>
    <span class="ff-skill-badge__label">Vue</span>
  </button>
</div>
```

### JSX

```jsx
import { SkillBadge, SkillGroup, SkillGrid, SkillSection } from '@flaviofusuma/ui';
import { ReactIcon, TypeScriptIcon, FigmaIcon, NodeIcon } from '@flaviofusuma/icons';

{/* Grouped display */}
<SkillSection label="Skills and technologies">
  <SkillGroup heading="Frontend">
    <SkillBadge icon={<ReactIcon />} label="React" size="md" />
    <SkillBadge icon={<TypeScriptIcon />} label="TypeScript" size="md" />
    <SkillBadge label="Next.js" size="md" />
    <SkillBadge label="Tailwind CSS" size="md" />
  </SkillGroup>

  <SkillGroup heading="Backend">
    <SkillBadge icon={<NodeIcon />} label="Node.js" size="md" />
    <SkillBadge label="Python" size="md" />
    <SkillBadge label="PostgreSQL" size="md" />
  </SkillGroup>

  <SkillGroup heading="Design">
    <SkillBadge icon={<FigmaIcon />} label="Figma" size="md"
                proficiency={{ level: "expert", percent: 95 }} />
    <SkillBadge label="Sketch" size="md"
                proficiency={{ level: "advanced", percent: 75 }} />
  </SkillGroup>
</SkillSection>

{/* Interactive filter badges */}
<SkillGrid variant="filter" label="Filter projects by technology">
  <SkillBadge
    interactive
    icon={<ReactIcon />}
    label="React"
    selected={filters.includes('react')}
    onToggle={() => toggleFilter('react')}
  />
  <SkillBadge
    interactive
    label="Vue"
    selected={filters.includes('vue')}
    onToggle={() => toggleFilter('vue')}
  />
</SkillGrid>

{/* Compact badges for project cards */}
<div className="project-tech-stack">
  <SkillBadge label="React" size="sm" />
  <SkillBadge label="TypeScript" size="sm" />
  <SkillBadge label="GraphQL" size="sm" />
</div>
```

---

## Related Components

- [Tags](/02-design-system/05-components/tags.md) -- General-purpose tags; skill badges are a specialized variant for technology/skill display.
- [Project Card](/02-design-system/05-components/project-card.md) -- Skill badges appear as tech tags within project cards.
- [Timeline](/02-design-system/05-components/timeline.md) -- Timeline entries may include skill badges for technologies used at each role.
- [Section Header](/02-design-system/05-components/section-header.md) -- Introduces the skills section on the portfolio page.
