# X / Twitter

The **named, real-time register** of customer voice: people saying things *to* brands (@-mention complaints, the pile-on under an announcement), announcing their switches in public, and — in the practices that live here as scenes (marketing, DTC, creators, developers, AI, finance, design) — narrating their own work as they do it. Lead channel for a named brand's current voice, for anything said directly to a brand, for a topic's sound **right now or inside a dated window** (the only search here that cuts by time), and a parallel peer to Reddit for topic research when the audience's scene is on X rather than in anonymous communities. The identity flip is the tradeoff to hold: a handle attached to every word means practitioners show their real choices — and means people perform, so what Reddit gets as confession, X gets as announcement.

## Evidence weight — know what you're holding

`mine_x_twitter` runs real X search: each string you write is an X advanced-search query, and every hit comes back as an **index row** with the full post text, the like / repost / reply / view counts, the date, the author's handle, follower count and `account_kind`, and whether it is a reply (and to whom). A tweet is short, so the row's `text` is the quotable wording itself — except a long-form post, which is cut and carries `body_chars`; open those before quoting. Weight by what the row is: a person replying to the brand's own handle, or narrating their own switch, outranks a media account's roundup, which outranks a bare mention in a long thread about something else.

## Not the lead for discovery

Searching a category you can't name by name finds nothing, so X never leads a hunt for unknown entrants — that is the competitor discovery recipe in `references/web.md`. X can serve the sweep as **one source family**: search the alternatives-ask shape (the product name with alternative-seeking vocabulary), open the asks' reply threads, and collect the names replies converge on — then tally them cross-source like every other family's candidates.

## Before searching

Start from the handles already on file — the brand page names the brand's own handle(s), saved X quotes carry their authors' handles and URLs — which on a dig arrive in the brief, since a digger never sees the workspace. Lift the brand's handle(s) into `exclude_handles` — their posts are marketing copy. Customer handles the brief names are voices already on file; the main agent dedupes your findings against them once the dig is back.

## 1. Query

You write the strings; the tool runs each one verbatim. X's native operators hold — and they are the craft:

**The shape of a string.** X matches every word you write with AND, so a string is not a sentence. It is an **anchor** — one quoted phrase, or one to three words that name the thing: the handle, the product phrase, the symptom, the practice's own idiom — plus at most one parenthesised group of alternatives (`(A OR B OR C)`) for the qualifier you want beside it, plus operators. Filler words are the failure mode: each one is another AND, and under `Latest` the posts that carry all of them are whichever recent posts happen to share the filler, not the posts about your topic. Real X searches run one to three words; a string that needs a fourth content word is two strings. A phrasing that only exists as an analyst's sentence has no tweet-shaped form — that is the signal to run Reddit or the web instead.

| Operator | Does | Use |
|---|---|---|
| `@handle` | posts mentioning the account | **the cleanest customer-voice shape on X** — only a real user talks *to* a brand; it also kills the collision when the brand name is an ordinary word |
| `"exact phrase"` | phrase match | switching constructions, a named symptom |
| `A OR B` | either | fan a symptom list into one string |
| `-filter:retweets` | drops reposts | always |
| `-filter:links` | drops posts carrying a link | removes article-promo and listicle posts — the media layer — when you want first-person voice |
| `lang:en` | language | always, unless the brief says otherwise |
| `min_faves:N` | at least N likes | **small numbers**: `5`–`20` filters junk; `50+` is the influencer layer, not the customer layer. The tool appends `min_faves:5` (and `lang:en`, `-filter:retweets`) to any string that carries none of that family — write your own to override, `min_faves: 0` / `lang: ""` to switch a default off |
| `since_time:<unix>` / `until_time:<unix>` | date window (unix seconds) | "right now" asks; pair with `query_type: Latest` |
| `from:handle` | one author | reading one switcher's story |

Two families, never mixed in one string:

