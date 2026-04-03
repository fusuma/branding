# Brand Governance

## 1. Purpose

This document establishes the rules, processes, and responsibilities for maintaining the integrity of the Flavio Fusuma brand. Consistent governance ensures that every expression of the brand -- whether created internally, by collaborators, or by third parties -- meets the quality and consistency standards established in this brand identity system.

---

## 2. Approval Process for Brand Usage

### Internal Usage

| Action | Approval Required | Approver |
|--------|-------------------|----------|
| Using existing brand assets as documented | None | Self-service from brand repository |
| Creating new content using brand templates | None | Follow templates and guidelines |
| Modifying existing brand assets (color, layout, typography) | Yes | Brand owner (Flavio Fusuma) |
| Creating new brand assets not covered by existing templates | Yes | Brand owner |
| Using the brand in a new channel or medium | Yes | Brand owner |

### Third-Party Usage

| Action | Approval Required | Process |
|--------|-------------------|---------|
| Conference or event organizers using the logo | Required | Submit request via email with context, dimensions, placement, and deadline |
| Publication or media featuring the brand | Required | Provide brand press kit; review final placement before publication |
| Partners co-branding with Flavio Fusuma | Required | Review co-branding agreement; approve final artwork |
| Open-source project attribution | Not required | Use the provided attribution badge (see section 6) |
| Social media mentions or shares | Not required | No approval needed for organic social mentions |

### Approval Workflow

1. **Request**: Describe the intended usage, including context, medium, dimensions, audience, and timeline.
2. **Review**: Brand owner reviews the request against brand guidelines within 3 business days.
3. **Feedback**: If modifications are needed, specific feedback is provided with reference to the relevant guideline section.
4. **Approval**: Written approval is given via email. Approval is specific to the described usage and does not extend to future or modified uses.
5. **Archive**: Approved usage is logged in the brand usage register for reference.

---

## 3. Version Control and Updates

### Versioning Strategy

The brand identity system follows semantic versioning:

| Change Type | Version Bump | Examples |
|-------------|-------------|----------|
| **Major** (x.0.0) | Breaking changes | Logo redesign, primary color change, typography overhaul, structural reorganization |
| **Minor** (1.x.0) | Additive changes | New brand application, new color added to extended palette, new component, new guideline section |
| **Patch** (1.0.x) | Corrections | Typo fixes, token value corrections, accessibility improvements, clarification of existing guidelines |

### Current Version

| Property | Value |
|----------|-------|
| **Version** | 1.0.0 |
| **Release date** | April 2026 |
| **Status** | Active |

### Update Process

1. **Identify**: Document the change needed, the rationale, and the scope of impact.
2. **Draft**: Create the proposed change in a branch of the brand repository.
3. **Review**: Assess impact across all brand touchpoints (do existing materials need updating?).
4. **Approve**: Brand owner approves the change.
5. **Implement**: Merge the change and update the version number.
6. **Communicate**: Notify all stakeholders of the change, including what was changed, why, and what (if anything) they need to update.
7. **Deprecate**: If the change replaces an existing asset or guideline, mark the old version as deprecated with a migration path.

### File Versioning

Brand assets in the repository are version-controlled via Git. The repository structure serves as the canonical source:

```
Repository: branding
Branch: main (production-ready, current version)
Branch: develop (work-in-progress changes)
Tags: v1.0.0, v1.1.0, etc.
```

---

## 4. Brand Audit Checklist

Conduct a brand audit quarterly (or before any major campaign or launch) to ensure consistency. Review each item and mark as compliant, non-compliant, or not applicable.

### Visual Identity

- [ ] Logo is used in an approved variation (full color, monochrome, reversed)
- [ ] Logo meets minimum size requirements (24px digital, 8mm print for monogram)
- [ ] Logo clear space is maintained (minimum 1F on all sides)
- [ ] No unauthorized modifications to the logo (stretching, recoloring, adding effects)
- [ ] Primary brand blue (`#1E3A5F`) is used correctly for headers and brand moments
- [ ] Accent amber (`#F59E0B`) is used sparingly (under 15% of layout)
- [ ] Color combinations meet WCAG AA contrast requirements
- [ ] Inter is the primary typeface for all UI and marketing text
- [ ] JetBrains Mono is used exclusively for code and technical content
- [ ] Font weights follow the documented hierarchy (Regular for body, SemiBold for subheads, Bold for headings)

### Digital Presence

