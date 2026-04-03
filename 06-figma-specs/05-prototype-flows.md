# Prototype Flows

> Interactive prototype specifications for the Flavio Fusuma Design System. Defines user flows, interaction triggers, animation settings, overlay behavior, and scroll specifications.

---

## User Flow Overview

The primary prototype covers the portfolio website experience. Each flow is built as a separate prototype connection set in Figma.

### Flow Map

```
                      ┌─────────────┐
                      │  Homepage   │
                      └──────┬──────┘
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ┌───────────┐ ┌──────────┐  ┌──────────┐
        │ Portfolio  │ │  About   │  │  Contact  │
        │  Listing   │ │          │  │           │
        └─────┬─────┘ └──────────┘  └──────────┘
              ▼
     ┌────────────────┐
     │ Project Detail  │
     └────────┬───────┘
              ▼
     ┌────────────────┐
     │ Contact (from   │
     │ project CTA)    │
     └────────────────┘
```

### Complete Flow Inventory

| Flow ID | Flow Name | Entry Point | Screens | Purpose |
|---|---|---|---|---|
| F-01 | Main navigation | Homepage | Homepage → Portfolio → Project Detail → Contact | Primary browsing journey |
| F-02 | Direct contact | Homepage | Homepage → Contact → Success state | Quick contact path |
| F-03 | Portfolio browse | Portfolio Listing | Listing → Filter → Listing (filtered) → Project Detail | Project discovery |
| F-04 | Mobile navigation | Homepage (mobile) | Hamburger → Nav overlay → Any page | Mobile menu interaction |
| F-05 | Theme toggle | Any page | Light → Dark (or reverse) | Theme switching |
| F-06 | Search | Any page | Search trigger → Search overlay → Results → Project Detail | Content search |
| F-07 | Error recovery | 404 page | 404 → Homepage (via CTA) | Error handling |

---

## Flow F-01: Main Navigation (Homepage → Portfolio → Project Detail → Contact)

### Screen 1: Homepage

| Element | Trigger | Action | Destination | Animation |
|---|---|---|---|---|
| Nav link "Portfolio" | Click | Navigate | Portfolio Listing | Smart Animate |
| Nav link "About" | Click | Navigate | About page | Smart Animate |
| Nav link "Contact" | Click | Navigate | Contact page | Smart Animate |
| Hero CTA "View Work" | Click | Navigate | Portfolio Listing | Smart Animate |
| Featured project card | Click | Navigate | Project Detail (specific) | Smart Animate |
| Footer CTA "Get in Touch" | Click | Navigate | Contact page | Smart Animate |
| Theme toggle button | Click | Navigate | Homepage (dark variant) | Smart Animate |
| Nav links | Hover | State change | Same screen (hover state) | Smart Animate |
| Featured project cards | Hover | State change | Same screen (card hover) | Smart Animate |

### Screen 2: Portfolio Listing

| Element | Trigger | Action | Destination | Animation |
|---|---|---|---|---|
| Back / breadcrumb "Home" | Click | Navigate | Homepage | Smart Animate |
| Filter chip (e.g., "Web") | Click | State change | Listing (filtered) | Smart Animate |
| Filter chip "All" | Click | State change | Listing (unfiltered) | Smart Animate |
| Project card | Click | Navigate | Project Detail | Smart Animate |
| Project card | Hover | State change | Card hover state | Smart Animate |
| Load more button | Click | State change | Extended listing | Dissolve |

### Screen 3: Project Detail

| Element | Trigger | Action | Destination | Animation |
|---|---|---|---|---|
| Back arrow / breadcrumb | Click | Navigate | Portfolio Listing | Smart Animate |
| "Next project" CTA | Click | Navigate | Next Project Detail | Smart Animate |
| "Start a project" CTA | Click | Navigate | Contact page | Smart Animate |
| Image gallery thumbnail | Click | Open overlay | Lightbox overlay | Dissolve |
| Lightbox close button | Click | Close overlay | Project Detail | Dissolve |
| Lightbox left/right arrows | Click | Swap overlay | Next/prev image | Move In |

