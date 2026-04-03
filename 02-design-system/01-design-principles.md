# Design Principles

Six core principles guide every decision in the Flavio Fusuma Design System. They are ordered by priority -- when principles conflict, the one listed first takes precedence.

Each principle includes a rationale, practical examples, and explicit do/don't guidance.

---

## 1. Clarity Over Cleverness

### Statement

Choose the obvious solution. If a user has to think about the interface, the interface has failed.

### Rationale

Clever interactions impress other designers but confuse real users. Clarity scales across cultures, literacy levels, and device contexts. When every element communicates its purpose unambiguously, users complete tasks faster and with fewer errors.

### In Practice

- Use established UI conventions (e.g., underlined links, filled primary buttons) rather than novel patterns.
- Label icons with text whenever space allows.
- Write interface copy at an 8th-grade reading level or lower.
- Prefer explicit state changes (e.g., a visible success message) over subtle cues (e.g., a brief color flash).

### Do / Don't

| Do | Don't |
|---|---|
| Use a labeled button ("Save Changes") for the primary action. | Use an unlabeled icon that requires a tooltip to understand. |
| Show a confirmation dialog before a destructive action. | Rely on an undo toast as the only safeguard against data loss. |
| Display form validation errors inline, next to the relevant field. | Collect all errors into a single banner at the top of the page. |
| Use a standard navigation pattern (sidebar, top nav) users already know. | Invent a gesture-based navigation that requires onboarding to learn. |
| Present data in a simple table when the user needs to compare values. | Use an animated visualization when a table would answer the question faster. |

---

## 2. Accessible By Default

### Statement

Every default meets WCAG 2.1 AA. Accessibility is a baseline, not a feature.

### Rationale

Over one billion people worldwide live with some form of disability. Accessible design is not an edge case -- it is the common case. When accessibility is designed in from the start, it improves the experience for everyone: users on slow connections, users in bright sunlight, users navigating with a keyboard, and users relying on screen readers.

### In Practice

- All text meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
- Interactive elements have a minimum target size of 44x44 CSS pixels.
- Every image, icon, and non-text element has an accessible name.
- Focus order follows a logical reading sequence, and focus indicators are always visible.
- Color is never the sole means of conveying information.

### Do / Don't

| Do | Don't |
|---|---|
| Pair color indicators with icons or text labels (e.g., a red icon AND the word "Error"). | Use red text alone to signal an error state. |
| Provide visible focus rings on all interactive elements. | Remove the default browser focus outline without replacing it. |
| Use semantic HTML (`<button>`, `<nav>`, `<main>`) for built-in accessibility. | Build custom controls from `<div>` and `<span>` without ARIA roles. |
| Test with screen readers (VoiceOver, NVDA) during development, not after. | Treat accessibility as a QA phase that happens before launch. |
| Set `min-height: 44px` on touch targets, even when visual design suggests smaller. | Make small icon-only buttons (24x24) the primary tap target on mobile. |

---

## 3. Systematic Flexibility

### Statement

Provide structured options, not open-ended freedom. Constrain choices to those that produce good outcomes.

### Rationale

A design system that offers infinite flexibility is not a system -- it is a suggestion. By defining scales, tokens, and deliberate constraints, the system ensures that every combination of values looks intentional. Teams move faster because they choose from a curated menu rather than inventing from scratch.

### In Practice

- Use the 8px spacing scale rather than arbitrary pixel values.
- Select colors only from the defined palette; do not introduce one-off hex values.
- Choose type sizes from the 12-level type scale; do not interpolate between levels.
- Layouts are built on the 12-column grid; asymmetric layouts use defined column spans (e.g., 3+9, 8+4).
- When a new need arises, extend the system formally rather than adding a local override.

### Do / Don't

| Do | Don't |
|---|---|
| Use `space-4` (32px) for consistent card padding. | Use `padding: 30px` because it "looks right." |
| Choose `heading-md` from the type scale for section headings. | Set a font size of 22px because it fits the layout better than the scale values. |
| Use `color-primary-500` for primary actions. | Sample a blue from a reference screenshot and hard-code the hex value. |
| Propose a new token when no existing token fits a genuine need. | Duplicate an existing token with a different name for a single component. |
| Build responsive layouts using the defined breakpoints. | Add a 920px breakpoint because one page looks awkward at that width. |

---

## 4. Content First

### Statement

Design around real content. The interface exists to serve the content, not the other way around.

### Rationale

Lorem ipsum hides design problems. When layouts are built around realistic content -- actual headlines, real data, translated strings -- they accommodate the messiness of production from the start. Content-first design produces interfaces that remain robust when headings are long, data sets are empty, and translations double the string length.

### In Practice

- Design with representative content from the earliest wireframe.
- Set maximum line widths (measure) for readability: 60--75 characters for body text.
- Account for empty states, error states, and overflow in every component.
- Test layouts with the longest supported language (often German or Finnish) early.
- Prioritize content hierarchy through type scale and spacing, not decoration.

