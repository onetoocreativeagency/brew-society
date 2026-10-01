# Brew Society — website brief

Source: client workshop transcript (Harry and Matt from Brew Society, Marcel from ONETOO), the existing sites, and Ahrefs. Status: **draft for Marcel's review before any design work starts**. Items marked **TBC** need an answer from Marcel or the client.

## 1. The job in one paragraph

Replace three disconnected properties (Webflow marketing site at `www.brewsociety.com.au`, Shopify store at `shop.brewsociety.com.au`, Ordermentum wholesale ordering) with **one Shopify site** at `www.brewsociety.com.au`. The site is a B2B shopfront first: it tells independent retailers, food service operators and international brand owners that Brew Society imports and distributes premium brands in Victoria and NSW, shows the portfolio in a scannable way, and sends wholesale buyers to the Pepper ordering portal. Direct-to-consumer sales stay available (carton quantities only) but are secondary. Visually: clean, black and white, mobile-first, with colour coming from the brands themselves. Copy: concise and professional, no more challenger-brand slogans.

## 2. Business context

- Brew Society is an **importer, brand owner and distributor** of beverage and snack brands, based in Melbourne, distributing in Victoria and NSW. Decision from the workshop: the site says *importer and distributor*. It does **not** say *brand owner*; owned brands are presented as "exclusive to Brew Society" alongside imported exclusives.
- **Customers today**: food service (cafes, restaurants) is about 70% of revenue. **Strategic push**: independent retail (IGA-style grocers, Tully's, Seller & Pantry, Cicluna's). Corporate and office supply exists but is minor.
- **Secondary audience**: international brand owners deciding who distributes them in Australia. The client wants the site to look credible to them ("show, don't tell"). No dedicated supplier enquiry flow; the one contact form covers it.
- **D2C reality**: the Shopify store does roughly $8k/month, about 95% Prana Chai, found through price search. The client has no interest in paid customer acquisition for D2C. D2C exists so people can buy the imported brands that aren't yet on shelves, and so ad traffic has somewhere to land.
- **Ads**: the client will run low-budget Meta awareness ads (roughly $500–1000/month) for the imported brands once the site is live. Ad traffic lands on **brand pages**, so those pages are the most important template after the homepage.
- **Ordering**: wholesale moves from Ordermentum to **Pepper** (B2B ordering portal). Requirements: ABN, $300 minimum order. D2C on Shopify has no minimum but sells **cartons only** (inventory is tracked in cartons, and single-unit retail would undercut their retailer customers).
- Timing driver: a senior retail hire is being announced; the client wants Pepper, the website and the brand ads all live for that.

## 3. Positioning and copy direction

