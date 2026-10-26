# Web

The open web as a channel: practitioner posts, articles, LinkedIn and Substack write-ups, agency and tool blogs, comparison pieces, docs. Lead channel for **how a kind of person does a thing, why, and with what** — workflow narration, motives, the tools and artefacts a practice actually names — and for the vocabulary a niche uses, which no single platform holds and which the platform digs need before they can be asked well. Also the fact-check channel: a claim from any other dig can be verified here. And the home of three composed tasks that are recipes rather than venues — independent reviews of a named product, competitor discovery, a deep-dive on one named competitor (**Task recipes**, below — two run as a `web` dig, competitor discovery is the main agent's own sweep). Weak for confession-grade complaint (that's Reddit) and for a brand's live buzz (that's X).

## Evidence weight — know what you're holding

Search results are **pointers, not evidence**: a title, a URL, a snippet. Nothing is quotable until `web_fetch` (or, for a reddit thread or X post, `read_social_post`) has returned the page and you are reading its actual text. Two search tools, different strengths:

| Tool | Finds | Best strings |
|---|---|---|
| `web_search` (Google via Serper) | pages whose words match | title-shaped: a first-person process account's title, a role paired with its task, an entity-versus-entity comparison; scope with `site` to a professional network, newsletter platform, community, or launch index (e.g. `linkedin.com`, `substack.com`, `reddit.com`, `producthunt.com`) |
| `exa_search` (semantic) | pages whose *meaning* matches | a plain description of the page you want — who the author is, what they are doing or leaving, in first person; `include_domains` to scope venues, `start_published_date` to stay recent |

