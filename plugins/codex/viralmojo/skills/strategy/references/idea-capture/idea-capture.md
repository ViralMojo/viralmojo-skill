---
name: idea-capture
description: Captures creative ideas into the brand's idea bank — one entry per idea, whether a hook, a visual, an angle, or a line of customer language. Use when the user says to save or remember an idea, shares a thought worth keeping, or when something worth banking surfaces mid-work (propose it).
---

# Idea capture

The idea bank is the always-on capture layer between the workspace's evidence and its briefs: raw but worth-keeping creative material, logged the moment it is noticed, so concepting never starts from a blank page. Entries are dated and accumulate; the index tracks them automatically.

## What an entry is

**One idea**: a hook, a visual, an angle, a line of customer language. Never a concept with variations — working an idea up is brief work — and never a decision — direction lives in strategy. If what's being saved is really three ideas, bank three entries.

## Capture

- **Both directions.** The user can ask at any moment — mid-research, reading a review, out of nowhere. And when something worth keeping surfaces in any work — a phrase recurring in reviews, a gap no competitor touches, a hook from a performance read — **propose banking it**. Propose the ones worth remembering, not everything that moves.
- **The bar is generous.** An idea backed by evidence names what backs it; the user's own hunch is banked all the same, with the user named as its source. Never refuse a capture for thinness.
- **Skip duplicates.** An idea already in the bank isn't re-added; point at the existing entry instead.
- **Confirm before writing.** State what you'd bank — the idea and why it earned a slot — and write only on the user's plain-language go-ahead. No card UI, no separate confirm step.
- When the user asks to save hooks or lines produced in conversation, each becomes its own entry.

Every entry is its own doc under `output/idea-bank/entries/` and carries: the idea, stated so a later reader can pick it up cold, as the doc's opening H1; why it earned a slot, pointing at the evidence behind it (or naming the user); a line labelled `Source:` naming the kind of source the idea came from; and a line labelled `Classification:` — the persona it fits, the awareness stage it speaks to, the winning elements it carries (hook / visual / angle / language).

## Nothing moves on its own

Capture touches only the bank — deleting an entry doesn't touch the briefs that name it. An idea built into a brief needs no marker: the brief names the entries it grew from, and that lineage is the record. No brief gets drafted from an idea on your own initiative, no entry is touched as a side effect of other work, and a strategy refresh leaves the bank untouched.

**The index follows the entries — never edit it directly.** Every write happens on an entry; the product updates the entry's index row in the same motion — on a write, an edit, a move or a delete — and builds it from the entry alone: the H1 is the idea summary, the `Source:` and `Classification:` lines are the source type and classification, the entry's path is the link through. An entry missing its H1 or either labelled line leaves that index field thin, so every entry carries all three. The entry's prose depth never enters the index.
