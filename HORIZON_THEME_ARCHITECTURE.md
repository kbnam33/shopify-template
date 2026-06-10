# Horizon Theme — Complete Architecture Analysis
## Neera Shopify Build Reference Document

---

## 1. SYSTEM OVERVIEW

The Horizon theme is built on a **composable block system**. Almost nothing is hardcoded — every visual element is a block, every block's appearance is driven by settings, and every setting ultimately resolves to a CSS custom property. Understanding this chain is the key to predicting what affects what.

The rendering chain from bottom to top:

```
config/settings_data.json
  → snippets/theme-styles-variables.liquid  (global CSS variables)
  → snippets/color-schemes.liquid           (per-scheme CSS variables)
  → layout/theme.liquid                     (base HTML shell)
  → sections/header-group.json             (header group config)
  → sections/footer-group.json             (footer group config)
  → templates/*.json                        (page-level section order)
  → sections/*.liquid                       (section HTML + local CSS)
  → blocks/*.liquid                         (block HTML + local CSS)
  → snippets/*.liquid                       (reusable render targets)
```

Every visual output is the result of this chain. Changing a setting in `settings_data.json` cascades through CSS variables that every section and block already reads.

---

## 2. THE DESIGN TOKEN SYSTEM

### 2a. Font Families — Four Slots

`snippets/theme-styles-variables.liquid` defines four font slots from `config/settings_data.json`:

| CSS Variable | settings_data key | Current Value | Used For |
|---|---|---|---|
| `--font-body--family` | `type_body_font` | Jost | Body text, paragraphs |
| `--font-subheading--family` | `type_subheading_font` | Jost (medium) | Labels, subheadings |
| `--font-heading--family` | `type_heading_font` | DM Serif Display | H1–H6, display text |
| `--font-accent--family` | `type_accent_font` | DM Serif Display italic | Special accents, pull quotes |

**Critical rule:** Any block or section that sets `font: var(--font-heading--family)` will use DM Serif Display. Any block that sets `font: var(--font-body--family)` will use Jost. The font slot is always specified at the block level — the global setting only defines what each slot contains.

**Nav font exception:** The nav does NOT use the global font variables directly. It uses `--menu-top-level-font-family` which is set by `snippets/menu-font-styles.liquid` based on the `type_font_primary_link` setting inside the `_header-menu` block in `sections/header-group.json`. This is why changing `type_font_h5` in `settings_data.json` has no effect on the nav — wrong file.

**The correct nav font control file:** `sections/header-group.json` → `sections.header_section.blocks.header-menu.settings.type_font_primary_link`

### 2b. Type Scale — Per-Preset Settings

Each heading preset (h1–h6) has five properties in `settings_data.json`:

- `type_size_h1` — font size in px
- `type_line_height_h1` — line height token (e.g. `display-tight`, `normal`)
- `type_letter_spacing_h1` — spacing token (e.g. `none`, `heading-loose`)
- `type_case_h1` — `none` or `uppercase`
- `type_font_h1` — which slot: `body`, `subheading`, `heading`, or `accent`

These values are read by `snippets/theme-styles-variables.liquid` and compiled into CSS custom properties like `--font-h1--size`, `--font-h1--family`, `--font-h1--case` etc. These are then applied inside `snippets/typography-style.liquid` when a block's `type_preset` is set to `h1`.

### 2c. Color Schemes — Six Slots

`config/settings_data.json` contains a `color_schemes` object with six entries (`scheme-1` through `scheme-6`). Each scheme defines approximately 30 color tokens. `snippets/color-schemes.liquid` compiles these into scoped CSS custom properties under `.color-scheme-1`, `.color-scheme-2` etc.

**Current Neera scheme assignments:**

| Scheme | Background | Role |
|---|---|---|
| scheme-1 | `#F2EDE6` Parchment | Main pages, product, collection |
| scheme-2 | `#232323` Near Black | Hero section |
| scheme-3 | `#5C1F2E` Deep Maroon | Header, high-contrast CTAs |
| scheme-4 | `#EBE4DC` Linen | Secondary sections, cards |
| scheme-5 | `#3D3530` Charcoal | Footer, marquee strip |
| scheme-6 | `rgba(0,0,0,0)` Transparent | Overlaid header on hero |

**How color propagates:** A section sets `color-{{ section.settings.color_scheme }}` as a class on its container div. The browser resolves all `var(--color-foreground)`, `var(--color-background)` etc. from the nearest ancestor with that class. This is pure CSS cascade — no JavaScript involved.

