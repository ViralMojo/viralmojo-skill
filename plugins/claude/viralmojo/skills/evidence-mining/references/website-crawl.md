# Website crawl

What a brand says about itself, at the source: positioning language, pricing, features, self-claimed audience, competitors the brand itself names — plus structural leads other channels build on. Works on the user's brand and on competitors alike.

## Everything here is self-claim

The crawl's output supports *"they describe themselves as X"* and factual self-statements — pricing, named features, published roadmap. It is **never** independent evidence of value, quality, or differentiation; those claims need 2+ independent sources from other channels. Quote the brand's language verbatim — how a brand words its own promise is itself evidence, but only of what they say.

## 1. Crawl with priorities

Fetch the base URL, then walk the site's links with a priority order — the goal is the few pages that carry positioning, not the whole site:

- **First**: pricing, features, comparison ("vs"), case-study pages.
- **Second**: use-case, changelog, shop, product pages.
- **Skip**: blog, careers, legal, privacy, press, login/signup, terms, about, contact, support, docs, API/developer pages.

Cap the pages fetched — a handful of the right pages beats an exhaustive crawl, and every fetch costs.

## 2. What to read out

- Positioning and one-liner language, **verbatim**.
- Pricing lines and plan structure.
- Feature names in the brand's own vocabulary.
- Competitors the brand itself names (comparison pages are a gift — the brand telling you who it fears).
- **Structural leads**: an App Store link (feeds `references/app-store.md`); non-English localizations and currency cues (drive the App Store country expansion — Chinese → cn/tw, Japanese → jp, EUR → de/fr).

## Blocked or empty sites

A site that returns no usable content is usually a JS-rendered single-page app. Try the alternate fetch path once; if it still comes back empty, that's a channel obstacle to report plainly — the user pasting text or a screenshot is the workaround, not scraping tricks.
