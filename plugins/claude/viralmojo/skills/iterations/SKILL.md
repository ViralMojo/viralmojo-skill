---
name: iterations
description: Recommends the highest-confidence next moves on a performing ad — either picking which ads deserve the effort first, or building the actual recommendations once one is chosen. Use when the user asks which ads to iterate on this week or month, hands over a specific ad and asks how to iterate it, asks how to extend a winner's life, or asks what to test next on an ad that's performing well. Not for a first script, a first headline, or any concept written from scratch — that's creative writing. Not for making the new version of a static itself — that's static ads.
user-invocable: false
---

# iterations

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "iterations"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "iterations"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
