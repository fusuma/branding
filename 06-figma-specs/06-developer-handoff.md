# Developer Handoff Setup

> Guidelines for preparing Figma designs for developer handoff, including inspect panel usage, export settings, annotation standards, and token-to-code mapping for the Flavio Fusuma Design System.

---

## Inspect Panel Usage Guidelines

### What Developers See

When a developer selects a layer in Figma's Dev Mode or Inspect panel, they see:

- **Position and dimensions** (x, y, width, height)
- **Auto-layout properties** (direction, gap, padding, alignment)
- **Fill, stroke, and effects** (colors, borders, shadows)
- **Typography** (font family, size, weight, line height, letter spacing)
- **Corner radius**
- **Component properties** (variant, boolean, text, instance swap)
- **CSS reference** (auto-generated)

### Best Practices for Accurate Inspect Data

1. **Use variables everywhere.** When a developer inspects a color fill, they should see the variable name (e.g., `color-bg-brand`) not a raw hex value. This maps directly to CSS custom properties.

2. **Use auto-layout, not manual positioning.** Auto-layout translates to flexbox properties. Manual positioning produces absolute coordinates that are meaningless in responsive implementation.

3. **Use text styles.** Named text styles in Figma (e.g., `Heading / H2`, `Body / Regular / md`) help developers identify which typography token to use.

4. **Use effect styles for shadows.** Named effect styles (e.g., `Elevation / sm`, `Elevation / md`) map to shadow tokens.

5. **Name every layer.** Layer names become class name hints. `icon-leading` tells the developer exactly what to name the element.

6. **Set constraints and resizing.** The inspect panel shows resizing behavior (Hug, Fill, Fixed) which informs the developer whether to use `flex: 1`, `width: fit-content`, or a fixed pixel value.

### What to Verify Before Handoff

- [ ] No raw hex values -- all colors reference Figma variables
- [ ] No raw font sizes -- all text uses shared text styles
- [ ] No unnamed layers (no "Frame 12", "Group 4", "Rectangle 9")
- [ ] Auto-layout is used wherever possible
- [ ] Component properties are correctly set (not overridden detached instances)
- [ ] Spacing annotations are present for any non-obvious values
- [ ] All icons are component instances from the icon library (not pasted SVGs)

---

## CSS Reference Generation

### Figma Dev Mode Settings

Configure Dev Mode for optimal CSS output:

| Setting | Value | Reason |
|---|---|---|
| Unit | px | Matches token definitions; developers convert to rem in code |
| Color format | HEX | Matches token values; developers reference CSS variables instead |
| Show variable names | Enabled | Shows `var(--ff-color-bg-brand)` references |
| Code syntax | CSS | Default output language |

### CSS Output Expectations

For a primary button (md, default state), Figma's inspect panel should output approximately:

```css
/* Layout */
display: flex;
flex-direction: row;
align-items: center;
justify-content: center;
gap: 8px;
padding: 8px 16px;

/* Sizing */
height: 40px;

/* Visual */
background: var(--ff-color-bg-brand);     /* #2563EB via variable */
border-radius: 8px;

/* Typography */
font-family: 'Inter', sans-serif;
font-size: 14px;
font-weight: 600;
line-height: 20px;
color: var(--ff-color-text-on-brand);     /* #FFFFFF via variable */
```

Developers should not copy this CSS verbatim. Instead, use it as reference to identify:
- Which tokens to use
- What the expected layout model is (flex, grid)
- What the dimensions and spacing should be

---

## Export Settings

### Icons (SVG)

All icons are exported as SVG for maximum flexibility.

| Setting | Value |
|---|---|
| Format | SVG |
| Include "id" attribute | No |
| Outline text | Yes |
| Flatten transforms | Yes |
| Naming convention | `icon-[name].svg` (kebab-case) |

Export icons from the `FF - Foundations` file, Icon section. Each icon is a 24x24 component. Export at 1x scale.

Configure SVG export presets:

```
Suffix:       (none)
Constraint:   Scale 1x
Format:       SVG
```

### Images (PNG)

Images (photos, illustrations, thumbnails) export at multiple densities.

| Format | Scale | Suffix | Use Case |
|---|---|---|---|
| PNG | 1x | (none) | Standard displays |
| PNG | 2x | `@2x` | Retina / high-DPI |
| PNG | 3x | `@3x` | Mobile (3x DPI devices) |
| WebP | 1x | (none) | Modern browsers (preferred) |

