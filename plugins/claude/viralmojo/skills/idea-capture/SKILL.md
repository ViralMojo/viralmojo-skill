---
name: idea-capture
description: Captures creative ideas into the brand's idea bank — one entry per idea, whether a hook, a visual, an angle, or a line of customer language. Use when the user says to save or remember an idea, shares a thought worth keeping, or when something worth banking surfaces mid-work (propose it).
user-invocable: false
---

# idea-capture

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "idea-capture"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "idea-capture"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
