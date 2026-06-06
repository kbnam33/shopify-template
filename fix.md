---

# TECHNICAL PLAN — Vignette Fix: Correct DOM Position

## TASK 1 — `sections/hero.liquid` — Move vignette divs out of `.hero__media-grid`

In the HTML of `sections/hero.liquid`, locate the two vignette divs (`hero__vignette-main` and `hero__vignette-nav`) that are currently sitting inside the `<div class="hero__media-grid">` element. Remove them from inside that div.

Place both divs immediately **after** the closing tag of `.hero__media-grid` and immediately **before** the opening tag of the `hero__content-wrapper` div. They should be direct children of `.hero__container` at this position.

Update the inline `style` attribute on `hero__vignette-main` to use `z-index: 3` instead of `z-index: 2` — this ensures it sits above the media grid's stacking context entirely.

Update the inline `style` attribute on `hero__vignette-nav` to use `z-index: 3` as well.

Both divs keep all other inline styles exactly as they are — only their DOM position and z-index value changes.

---

## Push after changes:

Push only `sections/hero.liquid` to theme `188273557786` on store `x9iqze-nb.myshopify.com`.