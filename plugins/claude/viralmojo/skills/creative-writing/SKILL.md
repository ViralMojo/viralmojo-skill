---
name: creative-writing
description: Writes creative deliverables in the conversation — hooks, scripts, ad copy, headlines, and variations of any of them — grounded in the brand's own customer language, personas, and messaging direction, and against a brief when one is named. Deliverables live in chat and are saved only on request. Use when the user asks for hooks, a script, copy, headlines, rewrites, or more variations of any of these — including ad copy modeled on a reference creative. Not for packaging a concept into a brief or a test plan for production; that's brief drafting. Not for the finished static ad — the generated image with its copy; that's static ads.
user-invocable: false
---

# creative-writing

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "creative-writing"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "creative-writing"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