### Screen 4: Contact

| Element | Trigger | Action | Destination | Animation |
|---|---|---|---|---|
| Form field | Click | State change | Focus state | Smart Animate |
| Form field | Blur (after interact) | State change | Filled or error state | Smart Animate |
| Submit button | Click | Navigate | Success state | Smart Animate |
| Submit button (error) | Click | State change | Form with errors | Smart Animate |
| Success "Back to Home" | Click | Navigate | Homepage | Smart Animate |

---

## Flow F-04: Mobile Navigation

### Interaction Sequence

```
1. User taps hamburger icon (☰)
   → Nav overlay slides in from right

2. User taps a nav link
   → Nav overlay slides out
   → Page transitions via Smart Animate

3. User taps close button (✕)
   → Nav overlay slides out to right
   → Returns to current page
```

| Step | Trigger | Action | Animation | Duration | Easing |
|---|---|---|---|---|---|
| Open menu | Click hamburger | Open overlay | Move in (right) | 300ms | Ease out |
| Select link | Click nav item | Navigate to page | Smart Animate | 300ms | Ease in-out |
| Close menu | Click close / overlay bg | Close overlay | Move out (right) | 250ms | Ease in |

---

## Interaction Specifications

### Trigger Types

| Trigger | When to Use | Figma Setting |
|---|---|---|
| **On Click** | Buttons, links, cards, nav items | "On click" |
| **On Hover** | State previews, tooltips, dropdown menus | "While hovering" |
| **On Press** | Active/pressed states for buttons | "While pressing" |
| **On Drag** | Carousel, sliders, swipe gestures | "On drag" |
| **After Delay** | Auto-advancing carousels, toast auto-dismiss | "After delay" + ms |
| **Mouse Enter** | Dropdown menu open | "Mouse enter" |
| **Mouse Leave** | Dropdown menu close, tooltip dismiss | "Mouse leave" |

### Animation Types

| Animation | Description | Primary Use |
|---|---|---|
| **Smart Animate** | Interpolates matching layers between frames | Page transitions, state changes, micro-interactions |
| **Dissolve** | Cross-fade between frames | Overlay appearance, image transitions, content swap |
| **Move In** | New frame slides in from specified direction | Mobile nav, drawer panels, slide-over sheets |
| **Move Out** | Current frame slides out to specified direction | Closing overlays, dismissing drawers |
| **Push** | New frame pushes current frame off screen | Page-level forward/back navigation (alternative to Smart Animate) |
| **Slide In** | Content slides into view within the same frame | Dropdown menus, expanding sections |
| **Slide Out** | Content slides out of view | Closing dropdowns, collapsing sections |
| **Instant** | No animation | Development-only flows, fallback |

---

## Duration and Easing Standards

### Duration Scale

| Category | Duration | Use Case |
|---|---|---|
| Micro | 100ms | Hover state color change, focus ring appearance |
| Short | 150ms | Button press feedback, checkbox toggle, tooltip show |
| Standard | 200ms | Dropdown open, accordion expand, tab switch |
| Medium | 300ms | Page transition (Smart Animate), overlay open, drawer slide |
| Long | 400ms | Complex layout rearrangement, multi-element orchestration |
| Extra long | 500ms | Full-page dissolve, onboarding sequences |

### Easing Curves

| Easing | Figma Name | CSS Equivalent | Use Case |
|---|---|---|---|
| **Ease out** | Ease out | `cubic-bezier(0, 0, 0.2, 1)` | Elements entering the screen (overlays, drawers, tooltips) |
| **Ease in** | Ease in | `cubic-bezier(0.4, 0, 1, 1)` | Elements leaving the screen (closing overlays, dismissing toasts) |
| **Ease in-out** | Ease in and out | `cubic-bezier(0.4, 0, 0.2, 1)` | Elements moving on screen (page transitions, layout shifts) |
| **Linear** | Linear | `linear` | Progress bars, loading indicators, opacity fades |
| **Spring** | Custom spring | Custom | Playful interactions (not used in base system) |

