# SCSS Styles

The SCSS implementation of the Flavio Fusuma design token system. These stylesheets translate the W3C DTCG design tokens into production-ready CSS custom properties and utility classes.

---

## File Structure

```
04-styles/
  main.scss            Entry point — imports all partials in correct order
  _variables.scss      CSS custom properties + SCSS variables and mixins
  _reset.scss          Minimal, modern CSS reset
  _colors.scss         Color utility classes + dark mode overrides
  _typography.scss     Type scale, font families, weights, alignment
  _spacing.scss        Margin, padding, and gap utilities
  _grid.scss           Container, 12-column grid, column spans
```

## Import Order

Import order is critical. The `main.scss` entry point handles this automatically, but if you are importing partials individually, follow this sequence:

1. **`_variables.scss`** — Must come first. Defines all CSS custom properties and SCSS variables that other files depend on.
2. **`_reset.scss`** — Baseline normalization. Must precede utility classes to avoid specificity conflicts.
3. **`_colors.scss`** — Color utilities and dark mode token overrides.
4. **`_typography.scss`** — Type scale and text utilities.
5. **`_spacing.scss`** — Margin, padding, and gap classes.
6. **`_grid.scss`** — Container, grid, and layout system.

## Quick Start

### Option A: Import Everything

```scss
// In your project's main stylesheet
@use 'path/to/04-styles/main';
```

### Option B: Import Individual Modules

```scss
// Import variables first (required by all other modules)
@use 'path/to/04-styles/variables' as *;

// Then import only what you need
@use 'path/to/04-styles/reset';
@use 'path/to/04-styles/typography';
@use 'path/to/04-styles/grid';
```

### Option C: Variables Only (for Custom Builds)

```scss
// Just the CSS custom properties and SCSS utilities
@use 'path/to/04-styles/variables' as *;

// Now use custom properties in your own styles
.my-component {
  color: var(--color-text-primary);
  font-size: var(--font-size-base);
  padding: var(--space-4);
  border-radius: var(--radius-md);
}

// And the breakpoint mixin
.my-layout {
  flex-direction: column;

  @include breakpoint('md') {
    flex-direction: row;
  }
}
```

## Font Loading

