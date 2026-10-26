---
name: strategy
description: Sets and records the brand's direction through ViralMojo: the territory calls (who to target, what to lead with, what to say, who fronts the creative) and the strategic roadmap; worked creative briefs with divergent test cells for production; and banking ideas in the idea bank. Use when the user asks for direction or priorities, to build or refresh a strategy doc or the roadmap, for a brief or what to hand a creator or agency, or to save or remember an idea.
---

# Strategy

This is one of ViralMojo's four companion skills. The standing rules and host routines every ViralMojo skill assumes — confirm before writing, never invent, the workspace anchor, job polling inside 45 seconds — live in `$viralmojo`: load it first if it is not loaded in this session.

Pick the one skill below whose description matches the request and read its file before doing the work — its instructions are the web agent's, byte for byte. Load one skill for the work in front of you, not every skill the ask brushes against.

| Skill | File | What it does and when to use it |
|---|---|---|
| `strategy` | `references/strategy/strategy.md` | Works up the brand's committed direction calls and keeps them current — the four territory inputs (persona / WHO, product priority / WHAT, messaging / what to say, creator-talent / who's on camera) and the strategic roadmap that synthesizes them into a diagnosis and ranked priorities. Reads the workspace's evidence and decides from it. Use when the user asks for direction — which buyer to target, what to lead with, what the message should be, who should front the creative, what to prioritize — or asks to build, review, or refresh any strategy document or the roadmap. |
| `brief-drafting` | `references/brief-drafting/brief-drafting.md` | Builds worked creative briefs — one concept per brief, with deliberately divergent variations as test cells, the creator direction, and the validation behind it — from banked ideas, the strategy, and the workspace's evidence. Use when the user asks for a brief, asks to turn banked ideas into a concept for production, asks for another round on a concept after results came back, or asks what to hand a creator, agency, or their own team to produce. Not for writing the copy, hook, or script itself in chat; that's creative writing. Not for making the finished static ad; that's static ads. |
| `idea-capture` | `references/idea-capture/idea-capture.md` | Captures creative ideas into the brand's idea bank — one entry per idea, whether a hook, a visual, an angle, or a line of customer language. Use when the user says to save or remember an idea, shares a thought worth keeping, or when something worth banking surfaces mid-work (propose it). |

Each skill's own links (`references/<file>.md`) resolve inside that skill's folder here: `references/strategy/references/<file>.md`. When a skill says to call `load_skill` with another skill's name, open that skill's file through its companion — `$research`, `$creative`, `$strategy` or `$performance` — and when it says `read_skill_reference`, open the file under that skill's own `references/` folder. Where you cannot read the plugin's files in this session, call the `load_skill` and `read_skill_reference` tools instead; they return the same text.
