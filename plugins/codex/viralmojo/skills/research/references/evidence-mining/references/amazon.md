# Amazon reviews

Public buyer reviews of one Amazon listing: star ratings, the verified-purchase badge, helpful votes, and the "good but…" gap between what the listing promises and what arrived. The strongest objection channel for a physical product sold on Amazon — the brand's own or a competitor's. No listing, no channel.

## 1. Locate the listing

`mine_amazon_reviews` needs the listing's product URL or its ASIN. The brand's site often links its Amazon store; take the address from there. Without one, `search_amazon` with what a shopper would type — the brand and product name for a named listing, the category in buyers' words for the category's sellers — returns the page's products with their ASINs, sponsored flags, ratings and review counts. Read the rows before choosing: a sponsored slot is paid placement, not rank; a reseller's or a bundle's listing is not the brand's own, so match the brand and the product name, and skip a listing whose review count is near zero. Variants usually share one review pool, so one listing per product is enough. Pick the marketplace the brand sells in; an ASIN often lives on one marketplace only, and a read on the wrong one comes back empty.

## 2. The brand's own listing, or a competitor's

Decide whose listing it is before reading, and say so.

- **The brand's own listing** — its buyers' reviews are first-party customer evidence. Present them like any finding; when the user wants them kept, they go into the customer-reviews table through the customer-evidence skill's flow (report how many, wait for the go-ahead, then the same read with `keep_as_customer_reviews`, which skips reviews already in the table). Never keep without that go-ahead.
- **A competitor's listing** — research. Findings come back in chat and land in a doc only on request; a competitor's reviews never enter the brand's customer-reviews table.

## 3. Read the listing against its reviews

`with_product` adds the listing: title, brand, price, rating, review count and the bullet features. The bullets are the claims the seller chose to make; the reviews test them. A claim the complaints contradict is an objection to answer; a benefit the loves keep naming that the bullets never mention is unclaimed copy.

## 4. Read across the stars, then size it

The default read is stratified: about ten reviews from each star level, in one call, so the complaints and the "good but…" middle are there even on a listing most buyers rate five stars. `stars` reads only the levels asked — the 1–2★ levels when the question is what goes wrong, the 3★ level for the "good but…" gap — and a level holds at most ten pages. `sort` picks the order inside each level: `helpful` (the default — pre-validated by other shoppers) or `recent` (what changed lately: a reformulation, a supplier switch, a new defect). `verified_only` drops unverified reviews at the source.

The sample is drawn per level, so its split says nothing about the listing. The result opens with the listing's own totals — average rating, rating count, the share of ratings at each star and the written reviews behind each level read. Size every finding against them: an objection is a share of the listing's ratings, not of what came back. Say how much of a level the read covered.

Every review read is paid for, and each level asked takes at least one page. Ask for what the question needs: `stars` instead of all five when only one side matters, a `max_reviews` that matches the depth you will actually read. Repeating the same read returns the same reviews — change the order, the levels or the verified filter, or stop.

## 5. Bucket what you read

- **Complaints** — 1–2★: the raw objection material.
- **Three-star** — the "good but…" middle: praise that pivots, and the *"only thing I wish…"* lines also buried in 4★ text. The sharpest marketing signal in the channel.
- **Loves** — 4–5★ patterns: what actually lands, in buyers' words.
- **Switching language** — any rating that says where the buyer came from or went to.

## 6. Rank and attribute

- A verified purchase outranks an unverified review; within each, helpful votes rank. A review nobody voted for and nobody verified is long tail.
- Convergence beats volume: the same objection across many reviews outranks one long rant.
- Source strings name the listing, the marketplace, the star rating, verified or not, the helpful votes and the date.

## Thin harvest: one re-angle, then stop

A listing with few reviews has little to give — re-reading it will not manufacture more; a level with no reviews comes back empty, and that is a finding about the listing, not a failure of the read. Re-angle once (the marketplace where the product actually sells, or the brand's other listing of the same product), otherwise report the thin harvest plainly.
