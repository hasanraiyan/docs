# Source: https://coursify.hasanraiyan.me/research/css-flexbox-cheat-sheet-the-complete-reference-guide

CSS Flexbox Cheat Sheet: The Complete Reference Guide

# 

CSS Flexbox Cheat Sheet: The Complete Reference Guide

Verified Sources

Jun 16, 2026

## AI Summary

CSS Flexbox (Flexible Box Layout) is a one-dimensional layout model that provides efficient distribution of space among items in a container, even when their sizes are dynamic or unknown. Unlike traditional block or inline layouts, Flexbox operates along a single axis at a time — either a main axis or a cross axis.

Every Flexbox layout is built around two entities:

- **Flex Container** — the parent element with `display: flex`
- **Flex Items** — the direct children of that container

The core mental model: `flex-direction` defines which axis is the _main_ axis. All alignment properties (`justify-content`, `align-items`, `align-content`) are relative to these axes, not to "horizontal" or "vertical" in the screen sense.

Understanding this hierarchy is essential: container properties control _how groups of items_ are distributed, while item properties control _how individual items_ behave within that distribution.

## Footnotes

1. [Basic concepts of flexbox - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts) - Foundational MDN reference on flex container and flex item concepts. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [A Complete Guide to Flexbox - CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox) - Comprehensive visual guide to all Flexbox properties and values. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 

#### Learn CSS Flexbox in 20 Minutes

## The Two Axes — The Key to Understanding Flexbox

Before memorizing any property values, internalize this: **Flexbox properties don't think in "horizontal" or "vertical." They think in "main axis" and "cross axis."** Changing `flex-direction` swaps what these axes represent.

| `flex-direction` | Main Axis | Cross Axis |
| --- | --- | --- |
| `row` (default) | Left → Right | Top → Bottom |
| `row-reverse` | Right → Left | Top → Bottom |
| `column` | Top → Bottom | Left → Right |
| `column-reverse` | Bottom → Top | Left → Right |

- `justify-content` **always** distributes along the **main axis**
- `align-items` and `align-content` **always** distribute along the **cross axis**

## Footnotes

