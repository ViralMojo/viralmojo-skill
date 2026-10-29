---
name: customer-evidence
description: Ingests and maintains a brand's own first-party customer evidence — its store and marketplace reviews, and its post-purchase survey responses — which come from the user, the one exception being the reviews of the brand's own Amazon or TikTok Shop listing, pulled on the user's ask. Use when the user shares reviews or survey responses in any shape (exports, spreadsheets, screenshots, pasted text), asks to keep the reviews of the brand's own Amazon or TikTok Shop listing, or asks to correct, update, or remove saved reviews or survey answers.
user-invocable: false
---

# customer-evidence

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "customer-evidence"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "customer-evidence"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
