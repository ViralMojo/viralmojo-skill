---
name: video-deep-read
description: Runs a fresh, targeted read of one video's actual frames and audio, for a question the video's fixed pre-processed context can't answer — a specific visual or on-screen detail, a storyboard or pacing walkthrough, or any video that has no pre-processed record yet: freshly uploaded, never tagged, or a video the user just attached in chat. Use only when the fixed context doesn't already cover what's asked; check it first, don't re-read a video for something already there (an attached video has no fixed context, so read it directly).
user-invocable: false
---

# video-deep-read

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "video-deep-read"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "video-deep-read"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
