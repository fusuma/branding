# Testimonial

> The Testimonial component displays client or colleague endorsements with a quote, attribution, and optional avatar, building trust and social proof on portfolio pages.

---

## Overview

Testimonials present authentic feedback from clients, colleagues, or collaborators. The component supports multiple visual treatments -- from compact inline quotes to large featured displays -- and can be arranged in a carousel for browsing multiple testimonials in limited space. Each testimonial includes a quote, the author's name and role, and optional elements like avatars, company logos, and star ratings.

---

## Anatomy

```
Quote card variant:
┌──────────────────────────────────────────────┐
│                                              │
│  "  Quote text goes here. This is the        │
│     feedback from a client or colleague      │
│     about the project or collaboration. "    │
│                                              │
│  ┌────┐                                      │
│  │    │  Author Name                         │
│  │ ○  │  Title, Company                      │
│  │    │  ★★★★★                               │
│  └────┘                                      │
│                                              │
└──────────────────────────────────────────────┘

Inline quote variant:
┌──────────────────────────────────────────────────────────────┐
│  ┌────┐  "Quote text here."  — Author Name, Title, Company  │
│  │ ○  │                                                      │
│  └────┘                                                      │
└──────────────────────────────────────────────────────────────┘

Featured (large) variant:
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│                          ██                                  │
│                        (quote mark)                          │
│                                                              │
│           "This is a large, prominent quote that             │
│            takes center stage on the page with               │
│            bigger typography and more whitespace."            │
│                                                              │
│                      ┌────┐                                  │
│                      │ ○  │                                  │
│                      └────┘                                  │
│                    Author Name                               │
│                  Title, Company                               │
│                                                              │
└──────────────────────────────────────────────────────────────┘

Carousel layout:
┌──────────────────────────────────────────────────────────────┐
│         ┌──────────────────────────────────┐                 │
│   [<]   │  Active testimonial card         │   [>]           │
│         │  "Quote text here..."            │                 │
│         │  — Author, Company               │                 │
│         └──────────────────────────────────┘                 │
│                     ● ○ ○ ○ ○                                │
└──────────────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Card or inline wrapper element |
| Quote text | Yes | The testimonial content (feedback text) |
| Quote mark | No | Decorative quotation mark graphic |
| Avatar | No | Author's photo (circle image) |
| Author name | Yes | Full name of the person giving the testimonial |
| Author title | No | Job title and company name |
| Rating | No | Star rating (1-5) for project satisfaction |
| Navigation | No | Previous/next arrows and dot indicators for carousel |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Quote card | Bordered card with quote, avatar, and attribution | Testimonial grids, sidebar widgets |
| Inline quote | Single-line horizontal layout with avatar | Compact references, within content sections |
| Featured | Large centered quote with decorative marks and prominent typography | Homepage highlight, section focal point |
| With rating | Any variant above with added star rating | Client satisfaction display |
| Carousel | Multiple testimonials in a navigable slideshow | Limited space with many testimonials |

---

## States

| State | Appearance | Notes |
|-------|-----------|-------|
| Default | Static card with quote and attribution | Resting display |
| Hover (card) | Subtle shadow lift | When cards are clickable (link to case study) |
| Focus (card) | 2px focus ring `blue-300` | Keyboard navigation for linked cards |
| Carousel active | Full opacity, centered | Currently visible testimonial |
| Carousel inactive | Hidden or reduced opacity | Off-screen testimonials |
| Loading | Skeleton placeholders for text and avatar | Content loading state |

### Carousel States

| State | Behavior | Notes |
|-------|----------|-------|
| Auto-play | Advances every 6 seconds | Pauses on hover or focus |
| Paused | Stays on current slide | User interaction pauses auto-play |
| First slide | Previous button disabled or wraps to last | Boundary handling |
| Last slide | Next button disabled or wraps to first | Boundary handling |

---

## Sizing

### Quote Card

| Size | Card Width | Quote Font | Name Font | Title Font | Padding | Avatar Size |
|------|-----------|-----------|-----------|-----------|---------|-------------|
| sm | 280px min | 14px, italic | 14px, semibold | 12px | 20px | 36px |
| md | 360px min | 16px, italic | 16px, semibold | 14px | 24px | 44px |
| lg | 440px min | 18px, italic | 16px, semibold | 14px | 32px | 48px |

### Inline Quote

| Property | Value |
|----------|-------|
| Quote font size | 14px, italic |
| Name font size | 14px, semibold |
| Avatar size | 32px |
| Gap between elements | 12px |
| Max width | 100% of container |

### Featured

| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Quote font size | 24px, italic | 20px | 18px |
| Name font size | 16px, semibold | 16px | 14px |
| Title font size | 14px | 14px | 12px |
| Avatar size | 56px | 48px | 44px |
| Quote mark size | 48px | 40px | 32px |
| Max content width | 720px | 600px | 100% |
| Vertical padding | 64px | 48px | 32px |

### Star Rating

| Property | Value |
|----------|-------|
| Star size | 16px (sm/md), 20px (lg/featured) |
| Star gap | 2px |
| Filled color | `amber-500` |
| Empty color | `neutral-200` |

---

## Carousel Behavior

| Property | Value |
|----------|-------|
| Transition | Slide or fade, 400ms ease-in-out |
| Auto-advance interval | 6000ms |
| Pause on hover | Yes |
| Pause on focus | Yes |
| Loop | Optional (wrap from last to first) |
| Dot indicators | Below carousel, centered |
| Arrow placement | Left and right of the active card |
| Swipe support | Left/right swipe on touch devices |
| Reduced motion | Instant transitions (no slide/fade animation) |

---

## Accessibility

- **Semantic structure**: Use `<blockquote>` for the quote text and `<cite>` for the attribution.
- **Carousel role**: The carousel container uses `role="region"` with `aria-label="Testimonials"`. Individual slides use `role="group"` with `aria-roledescription="slide"` and `aria-label="Testimonial 1 of 5"`.
- **Navigation**: Previous/next buttons have `aria-label="Previous testimonial"` and `aria-label="Next testimonial"`. Dot indicators use `aria-label="Go to testimonial 3"` and `aria-current="true"` on the active dot.
- **Auto-play**: Include a visible pause/play button. Auto-play must stop when any carousel element receives focus. This meets WCAG 2.2.2 (Pause, Stop, Hide).
- **Keyboard**:
  - Tab moves to the carousel navigation controls.
  - Arrow keys (left/right) move between slides when the carousel or its controls have focus.
  - Enter or Space activates navigation buttons and pause/play.
- **Screen reader**: Announce slide changes with `aria-live="polite"` on the active slide container (only when user-initiated, not auto-play).
- **Rating**: Star ratings must have text fallback: `aria-label="Rated 5 out of 5 stars"`. Do not rely on visual stars alone.
- **Focus**: Visible focus indicators on all interactive elements.
- **Motion**: Respect `prefers-reduced-motion` by disabling slide transitions and auto-play.

---

## Design Tokens

```json
{
  "testimonial": {
    "background": "{color.white}",
    "border-color": "{color.neutral.200}",
    "border-radius": "{border.radius.lg}",
    "shadow": "{shadow.sm}",
    "shadow-hover": "{shadow.md}",
    "quote-mark-color": "{color.primary.600}",
    "quote-mark-size": "48px",
    "quote-mark-font": "Georgia, serif",
    "quote": {
      "color": "{color.neutral.800}",
      "font-family": "{typography.font.sans}",
      "font-style": "italic",
      "font-size-sm": "{typography.body.sm.size}",
      "font-size-md": "{typography.body.md.size}",
      "font-size-lg": "{typography.body.lg.size}",
      "font-size-featured": "24px",
      "line-height": "1.6"
    },
    "author": {
      "name-color": "{color.neutral.900}",
      "name-font-weight": "{typography.weight.semibold}",
      "title-color": "{color.neutral.500}",
      "title-font-size": "{typography.caption.size}"
    },
    "avatar": {
      "size-sm": "36px",
      "size-md": "44px",
      "size-lg": "48px",
      "size-featured": "56px",
      "border-radius": "50%",
      "border": "2px solid {color.neutral.100}"
    },
    "rating": {
      "star-color-filled": "{color.amber.500}",
      "star-color-empty": "{color.neutral.200}",
      "star-size": "16px",
      "star-size-lg": "20px",
      "star-gap": "2px"
    },
    "carousel": {
      "transition-duration": "400ms",
      "transition-easing": "ease-in-out",
      "auto-advance": "6000ms",
      "dot-size": "8px",
      "dot-color": "{color.neutral.300}",
      "dot-color-active": "{color.primary.600}",
      "dot-gap": "{space.2}",
      "arrow-size": "40px",
      "arrow-color": "{color.neutral.600}",
      "arrow-color-hover": "{color.neutral.900}"
    },
    "sizing": {
      "sm": { "padding": "{space.5}", "min-width": "280px" },
      "md": { "padding": "{space.6}", "min-width": "360px" },
      "lg": { "padding": "{space.8}", "min-width": "440px" }
    },
    "featured": {
      "max-width": "720px",
      "padding-y": "{space.16}"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use real quotes from actual clients or colleagues with their permission.
- Include the author's full name and title for credibility.
- Use avatars when available; they increase trust and personal connection.
- Limit featured testimonials to one per page for maximum impact.
- Use the carousel when displaying 3 or more testimonials in limited space.
- Keep quotes concise (1-3 sentences); edit for clarity with the author's approval.
- Pair testimonials with the section header component to introduce the section.

**Don't:**
- Fabricate or heavily edit testimonials; authenticity is key.
- Display more than 3-4 quote cards in a static grid; use a carousel for more.
- Auto-play the carousel without a pause control.
- Mix testimonial card sizes within the same grid; keep them consistent.
- Use the featured variant for more than one testimonial per page.
- Place ratings on testimonials where the author did not provide an explicit rating.
- Use testimonials as the only content on a page; they support other content, not replace it.

---

## Code Example

### HTML

```html
<!-- Quote card -->
<blockquote class="ff-testimonial ff-testimonial--card ff-testimonial--md">
  <p class="ff-testimonial__quote">
    "Flavio transformed our product vision into a beautiful, functional interface.
    His attention to detail and user empathy made all the difference."
  </p>
  <footer class="ff-testimonial__attribution">
    <img src="/avatars/sarah.webp" alt="" class="ff-testimonial__avatar"
         width="44" height="44" loading="lazy" />
    <div class="ff-testimonial__author">
      <cite class="ff-testimonial__name">Sarah Chen</cite>
      <span class="ff-testimonial__title">CPO, TechStart Inc.</span>
      <div class="ff-testimonial__rating" aria-label="Rated 5 out of 5 stars">
        <svg class="ff-star ff-star--filled" aria-hidden="true"><!-- star --></svg>
        <svg class="ff-star ff-star--filled" aria-hidden="true"><!-- star --></svg>
        <svg class="ff-star ff-star--filled" aria-hidden="true"><!-- star --></svg>
        <svg class="ff-star ff-star--filled" aria-hidden="true"><!-- star --></svg>
        <svg class="ff-star ff-star--filled" aria-hidden="true"><!-- star --></svg>
      </div>
    </div>
  </footer>
</blockquote>

<!-- Featured testimonial -->
<blockquote class="ff-testimonial ff-testimonial--featured">
  <div class="ff-testimonial__quote-mark" aria-hidden="true">"</div>
  <p class="ff-testimonial__quote">
    "Working with Flavio was an extraordinary experience. He brought both
    creative vision and technical rigor to every aspect of the project."
  </p>
  <footer class="ff-testimonial__attribution">
    <img src="/avatars/marcus.webp" alt="" class="ff-testimonial__avatar"
         width="56" height="56" loading="lazy" />
    <cite class="ff-testimonial__name">Marcus Johnson</cite>
    <span class="ff-testimonial__title">CEO, DigitalCraft</span>
  </footer>
</blockquote>

<!-- Carousel -->
<div class="ff-testimonial-carousel" role="region" aria-label="Testimonials"
     aria-roledescription="carousel">
  <button class="ff-testimonial-carousel__prev"
          aria-label="Previous testimonial">&lt;</button>
  <div class="ff-testimonial-carousel__track">
    <div class="ff-testimonial-carousel__slide" role="group"
         aria-roledescription="slide" aria-label="Testimonial 1 of 3">
      <blockquote class="ff-testimonial ff-testimonial--card ff-testimonial--md">
        <p class="ff-testimonial__quote">"Outstanding work on every project."</p>
        <footer class="ff-testimonial__attribution">
          <cite class="ff-testimonial__name">Alex Rivera</cite>
          <span class="ff-testimonial__title">Lead Designer, Acme</span>
        </footer>
      </blockquote>
    </div>
    <!-- Additional slides... -->
  </div>
  <button class="ff-testimonial-carousel__next"
          aria-label="Next testimonial">&gt;</button>
  <div class="ff-testimonial-carousel__dots" role="tablist" aria-label="Testimonial slides">
    <button role="tab" aria-selected="true" aria-label="Go to testimonial 1"
            class="ff-testimonial-carousel__dot ff-testimonial-carousel__dot--active"></button>
    <button role="tab" aria-selected="false" aria-label="Go to testimonial 2"
            class="ff-testimonial-carousel__dot"></button>
    <button role="tab" aria-selected="false" aria-label="Go to testimonial 3"
            class="ff-testimonial-carousel__dot"></button>
  </div>
  <button class="ff-testimonial-carousel__pause" aria-label="Pause auto-play">
    <svg aria-hidden="true"><!-- pause icon --></svg>
  </button>
</div>
```

### JSX

```jsx
import { Testimonial, TestimonialCarousel, TestimonialFeatured } from '@flaviofusuma/ui';

{/* Quote card */}
<Testimonial
  variant="card"
  size="md"
  quote="Flavio transformed our product vision into a beautiful, functional interface."
  authorName="Sarah Chen"
  authorTitle="CPO, TechStart Inc."
  avatar="/avatars/sarah.webp"
  rating={5}
/>

{/* Inline */}
<Testimonial
  variant="inline"
  quote="Outstanding work on every project."
  authorName="Alex Rivera"
  authorTitle="Lead Designer, Acme"
  avatar="/avatars/alex.webp"
/>

{/* Featured */}
<TestimonialFeatured
  quote="Working with Flavio was an extraordinary experience. He brought both creative vision and technical rigor to every aspect of the project."
  authorName="Marcus Johnson"
  authorTitle="CEO, DigitalCraft"
  avatar="/avatars/marcus.webp"
/>

{/* Carousel */}
<TestimonialCarousel
  autoPlay
  autoPlayInterval={6000}
  loop
  pauseOnHover
  label="Testimonials"
>
  <Testimonial
    variant="card"
    size="md"
    quote="Flavio transformed our product vision."
    authorName="Sarah Chen"
    authorTitle="CPO, TechStart Inc."
    avatar="/avatars/sarah.webp"
    rating={5}
  />
  <Testimonial
    variant="card"
    size="md"
    quote="Outstanding attention to detail."
    authorName="Alex Rivera"
    authorTitle="Lead Designer, Acme"
    avatar="/avatars/alex.webp"
    rating={5}
  />
  <Testimonial
    variant="card"
    size="md"
    quote="Highly recommend for any design project."
    authorName="Jordan Lee"
    authorTitle="PM, InnovateCo"
    avatar="/avatars/jordan.webp"
    rating={4}
  />
</TestimonialCarousel>
```

---

## Related Components

- [Section Header](/02-design-system/05-components/section-header.md) -- Introduces the testimonials section.
- [Skeleton](/02-design-system/05-components/skeleton.md) -- Card skeleton while testimonials load.
- [Project Card](/02-design-system/05-components/project-card.md) -- Testimonials often appear alongside or below project cards.
- [Divider](/02-design-system/05-components/divider.md) -- Visual separation between testimonial sections.
