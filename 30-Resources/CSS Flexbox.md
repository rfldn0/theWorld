---
title: "CSS Flexbox"
date: 2026-06-25
tags: [css, flexbox, frontend, web-development]
status: evergreen
source: "Full Stack Webdevelopment vault + Grimoire vault"
related: []
---

## Summary
Flexbox is a one-dimensional CSS layout model for arranging items in a row or column. The container controls alignment and spacing; children control their own sizing behavior.

## Main Content

### Container Properties

| Property | Values | Effect |
|----------|--------|--------|
| `display` | `flex` | Activates flex context |
| `flex-direction` | `row` \| `column` \| `row-reverse` \| `column-reverse` | Main axis direction |
| `flex-wrap` | `nowrap` \| `wrap` \| `wrap-reverse` | Whether items wrap |
| `justify-content` | `flex-start` \| `flex-end` \| `center` \| `space-between` \| `space-around` \| `space-evenly` | Main axis alignment |
| `align-items` | `stretch` \| `flex-start` \| `flex-end` \| `center` \| `baseline` | Cross axis alignment (single line) |
| `align-content` | same as justify-content | Cross axis alignment (multi-line) |
| `gap` | `<length>` | Space between items |

### Child Properties

| Property | Values | Effect |
|----------|--------|--------|
| `order` | integer (default: 0) | Visual order without changing HTML |
| `flex-grow` | number (default: 0) | How much extra space to absorb |
| `flex-shrink` | number (default: 1) | How much to shrink when space is tight |
| `flex-basis` | `auto` \| length | Initial size before grow/shrink |
| `flex` | shorthand for grow shrink basis | e.g. `flex: 1` = `1 1 0%` |
| `align-self` | same as align-items | Override container alignment per item |

### Sizing Patterns

```css
/* Equal columns that fill container */
.item { flex: 1; }

/* Fixed + flexible */
.sidebar { flex: 0 0 250px; }
.main { flex: 1; }

/* Minimum size, then grow */
.item { flex: 1 1 200px; }
```

### Axis Reference
- **Main axis** — direction of `flex-direction`
- **Cross axis** — perpendicular to main axis
- `justify-content` always controls main axis
- `align-items` / `align-content` always control cross axis

## Key Insights
- `flex: 1` is shorthand for `flex-grow: 1; flex-shrink: 1; flex-basis: 0%` — items share space equally
- `align-items` works on a single line; `align-content` works when items wrap to multiple lines
- `order` changes visual position only — tab order and DOM order stay the same
- `flex-basis: auto` uses the item's content size as starting point; `flex-basis: 0` ignores content size

## Questions / Open Threads
- [ ] How does flexbox interact with CSS Grid in nested layouts?
- [ ] Practice: Flexbox Froggy (https://flexboxfroggy.com)

## Related
- [[CSS Grid]] — two-dimensional alternative to Flexbox