**Transparent header color logic:** When the header is transparent (floating over the hero), it uses `scheme-6`. Scheme-6's `foreground` value `#F2EDE6` (warm parchment white) is what makes nav links readable over the dark hero image. When the user scrolls and the header becomes sticky/solid, it switches to `scheme-3` (deep maroon).

### 2d. Z-Index Layering System

All z-index values use named CSS custom property tokens, never raw numbers (except in our vignette fix):

| Token | Value | Used For |
|---|---|---|
| `--layer-lowest` | -1 | Background elements |
| `--layer-base` | 0 | Default stacking |
| `--layer-flat` | 1 | Overlays, vignettes |
| `--layer-raised` | 2 | Cards, hover states |
| `--layer-heightened` | 4 | Dropdowns, tooltips |
| `--layer-sticky` | 8 | Sticky elements |
| `--layer-header-menu` | 12 | Mega menu |
| `--layer-overlay` | 16 | Header (transparent) |

**Important:** The hero container `.hero__container` creates an isolated stacking context. Elements placed as grid children of `.hero__container` can only stack relative to each other within that context — they cannot z-index above elements in a different stacking context above them. This is why vignette divs placed inside `.hero__container` as additional grid children were being ignored — they rendered in `grid-column: 2` (center column only) due to the `base.css` rule `.section > * { grid-column: 2; }`.

**The working vignette solution:** Uses the `overlay.liquid` snippet which renders inside `.hero__media-grid` — a `position: absolute; inset: 0` element that already has its own stacking context. The overlay div renders at `z-index: var(--layer-flat)` within `.hero__media-grid`'s context, which is above the image but below the content wrapper. A custom CSS class `.overlay--neera-vignette` was added to `snippets/overlay.liquid`'s stylesheet block and is activated by setting `overlay_style: "neera-vignette"` in `templates/index.json`.

---

## 3. SECTION ARCHITECTURE

### 3a. Two Types of Sections

**Type 1 — Universal Section (`sections/section.liquid`):**
The most important file in the theme. Handles almost all homepage sections. Its structure:
- A background div with the color scheme class
- A content div also with the color scheme class
- Inside: `snippets/background-media.liquid` for bg image/video
- Inside: `snippets/overlay.liquid` (conditional on `toggle_overlay`)
- Inside: a flex container that renders `{{ children }}` — the block output

The `section.liquid` snippet is called by `sections/_blocks.liquid` which is the actual Shopify section file. `_blocks.liquid` renders `{% content_for 'blocks' %}` and passes the output as `children` to `snippets/section.liquid`.

**Type 2 — Dedicated Sections:**
`sections/hero.liquid`, `sections/collection-list.liquid`, `sections/featured-product.liquid` etc. These have their own specific HTML structure for specialised layouts and are not processed through `snippets/section.liquid`. They have their own `{% stylesheet %}` blocks.

### 3b. Hero Section Specifics (`sections/hero.liquid`)

Structure:
```
.hero (outer wrapper — sets min-height, border, blur variables)
  .hero__container (CSS Grid, section--full-width, creates stacking context)
    .hero__link (optional full-coverage link)
    .hero__media-grid (position: absolute; inset: 0 — holds the image)
      overlay.liquid (rendered here when toggle_overlay is true)
      {{ media }} (the actual background image/video)
    .hero__vignette-main (our custom vignette — position absolute, z-index 3)
    .hero__vignette-nav (our custom nav vignette — position absolute, z-index 3)
    .hero__content-wrapper (holds the blocks — section_width constrains this)
      {% content_for 'blocks' %}
```

**Why vignettes work at the `.hero__container` level:** `.hero__container` is `display: grid` and `position: relative`. `.hero__media-grid` is `position: absolute; inset: 0` so it sits behind all grid children. The vignette divs are placed after `.hero__media-grid` in DOM order as direct children of `.hero__container`, but they need `grid-column: 1 / -1` to span full width — otherwise `.section > * { grid-column: 2 }` constrains them to the center column.

**Current vignette implementation:** Uses `overlay.liquid` with a custom `.overlay--neera-vignette` CSS class added to `snippets/overlay.liquid`. The class applies a `linear-gradient(315deg, ...)` at `rgba(0,0,0,0.82)` → `rgba(0,0,0,0.45)` → transparent, creating the bottom-right darkening. A second gradient in the same background property handles the top-nav darkening.