Configure export presets on image layers:

```
Export 1:  PNG, 1x,  suffix ""
Export 2:  PNG, 2x,  suffix "@2x"
Export 3:  PNG, 3x,  suffix "@3x"
Export 4:  WebP, 1x, suffix ""      (optional, for modern optimization)
```

### Logos and Brand Marks

| Asset | Formats | Sizes |
|---|---|---|
| Primary logo | SVG, PNG @1x/@2x/@3x | Variable (SVG), 200px width (PNG) |
| Logo mark (icon) | SVG, PNG @1x/@2x/@3x | Variable (SVG), 64px (PNG) |
| Favicon | PNG | 16x16, 32x32, 180x180 (apple-touch), 192x192, 512x512 |
| Social OG image | PNG, JPG | 1200x630 |

### Export Naming Convention

```
[category]-[name]-[variant]@[scale].[format]
```

Examples:

```
icon-arrow-right.svg
icon-search.svg
logo-primary-dark.svg
logo-mark-light.png
logo-mark-light@2x.png
logo-mark-light@3x.png
image-hero-homepage.png
image-hero-homepage@2x.png
image-project-thumb-01.webp
```

---

## Annotation Standards

### Spacing Annotations

Use `_Annotation / Spacing` frames to call out non-obvious spacing values. Each annotation consists of:

