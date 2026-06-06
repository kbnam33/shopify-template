# TECHNICAL PLAN — Vignette Fix: Use overlay.liquid Correctly

## TASK 1 — `sections/hero.liquid` — Remove the two vignette divs

In the HTML of `sections/hero.liquid`, find and remove both the `hero__vignette-main` div and the `hero__vignette-nav` div entirely. These have failed across multiple attempts due to Horizon's stacking context system.

---

## TASK 2 — `snippets/overlay.liquid` — Add a custom two-layer gradient style

Inside the `{% stylesheet %}` block of `snippets/overlay.liquid`, after the existing `.overlay--gradient` rule, add a new rule targeting `.overlay--neera-vignette`.

This rule sets `background` to a value that combines two gradients in a single `background` property — a comma-separated list. The first gradient is the main bottom-right vignette at 315 degrees going from `rgba(0,0,0,0.82)` at 0% to `rgba(0,0,0,0.45)` at 30% to fully transparent at 55%. The second gradient runs from top to bottom, starting at `rgba(0,0,0,0.35)` at 0% and fading to transparent over 110px using `calc` — specifically fading to transparent at the point where 110px of height has been covered.

---

## TASK 3 — `templates/index.json` — Enable the overlay and set it to the new style

Inside `section_Fh7TFQ`'s `"settings"` object:

Set `"toggle_overlay"` to `true` — this activates the `render 'overlay'` call inside `.hero__media-grid`, which is already `position: absolute; inset: 0` and uses `z-index: var(--layer-flat)` from the overlay snippet. This stacking context is correct and proven to work.

Set `"overlay_style"` to `"neera-vignette"` — this matches the new CSS class `.overlay--neera-vignette` added in Task 2.

---

## Push both files after changes:

Push `snippets/overlay.liquid` and `templates/index.json` to theme `188273557786` on store `x9iqze-nb.myshopify.com`.