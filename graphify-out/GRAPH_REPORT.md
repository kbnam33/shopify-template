# Graph Report - .  (2026-06-06)

## Corpus Check
- 114 files · ~139,110 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 1044 nodes · 1601 edges · 74 communities detected
- Extraction: 81% EXTRACTED · 18% INFERRED · 0% AMBIGUOUS · INFERRED: 293 edges (avg confidence: 0.8)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Facet Filtering|Facet Filtering]]
- [[_COMMUNITY_Cart Drawer|Cart Drawer]]
- [[_COMMUNITY_Deferred Media Player|Deferred Media Player]]
- [[_COMMUNITY_Image Comparison Slider|Image Comparison Slider]]
- [[_COMMUNITY_Component Base + Quantity Selectors|Component Base + Quantity Selectors]]
- [[_COMMUNITY_Cart Quantity Selector|Cart Quantity Selector]]
- [[_COMMUNITY_Localization Dropdown|Localization Dropdown]]
- [[_COMMUNITY_Quick Order List|Quick Order List]]
- [[_COMMUNITY_Custom Accordion|Custom Accordion]]
- [[_COMMUNITY_DOM Morph + Hydration|DOM Morph + Hydration]]
- [[_COMMUNITY_Popover Utilities|Popover Utilities]]
- [[_COMMUNITY_Collection Links Tabs|Collection Links Tabs]]
- [[_COMMUNITY_Product Card|Product Card]]
- [[_COMMUNITY_Custom Cart & Filter Events|Custom Cart & Filter Events]]
- [[_COMMUNITY_Hero Typography Plans|Hero Typography Plans]]
- [[_COMMUNITY_Layered Slideshow|Layered Slideshow]]
- [[_COMMUNITY_Morph & Performance Utils|Morph & Performance Utils]]
- [[_COMMUNITY_Paginated List Aspect Ratio|Paginated List Aspect Ratio]]
- [[_COMMUNITY_Cart Line Items|Cart Line Items]]
- [[_COMMUNITY_Mobile Header Drawer|Mobile Header Drawer]]
- [[_COMMUNITY_Gift Card Recipient Form|Gift Card Recipient Form]]
- [[_COMMUNITY_Desktop Header Menu|Desktop Header Menu]]
- [[_COMMUNITY_Declarative Shadow Component|Declarative Shadow Component]]
- [[_COMMUNITY_Marquee|Marquee]]
- [[_COMMUNITY_Announcement Bar|Announcement Bar]]
- [[_COMMUNITY_QR Code Generator|QR Code Generator]]
- [[_COMMUNITY_Section Rendering & Utilities|Section Rendering & Utilities]]
- [[_COMMUNITY_Volume Pricing Display|Volume Pricing Display]]
- [[_COMMUNITY_Cart Components Overview|Cart Components Overview]]
- [[_COMMUNITY_Results List|Results List]]
- [[_COMMUNITY_Cart Discount Codes|Cart Discount Codes]]
- [[_COMMUNITY_Cart Icon Counter|Cart Icon Counter]]
- [[_COMMUNITY_Anchored Popover|Anchored Popover]]
- [[_COMMUNITY_Header Actions|Header Actions]]
- [[_COMMUNITY_Product Custom Property|Product Custom Property]]
- [[_COMMUNITY_Rich Text Formatter|Rich Text Formatter]]
- [[_COMMUNITY_Copy to Clipboard|Copy to Clipboard]]
- [[_COMMUNITY_QR Code Image|QR Code Image]]
- [[_COMMUNITY_Search Page Input|Search Page Input]]
- [[_COMMUNITY_Video Background|Video Background]]
- [[_COMMUNITY_Image & Popover Comparison|Image & Popover Comparison]]
- [[_COMMUNITY_Slideshow Variants|Slideshow Variants]]
- [[_COMMUNITY_Blog Posts List|Blog Posts List]]
- [[_COMMUNITY_Cart Note|Cart Note]]
- [[_COMMUNITY_Caret & Double Chevron|Caret & Double Chevron]]
- [[_COMMUNITY_In-stock Checkmark|In-stock Checkmark]]
- [[_COMMUNITY_Left Right Chevrons|Left Right Chevrons]]
- [[_COMMUNITY_Close X Icons|Close X Icons]]
- [[_COMMUNITY_Grid Density Icons|Grid Density Icons]]
- [[_COMMUNITY_Plus Minus Icons|Plus Minus Icons]]
- [[_COMMUNITY_Play Pause Icons|Play Pause Icons]]
- [[_COMMUNITY_Accordion & Auto-Close|Accordion & Auto-Close]]
- [[_COMMUNITY_QR Code Pipeline|QR Code Pipeline]]
- [[_COMMUNITY_Volume Pricing Module|Volume Pricing Module]]
- [[_COMMUNITY_Add to Cart Icon|Add to Cart Icon]]
- [[_COMMUNITY_Arrow Icon|Arrow Icon]]
- [[_COMMUNITY_Checkmark Burst|Checkmark Burst]]
- [[_COMMUNITY_Delete Icon|Delete Icon]]
- [[_COMMUNITY_Discount Icon|Discount Icon]]
- [[_COMMUNITY_Error Icon|Error Icon]]
- [[_COMMUNITY_External Link Icon|External Link Icon]]
- [[_COMMUNITY_Filter Icon|Filter Icon]]
- [[_COMMUNITY_Info Icon|Info Icon]]
- [[_COMMUNITY_One Column Mobile Icon|One Column Mobile Icon]]
- [[_COMMUNITY_Reset Icon|Reset Icon]]
- [[_COMMUNITY_Search Icon|Search Icon]]
- [[_COMMUNITY_Shopify Logo Icon|Shopify Logo Icon]]
- [[_COMMUNITY_Slideshow Select Event|Slideshow Select Event]]
- [[_COMMUNITY_Cycle Focus|Cycle Focus]]
- [[_COMMUNITY_Custom Property Counter|Custom Property Counter]]
- [[_COMMUNITY_Product Title Truncation|Product Title Truncation]]
- [[_COMMUNITY_RTE Table Wrapper|RTE Table Wrapper]]
- [[_COMMUNITY_Scroll Hint|Scroll Hint]]
- [[_COMMUNITY_Video Background Loader|Video Background Loader]]