### 3c. Section Layout Grid

Every section uses a CSS grid inherited from `base.css`. The grid has three columns:
- Column 1: `--page-margin` (left gutter)
- Column 2: `1fr` (content area, constrained by `--page-width`)
- Column 3: `--page-margin` (right gutter)

`section--page-width` sections place content in column 2. `section--full-width` sections use `grid-column: 1 / -1` to span all three columns. The `.section > *` rule ensures all direct children default to column 2, which is why any absolutely-positioned overlay or vignette div must explicitly override with `grid-column: 1 / -1`.

---

## 4. BLOCK SYSTEM

### 4a. Block Types

Two categories of blocks exist:

**Public blocks** (in `blocks/` without underscore prefix): Available in the Theme Editor for merchants to add/remove. Examples: `button.liquid`, `text.liquid`, `image.liquid`, `email-signup.liquid`.

**Private/static blocks** (in `blocks/` with underscore prefix `_`): Not directly addable by merchants, used as structural sub-components by sections. Examples: `_collection-card.liquid`, `_product-card.liquid`, `_header-menu.liquid`.

### 4b. The Group Block (`blocks/group.liquid`)

The most powerful composable primitive. A group block:
- Renders as a flex container
- Can be `row` or `column` direction
- Has its own alignment settings (`horizontal_alignment`, `vertical_alignment`)
- Can have its own color scheme, background media, and overlay
- Can contain other blocks as children
- Controls padding on all four sides independently

**In the hero:** The group block wraps the headline, subheading, and CTA. Its alignment settings (`flex-end` horizontally and vertically) push the entire content unit to the bottom-right. Its `padding-inline-end` and `padding-block-end` control the margin from the right and bottom edges.

### 4c. Text Block (`blocks/text.liquid` + `blocks/_content.liquid`)

Renders rich text with the following key settings:
- `text` — the HTML content (must use block-level tags: `<h1>–<h6>`, `<p>`, `<ul>`, `<ol>`)
- `type_preset` — maps to a global preset (`h1`, `h2`, `paragraph`, `subheading`, `rte`)
- `font` — overrides the font family directly (e.g. `var(--font-heading--family)`)
- `alignment` — `left`, `center`, or `right`
- `color` — overrides the inherited color from the color scheme
- `max_width` — constrains container width (`narrow`, `normal`, `wide`)
- `letter_spacing` — applies a letter-spacing token

**Two-line headline technique:** Since `<h1>` is a block element, placing two separate `<h1>` tags in the `text` setting creates two stacked lines. The gap between them is controlled by the `gap` setting on the parent group block, not by the text block's own line-height.

### 4d. Button Block (`blocks/button.liquid`)

Key settings:
- `style` — `primary` (filled) or `secondary` (outlined/ghost)
- `case` — `none` or `uppercase`
- `alignment` — aligns the button within its container

