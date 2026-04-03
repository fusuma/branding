# Cards

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Cards are versatile container components that group related content and actions into a single cohesive unit. They create visual hierarchy by elevating content from the page surface, making it easy for users to scan and interact with distinct pieces of information. Use cards for product listings, content previews, dashboard widgets, profile summaries, and any context where information needs to be grouped and visually separated.

---

## Anatomy

```
┌──────────────────────────────────────────────────────┐
│ ┌──────────────────────────────────────────────────┐ │
│ │                                                  │ │
│ │              [Image / Media]                     │ │
│ │                                                  │ │
│ └──────────────────────────────────────────────────┘ │
│                                                      │
│  ┌──────────────────────────────────────────────────┐│
│  │ [Header]                                         ││
│  │  ┌────┐                                          ││
│  │  │Icon│  [Title]                    [Action Menu]││
│  │  └────┘  [Subtitle / Metadata]                   ││
│  └──────────────────────────────────────────────────┘│
│                                                      │
│  ┌──────────────────────────────────────────────────┐│
│  │ [Body]                                           ││
│  │                                                  ││
│  │  Body content: text, lists, data, or any         ││
│  │  child components.                               ││
│  │                                                  ││
│  └──────────────────────────────────────────────────┘│
│                                                      │
│  ┌──────────────────────────────────────────────────┐│
│  │ [Footer]                                         ││
│  │  ┌─────────┐  ┌──────────┐         [Metadata]   ││
│  │  │ Action 1│  │ Action 2 │                       ││
│  │  └─────────┘  └──────────┘                       ││
│  └──────────────────────────────────────────────────┘│
└──────────────────────────────────────────────────────┘

Horizontal card layout:
┌────────────────────────────────────────────────────────────┐
│ ┌──────────┐  ┌──────────────────────────────────────────┐ │
│ │          │  │ [Title]                                  │ │
│ │  Image   │  │ [Subtitle]                               │ │
│ │          │  │ [Body text content...]                    │ │
│ │          │  │ ┌─────────┐  ┌──────────┐                │ │
│ │          │  │ │ Action  │  │ Action 2 │                │ │
│ └──────────┘  │ └─────────┘  └──────────┘                │ │
│               └──────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────┘
```

| Part         | Required | Description                                             |
|--------------|----------|---------------------------------------------------------|
| Container    | Yes      | Outer wrapper with background, border, shadow, and radius|
| Image/Media  | No       | Top image, video thumbnail, or illustration              |
| Header       | No       | Title, subtitle, icon, and optional overflow menu        |
| Title        | No       | Primary heading text for the card                        |
| Subtitle     | No       | Secondary text: metadata, category, date                 |
| Body         | No       | Main content area: text, lists, charts, child components |
| Footer       | No       | Action buttons, links, and secondary metadata            |
| Action menu  | No       | Overflow menu (three dots) for additional actions         |
| Badge/Tag    | No       | Status indicator overlaid on image or placed in header   |

---

## Variants

| Variant      | Description                                        | Use Case                                          |
|--------------|----------------------------------------------------|---------------------------------------------------|
| Default      | Subtle shadow, white background                     | General content grouping, dashboard widgets        |
| Elevated     | Stronger shadow for prominent elevation              | Featured content, highlighted items                |
| Outlined     | Border only, no shadow                              | Dense layouts, data-heavy interfaces, lists        |
| Interactive  | Clickable card with hover/active states              | Product listings, navigation cards, link cards     |

### Variant Visual Reference

```
Default:                  Elevated:                 Outlined:
┌──────────────┐          ┌──────────────┐          ┌──────────────┐
│              │          ┃              ┃          │              │
│   Content    │          ┃   Content    ┃          │   Content    │
│              │          ┃              ┃          │              │
└──────────────┘          ┗━━━━━━━━━━━━━━┛          └──────────────┘
  light shadow              heavy shadow              border, no shadow

Interactive (hover):
┌──────────────┐
│▒▒▒▒▒▒▒▒▒▒▒▒▒▒│  <- cursor: pointer
│▒▒ Content  ▒▒│     slight lift on hover
│▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
└──────────────┘
```

---

## States

### Default / Elevated / Outlined Card States

| State    | Background  | Border         | Shadow     | Notes                        |
|----------|-------------|----------------|------------|------------------------------|
| Default  | `white`     | --             | `sm`       | Resting state                |
| Elevated | `white`     | --             | `lg`       | Increased visual prominence  |
| Outlined | `white`     | `neutral-200`  | `none`     | Border-defined boundary      |

### Interactive Card States

