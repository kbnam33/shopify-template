TECHNICAL PLAN — Vignette Fix: Override Grid Column

TASK 1 — sections/hero.liquid — Add grid-column override to both vignette divs
In the HTML of sections/hero.liquid, locate the two vignette divs (hero__vignette-main and hero__vignette-nav). On each div, add grid-column: 1 / -1 to the existing inline style attribute. This forces both divs to span all grid columns — matching how .hero__media-grid spans the full width using grid-column: 1 / -1 in the existing stylesheet.
No other changes needed. DOM position and z-index remain exactly as they are.

Push after changes:
Push only sections/hero.liquid to theme 188273557786 on store x9iqze-nb.myshopify.com.