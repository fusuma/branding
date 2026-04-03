# Visual Direction

## 1. Overview

The Flavio Fusuma visual direction translates the brand's core tension -- engineering precision and human-centered warmth -- into a cohesive visual language across photography, illustration, iconography, graphic elements, and motion. Every visual decision reinforces the brand personality: precise, approachable, confident, curious, and intentional.

---

## 2. Photography Style

### Mood

Photography for the Flavio Fusuma brand should feel **authentic, focused, and quietly confident**. Images should evoke the feeling of deep work, creative craft, and purposeful collaboration. The overall mood is calm and considered -- not sterile or corporate, but not chaotic or overly casual.

### Subjects

| Category | Subject Matter | Notes |
|----------|---------------|-------|
| **Workspaces** | Clean desks, monitors with code or design tools, organized setups | Show the craft environment, not the chaos |
| **Technology** | Close-ups of keyboards, screens, code editors, design software | Abstract enough to be timeless, specific enough to be authentic |
| **Architecture** | Modern structures, geometric patterns, bridges, clean lines | Metaphors for engineering and structure |
| **Nature + texture** | Wood grain, water surfaces, geometric formations in nature | Warmth and organic contrast to technology |
| **People** | Focused individuals, small collaborative groups, candid moments | Real and diverse; never staged stock photography |
| **Abstract** | Light and shadow, reflections, motion blur on geometric forms | For hero backgrounds, section dividers, atmospheric use |

### Treatment

| Parameter | Specification |
|-----------|---------------|
| **Color grading** | Cool shadows, warm highlights. Slight desaturation overall. Blue undertone in shadows harmonizing with brand blue. |
| **Contrast** | Medium-high. Clear separation between subject and background. |
| **Exposure** | Slightly bright. Generous with light. Never underexposed or moody. |
| **Depth of field** | Shallow-to-medium. Use selective focus to guide the eye to the subject. |
| **Aspect ratios** | 16:9 (hero), 3:2 (editorial), 1:1 (social, avatar), 4:5 (portrait) |
| **Resolution** | Minimum 2x for retina: 2880px wide for hero images, 1600px for editorial |
| **File format** | WebP with JPEG fallback. PNG for images requiring transparency. |

### Photography Do's and Don'ts

**Do:**
- Show real work environments and authentic moments
- Use natural light or soft, directional artificial light
- Include details that reward close inspection (a well-organized bookshelf, a handwritten note, an elegant code snippet on screen)
- Apply the brand color grading consistently across all photography
- Crop with intention -- lead the eye to the meaningful element

**Don't:**
- Use generic stock photography with forced smiles or handshakes
- Use heavy filters, Instagram-style presets, or lens flares
- Photograph messy or cluttered environments (unless intentionally curated)
- Over-saturate colors or add artificial warmth that conflicts with the brand blue
- Use photography where the subject is ambiguous or the composition lacks a focal point

---

## 3. Illustration Style

### Approach: Geometric + Structural

Illustrations in the Flavio Fusuma system are geometric, line-based, and structural. They echo the precision of engineering while maintaining approachability through color and gentle asymmetry.

### Visual Characteristics

| Characteristic | Specification |
|----------------|---------------|
| **Line style** | Uniform stroke weight (2px at 1x, 4px at 2x). No tapering or calligraphic variation. |
| **Geometry** | Grid-aligned. Angles at 0°, 45°, 90°. Curves are circular arcs from grid-snapped centers. |
| **Color palette** | Brand blue (`#1E3A5F`) as primary stroke. Amber (`#F59E0B`) as selective accent fill. Neutral-200 (`#E2E8F0`) for subtle structure. |
| **Fill style** | Minimal. Use flat color only for emphasis. Most illustration is line-based. |
| **Perspective** | Flat / isometric. No realistic 3D rendering or complex perspective. |
| **Detail level** | Medium. Enough to communicate clearly, not so much that it becomes decorative noise. |
| **Scale** | Illustrations should work from 120px wide (inline) to full-bleed hero (1440px+). |

### Illustration Categories

| Category | Description | Usage |
|----------|-------------|-------|
| **Spot illustrations** | Small, focused icons (64-120px). Single concept per illustration. | Inline with text, feature lists, empty states |
| **Scene illustrations** | Larger compositions (400-800px). Multiple elements in a structured scene. | Landing pages, about sections, blog headers |
| **Diagrams** | Technical diagrams, architecture charts, flow diagrams. | Technical content, documentation, case studies |
| **Decorative elements** | Abstract geometric patterns, connector lines, grid overlays. | Backgrounds, section dividers, subtle texture |

