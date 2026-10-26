# Query craft

Cross-channel handbook for shaping the queries inside a dig. Channel choice stays with the skill — the smallest set that answers the intent; this governs how the chosen channels get asked. Each channel handbook owns its platform-specific tactics; these rules come first.

## You write the strings

No tool expands, rewrites, or templates a query: what you pass is what the vendor searches, byte for byte. `mine_reddit`, `mine_x_twitter`, `mine_youtube`, `web_search`, `exa_search` all take your `queries` (or `query`) as written. Each runs on its own engine with its own operators — `mine_x_twitter` is real X search (`@handle`, `min_faves:`, `-filter:retweets`), `web_search` is Google (`site:`, quotes) — so an operator belongs to the tool it is written for, never carried across. That puts the whole craft on you — and it means a dig can only be as good as its strings.

Two families of string, and a single string is never both:

| Family | Shape | When |
|---|---|---|
| **Name-anchored** | strings built on the entity's name: the name alone for raw opinion, the name joined to evaluation vocabulary for reviews and worth-it doubts, a switching construction aimed at the name for leavers, the name paired with a rival's for comparison | the ask is about a named brand, product, tool, or person — something people actually refer to by name |
| **Topic-anchored** | strings naming the behaviour, workflow, category, symptom, or kind of person in the words the community posts with — a process question, a doubt about the practice, a named artefact of it; on X, the first-person phrasing a scene actually tweets | the ask is about a behaviour, a motive, a workflow, a category, or a kind of person — and it runs on whichever channel that audience talks in (Reddit's communities, X's scenes, the open web), not on a fixed one |

A brand-less ask gets **zero** name-anchored strings. A brand nobody talks about yet returns nothing on its own, and pairing it with the topic returns nothing squared — the search proves the brand is quiet, not that the topic is. Conversely a named-brand ask usually wants both families: the name for direct opinion, the topic for the category pain the brand sits in.

## Pre-flight: diagnose the keyword before spending

Some asks arrive carrying a keyword that is doomed as a search — not vague (the confirm step catches vague), but phrased in vocabulary no real person posts in. Diagnose before running; a dig on a doomed keyword spends the user's money proving nothing. Four traps, each with its rewrite:

| Trap | Looks like | Why it fails | Rewrite |
|---|---|---|---|
| Demographic shopping | the ask describes the buyer by demographic attributes — an age, a gender, a bracket | no one posts their purchase that way — real threads name the relationship, the hobby, or the occasion | translate the demographic into that vocabulary: the relationship, the hobby, the occasion |
| Numeric collision | the ask carries a number that also means other things | the number dominates retrieval and pulls unrelated content | drop the number unless it is part of the thing's proper name |
| Tutorial phrasing | the query is instruction-seeking — a how-to or a what-is | tutorial wording matches blog and docs titles, not posts — people post their own setup, tips, and experience, not lessons | reframe into the vocabulary of someone sharing, not someone teaching |
| Bare category noun | a single category word with no angle | no anchor — the corpus is infinite and the signal is noise | get the angle first; one clarifying question beats a doomed run |

**The one-turn gate.** A trapped keyword never runs as-is: either the rewrite is concrete, or one short clarifying question goes out first. "Just run it" is a valid answer — run the best rewrite and say what was searched. And when the ask already carries the missing context, skip the question and go straight to the rewrite.

## Seed the query with the customer's words

The workspace often already holds the niche's real vocabulary — the Voice of Customer bank, the personas' voice, saved review phrasing. Seed queries from that language rather than echoing the user's wording; it costs nothing, and the tree usually knows the audience's words better than the ask does.

When it doesn't — a topic the workspace has nothing on — the vocabulary usually lives on the open web. A `web` pass, or one cheap `web_search` / `exa_search`, that reads 3–5 real posts or articles and lifts their phrases into the Reddit / X / YouTube strings is typically the cheapest way to avoid inventing jargon that reads like an analyst wrote it and that nobody titles a post with. This is advice about where words come from, not a sequence to follow: judge per ask.

When a dig comes back thin and the likely cause is vocabulary — the topic exists, the words were wrong — offer a re-seeded second pass instead of only a channel switch: a small harvest of how real posts actually phrase it, then the dig re-run in those words. It spends money, so it is an offer after the dig, never an automatic re-run.

## Anchor names that collide

When the brand, product, or founder name is also a common word or is shared by a more famous entity, a bare-name query pulls the wrong entity — often overwhelmingly. Weld a disambiguating anchor onto **every** query in the dig, not just the first: the category, the company, the role — and on X, the brand's `@handle`, which is both the anchor and the customer-voice shape. A globally unambiguous name needs none.

## Fan one ask into a lead query and escorts

An open ask rarely maps to a single query. Inside the chosen channels, split it:

- **One lead query** carries the ask's center — run it at full depth.
- **One to three escort queries** cover adjacent angles — a rival's name, the launch, the recurring complaint. Run them light: enough to catch signal, never enough to drown the lead.
- **Comparison asks** split per entity plus one head-to-head — each entity queried alone as well, or the louder brand's noise swallows the quieter one.

Two rules for the query strings themselves:

- **Write the query the way content is titled, not the way the question is asked.** What this dig is trying to learn stays separate in your head — it judges the results; the query string matches how people title posts.
- **No temporal or meta words.** Words that mark a query as news-seeking — recency vocabulary, date words, coverage words — match media headlines and roundups, not customers talking.
