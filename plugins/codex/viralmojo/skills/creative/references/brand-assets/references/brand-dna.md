# Building the Brand DNA doc

The Brand DNA doc is how the brand looks, written down precisely enough for an image model to reproduce it. An image model can't be told "make it feel like us"; it needs the typefaces, the hex values, the light, the surfaces and the label placement spelled out. The doc covers the visual half of the brand only.

Build it once, in `context/brand-assets/brand-dna`. Every image afterwards reads it, and nothing re-researches it.

## Research

Three sources, in this order. Nothing else is searched.

**1. The brand's site — `read_site_brand`.** Pass the site's address as `url`: the one on brand context's `website-and-product` page, or the one the user gave. Pass `product_urls` when the user named product pages. One call is usually enough; it fetches the home page, an about page, the product list, the stylesheets, and the pictures that matter, and you see those pictures in its result. What each part is good for:

- `colors.custom_properties` — the palette as the site declares it, exact hex; the names often say the role (primary, accent, background). An entry's `declared` is the value as the site wrote it when that was not a hex, and `source: inline style` means the page set it on one section — both are the site's own declaration. `read`.
- `colors.buttons` — the call-to-action fill and corner, exact: `source: page` entries are the home page's own buttons (with their label and how often they appear), ahead of the stylesheet's button rules, and `where` and `count` say why the first one leads; when a `buttons:` note says the page singles none out, name both and call neither primary. `colors.button_radius` is a radius the theme declares. `read`.
- `colors.most_used` — which colours lead in practice: a check on the declared palette, and the palette itself when nothing was declared. The count is how often, not what role; judge the role. `read`.
- `colors.theme_color` — the colour the brand picked for the browser bar. `read`.
- `site.read_through_reader` — pages the site would not serve directly and that came through a rendering reader instead; their text and pictures are sound. The stylesheets are still fetched directly, so the palette and typefaces stand unless a note says the stylesheets answered an HTTP error — then say they were not read rather than building a palette from what is left.
- `logo[].kind` — `logo` is the brand's mark, `icon` an app icon or favicon that is never kept as the logo; an entry carrying `logo[].load_error` could not be fetched and is not a file to keep. `read`.
- `products[].price_text` — the page's own price wording when no structured price exists ("From $399"); quote it as written and judge what it covers, never tag a number of your own as `read`.
- `fonts.faces`, `fonts.google_fonts`, `fonts.families` — the typefaces by name; `fonts.headings` and `fonts.body` say which is used where, when the site's rules say so. `read`.
- `fonts.custom_properties` — the theme's typeface tokens by name; `fonts.body_system_stack` means body text uses the visitor's system fonts, not a brand typeface. `read`.
- The pictures, named in order by `images_shown` (logo, share image, product photos) — photography direction, the product's physical details and packaging, and how the brand sets text on its own promotional images. `judged`.
- `products` — the product list: which products exist, what to offer folders for, and physical details a description states outright (material, size). Stated details are `read`.
- `pages` — the home and about text. Read it only for what it says about the look; positioning and voice are brand context's, not this doc's.
- `notes` — what the site did not yield. A client-rendered site, or no readable stylesheet, leaves colours and typefaces to the pictures and the user.

A refused or failed read (`UNSAFE_URL`, `UNREACHABLE`, `NOT_HTML`, `EMPTY`) is not charged. Go on with the photos and the user, and say the site couldn't be read.

**2. The photos on file — `view_image`.** Look at every kept product photo and the logo. They are the ground truth for the product's physical details (shape, material, finish, translucency, label layout) and a check on everything the site said. Where a kept photo and the site disagree about the product, the kept photo wins: the user put it there.

**3. The user.** For what neither gave. Guidelines the user hands over in chat (a document, pasted values, an image of a style sheet) are the user's word.

## What the doc holds

Every value says where it came from:

- **read** — declared by the site (its stylesheets or its product data), with the site's address;
- **judged** — from a picture, by eye: the site's or a kept photo;
- **given** — by the user.

A judged value comes from a picture you were shown in this build, or from the role you give a colour the read returned. Every hex comes from the read's colours or the user: a colour a picture shows takes the hex of the read's colour nearest it, when one is near; when none is, name the colour in words and leave its hex "not found" — one of the missing values to ask for. A picture's pixels can't be measured by eye, so a hex written for one comes from memory, for a well-known brand its published palette, and that passes for a read when it isn't one. When a field has no source at all, write "not found" rather than a plausible guess.

Five sections, in this order:

1. **Visual system** — primary and secondary typefaces, each named when known and always described (weight, width, serif or sans, any quirks), since an image model draws from the description, not the name; primary, secondary and accent colours with hex; background colours; the call-to-action colour and button style.
2. **Photography direction** — lighting, colour grading, composition, subject matter, props and surfaces, mood.
3. **Product details** — for each product with a folder in brand assets, or, when none has one yet, each product the site's pictures showed: physical description (shape, size cues, materials, colours, matte or gloss, translucency), where the label and logo sit, distinctive features, and how the packaging works across the range.
4. **Ad creative style** — how the brand sets text on its images, photography or illustration, how much it leans on customer-made content, how it presents an offer. The site's share image and promotional pictures hint at it; the user knows it. What neither shows is "not found".
5. **Style paragraph** — one paragraph of 50 to 75 words that goes in front of every image prompt. It describes the image the brand would make: the exact colours by name and hex, the typefaces by description, the light and grading, the surfaces, the mood. Write it as a description of the picture, not as instructions to a designer, and use only what the sections above settle; a "not found" field stays out of it.

## Writing it

Write the doc with `write_doc`. Then say in the reply what was read from the site, what was judged from pictures, and what wasn't found, and ask for the few missing values that matter most — usually the exact hex values and the typefaces, when the site didn't declare them. Close with the offers the site read opened: its pictures as the photos of a product that has none, its raster logo when none is kept.

A user's answer to those questions, or any later correction, is a scoped fix: apply it with `edit_doc` and mark the value `given`.
