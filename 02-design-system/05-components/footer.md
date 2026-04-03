# Footer

> The Footer component anchors the bottom of every page, providing navigation, branding, social links, and legal information in a consistent, accessible layout.

---

## Overview

The Footer is a page-level landmark that contains secondary navigation, brand identity, social media links, copyright notices, and optional newsletter signup. It serves as a reliable orientation point -- users know they can scroll to the bottom for contact details, legal links, and additional navigation. The footer adapts from a multi-column layout on desktop to a stacked layout on mobile.

---

## Anatomy

```
Multi-column variant:
┌──────────────────────────────────────────────────────────────────┐
│  Footer Container                                                │
│  ┌────────────────────────────────────────────────────────────┐  │
│  │  Upper Section                                             │  │
│  │  ┌──────────┬───────────┬───────────┬────────────────────┐ │  │
│  │  │ Logo     │ Nav Col 1 │ Nav Col 2 │ Newsletter Signup  │ │  │
│  │  │ Tagline  │ Link      │ Link      │ [Email        ]    │ │  │
│  │  │          │ Link      │ Link      │ [Subscribe]        │ │  │
│  │  │          │ Link      │ Link      │                    │ │  │
│  │  └──────────┴───────────┴───────────┴────────────────────┘ │  │
│  ├────────────────────────────────────────────────────────────┤  │
│  │  Divider                                                   │  │
│  ├────────────────────────────────────────────────────────────┤  │
│  │  Lower Section                                             │  │
│  │  ┌─────────────────────────────────┬──────────────────────┐│  │
│  │  │ (c) 2026 Flavio Fusuma         │ [tw] [gh] [li] [dr]  ││  │
│  │  │ Privacy | Terms | Cookies      │                       ││  │
│  │  └─────────────────────────────────┴──────────────────────┘│  │
│  └────────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────────┘

Simple variant:
┌──────────────────────────────────────────────────────────────────┐
│  ┌──────────────────────────────────────────────────────────┐    │
│  │ Logo    [Link] [Link] [Link] [Link]    [tw] [gh] [li]   │    │
│  ├──────────────────────────────────────────────────────────┤    │
│  │ (c) 2026 Flavio Fusuma. All rights reserved.            │    │
│  └──────────────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────────────┘

Minimal variant:
┌──────────────────────────────────────────────────────────────────┐
│  (c) 2026 Flavio Fusuma  |  Privacy  |  Terms     [tw] [gh]     │
└──────────────────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Full-width footer wrapper with background |
| Logo | No | Brand mark or wordmark, links to homepage |
| Tagline | No | Short brand description below the logo |
| Navigation columns | No | Grouped link lists for site sections |
| Social links | No | Icon links to social media profiles |
| Newsletter signup | No | Email input and subscribe button |
| Copyright | Yes | Legal copyright notice |
| Legal links | No | Privacy policy, terms of service, cookie policy |
| Divider | No | Visual separator between upper and lower sections |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Multi-column | Logo, 2-4 nav columns, newsletter signup, lower bar | Marketing sites, portfolio homepage |
| Simple | Single row with logo, inline links, social icons, copyright below | Blog, single-page portfolio |
| Minimal | Single line with copyright and essential legal links | App-style pages, focused landing pages |

---

## States

| State | Appearance | Notes |
|-------|-----------|-------|
| Default | Dark background (`blue-800` or `neutral-900`) with light text | Standard rendering |
| Light | White or `neutral-50` background with dark text | For light-themed pages |
| Link default | `neutral-300` text | Resting link state |
| Link hover | `white` text with underline | Interactive feedback |
| Link focus | `white` text with 2px focus ring `blue-300` | Keyboard navigation |
| Newsletter success | Input replaced with success message | After successful subscription |
| Newsletter error | Input border turns `red-500`, error message below | Validation failure |

---

## Sizing

### Padding

| Section | Padding (desktop) | Padding (mobile) |
|---------|-------------------|------------------|
| Container outer | 48px top / 32px bottom, 0 horizontal | 32px top / 24px bottom, 0 horizontal |
| Content inner | 0 vertical, max-width container centered | 0 vertical, 16px horizontal |
| Upper section | 0 0 32px 0 (bottom margin) | 0 0 24px 0 |
| Lower section | 24px 0 0 0 (top padding) | 16px 0 0 0 |

### Navigation Columns

| Property | Value |
|----------|-------|
| Column gap | 48px (desktop), 32px (tablet) |
| Link vertical spacing | 12px |
| Column heading font size | 14px, semibold, uppercase |
| Link font size | 14px, regular |

### Social Icons

| Property | Value |
|----------|-------|
| Icon size | 20px |
| Touch target | 40px x 40px |
| Gap between icons | 16px |

---

## Responsive Behavior

| Breakpoint | Layout |
|------------|--------|
| >= 1024px | Multi-column grid: logo column + nav columns + newsletter in a row |
| 768px -- 1023px | 2-column grid: logo + newsletter on top row, nav columns below |
| < 768px | Single column, all sections stacked vertically; nav columns become accordion or stacked lists; social icons centered |

```
Mobile stacked layout:
┌──────────────────────────┐
│  [Logo]                  │
│  Tagline text here       │
│                          │
│  Navigation              │
│  > Products              │
│  > Resources             │
│  > Company               │
│                          │
│  Newsletter              │
│  [Email               ]  │
│  [Subscribe           ]  │
│                          │
│  ────────────────────    │
│                          │
│  [tw] [gh] [li] [dr]    │
│                          │
│  (c) 2026 Flavio Fusuma │
│  Privacy | Terms         │
└──────────────────────────┘
```

---

## Accessibility

- **Landmark**: Use `<footer>` element which maps to `role="contentinfo"`. Only one `contentinfo` landmark per page.
- **Navigation**: Wrap link groups in `<nav>` with `aria-label` such as "Footer navigation" or "Social media links".
- **Headings**: Navigation column headings should use appropriate heading level (e.g., `<h2>` or `<h3>`) or be `<p>` elements with `id` referenced by `aria-labelledby` on the `<nav>`.
- **Social links**: Each icon link must have `aria-label` describing the destination (e.g., "GitHub profile", "Follow on Twitter"). Use `target="_blank"` with `rel="noopener noreferrer"` and optionally indicate "(opens in new tab)" in the label.
- **Newsletter form**: Label the email input with a visible `<label>` or `aria-label`. Announce success/error states via `aria-live="polite"` region.
- **Keyboard**: All links and form elements are reachable via Tab. Focus indicators are visible (2px `blue-300` ring).
- **Color**: Footer text on dark backgrounds must meet WCAG AA contrast (4.5:1 for body text, 3:1 for large text). `neutral-300` on `blue-800` achieves 7.2:1.
- **Skip link**: Consider a "Back to top" link at the footer end for long pages.

---

## Design Tokens

```json
{
  "footer": {
    "background": "{color.blue.800}",
    "background-light": "{color.neutral.50}",
    "text-color": "{color.neutral.300}",
    "text-color-light": "{color.neutral.600}",
    "heading-color": "{color.white}",
    "heading-font-size": "{typography.caption.size}",
    "heading-font-weight": "{typography.weight.semibold}",
    "heading-text-transform": "uppercase",
    "heading-letter-spacing": "0.05em",
    "link-color": "{color.neutral.300}",
    "link-color-hover": "{color.white}",
    "link-font-size": "{typography.body.sm.size}",
    "link-gap": "{space.3}",
    "social-icon-size": "20px",
    "social-icon-gap": "{space.4}",
    "social-icon-color": "{color.neutral.400}",
    "social-icon-color-hover": "{color.white}",
    "copyright-font-size": "{typography.caption.size}",
    "copyright-color": "{color.neutral.400}",
    "divider-color": "{color.neutral.700}",
    "padding-top": "{space.12}",
    "padding-bottom": "{space.8}",
    "padding-top-mobile": "{space.8}",
    "padding-bottom-mobile": "{space.6}",
    "column-gap": "{space.12}",
    "column-gap-tablet": "{space.8}",
    "max-width": "1200px"
  }
}
```

---

## Usage Guidelines

**Do:**
- Include the footer on every page for consistent navigation and legal compliance.
- Keep navigation links organized in logical groups (Products, Resources, Company).
- Place the most important links in the leftmost column (LTR reading order).
- Use the minimal variant for focused experiences (checkout, onboarding) where distractions should be limited.
- Include a "Back to top" action on long-scrolling pages.
- Ensure social media icon links open in new tabs with proper `rel` attributes.

**Don't:**
- Overload the footer with too many links -- aim for 4-6 links per column, 2-4 columns maximum.
- Duplicate primary navigation exactly; the footer should offer complementary or secondary paths.
- Use the footer for critical calls-to-action that users must see; above-the-fold placement is better.
- Hide the copyright notice or legal links; these are often legally required.
- Use low-contrast text that fails accessibility checks, even in footer sections.
- Include autoplaying content or animations in the footer.

---

## Code Example

### HTML

```html
<footer class="ff-footer ff-footer--multi-column">
  <div class="ff-footer__inner">
    <!-- Upper section -->
    <div class="ff-footer__upper">
      <div class="ff-footer__brand">
        <a href="/" class="ff-footer__logo" aria-label="Flavio Fusuma - Home">
          <img src="/logo-white.svg" alt="Flavio Fusuma" width="140" height="32" />
        </a>
        <p class="ff-footer__tagline">Designing digital experiences that matter.</p>
      </div>

      <nav class="ff-footer__nav" aria-label="Footer navigation">
        <div class="ff-footer__nav-col">
          <h3 class="ff-footer__nav-heading">Portfolio</h3>
          <ul class="ff-footer__nav-list">
            <li><a href="/projects" class="ff-footer__link">Projects</a></li>
            <li><a href="/case-studies" class="ff-footer__link">Case Studies</a></li>
            <li><a href="/playground" class="ff-footer__link">Playground</a></li>
          </ul>
        </div>
        <div class="ff-footer__nav-col">
          <h3 class="ff-footer__nav-heading">Connect</h3>
          <ul class="ff-footer__nav-list">
            <li><a href="/about" class="ff-footer__link">About</a></li>
            <li><a href="/blog" class="ff-footer__link">Blog</a></li>
            <li><a href="/contact" class="ff-footer__link">Contact</a></li>
          </ul>
        </div>
      </nav>

      <div class="ff-footer__newsletter">
        <h3 class="ff-footer__nav-heading">Stay Updated</h3>
        <form class="ff-footer__newsletter-form" aria-label="Newsletter signup">
          <label for="footer-email" class="ff-sr-only">Email address</label>
          <input type="email" id="footer-email" class="ff-input ff-input--sm"
                 placeholder="your@email.com" required />
          <button type="submit" class="ff-btn ff-btn--primary ff-btn--sm">Subscribe</button>
        </form>
      </div>
    </div>

    <hr class="ff-footer__divider" />

    <!-- Lower section -->
    <div class="ff-footer__lower">
      <div class="ff-footer__legal">
        <p class="ff-footer__copyright">&copy; 2026 Flavio Fusuma. All rights reserved.</p>
        <nav aria-label="Legal links">
          <a href="/privacy" class="ff-footer__link">Privacy</a>
          <a href="/terms" class="ff-footer__link">Terms</a>
        </nav>
      </div>
      <nav class="ff-footer__social" aria-label="Social media links">
        <a href="https://twitter.com" class="ff-footer__social-link"
           aria-label="Follow on Twitter (opens in new tab)"
           target="_blank" rel="noopener noreferrer">
          <svg aria-hidden="true"><!-- twitter icon --></svg>
        </a>
        <a href="https://github.com" class="ff-footer__social-link"
           aria-label="GitHub profile (opens in new tab)"
           target="_blank" rel="noopener noreferrer">
          <svg aria-hidden="true"><!-- github icon --></svg>
        </a>
        <a href="https://linkedin.com" class="ff-footer__social-link"
           aria-label="LinkedIn profile (opens in new tab)"
           target="_blank" rel="noopener noreferrer">
          <svg aria-hidden="true"><!-- linkedin icon --></svg>
        </a>
      </nav>
    </div>
  </div>