The stylesheets reference Inter and JetBrains Mono via CSS custom properties but do not load the fonts. Add font loading to your HTML:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
```

Or self-host the fonts and declare `@font-face` rules before importing these styles.

## Dark Mode

Dark mode is activated by setting `data-theme="dark"` on a parent element (typically `<html>` or `<body>`):

```html
<html data-theme="dark">
```

All semantic color utilities (`.text-primary`, `.bg-secondary`, `.border-brand`, etc.) automatically update because the dark theme overrides the underlying CSS custom properties. No additional classes are needed.

### JavaScript Toggle

```js
function toggleTheme() {
  const html = document.documentElement;
  const current = html.getAttribute('data-theme');
  html.setAttribute('data-theme', current === 'dark' ? 'light' : 'dark');
}
```

## Utility Class Reference

### Colors

| Pattern | Example | Description |
|---------|---------|-------------|
| `.text-{semantic}` | `.text-primary` | Text color |
| `.bg-{semantic}` | `.bg-brand-subtle` | Background color |
| `.border-{semantic}` | `.border-error` | Border color |
| `.text-{palette}-{step}` | `.text-blue-600` | Primitive text color |
| `.bg-{palette}-{step}` | `.bg-amber-500` | Primitive background color |

### Typography

| Class | Description |
|-------|-------------|
| `.text-display-xl` through `.text-display-sm` | Display sizes (96px down to 48px) |
| `.text-h1` through `.text-h6` | Heading sizes (36px down to 16px) |
| `.text-body-xl` through `.text-body-xs` | Body text sizes |
| `.text-label-lg`, `.text-label-base`, `.text-label-sm` | Form labels |
| `.text-caption`, `.text-caption-sm` | Caption text |
| `.text-overline` | Overline / eyebrow (uppercase, tracked) |
| `.text-code-block`, `.text-code-inline` | Monospace code text |
| `.font-sans`, `.font-mono` | Font family |
| `.font-weight-{name}` | Font weight (thin through black) |
| `.text-left`, `.text-center`, `.text-right` | Text alignment |

### Spacing

| Pattern | Example | Description |
|---------|---------|-------------|
| `.m-{n}` | `.m-4` | Margin all sides (16px) |
| `.mx-{n}`, `.my-{n}` | `.mx-auto` | Horizontal / vertical margin |
| `.mt-{n}`, `.mr-{n}`, `.mb-{n}`, `.ml-{n}` | `.mt-8` | Single-side margin |
| `.p-{n}` | `.p-6` | Padding all sides (24px) |
| `.px-{n}`, `.py-{n}` | `.py-4` | Horizontal / vertical padding |
| `.gap-{n}` | `.gap-6` | Flex/grid gap |

### Grid

| Class | Description |
|-------|-------------|
| `.container` | Centered container with responsive max-widths |
| `.container-fluid` | Full-width container with padding |
| `.container-narrow` | Narrow container (720px max) for text content |
| `.grid` | 12-column CSS Grid |
| `.col-{n}` | Span n columns (1-12) |
| `.col-{bp}-{n}` | Responsive column span (e.g., `.col-md-8`) |
| `.col-start-{n}` | Column start position |

## Customization

### Overriding Variables

Override CSS custom properties in your own stylesheet to customize the system:

```scss
:root {
  // Change the primary brand color
  --color-blue-800: #YOUR_COLOR;

  // Adjust spacing base
  --space-2: 10px;

  // Use a different font
  --font-family-sans: 'Your Font', sans-serif;
}
```

### Overriding SCSS Variables

Override SCSS variables before importing to change breakpoints, grid settings, or spacing scales:

```scss
// Override before import
$breakpoints: (
  'sm': 480px,
  'md': 768px,
  'lg': 1024px,
  'xl': 1280px,
) !default;

$grid-columns: 12;
$grid-gutter: 32px;

@use 'path/to/04-styles/main';
```

### Extending the System

Add new utility classes that follow the same patterns:

```scss
@use 'path/to/04-styles/variables' as *;

// Add a new semantic color
:root {
  --color-bg-highlight: var(--color-amber-100);
}

.bg-highlight {
  background-color: var(--color-bg-highlight);
}

[data-theme="dark"] {
  --color-bg-highlight: #F59E0B26;
}
```

## Compilation

These files require a Sass compiler (Dart Sass recommended). They use the modern `@use` module system.

```bash
# Install Dart Sass
npm install -g sass

# Compile
sass 04-styles/main.scss dist/styles.css

# Compile with source maps (development)
sass --source-map 04-styles/main.scss dist/styles.css

# Compile compressed (production)
sass --style=compressed 04-styles/main.scss dist/styles.min.css

# Watch for changes
sass --watch 04-styles/main.scss dist/styles.css
```

## Design Token Relationship

These SCSS files are a direct implementation of the design tokens in `03-design-tokens/`. The mapping is:

| Token File | SCSS File | What It Produces |
|------------|-----------|------------------|
| `global/color.tokens.json` | `_variables.scss` | `--color-{palette}-{step}` custom properties |
| `global/typography.tokens.json` | `_variables.scss` | `--font-*`, `--line-height-*`, `--letter-spacing-*` |
| `global/spacing.tokens.json` | `_variables.scss` | `--space-{n}` custom properties |
| `global/border.tokens.json` | `_variables.scss` | `--radius-*`, `--border-width-*` |
| `global/shadow.tokens.json` | `_variables.scss` | `--shadow-*` custom properties |
| `global/motion.tokens.json` | `_variables.scss` | `--duration-*`, `--ease-*` |
| `semantic/color.tokens.json` | `_variables.scss` | `--color-bg-*`, `--color-text-*`, `--color-border-*` |
| `themes/dark.tokens.json` | `_colors.scss` | `[data-theme="dark"]` overrides |

---

**Version**: 1.0.0
**Last Updated**: April 2026
