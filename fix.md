TECHNICAL PLAN — Nav Font Fix

TASK 1 — sections/header-group.json — Change nav font to body
Open sections/header-group.json. Inside the "sections" object, find "header_section". Inside its "blocks" object, find the block with key "header-menu". Inside that block's "settings" object, make these two changes:
Change "type_font_primary_link" from "accent" to "body" — this switches the nav from DM Serif Display italic to Jost.
Change "type_case_primary_link" from "uppercase" to "uppercase" — keep this as is, uppercase is correct for Jost nav.

Push after changes:
Push only sections/header-group.json to theme 188273557786 on store x9iqze-nb.myshopify.com.