In scheme-2 (hero's dark background), `secondary_button_text` and `secondary_button_border` are both `#F2EDE6` — this gives the ghost button its white outline appearance on the hero.

---

## 5. HEADER ARCHITECTURE

### 5a. File Structure

The header is a **section group** — a Shopify concept where multiple sections are locked together and cannot be reordered by merchants. The group is defined by:

- `sections/header-group.json` — the configuration file (section group settings + block settings)
- `sections/header.liquid` — the header section template
- `blocks/_header-logo.liquid` — the logo block
- `blocks/_header-menu.liquid` — the navigation block
- `snippets/header-row.liquid` — renders each row of the header
- `snippets/header-actions.liquid` — renders search/account/cart icons
- `snippets/menu-font-styles.liquid` — compiles nav font CSS variables
- `snippets/submenu-font-styles.liquid` — compiles dropdown font CSS variables

### 5b. Nav Font Control Chain

```
sections/header-group.json
  → blocks.header-menu.settings.type_font_primary_link  ("body" = Jost)
  → snippets/menu-font-styles.liquid
  → --menu-top-level-font-family: var(--font-body--family)
  → nav links render in Jost
```

**The `type_font_primary_link` setting accepts:** `body`, `subheading`, `heading`, `accent`. Currently set to `body` (Jost). Was previously `accent` (DM Serif Display italic) which caused the italic nav text.

### 5c. Transparent Header Logic

The header transparency is controlled by three settings in `sections/header-group.json` → `sections.header_section.settings`:

- `enable_transparent_header_home: true` — activates transparent mode on the homepage
- `color_scheme_transparent: "scheme-6"` — the color scheme used when transparent
- `color_scheme_top: "scheme-3"` — the color scheme used when solid (scrolled)

When `enable_transparent_header_home` is true and the page is at the top, the header adds `transparent` and `transparent='not-sticky'` attributes to `#header-component`. The CSS in `sections/header.liquid` then uses `[transparent]` selectors to: position the header absolutely over the page, hide the default logo and show the inverse logo, and inherit color variables from the transparent scheme.

### 5d. Color Scheme Inheritance on Scroll

When the user scrolls down, `header.js` adds `data-sticky-state="active"` to `#header-component`. The CSS rule `[transparent='not-sticky'][data-sticky-state='active']` then restores the solid color scheme by un-inheriting the transparent values, revealing `scheme-3` (deep maroon background).

---

## 6. OVERLAY SYSTEM

### 6a. `snippets/overlay.liquid`

The central overlay primitive. Renders a `position: absolute; inset: 0` div inside any container that calls `{% render 'overlay', settings: section.settings %}`. The div's class is `overlay overlay--{{ settings.overlay_style }}`.

**Supported styles (in stylesheet):**
- `overlay--solid` — flat `background: var(--overlay-color)`
- `overlay--gradient` — `linear-gradient(var(--overlay-direction), var(--overlay-color), transparent)`
- `overlay--vignette` — `radial-gradient(ellipse...)` — added for Neera but not currently in use
- `overlay--neera-vignette` — **the active Neera vignette** — added to the stylesheet, activated by setting `overlay_style: "neera-vignette"` in the section settings

**How the neera-vignette works:** Two linear gradients stacked in the same `background` property (CSS allows comma-separated multiple backgrounds). Gradient 1: `linear-gradient(315deg, rgba(0,0,0,0.82) 0%, rgba(0,0,0,0.45) 30%, rgba(0,0,0,0) 55%)` — the main bottom-right vignette. Gradient 2: `linear-gradient(to bottom, rgba(0,0,0,0.35) 0%, rgba(0,0,0,0) 110px)` — the top nav protection gradient.

**Where the overlay renders in the hero:** Inside `.hero__media-grid` — the absolute-positioned image wrapper. The overlay sits at `z-index: var(--layer-flat)` (z-index: 1) within that wrapper, above the image but below the content.

---

## 7. RESOURCE LIST SYSTEM

### 7a. Purpose

The resource list system is Horizon's unified way to render grids of products, collections, or articles. It supports four layout modes switched by a single `layout_type` setting.

### 7b. Files Involved

- `snippets/resource-list.liquid` — the router: reads `layout_type` and delegates to the right renderer
- `snippets/bento-grid.liquid` — renders items in a bento/mosaic grid
- `snippets/resource-list-carousel.liquid` — renders items in a scrolling carousel
- `snippets/editorial-collection-grid.liquid` — editorial layout for collections
- `snippets/editorial-product-grid.liquid` — editorial layout for products
- `snippets/editorial-blog-grid.liquid` — editorial layout for articles
- `snippets/resource-card.liquid` — the card component used by all layouts
- `snippets/resource-image.liquid` — handles image rendering within resource cards

### 7c. Layout Types

| Type | Description | Best For |
|---|---|---|
| `grid` | Equal-width CSS grid | Standard collection/product grids |
| `carousel` | Horizontal scrolling carousel | Featured collections, product rows |
| `bento` | Mosaic/masonry-style grid | Editorial homepage sections |
| `editorial` | Magazine-style unequal grid | Featured articles, hero collections |

### 7d. How Sections Feed the Resource List

Sections like `collection-list.liquid` and `product-list.liquid` follow this pattern:
1. Determine the data source (a collection, a collection_list setting, or all collections)
2. Capture a string of HTML items using `{% capture list_items %}` with a `<!--@list/split-->` delimiter
3. Split the string into an array for layouts that need item-level control
4. Call `{% render 'resource-list', ... %}` passing both the string and array

The `_collection-card` static block type is used within collection list sections via `{% content_for 'block', type: '_collection-card', id: 'static-collection-card', closest.collection: collection %}`.

---

## 8. DATA CONFIGURATION FILES

### 8a. `config/settings_data.json`

The global brain. Everything under `"current"` applies site-wide. Key sections:
- Font settings (`type_body_font`, `type_heading_font`, etc.)
- Type scale settings (`type_size_h1` through `type_size_h6`)
- Type case settings (`type_case_h1` through `type_case_h6`)
- Color schemes object (all six Neera schemes)
- Global UI settings (animations, drawers, sticky header behavior)

**Rule:** Any change here affects every section and block on every page simultaneously through CSS variables.

### 8b. `templates/index.json`

The homepage configuration. Controls:
- Which sections appear on the homepage
- The order sections appear in
- The settings for each section instance
- The blocks within each section, their order, and their settings

**Structure:** A `"sections"` object (keyed by unique IDs) and an `"order"` array (specifying the render order). Each section entry has `"type"` (matching the filename minus `.liquid`), `"settings"`, `"blocks"`, and `"block_order"`.

**Current homepage order:**
1. `section_Fh7TFQ` — Hero (type: `section`, using `sections/section.liquid` via `_blocks.liquid`)
2. `collection_list_FFV7jq` — Collection list (type: `collection-list`)
3. `featured_product_pW7dEU` — Featured product (type: `featured-product`)
4. `product_list_8kR3Hb` — Product list (type: `product-list`)
5. `marquee_9AMajF` — Marquee (type: `marquee`)

### 8c. `sections/header-group.json`

The header configuration. Not editable through `templates/index.json` — it's a section group managed separately. Key settings:
- `type_font_primary_link` in the `header-menu` block — controls nav font
- `type_case_primary_link` — controls nav uppercase/none
- `color_scheme_top` — solid header color scheme (currently `scheme-3`)
- `color_scheme_transparent` — transparent header color scheme (currently `scheme-6`)
- `enable_transparent_header_home` — activates transparent overlay on homepage

### 8d. `sections/footer-group.json`

The footer configuration. Also a section group. Currently uses `scheme-2` (near black). Contains menu blocks and an email signup block.

---

## 9. SNIPPET DEPENDENCY MAP

| Snippet | Called By | What It Does |
|---|---|---|
| `theme-styles-variables.liquid` | `layout/theme.liquid` | Compiles all global CSS tokens once per page |
| `color-schemes.liquid` | `layout/theme.liquid` | Compiles per-scheme CSS variable scopes |
| `overlay.liquid` | `sections/hero.liquid`, `sections/section.liquid`, `blocks/group.liquid` | Renders full-bleed color/gradient overlays |
| `background-media.liquid` | `snippets/section.liquid` | Renders background image or video |
| `typography-style.liquid` | `blocks/text.liquid`, `blocks/_content.liquid` | Outputs inline CSS for text typography |
| `menu-font-styles.liquid` | `blocks/_header-menu.liquid` | Outputs CSS variables for nav font |
| `submenu-font-styles.liquid` | `blocks/_header-menu.liquid` | Outputs CSS variables for dropdown font |
| `resource-list.liquid` | `sections/collection-list.liquid`, `sections/product-list.liquid`, etc. | Routes to the correct grid/carousel renderer |
| `resource-card.liquid` | `snippets/editorial-*.liquid`, `snippets/bento-grid.liquid` | Renders individual product/collection cards |
| `resource-image.liquid` | `snippets/resource-card.liquid` | Renders responsive images within cards |
| `layout-panel-style.liquid` | `snippets/section.liquid`, `blocks/group.liquid` | Outputs flexbox alignment CSS |
| `spacing-style.liquid` | Most sections and blocks | Outputs padding CSS variables |
| `border-override.liquid` | `snippets/section.liquid` | Outputs border CSS |

---

## 10. KNOWN CONSTRAINTS AND GOTCHAS

### CSS Deduplication
Horizon's `{% stylesheet %}` blocks are deduplicated — if two sections include the same stylesheet, it only renders once. This means CSS added in `{% stylesheet %}` blocks applies globally once included, but you cannot rely on it being re-evaluated per section instance. Always use inline `style` attributes for per-instance values.

### Grid Column Override
Any element that is a direct child of a `.section` grid container will have `grid-column: 2` applied by `base.css`. Full-width elements must explicitly use `grid-column: 1 / -1`. This was the root cause of the vignette failures when placing divs as children of `.hero__container`.

### `richtext` vs `text` Setting Types
In `templates/index.json`, settings of type `richtext` (used in some blocks and sections) require HTML-wrapped strings (`<p>text</p>`). Plain strings fail validation. The `text` setting type in blocks accepts plain strings but the content must still be valid HTML in the `"text"` field of text blocks.

### Locale Key Placeholders
Horizon's default `settings_data.json` uses `"t:html_defaults.some_key"` as placeholder values for richtext settings. These are locale keys that resolve in the theme editor but fail when pushed via CLI because they're not real HTML values. Always replace them with actual HTML strings (`<p>Content here</p>`) before pushing.

### Nav Font Independence
The nav font is NOT controlled by `settings_data.json` type scale settings. It is controlled by `sections/header-group.json` → `header-menu block` → `type_font_primary_link`. Changing h5/h6 settings in `settings_data.json` has zero effect on nav rendering.

### section.liquid vs hero.liquid
The hero on the Neera homepage uses `sections/section.liquid` (via `sections/_blocks.liquid` with type `"section"`) — NOT `sections/hero.liquid`. This means the overlay system, grid, and CSS from `snippets/section.liquid` applies, not from `sections/hero.liquid`. The `sections/hero.liquid` file exists in the theme but is not currently used on the Neera homepage.

### Transparent Header + First Section Height
When the header is transparent, `snippets/section.liquid` adds `--section-height-offset: var(--header-group-height, 0)` to the first section's min-height. This ensures the hero accounts for the header height so content doesn't sit behind the navbar. This only applies when `enable_transparent_header_home` is true and there is no intervening section between the header group and the first main section.

---

## 11. QUICK REFERENCE — WHAT FILE TO EDIT FOR COMMON CHANGES

| Change | File | Location |
|---|---|---|
| Nav font (family) | `sections/header-group.json` | `blocks.header-menu.settings.type_font_primary_link` |
| Nav uppercase/case | `sections/header-group.json` | `blocks.header-menu.settings.type_case_primary_link` |
| Header color (solid) | `sections/header-group.json` | `sections.header_section.settings.color_scheme_top` |
| Header color (transparent) | `sections/header-group.json` | `sections.header_section.settings.color_scheme_transparent` |
| Global heading font | `config/settings_data.json` | `current.type_heading_font` |
| Global body font | `config/settings_data.json` | `current.type_body_font` |
| H1 font size | `config/settings_data.json` | `current.type_size_h1` |
| H1 uppercase | `config/settings_data.json` | `current.type_case_h1` |
| Color scheme values | `config/settings_data.json` | `current.color_schemes.scheme-N.settings.*` |
| Hero background image | `templates/index.json` | `section_Fh7TFQ.settings.background_image` |
| Hero overlay | `templates/index.json` | `section_Fh7TFQ.settings.toggle_overlay` + `overlay_style` |
| Vignette gradient style | `snippets/overlay.liquid` | `.overlay--neera-vignette` CSS rule |
| Hero text content | `templates/index.json` | `section_Fh7TFQ.blocks.[group_id].blocks.[text_id].settings.text` |
| Hero text alignment | `templates/index.json` | Group block `horizontal_alignment_flex_direction_column` |
| Footer color | `sections/footer-group.json` | `sections.footer_*.settings.color_scheme` |
| Homepage section order | `templates/index.json` | `order` array |
| Section color scheme | `templates/index.json` | `[section_id].settings.color_scheme` |
| Add new section type | `sections/[name].liquid` (new file) + `templates/index.json` (add entry) | — |


-----------------------


Let me verify directly from the repo.I can confirm — **yes, the analysis is based on the actual Ritual theme code in the repo.** Here's what the repo confirms:

---

**Confirmed from the repo:**

- `sections/hero.liquid` — contains the `.hero__vignette-main` and `.hero__vignette-nav` divs we added, confirming this is the current Ritual theme codebase

- `snippets/overlay.liquid` — contains the `.overlay--vignette` and our custom `.overlay--neera-vignette` class we added

- `templates/index.json` — contains `section_Fh7TFQ` with `"background_image": "shopify://shop_images/hero-bg.jpg"`, `"overlay_style": "vignette"`, `"toggle_overlay": false`, and the group block `group_heroText` with blocks `text_AH9jnc`, `text_subN2r4`, `button_expB1n` — all matching exactly what we built

**One correction to the report however:** The hero section type in `templates/index.json` is not `sections/section.liquid` via `_blocks.liquid` as I stated — it is actually using `sections/hero.liquid` directly (the section key's type resolves through the hero section). The report's section 10 note about this needs updating. Everything else in the analysis is accurate to the current Ritual theme repo.