- [ ] Website uses the correct favicon at all required sizes (16, 32, 180, 192, 512)
- [ ] Social media profiles use current avatar and banner images
- [ ] Social media bios match the approved copy
- [ ] Email signature follows the documented HTML structure
- [ ] Dark mode implementation correctly remaps all semantic tokens
- [ ] All interactive elements use blue-600 (`#2563EB`) as the interactive color
- [ ] Focus states are visible and use the documented focus ring (blue-500, 2px)

### Print Materials

- [ ] Business cards use the correct stock, dimensions, and layout
- [ ] Letterhead follows the documented margins, header, and footer structure
- [ ] CMYK values match the documented specifications (not converted from RGB)
- [ ] Pantone spot colors are specified where available

### Content and Voice

- [ ] Written content follows the tone of voice guidelines (clear, confident, warm, intentional)
- [ ] Technical content uses the appropriate vocabulary and complexity level
- [ ] No unapproved taglines, slogans, or brand claims are in use
- [ ] Photography and imagery follow the visual direction guidelines

### Accessibility

- [ ] All text meets WCAG 2.1 AA contrast ratios (4.5:1 for body text, 3:1 for large text)
- [ ] All images have descriptive alt text
- [ ] All interactive elements are keyboard-accessible
- [ ] Motion respects `prefers-reduced-motion` user preference
- [ ] Focus indicators are visible on all interactive elements

---

## 5. Third-Party Usage Guidelines

### Brand Press Kit

A downloadable press kit is available for journalists, event organizers, and partners. The kit contains:

| Asset | Formats | Included Variations |
|-------|---------|---------------------|
| FF Monogram | SVG, PNG (1x, 2x, 4x), EPS | Full color, monochrome, reversed, white |
| Wordmark | SVG, PNG (1x, 2x, 4x), EPS | Full color, monochrome |
| Lockups | SVG, PNG (1x, 2x, 4x) | Horizontal, stacked |
| Brand colors | ASE (Adobe Swatch), JSON | Full palette |
| Brand guidelines summary | PDF | 2-page quick reference |

### Usage Rules for Third Parties

**Permitted:**
- Display the logo to identify Flavio Fusuma in editorial content, conference materials, or partner listings
- Use the logo in its provided form without modification
- Scale the logo proportionally (no stretching or distortion)
- Place the logo on backgrounds that meet the documented contrast requirements

**Not Permitted:**
- Modify the logo in any way (color, proportion, orientation, adding elements)
- Use the logo to imply endorsement of products or services not associated with Flavio Fusuma
- Place the logo on busy, patterned, or photographic backgrounds where contrast is insufficient
- Incorporate the logo into another logo or trademark
- Use the brand colors, typography, or visual style to create materials that could be confused with official Flavio Fusuma content
- Use the logo at sizes below the documented minimum

### Attribution for Open-Source Projects

For projects where Flavio Fusuma is a contributor or maintainer, the following attribution formats are approved:

**README badge** (Markdown):
```markdown
[![Built by Flavio Fusuma](https://img.shields.io/badge/built%20by-Flavio%20Fusuma-1E3A5F)](https://flaviofusuma.com)
```

**Footer attribution** (HTML):
```html
<p>Built by <a href="https://flaviofusuma.com">Flavio Fusuma</a></p>
```

---

## 6. Brand Asset Distribution

### Access Levels

| Level | Who | Access |
|-------|-----|--------|
| **Full access** | Brand owner | All source files, editable formats (Figma, AI, SVG), design tokens, repository write access |
| **Collaborator access** | Trusted partners, agencies | Brand press kit, style guide PDF, design tokens (read-only), repository read access |
| **Public access** | Anyone | Press kit (logo files, color reference, 2-page guide) via website download |

### Distribution Channels

| Channel | Content | Update Frequency |
|---------|---------|------------------|
| **Git repository** (this repo) | Complete brand system, design tokens, SCSS, documentation | On every version change |
| **Website** (`/press` page) | Press kit download (ZIP) | On major/minor version changes |
| **Figma** | Design file with components, tokens, and examples | Synced with repository changes |
| **npm** (future) | Design tokens as an installable package | On token changes |

### Deprecation Policy

When brand assets are updated:

1. The previous version remains available for 90 days after the new version is published.
2. During the 90-day transition period, both versions are considered acceptable.
3. After 90 days, the previous version is archived and should no longer be used in new materials.
4. Existing printed materials using the deprecated version may continue to circulate until their natural end of life (e.g., existing business card stock may be used until depleted).

---

## 7. Contact

For brand usage questions, approval requests, or to report brand misuse:

- **Email**: hello@flaviofusuma.com
- **Subject line**: "Brand Usage Request" or "Brand Issue Report"
- **Response time**: Within 3 business days
