# Developer Handoff Guide

## Overview

This guide bridges the gap between the Flavio Fusuma Design System and its implementation in code. It covers naming conventions, token-to-CSS mapping, component architecture, and quality standards to ensure consistent, maintainable implementation.

---

## 1. Token-to-CSS Variable Mapping

Design tokens are the single source of truth. CSS custom properties are generated from the JSON token files using Style Dictionary.

### Naming Convention

```
Token:    color.blue.600
CSS var:  --ff-color-blue-600
SCSS var: $ff-color-blue-600
Class:    .ff-text-blue-600, .ff-bg-blue-600
```

### Mapping Rules

| Token Layer | CSS Variable Prefix | Example |
|-------------|-------------------|---------|
| Global colors | `--ff-color-{name}-{shade}` | `--ff-color-blue-600` |
| Semantic colors | `--ff-color-{role}-{variant}` | `--ff-color-action-primary` |
| Typography | `--ff-font-{property}-{value}` | `--ff-font-size-body-md` |
| Spacing | `--ff-space-{scale}` | `--ff-space-4` |
| Border | `--ff-radius-{size}` | `--ff-radius-md` |
| Shadow | `--ff-shadow-{level}` | `--ff-shadow-md` |
| Motion | `--ff-duration-{name}` | `--ff-duration-normal` |

### Theme Switching

Themes are applied via a `data-theme` attribute on the root element:

```css
:root, [data-theme="light"] {
  --ff-color-surface-primary: var(--ff-color-neutral-0);
  --ff-color-text-primary: var(--ff-color-neutral-900);
}

[data-theme="dark"] {
  --ff-color-surface-primary: var(--ff-color-neutral-900);
  --ff-color-text-primary: var(--ff-color-neutral-50);
}
```

**Rule**: Always use semantic tokens in component CSS. Never reference global primitives directly in component styles.

```css
/* Correct */
.ff-card { background: var(--ff-color-surface-primary); }

/* Incorrect */
.ff-card { background: var(--ff-color-neutral-0); }
```

---

## 2. Component Naming Convention (BEM)

All components follow BEM (Block Element Modifier) with the `ff-` prefix.

### Structure

```
.ff-{block}
.ff-{block}__{element}
.ff-{block}--{modifier}
.ff-{block}__{element}--{modifier}
```

### Examples

```html
<!-- Button component -->
<button class="ff-button ff-button--primary ff-button--lg">
  <span class="ff-button__icon">...</span>
  <span class="ff-button__label">Get in Touch</span>
</button>

<!-- Card component -->
<article class="ff-card ff-card--elevated">
  <div class="ff-card__media">
    <img class="ff-card__image" src="..." alt="..." />
  </div>
  <div class="ff-card__body">
    <h3 class="ff-card__title">Project Name</h3>
    <p class="ff-card__description">Description text</p>
  </div>
  <div class="ff-card__footer">
    <a class="ff-card__action" href="#">View Project</a>
  </div>
</article>

<!-- Input component -->
<div class="ff-input ff-input--error">
  <label class="ff-input__label" for="email">Email</label>
  <input class="ff-input__field" id="email" type="email" />
  <span class="ff-input__message ff-input__message--error">
    Please enter a valid email address.
  </span>
</div>
```

### Naming Rules

1. **Block names** are lowercase, hyphen-separated: `ff-project-card`
2. **Element names** are lowercase, hyphen-separated: `ff-card__footer-action`
3. **Modifier names** describe the variation: `--primary`, `--lg`, `--disabled`
4. **State classes** use `is-` prefix: `is-active`, `is-open`, `is-loading`
5. **JS hooks** use `js-` prefix: `js-toggle`, `js-modal-trigger` (never styled)

---

## 3. CSS Architecture

### File Organization

```
styles/
├── main.scss              # Entry point
├── _variables.scss        # CSS custom properties from tokens
├── _reset.scss            # Minimal reset / normalize
├── _colors.scss           # Color utility classes
├── _typography.scss       # Type scale classes
├── _spacing.scss          # Margin, padding, gap utilities
├── _grid.scss             # Grid system
└── components/            # Component-specific styles (if needed)
    ├── _button.scss
    ├── _card.scss
    └── ...
```