| Element | Visual | Spec |
|---|---|---|
| Measurement line | Red (#EF4444) line, 1px weight | Connects the two edges being measured |
| Value label | Red background pill, white text | Shows the pixel value and token name |
| Arrow heads | Small red triangles at each end | Indicate measurement direction |

Example annotation format:

```
├── 24px (space-3) ──┤
```

#### When to Annotate Spacing

- Padding inside components (top, right, bottom, left)
- Gap between sibling elements
- Margin between sections
- Any value that is not immediately obvious from the auto-layout panel

#### When Spacing Annotations Are Not Needed

- When auto-layout gap and padding values are visible in the inspect panel and clearly map to tokens
- Between elements in a well-structured auto-layout frame

### Alignment Annotations

Use `_Annotation / Alignment` frames to indicate:

| Annotation | Visual | Meaning |
|---|---|---|
| Center line | Dashed blue (#2563EB) line | Elements are centered on this axis |
| Baseline alignment | Dashed green (#10B981) line | Text baselines are aligned |
| Edge alignment | Solid red (#EF4444) line | Elements share a common edge |

### Breakpoint Annotations

For responsive designs, include a `_Annotation / Responsive Behavior` frame showing:

1. All four breakpoint frames side by side (scaled to fit).
2. Red lines connecting elements that change position or visibility.
3. Notes explaining what changes at each breakpoint:

```
Mobile (375):     Single column, nav collapsed, hero image above text
Tablet (768):     Two columns for cards, nav visible, hero side-by-side
Desktop (1024):   Three columns for cards, sidebar appears
Desktop (1440):   Same as 1024 with wider margins
```

### Interaction Annotations

Use `_Annotation / Interaction` frames for hover, focus, and active states:

| Label | Description |
|---|---|
| `[HOVER]` | Shows the visual change on mouse hover |
| `[FOCUS]` | Shows the focus ring and any visual shift |
| `[ACTIVE]` | Shows the pressed/active state |
| `[DISABLED]` | Shows the disabled appearance |
| `[ERROR]` | Shows validation error state |
| `[LOADING]` | Shows loading/skeleton state |

---

## Token-to-Code Mapping Reference

### Color Tokens

| Figma Variable | CSS Custom Property | Example Value (Light) |
|---|---|---|
| `color/bg/primary` | `--ff-color-bg-primary` | `#FFFFFF` |
| `color/bg/secondary` | `--ff-color-bg-secondary` | `#F9FAFB` |
| `color/bg/brand` | `--ff-color-bg-brand` | `#2563EB` |
| `color/bg/accent` | `--ff-color-bg-accent` | `#F59E0B` |
| `color/text/primary` | `--ff-color-text-primary` | `#111827` |
| `color/text/secondary` | `--ff-color-text-secondary` | `#4B5563` |
| `color/text/brand` | `--ff-color-text-brand` | `#2563EB` |
| `color/text/on-brand` | `--ff-color-text-on-brand` | `#FFFFFF` |
| `color/border/default` | `--ff-color-border-default` | `#D1D5DB` |
| `color/border/focus` | `--ff-color-border-focus` | `#2563EB` |

### Spacing Tokens

| Figma Variable | CSS Custom Property | Value |
|---|---|---|
| `space/0.5` | `--ff-space-0-5` | `4px` |
| `space/1` | `--ff-space-1` | `8px` |
| `space/1.5` | `--ff-space-1-5` | `12px` |
| `space/2` | `--ff-space-2` | `16px` |
| `space/3` | `--ff-space-3` | `24px` |
| `space/4` | `--ff-space-4` | `32px` |
| `space/5` | `--ff-space-5` | `40px` |
| `space/6` | `--ff-space-6` | `48px` |
| `space/8` | `--ff-space-8` | `64px` |
| `space/10` | `--ff-space-10` | `80px` |
| `space/12` | `--ff-space-12` | `96px` |
| `space/16` | `--ff-space-16` | `128px` |

### Typography Tokens

| Figma Text Style | CSS Custom Properties |
|---|---|
| `Heading / H1` | `font-size: var(--ff-font-size-3xl)` (30px), `font-weight: var(--ff-font-weight-bold)` (700), `line-height: var(--ff-line-height-tight)` (1.25), `font-family: 'Inter'` |
| `Heading / H2` | `font-size: var(--ff-font-size-2xl)` (24px), `font-weight: 700`, `line-height: 1.25` |
| `Heading / H3` | `font-size: var(--ff-font-size-xl)` (20px), `font-weight: 600`, `line-height: 1.3` |
| `Heading / H4` | `font-size: var(--ff-font-size-lg)` (18px), `font-weight: 600`, `line-height: 1.4` |
| `Body / Regular / md` | `font-size: var(--ff-font-size-base)` (16px), `font-weight: 400`, `line-height: 1.5` |
| `Body / Regular / sm` | `font-size: var(--ff-font-size-sm)` (14px), `font-weight: 400`, `line-height: 1.5` |
| `Body / Regular / xs` | `font-size: var(--ff-font-size-xs)` (12px), `font-weight: 400`, `line-height: 1.5` |
| `Code / Block` | `font-family: 'JetBrains Mono'`, `font-size: var(--ff-font-size-sm)` (14px), `line-height: 1.6` |
| `Code / Inline` | `font-family: 'JetBrains Mono'`, `font-size: 0.875em`, `line-height: inherit` |

### Radius Tokens

| Figma Variable | CSS Custom Property | Value |
|---|---|---|
| `radius/none` | `--ff-radius-none` | `0px` |
| `radius/sm` | `--ff-radius-sm` | `4px` |
| `radius/md` | `--ff-radius-md` | `8px` |
| `radius/lg` | `--ff-radius-lg` | `12px` |
| `radius/xl` | `--ff-radius-xl` | `16px` |
| `radius/full` | `--ff-radius-full` | `9999px` |

### Shadow Tokens

| Figma Effect Style | CSS Custom Property | Value |
|---|---|---|
| `Elevation / sm` | `--ff-shadow-sm` | `0 1px 2px 0 rgba(0,0,0,0.05)` |
| `Elevation / md` | `--ff-shadow-md` | `0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -2px rgba(0,0,0,0.1)` |
| `Elevation / lg` | `--ff-shadow-lg` | `0 10px 15px -3px rgba(0,0,0,0.1), 0 4px 6px -4px rgba(0,0,0,0.1)` |
| `Elevation / xl` | `--ff-shadow-xl` | `0 20px 25px -5px rgba(0,0,0,0.1), 0 8px 10px -6px rgba(0,0,0,0.1)` |

---

## Naming Convention Alignment: Figma Layers to CSS Classes

The Flavio Fusuma system uses BEM naming in CSS. Figma layer names inform CSS class names.

### BEM Convention

```
Block:     ff-[component]
Element:   ff-[component]__[element]
Modifier:  ff-[component]--[modifier]
```

### Mapping Table

| Figma Layer Name | CSS Class | Notes |
|---|---|---|
| `button` (component) | `.ff-button` | Block |
| `text-label` (inside button) | `.ff-button__label` | Element |
| `icon-leading` (inside button) | `.ff-button__icon--leading` | Element + modifier |
| `icon-trailing` (inside button) | `.ff-button__icon--trailing` | Element + modifier |
| Primary variant | `.ff-button--primary` | Modifier |
| Secondary variant | `.ff-button--secondary` | Modifier |
| Size sm | `.ff-button--sm` | Modifier |
| Size lg | `.ff-button--lg` | Modifier |
| Disabled state | `.ff-button--disabled` or `[disabled]` | Prefer attribute |
| `card` | `.ff-card` | Block |
| `card-media` | `.ff-card__media` | Element |
| `card-body` | `.ff-card__body` | Element |
| `card-footer` | `.ff-card__footer` | Element |
| `text-title` (in card) | `.ff-card__title` | Element |
| `text-description` (in card) | `.ff-card__description` | Element |
| `input-field` | `.ff-input` | Block |
| `text-label` (in input) | `.ff-input__label` | Element |
| `input-container` | `.ff-input__field` | Element (the actual input) |
| `slot-prefix` | `.ff-input__prefix` | Element |
| `slot-suffix` | `.ff-input__suffix` | Element |
| `text-helper` | `.ff-input__helper` | Element |
| Error state | `.ff-input--error` | Modifier |
| `nav-bar` | `.ff-nav` | Block |
| `nav-left` | `.ff-nav__brand` | Element |
| `nav-center` | `.ff-nav__links` | Element |
| `nav-right` | `.ff-nav__actions` | Element |
| `nav-link` | `.ff-nav__link` | Element |
| Active nav link | `.ff-nav__link--active` | Modifier |
| `modal-container` | `.ff-modal` | Block |
| `modal-header` | `.ff-modal__header` | Element |
| `modal-body` | `.ff-modal__body` | Element |
| `modal-footer` | `.ff-modal__footer` | Element |
| `bg-overlay` | `.ff-modal__overlay` | Element |

### Layer Name to Class Name Rules

1. The component root layer name maps to the BEM block: `ff-[layer-name]`.
2. Child layers map to BEM elements: `ff-[block]__[child-name]`.
3. Drop the `text-`, `slot-`, `icon-` prefix when forming the BEM element name (e.g., `text-label` becomes `__label`).
4. Variant property values map to BEM modifiers: `ff-[block]--[variant-value]`.
5. Boolean properties (`hasIcon`) translate to presence/absence of the element in HTML, not a CSS modifier.
6. State properties map to either modifiers (`--disabled`) or pseudo-classes (`:hover`, `:focus`).

---

## Handoff Checklist

Before marking a design as "Ready for Development":

### Design Quality

- [ ] All components are instances from the shared library (no detached components)
- [ ] All colors reference Figma variables (no raw hex)
- [ ] All text uses shared text styles (no arbitrary font sizes)
- [ ] All spacing values are from the 8px scale
- [ ] All corners use radius tokens (no arbitrary values)
- [ ] Auto-layout is used everywhere possible
- [ ] Every layer is named descriptively (no default names)

### Responsive

- [ ] Designs provided for all four breakpoints (375, 768, 1024, 1440)
- [ ] Responsive behavior annotated for layout changes
- [ ] Breakpoint-specific content shown (collapsed nav, stacked columns, etc.)

### States and Interactions

- [ ] All interactive states shown (default, hover, focus, active, disabled)
- [ ] Error states demonstrated for form elements
- [ ] Loading and empty states provided
- [ ] Interaction annotations present (trigger, animation, duration)

### Accessibility

- [ ] Focus order annotated
- [ ] Color contrast verified (4.5:1 for normal text, 3:1 for large text)
- [ ] Touch target sizes are at least 44x44px on mobile
- [ ] ARIA roles and labels annotated where non-obvious
- [ ] Alternative text noted for images

### Assets

- [ ] Icons exported as SVG with correct naming
- [ ] Images exported at @1x, @2x, @3x with correct naming
- [ ] Logo assets provided in required formats
- [ ] Favicon set exported at all required sizes

### Documentation

- [ ] Component usage notes included
- [ ] Spacing annotations present for non-obvious values
- [ ] Token references documented in component description
- [ ] Link to component documentation in design system docs
