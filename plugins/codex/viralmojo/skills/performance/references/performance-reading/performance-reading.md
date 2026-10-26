---
name: performance-reading
description: Reads the brand's connected Meta ad account and turns the numbers into judgments, delivered in chat — account-level reads over any time window, the deep creative read of a single ad (hook, angle, structure, and a keep / iterate / kill verdict), whether an ad is fatiguing, where spend concentrates by placement, who's actually converting by demographic, and checking what a brief's test settled. The account's nodes show data; every diagnosis is produced in conversation. Use when the user asks how their ads are doing, what to kill, iterate, or scale, whether an ad is fatiguing or ready to scale further, where their spend is going, who their ads are reaching, hands an ad to the main agent from its detail, or asks whether a test settled its question.
---

# Performance reading

The ad-account nodes — Performance, All Ads — show **data**: the numbers as delivered, plus plain calculations over them, and each ad read the way a competitor's is — its own words and its Breakdown (the hook and its awareness, funnel and creative-format labels, judged once from those words). You produce every **read** of that data, in chat: why an ad wins, what to do with it, what a test proved. **The board reports; you diagnose.** Your analysis lives in the conversation — nothing you produce lands on the board, and it moves elsewhere in the workspace only at the user's ask.

## Scope a read

- Every read has a window and a focus, taken from the ask: "how did last week do" is a last-week read; "how are my hooks" is a hook-focused read.
- **A vague ask gets a default, not a menu**: propose reading the trailing 30 days across the active ads and say that's what you'll do. The user can narrow it.
- If the window holds too little spend to say anything, say that instead of manufacturing certainty. "Not enough data yet" is a valid read.
- **Narrow on the server, not by reading everything.** `read_ad_performance` filters the account's ads by window, status, media (video, static image, carousel) and the three labels; a cohort question takes a filtered read. An ad not yet labelled matches no label filter, so say what share of spend a label-scoped read leaves out.

## Read the numbers honestly

- **The account's own history judges first.** Verdicts run against the account's own best numbers — the hook rate to beat, its normal returns — with generic industry thresholds only when the account has no history to read: outside numbers vary wildly by niche, and the account's history is the only benchmark that carries its context.
- **Ask for the brand-side numbers when they matter.** Target CPA or ROAS, lifetime value, what a signup is worth — the account cannot show these. When a verdict depends on one and the user hasn't given it, ask; record what they say as the brand's word. Never guess a brand-side number.
- **Two metric layers.** Attention metrics — hook rate, hold rate — are triage: they say where to look, never what won. Money metrics — spend, returns against the brand's target, frequency — decide. A high-hook, low-conversion ad may just be good clickbait.
- **Spend allocation leads; returns lag.** Where the account lets the platform allocate budget across ads, sustained spend share is the platform's vote and often the earliest true signal. But read the account's structure first: where budgets are forced per ad set, allocation says nothing.
- **Attribution honesty.** Name what the platform cannot see — post-click economics, conversions that land off-platform or late. When the business converts downstream of the click, platform cost-per-result is directional, not the final scoreboard.
- **Rule out the breakdown effect and an attribution-setting change before calling a number wrong.** Meta shifts budget toward what it predicts will be efficient over the whole flight, not the moment you're looking — and a changed attribution setting between two periods means the two numbers aren't answering the same question. Both fuller in [references/metrics.md](references/metrics.md).
- Metric definitions, healthy ranges, and how much spend or time a verdict needs: [references/metrics.md](references/metrics.md).

## The deep creative read — one ad

When the user hands an ad over from its detail, or names one, start from its record (`read_record`): the ad's words — copy, transcript, on-creative text, carousel cards — its title, description, CTA and landing page, its hook and three labels, the campaign objective and what it optimises for, who it is shown to, and its daily numbers. Take it apart in the workspace's shared creative vocabulary: the **hook**, quoted, and what makes it stop the scroll or fail to; the **angle** and the **promise**; the **persona and awareness stage** it speaks to; its **pacing, desire, and format**; and where its funnel breaks. The labels were judged from the words alone; when the numbers argue with them, say so. The record holds what the ad says, not how it looks or moves — when the read turns on pixels (pacing, a scene, how it builds shot by shot), run a fresh read of the creative with `video-deep-read`. End with the verdict — **keep, iterate, or kill** — and the reason. This is the same vocabulary idea entries and brief variations use, so what one ad teaches travels.

## Verdicts

- Every significant creative gets one: **keep**, **iterate**, or **kill** — and a keeper with room (the platform still feeding it, frequency low, returns holding) earns **scale**. When the data isn't there yet, *keep watching* and name what would make it judgeable. Signals and reasoning per verdict: [references/verdicts.md](references/verdicts.md).
- **Record why for every kill.** A kill without a reason teaches nothing; the reason is what stops the same mistake from being paid for twice.
- **Close account-level reads with the portfolio look.** When the winners all share one DNA and new variants come in worse at rising frequency, the account needs a genuinely new direction, not another iteration — say so.
- **Fatigue is a trajectory question, not a snapshot one.** Asked whether an ad is fatiguing or still has room, read the trend against its own lifetime, not just its current numbers. The signal list and lifecycle stages: [references/verdicts.md](references/verdicts.md).
- **Comparing creative types needs spend-weighting, not an average.** Asked which format, creator, or approach wins, weigh each cohort by total spend against total customers — never the cheapest ad in a group. Detail: [references/verdicts.md](references/verdicts.md).
- **Recommendations end at the creative decision.** Executing them — pausing ads, moving budget, structuring campaigns — is the user's own media buying. Asked how, describe the common approaches neutrally, note that experienced operators genuinely disagree, and leave the pick to the user.

## Reading the mix

Asked where spend is going, or who's actually converting, read the placement or demographic breakdown rather than the ad-level numbers alone. Placement doubles as an audience proxy when demographic data is thin — heavy Instagram Reels delivery reads younger and trend-driven, heavy Facebook Feed reads older and consideration-stage. Demographic reads run on one hard rule: **the data overrides the brand's stated ICP, not the other way around** — a cohort converting at a lower CPA than the brand's intended audience is part of the real ICP whether the brand expected it or not, and it's usually telling you something about how the creative is actually reading first, targeting second. Full placement table and detail: [references/metrics.md](references/metrics.md).

## Checking a brief's results

When a brief's creative has run, the user says which live ads ran which cells — the mapping is theirs to give, never yours to guess from resemblance; ask when it's missing. Then read the cells against what the brief said would count — each variation's hypothesis and the benchmark it had to beat — and say what the test **settled**, not just how the ads performed. A test that proved its hypothesis wrong is a successful test. If the result calls for another round, that is brief work, started when the user asks.

## After a read

The conversation is the deliverable. A read writes nothing to the workspace: no idea banked, no brief drafted, no strategy call rewritten on your own initiative. When a read surfaces something that belongs elsewhere — a hook worth banking, a result that contradicts the standing strategy — say so and let the user take it there.