| State    | Background  | Border         | Shadow     | Transform        | Notes                       |
|----------|-------------|----------------|------------|------------------|-----------------------------|
| Default  | `white`     | --             | `sm`       | `none`           | Resting state               |
| Hover    | `white`     | --             | `md`       | `translateY(-2px)` | Slight lift on hover      |
| Active   | `white`     | --             | `sm`       | `translateY(0)`  | Pressed state               |
| Focus    | `white`     | `blue-600`     | `sm`       | `none`           | Keyboard focus, 2px ring    |
| Disabled | `neutral-50`| --             | `none`     | `none`           | Non-interactive             |

---

## Sizing

### Card Padding

| Section   | Padding   | Token       |
|-----------|-----------|-------------|
| Header    | 16px 24px | `{space.4} {space.6}` |
| Body      | 0 24px    | `0 {space.6}` |
| Footer    | 16px 24px | `{space.4} {space.6}` |
| Image     | 0         | --          |

### Card Dimensions

| Property          | Value                          | Token                  |
|-------------------|--------------------------------|------------------------|
| Border radius     | 12px                           | `{border.radius.xl}`   |
| Image border radius (top) | 12px 12px 0 0          | `{border.radius.xl}` top only |
| Border width (outlined) | 1px                      | --                     |
| Min width         | 280px                          | --                     |
| Max width         | 100% of parent                 | --                     |
| Header-to-body gap| 8px                            | `{space.2}`            |
| Body-to-footer gap| 16px                           | `{space.4}`            |
| Title font size   | 18px                           | `{typography.heading.sm.size}` |
| Title font weight | 600                            | `{typography.weight.semibold}` |
| Subtitle font size| 14px                           | `{typography.body.sm.size}` |
| Body font size    | 16px                           | `{typography.body.md.size}` |
| Footer gap        | 8px between actions            | `{space.2}`            |

### Image Aspect Ratios

| Ratio    | Use Case                                |
|----------|-----------------------------------------|
| 16:9     | Video thumbnails, landscape photos       |
| 4:3      | Product images, general media            |
| 1:1      | Profile avatars, square thumbnails       |
| Free     | No constraint, image fills natural height|

---

## Responsive Behavior

| Breakpoint   | Behavior                                                     |
|--------------|--------------------------------------------------------------|
| Desktop (>1024px) | Cards in grid layouts: 3-4 columns. Full padding.       |
| Tablet (768-1024px) | Cards in 2-column grid. Full padding.                 |
| Mobile (<768px) | Cards stack vertically, full width. Horizontal cards switch to vertical layout. Padding reduces to 12px 16px. |

### Grid Layout

```
Desktop (3-column):
┌──────┐ ┌──────┐ ┌──────┐
│ Card │ │ Card │ │ Card │
│      │ │      │ │      │
└──────┘ └──────┘ └──────┘
┌──────┐ ┌──────┐ ┌──────┐
│ Card │ │ Card │ │ Card │
└──────┘ └──────┘ └──────┘
  gap: 24px ({space.6})

Mobile (1-column):
┌──────────────────┐
│ Card             │
└──────────────────┘
┌──────────────────┐
│ Card             │
└──────────────────┘
  gap: 16px ({space.4})
```

---

## Accessibility

- **Semantic structure**: Use appropriate heading levels for card titles (`<h2>`, `<h3>`, etc.) based on the card's position in the page hierarchy. Do not skip heading levels.
- **Interactive cards**: If the entire card is clickable, wrap the card in an `<a>` or `<button>` element, or use a click handler on the container with `role="link"` or `role="button"` and `tabindex="0"`. Prefer making only the title a link and stretching the click area with CSS (`::after` pseudo-element).
- **Nested actions**: When a card has both a primary click action and secondary action buttons, ensure each interactive element has a distinct accessible name. Avoid nesting `<button>` inside `<a>` or `<a>` inside `<button>`.
- **Image alt text**: Provide descriptive `alt` text for card images. Use `alt=""` for purely decorative images.
- **Keyboard**:
  - Interactive cards: `Tab` to focus the card, `Enter` or `Space` to activate.
  - Cards with multiple actions: `Tab` navigates between action buttons in the footer.
- **Focus indicator**: 2px solid ring in `blue-100` around the card border. For interactive cards, the focus ring appears around the entire card. Meets WCAG 2.1 SC 2.4.7.
- **Color contrast**: Title text in `neutral-900` on `white` meets WCAG AAA (>7:1). Body text in `neutral-700` on `white` meets WCAG AA (4.5:1).
- **Motion**: Hover lift animation on interactive cards respects `prefers-reduced-motion: reduce` by disabling the transform.
- **Landmark**: For dashboard card grids, wrap in a `<section>` with `aria-label` describing the collection.

---

## Design Tokens