### Import Order

```scss
// 1. Settings (tokens, variables)
@use 'variables';

// 2. Reset/normalize
@use 'reset';

// 3. Base elements
@use 'typography';
@use 'colors';

// 4. Layout
@use 'grid';
@use 'spacing';

// 5. Components (if using SCSS components)
// @use 'components/button';
// @use 'components/card';
```

### CSS Property Order

Within a selector, order properties consistently:

```css
.ff-component {
  /* 1. Layout / Position */
  display: flex;
  position: relative;
  z-index: 1;

  /* 2. Box Model */
  width: 100%;
  padding: var(--ff-space-4);
  margin-bottom: var(--ff-space-4);
  border: 1px solid var(--ff-color-border-default);
  border-radius: var(--ff-radius-md);

  /* 3. Typography */
  font-family: var(--ff-font-family-sans);
  font-size: var(--ff-font-size-body-md);
  font-weight: var(--ff-font-weight-regular);
  line-height: var(--ff-line-height-normal);
  color: var(--ff-color-text-primary);

  /* 4. Visual */
  background: var(--ff-color-surface-primary);
  box-shadow: var(--ff-shadow-sm);

  /* 5. Animation */
  transition: background-color var(--ff-duration-fast) var(--ff-easing-default);

  /* 6. Misc */
  cursor: pointer;
}
```

---

## 4. Responsive Implementation

### Mobile-First Approach

Write base styles for mobile, then layer on complexity:

```css
.ff-hero__title {
  font-size: var(--ff-font-size-heading-lg);    /* Mobile default */
}

@media (min-width: 768px) {
  .ff-hero__title {
    font-size: var(--ff-font-size-display-lg);   /* Tablet+ */
  }
}

@media (min-width: 1024px) {
  .ff-hero__title {
    font-size: var(--ff-font-size-display-xl);   /* Desktop+ */
  }
}
```

### Breakpoint Variables

```scss
$ff-breakpoint-sm:  640px;   // Small devices
$ff-breakpoint-md:  768px;   // Tablets
$ff-breakpoint-lg:  1024px;  // Desktops
$ff-breakpoint-xl:  1280px;  // Large desktops
$ff-breakpoint-2xl: 1440px;  // Wide screens
```

### Container Widths

| Breakpoint | Container Max-Width | Side Padding |
|------------|-------------------|-------------|
| < 640px | 100% | 16px |
| 640–767px | 100% | 24px |
| 768–1023px | 720px | 24px |
| 1024–1279px | 960px | 32px |
| 1280–1439px | 1152px | 32px |
| ≥ 1440px | 1280px | 32px |

---

## 5. Accessibility Implementation Checklist

For every component implementation, verify:

- [ ] Semantic HTML used (button, nav, main, etc.)
- [ ] Keyboard navigable (Tab, Enter/Space, Escape, Arrow keys)
- [ ] Focus visible and meets contrast requirements
- [ ] ARIA attributes applied where semantic HTML is insufficient
- [ ] Color is not the sole indicator of state
- [ ] Touch targets ≥ 44×44px
- [ ] `prefers-reduced-motion` respected
- [ ] Screen reader tested (announcements make sense)
- [ ] Works at 200% zoom without horizontal scroll
- [ ] Works at 320px viewport width

---

## 6. Browser Support

| Browser | Version | Support Level |
|---------|---------|--------------|
| Chrome | Last 2 versions | Full |
| Firefox | Last 2 versions | Full |
| Safari | Last 2 versions | Full |
| Edge | Last 2 versions | Full |
| iOS Safari | Last 2 versions | Full |
| Chrome Android | Last 2 versions | Full |
| Samsung Internet | Last 2 versions | Full |

### CSS Feature Requirements
- CSS Custom Properties (variables)
- CSS Grid Layout
- CSS Flexbox
- `gap` property for Flexbox
- `clamp()` for fluid typography
- `prefers-reduced-motion` media query
- `prefers-color-scheme` media query
- Container queries (progressive enhancement)

