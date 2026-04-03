# Global Accessibility Guidelines

## Overview

The Flavio Fusuma Design System is built to meet **WCAG 2.1 Level AA** compliance as a minimum standard, with **Level AAA** applied wherever practical. Accessibility is not an afterthought — it is a core design principle that influences every decision, from color selection to component architecture.

---

## 1. Compliance Standards

| Standard | Requirement | Our Target |
|----------|------------|------------|
| WCAG 2.1 Level A | Minimum baseline | Required |
| WCAG 2.1 Level AA | Industry standard | Required |
| WCAG 2.1 Level AAA | Highest compliance | Applied where feasible |
| Section 508 | US federal requirement | Compliant |
| EN 301 549 | EU accessibility standard | Compliant |

---

## 2. Color & Contrast

### Text Contrast Requirements

| Text Type | Minimum Ratio (AA) | Enhanced Ratio (AAA) | Our Standard |
|-----------|-------------------|---------------------|--------------|
| Normal text (<18px) | 4.5:1 | 7:1 | 4.5:1 minimum |
| Large text (≥18px bold, ≥24px) | 3:1 | 4.5:1 | 4.5:1 target |
| UI components & graphics | 3:1 | — | 3:1 minimum |
| Placeholder text | 4.5:1 | — | 4.5:1 minimum |

### Color Independence
- Never use color as the **sole** means of conveying information
- Always pair color with: text labels, icons, patterns, or shape
- Examples:
  - Error states: Red color + error icon + error text
  - Success states: Green color + checkmark icon + success text
  - Charts: Color + pattern fills + labels

### Focus Indicators
- Visible focus ring on all interactive elements
- Focus ring: 2px solid `blue-500`, 2px offset
- Contrast ratio of focus indicator against adjacent colors: ≥3:1
- Never use `outline: none` without a visible alternative

---

## 3. Keyboard Navigation

### General Requirements
- All interactive elements reachable via `Tab` key
- Logical tab order matching visual layout (left-to-right, top-to-bottom)
- No keyboard traps (except intentional: modals, dialogs)
- `Escape` key closes overlays (modals, dropdowns, tooltips)

### Expected Keyboard Interactions

| Component | Keys | Behavior |
|-----------|------|----------|
| Button | `Enter`, `Space` | Activate |
| Link | `Enter` | Navigate |
| Checkbox | `Space` | Toggle |
| Radio | `Arrow keys` | Navigate within group |
| Select/Dropdown | `Arrow keys`, `Enter`, `Escape` | Navigate, select, close |
| Tabs | `Arrow keys` | Switch tabs |
| Modal | `Tab` (trapped), `Escape` | Navigate within, close |
| Accordion | `Enter`, `Space` | Toggle section |
| Menu | `Arrow keys`, `Enter`, `Escape` | Navigate, select, close |
| Slider | `Arrow keys` | Adjust value |
| Tooltip | `Escape` | Dismiss |

### Skip Links
- First focusable element on every page: "Skip to main content"
- Additional skip links for complex layouts: "Skip to navigation", "Skip to footer"
- Visually hidden until focused

```html
<a href="#main-content" class="ff-skip-link">
  Skip to main content
</a>
```

```css
.ff-skip-link {
  position: absolute;
  top: -100%;
  left: 16px;
  z-index: 100;
  padding: 8px 16px;
  background: var(--color-blue-600);
  color: var(--color-neutral-0);
  border-radius: var(--radius-md);
  text-decoration: none;
  font-weight: 600;
}
.ff-skip-link:focus {
  top: 16px;
}
```

---

## 4. Screen Reader Support

### Semantic HTML
Always use semantic HTML elements before resorting to ARIA:

| Purpose | Use This | Not This |
|---------|----------|----------|
| Navigation | `<nav aria-label="Main">` | `<div role="navigation">` |
| Main content | `<main>` | `<div role="main">` |
| Headings | `<h1>` – `<h6>` | `<div class="heading">` |
| Lists | `<ul>`, `<ol>` | `<div>` with bullet styling |
| Buttons | `<button>` | `<div onclick>` |
| Links | `<a href>` | `<span onclick>` |
| Form inputs | `<input>`, `<select>`, `<textarea>` | Custom `<div>` elements |

### ARIA Landmarks

Every page must include these landmarks:

| Landmark | Element | Required |
|----------|---------|----------|
| Banner | `<header>` | Yes (one per page) |
| Navigation | `<nav aria-label="...">` | Yes (label each) |
| Main | `<main>` | Yes (one per page) |
| Contentinfo | `<footer>` | Yes (one per page) |
| Complementary | `<aside>` | When sidebar exists |
| Search | `<search>` or `role="search"` | When search exists |

### ARIA Attributes Guide

| Attribute | Usage |
|-----------|-------|
| `aria-label` | Provide accessible name when no visible label |
| `aria-labelledby` | Reference visible element as the label |
| `aria-describedby` | Reference element providing additional description |
| `aria-expanded` | Indicate expandable controls (accordion, dropdown) |
| `aria-hidden` | Hide decorative elements from screen readers |
| `aria-live` | Announce dynamic content changes ("polite" or "assertive") |
| `aria-current` | Indicate current item (page, step, date) |
| `aria-required` | Indicate required form fields |
| `aria-invalid` | Indicate validation errors |

### Live Regions

For dynamic content updates (toasts, form errors, loading states):

```html
<!-- Polite: announced at next pause (toasts, status updates) -->
<div role="status" aria-live="polite">
  Your message has been sent.
</div>

<!-- Assertive: announced immediately (critical errors) -->
<div role="alert" aria-live="assertive">
  Session expired. Please log in again.
</div>
```