## God Nodes (most connected - your core abstractions)
1. `closest()` - 44 edges
2. `Slideshow` - 33 edges
3. `Component base class` - 30 edges
4. `LayeredSlideshowComponent` - 27 edges
5. `preventDefault()` - 27 edges
6. `QuickOrderListComponent` - 26 edges
7. `QuantitySelectorComponent` - 19 edges
8. `ProductCard` - 18 edges
9. `GiftCardRecipientForm` - 17 edges
10. `OverflowList` - 17 edges

## Surprising Connections (you probably didn't know these)
- `<results-list> (PaginatedList subclass with layout switcher)` --calls--> `Scroller`  [INFERRED]
  assets/results-list.js → D:\Shopify-theme\assets\scrolling.js
- `Technical Plan — Hero Typography Fixes` --semantically_similar_to--> `Technical Plan — Hero Design Refinement`  [INFERRED] [semantically similar]
  E2.md → Execution.md
- `Technical Plan — Hero Typography Fixes` --semantically_similar_to--> `Technical Plan — Hero Content + Nav Fix (two plans)`  [INFERRED] [semantically similar]
  E2.md → ideal_instruction_format.md
- `Technical Plan — Nav Font Fix` --semantically_similar_to--> `Technical Plan — Hero Typography Fixes`  [INFERRED] [semantically similar]
  fix.md → E2.md
- `Technical Plan — Hero Design Refinement` --semantically_similar_to--> `Technical Plan — Hero Content + Nav Fix (two plans)`  [INFERRED] [semantically similar]
  Execution.md → ideal_instruction_format.md