</footer>
```

### JSX

```jsx
import { Footer, FooterBrand, FooterNav, FooterNavColumn, FooterNewsletter,
         FooterSocial, FooterLegal } from '@flaviofusuma/ui';
import { TwitterIcon, GitHubIcon, LinkedInIcon } from '@flaviofusuma/icons';

<Footer variant="multi-column">
  <FooterBrand
    logo="/logo-white.svg"
    logoAlt="Flavio Fusuma"
    tagline="Designing digital experiences that matter."
    homeHref="/"
  />

  <FooterNav label="Footer navigation">
    <FooterNavColumn heading="Portfolio">
      <a href="/projects">Projects</a>
      <a href="/case-studies">Case Studies</a>
      <a href="/playground">Playground</a>
    </FooterNavColumn>
    <FooterNavColumn heading="Connect">
      <a href="/about">About</a>
      <a href="/blog">Blog</a>
      <a href="/contact">Contact</a>
    </FooterNavColumn>
  </FooterNav>

  <FooterNewsletter
    heading="Stay Updated"
    placeholder="your@email.com"
    onSubmit={handleSubscribe}
    successMessage="Thanks for subscribing!"
  />

  <FooterLegal copyright="2026 Flavio Fusuma. All rights reserved.">
    <a href="/privacy">Privacy</a>
    <a href="/terms">Terms</a>
  </FooterLegal>

  <FooterSocial label="Social media links">
    <FooterSocial.Link href="https://twitter.com" icon={<TwitterIcon />}
                        label="Follow on Twitter" />
    <FooterSocial.Link href="https://github.com" icon={<GitHubIcon />}
                        label="GitHub profile" />
    <FooterSocial.Link href="https://linkedin.com" icon={<LinkedInIcon />}
                        label="LinkedIn profile" />
  </FooterSocial>
</Footer>
```

---

## Related Components

- [Divider](/02-design-system/05-components/divider.md) -- Used to separate upper and lower footer sections.
- [Buttons](/02-design-system/05-components/buttons.md) -- Newsletter subscribe button.
- [Section Header](/02-design-system/05-components/section-header.md) -- Column headings within the footer follow a similar pattern.
- [Hero](/02-design-system/05-components/hero.md) -- The hero and footer bookend the page content.