### Do / Don't

| Do | Don't |
|---|---|
| Use real product names, actual user data (anonymized), and representative text lengths. | Design with "Lorem ipsum dolor sit amet" and assume real content will fit. |
| Define a max-width on body text containers (~65ch) for comfortable reading. | Allow body text to span the full width of a 1440px viewport. |
| Design empty states with helpful messaging and a clear call to action. | Show a blank white screen when a data table has no rows. |
| Truncate overflowing text with an ellipsis AND provide access to the full text (tooltip, expand). | Clip overflowing text with `overflow: hidden` and no way to see the rest. |
| Test card layouts with both very short and very long content. | Only test with the "ideal" content length that fits the design perfectly. |

---

## 5. Purposeful Motion

### Statement

Every animation communicates something. If it does not, remove it.

### Rationale

Motion is a powerful communication tool: it can show relationships, guide attention, and reinforce spatial models. But gratuitous animation slows perceived performance, triggers motion sensitivities, and adds maintenance cost. Every transition in the system must justify its existence by answering: "What does this help the user understand?"

### In Practice

- Use motion to show cause and effect (e.g., a button press triggering a panel slide).
- Keep durations short: 150ms for micro-interactions, 300ms for layout transitions, 500ms maximum for page-level transitions.
- Respect `prefers-reduced-motion`: reduce or remove animations for users who request it.
- Use easing curves that feel natural: ease-out for entrances, ease-in for exits.
- Avoid animation on first paint -- content should be immediately available.

### Do / Don't

| Do | Don't |
|---|---|
| Animate a dropdown opening downward to show where it came from. | Add a bounce effect to a dropdown because it "feels fun." |
| Use a 150ms fade for tooltip appearance to avoid visual pop-in. | Animate tooltips with a 500ms slide-and-fade sequence. |
| Provide `@media (prefers-reduced-motion: reduce)` overrides that disable non-essential motion. | Ignore the reduced-motion preference because "the animation is subtle." |
| Use a brief loading skeleton that transitions to content. | Show a spinning logo animation while content loads. |
| Keep page transitions under 300ms so navigation feels instant. | Use a 1-second cross-fade between pages for "cinematic" effect. |

---

## 6. Honest Interfaces

### Statement

The UI must never mislead. States, affordances, and feedback must be truthful.

### Rationale

Trust is the foundation of every user relationship. When a button looks clickable, it must be clickable. When a progress bar shows 80%, 80% of the work must actually be complete. When a form says "Saved," the data must be saved. Dishonest interfaces -- even when well-intentioned -- erode trust and create anxiety.

### In Practice

- Disabled elements must look disabled: reduced opacity, no pointer cursor, clear visual distinction.
- Progress indicators must reflect actual progress, not estimated or faked progress.
- Destructive actions must be visually distinct from safe actions.
- Error messages must describe what happened and what the user can do, not generic "Something went wrong."
- Pricing, data usage, and permission requests must be presented without dark patterns.

### Do / Don't

| Do | Don't |
|---|---|
| Show a determinate progress bar only when you can measure actual progress. | Animate a fake progress bar that reaches 90% instantly then stalls. |
| Style destructive buttons (delete, remove) with a warning color and confirm step. | Style a "Delete Account" button identically to "Save Changes." |
| Disable a submit button and explain why ("Complete all required fields"). | Hide the submit button with no explanation until all fields are valid. |
| Show real-time status: "Saving..." then "Saved" then "Last saved 2 min ago." | Show a checkmark immediately on click before the server confirms the save. |
| Write error messages that explain the cause and suggest a fix: "Email address is not valid. Example: name@example.com." | Display "Error 422" or "Something went wrong. Please try again." |

---

## Applying the Principles

### When Principles Conflict

Principles are listed in priority order. If two principles suggest different solutions, the higher-ranked principle wins. For example:

- **Clarity vs. Motion**: If an animation makes the interface harder to understand, remove it (Clarity wins).
- **Accessibility vs. Flexibility**: If a systematic constraint produces an inaccessible outcome, accessibility takes priority.
- **Content vs. Honesty**: These rarely conflict, but if displaying real content would mislead (e.g., showing stale data as current), honesty wins -- show a "data may be outdated" indicator.

### Principle Checklist for Design Reviews

Use this checklist during design reviews to verify that a design honors the system principles:

- [ ] Can a first-time user complete the primary task without instructions? (Clarity)
- [ ] Does every text/background combination meet WCAG 2.1 AA contrast? (Accessible)
- [ ] Are all values (colors, spacing, type sizes) drawn from system tokens? (Systematic)
- [ ] Has the design been tested with realistic content, including edge cases? (Content)
- [ ] Does every animation answer "what does this help the user understand?" (Motion)
- [ ] Do all interactive states (disabled, loading, error, success) accurately reflect reality? (Honest)