### Illustration Do's and Don'ts

**Do:**
- Align all elements to the 8px grid
- Use brand blue as the primary color; amber only for the single most important element
- Keep compositions balanced with generous whitespace
- Test illustrations at minimum display size before finalizing

**Don't:**
- Use gradients, shadows, or dimensionality effects in illustrations
- Mix illustration styles (e.g., geometric with hand-drawn)
- Use more than 3 colors from the palette in a single illustration
- Create illustrations that require explanation to understand

---

## 4. Iconography

### Icon System

The Flavio Fusuma icon system is stroke-based, geometrically constructed, and designed for clarity at small sizes. Icons function as visual shorthand -- they should communicate instantly and never require a label to be understood in context.

### Construction Specifications

| Parameter | Value |
|-----------|-------|
| **Grid** | 24 x 24 unit grid with 2-unit padding (20 x 20 live area) |
| **Stroke weight** | 1.5px at 24px size (scales proportionally) |
| **Stroke cap** | Round |
| **Stroke join** | Round |
| **Corner radius** | 2px for internal corners |
| **Minimum gap** | 2px between parallel strokes |
| **Optical alignment** | Circular and triangular icons are optically scaled to match the visual weight of square icons |

### Available Sizes

| Size | Use Case | Stroke Weight |
|------|----------|---------------|
| **16px** | Inline text, compact UI, metadata | 1px |
| **20px** | Form inputs, buttons, navigation items | 1.5px |
| **24px** | Default size. Section headers, standalone icons | 1.5px |
| **32px** | Feature callouts, marketing emphasis | 2px |
| **48px** | Hero features, large empty states | 2px |

### Icon Colors

Icons inherit their color from the parent text color by default (`currentColor`). Override with the semantic icon color classes:

| Class | Token | Usage |
|-------|-------|-------|
| Default | `currentColor` | Inherits from parent text |
| `.icon-primary` | `--color-icon-primary` | Primary icon color (neutral-700) |
| `.icon-secondary` | `--color-icon-secondary` | Secondary / muted (neutral-400) |
| `.icon-brand` | `--color-icon-brand` | Brand blue (blue-800) |
| `.icon-accent` | `--color-icon-accent` | Accent amber (amber-500) |

### Iconography Do's and Don'ts

**Do:**
- Use the 24x24 grid for all icon construction
- Maintain consistent stroke weight across all icons in a set
- Use `currentColor` to allow icons to inherit text color
- Test every icon at 16px to verify legibility
- Keep icons simple -- one concept per icon

**Don't:**
- Mix filled and stroked icons in the same context
- Use icons smaller than 16px
- Add decorative detail that does not aid recognition
- Use brand-specific colors on icons that should be neutral
- Create icons with more than 3 distinct shapes or 2 levels of nesting

---

## 5. Graphic Elements

### Patterns

Geometric patterns reinforce the brand's engineering precision and can be used as subtle background textures or decorative accents.

| Pattern | Description | Usage |
|---------|-------------|-------|
| **Dot grid** | Evenly spaced dots on 8px intervals. Blue-200 on white, or blue-900 on dark backgrounds. | Page backgrounds, section fills, subtle texture |
| **Line grid** | Horizontal and vertical lines at 8px intervals. 1px stroke, neutral-200 / neutral-700 in dark mode. | Technical documentation, developer-facing contexts |
| **Diagonal hatch** | 45° lines at 16px intervals. 1px stroke, neutral-200. | Disabled states, placeholder areas, background texture |
| **Chevron repeat** | Repeating chevron / angle-bracket motif at 32px intervals. Blue-100 on white. | Hero backgrounds, branded sections, marketing materials |

### Pattern Guidelines

- Patterns are always **background elements** -- never the focal point
- Opacity should be reduced (10-20%) so patterns do not compete with content
- In dark mode, pattern colors invert (use the dark neutral equivalent)
- Patterns should tile seamlessly

### Decorative Elements

