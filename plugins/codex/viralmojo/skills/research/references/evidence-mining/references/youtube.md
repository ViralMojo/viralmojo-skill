# YouTube

Customer voice the website hides: the top-liked comments under reviewer videos. The video is context; **the comment section is the harvest** — a comment with hundreds of likes is audience-validated language. Also useful for how reviewers frame the category. Weak for niche products with no video coverage.

## 1. Expand the intent into queries

3–5 search strings from different angles, written the way videos are titled: for a named product, its review, versus, worth-it, and category best-of forms; for a topic, the tutorial and process shapes people actually title videos with — first-person how-I accounts, tutorials, tool reviews, role workflows. One query rarely finds the right comment sections.

## 2. Pick the videos

`mine_youtube` pools and dedupes the hits and **ranks the pool by view count**; by default it harvests the top 3 by views, skipping any channel you name in `exclude_channels` — always the brand's own channel (self-claim territory; its comments skew fans) and tool vendors' demo channels. Prefer independent reviews, comparisons, and process videos with real audiences: a comment section under a 500-view video carries no audience voice, whatever the title promised. When the pick matters, use the two-call shape: `max_videos: 0` returns only the ranked `candidates`; read them, then call again with `video_ids` naming exactly the videos to harvest.

## 3. Harvest comments

Per video: pull the comments, sort by likes, keep the top ~20. Keep a short description excerpt of the video itself for framing the quotes. Comments are quoted verbatim like any other evidence.

## 4. Rank and attribute

- Tiers: video ≥ 100k views = top, ≥ 10k = mid; comment ≥ 50 likes = top, ≥ 5 = mid; else long-tail. Ranking only.
- Source strings name the channel whose video the comment sits under and the comment's like count.

## Thin harvest: one re-angle, then stop

A thin harvest — few videos, or comment sections that don't speak to the ask — is often the real answer: niche products lack video coverage. If the first query set comes back thin, run **at most one** more round with re-angled queries (a competitor comparison, a different use-case framing); if that's still thin, report it plainly. The video pool for a given product is small and shared across query phrasings, so further rounds re-mine the same handful of comment sections and spend the user's money re-proving the same read.

## Failure shape

A single failed query is skipped silently — best-effort, move to the next. All queries failing is a channel failure to report, not an empty result.