## Hyperedges (group relationships)
- **Neera hero design system (font, type scale, layout, color, CTA)** — dm_serif_display, jost_font, neera_brand_voice, two_line_headline_break, warm_sand_color, cta_explore_collection, headline_wear_what, subheading_from_first_meeting [EXTRACTED 0.90]
- **Nav typography override chain (preset → font → case → tracking → size)** — horizon_theme, jost_font, ideal_instruction_format_md, e2_md, fix_md, execution_md [EXTRACTED 0.85]
- **Hero section modification cluster — all four plans touch templates/index.json section_Fh7TFQ** — hero_section_fh7tfq, e2_md, execution_md, ideal_instruction_format_md, theme_188273557786 [EXTRACTED 0.95]
- **Cart state coordination via ThemeEvents (cartUpdate/discountUpdate/quantitySelectorUpdate/cartAdd)** — cart_icon, cart_drawer, cart_discount, cart_note, component_cart_items [INFERRED 0.90]
- **Open/close lifecycle of native <details> elements** — accordion_custom, auto_close_details [INFERRED 0.85]
- **Cart mutation -> morphSection re-render pipeline (uses Theme.routes.cart_*_url + morphSection)** — cart_discount, cart_note, component_cart_items [INFERRED 0.85]
- **Cart update event-driven orchestration** — events_ThemeEvents, events_CartUpdateEvent, events_CartErrorEvent, header_actions_HeaderActions, gift_card_recipient_form_GiftCardRecipientForm [EXTRACTED 0.90]
- **Variant selection propagates to dependent UI** — events_VariantUpdateEvent, media_gallery_MediaGallery, local_pickup_LocalPickup, events_ThemeEvents [EXTRACTED 0.90]
- **Faceted filtering coordination pattern** — facets_FacetsFormComponent, facets_FacetInputsComponent, facets_PriceFacetComponent, facets_FacetStatusComponent, facets_FacetClearComponent, events_FilterUpdateEvent [EXTRACTED 0.95]
- **Variant update event listeners that re-render their own subtree** — product-inventory_product-inventory, product-price_product-price, product-sku_product-sku, product-form_product-form [INFERRED 0.90]
- **Components that use morph() for in-place DOM updates (no full re-render)** — predictive-search_predictive-search, product-card_product-card, product-inventory_product-inventory, product-form_product-form, quick-add_quick-add [EXTRACTED 0.95]
- **Section-renderer-driven paginated/hydrated content fetchers** — paginated-list_paginated-list, results-list_results-list, product-recommendations_product-recommendations, quick-order-list_quick-order-list [INFERRED 0.85]
- **View Transitions API orchestration across SPA navigation, gallery zoom, and slideshow setup** — utilities.utilities, slideshow.Slideshow, zoom-dialog.ZoomDialog, view-transitions.viewTransitions [INFERRED 0.90]
- **Section Rendering API + morph-based partial DOM update pipeline** — section-renderer.SectionRenderer, section-hydration.hydrate, variant-picker.VariantPicker, sticky-add-to-cart.StickyAddToCartComponent [INFERRED 0.85]
- **Custom elements extending Component base class with refs/dataset/requiredRefs lifecycle** — search-page-input.SearchPageInputComponent, show-more.ShowMoreComponent, slideshow.Slideshow, sticky-add-to-cart.StickyAddToCartComponent, variant-picker.VariantPicker, video-background.VideoBackgroundComponent, volume-pricing.VolumePricingComponent, volume-pricing-info.VolumePricingInfoComponent, zoom-dialog.ZoomDialog [EXTRACTED 1.00]

## Communities

### Community 0 - "Facet Filtering"
Cohesion: 0.04
Nodes (16): FacetClearComponent, FacetInputsComponent, FacetRemoveComponent, FacetsFormComponent, FacetStatusComponent, PriceFacetComponent, SortingFilterComponent, LocalPickup (+8 more)

### Community 1 - "Cart Drawer"
Cohesion: 0.03
Nodes (25): CartDrawerComponent, DialogCloseEvent, DialogComponent, DialogOpenEvent, MediaGallery, scrollIntoView(), calculateHeaderGroupHeight(), debounce() (+17 more)

### Community 2 - "Deferred Media Player"
Cohesion: 0.04
Nodes (10): DeferredMedia, ProductModel, calculatePaddingStart(), getScrollAxis(), Scroller, onPointerMove(), onPointerUp(), Slideshow (+2 more)

### Community 3 - "Image Comparison Slider"
Cohesion: 0.04
Nodes (10): ComparisonSliderComponent, FloatingPanelComponent, FlyToCart, HeaderComponent, JumboText, OverflowList, OverflowMinimumEvent, ProductRecommendations (+2 more)

### Community 4 - "Component Base + Quantity Selectors"
Cohesion: 0.06
Nodes (57): Component base class, DeclarativeShadowElement, MissingRefError, CartQuantitySelectorComponent, QuantitySelectorComponent, getEffectiveMax (product page logic), updateButtonStates, registerEventListeners (delegated event system) (+49 more)

### Community 5 - "Cart Quantity Selector"
Cohesion: 0.08
Nodes (6): CartQuantitySelectorComponent, QuantitySelectorComponent, AddToCartComponent, ProductFormComponent, parseIntOrDefault(), preventDefault()

### Community 6 - "Localization Dropdown"
Cohesion: 0.06
Nodes (8): DrawerLocalizationComponent, DropdownLocalizationComponent, LocalizationFormComponent, PredictiveSearchComponent, RecentlyViewed, normalizeString(), onAnimationEnd(), VolumePricingComponent

### Community 7 - "Quick Order List"
Cohesion: 0.09
Nodes (13): QuickOrderListComponent, hydrate(), hydrateSection(), buildSectionRenderingURL(), buildSectionSelector(), containsShadowRoot(), injectSectionStylesheet(), morphSection() (+5 more)