---

## 5. Form Accessibility

### Labels
- Every form input **must** have a visible `<label>` associated via `for`/`id`
- Group related inputs with `<fieldset>` and `<legend>`
- Never use placeholder as a replacement for labels

### Error Handling
- Errors announced via `aria-invalid="true"` and `aria-describedby`
- Error summary at top of form for server-side validation
- Inline errors next to the relevant field
- Error messages are specific: "Email address must include @" not "Invalid input"

### Required Fields
- Mark required fields with `aria-required="true"` and visible indicator
- Explain the indicator: "Fields marked with * are required"

```html
<div class="ff-input-group">
  <label for="email">
    Email address <span aria-hidden="true">*</span>
  </label>
  <input
    type="email"
    id="email"
    aria-required="true"
    aria-invalid="false"
    aria-describedby="email-hint"
  />
  <span id="email-hint" class="ff-input__hint">
    We'll use this to respond to your inquiry.
  </span>
</div>
```

---

## 6. Touch & Pointer

### Touch Target Sizes

| Element | Minimum Size | Recommended | Spacing |
|---------|-------------|-------------|---------|
| Buttons | 44×44px | 48×48px | 8px between |
| Links (inline) | 44px height | — | Sufficient padding |
| Icons (interactive) | 44×44px | 48×48px | 8px between |
| Form inputs | 44px height | 48px height | — |
| Checkboxes/Radios | 44×44px touch area | — | 8px between |

### Implementation
- Touch targets can be larger than the visible element using padding or `::before`/`::after`
- Minimum 8px spacing between adjacent touch targets
- Test with actual touch devices, not just browser emulation

---

## 7. Motion & Animation

### Reduced Motion

All animations must respect `prefers-reduced-motion`:

```css
/* Default: animations on */
.ff-component {
  transition: transform 200ms ease, opacity 200ms ease;
}

/* Reduced motion: disable or simplify */
@media (prefers-reduced-motion: reduce) {
  .ff-component {
    transition: none;
  }
}
```

### Animation Guidelines
- No content that flashes more than 3 times per second
- Auto-playing animations should be pausable
- Parallax scrolling should be disabled for reduced motion
- Loading spinners: simplify to opacity pulse in reduced motion mode
- Page transitions: instant in reduced motion mode

---

## 8. Images & Media

### Images
- All informational images must have descriptive `alt` text
- Decorative images use `alt=""` and `aria-hidden="true"`
- Complex images (charts, diagrams) need long descriptions

```html
<!-- Informational -->
<img src="project-screenshot.png" alt="Dashboard showing real-time analytics with three chart widgets" />

<!-- Decorative -->
<img src="decorative-pattern.svg" alt="" aria-hidden="true" />

<!-- Complex -->
<figure>
  <img src="architecture-diagram.png" alt="System architecture diagram" aria-describedby="arch-desc" />
  <figcaption id="arch-desc">
    The system uses a microservices architecture with three main services:
    authentication, data processing, and notification...
  </figcaption>
</figure>
```

### Video & Audio
- Provide captions for all video content
- Provide transcripts for audio content
- Auto-play is disabled by default
- Player controls are keyboard accessible

---

## 9. Typography & Readability

- Minimum body text size: 16px (never smaller for primary content)
- Minimum secondary text size: 14px
- Line height: 1.5 for body text (WCAG SC 1.4.12)
- Paragraph max-width: 65–75 characters for optimal readability
- Text can be resized up to 200% without loss of content (WCAG SC 1.4.4)
- No horizontal scrolling at 320px viewport width (WCAG SC 1.4.10)
- Text spacing adjustable: line height 1.5×, paragraph spacing 2×, word spacing 0.16×, letter spacing 0.12× (WCAG SC 1.4.12)

---

## 10. Testing Checklist

### Automated Testing
- [ ] Run axe-core or Lighthouse accessibility audit
- [ ] Validate HTML with W3C validator
- [ ] Check color contrast with automated tools
- [ ] Lint for missing alt text, labels, ARIA

### Manual Testing
- [ ] Navigate entire page with keyboard only
- [ ] Test with screen reader (VoiceOver, NVDA, or JAWS)
- [ ] Verify focus order matches visual order
- [ ] Test at 200% zoom — no horizontal scroll, no content loss
- [ ] Test at 320px width — responsive, no overflow
- [ ] Test with `prefers-reduced-motion: reduce`
- [ ] Test with high contrast mode
- [ ] Test with browser text resizing (not zoom)

### Screen Reader Testing Matrix

| Browser | Screen Reader | OS |
|---------|--------------|-----|
| Chrome | NVDA | Windows |
| Firefox | NVDA | Windows |
| Safari | VoiceOver | macOS |
| Safari | VoiceOver | iOS |
| Chrome | TalkBack | Android |

### Recommended Tools

| Tool | Purpose |
|------|---------|
| axe DevTools | Automated accessibility testing |
| Lighthouse | Performance + accessibility audit |
| WAVE | Visual accessibility evaluation |
| Colour Contrast Analyser | Manual contrast checking |
| NVDA | Free Windows screen reader |
| VoiceOver | Built-in macOS/iOS screen reader |
| Accessibility Insights | Microsoft's testing tool |

---

## 11. Content Accessibility

- Use clear, simple language (aim for 8th-grade reading level for general content)
- Provide descriptive link text ("Read the case study" not "Click here")
- Use proper heading hierarchy (never skip levels)
- Provide text alternatives for all non-text content
- Ensure content is understandable without CSS (structural HTML order)
- Support both left-to-right and right-to-left text direction
- Use `lang` attribute on `<html>` and for any inline language changes
