# TECHNICAL PLAN — Hero Content + Nav Fix

## TASK 1 — `templates/index.json` — Remove the stray default text block

Inside `section_Fh7TFQ`, find any text block that contains the default placeholder copy ("Fashion for the wild at heart..."). This block is sitting outside the new group and is not part of the Neera hero. Remove it entirely from both the `"blocks"` object and the `"block_order"` array of the section.

---

## TASK 2 — `templates/index.json` — Fix group block content and alignment

Inside the new group block that was created in the previous task, verify the following:

The `"block_order"` array inside the group contains exactly three items in this order: the headline text block, the subheading text block, and the button block.

Inside the group's `"settings"`, confirm that `content_direction` is set to `column` so the three blocks stack vertically. Confirm `horizontal_alignment_flex_direction_column` is set to `flex-end` and `vertical_alignment_flex_direction_column` is set to `flex-end`.

For the headline text block inside the group, confirm its `"alignment"` setting is `"right"` and its `"text"` contains only "Wear what the day demands." wrapped in an `h1` tag. Remove any period if the brand direction specifies no period, or keep it — Neera's reference uses a period so keep it.

For the subheading text block inside the group, set its `"text"` to "From the first meeting to the last." wrapped in a `p` tag. Set its `"alignment"` to `"right"`. Set its `"type_preset"` to `"paragraph"`. Set its `"color"` to the warm sand value from scheme-2 foreground (`#C8B89A`) so it reads as a quieter second line beneath the headline.

For the button block inside the group, confirm `"alignment"` is `"right"`, text is "Explore the collection", link is `/collections/all`, style is `"secondary"`, and case is `"uppercase"`.

---

## TASK 3 — `config/settings_data.json` — Fix nav typography

Inside the `"current"` object, the nav items render using the h6 preset in Horizon's header. Make these changes:

Set `"type_font_h6"` to `"body"` — this switches nav items to Jost instead of Cormorant.

Set `"type_case_h6"` to `"uppercase"` — nav should remain uppercase for readability.

Set `"type_letter_spacing_h6"` to `"heading-loose"` — adds the spaced tracking that makes Jost uppercase nav legible at small sizes.

Set `"type_size_h6"` to `"12"` — keeps nav compact and refined.

---

## TASK 4 — `config/settings_data.json` — Establish clear type hierarchy

Inside the `"current"` object, update the heading size presets so Cormorant and Jost play distinct roles:

Set `"type_size_h1"` to `"64"` — slightly reduced from 72, gives the hero headline more elegance and less bluntness.

Set `"type_line_height_h1"` to `"display-tight"` — keeps the two-line headline close together as a single visual unit.

Set `"type_letter_spacing_h1"` to `"none"` — Cormorant at display size should have no added tracking, its natural spacing is correct.

Set `"type_case_h1"` to `"none"` — sentence case for the serif headline, consistent with Neera's brand voice.

---

## Push both files after changes:

Push `templates/index.json` and `config/settings_data.json` to theme `188273557786` on store `x9iqze-nb.myshopify.com`.


----------------------------------------------------

# TECHNICAL PLAN — Hero Fixes

## TASK 1 — `templates/index.json` — Hero text alignment and content

Open `templates/index.json`. Find the section with key `"section_Fh7TFQ"`. Inside its `"settings"` object, make these changes:

- Change `horizontal_alignment` to `flex-end` (pushes content to the right side)
- Change `vertical_alignment` to `flex-end` (pushes content to the bottom)
- Change `horizontal_alignment_flex_direction_column` to `flex-end`
- Change `vertical_alignment_flex_direction_column` to `flex-end`

Inside the `"blocks"` object of `"section_Fh7TFQ"`, find the group block (the one wrapping the text blocks). Inside that group's `"settings"`, make these changes:

- Change `horizontal_alignment` to `flex-end`
- Change `vertical_alignment` to `flex-end`
- Change `horizontal_alignment_flex_direction_column` to `flex-end`
- Change `vertical_alignment_flex_direction_column` to `flex-end`
- Change `padding-inline-end` to `48`
- Change `padding-block-end` to `48`

For every text block inside the group (headline, subheading), change `"alignment"` to `"right"`.

For the button block, change `"alignment"` to `"right"`.

---

## TASK 2 — `templates/index.json` — Vignette overlay

Inside the `"settings"` object of `"section_Fh7TFQ"`:

- Ensure `toggle_overlay` is `true`
- Set `overlay_style` to `gradient`
- Set `gradient_direction` to `to top left` — this concentrates the dark fade in the bottom-right corner where the text sits
- Set `overlay_color` to a dark semi-transparent value at approximately 55% opacity

---

## TASK 3 — `config/settings_data.json` — Nav font

Inside the `"current"` object, the navigation uses the heading font by default in this theme. To override it to use the body font (Jost) instead of the heading font (Cormorant), find the setting `"type_font_h5"` and change its value from `"heading"` to `"body"`. The nav in Horizon uses the h5 preset for menu items.

Also change `"type_letter_spacing_h5"` to `"heading-loose"` — this gives Jost the spaced uppercase tracking that matches the reference screenshot nav style.

---

## Push both files after changes:

Push `templates/index.json` and `config/settings_data.json` together to theme `188273557786` on store `x9iqze-nb.myshopify.com`.