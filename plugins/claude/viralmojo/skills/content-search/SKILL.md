---
name: content-search
description: Searches TikTok and Instagram Reels for content — viral videos, niche creators, formats and hooks worth studying — returning one curated, browsable collection the user can save from into the swipe file. Use when the user asks to find, search, or pull videos, reels, or TikToks on a topic, angle, brand, or trend. Not for links the user pastes (those parse on their own) and not for text-evidence digs into quotes, reviews, or complaints — this finds watchable reference content. Also the home of saved queries — use when the user wants an angle watched on an ongoing basis ("keep an eye on", "every week", "track", "add a query") or wants to drop one, and when a one-off search proves rich enough to keep.
user-invocable: false
---

# content-search

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "content-search"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "content-search"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
