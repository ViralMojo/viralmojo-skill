# LinkedIn

The **named-professional register**: the same person who tweets a hot take and confesses on Reddit writes their considered, career-attached version here — full-length switching narratives ("I'm leaving X after 5 years, here's why"), workflow and process posts with the actual steps, agency and operator voice about client work, B2B buying signal. Lead channel for practitioner narration at length and for professional-audience customer voice; the comment sections are peer review — practitioners correcting, confirming, and naming alternatives under a colleague's post, each commenter carrying the job title they chose to show. Weak for consumer confession (that's Reddit) and for raw unperformed reaction (nowhere is less raw than LinkedIn).

## Evidence weight — the performance discount

Everything on LinkedIn is written to be seen by employers, clients, and peers, and an entire growth industry ("broetry", hook-listicle templates, engagement pods) manufactures posts shaped exactly like evidence. Weight accordingly:

- **First-person narration with specifics** — named tools, real numbers, actual steps, a concrete before/after — is the channel's gold and outranks everything else.
- **A polished framework post** ("5 lessons from…", "Here's your simple guide") is content marketing whoever wrote it: rank it as promotional unless its specifics are independently verifiable. The giveaway is that it teaches; evidence narrates.
- **"I switched" posts are sometimes the ad.** Creators and consultants announce switches as content; check whether the author sells something adjacent (their headline usually says) and note it in the source string.
- **Comments outrank posts for candor.** A comment is lower-stakes than a post, so objections and "actually, X broke for us" live there; a converging comment section under a switching post is stronger than the post itself.
- **A named role beats an anonymous handle.** Every author and commenter here states a role; for B2B evidence that role is half the quote's worth — it tells the reader which buyer said it. Prefer the comment whose stated role matches the audience the ask is about over a louder one whose role does not.

## Before searching

Posts already on file — saved quotes carry their post URLs and author names — arrive in the brief on a dig, since a digger never sees the workspace. Don't spend searches re-finding them: open one with `read_social_post` when the ask needs its text or comments, and search for what the brief doesn't already hold.

## 1. Query

You write the strings; `mine_linkedin` runs each verbatim. The craft: write the string the way a post opens or a piece is titled, quotes for an exact phrase, no engagement or author operators. `date_posted` is the one filter, from last-hour through last-month, three and six months, and last-year. There is no all-time search: an omitted window runs the last year, the widest there is, and the result says so — so an "ever" ask is answered for the last year, and said that way. Recency asks tighten the window.

| Family | Strings | Use |
|---|---|---|
| Name-anchored | switching openings aimed at the name ("switched from X", "leaving X", "moved off X", "X to Y"); the name with evaluation vocabulary ("X review", "why we chose X"); the name paired with a rival's | how professionals narrate their relationship with a named product — the channel's home ground |
| Topic-anchored | the practice phrased as a post opening ("how I run", "my process for", "lessons from", the role + its task); a named artefact of the practice with worth-it or versus vocabulary | how a professional audience does a thing and why — strongest when the audience is operators, marketers, founders, or agencies, i.e. people whose job includes posting here |

A brand-less ask gets zero name-anchored strings (query-craft.md). A light pull is 2–3 strings, one page each, one or two opens.

## 2. Open the posts that earn it

Rows come back in the index's own order (its relevance for your string, carried as `rank`; reactions are a signal on the row, not its position) with the author's stated role (`author_headline`, when known) and a sentence-bounded excerpt only — a LinkedIn post runs 1–2K characters, so **the row is never a quote source** (same rule as Reddit: the excerpt is cut; quoting it is fabrication). Pick the 2–4 rows whose author, role, excerpt, and `comment_count` promise substance — a first-person switch with a live comment section, a process post from someone whose stated role is the one the ask is about — and open each with `read_social_post(url)`: the full body plus its comments, the most-reacted first, each with the commenter's stated role and profile link (up to 30; `comments_available` against `comments_returned` says how much of the section you saw — the post's own count includes replies, which are not readable, so a comment carries its reply count only). `pages_per_query: 2` is the broadening move when page one of a rich vein ran out, never the default.

## Pages and people, read whole

`read_creator(platform: "linkedin")` reads one page by its URL — there is no lookup by name, so find the URL first (a row's `author_url`, a post's author, or a `web_search` for the company's LinkedIn page).

- **A company page** returns its own self-description (tagline, industry, employee range, followers, founded, headquarters, specialities) and its recent posts. On a competitor deep-dive this is the company's own voice: what it claims, what it pushes, which posts draw a comment section. Rank it with self-claims, never as customer voice; the customer reaction is in the comments of the posts that drew them, opened with `read_social_post`.
- **A member** returns their recent posts. Read a practitioner whole when one post earned it — their recurring themes, whether the switch they narrated was a one-off or a pattern, whether they sell something adjacent (the stated role and the posts usually say).

Both return index rows (an excerpt, reactions with their breakdown, comments, reposts, date, the kind of media, and for a repost the original's author) — the same rule applies: a row is for the open/skip call, and a quote comes from an opened post.

## 3. Rank and attribute

- Rank by evidence type, then convergence: first-person narration with specifics → comment-section candor → reasoned comparison → framework posts (promotional; rank nowhere unless independently verifiable).
- Source strings name the author or commenter and their role as LinkedIn states it, plus the signal: *LinkedIn · Jane Doe, growth lead (66 reactions, 22 comments)*. A commenter's quote names the commenter and their role, not the post's author. Note when the author sells something adjacent to the claim.
- Follower counts are context when present, never the ranking — a 200-follower operator's specific account outranks a 60K-follower creator's framework.
- A post two queries both reached (`also_matched`) is stronger than either match alone.

## Thin harvest: one re-angle, then stop

Thin usually means the phrasing didn't match how posts open — re-angle once with the openings the first pass surfaced, or widen `date_posted` one step. A professional topic with no LinkedIn voice is a real answer: not every audience posts here, and consumer categories mostly don't — that thinness points at Reddit or the open web, and the follow-through offer names it.

## Error is not empty

`LINKEDIN_SEARCH_FAILED` is a channel failure to report, never "no one posts about this". `posts_found: 0` with no error is the genuine empty.