### Community 8 - "Custom Accordion"
Cohesion: 0.06
Nodes (6): AccordionCustom, ProductHotspotComponent, QuickAddComponent, QuickAddDialog, ShowMoreComponent, isMobileBreakpoint()

### Community 9 - "DOM Morph + Hydration"
Cohesion: 0.09
Nodes (16): collectHydrationTargets(), copyAttributes(), getNodeKey(), morph(), morphHydrationByKey(), recreateAppBlockScripts(), same(), updateAttribute() (+8 more)

### Community 10 - "Popover Utilities"
Cohesion: 0.14
Nodes (30): apply(), checkPopoverValidity(), closeAllOpenPopovers(), closeAllOpenPopoversInList(), focusDelegate(), getPopoverVisibilityState(), getRootNode(), getStackPosition() (+22 more)

### Community 11 - "Collection Links Tabs"
Cohesion: 0.09
Nodes (8): CollectionLinks, DragZoomWrapper, getDistance(), cycleFocus(), getFocusableElements(), removeTrapFocus(), trapFocus(), clamp()

### Community 12 - "Product Card"
Cohesion: 0.08
Nodes (3): ProductCard, ProductCardLink, SwatchesVariantPickerComponent

### Community 13 - "Custom Cart & Filter Events"
Cohesion: 0.07
Nodes (13): CartAddEvent, CartErrorEvent, CartUpdateEvent, DiscountUpdateEvent, FilterUpdateEvent, MediaStartedPlayingEvent, MegaMenuHoverEvent, QuantitySelectorUpdateEvent (+5 more)

### Community 14 - "Hero Typography Plans"
Cohesion: 0.14
Nodes (27): Cormorant — prior heading font being replaced, CTA 'Explore the collection' → /collections/all, DM Serif Display — heading font family, Technical Plan — Hero Typography Fixes, Technical Plan — Hero Design Refinement, Technical Plan — Nav Font Fix, header-menu block inside sections/header-group.json, Headline copy 'Wear what the day demands.' (+19 more)

### Community 15 - "Layered Slideshow"
Cohesion: 0.14
Nodes (1): LayeredSlideshowComponent

### Community 16 - "Morph & Performance Utils"
Cohesion: 0.1
Nodes (26): morph() DOM tree differ, MORPH_OPTIONS default configuration, <overflow-list> custom element with ResizeObserver reflow, OverflowMinimumEvent (overflowMinimum bubble event), PaginatedListAspectRatioHelper (design-mode aspect ratio enforcer), <paginated-list> custom element with infinity scroll, cartPerformance singleton ('cart-performance' prefix), ThemePerformance class wrapping performance.mark/measure (+18 more)

### Community 17 - "Paginated List Aspect Ratio"
Cohesion: 0.16
Nodes (2): PaginatedListAspectRatioHelper, PaginatedList

### Community 18 - "Cart Line Items"
Cohesion: 0.12
Nodes (3): CartItemsComponent, ThemePerformance, TextComponent

### Community 19 - "Mobile Header Drawer"
Cohesion: 0.15
Nodes (3): HeaderDrawer, saveEditorState(), update()

### Community 20 - "Gift Card Recipient Form"
Cohesion: 0.23
Nodes (1): GiftCardRecipientForm

### Community 21 - "Desktop Header Menu"
Cohesion: 0.15
Nodes (3): findSubmenu(), HeaderMenu, onDocumentLoaded()

### Community 22 - "Declarative Shadow Component"
Cohesion: 0.17
Nodes (8): Component, DeclarativeShadowElement, getAncestor(), getClosestComponent(), MissingRefError, parseData(), parseValue(), registerEventListeners()

### Community 23 - "Marquee"
Cohesion: 0.21
Nodes (2): animateValue(), MarqueeComponent

### Community 24 - "Announcement Bar"
Cohesion: 0.21
Nodes (1): AnnouncementBar

### Community 25 - "QR Code Generator"
Cohesion: 0.2
Nodes (2): getTypeNumber(), getUTF8Length()

