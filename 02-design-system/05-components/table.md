# Table

> Tables organize and display structured data in rows and columns, enabling users to scan, compare, and act on information efficiently.

---

## Overview

The Table component presents tabular data with support for sorting, row selection, striped rows, hover highlighting, and sticky headers. Tables handle responsive breakpoints gracefully by offering horizontal scroll or stacked layouts for narrow viewports. Pagination can be integrated at the table footer for large datasets.

---

## Anatomy

```
┌──────────────────────────────────────────────────────────────┐
│  Table Container                                             │
│  ┌──────────────────────────────────────────────────────────┐│
│  │  Header Row                                              ││
│  │  ┌──────┬──────────────┬────────────┬──────────┬───────┐ ││
│  │  │ [CB] │ Name    [^]  │ Role       │ Status   │ Actn  │ ││
│  │  └──────┴──────────────┴────────────┴──────────┴───────┘ ││
│  ├──────────────────────────────────────────────────────────┤│
│  │  Body                                                    ││
│  │  ┌──────┬──────────────┬────────────┬──────────┬───────┐ ││
│  │  │ [CB] │ Jane Doe     │ Designer   │ Active   │ [...]  │││
│  │  ├──────┼──────────────┼────────────┼──────────┼───────┤ ││
│  │  │ [CB] │ John Smith   │ Developer  │ Inactive │ [...]  │││
│  │  └──────┴──────────────┴────────────┴──────────┴───────┘ ││
│  ├──────────────────────────────────────────────────────────┤│
│  │  Footer                                                  ││
│  │  ┌────────────────────────────────────────────────┐      ││
│  │  │ Showing 1-10 of 42        [< 1 2 3 4 5 >]     │      ││
│  │  └────────────────────────────────────────────────┘      ││
│  └──────────────────────────────────────────────────────────┘│
└──────────────────────────────────────────────────────────────┘
```

| Part | Required | Description |
|------|----------|-------------|
| Container | Yes | Scrollable wrapper that contains the table |
| Header Row | Yes | Column labels with optional sort controls |
| Body | Yes | Data rows containing cell content |
| Footer | No | Summary row, totals, or pagination controls |
| Checkbox | No | Row-level and header-level select controls |
| Sort indicator | No | Ascending/descending arrow icon in header cells |
| Action cell | No | Row-level action menu (edit, delete, view) |

---

## Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| Default | Plain table with header and body | Simple data display |
| Striped | Alternating row background colors | Improved scan-ability for dense data |
| Bordered | Cell borders on all sides | Data that requires clear cell delineation |
| Hoverable | Row highlight on mouse hover | Interactive tables where rows are clickable |
| Compact | Reduced cell padding | Dense data displays, dashboards |
| Selectable | Checkbox column for row selection | Bulk actions on multiple rows |
| Sortable | Clickable header cells with sort indicators | Data that benefits from reordering |

---

## States

### Row States

| State | Background | Border | Text | Notes |
|-------|-----------|--------|------|-------|
| Default | `white` | `neutral-200` bottom | `neutral-900` | Resting state |
| Hover | `neutral-50` | `neutral-200` bottom | `neutral-900` | Mouse over (hoverable variant) |
| Selected | `blue-50` | `blue-200` bottom | `neutral-900` | Checkbox checked |
| Striped (even) | `neutral-50` | `neutral-200` bottom | `neutral-900` | Even rows in striped variant |
| Disabled | `neutral-50` | `neutral-200` bottom | `neutral-400` | Non-interactive row |

### Header States

| State | Background | Text | Icon | Notes |
|-------|-----------|------|------|-------|
| Default | `neutral-50` | `neutral-700` | `neutral-400` | Unsorted column |
| Hover | `neutral-100` | `neutral-900` | `neutral-600` | Sortable header hover |
| Active sort (asc) | `neutral-100` | `blue-600` | `blue-600` (up) | Sorted ascending |
| Active sort (desc) | `neutral-100` | `blue-600` | `blue-600` (down) | Sorted descending |

### Cell States

| State | Appearance | Notes |
|-------|-----------|-------|
| Default | Standard text rendering | Normal cell content |
| Truncated | Text with ellipsis | When content exceeds max-width |
| Empty | En-dash `--` in neutral-400 | No data available for cell |
| Loading | Skeleton text placeholder | Data being fetched |

---

## Sizing

| Size | Row Height | Cell Padding (y / x) | Font Size | Header Font Size |
|------|-----------|----------------------|-----------|------------------|
| sm | 36px | 6px / 12px | 14px | 12px |
| md | 48px | 12px / 16px | 14px | 12px |
| lg | 56px | 16px / 16px | 16px | 14px |

### Column Widths

| Type | Behavior | Notes |
|------|----------|-------|
| Auto | Columns size to content | Default behavior |
| Fixed | Explicit pixel or percentage widths | Use for consistent layouts |
| Min-width | Minimum width with flexible growth | Prevents content cramming |
| Checkbox column | 48px fixed | Consistent selection column |
| Action column | 56px fixed | Consistent action menu column |

---

## Responsive Behavior

