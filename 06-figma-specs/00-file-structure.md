# Figma File Structure

This document defines the organizational structure, naming conventions, and page hierarchy for all Figma files in the Flavio Fusuma design system. Consistent file structure ensures that designers, engineers, and stakeholders can locate assets quickly and contribute without ambiguity.

---

## File Organization

The Flavio Fusuma design system spans multiple Figma files, each scoped to a specific concern. This separation keeps file size manageable and permissions granular.

| File | Purpose | Access |
|---|---|---|
| **FF - Foundations** | Color, typography, spacing, grid, iconography, elevation | View: all / Edit: design leads |
| **FF - Components** | All production components with variants | View: all / Edit: design system team |
| **FF - Patterns** | Composed patterns (forms, navigation, data display) | View: all / Edit: design system team |
| **FF - Templates** | Page-level templates for common layouts | View: all / Edit: product designers |
| **FF - Prototypes** | Interactive prototypes for user testing and stakeholder review | View: all / Edit: product designers |
| **FF - Playground** | Experimentation and proposals (not production) | View: team / Edit: all designers |
| **FF - Brand & Marketing** | Marketing assets, social templates, presentation decks | View: all / Edit: marketing + design |

---

## Page Hierarchy

Every production Figma file follows the same page structure. Pages are numbered to enforce order in the sidebar.

### Standard Page Order

```
📄 Cover
📄 0 - Changelog
📄 1 - Foundations
📄 2 - Components
📄 3 - Patterns
📄 4 - Templates
📄 5 - Prototypes
📄 6 - Archive
```

### Page Descriptions

#### Cover

The first page in every file. Contains:

- File title (e.g., "Flavio Fusuma -- Components")
- File description (one sentence)
- Last updated date
- Status label (see Status Labels below)
- Table of contents linking to key sections
- Owner and contributors list

The cover frame uses a fixed size of 1600x900px with the brand primary (`#1E3A5F`) background and white text set in Inter.

#### 0 - Changelog

A running log of significant changes to the file. Each entry includes:

- Date (YYYY-MM-DD format)
- Author
- Summary of change
- Status label if applicable

Layout: vertical stack of changelog entries, newest at top. Each entry is a component instance of `_Utility / Changelog Entry`.

#### 1 - Foundations

Contains foundational elements that components are built from:

- **Color swatches**: All palette colors displayed with token names, hex values, and contrast ratios
- **Typography samples**: Every type scale level rendered with metadata (size, weight, line height, letter spacing)
- **Spacing scale**: Visual representation of the 8px spacing scale from `space-0.5` (4px) through `space-24` (192px)
- **Grid reference**: Visual grid overlays at each breakpoint
- **Elevation/shadow**: Each elevation level with token names and CSS values
- **Border radii**: Visual samples of each radius token
- **Iconography**: Icon grid, sizing rules, and stroke weight standards

#### 2 - Components

All production-ready components organized into sections (see Section Organization below). Each component section contains:

- Component description and usage notes
- All variants displayed in a matrix
- All states demonstrated
- All sizes shown
- Anatomy annotation frame
- Spacing and measurement annotation frame
- Accessibility notes frame

#### 3 - Patterns

Composed patterns built from multiple components:

- Form patterns (contact, signup, search, multi-step)
- Navigation patterns (top nav, sidebar, mobile, breadcrumbs)
- Data display patterns (tables, lists, cards grid)
- Feedback patterns (empty states, error pages, loading)
- Layout patterns (hero, content sections, sidebars)

#### 4 - Templates

Full-page compositions at each breakpoint:

- Homepage
- Portfolio listing
- Project detail
- About / biography
- Contact page
- Blog listing
- Blog post
- 404 error page

Each template is shown at all four breakpoints (375px, 768px, 1024px, 1440px).

#### 5 - Prototypes

Interactive prototype flows organized by user journey. Each flow has:

- Flow diagram showing screen connections
- Annotated interaction notes
- Device-specific frames (desktop, tablet, mobile)