1. [CSS Flexbox Explained - freeCodeCamp](https://www.freecodecamp.org/news/css-flexbox-complete-guide) - Detailed guide covering container vs item property distinctions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

### 

Flexbox Property Distribution: Container vs Item

Number of properties applied to the container versus the item

## Flex Container Properties — Complete Reference

The following properties are applied to the **parent flex container** (the element with `display: flex`).

### 1\. `display`

`1.container { 2  display: flex;        /* block-level flex container */ 3  display: inline-flex; /* inline-level flex container */ 4}`

This is the gateway — it establishes a flex formatting context for all direct children.

### 2\. `flex-direction`

Defines the main axis direction:

| Value | Direction | Start → End |
| --- | --- | --- |
| `row` | Horizontal (default) | Left → Right |
| `row-reverse` | Horizontal reversed | Right → Left |
| `column` | Vertical | Top → Bottom |
| `column-reverse` | Vertical reversed | Bottom → Top |

### 3\. `flex-wrap`

Controls whether items wrap onto multiple lines:

| Value | Behavior |
| --- | --- |
| `nowrap` (default) | All items on one line (may shrink or overflow) |
| `wrap` | Items wrap onto new lines |
| `wrap-reverse` | Items wrap in reverse order |

### 4\. `flex-flow` (Shorthand)

`1.container { 2  flex-flow: <direction> <wrap>;  /* e.g., flex-flow: row wrap; */ 3}`

### 5\. `justify-content` — Main Axis Distribution

Distributes **extra free space** along the main axis:

| Value | Space Distribution |
| --- | --- |
| `flex-start` | Items packed to start |
| `flex-end` | Items packed to end |
| `center` | Items centered |
| `space-between` | First at start, last at end, equal space between |
| `space-around` | Equal space around each item (edges = half) |
| `space-evenly` | Equal space between and at edges |

### 6\. `align-items` — Cross Axis Alignment (Single Line)

Controls how each item aligns on the cross axis:

| Value | Behavior |
| --- | --- |
| `stretch` (default) | Stretch to fill container |
| `flex-start` | Align to cross-start |
| `flex-end` | Align to cross-end |
| `center` | Center on cross axis |
| `baseline` | Align to text baseline |

### 7\. `align-content` — Cross Axis Distribution (Multiple Lines)

Controls how **lines of items** are distributed when there is extra space on the cross axis. **Only works with `flex-wrap: wrap` and multiple lines**:

| Value | Behavior |
| --- | --- |
| `stretch` (default) | Lines stretch to fill space |
| `flex-start` | Lines packed to start |
| `flex-end` | Lines packed to end |
| `center` | Lines centered |
| `space-between` | Equal space between lines |
| `space-around` | Equal space around each line |

### 8\. `gap`

`1.container { 2  gap: 10px;              /* row-gap and column-gap */ 3  gap: 10px 20px;         /* row-gap column-gap */ 4  row-gap: 10px; 5  column-gap: 20px; 6}`

The `gap` property explicitly controls spacing between items without using margins.

## Footnotes

1. [Flex It Like a Pro - DEV Community](https://dev.to/codebyshreya/flex-it-like-a-pro-a-beginners-guide-to-css-flexbox-4m5m) - Beginner-friendly breakdown of all Flexbox properties. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [CSS Flex Property & Layout Guide - Elementor](https://elementor.com/blog/flex-css) - Complete guide covering main axis vs cross axis concepts. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
3. [FLEX: Visual Cheatsheet - Malven](https://flexbox.malven.co) - Visual cheat sheet for all Flexbox property values. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6)
 
4. [Aligning items in a flex container - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items) - MDN deep dive into Flexbox alignment properties. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 
5. [Everything You Need To Know About Alignment In Flexbox - Smashing Magazine](https://www.smashingmagazine.com/2018/08/flexbox-alignment) - Advanced article on fallback alignment and auto margins. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-8)
 
6. [Common CSS Flexbox Layout Patterns - Tobias Ahlin](https://tobiasahlin.com/blog/common-flexbox-patterns) - 10 practical layout patterns with copy-paste CSS. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9)
 

#### align-content vs align-items

A common mistake: `align-content` has **no effect** on a single-line flex container. It only distributes space **between lines** when `flex-wrap: wrap` is active and there are multiple rows. For single-line alignment, use `align-items`. If you set `align-content` on a non-wrapping container, nothing visible happens.

more...

Container Properties

Item Properties

`1    /* All flex container properties at a glance */ 2    .container { 3      display: flex;               /* or inline-flex */ 4      flex-direction: row;         /* row | row-reverse | column | column-reverse */ 5      flex-wrap: nowrap;           /* nowrap | wrap | wrap-reverse */ 6      flex-flow: row nowrap;       /* shorthand: direction + wrap */ 7      justify-content: flex-start; /* flex-start | flex-end | center | space-between | space-around | space-evenly */ 8      align-items: stretch;        /* stretch | flex-start | flex-end | center | baseline */ 9      align-content: stretch;      /* stretch | flex-start | flex-end | center | space-between | space-around */ 10      gap: 0px;                    /* row-gap column-gap */ 11    }`

## Flex Item Properties — Complete Reference

These properties are applied to **individual flex items** (the direct children of the container).

### 1\. `order`

`1.item { order: <integer>; }  /* default: 0 */`

Controls the visual order of items. Items with the same `order` value revert to source order. Negative values are allowed.

### 2\. `flex-grow`

`1.item { flex-grow: <number>; }  /* default: 0 */`

Defines the grow factor. If all items have `flex-grow: 1`, remaining space is distributed equally. An item with `flex-grow: 2` would take twice as much space as one with `flex-grow: 1`.

### 3\. `flex-shrink`

`1.item { flex-shrink: <number>; }  /* default: 1 */`

Defines the shrink factor. Items with a higher value shrink more. `flex-shrink: 0` prevents an item from shrinking.

### 4\. `flex-basis`

`1.item { flex-basis: <length> | auto | content; }  /* default: auto */`

Sets the **initial main size** of an item before free space distribution. It overrides `width`/`height` for flex items.

### 5\. `flex` (Shorthand) ⭐

`1.item { 2  flex: none;          /* → 0 0 auto */ 3  flex: auto;          /* → 1 1 auto */ 4  flex: initial;       /* → 0 1 auto */ 5  flex: 1;             /* → 1 1 0% */ 6  flex: 2 1;           /* → 2 1 0% */ 7  flex: 1 1 200px;     /* → grow=1 shrink=1 basis=200px */ 8}`

This is the **recommended** way to set flex sizing — the CSS specification strongly advises using the shorthand over individual properties.

### 6\. `align-self`

`1.item { align-self: auto | flex-start | flex-end | center | baseline | stretch; }`

Overrides `align-items` for a **single item**, allowing it to have a different cross-axis alignment than its siblings.

## Footnotes

1. [Understanding Flexbox - Medium/freeCodeCamp](https://medium.com/free-code-camp/understanding-flexbox-everything-you-need-to-know-b4013d4dc9af) - Deep walkthrough of flex item properties including nested containers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-10)
 
2. [flex CSS property - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/flex) - Specification detail on the flex shorthand and its expansion rules. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-11)
 

#### The Most Common Flex Shorthand Patterns

Memorize these three `flex` shorthand values and you'll cover 90% of use cases:

• `flex: 0 1 auto` (default) — item doesn't grow but shrinks if needed • `flex: 1` — item grows to fill available space equally (shorthand for `1 1 0%`) • `flex: none` — item is inflexible: keeps its size (shorthand for `0 0 auto`)

more...

### How Flex Distributes Space (Algorithm)

1. 1
 
 Step 1
 
 Establish the container
 
 Set `display: flex` on the parent element. This creates a flex formatting context — all **direct children** become flex items.
 
2. 2
 
 Step 2
 
 Determine the main axis
 
 The `flex-direction` property sets the main axis. Default is `row` (horizontal, left-to-right). This determines which direction `justify-content` and `align-items` operate on.
 
3. 3
 
 Step 3
 
 Calculate each item's hypothetical size
 
 Each item's starting size comes from `flex-basis`. If `flex-basis: auto`, the item uses its `width`/`height` or content size. Items are then laid out along the main axis.
 
4. 4
 
 Step 4
 
 Check for available space
 
 Subtract total item sizes from the container size.
 
 • **Positive free space** → distribute using `flex-grow` • **Negative free space** → resolve using `flex-shrink`
 
5. 5
 
 Step 5
 
 Distribute positive space (flex-grow)
 
 If there's extra space, each item receives a share proportional to its `flex-grow` value. Total extra space is divided by the sum of all grow factors. An item with `flex-grow: 2` gets twice as much as one with `flex-grow: 1`.
 
6. 6
 
 Step 6
 
 Resolve negative space (flex-shrink)
 
 If items overflow, each item shrinks proportionally to its `flex-shrink` value × its `flex-basis`. This is a weighted shrink — larger items give up more space. Items with `flex-shrink: 0` refuse to shrink.
 
7. 7
 
 Step 7
 
 Apply alignment properties
 
 After sizing, `justify-content` distributes remaining main-axis space, and `align-items`/`align-self` positions items on the cross axis. If the container has multiple wrapped lines, `align-content` distributes space between those lines.
 
8. 8
 
 Step 8
 
 Final rendering
 
 The browser renders each item at its computed size and position. Note: `float`, `clear`, and `vertical-align` have **no effect** on flex items.
 
 ## Footnotes
 
 1. [A Complete CSS Flexbox Layout Guide - CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox) - Notes on float, clear, and vertical-align having no effect on flex items. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-12)
 
 

### 

Flexbox Spec Evolution

#### Initial Working Draft

2009

First W3C Working Draft published with an early syntax using `display: box`. Browser implementations used vendor prefixes like `-webkit-box`."

#### Candidate Recommendation

2012

Major syntax overhaul: `display: flexbox` replaced with `display: flex`. `flex-order` became `order`, `box-flex` became `flex`. This is closer to the modern syntax."

#### W3C Candidate Recommendation (Stable)

2015

Property names finalized as we know them today. `flex-grow`, `flex-shrink`, `flex-basis`, and the `flex` shorthand are standardized. `gap` not yet included."

#### Browser Adoption Peak

2016-2018

All major browsers ship unprefixed Flexbox support. The `gap` property is later added for Flexbox (initially Grid-only). IE11 remains the last holdout with known bugs."

#### Modern Flexbox + gap

2020+

The `gap` property is supported in Flexbox across all modern browsers. Flexbox becomes the default layout model for component architectures (React, Vue, etc.). IE11 drops off support lists."

### 

justify-content Values: Space Distribution Comparison

How each value distributes space (higher = more space at edges)

## Common Flexbox Layout Patterns

Here are the most frequently used layout patterns with ready-to-use code[2]().

### 1\. Perfect Centering

`1.container { 2  display: flex; 3  justify-content: center;  /* main axis center */ 4  align-items: center;       /* cross axis center */ 5}`

The most iconic Flexbox pattern — centers an item both horizontally and vertically without knowing its size.

### 2\. Navbar with Pushed-Right Item

`1.navbar { 2  display: flex; 3  /* no justify-content needed — items flow from start */ 4} 5.navbar .push-right { 6  margin-left: auto;  /* absorbs all left-side space */ 7}`

Using `margin-left: auto` on a flex item pushes it to the end — this works because `auto` margins absorb all available free space on that side.

### 3\. Holy Grail Layout (Sidebar + Main + Sidebar)

`1.layout { 2  display: flex; 3  flex-wrap: wrap; 4} 5.sidebar-left  { flex: 0 0 200px; } 6.main-content  { flex: 1; }         /* grows to fill remaining space */ 7.sidebar-right { flex: 0 0 200px; }`

### 4\. Responsive Card Grid (with gap)

`1.card-grid { 2  display: flex; 3  flex-wrap: wrap; 4  gap: 16px; 5} 6.card { 7  flex: 1 1 280px; /* grow, shrink, min 280px */ 8}`

Items grow to fill space, shrink when needed, but never go below 280px — at which point they wrap to the next line.

### 5\. Sticky Footer

`1.page { 2  display: flex; 3  flex-direction: column; 4  min-height: 100vh; 5} 6.content { 7  flex: 1;  /* grows to push footer down */ 8}`

### Space Distribution Visual Guide

## Footnotes

1. [Mastering CSS Flexbox - Williams Media](https://williamsmedia.co/css-flexbox-layouts) - Responsive card layout and common Flexbox patterns. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-13)
 
2. [Common CSS Flexbox Layout Patterns - Tobias Ahlin](https://tobiasahlin.com/blog/common-flexbox-patterns) - Graph patterns, grids, and alternating layouts with Flexbox. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-14)
 
3. [Everything You Need To Know About Alignment In Flexbox - Smashing Magazine](https://www.smashingmagazine.com/2018/08/flexbox-alignment) - Detailed explanation of auto margin behavior and priority over justify-content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-15)
 

### Flexbox FAQ & Edge Cases

What's the difference between space-around and space-evenly?

Why isn't align-content working?

Can I use flex-grow with flex-basis: 0 vs auto?

What happens when justify-content and margin: auto conflict?

Does Flexbox replace CSS Grid?

Why do my flex items overflow?

#### The min-width: auto Trap

Flex items have a default `min-width: auto`, which means they **won't shrink below their content size**. This causes unexpected overflow in containers like `overflow: hidden` text containers. Fix it with `min-width: 0` on the flex item or set `overflow: hidden` + `text-overflow: ellipsis`.

more...

## Quick Reference: The `flex` Shorthand Value Decoder

The `flex` shorthand is the most important property for item sizing. Here's a decoder for the most common patterns:

| Shorthand | Expands To | Meaning |
| --- | --- | --- |
| `flex: initial` | `flex: 0 1 auto` | No grow, can shrink, sized by width/height |
| `flex: auto` | `flex: 1 1 auto` | Can grow **and** shrink, sized by width/height |
| `flex: none` | `flex: 0 0 auto` | Fully inflexible: keeps its size |
| `flex: 1` | `flex: 1 1 0%` | Grows equally, shrinks, starts from zero |
| `flex: 2` | `flex: 2 1 0%` | Grows 2× more than `flex: 1` siblings |

The formula for distributing extra space:

Item size\=flex-basis+flex-growi∑flex-grow×free space\\text{Item size} = \\text{flex-basis} + \\frac{\\text{flex-grow}\_i}{\\sum \\text{flex-grow}} \\times \\text{free space}Item size\=flex-basis+∑flex-growflex-growi​​×free space

And for shrinking when there's overflow:

Shrink amounti\=flex-shrinki×flex-basisi∑(flex-shrink×flex-basis)×overflow\\text{Shrink amount}\_i = \\frac{\\text{flex-shrink}\_i \\times \\text{flex-basis}\_i}{\\sum (\\text{flex-shrink} \\times \\text{flex-basis})} \\times \\text{overflow}Shrink amounti​\=∑(flex-shrink×flex-basis)flex-shrinki​×flex-basisi​​×overflow

### 

flex-basis Comparison: 0% vs auto

Final item sizes when three items have different content sizes

### Knowledge Check

Question 1 of 5

Q1Single choice

Which property controls the distribution of space along the main axis in a flex container?

align-items

justify-content

flex-direction

align-content

BackNext

## Explore Related Topics

[1\\ \\ Node.js Roadmap 2026: The Complete Developer's Guide\\ \\ Node.js 2026 marks a “native‑first” shift, with Node 26 delivering built‑in TypeScript, the Temporal API, a permission model, V8 14.6 language upgrades, and a hybrid runtime strategy alongside Bun.\\ \\ - Node 26’s flagship features: default Temporal API, native TypeScript type‑stripping, permission flags, Map `getOrInsert`, `Iterator.concat`, Undici 8, and experimental `node:ffi`. - Benchmarks show Bun out‑performs Node on raw throughput, but Node retains the deepest npm ecosystem; enterprises adopt Bun for tooling and Node for production stability. - Migration checklist: audit/removing replaced packages, convert to ESM, enable permission model, switch to `node:test`, replace `Date` with Temporal, rebuild native addons for NODE\_MODULE\_VERSION 147. - 2026‑essential developer skills: ESM + modern JavaScript, TypeScript, Fastify/Nest, observability (OpenTelemetry, structured logging), security (Permission Model), edge/serverless, worker threads, WASM, and Temporal.](https://coursify.hasanraiyan.me/research/nodejs-roadmap-2026-the-complete-developers-guide) [2\\ \\ React Hooks Deep Dive\\ \\ React Hooks, introduced in React 16.8, fundamentally transformed how developers write React applications by allowing functional components to manage state and side effects. Prior to Hooks, complex logic and lifecycle management were confined to class components, often leading to convoluted code, dee](https://coursify.hasanraiyan.me/research/react-hooks-deep-dive) [3\\ \\ Advanced CSS Layouts\\ \\ Advanced CSS layouts combine Grid, Flexbox, subgrid, container queries, and intrinsic sizing to create modular, responsive, and stable designs.\\ \\ - Grid defines two‑dimensional page structure; Flexbox handles one‑dimensional alignment inside components. - Subgrid allows nested grids to inherit parent tracks, solving alignment inconsistencies across cards and sections. - Container queries make components adapt to their own container size, enabling true component‑level responsiveness. - Fluid patterns such as `repeat(auto‑fit, minmax(...))`, `fr`, `minmax()`, and `clamp()` replace fixed breakpoints for resilient layouts. - Intrinsic sizing tools like `aspect‑ratio` preserve media space and reduce layout shift.](https://coursify.hasanraiyan.me/research/advanced-css-layouts)

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)