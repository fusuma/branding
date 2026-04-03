# Hero

> The Hero component is the prominent banner at the top of a page, delivering the primary message and call-to-action through a bold combination of heading, subheading, buttons, and optional media.

---

## Overview

The Hero section establishes the visual tone and communicates the page's core value proposition within seconds. It supports centered, split (text + image), and full-bleed background layouts. Each variant adapts responsively, ensuring readability and visual impact across all screen sizes. Use the hero as the first content block on landing pages, the portfolio homepage, and case study pages.

---

## Anatomy

```
Centered variant:
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│                        [Eyebrow]                             │
│                                                              │
│                   Main Heading Text                          │
│                 Goes Here Prominently                        │
│                                                              │
│            Supporting subheading text that                    │
│            provides additional context.                       │
│                                                              │
│              [Primary CTA]  [Secondary CTA]                  │
│                                                              │
└──────────────────────────────────────────────────────────────┘

Split variant (text + image):
┌──────────────────────────────────────────────────────────────┐
│  ┌─────────────────────────┬────────────────────────────────┐│
│  │  [Eyebrow]              │                                ││
│  │                         │   ┌────────────────────────┐   ││
│  │  Main Heading           │   │                        │   ││
│  │  Text Here              │   │       Image /          │   ││
│  │                         │   │       Video            │   ││
│  │  Subheading text that   │   │                        │   ││
│  │  provides context.      │   └────────────────────────┘   ││
│  │                         │                                ││
│  │  [Primary] [Secondary]  │                                ││
│  └─────────────────────────┴────────────────────────────────┘│
└──────────────────────────────────────────────────────────────┘

Full-bleed variant:
┌──────────────────────────────────────────────────────────────┐
│▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓▓▓ Background Image / Video ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓ ┌──────────────────────────┐ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓ │ Overlay                  │ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓ │ Heading Text             │ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓ │ Subheading               │ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓ │ [Primary] [Secondary]    │ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓ └──────────────────────────┘ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
└──────────────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Full-width section wrapper with optional background |
| Eyebrow / Overline | No | Small text above the heading for context or category |
| Heading | Yes | Primary headline, typically `<h1>` on landing pages |
| Subheading | No | Supporting paragraph below the heading |
| Primary CTA | No | Main call-to-action button |
| Secondary CTA | No | Supporting call-to-action button or link |
| Media (image/video) | No | Visual content for split or full-bleed variants |
| Overlay | No | Semi-transparent layer for text readability over media |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Centered | Text centered, no media, optional background color/gradient | Homepage, about page, simple landing pages |
| Split | Text on one side, image/video on the other (50/50 or 40/60) | Portfolio homepage, case studies, product pages |
| Full-bleed | Full-width background image/video with overlay and centered text | High-impact visual pages, featured projects |

### Content Alignment Options

| Alignment | Description |
|-----------|-------------|
| Center | All text and CTAs centered (default for centered and full-bleed) |
| Left | Text and CTAs left-aligned (default for split variant) |
| Right | Text and CTAs right-aligned (split variant with reversed layout) |

---

## States

| State | Appearance | Notes |
|-------|-----------|-------|
| Default | Static rendering of heading, subheading, and CTAs | Initial page load |
| With video | Background or inline video autoplays (muted) | Full-bleed and split variants |
| Loading | Skeleton placeholder for media, text renders immediately | While image/video loads |
| Reduced motion | Video replaced with static poster image | Respects `prefers-reduced-motion` |
| Error media | Fallback background color (`blue-800`) if media fails to load | Graceful degradation |

---

## Sizing

### Height

| Size | Desktop Height | Tablet Height | Mobile Height |
|------|---------------|---------------|---------------|
| sm | 400px (or auto) | 360px | 320px |
| md | 520px (or 60vh) | 440px | 400px |
| lg | 640px (or 80vh) | 520px | 440px |
| full | 100vh | 100vh | 100vh (100svh) |

### Content Area

| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Max content width | 720px (centered), 560px (split text) | 640px | 100% |
| Horizontal padding | 24px | 24px | 16px |
| Vertical padding | 64px | 48px | 40px |
| CTA button gap | 16px | 16px | 12px |

### Typography

| Element | Desktop | Tablet | Mobile |
|---------|---------|--------|--------|
| Eyebrow | 14px, semibold, uppercase, `blue-600` | 14px | 12px |
| Heading | 48px -- 64px, bold, `neutral-900` or `white` | 40px | 32px |
| Subheading | 18px -- 20px, regular, `neutral-600` or `neutral-200` | 18px | 16px |

### Split Media

| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Image width | 50% or 60% of row | 100% | 100% |
| Image aspect ratio | Flexible (object-fit: cover) | 16:9 | 4:3 |
| Image border radius | `16px` | `12px` | `8px` |

---

## Responsive Behavior

| Breakpoint | Behavior |
|------------|----------|
| >= 1024px | Full layout as designed (side-by-side for split, centered for others) |
| 768px -- 1023px | Split variant stacks (image above text or below text); heading size reduces |
| < 768px | All variants become single-column, centered; image placed above text; CTA buttons stack vertically at full-width |

```
Mobile layout (split variant):
┌──────────────────────────┐
│  ┌──────────────────────┐│
│  │                      ││
│  │    Image / Video     ││
│  │                      ││
│  └──────────────────────┘│
│                          │
│  [Eyebrow]               │
│  Heading Text             │
│  Subheading text          │
│                          │
│  [Primary CTA         ]  │
│  [Secondary CTA       ]  │
└──────────────────────────┘
```

---

## Accessibility

- **Landmark**: Wrap the hero in a `<section>` with `aria-label="Hero"` or a descriptive label like "Introduction".
- **Heading hierarchy**: The hero heading should typically be `<h1>` on the page. Avoid skipping heading levels.
- **Media alt text**: Images must have descriptive `alt` text. Decorative background images use `role="img"` with `aria-label` or are set via CSS background.
- **Video**: Autoplaying video must be muted by default. Provide a pause/play control. Include `<track>` elements for captions. If the video is decorative, use `aria-hidden="true"`.
- **Overlay contrast**: Text over images must meet WCAG AA contrast. Use a dark overlay (`rgba(0, 0, 0, 0.5)` minimum) or gradient to ensure readability.
- **CTA buttons**: Follow standard button accessibility. Primary CTA should have clear, action-oriented label.
- **Keyboard**: All interactive elements (buttons, video controls) are reachable via Tab with visible focus indicators.
- **Motion**: Respect `prefers-reduced-motion` by replacing video with a poster image and disabling entrance animations.
- **Reduced data**: Consider `prefers-reduced-data` by serving smaller image assets or skipping video.

---

## Design Tokens

```json
{
  "hero": {
    "background-default": "{color.white}",
    "background-dark": "{color.blue.800}",
    "text-color-light": "{color.neutral.900}",
    "text-color-dark": "{color.white}",
    "eyebrow-color": "{color.primary.600}",
    "eyebrow-font-size": "{typography.caption.size}",
    "eyebrow-font-weight": "{typography.weight.semibold}",
    "eyebrow-text-transform": "uppercase",
    "eyebrow-letter-spacing": "0.08em",
    "eyebrow-margin-bottom": "{space.3}",
    "heading-font-family": "{typography.font.sans}",
    "heading-font-weight": "{typography.weight.bold}",
    "heading-line-height": "1.1",
    "heading-font-size-desktop": "56px",
    "heading-font-size-tablet": "40px",
    "heading-font-size-mobile": "32px",
    "heading-margin-bottom": "{space.4}",
    "subheading-font-size": "{typography.body.lg.size}",
    "subheading-line-height": "1.6",
    "subheading-color-light": "{color.neutral.600}",
    "subheading-color-dark": "{color.neutral.200}",
    "subheading-max-width": "560px",
    "subheading-margin-bottom": "{space.8}",
    "cta-gap": "{space.4}",
    "cta-gap-mobile": "{space.3}",
    "padding-y-desktop": "{space.16}",
    "padding-y-tablet": "{space.12}",
    "padding-y-mobile": "{space.10}",
    "overlay-color": "rgba(30, 58, 95, 0.65)",
    "media-border-radius": "{border.radius.xl}",
    "media-border-radius-mobile": "{border.radius.md}",
    "max-content-width": "720px",
    "height-sm": "400px",
    "height-md": "520px",
    "height-lg": "640px"
  }
}
```

---

## Usage Guidelines

**Do:**
- Use the hero as the first visible content block below the navigation.
- Write concise, benefit-driven headings -- aim for 4-8 words.
- Limit to one primary CTA and one secondary CTA maximum.
- Optimize hero images for performance: use responsive `srcset`, WebP format, and lazy loading for below-fold content.
- Use the full-bleed variant sparingly for high-impact moments (homepage, flagship case study).
- Test overlay contrast with different background images to ensure readability.

**Don't:**
- Stack multiple hero components on a single page.
- Use paragraphs longer than 2-3 sentences in the subheading -- be concise.
- Autoplay video with sound; always mute by default.
- Use the hero for non-introductory content; it should always be the first section.
- Place form elements inside the hero (use a dedicated section below).
- Rely solely on the background image to convey critical information; the text overlay must communicate the key message.

---

## Code Example

### HTML

```html
<!-- Centered hero -->
<section class="ff-hero ff-hero--centered ff-hero--md" aria-label="Introduction">
  <div class="ff-hero__inner">
    <span class="ff-hero__eyebrow">Portfolio</span>
    <h1 class="ff-hero__heading">Designing Digital Experiences That Matter</h1>
    <p class="ff-hero__subheading">
      I craft user-centered interfaces that balance beauty with usability,
      helping businesses connect with their audience.
    </p>
    <div class="ff-hero__actions">
      <a href="/projects" class="ff-btn ff-btn--primary ff-btn--lg">View Projects</a>
      <a href="/contact" class="ff-btn ff-btn--outline ff-btn--lg">Get in Touch</a>
    </div>
  </div>
