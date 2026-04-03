# Pagination

> Flavio Fusuma Design System -- Component Documentation

---

## Overview

Pagination divides large sets of content into discrete pages, allowing users to navigate through results in manageable chunks. It communicates the total scope of results and the user's current position within the set. Use pagination when content exceeds a single view and users benefit from browsing sequentially through pages.

---

## Anatomy

### Numbered Pagination

```
┌──────────────────────────────────────────────────────────────┐
│  ┌───┐  ┌───┐ ┌───┐ ┌───┐ ┌───┐       ┌───┐ ┌───┐ ┌───┐  │
│  │ < │  │ 1 │ │ 2 │ │ 3 │ │...│       │ 9 │ │10 │ │ > │  │
│  │   │  │   │ │███│ │   │ │   │       │   │ │   │ │   │  │
│  └───┘  └───┘ └───┘ └───┘ └───┘       └───┘ └───┘ └───┘  │
│  prev    pages  active              ellipsis  last   next  │
└──────────────────────────────────────────────────────────────┘
```

### Simple Pagination (Prev/Next)

```
┌──────────────────────────────────────────────┐
│  ┌──────────┐    Page 2 of 10   ┌──────────┐ │
│  │ Previous │                   │   Next   │ │
│  └──────────┘                   └──────────┘ │
└──────────────────────────────────────────────┘
```

### Load More

```
┌──────────────────────────────────────────────┐
│                                              │
│         Showing 20 of 156 results            │
│                                              │
│           ┌────────────────┐                 │
│           │   Load More    │                 │
│           └────────────────┘                 │
│                                              │
└──────────────────────────────────────────────┘
```

### Full-Featured Pagination

