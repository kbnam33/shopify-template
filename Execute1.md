## TASK 1 — `config/settings_schema.json`

**Action:** Add a new setting block for hero animation control. Insert this as a new object entry **after** the `"t:names.animations"` block (around line position after `add_to_cart_animation`):

```json
{
  "name": "Hero Section",
  "settings": [
    {
      "type": "checkbox",
      "id": "hero_breathing_animation",
      "label": "Enable hero breathing animation",
      "default": true,
      "info": "Slow scale pulse on the hero background image"
    },
    {
      "type": "range",
      "id": "hero_breathing_duration",
      "label": "Breathing animation speed (seconds)",
      "min": 4,
      "max": 20,
      "step": 1,
      "unit": "s",
      "default": 8
    },
    {
      "type": "select",
      "id": "hero_text_alignment",
      "label": "Hero text alignment",
      "options": [
        { "value": "left", "label": "Left" },
        { "value": "center", "label": "Center" },
        { "value": "right", "label": "Right" }
      ],
      "default": "right"
    },
    {
      "type": "select",
      "id": "hero_text_vertical_position",
      "label": "Hero text vertical position",
      "options": [
        { "value": "top", "label": "Top" },
        { "value": "middle", "label": "Middle" },
        { "value": "bottom", "label": "Bottom" }
      ],
      "default": "bottom"
    },
    {
      "type": "range",
      "id": "hero_overlay_opacity",
      "label": "Image overlay opacity",
      "min": 0,
      "max": 80,
      "step": 5,
      "unit": "%",
      "default": 20
    }
  ]
}
```

---

## TASK 2 — `snippets/theme-styles-variables.liquid`

**Action:** Inside the `:root { }` block, **before** the closing `}` of `:root`, append these CSS custom properties:

```liquid
    /* Hero Breathing Animation */
    --hero-breathing-duration: {{ settings.hero_breathing_duration }}s;
    --hero-overlay-opacity: {{ settings.hero_overlay_opacity | divided_by: 100.0 }};
```

Then, **after** the closing `{% endstyle %}` tag, add this new style block:

```liquid
{% if settings.hero_breathing_animation %}
{% style %}
  @keyframes hero-breathe {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.04); }
  }

  .hero__media--breathing .hero__image,
  .hero__media--breathing video {
    animation: hero-breathe var(--hero-breathing-duration) ease-in-out infinite;
    will-change: transform;
  }
{% endstyle %}
{% endif %}
```

---

## TASK 3 — `sections/hero.liquid`

**Action:** This is the most significant modification. OpenCode should open `sections/hero.liquid` and make the following targeted changes:

**3a. Find the outer section wrapper element** (likely `<div class="hero ...">` or `<section class="hero ...">`) and ensure it has `overflow: hidden` and `position: relative` applied via an inline style or existing class. If no class handles this, add `style="overflow: hidden; position: relative;"`.

**3b. Find the media container** (the element wrapping the background image — likely a `<div class="hero__media">` or similar). Add the conditional class:

```liquid
class="hero__media{% if settings.hero_breathing_animation %} hero__media--breathing{% endif %}"
```

**3c. Find the text/content overlay container** (the element holding the heading, subheading, and CTA — likely `<div class="hero__content">` or similar). Replace or augment its inline/class-based positioning to support the three settings. Add these inline styles:

```liquid
style="
  text-align: {{ settings.hero_text_alignment }};
  align-items: {% if settings.hero_text_alignment == 'right' %}flex-end{% elsif settings.hero_text_alignment == 'center' %}center{% else %}flex-start{% endif %};
  justify-content: {% if settings.hero_text_vertical_position == 'top' %}flex-start{% elsif settings.hero_text_vertical_position == 'middle' %}center{% else %}flex-end{% endif %};
"
```

**3d. Find the overlay element** (if one exists — a `<div>` with a dark background or `rgba` background). Update its opacity to use the CSS variable:

```liquid
style="background-color: rgba(0,0,0,var(--hero-overlay-opacity));"
```

If no overlay element exists, add one directly inside the section wrapper, before the media container:

```liquid
<div class="hero__overlay" style="position: absolute; inset: 0; background-color: rgba(0,0,0,var(--hero-overlay-opacity)); z-index: 1; pointer-events: none;"></div>
```

And ensure the content container has `position: relative; z-index: 2;`.

---

## TASK 4 — `sections/header-announcements.liquid`

**Action:** Open the file. Locate the schema block `{% schema %}` at the bottom. Find the `settings` array and ensure the following settings exist (add any that are missing — do not remove existing ones):

