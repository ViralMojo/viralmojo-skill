# Reddit

The richest unfiltered customer voice on the web. Lead channel for switcher language, confession-grade quotes, niche vocabulary, and honest complaints — people write things in throwaway-account threads they'd never put in a review. Weak when the category has no community presence; a thin harvest there is a real answer, not a failed dig.

## 1. Find the communities

Where this brand's customers talk is usually already on file — every saved Reddit quote carries its subreddit in its source string, and brand pages name communities — and on a dig those subreddits arrive in the brief, since a digger never sees the workspace. Before spending a discovery request, pass the subreddits the brief names as `subreddits`. Subreddits explicitly named on the brand's website, or that you already know from the ask, count the same way. Only when the brief and the ask name none does discovery run:

- Discovery runs **site-wide keyword search** on `discovery_queries` (default: your first 3 `queries`) and ranks candidate subreddits by how often the returned posts land in them — mention density, not first hit. User-profile pages (`u_*`) are skipped. The tool keeps the top 3.
- Give discovery strings that name the *community's* thing, not the brand's: for a named brand, the product name plus the category as buyers say it plus an alternatives-or-recommendations ask on the category; for a topic, the topic phrase plus the role or scene it lives in.
- If discovery skews to the brand's own subreddits, call again naming 2–3 category-peer communities in `subreddits` — switcher language and competitor complaints live where the category talks, not where the brand's fans gather.

No relevant subreddits at all → report thin signal and stop; don't force queries into generic subs.

## 2. Write the query set

You write every string; the tool runs each one verbatim against each of the top 3 subs. Order the list by evidence value — the return is grouped in that order, each query guaranteed a base quota of the ≤30 findings so a quiet steady-state query is never buried by a loud controversy query. Two recommended sets:

**Brand-anchored dig** (the ask is about a named product):

| Shape | Strings | What it surfaces |
|---|---|---|
| product | the product name alone, and joined to review and worth-it vocabulary | direct opinion on the brand |
| switching | leaving constructions aimed at the product name — the switching-marker verbs in query form — plus the versus form | switcher language — the highest-signal shape |
| experience | the product name joined to 3–4 everyday symptom words in the niche's own vocabulary — the sensory, physical, or functional complaints this kind of product draws | steady-state product-experience complaints that controversy threads bury; brand-name strings structurally miss these |
| problem | category-anchored pain phrasings — the category not working, alternatives-seeking, frustration vocabulary | pain in the category, brand-agnostic |
| category | the category alone, and its best-of form | vocabulary and framing |

**Topic-anchored dig** (the ask is about a behaviour, workflow, motive, or kind of person — no brand to name):

| Shape | Strings | What it surfaces |
|---|---|---|
| how-do-you | the thing phrased as the community's own process questions and recommendation requests | first-person process accounts, recommendation-request threads whose replies converge |
| problem | doubt and pain phrasings around the practice — worth-it doubts, time-waste complaints, struggling admissions | the pain and the doubt around the practice |
| tool / artefact | the named tools and artefacts of the practice — names the open web or a first Reddit pass has surfaced — with worth-it and versus forms | where the practice is discussed concretely |
| role | the role's own workflow and day-in-the-life phrasings | who does it and how it sits in their job |

Sort and timeframe apply per call. By default every string runs a `top` page against each sub (the window's loudest threads, where opinion and brand strings find their signal), and a string those pages leave short of its share of the rows also runs a `relevance` page (the threads that match the string, where an everyday how-do-you or problem thread with a modest score surfaces instead of being out-scored by the year's scandal) — merged and deduplicated; `sorts` lists the pages that ran and each row's `matched_via.sort` says which page surfaced it. Pass `sort` to run one page only: `new` for a right-now read, `relevance` alone when the loud layer is already on file. `timeframe: "year"` (the default) holds unless the ask is historical: relevance over an unbounded window drifts to dead threads.

The experience shape (brand-anchored) is not optional in a dig: carry 3–4 everyday symptom words in the niche's own vocabulary; drop it only when the niche genuinely has none, and say so in what you searched. (A light pull runs 2–3 queries total — pick the shapes the ask needs most rather than carrying the full set.) It is the steady-state complaint read the brand-name strings structurally bury.