### Community 26 - "Section Rendering & Utilities"
Cohesion: 0.27
Nodes (11): SearchPageInputComponent (search input clear-on-Escape-when-empty and form submit), Section hydration entry (idle-time partial section re-render with state preservation), SectionRenderer singleton (fetches + morphs section HTML via Section Rendering API, supports hydration/full modes, aborts in-flight morphs), ShowMoreComponent (expand/collapse content with height animation, responsive desktop-disable, data-expanded state), Slideshow (scroll-snap carousel with drag, autoplay pause-on-hover/visibility, viewport-gated compositing to avoid iOS Safari crash, infinite-loop placeholder trick), StickyAddToCartComponent (floats when buy buttons scroll out, hides at footer, morphs on variant update, fly-to-cart animation), Theme editor integration (block:select/deselect slideshow orchestration, header custom-properties refresh, dialog open-state persistence across editor reloads), Utilities module (debounce/throttle, requestIdleCallback, viewTransition state, scheduler, morph helpers, header custom properties, fetch config, media queries) (+3 more)

### Community 27 - "Volume Pricing Display"
Cohesion: 0.36
Nodes (1): PricePerItemComponent

### Community 28 - "Cart Components Overview"
Cohesion: 0.32
Nodes (8): CartDiscount (apply/remove discount codes), CartDrawerComponent (Dialog + history state), CartIcon (bubble count + sessionStorage cache), CartNote (debounced note PATCH), CartItemsComponent (quantity/discount/morph pipeline), Inventory Status Dot Icon, Orders Clipboard Icon, Out-of-Stock Red X Icon

### Community 29 - "Results List"
Cohesion: 0.33
Nodes (1): ResultsList

### Community 30 - "Cart Discount Codes"
Cohesion: 0.4
Nodes (1): CartDiscount

### Community 31 - "Cart Icon Counter"
Cohesion: 0.4
Nodes (1): CartIcon

### Community 32 - "Anchored Popover"
Cohesion: 0.5
Nodes (1): AnchoredPopoverComponent

### Community 33 - "Header Actions"
Cohesion: 0.5
Nodes (1): HeaderActions

### Community 34 - "Product Custom Property"
Cohesion: 0.67
Nodes (1): ProductCustomProperty

### Community 35 - "Rich Text Formatter"
Cohesion: 0.5
Nodes (1): RTEFormatter

### Community 36 - "Copy to Clipboard"
Cohesion: 0.67
Nodes (1): CopyToClipboardComponent

### Community 37 - "QR Code Image"
Cohesion: 0.67
Nodes (1): QRCodeImage

### Community 38 - "Search Page Input"
Cohesion: 0.67
Nodes (1): SearchPageInputComponent

### Community 39 - "Video Background"
Cohesion: 0.67
Nodes (1): VideoBackgroundComponent

### Community 40 - "Image & Popover Comparison"
Cohesion: 0.67
Nodes (3): AnchoredPopoverComponent (popover anchor + CSS-var positioning), ComparisonSliderComponent (image compare with --compare CSS var), Hamburger Menu Icon

### Community 41 - "Slideshow Variants"
Cohesion: 0.67
Nodes (3): AnnouncementBar (autoplay slideshow), BlogPostsList (PaginatedList subclass), CollectionLinks (slideshow tab strip with hover-reveal images)

### Community 42 - "Blog Posts List"
Cohesion: 1.0
Nodes (1): BlogPostsList

### Community 43 - "Cart Note"
Cohesion: 1.0
Nodes (1): CartNote

### Community 44 - "Caret & Double Chevron"
Cohesion: 1.0
Nodes (2): Down caret (14x14), Double chevron (up and down)

### Community 45 - "In-stock Checkmark"
Cohesion: 1.0
Nodes (2): Available / in-stock checkmark (green), Checkmark icon

### Community 46 - "Left Right Chevrons"
Cohesion: 1.0
Nodes (2): Chevron left (8x12), Chevron right (8x12)

### Community 47 - "Close X Icons"
Cohesion: 1.0
Nodes (2): Close X icon (14x14), Filters-close small X (7x8)

### Community 48 - "Grid Density Icons"
Cohesion: 1.0
Nodes (2): Grid 2x2 view icon (default density), Grid 3x3 view icon (dense density)

### Community 49 - "Plus Minus Icons"
Cohesion: 1.0
Nodes (2): Minus Sign Icon, Plus Sign Icon

### Community 50 - "Play Pause Icons"
Cohesion: 1.0
Nodes (2): Pause Icon, Play Icon

### Community 51 - "Accordion & Auto-Close"
Cohesion: 1.0
Nodes (2): AccordionCustom (details/summary wrapper), AutoCloseDetails (global details click-closer IIFE)

### Community 52 - "QR Code Pipeline"
Cohesion: 1.0
Nodes (2): QRCode class (3rd-party qrcodejs port), <qr-code-image> custom element