```json
{
  "card": {
    "border-radius": "{border.radius.xl}",
    "font-family": "{typography.font.sans}",
    "transition": "box-shadow 200ms ease, transform 200ms ease",
    "default": {
      "bg": "{color.white}",
      "shadow": "{shadow.sm}"
    },
    "elevated": {
      "bg": "{color.white}",
      "shadow": "{shadow.lg}"
    },
    "outlined": {
      "bg": "{color.white}",
      "border": "{color.neutral.200}",
      "border-width": "1px",
      "shadow": "none"
    },
    "interactive": {
      "bg": "{color.white}",
      "shadow": "{shadow.sm}",
      "shadow-hover": "{shadow.md}",
      "transform-hover": "translateY(-2px)",
      "bg-disabled": "{color.neutral.50}",
      "cursor": "pointer",
      "focus-ring-color": "{color.blue.100}",
      "focus-ring-width": "2px"
    },
    "header": {
      "padding": "{space.4} {space.6}",
      "title-font-size": "{typography.heading.sm.size}",
      "title-font-weight": "600",
      "title-color": "{color.neutral.900}",
      "subtitle-font-size": "{typography.body.sm.size}",
      "subtitle-color": "{color.neutral.500}"
    },
    "body": {
      "padding": "0 {space.6}",
      "font-size": "{typography.body.md.size}",
      "color": "{color.neutral.700}",
      "line-height": "24px"
    },
    "footer": {
      "padding": "{space.4} {space.6}",
      "gap": "{space.2}",
      "border-top": "none",
      "border-top-outlined": "1px solid {color.neutral.100}"
    },
    "image": {
      "border-radius-top": "{border.radius.xl}",
      "object-fit": "cover"
    },
    "responsive": {
      "mobile-padding": "{space.3} {space.4}",
      "grid-gap-desktop": "{space.6}",
      "grid-gap-mobile": "{space.4}"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use cards to group related content that belongs together -- a title, description, image, and actions about the same entity.
- Maintain consistent card heights within a row by aligning footers and using equal image ratios.
- Use the interactive variant for cards that navigate to a detail page; make the title the primary link.
- Use the outlined variant in data-dense layouts where shadows would add too much visual noise.
- Keep card content concise -- cards are for summaries, not full articles.
- Use a consistent number of action buttons across cards in the same collection (1-2 maximum).
- Allow card grids to reflow responsively from multi-column to single-column layouts.

**Don't:**
- Don't nest cards inside other cards -- this creates confusing visual hierarchy.
- Don't overload cards with too many actions or too much content -- keep them scannable.
- Don't mix card variants within the same grid row -- use the same variant for all cards in a collection.
- Don't use interactive cards when the card contains multiple distinct actions (use default/outlined with action buttons instead).
- Don't remove border-radius or override shadow tokens with hardcoded values.
- Don't use cards for single-field content that would be better served by a list item.
- Don't make the entire card clickable if it contains form elements, links, or other interactive content inside it.

---

## Code Example

### HTML

```html
<!-- Default card with image, header, body, and footer -->
<article class="ff-card ff-card--default">
  <div class="ff-card__image">
    <img src="/images/product.jpg" alt="Wireless headphones on a wooden desk" />
  </div>
  <div class="ff-card__header">
    <h3 class="ff-card__title">Wireless Headphones</h3>
    <p class="ff-card__subtitle">Audio & Sound</p>
  </div>
  <div class="ff-card__body">
    <p>Premium over-ear headphones with active noise cancellation, 30-hour battery life, and multi-device connectivity.</p>
  </div>
  <div class="ff-card__footer">
    <button class="ff-btn ff-btn--primary ff-btn--sm">Add to Cart</button>
    <button class="ff-btn ff-btn--ghost ff-btn--sm">Learn More</button>
  </div>
</article>

<!-- Elevated card -->
<article class="ff-card ff-card--elevated">
  <div class="ff-card__header">
    <div class="ff-card__header-icon">
      <svg aria-hidden="true"><!-- chart icon --></svg>
    </div>
    <div>
      <h3 class="ff-card__title">Revenue Overview</h3>
      <p class="ff-card__subtitle">Last 30 days</p>
    </div>
  </div>
  <div class="ff-card__body">
    <p class="ff-card__metric">$124,563.00</p>
    <p class="ff-card__metric-change ff-card__metric-change--positive">+12.5%</p>
  </div>
</article>

<!-- Outlined card -->
<article class="ff-card ff-card--outlined">
  <div class="ff-card__header">
    <h3 class="ff-card__title">Team Member</h3>
  </div>
  <div class="ff-card__body">
    <p>Jane Doe -- Senior Designer</p>
    <p>Working on the design system refresh and component library.</p>
  </div>
  <div class="ff-card__footer">
    <button class="ff-btn ff-btn--outline ff-btn--sm">View Profile</button>
  </div>
</article>

