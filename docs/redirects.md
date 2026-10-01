# Redirect map (draft)

Applies at launch when `www.brewsociety.com.au` becomes the Shopify primary domain and `shop.brewsociety.com.au` redirects to it. Source: Ahrefs crawl of both hosts, September 2026. Organic traffic is negligible everywhere except the Prana Chai product page, so this is about not breaking links and ad destinations, not SEO preservation.

## Webflow marketing site → Shopify

| From (`www.brewsociety.com.au`) | To |
|---|---|
| `/` | `/` |
| `/brands` | `/collections/brands` |
| `/services/<brand-slug>` (35 pages) | `/collections/<brand-handle>` — handles mostly match the Webflow slugs; map individually once the brand list is final |
| `/wholesale` | `/pages/wholesale` |
| `/contact` | `/pages/contact` |
| `/society` | `/pages/about` (or `/` if About is dropped) |
| `/industries`, `/industries/cafes`, `/industries/coffee-roasters`, `/industries/office`, `/industries/restaurants-hotels` | `/pages/wholesale` |
| `/checkout`, `/order-confirmation`, `/paypal-checkout`, `/search` | `/` (Webflow ecommerce leftovers, no value) |

## Shopify store on the old host → same paths on the new host

Shopify handles the host-level redirect itself once the primary domain changes. Product and collection handles stay the same, so no path rewrites are needed. Only these change:

| From (`shop.brewsociety.com.au`) | To |
|---|---|
| `/collections/home-beverages` (currently titled "Tea Culture™") | `/collections/tea-culture` — rename handle, add redirect |
| `/collections/coffee-1` (Frederick's Coffee) | `/collections/fredericks-coffee` — rename handle, add redirect |
| `/collections/home-page` | `/` |
| `/products/prana-chai` | **unchanged** — the one URL with real organic traffic (ranks #4 for "prana chai 1kg") |

Products removed from the catalogue (e.g. Vivani single units, if the client confirms) redirect to their brand collection.