The tool drops posts with a score under `min_score` (default 5) unless the thread already holds a few comments — a score-1 question with a dozen answers is a thread, and the answers are the evidence — and posts with no substantive title or text; the floor filters junk, it is not a preference; ranking is §5's job, and it runs on convergence, not score. Around 30 **index rows** come back — title, score, comment count, date, a short excerpt of the body and its length — past that you're collecting, not ranking. A row is what decides whether a thread is worth opening; it is never a quote source (§3). A body length of 0 is a link post or a body the index did not carry — it is not a verdict on the thread. Judge such a row by its title and comment count; a title that fits the ask over a live comment section earns the open either way, and the opened thread returns whatever body exists.

## 3. Open the threads that earn it

Reading is a separate, deliberate step: pick the 3–5 rows whose title, excerpt, and comment count say the thread holds what the ask needs — a steady-state complaint thread with a live comment section, a recommendation request with many replies, a switching story with a real body — and open each with `read_social_post(post_url)`: one call, the full post plus its score-ranked comments. Steady-state complaint threads rarely score high; their comment sections are where everyday objections live in their own words. The comment section often carries the confession the post itself dances around — a high-scoring comment is community-validated language. When a recommendation-request thread's replies independently converge on one name, that convergence is the strongest endorsement the channel gives — stronger than any single comment's score — and the finding should say so, naming the convergence itself.

**Never quote from an index row.** The excerpt is cut, so a quote lifted from it is truncated wording — fabrication under the verbatim discipline. Every quote comes from an opened thread. Opening is also where a row's promise gets tested: a thread whose comments turn out thin is a row judged out, not a finding. A dig has ten turns — one or two searches, three to five opens, and the submit fit comfortably; opening every row does not, and is collecting, not ranking.

`with_comments: true` makes one call return the strongest posts' top comments inline — a much larger result and one extra request per such post. It is for a single bounded read where no follow-up turn exists, never the default for a pull or a dig.

**A thread you already hold the URL for.** `mine_reddit` is a search over the vendor's index; it finds threads by what they say, and it often cannot re-find a specific thread by its title. When the brief or a `web_search` hit gives you the URL of a thread, `read_social_post(url)` is the tool — never spend searches trying to surface a thread you can already fetch.

## 4. One broadening pass, then stop

If the harvest is thin (fewer than ~5 usable findings, or nothing top-tier), broaden once — a second `mine_reddit` call with **different strings**: first-word variants of the category, plainer phrasing, the words a first pass or an open-web look showed people actually use — and, when discovery chose poorly, named `subreddits`. A rich harvest can earn the same single pass: when roughly four in five usable findings trace to one event or thread — a scandal, an acquisition, one viral post — broaden once through the experience or how-do-you shapes; a monothematic harvest proves one story outranked everything else this year, not that no other complaints exist. One pass only, whichever trigger fired; a second broadening spends the user's money re-proving the same read. Anything past it — a stronger channel, or a re-seeded run in the niche's own words — is the skill's follow-through offer, never another automatic pass.

## 5. Rank and attribute

- Rank by theme, not by engagement. Group findings by the symptom or claim they converge on; order themes by how many independent posts and comments voice them — §3's convergence principle, extended: five unrelated low-score complaints about one symptom outrank one high-score scandal thread. A post that two different queries both reached (`also_matched`) is stronger than either match alone. For frequency-shaped asks ("most common objections, ranked"), theme mention count is the ranking.
- One event, one slot. When several findings trace to the same event or thread (§4's four-in-five shape, at any scale), they collapse into a single theme — a scandal is real voice, but it takes one line, not the whole list.
- Within a theme, quote from the opened thread that best represents it; among equally representative candidates, prefer the higher-engagement one. Engagement tiers (score ≥ 500 = top, ≥ 50 = mid, else long-tail) are a tie-breaker and a context note, never the ranking; tiers never appear in findings.
- Source strings name the subreddit and the signal — the score, the sort window, whether it's a post or a comment. Note throwaway accounts when apparent — anonymity is context for confession-grade quotes.