```
┌────────────────────────────────────────────────────────────────────────┐
│  Showing 11-20 of 156   ┌──────────────┐   ┌───┐┌───┐┌───┐   ┌─────┐│
│                          │ 10 per page ▼│   │ < ││1-5││ > │   │Go to││
│  results                 └──────────────┘   └───┘└───┘└───┘   │ __ ││
│                           page size          prev/next         └─────┘│
└────────────────────────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Outer wrapper with flexbox layout |
| Previous button | Yes | Navigates to the previous page |
| Next button | Yes | Navigates to the next page |
| Page numbers | No | Individual page buttons (numbered variant) |
| Active page indicator | Yes | Highlights the current page |
| Ellipsis | No | Indicates skipped pages in numbered variant |
| Results summary | No | Text showing "Showing X-Y of Z results" |
| Page size selector | No | Dropdown to change items per page |
| Jump to page | No | Input field to navigate directly to a page number |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Numbered | Page number buttons with prev/next arrows | Data tables, search results, product listings |
| Simple (prev/next) | Only previous and next buttons with page indicator | Blog posts, article navigation, simple content flows |
| Load more | Single button to append more results | Social feeds, infinite-scroll alternatives, card grids |

---

## States

### Page Number Button States

| State | Background | Border | Text | Notes |
|-------|-----------|--------|------|-------|
| Default | `transparent` | `transparent` | `neutral-600` | Resting state |
| Hover | `neutral-50` | `neutral-200` | `neutral-900` | Mouse over |
| Active (current page) | `blue-600` | `blue-600` | `neutral-0` | Filled blue background |
| Focus | `transparent` | `transparent` | `neutral-600` | 2px focus ring `blue-600` |
| Disabled | `transparent` | `transparent` | `neutral-300` | Not applicable (pages are always valid) |

### Previous / Next Button States

| State | Background | Border | Text / Icon | Notes |
|-------|-----------|--------|-------------|-------|
| Default | `transparent` | `neutral-200` | `neutral-600` | Resting state |
| Hover | `neutral-50` | `neutral-300` | `neutral-900` | Mouse over |
| Active | `neutral-100` | `neutral-400` | `neutral-900` | Mouse down |
| Focus | `transparent` | `neutral-200` | `neutral-600` | 2px focus ring `blue-600` |
| Disabled | `transparent` | `neutral-100` | `neutral-300` | First page (prev) or last page (next) |

### Load More Button States

| State | Background | Border | Text | Notes |
|-------|-----------|--------|------|-------|
| Default | `transparent` | `blue-600` | `blue-600` | Outline button style |
| Hover | `blue-50` | `blue-700` | `blue-700` | Mouse over |
| Active | `blue-100` | `blue-800` | `blue-800` | Mouse down |
| Focus | `transparent` | `blue-600` | `blue-600` | 2px focus ring `blue-600` |
| Loading | `transparent` | `blue-600` | spinner | Fetching next batch |

### Ellipsis States

| State | Text Color | Notes |
|-------|-----------|-------|
| Default | `neutral-400` | Three dots, non-interactive |
| Hover (if expandable) | `neutral-600` | Clickable to show hidden pages |

---

## Sizing

| Property | Value | Token |
|----------|-------|-------|
| Page button size | 36px x 36px | -- |
| Page button border-radius | `{border.radius.md}` (6px) | -- |
| Page button font size | 14px / medium (500) | `{typography.body.md}` |
| Prev/Next button height | 36px | -- |
| Prev/Next button padding | 8px 12px | `{space.2}` `{space.3}` |
| Prev/Next border-radius | `{border.radius.md}` (6px) | -- |
| Icon size (arrows) | 16px | -- |
| Button gap | 4px | `{space.1}` |
| Container gap | 16px | `{space.4}` |
| Results text font size | 14px / regular (400) | `{typography.body.md}` |
| Page size selector width | 120px | -- |
| Jump-to-page input width | 64px | -- |
| Min touch target | 44px | Padded hit area for mobile |

---

## Page Size Selector

| Property | Value | Notes |
|----------|-------|-------|
| Default options | 10, 25, 50, 100 | Configurable |
| Default selected | 10 | First option |
| Label | "per page" or "rows per page" | Placed after the select |
| Select style | Matches form select component | Uses `ff-select--sm` styling |

---

## Jump to Page

| Property | Value | Notes |
|----------|-------|-------|
| Input type | `number` | With `min="1"` and `max="[total pages]"` |
| Label | "Go to page" | Visible label or `aria-label` |
| Submit | On `Enter` keypress | Navigates to entered page number |
| Validation | Clamps to valid range | Out-of-range values snap to nearest valid page |

---

## Accessibility

- **Role**: Use `<nav>` with `aria-label="Pagination"`. Page buttons use a `<ul>` / `<li>` list structure.
- **ARIA -- current page**: The active page button uses `aria-current="page"`.
- **ARIA -- prev/next**: Buttons use `aria-label="Go to previous page"` and `aria-label="Go to next page"`. When disabled, use `aria-disabled="true"`.
- **ARIA -- page numbers**: Each page button has `aria-label="Go to page N"`.
- **ARIA -- results**: The results summary uses `aria-live="polite"` to announce updates when the page changes.
- **Keyboard**:
  - `Tab` / `Shift+Tab` moves through pagination controls.
  - `Enter` or `Space` activates a page button.
  - For the jump-to-page input, `Enter` triggers navigation.
- **Screen reader**: Announces the pagination landmark, current page, and total pages. Page changes announce the new results summary.
- **Focus**: Visible focus ring on all interactive elements. After page change, focus moves to the first item of the new page content or remains on the pagination control.
- **Color**: Active page uses both color (filled `blue-600` background) and visual weight to distinguish from other pages.

---

## Design Tokens

```json
{
  "pagination": {
    "font-family": "{typography.font.sans}",
    "font-weight": "500",
    "font-size": "{typography.body.md.size}",
    "transition": "all 150ms ease",
    "focus-ring-width": "2px",
    "focus-ring-offset": "2px",
    "focus-ring-color": "{color.blue.600}",
    "container-gap": "{space.4}",
    "button-gap": "{space.1}",
    "page-button": {
      "size": "36px",
      "border-radius": "{border.radius.md}",
      "bg": "transparent",
      "bg-hover": "{color.neutral.50}",
      "bg-active": "{color.blue.600}",
      "text-color": "{color.neutral.600}",
      "text-hover": "{color.neutral.900}",
      "text-active": "{color.neutral.0}",
      "text-disabled": "{color.neutral.300}",
      "border-hover": "{color.neutral.200}"
    },
    "nav-button": {
      "height": "36px",
      "padding-x": "{space.3}",
      "padding-y": "{space.2}",
      "border-radius": "{border.radius.md}",
      "border-color": "{color.neutral.200}",
      "border-hover": "{color.neutral.300}",
      "border-disabled": "{color.neutral.100}",
      "bg": "transparent",
      "bg-hover": "{color.neutral.50}",
      "text-color": "{color.neutral.600}",
      "text-hover": "{color.neutral.900}",
      "text-disabled": "{color.neutral.300}",
      "icon-size": "16px"
    },
    "ellipsis": {
      "color": "{color.neutral.400}",
      "size": "36px"
    },
    "results-text": {
      "color": "{color.neutral.500}",
      "font-weight": "400"
    },
    "load-more": {
      "border-color": "{color.blue.600}",
      "text-color": "{color.blue.600}",
      "bg-hover": "{color.blue.50}",
      "border-radius": "{border.radius.md}",
      "padding": "{space.2} {space.6}"
    },
    "page-size-selector": {
      "width": "120px"
    },
    "jump-to-page": {
      "width": "64px"
    }
  }
}
```

---

## Usage Guidelines

**Do:**
- Use numbered pagination for data-heavy interfaces where users need random access to specific pages.
- Use simple prev/next pagination for sequential content like articles or blog posts.
- Use the load-more pattern for card grids and social feeds where appending feels natural.
- Always show the results summary (e.g., "Showing 11-20 of 156") to orient users within the full set.
- Disable the previous button on the first page and the next button on the last page.
- Include a page size selector when users may want to control how much content they see at once.

**Don't:**
- Don't use pagination for fewer than two pages of content; show all items directly.
- Don't display more than seven page number buttons at once; use ellipsis for larger ranges.
- Don't combine numbered pagination with load-more in the same interface; pick one pattern.
- Don't remove the current page indicator when the user is on a middle page.
- Don't reset scroll position without user expectation; scroll to the top of the results after page change.
- Don't use pagination when infinite scroll with a sentinel element would provide a better experience (e.g., image galleries).

---

## Code Example

### HTML

```html
<!-- Numbered pagination -->
<nav class="ff-pagination" aria-label="Pagination">
  <span class="ff-pagination__summary" aria-live="polite">
    Showing 11-20 of 156 results
  </span>
  <ul class="ff-pagination__list">
    <li>
      <button class="ff-pagination__btn ff-pagination__btn--prev" aria-label="Go to previous page">
        <svg aria-hidden="true"><!-- chevron-left --></svg>
        <span class="ff-pagination__btn-label">Previous</span>
      </button>
    </li>
    <li>
      <button class="ff-pagination__page" aria-label="Go to page 1">1</button>
    </li>
    <li>
      <button class="ff-pagination__page ff-pagination__page--active" aria-current="page" aria-label="Page 2">2</button>
    </li>
    <li>
      <button class="ff-pagination__page" aria-label="Go to page 3">3</button>
    </li>
    <li>
      <span class="ff-pagination__ellipsis" aria-hidden="true">...</span>
    </li>
    <li>
      <button class="ff-pagination__page" aria-label="Go to page 16">16</button>
    </li>
    <li>
      <button class="ff-pagination__btn ff-pagination__btn--next" aria-label="Go to next page">
        <span class="ff-pagination__btn-label">Next</span>
        <svg aria-hidden="true"><!-- chevron-right --></svg>
      </button>
    </li>
  </ul>