```json
{
  "type": "text",
  "id": "announcement_text",
  "label": "Announcement text",
  "default": "Free shipping on orders above ₹999"
},
{
  "type": "select",
  "id": "announcement_text_case",
  "label": "Text case",
  "options": [
    { "value": "none", "label": "Default" },
    { "value": "uppercase", "label": "Uppercase" }
  ],
  "default": "uppercase"
},
{
  "type": "range",
  "id": "announcement_letter_spacing",
  "label": "Letter spacing",
  "min": 0,
  "max": 8,
  "step": 1,
  "unit": "px",
  "default": 2
}
```

Then in the HTML portion of the file, find the announcement text output element and add these inline styles:

```liquid
style="text-transform: {{ section.settings.announcement_text_case }}; letter-spacing: {{ section.settings.announcement_letter_spacing }}px;"
```

---

## TASK 5 — `sections/marquee.liquid`

**Action:** Open the file. Locate the schema `settings` array and ensure these exist (add any missing):

```json
{
  "type": "range",
  "id": "marquee_speed",
  "label": "Scroll speed (seconds per loop)",
  "min": 10,
  "max": 60,
  "step": 5,
  "default": 25
},
{
  "type": "select",
  "id": "marquee_text_case",
  "label": "Text case",
  "options": [
    { "value": "none", "label": "Default" },
    { "value": "uppercase", "label": "Uppercase" }
  ],
  "default": "none"
},
{
  "type": "text",
  "id": "marquee_separator",
  "label": "Separator between items",
  "default": "·"
}
```

In the HTML, find where the animation duration is set and replace it with:

```liquid
style="--marquee-duration: {{ section.settings.marquee_speed }}s;"
```

Find the text output elements and add:

```liquid
style="text-transform: {{ section.settings.marquee_text_case }};"
```

---

## TASK 6 — `sections/collection-links.liquid`

**Action:** Open the file. Locate the schema and ensure these settings exist:

```json
{
  "type": "text",
  "id": "section_heading",
  "label": "Section heading",
  "default": "Shop by Category"
},
{
  "type": "select",
  "id": "columns_desktop",
  "label": "Columns on desktop",
  "options": [
    { "value": "2", "label": "2" },
    { "value": "3", "label": "3" },
    { "value": "4", "label": "4" }
  ],
  "default": "3"
},
{
  "type": "select",
  "id": "image_ratio",
  "label": "Image ratio",
  "options": [
    { "value": "square", "label": "Square" },
    { "value": "portrait", "label": "Portrait (3:4)" },
    { "value": "landscape", "label": "Landscape (4:3)" }
  ],
  "default": "portrait"
}
```

In the HTML, find the grid container and set columns via inline style or CSS variable:

```liquid
style="--collection-grid-columns: {{ section.settings.columns_desktop }};"
```

Add this to your theme's CSS (or inline in the section):

```css
.collection-links__grid {
  display: grid;
  grid-template-columns: repeat(var(--collection-grid-columns, 3), 1fr);
  gap: var(--gap-2xl);
}

@media screen and (max-width: 749px) {
  .collection-links__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
```

---

## TASK 7 — Create `sections/email-signup-custom.liquid`

**Action:** Create this file from scratch at `D:\Shopify-theme\sections\email-signup-custom.liquid`:

