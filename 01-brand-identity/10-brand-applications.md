# Brand Applications

## 1. Overview

This document specifies how the Flavio Fusuma brand identity is applied to key physical and digital touchpoints. Each application includes exact dimensions, layout rules, color specifications, and typography settings to ensure consistent reproduction across all media.

All applications reference the design tokens documented in `03-design-tokens/` and the SCSS implementation in `04-styles/`.

---

## 2. Business Card

### Specifications

| Property | Value |
|----------|-------|
| **Size** | 3.5" x 2" (89mm x 51mm) — US standard |
| **Bleed** | 0.125" (3.175mm) on all sides |
| **Safe zone** | 0.125" inset from trim edge |
| **Stock** | 16pt uncoated matte or 14pt soft-touch laminate |
| **Print method** | Offset lithography or digital press |
| **Color mode** | CMYK + Pantone 289 C (brand blue) + Pantone 137 C (amber accent) |

### Front Layout

```
┌──────────────────────────────────┐
│                                  │
│  [FF Monogram]                   │
│  24 x 24 pt, Fusuma Blue         │
│  Positioned: 0.25" from left,    │
│              0.3" from top        │
│                                  │
│                                  │
│                                  │
│  flavio fusuma                   │
│  Inter SemiBold, 10pt, Blue-800  │
│  0.25" from left, 1.3" from top  │
│                                  │
│  Software Engineer               │
│  Inter Regular, 7.5pt, Neutral-500│
│  2pt below name                  │
│                                  │
│  ─────                           │
│  Amber accent line, 24pt wide,   │
│  2pt stroke, 8pt below title     │
│                                  │
└──────────────────────────────────┘
```

### Back Layout

```
┌──────────────────────────────────┐
│                                  │
│                        Right-aligned block │
│                        0.25" from right,   │
│                        0.3" from top        │
│                                  │
│  hello@flaviofusuma.com          │
│  Inter Regular, 7pt, Neutral-700 │
│                                  │
│  flaviofusuma.com                │
│  Inter Medium, 7pt, Blue-600     │
│                                  │
│  github.com/flaviofusuma         │
│  JetBrains Mono, 6.5pt, Neutral-500│
│                                  │
│                                  │
│                                  │
│                  Full-width amber │
│                  stripe, 2pt,     │
│                  bottom edge      │
└──────────────────────────────────┘
```

### Color Specifications (Print)

| Element | Color | CMYK | Pantone |
|---------|-------|------|---------|
| Monogram | Fusuma Blue | 68, 39, 0, 63 | 289 C |
| Name | Fusuma Blue | 68, 39, 0, 63 | 289 C |
| Title | Neutral-500 | 28, 20, 14, 44 | Cool Gray 9 C |
| Contact info | Neutral-700 | 40, 30, 22, 67 | Cool Gray 11 C |
| URL | Blue-600 | 84, 58, 0, 8 | 2728 C |
| Accent line | Fusuma Amber | 0, 36, 96, 4 | 137 C |
| Card stock | White | 0, 0, 0, 0 | — |

---

## 3. Letterhead

### Specifications

| Property | Value |
|----------|-------|
| **Size** | A4 (210mm x 297mm) |
| **Margins** | Top: 30mm, Bottom: 25mm, Left: 25mm, Right: 25mm |
| **Stock** | 100gsm uncoated white |
| **Print method** | Digital or offset |

### Header Layout

```
┌─────────────────────────────────────┐
│  30mm top margin                     │
│                                     │
│  [FF Monogram]    flavio fusuma     │
│  16 x 16mm        Inter SemiBold   │
│  Left: 25mm       9pt, Blue-800    │
│  Top: 30mm        Aligned to mono  │
│                   baseline          │
│                                     │
│  ───────────────────────────────── │
│  0.5pt rule, Neutral-200, full     │
│  text width, 6mm below monogram    │
│                                     │
│                                     │
│  [Body text area]                   │
│  Inter Regular, 10.5pt             │
│  Line-height: 15pt (1.43)          │
│  Color: Neutral-800                │
│  First line: 12mm below rule       │
│                                     │
│                                     │
│                                     │
│                                     │
│                                     │
│                                     │
│  ───────────────────────────────── │
│  0.5pt rule, Neutral-200           │
│  20mm from bottom                  │
│                                     │
│  hello@flaviofusuma.com  ·  flaviofusuma.com  ·  github.com/flaviofusuma │
│  Inter Regular, 7.5pt, Neutral-500 │
│  Center-aligned, 14mm from bottom   │
│                                     │
│  25mm bottom margin                 │
└─────────────────────────────────────┘
```

### Continuation Page

Subsequent pages omit the header monogram and name. They retain:
- The top horizontal rule at 20mm from the top edge
- The footer rule and contact information
- Page numbers: Inter Regular, 7.5pt, Neutral-400, right-aligned above footer rule

---

## 4. Email Signature

### Specifications

