---
name: iterations
description: Recommends the highest-confidence next moves on a performing ad — either picking which ads deserve the effort first, or building the actual recommendations once one is chosen. Use when the user asks which ads to iterate on this week or month, hands over a specific ad and asks how to iterate it, asks how to extend a winner's life, or asks what to test next on an ad that's performing well. Not for a first script, a first headline, or any concept written from scratch — that's creative writing. Not for making the new version of a static itself — that's static ads.
user-invocable: false
---

# Iterations

Two phases, one flow. **Phase A** — no ad named yet — picks which ads are worth the effort. **Phase B** — an ad is already chosen — diagnoses it and builds the recommendations. Both are delivered in chat; nothing here writes to the workspace on its own.

## Which phase to enter

- A specific ad is named, or handed over — skip straight to Phase B.
- An account-level ask — "what should we iterate on this month," no ad named — run Phase A first, checkpoint the shortlist, then Phase B on each confirmed ad, carrying the selection reasoning forward rather than re-deriving it.
- Unclear which — ask, or offer to run Phase A.

## Ground first

Read the brand's committed strategy and the idea bank before anything else — a request that cuts against the committed strategy gets the conflict named, not silently executed, and an iteration that needs a new element checks the idea bank for a graded entry before inventing one. Then brand voice, ICP, compliance, and the account's own iteration history on the ad in question — ask for it if it isn't already in the conversation; never guess it from resemblance.

## Phase A — which ads deserve it

Pull the account sorted by spend over a meaningful window (60 days is a good default). For each candidate: is the spend significant *relative to this account's own scale*, not a fixed number; is it rising, steady, or dropping week over week (rising or steady favors selection, dropping deprioritizes); is it a promotional or discount push — if so, drop it, it spikes and dies on its own and teaches nothing durable. Read what the account's actual top performers share — format, angle, creator, how soon the product appears — and note anything unusual that's winning anyway; that pattern travels into Phase B. Check whether a candidate has already been iterated and whether those iterations worked, so a stale round doesn't repeat.

Present the ranked shortlist — what's selected and why, what was passed over and why — and wait for confirmation before spending effort on recommendations, unless the user asked to run straight through.

## Phase B — building the recommendations

**Diagnose through two lenses, both, every time.**

- **The data lens.** Find the bottleneck: hook rate below ~30% is a stop-scroll problem, hold rate under ~25–30% is a body that loses people, CTR under ~1% is a weak CTA or offer, frequency past ~1.2–2 is fatigue from re-serving the same audience. The bottleneck is whichever sits below its floor while the others hold — not a feeling. Confirm the ad is a genuine winner first: the account's top spender is usually the most potent ad, and a high ROAS on low spend tends to dry out fast — don't iterate on an ad that just picked the low-hanging fruit.
- **The creative lens.** Set the data aside and watch the ad as a viewer would. What's the angle, the hook, the emotional journey, the awareness stage it's pitched at. Its words, hook and three labels are already on its record (`read_record`); read its frames fresh (`video-deep-read`) only when the lens turns on what the ad shows rather than what it says. Grade it against what a genuinely strong ad in this account looks like — the element it nails is the one to protect; if it only works on an audience that already knows the brand, that itself points the iteration toward a broader, more educational hook.

**Skipping either lens produces shallow recommendations** — data-only optimization converges every ad in the account toward the same narrow pattern; creative-only misses what the numbers are actually saying.

From both lenses: name the working elements to protect, and the specific underperforming element to iterate on — forensically specific ("the hook is a talking-head that isn't stopping the scroll, but the copy converts once someone watches" — not "the hook is weak").

**State the diagnosis and the chosen moves before building them out** — two to four sentences, checkpoint before drafting, skip only when the user already approved a specific move or asked to skip the review.

**Pick from the move menu** — [references/iteration-moves.md](references/iteration-moves.md) — matched to the diagnosis, never picked because a move is historically popular. Default to three recommendations unless the user asked for a different number; if only fewer than three are genuinely strong, give fewer and say why padding would waste budget.

## What every recommendation has to clear

- Addresses the actual diagnosed bottleneck or strategic goal — not a move that just sounds good.
- Changes exactly one variable. Two changes in one recommendation means the result can't be attributed to either.
- Protects whatever's already working — don't propose a messaging rewrite first when the message is what's converting.
- Doesn't repeat a move this ad has already been through, unless the prior round's result is being explicitly built on.
- Specific enough to execute without a follow-up question — an exact moment, line, or element named, not a category of change.
- Reads like a person when it includes new customer-facing words, not like a model — no fabricated stats, no predicted metric improvements ("this will lift CTR 15%" is never said), no forbidden term even if asked for — offer the compliant version instead.

When recommending three or more, favor a genuine mix over three variations on the same lever — a bigger swing (new format, new angle) next to a smaller one (a hook-only swap, a pacing trim) gives the account more than one path to learn from. Match swing size to spend: an ad carrying heavy spend has likely saturated its audience and needs a bigger swing; an ad still scaling quickly is better served by smaller, lower-risk moves that protect its trajectory. Before proposing anything built from scratch, check whether two existing winners can simply be recombined instead — that's usually the lowest-risk move available.

## Check before it ships

When a recommendation carries new customer-facing words, the same gate that guards creative writing runs here too, before presenting: put the new copy through `run_voice_review`. It reads every line on its own and names the ones that show a generated-writing tell — it judges, it never rewrites.

- **Flagged lines are yours to rewrite**, against the tells, the testimonial trap and the cold-audience-first rule in the creative-writing skill's `ai-writing-tells.md` reference — rewritten the way the customer would actually say it, not synonym-swapped. Then run the check once more; the second result stands, two runs at most.
- **Kept lines stay as they are** — the check found them in the customer's own words.

**When the gate runs, it closes the reply as its own labeled section — Voice Review — pass or fail:** ships or flagged; which tells were flagged and how the lines were changed; anything still flagged after the second run, stated plainly; each kept line and why. If the check itself failed to run, the section says the copy went out unchecked. A reply that ran the gate and is missing the section did not pass it.

**A round that introduces no new customer-facing words doesn't run the gate and shows no section.** Recommendations like "cut the first 1.2 seconds", "re-shoot this in daylight", "run it as a 9:16 instead" change no words: there is no copy for the voice check to read. Running it anyway would produce a section whose only content is "nothing to check", which trains the user to skip past exactly the section that matters on the rounds that do carry copy. Don't emit an empty or "n/a" version of it — omit it.

## Output

Two to four sentences on what's working and the bottleneck, then the ranked recommendations — each named descriptively (not "Iteration 1"), tied to the diagnosis with the specific data behind it, and specific enough to shoot or build immediately — then which to test first and why, calling out anything that needs real production time versus what can go out today. A recommendation for a static can be offered for generation; the new static is made only when the user asks for it.