```liquid
<section
  class="email-signup-custom color-{{ section.settings.color_scheme }}"
  style="padding-block: {{ section.settings.padding_top }}px {{ section.settings.padding_bottom }}px;"
>
  <div class="email-signup-custom__inner page-width">
    {%- if section.settings.heading != blank -%}
      <h2
        class="email-signup-custom__heading"
        style="text-transform: {{ section.settings.heading_case }}; letter-spacing: {{ section.settings.heading_letter_spacing }}px;"
      >
        {{ section.settings.heading }}
      </h2>
    {%- endif -%}

    {%- if section.settings.subheading != blank -%}
      <p class="email-signup-custom__subheading">{{ section.settings.subheading }}</p>
    {%- endif -%}

    {%- form 'customer', class: 'email-signup-custom__form' -%}
      <input type="hidden" name="contact[tags]" value="newsletter">
      <div class="email-signup-custom__field-group">
        <input
          type="email"
          name="contact[email]"
          placeholder="{{ section.settings.input_placeholder }}"
          required
          autocorrect="off"
          autocapitalize="off"
          class="email-signup-custom__input"
        >
        <button
          type="submit"
          class="email-signup-custom__button button button--primary"
          style="text-transform: {{ section.settings.button_case }}; letter-spacing: {{ section.settings.button_letter_spacing }}px;"
        >
          {{ section.settings.button_text }}
        </button>
      </div>

      {%- if form.errors -%}
        <p class="email-signup-custom__error">{{ form.errors | default_errors }}</p>
      {%- endif -%}

      {%- if form.posted_successfully? -%}
        <p class="email-signup-custom__success">{{ section.settings.success_message }}</p>
      {%- endif -%}
    {%- endform -%}
  </div>
</section>

<style>
  .email-signup-custom {
    text-align: center;
  }
  .email-signup-custom__inner {
    max-width: 560px;
    margin-inline: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--gap-xl);
  }
  .email-signup-custom__heading {
    font-family: var(--font-heading--family);
    font-size: var(--font-size--h3);
    line-height: var(--line-height--display-normal);
    margin: 0;
  }
  .email-signup-custom__subheading {
    font-size: var(--font-size--paragraph);
    opacity: var(--opacity-subdued-text);
    margin: 0;
  }
  .email-signup-custom__form {
    width: 100%;
  }
  .email-signup-custom__field-group {
    display: flex;
    gap: var(--gap-sm);
    flex-wrap: wrap;
    justify-content: center;
  }
  .email-signup-custom__input {
    flex: 1 1 220px;
    min-width: 0;
  }
  .email-signup-custom__error {
    color: var(--color-error);
    font-size: var(--font-size--sm);
    margin-top: var(--margin-sm);
  }
  .email-signup-custom__success {
    color: var(--color-success);
    font-size: var(--font-size--sm);
    margin-top: var(--margin-sm);
  }
</style>

{% schema %}
{
  "name": "Email Signup",
  "tag": "section",
  "class": "email-signup-section",
  "settings": [
    {
      "type": "color_scheme",
      "id": "color_scheme",
      "label": "Color scheme",
      "default": "scheme-1"
    },
    {
      "type": "text",
      "id": "heading",
      "label": "Heading",
      "default": "Stay in the loop"
    },
    {
      "type": "select",
      "id": "heading_case",
      "label": "Heading text case",
      "options": [
        { "value": "none", "label": "Default" },
        { "value": "uppercase", "label": "Uppercase" }
      ],
      "default": "none"
    },
    {
      "type": "range",
      "id": "heading_letter_spacing",
      "label": "Heading letter spacing",
      "min": 0,
      "max": 8,
      "step": 1,
      "unit": "px",
      "default": 0
    },
    {
      "type": "text",
      "id": "subheading",
      "label": "Subheading",
      "default": "New arrivals, restocks, and nothing else."
    },
    {
      "type": "text",
      "id": "input_placeholder",
      "label": "Input placeholder",
      "default": "Your email address"
    },
    {
      "type": "text",
      "id": "button_text",
      "label": "Button text",
      "default": "Subscribe"
    },
    {
      "type": "select",
      "id": "button_case",
      "label": "Button text case",
      "options": [
        { "value": "none", "label": "Default" },
        { "value": "uppercase", "label": "Uppercase" }
      ],
      "default": "uppercase"
    },
    {
      "type": "range",
      "id": "button_letter_spacing",
      "label": "Button letter spacing",
      "min": 0,
      "max": 8,
      "step": 1,
      "unit": "px",
      "default": 2
    },
    {
      "type": "text",
      "id": "success_message",
      "label": "Success message",
      "default": "Thank you for subscribing."
    },
    {
      "type": "range",
      "id": "padding_top",
      "label": "Padding top",
      "min": 0,
      "max": 120,
      "step": 4,
      "unit": "px",
      "default": 60
    },
    {
      "type": "range",
      "id": "padding_bottom",
      "label": "Padding bottom",
      "min": 0,
      "max": 120,
      "step": 4,
      "unit": "px",
      "default": 60
    }
  ],
  "presets": [
    {
      "name": "Email Signup"
    }
  ]
}
{% endschema %}
```

---

## TASK 8 — `templates/index.json`

**Action:** Open `templates/index.json`. Find the `"order"` array and set the section order to:

```json
"order": [
  "header_announcements",
  "hero",
  "marquee",
  "collection_links",
  "email_signup_custom"
]
```

Make sure each section in the `"sections"` object matches its key. If `email_signup_custom` doesn't exist yet as a key, add it:

```json
"email_signup_custom": {
  "type": "email-signup-custom",
  "settings": {}
}
```

---