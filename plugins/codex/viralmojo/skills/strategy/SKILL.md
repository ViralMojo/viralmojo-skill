---
name: strategy
description: Sets and records the brand's direction through ViralMojo: the territory calls (who to target, what to lead with, what to say, who fronts the creative) and the strategic roadmap; worked creative briefs with divergent test cells for production; and banking ideas in the idea bank. Use when the user asks for direction or priorities, to build or refresh a strategy doc or the roadmap, for a brief or what to hand a creator or agency, or to save or remember an idea.
---

# Strategy

This is one of ViralMojo's four companion skills. The standing rules and host routines every ViralMojo skill assumes — confirm before writing, never invent, the workspace anchor, job polling inside 45 seconds — live in `$viralmojo`: load it first if it is not loaded in this session.

Pick the one skill below whose description matches the request and, before doing the work, call the ViralMojo `load_skill` tool with its name; follow the instructions it returns. They are the web agent's own, served by ViralMojo, so they are always the deployed ones. Load one skill for the work in front of you, not every skill the ask brushes against.

| Skill | What it does and when to use it |
|---|---|
| `strategy` | Works up the brand's committed direction calls and keeps them current — the four territory inputs (persona / WHO, product priority / WHAT, messaging / what to say, creator-talent / who's on camera) and the strategic roadmap that synthesizes them into a diagnosis and ranked priorities. Reads the workspace's evidence and decides from it. Use when the user asks for direction — which buyer to target, what to lead with, what the message should be, who should front the creative, what to prioritize — or asks to build, review, or refresh any strategy document or the roadmap. |
| `brief-drafting` | Builds worked creative briefs — one concept per brief, with deliberately divergent variations as test cells, the creator direction, and the validation behind it — from banked ideas, the strategy, and the workspace's evidence. Use when the user asks for a brief, asks to turn banked ideas into a concept for production, asks for another round on a concept after results came back, or asks what to hand a creator, agency, or their own team to produce. Not for writing the copy, hook, or script itself in chat; that's creative writing. Not for making the finished static ad; that's static ads. |
| `idea-capture` | Captures creative ideas into the brand's idea bank — one entry per idea, whether a hook, a visual, an angle, or a line of customer language. Use when the user says to save or remember an idea, shares a thought worth keeping, or when something worth banking surfaces mid-work (propose it). |

Where a skill points at a reference file (`references/<file>.md`), read it with `read_skill_reference`, the skill's name and the file name; `load_skill` lists the files. Where it says to call `load_skill` with another skill's name, call it — the skill may sit in another companion (`$research`, `$creative`, `$strategy` or `$performance`), and the tool loads it either way. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
