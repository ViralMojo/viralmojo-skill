---
name: brief-drafting
description: Builds worked creative briefs — one concept per brief, with deliberately divergent variations as test cells, the creator direction, and the validation behind it — from banked ideas, the strategy, and the workspace's evidence. Use when the user asks for a brief, asks to turn banked ideas into a concept for production, asks for another round on a concept after results came back, or asks what to hand a creator, agency, or their own team to produce. Not for writing the copy, hook, or script itself in chat; that's creative writing. Not for making the finished static ad; that's static ads.
user-invocable: false
---

# brief-drafting

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "brief-drafting"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "brief-drafting"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