| Property | Value |
|----------|-------|
| **Max width** | 500px |
| **Max height** | 150px (visible area) |
| **Format** | Inline HTML (no external stylesheets) |
| **Image** | Monogram as embedded PNG or Base64 (32x32px @2x = 64x64px source) |
| **Fonts** | System font stack (email clients do not support custom fonts) |

### HTML Structure

```html
<table cellpadding="0" cellspacing="0" border="0" style="
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.5;
  color: #334155;
">
  <tr>
    <td style="padding-right: 16px; vertical-align: top;">
      <img src="[monogram-url]" alt="FF" width="40" height="40"
        style="display: block; border: 0;" />
    </td>
    <td style="vertical-align: top;">
      <div style="font-weight: 600; font-size: 14px; color: #1E3A5F;">
        Flavio Fusuma
      </div>
      <div style="font-size: 12px; color: #64748B; margin-top: 2px;">
        Software Engineer
      </div>
      <div style="
        width: 24px;
        height: 2px;
        background-color: #F59E0B;
        margin: 8px 0;
      "></div>
      <div style="font-size: 12px; color: #475569;">
        <a href="mailto:hello@flaviofusuma.com"
           style="color: #475569; text-decoration: none;">
          hello@flaviofusuma.com
        </a>
      </div>
      <div style="font-size: 12px; margin-top: 2px;">
        <a href="https://flaviofusuma.com"
           style="color: #2563EB; text-decoration: none;">
          flaviofusuma.com
        </a>
        <span style="color: #CBD5E1; margin: 0 6px;">|</span>
        <a href="https://github.com/flaviofusuma"
           style="color: #64748B; text-decoration: none;">
          GitHub
        </a>
      </div>
    </td>
  </tr>
</table>
```

### Email Signature Guidelines