### Community 53 - "Volume Pricing Module"
Cohesion: 1.0
Nodes (2): VolumePricingInfoComponent (popover body with quantity-tier highlight, triggers parent anchored-popover-component ref refresh), VolumePricingComponent (expandable pricing-tier table, simple class toggle)

### Community 56 - "Add to Cart Icon"
Cohesion: 1.0
Nodes (1): Add to cart icon — bag with plus

### Community 57 - "Arrow Icon"
Cohesion: 1.0
Nodes (1): Right arrow icon

### Community 58 - "Checkmark Burst"
Cohesion: 1.0
Nodes (1): Checkmark with burst animation (8 lines, animated)

### Community 59 - "Delete Icon"
Cohesion: 1.0
Nodes (1): Delete / trash icon

### Community 60 - "Discount Icon"
Cohesion: 1.0
Nodes (1): Discount / price tag icon

### Community 61 - "Error Icon"
Cohesion: 1.0
Nodes (1): Error icon — red circle with exclamation

### Community 62 - "External Link Icon"
Cohesion: 1.0
Nodes (1): External link icon (box with arrow)

### Community 63 - "Filter Icon"
Cohesion: 1.0
Nodes (1): Filter icon — funnel-like horizontal sliders

### Community 64 - "Info Icon"
Cohesion: 1.0
Nodes (1): Info Icon

### Community 65 - "One Column Mobile Icon"
Cohesion: 1.0
Nodes (1): Single Column Mobile Layout Icon

### Community 66 - "Reset Icon"
Cohesion: 1.0
Nodes (1): Reset/Clear Circle-X Icon

### Community 67 - "Search Icon"
Cohesion: 1.0
Nodes (1): Search Magnifier Icon

### Community 68 - "Shopify Logo Icon"
Cohesion: 1.0
Nodes (1): Shopify Logo Icon

### Community 69 - "Slideshow Select Event"
Cohesion: 1.0
Nodes (1): SlideshowSelectEvent

### Community 70 - "Cycle Focus"
Cohesion: 1.0
Nodes (1): cycleFocus

### Community 71 - "Custom Property Counter"
Cohesion: 1.0
Nodes (1): <product-custom-property-component> char counter

### Community 72 - "Product Title Truncation"
Cohesion: 1.0
Nodes (1): <product-title> responsive -webkit-line-clamp

### Community 73 - "RTE Table Wrapper"
Cohesion: 1.0
Nodes (1): <rte-formatter> table wrapper injector

### Community 74 - "Scroll Hint"
Cohesion: 1.0
Nodes (1): <scroll-hint> fade-mask custom element

### Community 75 - "Video Background Loader"
Cohesion: 1.0
Nodes (1): VideoBackgroundComponent (sets video src from dataset, triggers videoElement.load)

## Ambiguous Edges - Review These
- `Inventory Status Dot Icon` → `CartDiscount (apply/remove discount codes)`  [AMBIGUOUS]
  assets/icon-inventory.svg · relation: conceptually_related_to
- `Hamburger Menu Icon` → `AnchoredPopoverComponent (popover anchor + CSS-var positioning)`  [AMBIGUOUS]
  assets/icon-menu.svg · relation: conceptually_related_to
- `Orders Clipboard Icon` → `CartDrawerComponent (Dialog + history state)`  [AMBIGUOUS]
  assets/icon-orders.svg · relation: conceptually_related_to
- `Out-of-Stock Red X Icon` → `CartItemsComponent (quantity/discount/morph pipeline)`  [AMBIGUOUS]
  assets/icon-unavailable.svg · relation: conceptually_related_to

