# Metrics — definitions, ranges, and when a verdict is earned

Guidance, not law. The ranges below are practitioner consensus for video ads on Meta; they vary by niche and price point. **The account's own baselines override every number here** — once the account has history, judge against its own best (a "hook rate to beat"), and use these ranges only to orient a young account.

## Definitions

**Money metrics** — what says whether spend is paying back:
- **CPA** — cost per purchase. Read against the brand's own KPI threshold, never a generic number.
- **ROAS** — read only alongside spend volume. $30 of spend at ROAS 5 is not the same win as $300 of spend at ROAS 1.5 — the second moved real money at nearly the same efficiency, and the first is likely converting people who were already going to buy.

**Attention metrics** — video only:
- **Hook rate** (thumbstop) — 3-second video views ÷ impressions. Did the open stop the scroll.
- **Hold rate** — viewers still watching at the 25% mark ÷ 3-second viewers. Did the body keep who the hook caught.
- **Statics have no hook or hold** — triage them on CTR, CPM, and spend allocation instead.

**Reach metrics** — what it costs to be seen, and by whom:
- **CPM** — cost per 1,000 impressions.
- **Cost per 1,000 accounts reached** — cost per 1,000 *unique* people, not impressions. Read the two together: low CPM with a high cost-per-1,000-reached means the account is cheaply hitting the same eyeballs over and over — a saturation signal even when CPM alone looks healthy. High CPM with a low cost-per-1,000-reached means the ad is paying more per impression but genuinely finding new people — a growth signal, not a red flag.
- **Cost per save / cost per share** — the free-reach proxies. Low cost per save means people are bookmarking it; low cost per share means it's being passed around. A cost per share above roughly $1,000 is functionally not being shared at all.

## Triage ranges (video)

| Metric | Weak | Healthy | Exceptional |
|---|---|---|---|
| Hook rate | under ~25–30% — the open is the problem; fix the first seconds before judging anything else | ~30–45% | 50%+ |
| Hold rate | under ~25–30% — the middle loses them | ~40–50% | 60%+ |

Supporting signals: CTR for whether attention turns into intent, CPM and cost-per-1,000-reached for what reach costs (see Reach metrics above). **Frequency** — under ~1.3 means real room to scale into cold audiences; 1.3–2 is where fatigue typically starts showing on other signals first; past ~2 with weakening returns is saturation, not just a warning. Those lines are cold-audience numbers — retargeting and small audiences run naturally higher bands and don't read against them; an ad's audience summary says which it is. A frequency climb is also worth checking against exclusion-list hygiene — a stale exclusion list re-serves acquisition creative to existing customers, which inflates frequency without any actual creative problem.

## Funnel diagnosis

Read the metrics left to right — spend → hook → hold → CTR → conversion — and name where the funnel breaks:

- **Strong hook, weak hold** — the open over-promises or the body under-delivers; the problem starts after second three.
- **Strong hold, weak CTR** — they watched but weren't moved to act; the desire or offer half is soft.
- **Strong CTR, weak conversion** — the click's promise isn't kept downstream; usually an offer or landing problem, not the creative's, and worth saying so rather than iterating the ad.
- **Rising CPA, rising frequency, falling ROAS** — audience fatigue, not a creative defect. The creative isn't broken; the audience it's been shown to is used up.
- **Healthy numbers that won't climb any higher** — the audience-format combination is tapped, not failing. Iterating the same creative won't unlock more; it needs a new segment, format, or awareness stage to reach people the current combination can't.
- **High CPM but low cost-per-1,000-reached** — paying more per impression, but for genuinely new reach: a growth signal. **Low CPM but high cost-per-1,000-reached** — cheap on paper, but repeatedly hitting the same people: a saturation signal even when the CPM line looks fine.

Triage locates the problem. Money metrics — spend, returns against the brand's target, frequency — decide the verdict.

## Two things to check before you diagnose

Two account-level facts change what a number means, and skipping them is the fastest way to misread a healthy account as broken.

**The breakdown effect.** Meta's delivery system shifts budget toward whichever campaign, ad set, or ad it predicts will be most efficient *over the whole flight*, not at the moment you happen to be looking. A placement or ad showing a higher CPA right now can still be the right place for budget if Meta predicts its costs will rise more slowly than the alternative's. Read at the level that matches the campaign's structure — campaign level under Advantage+ campaign budget, ad set level under automatic placements or when several ads share one ad set — and rule this out before calling anything a misallocation.

**Attribution windows.** The brand's attribution setting decides which conversions get counted at all: click-through (within 1 or 7 days of a click), view-through (within 1 day of an impression), engaged-view (after 10 seconds of video play), standard (one window plus one behavior), or incremental (Meta's model estimating which conversions the ad actually caused). If the brand changed its attribution setting between two periods being compared, the two numbers are answering different questions — flag it before drawing any period-over-period conclusion. The same holds when the platform changes the counting on its own — a comparison spanning such a change answers two different questions even though the brand touched nothing.

## Placement and audience mix

When the read is about *where* spend concentrates or *who's* actually converting, two breakdowns sit beneath the ad-level numbers above: placement — by platform and by position within it (Facebook Feed / Instagram Feed / Facebook Stories / Instagram Stories / Facebook Reels / Instagram Reels) — and demographic (age, gender, age+gender). Both read spend-first — sort by spend, because that's where the delivery system has concentrated its bet.

**Placement doubles as an audience proxy** when a demographic breakdown is thin or unavailable:

| Heavy placement | Implied audience |
|---|---|
| Facebook Feed | Older, community-oriented, consideration/research phase |
| Instagram Feed | Younger, aspirational, top/mid funnel, visual-led |
| Facebook Reels | Casual viewing, broader/older skew, top-of-funnel reach, weaker intent |
| Instagram Reels | Trend-following, younger, early funnel, high virality potential |
| Facebook Stories | Older, passive tapping-through, upper-funnel exposure |
| Instagram Stories | Younger, interactive, mid-to-lower funnel when the CTA works |

**The data overrides the stated ICP, not the other way around.** If the brand expects to reach 30-year-olds but a 60-year-old cohort converts at a lower CPA, that cohort is part of the real ICP whether the brand recognized it going in or not. A skew toward an unexpected demographic is information about the creative first — it usually means the creative is *reading* older or younger than intended — and about targeting second.

## When a verdict is earned

Too little spend is noise, not signal. Rough floors, scaled to the account:

- **Modest budgets** (tens to low hundreds per day): give a creative 3–7 days, and treat anything under roughly $40–50 of spend — or ~3× the brand's target CPA, whichever is higher — as unjudgeable: three targets' worth of spend with no conversion means the ad genuinely misses (~95% confidence), while judging at 2× miskills about one in seven.
- **Mid-size accounts**: a week or two per round, watching frequency and spend allocation alongside returns.
- **Large accounts** run faster — losers cut inside days, with the account leaning on creative velocity rather than any single ad's perfection.

Two corrections to those floors: a **considered purchase** (long click-to-conversion lag) needs windows stretched past the lag, or the read undercounts everything recent; and day-to-day return swings mean a verdict from any single day is a coin flip — read windows, not days.
