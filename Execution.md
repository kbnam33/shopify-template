# TECHNICAL PLAN — Two-Layer Vignette on Hero

## TASK 1 — `sections/hero.liquid` — Add nav vignette via `::before` pseudo-element

Inside the `{% stylesheet %}` block of `sections/hero.liquid`, locate the existing `.hero__container` rule. Immediately after it, add a new rule targeting `.hero__container::before`.

Configure it as follows:

- `content` set to empty string
- `position: absolute`, `top: 0`, `left: 0`, `right: 0`
- `height: 110px`
- `background` set to a linear gradient running from top to bottom — starting at `rgba(0,0,0,0.35)` at 0% and ending at fully transparent at 100%
- `z-index` set to `var(--layer-flat)` so it sits above the image
- `pointer-events: none`

This handles navbar readability — the top edge of the hero darkens just enough for the transparent white nav links to read clearly against any bright photograph.

---

## TASK 2 — `sections/hero.liquid` — Add main content vignette via `::after` pseudo-element

Immediately after the `::before` rule added in Task 1, add a new rule targeting `.hero__container::after`.

Configure it as follows:

- `content` set to empty string
- `position: absolute` with `inset: 0`
- `pointer-events: none`
- `z-index` set to `var(--layer-flat)`
- `background` set to a linear gradient at exactly `315deg` — meaning the darkness originates from the bottom-right corner and fades toward the top-left — with three stops: `rgba(0,0,0,0.82)` at 0%, `rgba(0,0,0,0.45)` at 30%, and fully transparent at 55%

This is the main vignette that creates the darkened region where the headline and CTA live.

---

## TASK 3 — `templates/index.json` — Disable the built-in overlay

Inside `section_Fh7TFQ`'s `"settings"` object, set `"toggle_overlay"` to `false`. The two pseudo-element layers from Tasks 1 and 2 fully replace the built-in overlay system. Running both simultaneously would over-darken the image.

---

## Push both files after changes:

Push `sections/hero.liquid` and `templates/index.json` to theme `188273557786` on store `x9iqze-nb.myshopify.com`.