| Family | Strings | Use |
|---|---|---|
| Name-anchored | `@brand` joined to complaint or question vocabulary (`slow OR bug OR "why does"`); `@brand` alone; `"switched from brand"` / `"left brand"` / `"moved off brand"`; `brand vs rival`, each name alone as well as paired | how people talk about a named brand, tool, or person right now — the channel's home ground; a bare name that is also a common word (`notion`, `slack`, `arc`) **must** be anchored on its `@handle` or a product phrase, or the harvest is noise |
| Topic-anchored | the practice in the words its scene posts with: first-person process phrasings ("how I", "my … workflow", "I stopped doing"), a named artefact or tool of the practice with worth-it or versus vocabulary, the scene's own idioms and hot-take phrases, a symptom in the niche's words — `-filter:links` for first-person voice; the default like floor and the two pages already carry the everyday layer | a behaviour, workflow, or category ask whose audience has a live X scene — the peer of a topic-anchored reddit dig, in the named register. The gate is tweetability: phrase it as something a person would actually post, in the shape above |

`query_type` applies to the call. By default every string runs twice — `Latest` (recency: the everyday voice, replies included) and `Top` (engagement: the loud posts, which on a brand name means the brand's own account and media or influencer threads where the name appears in passing) — merged and deduplicated; a row's `matched_via.query_type` says which page surfaced it, and a post both pages returned is credited to `Latest`. Pass `query_type` to run one page only: `Latest` with `since_time:`/`until_time:` for a dated window, `Top` alone for a second look at what went loud. A light pull is 2–3 strings, no second page, one or two opens.

A brand-less ask gets zero name-anchored strings (query-craft.md) — and never the *user's own* brand paired with the topic when nobody is tweeting about that brand yet.

**Does this audience have an X scene? One query answers it.** When you're unsure whether a topic lives here, spend a single probe — the topic's most tweetable phrase, `Latest`, small `min_faves:` — and read what comes back: first-person posts from people doing the thing means the scene exists, run the topic here; collisions and content-farm posts mean it doesn't, and Reddit or the web owns this ask. The probe costs a fraction of a cent; guessing wrong costs the whole pass.

## 2. Open the threads that earn it

The reply thread under a post is X's comment section, and it is where the channel's best evidence lives: the "same here" replies under a complaint, the pile-on under the brand's own announcement, the replies to an "anyone switched?" ask that converge on one name. Pick the 2–4 rows whose `replies` count and `account_kind` promise it — a person's complaint with many replies, a brand announcement with a loud thread — and open each with `read_social_post(url)`: the post plus its replies, ranked by likes, one call. Opening every row is collecting, not ranking.

## 3. Filter and attribute

- The tool has already dropped the brand's own handles (`exclude_handles`) and reposts; everything else is ranked, not dropped. `account_kind: media_or_influencer` (large following, business-verified) marks the noise floor of `Top` — weigh those rows as what they are (a media roundup, a content creator's list), and keep the occasional real switching story one of them tells. A `media_only` row is a post whose text is only its video or image — nothing to read on the row, but its `replies` count still says whether the thread under it is worth opening; such rows sit after every text row and never take a quota slot.
- A reply row carries `in_reply_to`: a reply *to the brand* is direct customer voice; a reply inside an unrelated thread that happens to name the brand is a bare mention.
- Engagement tiers for ranking: likes ≥ 500 = top, ≥ 50 = mid, else long-tail — a tie-breaker and a context note, never the ranking. Five low-like replies voicing one symptom outrank one viral post.
- Source strings name the author's handle and the like count, e.g. *X · @handle (36 likes, reply to @brand)*. Note when the author is a media or influencer account.
- When several hits turn out to be independent replies to the same ask, converging on one name, that convergence outranks any single post's count — present it as what it is: the ask, and the convergence of its replies.

## Thin harvest: one re-angle, then stop

A thin first pass usually means the strings: re-angle **once** — the `@handle` form when you ran the bare name, `Latest` when `Top` returned the media layer, a competitor's name, the niche's own idiom — then report the thinness plainly, naming what was searched. A named brand nobody tweets about is a real answer.

## Error is not empty

`X_SEARCH_FAILED` is a **channel failure** — the search backend or its rate limit — never "no chatter on X". The fabrication this rule exists to prevent: concluding "this category has no X presence" when the request never landed. `tweets_found: 0` with no error is the genuine empty.
