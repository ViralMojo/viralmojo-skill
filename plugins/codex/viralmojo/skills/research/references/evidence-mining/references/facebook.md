# Facebook

The **owned-audience and community register**: people answering a brand where the brand posts, members of a group talking among themselves, and customers recommending — or not — a business page. Lead channel when the brand or a competitor runs an active page whose posts draw comments, when the category has group culture (hobbies, parenting, home, pets, health conditions, local services, older audiences), and for local customer voice. Weak when the page is quiet or the category's talk lives elsewhere; a thin harvest there is a real answer, not a failed dig.

## Entry is always a URL

There is no keyword search on this channel. Every read starts from an address:

- **A page** — the brand's own or a competitor's — read with `read_facebook_page`: its recent posts as index rows, plus its size (followers, likes, talking-about count) and category.
- **A public group** — read with `read_facebook_group`: the community's own timeline, the Facebook counterpart of a subreddit listing. There is no member count or description for a group; judge its life by how recent its posts are and how many comments they draw.
- **A post** — pasted by the user, carried in the brief, or taken from a row — opened with `read_social_post`.
- **A page's reviews** — read with `mine_facebook_reviews`.

Pages and groups already on file arrive in the brief on a dig — saved quotes carry their post URLs, brand pages name their Facebook presence — so start there. When the brief names a brand but no URL, find its page with `web_search` (the brand name with `site:facebook.com`) or from the brand's own site. Groups are found the same way: `web_search` with `site:facebook.com/groups` plus the community's own words for the category or the kind of person — never the brand's copy. Only public groups are readable; a private group's rows come back as a failure, and the dig moves on.

## Choosing the venue

- **What customers say to a brand** — its page's comment sections. Pick the posts whose comment counts stand out against the page's usual, and open those; a launch, a price change or a contested claim draws the objections and the defenders together.
- **What a kind of person deals with** — a group in that niche. A group's timeline shows what members chose to raise, without a query to steer it; questions asked by members and the advice that answers them are the evidence.
- **Whether customers recommend a business** — its reviews. Facebook has no stars: each review recommends or not, so read the not-recommended ones for objections and the recommended ones for the language of what landed. The page's own reply sits beside a review; it is the brand's voice, never customer evidence.
- **A competitor** — the same three reads on its page: what its audience asks and complains about under its posts, and its reviews.

Facebook is the wrong channel for anonymous confession (Reddit), for the professional's long-form account (LinkedIn), or for a brand with no active page and a category with no groups.

## Read rows, then open

Page and group rows are an index — an excerpt, its length, reactions, comment count, format and age. A row is never a quote source: its excerpt is cut. Open the 3–5 posts whose comment counts and excerpts promise what the ask needs with `read_social_post(post_url)`: the post, a page of its comments in Facebook's order, and under the most-discussed comments their replies (`depth: 1`). A reply that corrects or contradicts the comment above it is part of the evidence; follow-up questions, "did it work for you" exchanges and the brand's own answers live in the replies. A video post also returns its spoken transcript — the brand's words, not the audience's.

Reactions are the engagement signal: the total, with the split by type when it says something (an angry or sad share on a brand post is a signal; likes alone are reach). Reactions rank candidates; they are never themselves a finding.

## One broadening pass, then stop

If the harvest is thin, broaden once: the next cursor page of the same page or group when its recent posts were off-topic, a second group the first search surfaced, or the reviews when the posts drew no talk. One pass only; anything past it is the skill's follow-through offer.

## Rank and attribute

- Rank by theme and convergence, as on every channel: the same objection voiced under several posts or by several members outranks one loud comment.
- Drop the brand's own comments and replies as evidence of customer voice; quote them only as what the brand says.
- Source strings name the venue — the page or the group by name, or the page's reviews — whether the quote is a post, a comment or a reply, its reactions, and the date.
