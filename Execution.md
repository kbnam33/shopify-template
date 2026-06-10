# TECHNICAL PLAN — Hero Design Refinement

## TASK 1 — `config/settings_data.json` — Switch heading font to DM Serif Display

Inside the `"current"` object, change `"type_heading_font"` from `"cormorant_n4"` to `"dm_serif_display_n4"`.

Change `"type_accent_font"` from `"cormorant_i4"` to `"dm_serif_display_i4"`.

This is the only font change — body and nav remain Jost.

---

## TASK 2 — `config/settings_data.json` — Set the full type scale for the hero

Inside the `"current"` object, set the following heading scale values:

Set `"type_size_h1"` to `"72"` — DM Serif Display at 72px reads as a strong editorial statement without feeling like a shout. Cormorant needed to be pulled back; DM Serif can carry 72.

Set `"type_line_height_h1"` to `"display-tight"` — keeps the two lines of the headline close together as a single unit.

Set `"type_letter_spacing_h1"` to `"none"` — DM Serif Display has natural elegant spacing, no tracking needed.

Set `"type_case_h1"` to `"none"` — sentence case, consistent with Neera's brand voice (never shouts).

Set `"type_size_h2"` to `"52"`.

Set `"type_size_h3"` to `"36"`.

Set `"type_size_h4"` to `"24"`.

For nav (h6 preset): set `"type_size_h6"` to `"11"`, `"type_case_h6"` to `"uppercase"`, `"type_letter_spacing_h6"` to `"heading-loose"`, `"type_font_h6"` to `"body"`.

---

## TASK 3 — `templates/index.json` — Hero headline forced two-line break

Inside `section_Fh7TFQ`, inside the group block, find the headline text block. Its `"text"` value currently contains the full sentence in a single h1 tag on one line.

Change the `"text"` value so that "Wear what" is on the first line and "the day demands." is on the second line — achieved by closing the first h1 tag after "Wear what" and opening a second h1 tag for "the day demands." This produces two separate block-level elements that stack vertically, creating the natural two-line visual break seen in the reference.

Change the headline block's `"max_width"` to `"narrow"` and `"width"` to `"fit-content"` — this constrains the container so the lines don't stretch beyond the natural length of the text.

Change the headline block's `"type_preset"` to `"h1"` — confirm this is set correctly.

---

## TASK 4 — `templates/index.json` — Hero content group positioning

Inside the group block wrapping all hero content, update the padding settings:

Set `"padding-inline-end"` to `64` — pushes the text block away from the right edge, giving it breathing room.

Set `"padding-block-end"` to `72` — lifts the text block up from the very bottom edge.

Set `"gap"` inside the group to `12` — tightens the vertical space between headline, subheading, and CTA so they read as one cohesive unit rather than three separate items.

---

## TASK 5 — `templates/index.json` — Subheading refinement

Inside the subheading text block within the group:

Set `"type_preset"` to `"subheading"` — renders at a slightly larger and more intentional size than paragraph.

Set `"letter_spacing"` to `"heading-loose"` — gives the subheading the tracked quality that separates it visually from the headline.

Set `"color"` to `"#C8B89A"` — the warm sand tone, quieter than the headline's pure white, creating a clear hierarchy between the two lines.

Set `"padding-block-start"` to `8` — adds a small breath between the headline and subheading.

---

## TASK 6 — `templates/index.json` — CTA button refinement

Inside the button block within the group:

Set `"style"` to `"secondary"` — renders as an outlined/ghost button, which is more refined than a filled button on a dark hero.

Set `"case"` to `"uppercase"`.

Set `"padding-block-start"` to `16` — separates the button from the subheading with intentional space.

Confirm `"text"` is `"Explore the collection"` and `"link"` is `"/collections/all"`.

---

## Push both files after all changes:

Push `config/settings_data.json` and `templates/index.json` to theme `188273557786` on store `x9iqze-nb.myshopify.com`.


------------------------------

# TECHNICAL PLAN — Hero Typography Fixes

## TASK 1 — `templates/index.json` — Reduce headline line gap

Inside `section_Fh7TFQ`, inside the group block, find the headline text block. The two-line break is currently implemented as two separate h1 tags stacked vertically. The gap between them is being driven by the `"gap"` setting on the group block, not by line-height.

Inside the group block's `"settings"`, change `"gap"` from its current value to `4` — this tightens the space between all three elements (headline line 1, headline line 2, subheading, button) to a minimal value so the two headline lines read as one unit.

Then on the headline text blocks themselves, set `"padding-block-start"` and `"padding-block-end"` to `0` on both — ensuring no block-level padding is adding to the visual gap between the two lines.

---

## TASK 2 — `config/settings_data.json` — Fix nav font

The nav is picking up DM Serif Display because the header in Horizon uses either `h5` or `h6` preset for nav links, and the h5/h6 preset is currently mapped to the heading font family.

Inside the `"current"` object, make these changes:

Set `"type_font_h5"` to `"body"` — forces h5 preset to use Jost.

Set `"type_font_h6"` to `"body"` — forces h6 preset to use Jost.

Set `"type_case_h5"` to `"uppercase"`.

Set `"type_case_h6"` to `"uppercase"`.

Set `"type_letter_spacing_h5"` to `"heading-loose"`.

Set `"type_letter_spacing_h6"` to `"heading-loose"`.

Set `"type_size_h5"` to `"12"`.

Set `"type_size_h6"` to `"11"`.

---

## Push both files after changes:

Push `config/settings_data.json` and `templates/index.json` to theme `188273557786` on store `x9iqze-nb.myshopify.com`.