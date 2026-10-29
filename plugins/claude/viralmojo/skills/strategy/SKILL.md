---
name: strategy
description: Works up the brand's committed direction calls and keeps them current — the four territory inputs (persona / WHO, product priority / WHAT, messaging / what to say, creator-talent / who's on camera) and the strategic roadmap that synthesizes them into a diagnosis and ranked priorities. Reads the workspace's evidence and decides from it. Use when the user asks for direction — which buyer to target, what to lead with, what the message should be, who should front the creative, what to prioritize — or asks to build, review, or refresh any strategy document or the roadmap.
user-invocable: false
---

# strategy

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "strategy"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "strategy"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