<!-- Interactive (clickable) card -->
<a href="/articles/design-systems" class="ff-card ff-card--interactive">
  <div class="ff-card__image">
    <img src="/images/article.jpg" alt="" />
  </div>
  <div class="ff-card__header">
    <h3 class="ff-card__title">Building a Design System from Scratch</h3>
    <p class="ff-card__subtitle">Design -- 5 min read</p>
  </div>
  <div class="ff-card__body">
    <p>A practical guide to creating a scalable design system for your team.</p>
  </div>
</a>

<!-- Card grid -->
<section class="ff-card-grid" aria-label="Featured products">
  <article class="ff-card ff-card--default">
    <!-- card content -->
  </article>
  <article class="ff-card ff-card--default">
    <!-- card content -->
  </article>
  <article class="ff-card ff-card--default">
    <!-- card content -->
  </article>
</section>

<!-- Horizontal card -->
<article class="ff-card ff-card--default ff-card--horizontal">
  <div class="ff-card__image ff-card__image--side">
    <img src="/images/event.jpg" alt="Conference hall with speakers on stage" />
  </div>
  <div class="ff-card__content">
    <div class="ff-card__header">
      <h3 class="ff-card__title">Design Conference 2026</h3>
      <p class="ff-card__subtitle">April 15-17, San Francisco</p>
    </div>
    <div class="ff-card__body">
      <p>Three days of talks, workshops, and networking with design leaders.</p>
    </div>
    <div class="ff-card__footer">
      <button class="ff-btn ff-btn--primary ff-btn--sm">Register</button>
    </div>
  </div>
</article>
```

### JSX

```jsx
import { Card, CardGrid } from '@flavio-fusuma/ui';
import { Button } from '@flavio-fusuma/ui';

// Default card with all slots
<Card variant="default">
  <Card.Image src="/images/product.jpg" alt="Wireless headphones on a wooden desk" />
  <Card.Header
    title="Wireless Headphones"
    subtitle="Audio & Sound"
  />
  <Card.Body>
    <p>Premium over-ear headphones with active noise cancellation and 30-hour battery life.</p>
  </Card.Body>
  <Card.Footer>
    <Button variant="primary" size="sm">Add to Cart</Button>
    <Button variant="ghost" size="sm">Learn More</Button>
  </Card.Footer>
</Card>

// Elevated card (dashboard widget)
<Card variant="elevated">
  <Card.Header
    icon={<ChartIcon />}
    title="Revenue Overview"
    subtitle="Last 30 days"
  />
  <Card.Body>
    <MetricDisplay value="$124,563.00" change="+12.5%" trend="up" />
  </Card.Body>
</Card>

// Outlined card
<Card variant="outlined">
  <Card.Header title="Team Member" />
  <Card.Body>
    <p>Jane Doe -- Senior Designer</p>
  </Card.Body>
  <Card.Footer>
    <Button variant="outline" size="sm">View Profile</Button>
  </Card.Footer>
</Card>

// Interactive card
<Card variant="interactive" href="/articles/design-systems">
  <Card.Image src="/images/article.jpg" alt="" />
  <Card.Header
    title="Building a Design System from Scratch"
    subtitle="Design -- 5 min read"
  />
  <Card.Body>
    <p>A practical guide to creating a scalable design system for your team.</p>
  </Card.Body>
</Card>

// Horizontal card
<Card variant="default" direction="horizontal">
  <Card.Image src="/images/event.jpg" alt="Conference hall" />
  <Card.Header title="Design Conference 2026" subtitle="April 15-17" />
  <Card.Body>
    <p>Three days of talks, workshops, and networking.</p>
  </Card.Body>
  <Card.Footer>
    <Button variant="primary" size="sm">Register</Button>
  </Card.Footer>
</Card>

// Card grid
<CardGrid columns={{ base: 1, md: 2, lg: 3 }} gap="lg">
  {products.map(product => (
    <Card key={product.id} variant="default">
      <Card.Image src={product.image} alt={product.name} />
      <Card.Header title={product.name} subtitle={product.category} />
      <Card.Body><p>{product.description}</p></Card.Body>
      <Card.Footer>
        <Button variant="primary" size="sm">Add to Cart</Button>
      </Card.Footer>
    </Card>
  ))}
</CardGrid>
```

---

## Related Components

- **[Buttons](./buttons.md)** -- Card footers frequently contain button groups for primary and secondary actions.
- **[Badges](./badges.md)** -- Badges can overlay card images or appear in card headers to indicate status or category.
- **[Modals](./modals.md)** -- Interactive cards may open modals for detailed views or confirmation dialogs.
- **[Tooltips](./tooltips.md)** -- Tooltips can provide additional context on card metadata or truncated text.
- **[Inputs](./inputs.md)** -- Cards can contain form inputs for inline editing or data entry workflows.
