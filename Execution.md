## TECHNICAL INSTRUCTIONS — Font Replacement & Remove Unused Sections

---

## PART 1 — FONT REPLACEMENT

### TARGET FILE: `config/settings_data.json`
### TARGET OBJECT: `"current"` at root level

**The problem:** `dm_serif_display_n4` is rendering as a heavy, condensed display serif that reads more like Times New Roman at small sizes and becomes overpowering at large display sizes. The brand needs a refined editorial serif with elegant proportions — warmer, more legible, less newspaper-like.

**Recommended replacement:** `cormorant_garamond_n4` for headings and accent — this is a high-contrast elegant serif widely used by premium fashion and textile brands. It has the same display quality but with better proportions, a softer character, and reads as genuinely luxurious rather than archival.

---

### INSTRUCTION 1 — Heading Font

Within the `"current"` object, find the key `"type_heading_font"`. Change its value from `"dm_serif_display_n4"` to `"cormorant_garamond_n6"`. The `n6` weight gives it the bold presence needed for hero headlines without appearing heavy.

---

### INSTRUCTION 2 — Accent Font

Within the `"current"` object, find the key `"type_accent_font"`. Change its value from `"dm_serif_display_i4"` to `"cormorant_garamond_i4"`. The `i4` is the italic variant — used for eyebrow labels and decorative text.

---

### INSTRUCTION 3 — Body Font Size

Within the `"current"` object, find the key `"type_size_paragraph"`. Change its value from `"14"` to `"15"`. Jost at 14px is slightly tight for body copy on a fashion brand — 15px improves reading comfort without breaking the layout rhythm.

---

## PART 2 — REMOVE UNUSED SECTIONS

### TARGET FILE: `templates/index.json`

Looking at the screenshots, the following sections are rendering with placeholder content (Shopify's default illustration placeholders — the illustrated clothing hangers, the t-shirt graphic, the "SHOP NOW" ticker bar, and the "Demo Store" footer wordmark). These sections have no real content assigned and should be removed entirely from the homepage.

---

### INSTRUCTION 4 — Remove Collection List (placeholder illustrations row)

In the `"sections"` object, find and delete the entire entry with key `"collection_list_FFV7jq"` (type `"collection-list"` — the one showing 6 placeholder collection cards with illustrated garments on hangers). Also remove its key from the `"order"` array.

---

### INSTRUCTION 5 — Remove Featured Product (illustrated t-shirt section)

In the `"sections"` object, find and delete the entire entry with key `"featured_product_pW7dEU"` (type `"featured-product"` — the one showing the placeholder illustrated t-shirt on a warm beige background alongside the fabric illustration). Also remove its key from the `"order"` array.

---

### INSTRUCTION 6 — Remove Second Collection List (bottom placeholder grid)

In the `"sections"` object, find and delete the entire entry with key `"collection_list_iAQiBH"` (type `"collection-list"` — the second collection list visible lower on the page). Also remove its key from the `"order"` array.

---

### INSTRUCTION 7 — Verify the Final Order Array

After removals, the `"order"` array in `templates/index.json` should contain only these keys in this sequence:

`"section_Fh7TFQ"` (hero) → `"media_linen"` → `"media_mulmul"` → the featured collection section key showing "The Edit".

Confirm no other section keys remain in the array beyond these four.

---

## PUSH AFTER ALL CHANGES

Push both `config/settings_data.json` and `templates/index.json` to theme `188273557786` on store `x9iqze-nb.myshopify.com`.