| Breakpoint | Strategy | Description |
|------------|----------|-------------|
| >= 1024px | Full table | All columns visible, horizontal layout |
| 768px -- 1023px | Horizontal scroll | Table scrolls horizontally within container, shadow indicators on edges |
| < 768px (scroll) | Horizontal scroll | Compact padding, fewer visible columns, scroll for rest |
| < 768px (stack) | Stacked cards | Each row becomes a card with label:value pairs stacked vertically |

```
Stacked layout (mobile):
┌─────────────────────────┐
│  Name:     Jane Doe     │
│  Role:     Designer     │
│  Status:   Active       │
│  [Edit] [Delete]        │
├─────────────────────────┤
│  Name:     John Smith   │
│  Role:     Developer    │
│  Status:   Inactive     │
│  [Edit] [Delete]        │
└─────────────────────────┘
```

### Sticky Header

| Property | Value | Notes |
|----------|-------|-------|
| Position | `sticky` | Sticks to top of scroll container |
| Top offset | `0` (or configurable) | Adjustable for fixed navbars |
| z-index | `10` | Above body rows |
| Shadow | `0 2px 4px rgba(0,0,0,0.08)` | Visual cue when scrolled |
| Background | `neutral-50` | Opaque to cover scrolling rows |

---

## Pagination Integration

| Property | Description |
|----------|-------------|
| Placement | Table footer, right-aligned or centered |
| Page sizes | 10, 25, 50, 100 (configurable) |
| Navigation | Previous / Next arrows with page numbers |
| Info text | "Showing 1-10 of 42 results" |
| Disabled states | Previous disabled on page 1; Next disabled on last page |

---

## Accessibility

- **Role**: Use semantic `<table>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<th>`, `<td>` elements. Avoid `div`-based tables unless ARIA grid roles are fully implemented.
- **Caption**: Include a `<caption>` element or `aria-label` on the table describing its purpose.
- **Scope**: Use `scope="col"` on header cells.
- **Sorting**: Sortable headers use `aria-sort="ascending"`, `aria-sort="descending"`, or `aria-sort="none"`. Sorting buttons within `<th>` should have descriptive `aria-label` values such as "Sort by name ascending".
- **Selection**: Row checkboxes must have `aria-label` describing the row, e.g., "Select Jane Doe". The header checkbox uses `aria-label="Select all rows"`.
- **Keyboard**:
  - `Tab` moves focus between interactive elements (checkboxes, sort buttons, action menus, pagination).
  - `Enter` or `Space` activates sort toggles and checkboxes.
  - Arrow keys may navigate cells in grid mode (`role="grid"`).
- **Responsive**: Stacked card layouts must maintain label-value association using `<dl>`, `<dt>`, `<dd>` or `aria-label` on value cells.
- **Focus**: Visible focus ring on all interactive elements within the table (2px solid `blue-300`, 2px offset).
- **Live regions**: Use `aria-live="polite"` to announce sort changes and pagination updates.

---

## Design Tokens

```json
{
  "table": {
    "border-color": "{color.neutral.200}",
    "border-radius": "{border.radius.md}",
    "font-family": "{typography.font.sans}",
    "header": {
      "background": "{color.neutral.50}",
      "background-hover": "{color.neutral.100}",
      "text-color": "{color.neutral.700}",
      "text-color-active": "{color.primary.600}",
      "font-size": "{typography.caption.size}",
      "font-weight": "{typography.weight.semibold}",
      "text-transform": "uppercase",
      "letter-spacing": "0.05em"
    },
    "body": {
      "background": "{color.white}",
      "background-hover": "{color.neutral.50}",
      "background-selected": "{color.blue.50}",
      "background-stripe": "{color.neutral.50}",
      "text-color": "{color.neutral.900}",
      "font-size": "{typography.body.sm.size}"
    },
    "footer": {
      "background": "{color.neutral.50}",
      "text-color": "{color.neutral.600}",
      "font-size": "{typography.caption.size}"
    },
    "sizing": {
      "sm": {
        "row-height": "36px",
        "padding-x": "{space.3}",
        "padding-y": "{space.1.5}"
      },
      "md": {
        "row-height": "48px",
        "padding-x": "{space.4}",
        "padding-y": "{space.3}"
      },
      "lg": {
        "row-height": "56px",
        "padding-x": "{space.4}",
        "padding-y": "{space.4}"
      }
    },
    "sticky-header-shadow": "0 2px 4px rgba(0, 0, 0, 0.08)",
    "sticky-header-z-index": "10",
    "sort-icon-color": "{color.neutral.400}",
    "sort-icon-color-active": "{color.primary.600}",
    "empty-cell-color": "{color.neutral.400}"
  }
}
```

---

## Usage Guidelines

**Do:**
- Use tables for structured, comparable data with consistent columns.
- Include a caption or descriptive heading above the table for context.
- Enable sorting on columns where reordering adds value (alphabetical names, dates, amounts).
- Use the striped variant for tables with many rows to improve scan-ability.
- Provide horizontal scroll indicators (gradient shadow) when the table overflows on mobile.
- Use the stacked card layout on mobile for tables with fewer than 6 columns.

