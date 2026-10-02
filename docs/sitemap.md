# Sitemap v2 — page tree, templates and content blocks

Text mirror of the Octopus.do project "Brew Society — Sitemap v2" (id `is4m3g73wo9`), which is the editable source of truth. Keep this file in sync when the Octopus project changes. Earlier FigJam sketch (v1, superseded): https://www.figma.com/board/DPYLHR2LWPpg4tRnK4Tn0y

Legend: `→ Pepper` = external link to the wholesale ordering portal. `[TBC]` = client decision pending.

## Principle: one data model, two entry points

Every brand and every product type is a Shopify **collection**, distinguished by a `type` metafield (brand / category). Two collection templates render them. The nav offers two ways in:

- **Brands** → catalogue grouped by brand under product-type headings. Business intent. Leads with "Order wholesale on Pepper".
- **Shop** → Shopify's built-in all-products collection on the category template, with native filters. Consumer intent. Leads with add to cart.

Budget is tight ($10k), so there are **six designed templates** plus shells. Everything else is a restyled Shopify default.

## Page tree

```
Home                                                /
├── Brands (catalogue by brand)                     /collections            list-collections template
│   └── Brand collection (template, ×35)            /collections/<brand>    collection.brand.json
├── Shop (all products)                             /collections/all        collection.json
│   ├── Category collection (template, ×6)          /collections/<type>     collection.json (same as Shop)
│   └── Buy panel — modal + product page            /products/<handle>      product.json; quick-add modal from any grid
│       └── Cart drawer                             (/cart exists, restyled minimally)
│           └── Checkout (Shopify)                  /checkout
├── Wholesale                                       /pages/wholesale        page.json (generic)
├── About [TBC]                                     /pages/about            page.json (generic)
├── Contact                                         /pages/contact          page.contact.json (generic + form)
├── Utility (Shopify defaults, restyled)
│   ├── Search                                      /search
│   ├── Account / Login                             /account
│   ├── Policies                                    /policies/*             page.json (generic)
│   └── 404
└── External
    └── Pepper wholesale portal                     URL TBC
```

Header: logo · Brands · Shop · Wholesale · Contact · search · cart (opens drawer) · **Order wholesale** button (→ Pepper).
Footer: who-we-supply sentence (independent retail, food service, corporate and office, VIC and NSW) · contact details · Order wholesale (→ Pepper) · Shop · Brands · policies · Instagram [TBC, account access].

## Templates to design (6)

| # | Template | Used by | Notes |
|---|---|---|---|
| 1 | Home | `/` | Two-CTA hero, exclusive brands, logo strip, how wholesale works, testimonials, contact CTA |
| 2 | Catalogue by brand | `/collections` | Brand cards grouped by product type, Exclusive row first, anchor nav. No filter JS |
| 3 | Brand collection | 35 brand collections | Brand hero from metafields, Pepper primary, product grid with quick add |
| 4 | Category collection | Shop + 6 type collections | Header variant of 3. Native Shopify filters (type, brand). Add to cart primary |
| 5 | Buy panel | quick-add modal + `/products/*` | One component. Modal from any grid; product page = panel + description |
| 6 | Generic page | Wholesale, About, Policies, Contact | Sections the client can reorder. Contact adds the form |

Shells: header, footer, cart drawer. Not designed, restyled Dawn defaults: search, account, 404, checkout (branding only).

## Blocks per page

### Home `/`
1. Hero — importer + distributor statement; two equal CTAs: **Order wholesale** (→ Pepper) and **Shop direct** (→ /collections/all).
2. Exclusive brands — brand cards tagged "Exclusive to Brew Society". → brand collections.
3. Plus many more — logo strip of other distributed brands. Marquee or static [design call].
4. Why Brew Society — four proof points, one line each, no slogans (Dawn multicolumn): exclusive brands you cannot range elsewhere; built for independent retail; pricing within 24 hours then order online on Pepper; reliable delivery across VIC and NSW. Draft claims, client to confirm.
5. Who we supply — one sentence.
6. How wholesale works — ABN, $300 minimum, order on Pepper. "Prefer to talk? Pricing within 24 hours." → Contact.
7. Testimonials — 3 to 6 real quotes.
8. Contact CTA — "How can we help?" → Contact.

### Brands (catalogue) `/collections`
1. Page header — title, one line, anchor nav to product-type groups (Alt milk, Confectionery, Pantry, Drinks, Coffee, Tea & chai, Snacks, Packaging).
2. Exclusive to Brew Society — first row of brand cards, exclusives only.
3. Brands grouped by product type — one row per type. A brand in two types appears in both.
4. Stock these brands — Order wholesale (→ Pepper) · Get pricing (→ Contact) · "Shopping for home? Browse all products" (→ /collections/all).

### Brand collection `/collections/<brand>` (template)
1. Brand hero — logo, name, tags (type, Exclusive, Imported / Local), summary, **Order wholesale on Pepper** primary, *Get pricing* secondary. From collection metafields.
2. Brand media — image or video, optional.
3. Products (quick add) — product cards with quick-add → buy panel modal. Native filters by type. Hidden when no D2C products.
4. More exclusive brands — card strip.

### Shop `/collections/all` and Category `/collections/<type>` (one template)
1. Page header — title, one line (cartons only, no minimum). Category pages: type name + intro.
2. Native filters — Shopify Search & Discovery: product type, brand, availability.
3. Product grid (quick add) — image, brand, name, carton size, price, Exclusive tag, quick-add → buy panel.
4. Wholesale nudge — "Buying for a business? Order wholesale on Pepper."

### Buy panel — modal and `/products/<handle>`
1. Buy panel (this is the modal) — gallery, brand (→ brand collection), title, carton size and units per carton, price, variant if any, quantity, **Add to cart** (opens drawer), secondary **Order wholesale on Pepper**.
2. Description — product copy. Standalone page only.
3. More from this brand — card strip. Standalone page only.

### Cart drawer
Slide-in: line items with carton quantities, subtotal, Checkout. Wholesale nudge below. `/cart` page restyled minimally.

### Wholesale `/pages/wholesale` (generic page template)
1. Intro — who it's for.
2. Why Brew Society — same four proof points as Home, reused. Optional supplier line: "Looking for an Australian distributor for your brand? Get in touch." [TBC]
3. How it works — ABN, $300 minimum, order via Pepper, VIC and NSW delivery.
4. Order wholesale — primary CTA → Pepper.
5. New account or larger range? — pricing within 24 hours → Contact.
6. Exclusive brands — logo strip.

### About `/pages/about` [TBC] (generic page template)
1. Who we are. 2. Brands we work with (logos). 3. Contact CTA.

### Contact `/pages/contact` (generic page template + form)
1. Intro — "How can we help? Pricing within 24 hours."
2. Form — name, business, email, phone, message. No category radios, no map. Captcha on.
3. Direct details — email, phone, address, hours.
4. Already set up? — Order on Pepper →.

### Utility
Search, Account, Policies (generic page template), 404, Checkout: Shopify defaults restyled, no bespoke blocks.