</nav>

<!-- Simple prev/next -->
<nav class="ff-pagination ff-pagination--simple" aria-label="Pagination">
  <button class="ff-pagination__btn ff-pagination__btn--prev" aria-label="Go to previous page">
    <svg aria-hidden="true"><!-- chevron-left --></svg>
    Previous
  </button>
  <span class="ff-pagination__indicator">Page 2 of 10</span>
  <button class="ff-pagination__btn ff-pagination__btn--next" aria-label="Go to next page">
    Next
    <svg aria-hidden="true"><!-- chevron-right --></svg>
  </button>
</nav>

<!-- Load more -->
<div class="ff-pagination ff-pagination--load-more">
  <p class="ff-pagination__summary">Showing 20 of 156 results</p>
  <button class="ff-pagination__load-more-btn">
    Load More
  </button>
</div>

<!-- Full-featured with page size and jump-to -->
<nav class="ff-pagination ff-pagination--full" aria-label="Pagination">
  <span class="ff-pagination__summary" aria-live="polite">Showing 11-20 of 156 results</span>
  <div class="ff-pagination__page-size">
    <label for="page-size">Rows per page:</label>
    <select id="page-size" class="ff-select ff-select--sm">
      <option value="10" selected>10</option>
      <option value="25">25</option>
      <option value="50">50</option>
      <option value="100">100</option>
    </select>
  </div>
  <ul class="ff-pagination__list">
    <!-- page buttons -->
  </ul>
  <div class="ff-pagination__jump">
    <label for="jump-page">Go to page:</label>
    <input type="number" id="jump-page" class="ff-input ff-input--sm" min="1" max="16" />
  </div>
</nav>
```

### JSX

```jsx
import { Pagination, SimplePagination, LoadMore } from '@flaviofusuma/ui';

{/* Numbered pagination */}
<Pagination
  currentPage={2}
  totalPages={16}
  totalItems={156}
  itemsPerPage={10}
  onPageChange={(page) => setCurrentPage(page)}
  showSummary
/>

{/* Simple prev/next */}
<SimplePagination
  currentPage={2}
  totalPages={10}
  onPrevious={() => setPage(page - 1)}
  onNext={() => setPage(page + 1)}
/>

{/* Load more */}
<LoadMore
  loadedCount={20}
  totalCount={156}
  onLoadMore={handleLoadMore}
  loading={isLoading}
/>

{/* Full-featured */}
<Pagination
  currentPage={2}
  totalPages={16}
  totalItems={156}
  itemsPerPage={10}
  onPageChange={(page) => setCurrentPage(page)}
  showSummary
  showPageSize
  pageSizeOptions={[10, 25, 50, 100]}
  onPageSizeChange={(size) => setPageSize(size)}
  showJumpTo
/>
```

---

## Related Components

- **[Breadcrumbs](/02-design-system/05-components/breadcrumbs.md)** -- For hierarchical navigation; breadcrumbs show position in a tree, pagination shows position in a sequence.
- **[Buttons](/02-design-system/05-components/buttons.md)** -- Pagination controls use button patterns; prev/next and load-more are button variants.
- **[Select](/02-design-system/05-components/select.md)** -- The page size selector uses the select component internally.
- **[Inputs](/02-design-system/05-components/inputs.md)** -- The jump-to-page field uses the input component internally.
