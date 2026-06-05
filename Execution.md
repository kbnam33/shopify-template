Open templates/index.json. Find the section with key "section_Fh7TFQ". Inside its "settings" object, make these two changes:
1. Enable the overlay and set it to a radial vignette effect:
Change "toggle_overlay" from false to true
Change "overlay_style" from "solid" to "gradient"
Change "gradient_direction" from "to top" to "to top"
Change "overlay_color" from "#00000026" to "#00000059"
2. This makes the section use a gradient overlay — a dark fade from the bottom toward the top — which gives the vignette effect that makes white text readable against the image.