### Duration × Animation Matrix

| Interaction | Animation | Duration | Easing |
|---|---|---|---|
| Button hover state | Smart Animate | 100ms | Ease out |
| Button active state | Smart Animate | 50ms | Ease in |
| Focus ring appear | Smart Animate | 100ms | Ease out |
| Tooltip show | Dissolve | 150ms | Ease out |
| Tooltip hide | Dissolve | 100ms | Ease in |
| Dropdown open | Move In (bottom) | 200ms | Ease out |
| Dropdown close | Move Out (bottom) | 150ms | Ease in |
| Modal open | Dissolve (bg) + Scale (content) | 300ms | Ease out |
| Modal close | Dissolve | 200ms | Ease in |
| Drawer open | Move In (right/left) | 300ms | Ease out |
| Drawer close | Move Out (right/left) | 250ms | Ease in |
| Page transition | Smart Animate | 300ms | Ease in-out |
| Toast appear | Move In (bottom) | 300ms | Ease out |
| Toast auto-dismiss | Move Out (bottom) | 250ms | Ease in |
| Toast auto-dismiss delay | After delay | 5000ms | -- |
| Tab content switch | Dissolve | 200ms | Ease in-out |
| Accordion expand | Smart Animate | 200ms | Ease out |
| Image lightbox open | Dissolve | 300ms | Ease out |
| Image lightbox close | Dissolve | 200ms | Ease in |
| Filter state change | Smart Animate | 300ms | Ease in-out |
| Theme toggle | Smart Animate | 300ms | Ease in-out |

---

## Overlay Behavior

### Modal Overlay

| Property | Value |
|---|---|
| Type | Overlay (manual position: centered) |
| Background | `color-surface-overlay` (black 50%) |
| Close on click outside | Yes |
| Close animation | Dissolve, 200ms, ease in |
| Scroll behavior | Content scrolls within modal body; background does not scroll |

### Dropdown Menu

| Property | Value |
|---|---|
| Type | Overlay (relative to trigger) |
| Position | Below trigger, aligned to left edge |
| Offset | 4px below trigger |
| Background | No overlay dimming |
| Close on click outside | Yes |
| Open animation | Move In (top), 200ms, ease out |
| Close animation | Move Out (top), 150ms, ease in |
| Max height | 320px (scrollable) |

### Tooltip

| Property | Value |
|---|---|
| Type | Overlay (relative to trigger) |
| Position | Above trigger by default; auto-flip if near edge |
| Offset | 8px from trigger |
| Background | No overlay dimming |
| Trigger | While hovering |
| Show delay | 300ms (after delay) |
| Hide | On mouse leave, instant |
| Animation | Dissolve, 150ms, ease out |

### Mobile Navigation Drawer

| Property | Value |
|---|---|
| Type | Overlay (manual position: right edge) |
| Width | 280px |
| Height | Full screen height |
| Background | `color-surface-overlay` (black 50%) |
| Close on click outside | Yes |
| Open animation | Move In (right), 300ms, ease out |
| Close animation | Move Out (right), 250ms, ease in |

### Toast Notification

| Property | Value |
|---|---|
| Type | Overlay (manual position: bottom-center or top-right) |
| Background | No overlay dimming |
| Close on click outside | No |
| Auto dismiss | After 5000ms |
| Dismiss animation | Move Out (bottom), 250ms, ease in |
| Stack behavior | New toasts push existing ones up; max 3 visible |

---

## Scroll Behavior

### Fixed Scroll Regions

| Element | Scroll Behavior | Notes |
|---|---|---|
| Navigation bar | Fixed to top | `position: sticky` in implementation; in Figma, use "Fix position when scrolling" |
| Sidebar | Fixed, independent scroll | Sidebar scrolls independently from main content |
| Modal body | Scrollable | Body area scrolls; header and footer are fixed |
| Page background (under modal) | Scroll locked | Background does not scroll when modal is open |
| Footer | Normal scroll | Scrolls with content; appears at bottom |