</section>

<!-- Split hero (text + image) -->
<section class="ff-hero ff-hero--split ff-hero--lg" aria-label="Introduction">
  <div class="ff-hero__inner">
    <div class="ff-hero__content">
      <span class="ff-hero__eyebrow">Full-Stack Designer</span>
      <h1 class="ff-hero__heading">Hi, I'm Flavio Fusuma</h1>
      <p class="ff-hero__subheading">
        I design and build products that people love to use, from concept to code.
      </p>
      <div class="ff-hero__actions">
        <a href="/projects" class="ff-btn ff-btn--primary ff-btn--lg">See My Work</a>
        <a href="/about" class="ff-btn ff-btn--ghost ff-btn--lg">About Me</a>
      </div>
    </div>
    <div class="ff-hero__media">
      <img src="/hero-portrait.webp" alt="Flavio working at desk"
           class="ff-hero__image" width="600" height="500" loading="eager" />
    </div>
  </div>
</section>

<!-- Full-bleed hero with background -->
<section class="ff-hero ff-hero--full-bleed ff-hero--full"
         aria-label="Featured project">
  <div class="ff-hero__background">
    <img src="/hero-bg.webp" alt="" role="presentation"
         class="ff-hero__bg-image" loading="eager" />
    <div class="ff-hero__overlay"></div>
  </div>
  <div class="ff-hero__inner">
    <span class="ff-hero__eyebrow">Featured Project</span>
    <h1 class="ff-hero__heading">Redefining E-Commerce Checkout</h1>
    <p class="ff-hero__subheading">
      A complete redesign that increased conversion rates by 34%.
    </p>
    <div class="ff-hero__actions">
      <a href="/case-study/checkout" class="ff-btn ff-btn--primary ff-btn--lg">
        Read Case Study
      </a>
    </div>
  </div>