| Element | Description | Usage |
|---------|-------------|-------|
| **Accent line** | 4px-wide amber (`#F59E0B`) horizontal rule | Section emphasis, pull-quote accent, heading underline |
| **Corner bracket** | Right-angle bracket in brand blue, positioned at card or section corners | Card accents, featured content, pull-quotes |
| **Code cursor** | Blinking cursor animation in brand blue | Loading states, "typing" animations, developer-audience content |
| **Gradient overlay** | Linear gradient from blue-800 at 90% opacity to transparent | Hero image overlays, banner backgrounds |

### Texture

- Textures are limited to **noise grain** and **subtle paper** -- nothing heavy or skeuomorphic
- Noise grain: 2% opacity, monochromatic, applied as an SVG filter or CSS background
- Paper texture: Reserved for print materials and PDF exports only

---

## 6. Motion and Animation Direction

### Motion Philosophy

Motion in the Flavio Fusuma system is **purposeful, subtle, and communicative**. Every animation must serve one of three functions: provide feedback, maintain spatial orientation, or guide attention. Motion that is purely decorative is removed.

### Motion Principles

| Principle | Description |
|-----------|-------------|
| **Functional first** | Animation communicates state changes, transitions, or feedback. If it does not serve a function, it does not exist. |
| **Quick and confident** | Default duration is 200ms (`--duration-normal`). Most interactions resolve in 150-300ms. Nothing lingers. |
| **Natural easing** | Use `--ease-out` for entrances, `--ease-in` for exits, `--ease-in-out` for state changes. Linear only for progress indicators. |
| **Respect preferences** | All motion is disabled when `prefers-reduced-motion: reduce` is active. |

### Animation Tokens

These map directly to the motion tokens in `03-design-tokens/global/motion.tokens.json`:

| Token | Duration | Easing | Usage |
|-------|----------|--------|-------|
| Micro-interaction | `--duration-fast` (150ms) | `--ease-out` | Button press, checkbox toggle, icon state |
| Transition | `--duration-normal` (200ms) | `--ease-in-out` | Tab switch, accordion expand, tooltip show |
| Entrance | `--duration-slow` (300ms) | `--ease-out` | Modal open, dropdown appear, page element enter |
| Exit | `--duration-fast` (150ms) | `--ease-in` | Modal close, dropdown dismiss, toast exit |
| Complex | `--duration-slower` (400ms) | `--ease-spring` | Page transition, staggered list animation |
| Emphasis | `--duration-deliberate` (700ms) | `--ease-bounce` | Celebration, success state, attention draw |

### Common Animation Patterns

| Pattern | Properties Animated | Duration | Easing |
|---------|-------------------|----------|--------|
| **Fade in** | `opacity: 0 -> 1` | 200ms | ease-out |
| **Fade out** | `opacity: 1 -> 0` | 150ms | ease-in |
| **Slide up** | `transform: translateY(8px) -> 0`, `opacity: 0 -> 1` | 300ms | ease-out |
| **Scale in** | `transform: scale(0.95) -> 1`, `opacity: 0 -> 1` | 200ms | ease-out |
| **Collapse** | `height: auto -> 0`, `opacity: 1 -> 0` | 200ms | ease-in-out |
| **Skeleton pulse** | `opacity: 0.5 -> 1 -> 0.5` (loop) | 1500ms | ease-in-out |

### Logo Animation

The FF Monogram mark (Concept A) supports a simple entrance animation:

1. **Entry** (300ms, ease-out): The center vertical stem scales in from `scaleY(0)` to `scaleY(1)`. The two outer stems follow 50ms later (staggered). Horizontal bars fade in simultaneously.
2. **Idle**: No animation. The mark is static when at rest.
3. **Exit** (150ms, ease-in): The mark fades out uniformly with `opacity: 1 -> 0`.

### Motion Do's and Don'ts

**Do:**
- Use motion to communicate state changes (hover, active, focus, disabled)
- Stagger animations for grouped elements (50ms delay between items)
- Test all animations at 2x speed and 0.5x speed to ensure they feel natural at both extremes
- Always provide `prefers-reduced-motion` fallbacks

**Don't:**
- Animate layout properties (`width`, `height`, `top`, `left`) -- use `transform` and `opacity` instead
- Create animations longer than 700ms for standard UI interactions
- Use spring or bounce easing for functional transitions (reserve for emphasis moments)
- Animate on page load unless the element is above the fold and the animation is under 300ms
- Chain more than 3 sequential animations -- users lose patience after ~1 second of waiting
