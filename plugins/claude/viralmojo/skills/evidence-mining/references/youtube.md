# YouTube

Customer voice the website hides: the top-liked comments under reviewer videos. The video is context; **the comment section is the harvest** — a comment with hundreds of likes is audience-validated language. The video's own words are the second harvest, and only on asks that need them: how reviewers frame the category, the terms they compare on, the objections they raise on camera. Weak for niche products with no video coverage.

## 1. Expand the intent into queries

3–5 search strings from different angles, written the way videos are titled: for a named product, its review, versus, worth-it, and category best-of forms; for a topic, the tutorial and process shapes people actually title videos with — first-person how-I accounts, tutorials, tool reviews, role workflows. One query rarely finds the right comment sections.

## 2. Pick the videos

`mine_youtube` takes the top 5 hits of each query, pools and dedupes them, and **ranks the pool by view count**; by default it harvests the top 3 by views, skipping any channel you name in `exclude_channels` — always the brand's own channel (self-claim territory; its comments skew fans) and tool vendors' demo channels. Prefer independent reviews, comparisons, and process videos with real audiences: a comment section under a 500-view video carries no audience voice, whatever the title promised. Each candidate carries its length and its age: a years-old video describes the category as it was, so on an ask about the current state prefer the recent ones. When the pick matters, use the two-call shape: `max_videos: 0` returns only the ranked `candidates`; read them, then call again with `video_ids` naming exactly the videos to harvest.

## 3. Harvest comments — and, when the ask needs it, the words

Per video: the top 20 comments by likes, each with its reply count. A comment with many replies started an argument; the replies themselves are not returned, so treat the count as a sign of contention, never as agreement. Comments are quoted verbatim like any other evidence.

`with_transcript: true` adds each video's spoken words, cut near 6,000 characters at a sentence (`transcript_chars` says how long the whole was). Ask for it when the ask is about how the category is talked about rather than how buyers feel — the vocabulary reviewers use, the criteria a comparison weighs, the claims a competitor's reviewers repeat, what a demo shows a product doing. Leave it off for a customer-voice dig: comments carry the audience, the transcript carries the creator, and a creator's script is a performance, not evidence of what buyers think. A video without captions comes back with an empty transcript — no words, not a failure. Quote a transcript as the creator's words, attributed to the channel, never as customer voice.

## 4. Beyond the search

- **A video you already hold** — a link the user pasted, a URL from a web search or a finding — opens with `read_social_post`: its stats, description, top comments and transcript in one call. Don't search to find a video whose URL you have.
- **A channel worth reading whole** — a reviewer who covers the category, a competitor's own channel — reads with `read_creator(platform: "youtube")`: subscribers, total views, its About links and its videos newest first. Read a video's views against the channel's subscribers: far above them, the video reached past the channel's audience. YouTube videos are rows, not cards: they cannot be presented or saved, so name the ones worth opening with their links.

## 5. Rank and attribute

- Tiers: video ≥ 100k views = top, ≥ 10k = mid; comment ≥ 50 likes = top, ≥ 5 = mid; else long-tail. Ranking only.
- Source strings name the channel whose video the comment sits under and the comment's like count; a transcript quote names the channel and the video.

## Thin harvest: one re-angle, then stop

A thin harvest — few videos, or comment sections that don't speak to the ask — is often the real answer: niche products lack video coverage. If the first query set comes back thin, run **at most one** more round with re-angled queries (a competitor comparison, a different use-case framing); if that's still thin, report it plainly. The video pool for a given product is small and shared across query phrasings, so further rounds re-mine the same handful of comment sections and spend the user's money re-proving the same read.

## Failure shape

A single failed query is skipped silently — best-effort, move to the next. All queries failing is a channel failure to report, not an empty result. A video whose comments or transcript could not be read is marked so (`comments_unavailable`, `transcript_unavailable`) — say which, never read the gap as silence.