</section>
```

### JSX

```jsx
import { Hero, HeroContent, HeroMedia } from '@flaviofusuma/ui';

{/* Centered */}
<Hero variant="centered" size="md" label="Introduction">
  <HeroContent
    eyebrow="Portfolio"
    heading="Designing Digital Experiences That Matter"
    subheading="I craft user-centered interfaces that balance beauty with usability."
    primaryCta={{ label: "View Projects", href: "/projects" }}
    secondaryCta={{ label: "Get in Touch", href: "/contact", variant: "outline" }}
  />
</Hero>

{/* Split */}
<Hero variant="split" size="lg" label="Introduction">
  <HeroContent
    eyebrow="Full-Stack Designer"
    heading="Hi, I'm Flavio Fusuma"
    subheading="I design and build products that people love to use."
    primaryCta={{ label: "See My Work", href: "/projects" }}
    secondaryCta={{ label: "About Me", href: "/about", variant: "ghost" }}
  />
  <HeroMedia
    src="/hero-portrait.webp"
    alt="Flavio working at desk"
    loading="eager"
  />
</Hero>

{/* Full-bleed */}
<Hero variant="full-bleed" size="full" label="Featured project"
      backgroundImage="/hero-bg.webp" overlay>
  <HeroContent
    eyebrow="Featured Project"
    heading="Redefining E-Commerce Checkout"
    subheading="A complete redesign that increased conversion rates by 34%."
    primaryCta={{ label: "Read Case Study", href: "/case-study/checkout" }}
    dark
  />
</Hero>
```

---

## Related Components

- [Section Header](/02-design-system/05-components/section-header.md) -- For introducing content sections below the hero.
- [Buttons](/02-design-system/05-components/buttons.md) -- CTA buttons within the hero follow button component specs.
- [Footer](/02-design-system/05-components/footer.md) -- The footer and hero bookend the page.
- [Skeleton](/02-design-system/05-components/skeleton.md) -- Skeleton placeholder while hero media loads.
- [Project Card](/02-design-system/05-components/project-card.md) -- Often the first content below a portfolio hero.
