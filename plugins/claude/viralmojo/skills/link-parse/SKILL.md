---
name: link-parse
description: Handles TikTok, Instagram Reels, and Meta Ad Library links pasted into chat — resolves the link immediately into its full workspace record and returns a clickable card the user can open and save to the swipe file. Use whenever a message contains a link from one of those three platforms, with or without surrounding text. Not for general web URLs — only these three content platforms.
user-invocable: false
---

# link-parse

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "link-parse"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "link-parse"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