#### 6 - Archive

Deprecated components, patterns, and templates. Items moved here retain their layer structure and naming but receive the `[DEPRECATED]` prefix. Nothing is deleted; it is archived for reference.

---

## Frame Naming Conventions

### Top-Level Section Frames

Top-level frames on a page represent sections. They use title case with a category prefix.

```
Section / [Category Name]
```

Examples:

```
Section / Buttons
Section / Form Inputs
Section / Typography Scale
Section / Color Palette - Primary
Section / Navigation Patterns
```

### Component Frames

Component frames follow the naming pattern:

```
[Category] / [Component] / [Variant]
```

Examples:

```
Button / Primary / Default
Button / Primary / Hover
Button / Secondary / Disabled
Input / Text / Default
Input / Text / Error
Card / Default / With Image
Card / Default / Text Only
```

### Breakpoint Frames

Frames sized to specific breakpoints include the breakpoint name:

```
[Template Name] / [Breakpoint]
```

Examples:

```
Homepage / Mobile (375)
Homepage / Tablet (768)
Homepage / Desktop (1024)
Homepage / Desktop Wide (1440)
```

### Annotation Frames

Frames that contain design annotations use the `_Annotation` prefix:

```
_Annotation / [Component] / [Type]
```

Examples:

```
_Annotation / Button / Anatomy
_Annotation / Button / Spacing
_Annotation / Card / Responsive Behavior
```

---

## Layer Naming Standards

Consistent layer naming enables accurate developer handoff and reduces confusion when inspecting components.

### General Rules

1. Use `kebab-case` for all layer names (e.g., `icon-leading`, `text-label`, `container-inner`).
2. Never leave default Figma names (e.g., "Frame 437", "Rectangle 12", "Group 3").
3. Name every layer, including decorative elements.
4. Group related layers and name the group descriptively.
5. Boolean layers (show/hide) use the format `has-[element]` (e.g., `has-icon`, `has-avatar`).

### Layer Name Patterns

| Layer Type | Pattern | Example |
|---|---|---|
| Container / wrapper | `container`, `wrapper`, `content` | `container`, `content-wrapper` |
| Text | `text-[role]` | `text-label`, `text-description`, `text-helper` |
| Icon | `icon-[position]` or `icon-[name]` | `icon-leading`, `icon-trailing`, `icon-chevron` |
| Image | `image-[role]` | `image-thumbnail`, `image-avatar`, `image-hero` |
| Background | `bg-[modifier]` | `bg-surface`, `bg-overlay` |
| Border / divider | `border-[position]` or `divider` | `border-bottom`, `divider-horizontal` |
| Badge / indicator | `badge`, `indicator`, `dot` | `badge-count`, `indicator-status` |
| Slot (instance swap) | `slot-[name]` | `slot-icon`, `slot-action`, `slot-media` |
| State overlay | `state-[name]` | `state-hover`, `state-focus-ring` |

### Figma-Specific Layer Types

| Type | Naming Rule | Example |
|---|---|---|
| Auto-layout frame | Name by content purpose, not by layout direction | `actions` (not `horizontal-frame`) |
| Component instance | Keep the default instance name from the source component | `Button / Primary / Default` |
| Boolean group | `has-[feature]` matching the component property name | `has-icon` |
| Variant property frame | Named automatically by Figma; do not rename | `Type=Primary, Size=md, State=Default` |

---

## Section Organization Within Pages

### Component Page Sections

Each component type gets its own section frame. Within each section, content is arranged vertically in this order:

```
Section / [Component Name]
├── _header                          Description, status label, owner
├── anatomy                          Labeled diagram of component parts
├── variant-matrix                   Grid showing all variant × size combinations
├── states                           All states for each variant
├── sizing                           Side-by-side size comparison
├── spacing                          Annotated spacing and padding
├── accessibility                    ARIA attributes, keyboard behavior, contrast notes
├── usage-guidelines                 Do/Don't examples
├── related-components               Links to related component sections
└── changelog                        Component-specific change history
```

