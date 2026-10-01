# ONETOO Shopify Kit — Figma template

**File:** https://www.figma.com/design/1UrpX679KdVZKLM5BJl39b (ONETOO team drafts; move it into a "Templates" project). Base: Shopify Dawn 16.0.0. Frames: 1728 desktop, 390 mobile.

This is a template file, not a published library. Duplicate it per project so components can be modified freely, which matches the fork-and-modify dev approach. Brew Society is the first project built from it; the next Shopify store starts the same way. This doc belongs in a shared ONETOO repo eventually; it lives here until one exists.

## Structure

| Page | Holds |
|---|---|
| Cover, Read me | Purpose, how to start a project, rules |
| Tokens | Variable specimen: the four Scheme modes side by side, spacing bars, type/layout/shape tables |
| Foundations | Text styles (bound to Type variables) and effect styles, with Desktop and Mobile specimens |
| Primitives | 16 icons, `button` (Style × Size), `field-input` (states), `field-select`, `field-textarea`, `checkbox`, `badge`, `price`, `quantity-input`, `swatch`, `divider`, `breadcrumbs`, `pagination`, `filter-chip`, `link-list-item` |
| Cards | `card-product` (Quick add shown/hidden), `card-collection`, `article-card`, `card-logo` (bespoke, brand directories) |
| Global | `announcement-bar`, `nav-item`, `header`, `header-mega-menu`, `header-drawer`, `footer`, `cart-drawer`, `predictive-search`, `cart-notification` |
| Sections | Every Dawn 16 section (image-banner, slideshow, rich-text, image-with-text, multicolumn, multirow, collection-list, featured-collection, featured-product, collapsible-content, newsletter, email-signup-banner, contact-form, video, collage, featured-blog, related-products, apps, custom-liquid) plus bespoke `logo-list` and `testimonials` |
| Product & Collection | `main-collection-banner`, `main-collection-product-grid`, `facets-drawer`, `main-list-collections`, `main-product`, `quick-add-modal`, `main-search`, `main-cart`, `main-page`, `main-404`, `main-blog`, `main-article`, `disclosures` |
| Templates | One section per Dawn JSON template (index, collection, list-collections, product, page, page.contact, search, 404, cart, blog, article, password), desktop and mobile, composed from instances. Plus an example fuller homepage |
| Exploration, Presentation, Handoff | Project working pages. Dev reads Handoff only |

Page-wide components are variant sets `Viewport=Desktop | Mobile`. The Mobile variant switches the Layout and Type collections to Mobile mode, so gutters, header height and type sizes change with it.

## Variables (76)

| Collection | Modes | Contents | Code syntax |
|---|---|---|---|
| Primitives | Value | Raw colours (black, off-black, white, off-white, greys, accent, success, error, warning), `font/primary`, `font/secondary`. Hidden from pickers | none |
| Scheme | scheme-1 Light, scheme-2 Tint, scheme-3 Inverse, scheme-4 Accent | background, text, text-secondary, border, button, button-label, secondary-button-label, shadow, media-placeholder. Aliases to Primitives | Dawn: `rgb(var(--color-background))`, `rgb(var(--color-foreground))`, `rgb(var(--color-button))`, `rgb(var(--color-button-text))`, `rgb(var(--color-secondary-button-text))`, `rgb(var(--color-shadow))` |
| Type | Desktop, Mobile | family/heading, family/body (alias Primitives fonts); sizes micro 12/12, caption 14/14, body 16/16, body-lg 18/17, subhead 21/19, h5 24/21, h4 28/24, h3 32/27, h2 40/32, h1 48/36, display 61/44, display-xl 80/52; line-height, caps tracking | `var(--font-heading-family)`, `var(--font-body-family)`, `var(--theme-text-<size>)` |
| Spacing | Value | space/0 … space/256 | `var(--theme-space-N)` |
| Layout | Desktop, Mobile | viewport 1728/390, page-width, gutter 24/16, grid-gap 16/8, section-gap 96/64, header-height 88/64, announcement-height 40/36, columns 12/4, product-columns 4/2 | `var(--page-width)`, `var(--grid-desktop-horizontal-spacing)`, `var(--spacing-sections-desktop)`, `var(--header-height)`, `var(--theme-*)` |
| Shape | Value | radius/button, input, card, media, badge, popup; border/button, input, card, divider | Dawn: `var(--buttons-radius)`, `var(--inputs-radius)`, `var(--border-radius)`, `var(--media-radius)`, `var(--badge-corner-radius)`, `var(--popup-corner-radius)`, `var(--buttons-border-width)`, `var(--inputs-border-width)`, `var(--border-width)` |

`--theme-` is a placeholder prefix. Each project replaces it with its own (`nm-`, `bs-`) in `layout/theme.liquid`.

The Scheme collection maps one-to-one to Dawn's `color_scheme_group` roles. Setting a section instance's Scheme mode in Figma is the same decision as the section's colour scheme setting in the theme editor. Figma Pro allows four modes per collection, so the kit carries four schemes; Dawn ships five but the fifth is rarely used.

## Per-project steps

1. Duplicate the file, rename "<Client> — Website".
2. Tokens: set Primitives (palette, fonts), then the Scheme mode values, then Type sizes and Shape radii if needed. Text styles follow automatically.
3. Exploration: copy the Templates frames and design. Presentation: what the client sees. Handoff: frozen, one frame per Shopify template, desktop and mobile.
4. New bespoke sections: name them `<name>` in Figma with "Bespoke" in the description, and `<prefix>-<name>.liquid` in the theme.
5. Dev reads Handoff frames via the Figma MCP (`get_design_context` per section). Component names map to Dawn files directly.

## Known gaps (v0.1)

- Components are low-fi structure, not visual design. Inter is the placeholder typeface.
- `badge` instances inside cards show "Sale" because the Label property default was unified across the variant set. Set the label per instance.
- No Code Connect: Figma does not support Liquid. The naming convention replaces it.
- Customer account pages are not in Dawn 16 (new customer accounts are Shopify-hosted), so there are none here.
- Hover and focus states exist only on `field-input` and `nav-item`. Add per project if the design needs them.

## Brew Society specifics

Brew Society adds: `card-logo` grid grouped by product type for the catalogue (`main-list-collections` variant), brand hero on `main-collection-banner` with the Pepper CTA, and the `quick-add-modal` as the buy panel. See `docs/sitemap.md`.