**Don't:**
- Use tables for layout purposes -- use CSS Grid or Flexbox.
- Sort every column by default; only add sorting where it serves a user need.
- Mix selectable and non-selectable rows within the same table.
- Hide critical data columns on mobile; prioritize or use the scroll strategy instead.
- Use tables for fewer than 3 rows; consider a definition list or key-value layout instead.
- Nest tables within tables; flatten the data structure or use expandable rows.

---

## Code Example

### HTML

```html
<!-- Basic sortable table with selection -->
<div class="ff-table-container" role="region" aria-label="Team members" tabindex="0">
  <table class="ff-table ff-table--striped ff-table--hoverable ff-table--md">
    <caption class="ff-sr-only">List of team members with roles and status</caption>
    <thead class="ff-table__head ff-table__head--sticky">
      <tr>
        <th class="ff-table__th ff-table__th--checkbox" scope="col">
          <input type="checkbox" class="ff-checkbox" aria-label="Select all rows" />
        </th>
        <th class="ff-table__th ff-table__th--sortable" scope="col"
            aria-sort="ascending">
          <button class="ff-table__sort-btn" aria-label="Sort by name ascending">
            Name
            <svg class="ff-table__sort-icon" aria-hidden="true"><!-- arrow --></svg>
          </button>
        </th>
        <th class="ff-table__th" scope="col">Role</th>
        <th class="ff-table__th" scope="col">Status</th>
        <th class="ff-table__th ff-table__th--action" scope="col">
          <span class="ff-sr-only">Actions</span>
        </th>
      </tr>
    </thead>
    <tbody class="ff-table__body">
      <tr class="ff-table__row">
        <td class="ff-table__td ff-table__td--checkbox">
          <input type="checkbox" class="ff-checkbox" aria-label="Select Jane Doe" />
        </td>
        <td class="ff-table__td">Jane Doe</td>
        <td class="ff-table__td">Designer</td>
        <td class="ff-table__td">
          <span class="ff-badge ff-badge--success">Active</span>
        </td>
        <td class="ff-table__td ff-table__td--action">
          <button class="ff-btn ff-btn--ghost ff-btn--sm" aria-label="Actions for Jane Doe">
            ...
          </button>
        </td>
      </tr>
    </tbody>
    <tfoot class="ff-table__foot">
      <tr>
        <td colspan="5" class="ff-table__pagination">
          <span class="ff-table__info">Showing 1-10 of 42</span>
          <nav class="ff-pagination" aria-label="Table pagination">
            <button class="ff-pagination__btn" disabled aria-label="Previous page">&lt;</button>
            <button class="ff-pagination__btn ff-pagination__btn--active" aria-current="page">1</button>
            <button class="ff-pagination__btn">2</button>
            <button class="ff-pagination__btn">3</button>
            <button class="ff-pagination__btn" aria-label="Next page">&gt;</button>
          </nav>
        </td>
      </tr>
    </tfoot>
  </table>
</div>
```

### JSX

```jsx
import { Table, TableHead, TableBody, TableFoot, TableRow, TableCell, Pagination } from '@flaviofusuma/ui';

<Table
  variant="striped"
  hoverable
  size="md"
  stickyHeader
  caption="List of team members with roles and status"
>
  <TableHead>
    <TableRow>
      <TableCell type="header" checkbox onSelectAll={handleSelectAll} />
      <TableCell type="header" sortable sortDirection="asc" onSort={handleSort}>
        Name
      </TableCell>
      <TableCell type="header">Role</TableCell>
      <TableCell type="header">Status</TableCell>
      <TableCell type="header" action />
    </TableRow>
  </TableHead>
  <TableBody>
    {data.map((row) => (
      <TableRow key={row.id} selected={selectedIds.includes(row.id)}>
        <TableCell checkbox checked={selectedIds.includes(row.id)}
                   onChange={() => handleSelect(row.id)}
                   aria-label={`Select ${row.name}`} />
        <TableCell>{row.name}</TableCell>
        <TableCell>{row.role}</TableCell>
        <TableCell>
          <Badge variant={row.status === 'Active' ? 'success' : 'neutral'}>
            {row.status}
          </Badge>
        </TableCell>
        <TableCell action>
          <ActionMenu items={[
            { label: 'Edit', onClick: () => handleEdit(row.id) },
            { label: 'Delete', onClick: () => handleDelete(row.id), danger: true },
          ]} />
        </TableCell>
      </TableRow>
    ))}
  </TableBody>
  <TableFoot>
    <Pagination
      total={42}
      pageSize={10}
      currentPage={page}
      onPageChange={setPage}
    />
  </TableFoot>
</Table>
```

---

## Related Components

- [Pagination](/02-design-system/05-components/pagination.md) -- Standalone pagination used in the table footer.
- [Checkbox](/02-design-system/05-components/checkbox.md) -- Used for row selection within selectable tables.
- [Badge](/02-design-system/05-components/tags.md) -- Status indicators within table cells.
- [Skeleton](/02-design-system/05-components/skeleton.md) -- Loading state placeholder for table rows.
- [Divider](/02-design-system/05-components/divider.md) -- Alternative lightweight separation for simpler data displays.