## Knowledge Gaps
- **78 isolated node(s):** `BlogPostsList`, `CartNote`, `ThemeEvents`, `Scheduler`, `Add to cart icon — bag with plus` (+73 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **Thin community `Layered Slideshow`** (26 nodes): `layered-slideshow.js`, `LayeredSlideshowComponent`, `.#activate()`, `.#clearHeightStyles()`, `.connectedCallback()`, `.#endDrag()`, `.#focusPanelEdge()`, `.#getFocusableElements()`, `.#getMaxContentHeight()`, `.#handleDrag()`, `.#handleKeydown()`, `.#handlePanelKeydown()`, `.#handleTabClick()`, `.#handleTabFocus()`, `.#inactiveSize()`, `.#initializeDrag()`, `.#observeContentHeight()`, `.select()`, `.#setupEventListeners()`, `.#setupPanelFocusManagement()`, `.#startDrag()`, `.#syncDesktopHeight()`, `.#syncHeight()`, `.#syncMobileHeight()`, `.#updateActiveTab()`, `.#updateGridSizes()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Paginated List Aspect Ratio`** (24 nodes): `paginated-list-aspect-ratio.js`, `PaginatedListAspectRatioHelper`, `.#applyAspectRatioToGallery()`, `.#applyFixedAspectRatio()`, `.constructor()`, `.#fixAdaptiveAspectRatios()`, `.#getAspectRatioValue()`, `.#getSafeImageAspectRatio()`, `.#getUnprocessedGalleries()`, `.#markAsProcessed()`, `.processNewElements()`, `.#storeImageRatioSettings()`, `paginated-list.js`, `PaginatedList`, `.connectedCallback()`, `.#fetchPage()`, `.#fetchSpecificPage()`, `.#getGridForPage()`, `.#getPage()`, `.#observeViewMore()`, `.#renderNextPage()`, `.#renderPreviousPage()`, `.sectionId()`, `.#shouldUsePage()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Gift Card Recipient Form`** (18 nodes): `GiftCardRecipientForm`, `.#clearErrorMessages()`, `.#clearRecipientFields()`, `.connectedCallback()`, `.#disableRecipientFields()`, `.disconnectedCallback()`, `.#displayCartError()`, `.#displayErrorMessage()`, `.#enableRecipientFields()`, `.#handleCartAdd()`, `.#initializeForm()`, `.#inputFields()`, `.#setDateConstraints()`, `.toggleRecipientForm()`, `.#updateButtonStates()`, `.#updateCharacterCount()`, `.#updateFormState()`, `gift-card-recipient-form.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Marquee`** (14 nodes): `animateValue()`, `marquee.js`, `MarqueeComponent`, `.#addRepeatedItems()`, `.#calculateSpeed()`, `.clonedContent()`, `.connectedCallback()`, `.disconnectedCallback()`, `.#duplicateContent()`, `.#queryNumberOfCopies()`, `.#removeRepeatedItems()`, `.#restartAnimation()`, `.#setSpeed()`, `.#speedUp()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Announcement Bar`** (13 nodes): `AnnouncementBar`, `.autoplay()`, `.autoplayInterval()`, `.connectedCallback()`, `.current()`, `.next()`, `.pause()`, `.paused()`, `.play()`, `.previous()`, `.resume()`, `.suspend()`, `announcement-bar.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `QR Code Generator`** (11 nodes): `getTypeNumber()`, `getUTF8Length()`, `isSupportCanvas()`, `qr-code-generator.js`, `makeSVG()`, `onMakeImage()`, `QRBitBuffer()`, `QRCode()`, `QRCodeModel()`, `QRPolynomial()`, `QRRSBlock()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Volume Pricing Display`** (8 nodes): `price-per-item.js`, `PricePerItemComponent`, `.#attachEventListeners()`, `.connectedCallback()`, `.disconnectedCallback()`, `.#getCurrentQuantity()`, `.#parsePriceBreaks()`, `.updatePriceDisplay()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Results List`** (6 nodes): `results-list.js`, `ResultsList`, `.connectedCallback()`, `.disconnectedCallback()`, `.#setLayout()`, `.updateLayout()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Cart Discount Codes`** (5 nodes): `CartDiscount`, `.#createAbortController()`, `.#existingDiscounts()`, `.#handleDiscountError()`, `cart-discount.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Cart Icon Counter`** (5 nodes): `CartIcon`, `.connectedCallback()`, `.currentCartCount()`, `.disconnectedCallback()`, `cart-icon.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Anchored Popover`** (4 nodes): `AnchoredPopoverComponent`, `.connectedCallback()`, `.disconnectedCallback()`, `anchored-popover.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Header Actions`** (4 nodes): `HeaderActions`, `.connectedCallback()`, `.disconnectedCallback()`, `header-actions.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Product Custom Property`** (4 nodes): `product-custom-property.js`, `ProductCustomProperty`, `.handleInput()`, `.#updateCharacterCount()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Rich Text Formatter`** (4 nodes): `rte-formatter.js`, `RTEFormatter`, `.connectedCallback()`, `.#formatTable()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Copy to Clipboard`** (3 nodes): `CopyToClipboardComponent`, `.copyToClipboard()`, `copy-to-clipboard.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `QR Code Image`** (3 nodes): `qr-code-image.js`, `QRCodeImage`, `.connectedCallback()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Search Page Input`** (3 nodes): `search-page-input.js`, `SearchPageInputComponent`, `.#submitEmptySearch()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Video Background`** (3 nodes): `video-background.js`, `VideoBackgroundComponent`, `.connectedCallback()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Blog Posts List`** (2 nodes): `BlogPostsList`, `blog-posts-list.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Cart Note`** (2 nodes): `CartNote`, `cart-note.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Caret & Double Chevron`** (2 nodes): `Down caret (14x14)`, `Double chevron (up and down)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `In-stock Checkmark`** (2 nodes): `Available / in-stock checkmark (green)`, `Checkmark icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Left Right Chevrons`** (2 nodes): `Chevron left (8x12)`, `Chevron right (8x12)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Close X Icons`** (2 nodes): `Close X icon (14x14)`, `Filters-close small X (7x8)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Grid Density Icons`** (2 nodes): `Grid 2x2 view icon (default density)`, `Grid 3x3 view icon (dense density)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Plus Minus Icons`** (2 nodes): `Minus Sign Icon`, `Plus Sign Icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Play Pause Icons`** (2 nodes): `Pause Icon`, `Play Icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Accordion & Auto-Close`** (2 nodes): `AccordionCustom (details/summary wrapper)`, `AutoCloseDetails (global details click-closer IIFE)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `QR Code Pipeline`** (2 nodes): `QRCode class (3rd-party qrcodejs port)`, `<qr-code-image> custom element`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Volume Pricing Module`** (2 nodes): `VolumePricingInfoComponent (popover body with quantity-tier highlight, triggers parent anchored-popover-component ref refresh)`, `VolumePricingComponent (expandable pricing-tier table, simple class toggle)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Add to Cart Icon`** (1 nodes): `Add to cart icon — bag with plus`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Arrow Icon`** (1 nodes): `Right arrow icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Checkmark Burst`** (1 nodes): `Checkmark with burst animation (8 lines, animated)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Delete Icon`** (1 nodes): `Delete / trash icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Discount Icon`** (1 nodes): `Discount / price tag icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Error Icon`** (1 nodes): `Error icon — red circle with exclamation`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `External Link Icon`** (1 nodes): `External link icon (box with arrow)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Filter Icon`** (1 nodes): `Filter icon — funnel-like horizontal sliders`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Info Icon`** (1 nodes): `Info Icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `One Column Mobile Icon`** (1 nodes): `Single Column Mobile Layout Icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Reset Icon`** (1 nodes): `Reset/Clear Circle-X Icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Search Icon`** (1 nodes): `Search Magnifier Icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Shopify Logo Icon`** (1 nodes): `Shopify Logo Icon`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Slideshow Select Event`** (1 nodes): `SlideshowSelectEvent`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Cycle Focus`** (1 nodes): `cycleFocus`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Custom Property Counter`** (1 nodes): `<product-custom-property-component> char counter`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Product Title Truncation`** (1 nodes): `<product-title> responsive -webkit-line-clamp`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `RTE Table Wrapper`** (1 nodes): `<rte-formatter> table wrapper injector`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Scroll Hint`** (1 nodes): `<scroll-hint> fade-mask custom element`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Video Background Loader`** (1 nodes): `VideoBackgroundComponent (sets video src from dataset, triggers videoElement.load)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **What is the exact relationship between `Inventory Status Dot Icon` and `CartDiscount (apply/remove discount codes)`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._
- **What is the exact relationship between `Hamburger Menu Icon` and `AnchoredPopoverComponent (popover anchor + CSS-var positioning)`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._
- **What is the exact relationship between `Orders Clipboard Icon` and `CartDrawerComponent (Dialog + history state)`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._
- **What is the exact relationship between `Out-of-Stock Red X Icon` and `CartItemsComponent (quantity/discount/morph pipeline)`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._
- **Why does `closest()` connect `Facet Filtering` to `Cart Drawer`, `Deferred Media Player`, `Cart Quantity Selector`, `Localization Dropdown`, `Custom Accordion`, `DOM Morph + Hydration`, `Product Card`, `Layered Slideshow`, `Mobile Header Drawer`, `Desktop Header Menu`, `Volume Pricing Display`?**
  _High betweenness centrality (0.200) - this node is a cross-community bridge._
- **Why does `preventDefault()` connect `Cart Quantity Selector` to `Facet Filtering`, `Cart Drawer`, `Quick Order List`, `Custom Accordion`, `Collection Links Tabs`, `Product Card`, `Layered Slideshow`?**
  _High betweenness centrality (0.122) - this node is a cross-community bridge._
- **Are the 43 inferred relationships involving `closest()` (e.g. with `.#updateSection()` and `.sectionId()`) actually correct?**
  _`closest()` has 43 INFERRED edges - model-reasoned connections that need verification._