Both return ≤20 rows. Weight what you fetch by what it is (SKILL.md's evidence-type order): a practitioner narrating their own workflow in first person outranks a how-to article, which outranks a vendor blog. Vendor and agency posts are fine as evidence of *what people name* (which tools, which artefacts, which words) and useless as evidence of *value* — self-claim, per the disciplines.

## 1. Query

Fan the ask (query-craft.md): one lead string at full depth, one to three escorts light. Mix the two tools when the ask has both a keyword shape and a meaning shape. Write for how content is titled, never for how the question is asked; no temporal or meta words. On a brand-less ask, no brand-anchored strings.

Cap the pass around 4–6 searches; past that you are collecting, not ranking. (These numbers are a dig pass's. On a light pull the whole visit — searches and fetches together — stays inside the light cap: 1–2 searches, 2–3 fetches.)

## 2. Fetch

From the combined results pick the ≤6 pages most likely to hold first-person or concrete process voice — read the snippet, weigh the domain (a personal blog or LinkedIn post over a listicle), skip obvious SEO roundups unless the ask *is* "what does the market say". `web_fetch` each; an obstacle (`paywall`, `login_wall`, `js_rendered`, …) is a page not read — drop it or find the same voice elsewhere, never quote from a snippet. A hit that is a reddit thread, a single X post, or a LinkedIn post (a `site:reddit.com` / `site:x.com` / `site:linkedin.com` search lands these) is read with `read_social_post(url)` — full text plus top comments in one call; `web_fetch` forwards those URLs there itself, so either name works, but never try to make a `mine_*` search re-find a post you already hold the URL for.

## 3. Rank and attribute

- Quote verbatim from the fetched text; the finding is the passage plus who said it and where.
- Source strings name the venue and the author as the page states them — the platform, the author's name and role, the publication and date, whichever the page carries. Missing author → the domain plus the content type; never invented.
- Convergence ranks: three independent practitioners naming the same tool or the same reason outrank one polished article. Same event, same slot.
- Promotional pages rank nowhere as findings — but a *pattern* in what vendors claim (a whole category converging on the same promise) is a real observation about the category and can be reported as that, sourced.

## Task recipes

Three asks arrive often enough to be worth a recipe, and none of them is a venue — each is a composition over the four tools above. §2 and §3 hold on every one: fetch before you quote, verbatim, source mandatory, self-claim isn't evidence. What a recipe replaces is §1 — its battery *is* the pass.

A digger holds **ten turns, one tool call each**, and nothing it gathered reaches the main agent unless the run ended on `submit_dig_result`. So each recipe below states **who runs it** and **how many calls it takes**, and every count leaves the terminator its turn. A recipe that does not fit inside one dig is **split by the main agent** — into several sequential digs, or run by the main agent itself — never stretched by the digger.

Throughout, `{category}` is **the category in the community's own words, as the brief states it** — how buyers and users name the thing — never an internal label. Keep review-seeking searches year-scoped for freshness. `site:` operators go in the query string or in `web_search`'s `site` argument, whichever reads cleaner.

### Independent reviews

Third-party written assessments of a named product: launch positioning, review articles, comparison roundups, aggregator complaints. The whole value is **independence** — check who runs the domain before treating a page as third-party. A vendor's own why-we're-the-best page, found through a review query, is self-claim, not a review.

**One `web` dig.** Inside it: 2 searches (review articles; ProductHunt-scoped for software), fetch the 3–4 most independent pages, submit — six or seven of the ten turns. G2/Capterra only when the product has a listing, in place of one article fetch.

- **ProductHunt** (software): the product name scoped to the launch index — keep the top handful, for launch-day positioning and early-adopter reactions.
- **Review articles**: the product name joined to review vocabulary, year-scoped for freshness. Fetch the most independent of them, within the budget above, and pull **verbatim passages**; a snippet is rarely quotable evidence.
- **Structured review sites** (G2, Capterra) when the target has a listing: its **4★ reviews are the gold seam** — customers who like the product and still have complaints. The listing's own question structure does the sorting: what reviewers like best is their strengths, what they dislike is the openings, what problem they were solving is the job the customer hired it for. These wall harder than article pages; a blocked fetch is a failed fetch to report, not an empty channel.
- **Skip** social domains — Reddit, X, YouTube each have their own handbook — and login-walled marketplaces (a storefront that serves a sign-in wall serves no reviews).
- **Rank by domain authority.** Top: major tech and business press, and software indexes — TechCrunch, The Verge, Wired, PCMag, CNET, Forbes, Bloomberg, ProductHunt, G2, Capterra, GetApp, and peers. Long-tail: personal-blog platforms — Medium, Substack, WordPress, Blogspot. Everything else mid. Ranking only, as everywhere.
- Source strings: the domain and the content type — a review article, a launch thread.

Few independent articles, or only promotional pages, is often the real state of a young or niche product — after at most one re-angle (comparison framing, or a competitor's name), report that plainly.

### Competitor discovery

"Who else is out there?" — expanding the map. **Run by the main agent directly — not a dig.** The result is a candidate table, not quotes, and `submit_dig_result` cannot carry it. A real competitor shows up in more than one place; a blog's pet mention doesn't.

Run the same four intents across each source family: the category's best-of roundups (year-scoped) · alternatives-to-the-product asks · versus-comparisons on the product · direct competitor queries.

| Source family | How |
|---|---|
| General web | the four intents as-is |
| Reddit | `web_search` with `site:reddit.com` — Exa has delisted reddit.com, so semantic search is blind there; run the alternatives and versus intents through the keyword tool instead |
| YouTube | `site:youtube.com` — comparison and best-of videos |
| X | `mine_x_twitter` on the alternatives-ask shape (the product name with alternative-seeking vocabulary), then `read_social_post` on the 1–2 asks with the most replies — the reply threads name entrants; the asks themselves rarely do |
| Software category indexes (software products) | `site:g2.com`, capterra, getapp |

**Budget:** the four intents on general web (4 searches) + `site:reddit.com` on alternatives and versus (2) + one software-index search when the product is software (1) — **≈ 6–8 searches**, a `site:youtube.com` pass or the X alternatives-ask family (1 search + 1–2 thread opens) fitting at the top of that range when they're likely to name entrants. Each one is a priced call, so a vague ask gets the short confirm before the spend, as anywhere else.

X never leads this sweep — a name-anchored search cannot surface a brand you can't name; its alternatives-ask reply threads contribute candidate names as one family among the others, tallied the same way.

Then:

- Dedupe by URL across the whole sweep, and extract candidate brand names from titles and snippets — list articles, versus titles and index pages are richest.
- **Tally cross-source presence** per candidate: how many independent source families surfaced it. That tally *is* the ranking — a name appearing across web roundups, Reddit threads and a category index is a market-validated candidate; a name from one clever blog post is trivia. Keep the evidence URLs per candidate; the user may want to look.
- Every name comes back a **candidate flagged for core-job overlap**, never a confirmed competitor. Judge from its capabilities and positioning as far as you can read them, and say which kind of rival it is: the same solution to the job, or a different solution shape entirely (the workaround, the manual way, the adjacent-category tool) that the buyer weighs all the same. An adjacent tool overlapping on one feature is worth noting as adjacent, not tracking as a competitor. Its marketing copy is self-claim — confirmation comes from independent evidence, usually a follow-up deep-dive on the 1–2 strongest.
- **Present the ranked candidates** with their cross-source tallies and evidence URLs, and let the user pick who is worth a deep-dive or a place in the monitored set — tracking a competitor is their call, not yours. Whether a candidate advertises on Meta is a check, not a commitment: the Ad Library probe on the name reports its Ad Library page and live posture — active-ad count and the domains its ads land on — monitoring nothing, so run it on any candidate the user wants sized up, tracked or not (each check is a priced call like any search in this battery). A name the Ad Library has no page for is itself a finding worth saying: that competitor is not advertising on Meta, so the swipe and the organic grid are where its presence would show, not the competitor-ad surface. When the user picks names to track, check first, then add each to the monitored set by its name and chosen page — the probe's landing domains held against the brand's own domain settle same-name pages, with the sweep's category and positioning as the remaining tiebreakers — ask only when they don't settle it. Both the probe and the add are main-agent tools; a digger holds neither, which is one more reason this sweep is never a dig.

**One sweep, then stop.** The battery is fixed — running it again returns the same map. A thin candidate list is a real answer (a genuinely sparse category, or one these angles don't reach), not a reason to re-run: report it and name the stronger next move.

### Competitor deep-dive

Everything public on one **named** competitor: positioning, what users complain about, switching language, and the opening it creates. Run it on competitors the user tracks, or on the strongest candidates out of a discovery sweep. A deep-dive does not add anyone to the monitored set; if the user wants the name tracked after reading it, that is the one-line ask above.

**One `web` dig, one name per dig** — the battery below is 4–5 searches + 1–2 fetches + submit = 6–8 of the ten turns, leaving room for at most one re-angle or one extra fetch — nothing more. Two competitors are two sequential digs the main agent ranks across; deep-diving five in one turn is a spend decision the user should make knowingly.

- **Keyword rounds**: reviews of the name; versus-comparisons on the name; the name joined to complaint vocabulary.
- **ProductHunt round** (software products): the name scoped to the launch index.
- **Semantic round** (`exa_search`): a plain description of users leaving the product — frustrated, disappointed, switching to alternatives. Leaving-language is phrased too many ways for keywords; this is semantic search's home game.
- **Page pull**: fetch 1–2 **independent** review pages for verbatim passages. Skip the competitor's own domain (self-claim) and social domains (their own handbooks apply).

Bucket the harvest:

- **Complaints** — the objection patterns, verbatim with source.
- **Loves** — what keeps their users; this is what any positioning against them must survive.
- **Switching language** — markers: *switched*, *moved from*, *used to use*, *replaced*, *came from*, *left X for*. Directional gold: who they lose users to, and who loses users to them.

Category-wide customer voice that surfaces along the way goes back as a finding for the customer-side node it belongs to, clearly labeled — but don't spend a call searching for it here; that is a `reddit` dig.

Two disciplines bite hardest here. Substantive claims about their value or positioning need **2+ independent sources**; their own site only ever supports *"they describe themselves as…"*. And a complaint pattern is a pattern when it recurs across sources — one angry review is a quote, not a pattern. Say which you are presenting.

## Thin harvest: one re-angle, then stop

Thin usually means the words: re-angle once with the phrasing the first pass surfaced — the community's own name for the thing, not the analyst's — or switch tools (semantic when keyword search returned listicles; keyword when semantic drifted). Then report plainly, naming what was searched.

## Error is not empty

A search tool returning `PROVIDER_FAILED` / `NOT_CONFIGURED` is a channel failure to report, never "nothing on the web about this".
