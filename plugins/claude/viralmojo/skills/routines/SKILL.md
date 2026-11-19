---
name: routines
description: Sets up and manages routines — work the agent does on its own at a set time, each in a session of its own: a morning read of the ad account, a weekly dig for new complaints, a daily look at a competitor's new ads, a one-off run tomorrow at nine. Writes the ask as a self-standing instruction; before creating, restates schedule, time zone, spend, writes and quota and waits for a go-ahead; before deleting, confirms once — a routine's name alone is neither. Run now is `run_routine_now`, never doing the routine's work in the turn; what routines exist is read off the workspace anchor. Use when the user wants something done every day, each week, every morning or every few hours, says remind me, keep doing this, run this every, or do it automatically; asks what routines they have; asks to pause, resume, delete or change one; or says run it now. Not for the product's own refreshes — monitored competitors, monitors and the ad account refresh on their own, free; adding one is not a routine.
user-invocable: false
---

# routines

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "routines"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "routines"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