### Section Header Frame

Every section starts with a header frame containing:

| Element | Spec |
|---|---|
| Component name | Inter SemiBold, 32px, `color-neutral-900` |
| Description | Inter Regular, 16px, `color-neutral-600`, max 80 characters |
| Status label | Component instance of `_Utility / Status Label` |
| Owner | Inter Regular, 14px, `color-neutral-500` |
| Last updated | Inter Regular, 14px, `color-neutral-500` |
| Divider | 1px `color-neutral-200`, full width, 24px below header content |

### Spacing Between Sections

- Between sections on the same page: 160px vertical gap
- Between sub-sections within a section: 80px vertical gap
- Between individual component demonstrations: 40px vertical gap
- Between label and content: 16px vertical gap

---

## Status Labels

Status labels communicate the maturity of a component, pattern, or template.

| Label | Color | Meaning |
|---|---|---|
| **Ready** | `color-success-default` (#10B981) bg, white text | Production-ready. Approved for use in all projects. |
| **In Progress** | `color-accent-500` (#F59E0B) bg, `neutral-900` text | Actively being designed or refined. Not yet approved for production. |
| **In Review** | `color-info-default` (#3B82F6) bg, white text | Design complete, awaiting review from design system team. |
| **Deprecated** | `color-error-default` (#EF4444) bg, white text | Scheduled for removal. Use the documented replacement instead. |
| **Experimental** | `color-neutral-500` (#6B7280) bg, white text | Exploratory work. May or may not progress to production. |

### Status Label Component

The status label is a utility component:

- **Name**: `_Utility / Status Label`
- **Size**: Auto-width, 24px height
- **Padding**: 4px vertical, 8px horizontal
- **Font**: Inter SemiBold, 11px, uppercase, 0.05em letter-spacing
- **Border radius**: 4px
- **Variant property**: `status` (Ready | In Progress | In Review | Deprecated | Experimental)

---

## Naming Prefixes

Special prefixes signal layer purpose:

| Prefix | Purpose | Example |
|---|---|---|
| `_` (underscore) | Internal/utility components not published to library | `_Utility / Status Label`, `_Annotation / Redline` |
| `.` (dot) | Hidden layers (Figma convention for toggling visibility) | `.bg-overlay` |
| `#` (hash) | Documentation-only frames (not part of the design) | `#notes`, `#reference-image` |

---

## Version Control

### Branch Strategy

The Figma file uses Figma's built-in branching:

| Branch Type | Naming | Purpose |
|---|---|---|
| Main | `main` (default) | Production-ready source of truth |
| Feature | `feature/[component-name]` | New component development |
| Update | `update/[component-name]` | Modifications to existing components |
| Fix | `fix/[issue-description]` | Bug fixes and corrections |

### Merge Checklist

Before merging a branch back to main:

- [ ] All layers follow naming conventions documented above
- [ ] Status label is set correctly (Ready, In Progress, etc.)
- [ ] Changelog entry added with date, author, and description
- [ ] Component properties and variants are complete
- [ ] Accessibility annotations are present
- [ ] Spacing and measurement annotations are present
- [ ] No default Figma names remain (Frame 1, Rectangle 2, etc.)
- [ ] All colors reference shared styles or variables (no raw hex values)
- [ ] All text uses type scale styles (no arbitrary font sizes)

---

## File Hygiene

### Regular Maintenance

- **Weekly**: Remove unused local styles, delete stray frames outside sections, verify status labels are current.
- **Monthly**: Archive deprecated components, update changelog, verify library publish status.
- **Quarterly**: Full audit of naming conventions, layer structure, and accessibility annotations.

### Performance Guidelines

- Keep individual pages under 200 top-level frames.
- Flatten complex decorative vectors to reduce node count.
- Use component instances rather than detached copies.
- Avoid deeply nested groups beyond 5 levels.
- Rasterize complex illustrations that do not need to be editable.