---

## 7. Performance Guidelines

### CSS Performance
- Load critical CSS inline (above-the-fold styles, ~14KB max)
- Lazy-load non-critical stylesheets
- Avoid deeply nested selectors (max 3 levels)
- Minimize use of `!important` (only for utility overrides)
- Use CSS custom properties for theming (one repaint vs. many)

### Font Performance
- Use `font-display: swap` for all custom fonts
- Preconnect to font CDN: `<link rel="preconnect" href="https://fonts.googleapis.com">`
- Subset fonts if not using full character set
- Load variable fonts (one file vs. multiple weight files)

### Image Guidelines
- Use `loading="lazy"` for below-fold images
- Provide `width` and `height` attributes to prevent layout shift
- Use WebP/AVIF with fallbacks
- Responsive images with `srcset` and `sizes`

### Animation Performance
- Only animate `transform` and `opacity` (GPU-accelerated)
- Use `will-change` sparingly and only when needed
- Avoid animating `width`, `height`, `top`, `left` (triggers layout)

---

## 8. Code Review Checklist

When reviewing design system implementation:

### Tokens & Consistency
- [ ] Uses semantic CSS variables, not hardcoded values
- [ ] Colors reference semantic tokens (not global primitives)
- [ ] Spacing uses the defined scale (no arbitrary pixel values)
- [ ] Typography uses the type scale classes or tokens

### Structure
- [ ] BEM naming convention followed with `ff-` prefix
- [ ] Semantic HTML elements used appropriately
- [ ] No inline styles (except dynamic values from JS)
- [ ] CSS properties ordered consistently

### Responsiveness
- [ ] Mobile-first media queries
- [ ] Tested at all defined breakpoints
- [ ] No horizontal overflow at any viewport width
- [ ] Touch targets adequate on mobile

### Accessibility
- [ ] All items in the accessibility checklist (Section 5) pass
- [ ] No `outline: none` without visible alternative
- [ ] Interactive elements have hover, focus, and active states
- [ ] Form inputs have associated labels

### Performance
- [ ] No unnecessary CSS (unused selectors)
- [ ] Animations use GPU-accelerated properties only
- [ ] Images optimized and lazy-loaded
- [ ] Fonts loaded efficiently

---

## 9. Component Implementation Template

When implementing a new component:

```css
/**
 * Component: ff-example
 * Description: Brief description of the component
 * Tokens: Lists referenced design tokens
 * See: 02-design-system/05-components/example.md
 */

/* Block */
.ff-example {
  display: flex;
  align-items: center;
  padding: var(--ff-space-3) var(--ff-space-4);
  border: 1px solid var(--ff-color-border-default);
  border-radius: var(--ff-radius-md);
  background: var(--ff-color-surface-primary);
  color: var(--ff-color-text-primary);
  font-family: var(--ff-font-family-sans);
  font-size: var(--ff-font-size-body-md);
  transition: border-color var(--ff-duration-fast) var(--ff-easing-default),
              box-shadow var(--ff-duration-fast) var(--ff-easing-default);
}

/* States */
.ff-example:hover {
  border-color: var(--ff-color-border-hover);
}

.ff-example:focus-within {
  border-color: var(--ff-color-action-primary);
  box-shadow: 0 0 0 2px var(--ff-color-action-primary-light);
}

.ff-example.is-disabled {
  opacity: var(--ff-opacity-disabled);
  pointer-events: none;
}

/* Elements */
.ff-example__label {
  font-weight: var(--ff-font-weight-medium);
}

.ff-example__icon {
  width: 20px;
  height: 20px;
  margin-right: var(--ff-space-2);
  color: var(--ff-color-text-secondary);
}

/* Modifiers */
.ff-example--lg {
  padding: var(--ff-space-4) var(--ff-space-6);
  font-size: var(--ff-font-size-body-lg);
}

/* Responsive */
@media (prefers-reduced-motion: reduce) {
  .ff-example {
    transition: none;
  }
}
```