- Position: the distributor premium brands choose for Australia. Marcel's framing: "don't be the best, be the only". Translate into customer language, don't say it literally.
- Tone: professional, direct, still a challenger but "not lunatics". Less is more. Pull back the sales pitch; put the portfolio in front of people and make the next step obvious.
- **Kill**: "No more f-ups", "Help us help you", "Blood, sweat and tears", "Empathy over ego", "Fun to work with", "Bundle brands, save big", "The more you buy the more you save", "Meet the brands changing the game" (client doesn't believe it), the Society page and the word "society" as a concept, the Industries pages, the logo marquee of accounts they supply (half aren't customers).
- **Keep**: "Get pricing within 24 hours" promise (client liked it, and they do deliver on it).
- **Add**: a clear statement that they import; "exclusive to Brew Society" labelling; social proof via testimonials (real quotes only, client to supply) and the well-known brands they distribute (Milklab, BioPak, Tony's, Bonsoy, S.Pellegrino) even though those aren't retail-focused.

## 4. Audiences and primary actions

| Audience | What they need | Primary action |
|---|---|---|
| Independent retailer (new) | See the portfolio, understand exclusives, get pricing | Contact form ("How can we help?") → pricing in 24h |
| Cafe / food service (new or existing) | Order quickly | "Order wholesale" → Pepper (ABN + $300 MOQ) |
| Brand owner / supplier | Judge credibility: who they already distribute, that they import | Browse brands, contact form |
| Consumer | Buy a carton of a brand they already know (Prana Chai) | Shop → cart → checkout |

Mobile is 60–70% of traffic. One client stakeholder's parent is a reference user: everything must be obvious and foolproof, large tap targets, two clear CTAs on the homepage.

## 5. Site map (proposed)

```
/                         Home
/collections/brands       Brands directory (all brands, filterable)   ← see §6 for data model
/collections/<brand>      Brand page (one per brand)
/collections/all          Shop (D2C catalogue, cartons only)
/collections/<category>   Shop by category (tea & chai, drinking chocolate, soda, snacks, chocolate, coffee…)
/products/<handle>        Product page
/pages/wholesale          How to order wholesale (ABN, $300 MOQ, Pepper, pricing in 24h) + CTA to Pepper
/pages/about              Short "who we are" (replaces Society). Optional, TBC
/pages/contact            Contact — single free-text form
/cart, /checkout, /account, /search, /404, policies   Standard Shopify
→ Pepper portal           External link from header CTA, wholesale page, brand and product pages
```

Removed from the current site: `/society`, `/industries/*`, `/wholesale` (becomes `/pages/wholesale`), Webflow checkout pages, Ordermentum links.

Header: logo, Brands, Shop, Wholesale, Contact, cart icon, and a persistent **Order wholesale** button to Pepper. Footer: one-sentence "who we supply" (retail, food service, corporate and office across VIC and NSW), contact details, Pepper link, policies, Instagram if the client regains access to the account.

## 6. Brands directory and brand pages

This is the core of the B2B site and the landing surface for ads. Marcel's workshop proposal, agreed by the client: a structured, scannable list rather than a wall of logos. Per brand: logo, name, category, exclusive flag, origin/import status, one-line description. Filterable by category and "exclusive to Brew Society". Exclusive brands float to the top.

**Recommended data model: one Shopify collection per brand**, with collection metafields for the brand attributes. Why: brand pages then show D2C products natively when they exist, the URL is clean (`/collections/johnny-cashew`), and the client can edit everything in Shopify admin. Brands with no D2C products (BioPak, Milklab) still get a page: logo, description, category, "Order wholesale on Pepper" CTA, and an empty product grid that is simply hidden. Alternative considered: a `brand` metaobject with its own page template. More flexible but a second content model to teach the client and no native product listing. Go with collections unless Marcel disagrees.

Collection metafields (brand):

| Key | Type | Notes |
|---|---|---|
| `brand.logo` | file | Mono or full-colour, TBC in design |
| `brand.category` | list of single-line text | Tea & chai, Drinking chocolate, Coffee, Soda & drinks, Alt milk, Snacks, Chocolate & confectionery, Kids, Packaging… |
| `brand.exclusive` | boolean | Shows the "Exclusive to Brew Society" tag |
| `brand.status` | single-line text (choice) | `Imported exclusive`, `Local exclusive`, `Distributed` (owned brands appear as `Local exclusive`) |
| `brand.channels` | list | Retail, Food service — lets the client flag food-service-only lines |
| `brand.summary` | multi-line text | One or two lines, shown on the card |
| `brand.website` | URL | Optional |
| `brand.pepper_url` | URL | Deep link into Pepper if Pepper supports it, otherwise portal root. TBC |

Brand page template: hero (logo, name, tags, summary), optional image or video, products available direct (if any, cartons), "Stock this brand" block (Pepper CTA + contact form link), and a strip of other exclusive brands.

**Brands on the current site** (35, from `/services/*`): Allie's Juice, Alternative Dairy Co, BioPak, Bonsoy, Califia Oat, Chow Cacao, Coco Coast, Cocobella, Daelmans Stroopwafels, Dulwich Bakery, Famous Soda Co, Frederick's Coffee, FUNDAY Natural Sweets, Grumpy Bums, Happy Happy Soy Boy, Health Lab, Johnny Cashew, Karma Drinks, Milk Lab, Minor Figures, Nibana, Oatly, Ordinary Beverage Co, Prana Chai, Proper Crisps, S.Pellegrino, Shott, Simply Roasted, Smart Ass, Tea Culture, Tony's Chocolonely, Two Boys Brew, Vivani Organic Chocolate, Wallaby Water, Wild1.

Mentioned in the workshop but not on the site: Pernigotti, "Darwin's" (TBC spelling), "Hollies" (TBC). Owned brands, inferred: Tea Culture, Nibana, Grumpy Bums. Local partnerships named: Chow Cacao, Ordinary Beverage Co. **The client decides the final list and the per-brand attributes; we need this as a spreadsheet (see §11).**

## 7. Shop (D2C)

- Cartons only. Current store has single units for Vivani (100g bars, 40g snacks) alongside cartons; singles would be removed. **TBC with client** since Vivani singles currently sell.
- Current catalogue (about 70 live products): Tea Culture (loose leaf, pyramid infusers, chai, matcha, starter packs), Nibana drinking chocolate, Prana Chai 1kg and bundle, Frederick's Coffee beans and pods, Ordinary Soda 12-packs, Simply Roasted crisps 12-packs, Vivani chocolate cartons. To add: the imported exclusives (Johnny Cashew, Pernigotti, others TBC).
- Prana Chai is the one product with real organic traffic (ranks for "prana chai 1kg"). Keep the handle `/products/prana-chai` and keep the price positioning the client relies on.
- Product page: carton quantity and unit count clear in the title and a "units per carton" field, exclusive tag where relevant, add to cart, and a secondary "Buying for a business? Order wholesale on Pepper" link.
- No subscriptions, no wishlist, no reviews app unless the client asks. Collections by category plus the brand collections above.

## 8. Contact and lead handling

- One form, one free-text field ("How can we help?"), plus name, business, email, phone. No radio buttons for product categories (current form's options are stale). No map.
- Spam: the current Webflow form gets heavy spam. Shopify's native contact form has built-in captcha; that alone should fix most of it. Submissions go to the client's inbox as now.
- Response promise: "We'll get back to you with pricing within 24 hours."
- Routing guidance in copy: cafes can go straight to Pepper; retailers and larger accounts are invited to talk first.

## 9. Visual direction (for Figma)

- **Logo unchanged.** Client will not rebrand; vans and packaging carry the current mark.
- **Type**: keep the typeface tied to the logo. Marcel suggested adding a secondary face for contrast rather than replacing the primary. Font licensing status **TBC** before any self-hosting.
- **Colour**: lean into black and white, probably off-black and off-white rather than pure. Drop the red. The electric blue is likely dropped too; client is indifferent, so decide in design. Colour and vibrancy come from brand logos and product photography.
- **Feel**: clean, more "corporate" in the sense of credible and calm, not boring. Fine Food Merchant's new site was the liked competitor reference (suppliers section, testimonials, brand directory). Better Food Distribution and Feel Good Foods were seen as poor.
- Brand logo marquee: mixed views in the room. Keep as an option for the "plus many more" strip, decide in design.
- Mobile first. Homepage must present exactly two primary choices: order wholesale (Pepper) or shop direct.

## 10. Platform and build plan

- **Theme base**: Shopify Dawn, same approach as Nelson Made (fork and modify, bespoke files prefixed `bs-`, merchant-editable schemas, colour schemes for backgrounds). Pristine Dawn goes in as its own commit and is tagged `dawn-baseline` so the diff is always recoverable. **TBC**: Dawn vs Shopify's newer Horizon family; recommendation is Dawn.
- **Store**: reuse the existing Shopify store (keeps products, orders, customers, the Prana URL). New theme connected to `main` via GitHub; develop on `claude/*` branches. Preview via theme preview link.
- **Domain**: make `www.brewsociety.com.au` the Shopify primary domain at launch; `shop.brewsociety.com.au` redirects to it. Webflow site decommissioned. Redirect map in `docs/redirects.md`.
- **Integrations**: Pepper (external links only, no API), Meta pixel and GA4 for the ads, Shopify contact form. Klaviyo **TBC** (ONETOO has it connected; unclear if the client uses email marketing). Instagram feed only if the account is recovered.
- **Content the client maintains**: brand collections and metafields, products, testimonials (section blocks), homepage copy. Everything editable in the theme editor, labelled in plain language.

## 11. What we need from the client

1. **Brand spreadsheet**: every brand to appear, with logo file, category, exclusive yes/no, status (imported exclusive / local exclusive / distributed), channels, one-line description, website, and whether it has D2C products.
2. **Pepper**: portal URL, whether brand or product deep links exist, exact onboarding steps (ABN, $300 MOQ, approval time), and the go-live date.
3. **Testimonials**: 3 to 6 real quotes with name, business, and permission.
4. **Product list for D2C**: which imported brands go on sale direct, carton sizes, pricing, photography.
5. **Logo files and fonts** (with licence status), plus any product and lifestyle photography they hold or can get from the brands.
6. **Decisions**: drop the blue; keep an About page or fold it into the homepage; remove Vivani single units; keep the brand marquee.
7. **Access**: Shopify store collaborator access, Webflow access for the redirect export and decommission, DNS access for the domain move, Meta Business Manager if we set up the pixel.

## 12. Open questions for Marcel

- Budget mentioned in the room was around $10k. Confirm scope fits: homepage, brands directory, brand template, shop templates, wholesale, contact, about. Anything beyond that is a later phase.
- Who writes copy? The brief assumes ONETOO drafts, client approves. The brands spreadsheet needs client-written one-liners or we draft from brand sites.
- Figma: create a fresh Brew Society file from the Nelson Made structure, or do you want to start it? See the kickoff plan in the chat.
- Nelson Made CLAUDE.md conventions carry over mostly as-is. Anything you'd change for this build?
