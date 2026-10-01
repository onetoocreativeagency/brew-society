# Sitemap v1 — page tree and content blocks

Structured version of the sitemap for pushing into Octopus.do (pages, nesting, blocks) and for page-level wireframes in Figma. Mirrors `brief.md` §5 and the FigJam board: https://www.figma.com/board/DPYLHR2LWPpg4tRnK4Tn0y

Legend: `→ Pepper` = external link to the wholesale ordering portal. `[TBC]` = client decision pending.

## Page tree

```
Home                                   /
├── Brands                             /collections/brands
│   └── Brand page (template, ×35)     /collections/<brand>
├── Shop                               /collections/all
│   ├── Category (template, ×6)        /collections/<category>
│   └── Product page (template)        /products/<handle>
│       └── Cart                       /cart
│           └── Checkout (Shopify)     /checkout
├── Wholesale                          /pages/wholesale
├── About [TBC]                        /pages/about
├── Contact                            /pages/contact
├── Utility
│   ├── Search                         /search
│   ├── Account / Login                /account
│   ├── Policies (shipping, returns, privacy, terms)   /policies/*
│   └── 404
└── External
    └── Pepper wholesale portal        URL TBC
```

Header: logo · Brands · Shop · Wholesale · Contact · search · cart · **Order wholesale** button (→ Pepper).
Footer: who-we-supply sentence (independent retail, food service, corporate and office, VIC and NSW) · contact details · Order wholesale (→ Pepper) · Shop · Brands · policies · Instagram [TBC, account access].

## Blocks per page

### Home `/`
1. Hero — headline stating importer + distributor of premium brands; two equal CTAs: **Order wholesale** (→ Pepper) and **Shop direct** (→ Shop).
2. Exclusive brands — grid of brand cards tagged "Exclusive to Brew Society" (logo, name, category). Link to Brands.
3. Plus many more — logo strip of other distributed brands (Milklab, BioPak, Tony's, Bonsoy, S.Pellegrino…). Marquee or static grid [design call].
4. Who we supply — one sentence: independent retail, food service, corporate and office across Victoria and NSW.
5. How wholesale works — three steps: ABN, $300 minimum, order on Pepper. Secondary line: "Prefer to talk? Pricing within 24 hours." → Contact.
6. Testimonials — 3 to 6 real quotes with name and business.
7. Contact CTA — "How can we help?" short form or button → Contact.
8. Footer.

### Brands `/collections/brands`
1. Page header — title, one line on what the directory is.
2. Filters — category (Tea & chai, Drinking chocolate, Coffee, Soda & drinks, Alt milk, Snacks, Chocolate & confectionery, Kids, Packaging), Exclusive only toggle, channel (Retail / Food service).
3. Brand grid — cards: logo, name, category, Exclusive tag, import status. Exclusive brands sort first.
4. Stock these brands — CTA band: Order wholesale (→ Pepper) · Get pricing (→ Contact).

### Brand page `/collections/<brand>` (template)
1. Brand hero — logo, name, tags (category, Exclusive to Brew Society, Imported / Local), one-paragraph summary.
2. Brand media — image or video, optional.
3. Available direct — product grid of this brand's D2C cartons. Hidden when the brand has no D2C products.
4. Stock this brand — Order wholesale (→ Pepper, deep link if available) · Get pricing (→ Contact).
5. More exclusive brands — strip of other exclusive brand cards.

### Shop `/collections/all`
1. Page header — title, one line: cartons only, no minimum, shipped Australia-wide [TBC shipping scope].
2. Category chips — the six category collections.
3. Product grid — cards: image, brand, name, carton size, price, Exclusive tag.
4. Wholesale nudge — "Buying for a business? Order wholesale on Pepper."

### Category `/collections/<category>` (template)
Same as Shop with the grid pre-filtered and a category intro line.

### Product page `/products/<handle>` (template)
1. Gallery.
2. Buy box — brand (links to brand page), title, carton size and units per carton, price, quantity, Add to cart.
3. Description — product copy from the brand.
4. Wholesale nudge — "Buying for a business? Order wholesale on Pepper."
5. More from this brand — product strip.

### Wholesale `/pages/wholesale`
1. Intro — who it's for: retailers, cafes, restaurants, offices.
2. How it works — ABN required, $300 minimum order, order online via Pepper, delivery areas (VIC and NSW).
3. Order wholesale — primary CTA → Pepper.
4. New account or larger range? — pricing within 24 hours → Contact.
5. Exclusive brands — short strip.

### About `/pages/about` [TBC]
1. Who we are — importer and distributor, Melbourne, VIC and NSW. Two or three short paragraphs.
2. Brands we work with — logo strip.
3. Contact CTA.

### Contact `/pages/contact`
1. Intro — "How can we help? We'll get back to you with pricing within 24 hours."
2. Form — name, business, email, phone, message. No category radios, no map. Captcha on.
3. Direct details — email, phone, address, hours.
4. Shortcut — "Already set up? Order on Pepper."

### Cart `/cart` and Checkout
Shopify defaults restyled. Cart shows carton quantities and a wholesale nudge.

### Utility
Search, Account/Login, Policies, 404: Shopify defaults restyled, no bespoke blocks.