- Do not add images, banners, or promotional content below the signature
- Do not add quotes, disclaimers, or legal text (unless legally required by the recipient's jurisdiction)
- The amber accent line is the only decorative element permitted
- Test in Gmail, Outlook (desktop and web), Apple Mail, and Thunderbird before deployment

---

## 5. Social Media Profiles

### LinkedIn

| Asset | Dimensions | Layout |
|-------|-----------|--------|
| **Profile photo** | 400 x 400 px (displays as circle) | FF Monogram centered on white background, or professional headshot |
| **Banner image** | 1584 x 396 px | Gradient from blue-800 to blue-950 left-to-right. FF Monogram at 64px, left-aligned at 80px from left edge, vertically centered. Optional tagline "Craft at the intersection of code and design" in Inter Regular, 18px, white, right-aligned. |
| **Post images** | 1200 x 627 px | Content area with 80px padding. Blue-800 or white background. |

### Twitter / X

| Asset | Dimensions | Layout |
|-------|-----------|--------|
| **Profile photo** | 400 x 400 px | Same as LinkedIn profile photo |
| **Header image** | 1500 x 500 px | Similar to LinkedIn banner. Gradient from blue-800 to blue-900. Monogram left, tagline right. Keep key elements in the center 60% (edges are cropped on mobile). |

### GitHub

| Asset | Dimensions | Layout |
|-------|-----------|--------|
| **Avatar** | 500 x 500 px | FF Monogram (Concept A, filled) centered on white background. Monogram in Fusuma Blue at 60% of frame width. |
| **Social preview** | 1280 x 640 px | For repository social cards. Blue-800 background. Project name in Inter Bold, 48px, white. Brief description in Inter Regular, 20px, neutral-300. FF Monogram watermark at 10% opacity in bottom-right corner. |

### Profile Bio Copy

- **LinkedIn**: "Software engineer crafting production-grade solutions at the intersection of code and design. Clean architecture, accessible interfaces, thoughtful engineering."
- **Twitter/X**: "Software engineer. Building at the intersection of code and design. Open source contributor."
- **GitHub**: "Software engineer focused on craft, clarity, and user-centered code."

---

## 6. Presentation Template

### Specifications

| Property | Value |
|----------|-------|
| **Aspect ratio** | 16:9 |
| **Dimensions** | 1920 x 1080 px (HD) |
| **Grid** | 12-column, 60px margins, 24px gutters |
| **Fonts** | Inter (all weights), JetBrains Mono (code slides) |

### Slide Layouts

#### Title Slide

```
┌──────────────────────────────────────────┐
│                                          │
│  Background: Blue-800 (solid)            │
│                                          │
│     [FF Monogram, white, 64px]           │
│     Center-aligned, 25% from top         │
│                                          │
│     Presentation Title                   │
│     Inter Bold, 48px, White              │
│     Center-aligned                       │
│                                          │
│     Subtitle or date                     │
│     Inter Regular, 24px, Blue-200        │
│     Center-aligned, 16px below title     │
│                                          │
│                                          │
│     ─────                                │
│     Amber accent, 48px wide, centered    │
│                                          │
│     Flavio Fusuma                        │
│     Inter Medium, 18px, Blue-300         │
│                                          │
└──────────────────────────────────────────┘
```

#### Content Slide

```
┌──────────────────────────────────────────┐
│  Background: White                       │
│  60px margins on all sides               │
│                                          │
│  Section Title                           │
│  Inter Bold, 36px, Blue-800             │
│  Top-left, 60px from top                 │
│                                          │
│  ─────                                   │
│  Amber accent, 32px wide, 8px below     │
│                                          │
│  [Content area]                          │
│  Inter Regular, 20px, Neutral-700       │
│  Line-height: 1.6                        │
│  Max width: 65% of slide width           │
│                                          │
│                                          │
│                                          │
│                          [FF Monogram]   │
│                          12px, Neutral-200│
│                          Bottom-right     │
│  ─── Slide number: 01    ──────────────  │
│  Inter Mono, 14px, Neutral-400, bottom-left│
└──────────────────────────────────────────┘
```

#### Code Slide

```
┌──────────────────────────────────────────┐
│  Background: Neutral-900 (dark)          │
│                                          │
│  Code Example Title                      │
│  Inter SemiBold, 28px, Neutral-100      │
│                                          │
│  ┌────────────────────────────────────┐  │
│  │  Code block                        │  │
│  │  JetBrains Mono, 16px, Neutral-200│  │
│  │  Background: Neutral-950          │  │
│  │  Padding: 24px                     │  │
│  │  Border-radius: 8px               │  │
│  │  Syntax highlighting:             │  │
│  │    Keywords: Blue-400             │  │
│  │    Strings: Amber-400             │  │
│  │    Comments: Neutral-500          │  │
│  │    Functions: Teal-400            │  │
│  └────────────────────────────────────┘  │
│                                          │
└──────────────────────────────────────────┘
```

#### Section Divider Slide

```
┌──────────────────────────────────────────┐
│  Background: Blue-50                     │
│                                          │
│                                          │
│     Section Number                       │
│     Inter Bold, 96px, Blue-200          │
│     Center-aligned                       │
│                                          │
│     Section Title                        │
│     Inter Bold, 48px, Blue-800          │
│     Center-aligned                       │
│                                          │
│                                          │
└──────────────────────────────────────────┘
```

---

## 7. Favicon and App Icons

### Size Requirements

| Size | Format | Usage |
|------|--------|-------|
| **16 x 16 px** | ICO, PNG | Browser tab favicon (standard) |
| **32 x 32 px** | ICO, PNG | Browser tab favicon (retina), Windows taskbar |
| **180 x 180 px** | PNG | Apple Touch Icon (iOS home screen) |
| **192 x 192 px** | PNG | Android Chrome, PWA manifest |
| **512 x 512 px** | PNG | PWA splash screen, Google Play Store |

### Design Specifications

All icons use the **FF Monogram (Concept A)** in its filled variant for maximum legibility at small sizes.

| Size | Mark | Background | Padding |
|------|------|-----------|---------|
| 16px | FF Monogram, simplified | Transparent | 1px |
| 32px | FF Monogram, full detail | Transparent | 2px |
| 180px | FF Monogram | White (#FFFFFF) | 20% of icon size (36px) |
| 192px | FF Monogram | White (#FFFFFF) | 20% of icon size (38px) |
| 512px | FF Monogram | White (#FFFFFF) | 20% of icon size (102px) |

### Color Variants

| Variant | Mark Color | Background | Usage |
|---------|-----------|-----------|-------|
| **Default** | Blue-800 (`#1E3A5F`) | White (#FFFFFF) | Standard favicon, Apple Touch |
| **Dark** | White (#FFFFFF) | Blue-800 (`#1E3A5F`) | PWA on dark devices, dark mode contexts |
| **Monochrome** | Black (#000000) | Transparent | Safari pinned tab (SVG mask) |

### HTML Implementation

```html
<!-- Standard favicon -->
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">

<!-- Apple Touch Icon -->
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">

<!-- PWA manifest -->
<link rel="manifest" href="/site.webmanifest">

<!-- Safari pinned tab -->
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#1E3A5F">

<!-- Windows tile -->
<meta name="msapplication-TileColor" content="#1E3A5F">
<meta name="theme-color" content="#1E3A5F">
```

### Web Manifest (`site.webmanifest`)

```json
{
  "name": "Flavio Fusuma",
  "short_name": "Fusuma",
  "icons": [
    {
      "src": "/android-chrome-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "/android-chrome-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "theme_color": "#1E3A5F",
  "background_color": "#FFFFFF",
  "display": "standalone"
}
```

---

## 8. File Naming Convention

All brand application assets follow this naming pattern:

```
ff-{application}-{variant}-{size}.{format}

Examples:
  ff-businesscard-front.pdf
  ff-businesscard-back.pdf
  ff-letterhead-page1.pdf
  ff-signature-html.html
  ff-favicon-16x16.png
  ff-favicon-32x32.png
  ff-apple-touch-icon-180x180.png
  ff-android-chrome-192x192.png
  ff-android-chrome-512x512.png
  ff-linkedin-banner-1584x396.png
  ff-twitter-header-1500x500.png
  ff-github-avatar-500x500.png
  ff-presentation-template.pptx
```