### Figma Scroll Prototype Settings

For scrollable prototype frames:

1. **Vertical scrolling pages**: Set the frame height to the full content height (not viewport). In prototype settings, set "Overflow scrolling" to "Vertical."
2. **Fixed header**: Select the nav bar frame, check "Fix position when scrolling" in the prototype panel.
3. **Horizontal carousels**: Create a frame at viewport width with "Overflow scrolling" set to "Horizontal." Place the carousel content (wider than the frame) inside.

### Scroll-Triggered Animations (Annotation Only)

Figma does not natively support scroll-triggered animations, but annotate them for developer reference:

| Element | Scroll Trigger | Animation | Notes |
|---|---|---|---|
| Section headings | Enter viewport | Fade in + slide up | 20px translate, 400ms, ease out |
| Project cards | Enter viewport | Staggered fade in | 100ms stagger between cards |
| Progress bar (skill section) | Enter viewport | Width animates from 0 to value | 600ms, ease out |
| Back-to-top button | Scroll > 500px | Fade in | 200ms, ease out |
| Nav bar shadow | Scroll > 0px | Add shadow | `shadow-sm` appears on scroll |

Annotate these in Figma using `_Annotation / Scroll Behavior` frames placed adjacent to the relevant section.

---

## Prototype Device Settings

### Desktop Prototype

| Setting | Value |
|---|---|
| Device | None (custom size) |
| Frame size | 1440x900 (viewport) |
| Background color | `color-bg-primary` |
| Starting frame | Homepage / Desktop Wide (1440) |

### Tablet Prototype

| Setting | Value |
|---|---|
| Device | iPad Mini |
| Frame size | 768x1024 |
| Orientation | Portrait |
| Starting frame | Homepage / Tablet (768) |

### Mobile Prototype

| Setting | Value |
|---|---|
| Device | iPhone 15 |
| Frame size | 375x812 |
| Orientation | Portrait |
| Starting frame | Homepage / Mobile (375) |

---

## Prototype Naming Convention

Each prototype flow frame follows this naming pattern:

```
[Flow ID] - [Screen Name] / [Breakpoint] / [State]
```

Examples:

```
F-01 - Homepage / Desktop / Default
F-01 - Homepage / Desktop / Dark
F-01 - Portfolio Listing / Desktop / Default
F-01 - Portfolio Listing / Desktop / Filtered
F-01 - Project Detail / Desktop / Default
F-01 - Project Detail / Desktop / Lightbox Open
F-01 - Contact / Desktop / Default
F-01 - Contact / Desktop / Filled
F-01 - Contact / Desktop / Error
F-01 - Contact / Desktop / Success
F-04 - Homepage / Mobile / Nav Open
F-04 - Homepage / Mobile / Nav Closed
```

---

## Interaction Annotation Standards

For each prototype screen, add an annotation frame (`_Annotation / Interactions`) positioned to the right of the screen with 80px spacing. The annotation frame contains:

| Element | Format |
|---|---|
| Screen name | Inter SemiBold, 16px |
| Numbered hotspots | Red circles (24px diameter) with white number labels, positioned over interactive elements |
| Interaction table | Lists each numbered hotspot with: trigger, action, destination, animation, duration, easing |
| Notes | Any special behavior not captured in the table (e.g., "scroll-triggered", "after 5s delay") |

Example annotation table:

```
#  Trigger    Action      Destination           Animation       Duration  Easing
1  Click      Navigate    Portfolio Listing      Smart Animate   300ms     Ease in-out
2  Click      Navigate    About                  Smart Animate   300ms     Ease in-out
3  Click      Navigate    Contact                Smart Animate   300ms     Ease in-out
4  Hover      State chg   Card hover state       Smart Animate   100ms     Ease out
5  Click      Navigate    Project Detail         Smart Animate   300ms     Ease in-out
6  Click      Open ovl    Theme toggle           Smart Animate   300ms     Ease in-out
```
