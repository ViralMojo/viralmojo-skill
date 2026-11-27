---
name: creator-outreach
description: Emails creators and influencers about working with the brand, from a mailbox the user's organization opens in ViralMojo — finds a creator's contact email from their Instagram, TikTok or X profile, drafts a short email specific to that creator's content, shows it in full and sends only on the user's go-ahead for that email, reads replies when asked and answers in the thread. Before opening a mailbox, states that it costs credits now and every month and waits for a go-ahead; before closing one, restates that the address and all its mail are gone for good — an address alone is not a confirmation. Use when the user wants to contact, email, pitch or reach out to creators, influencers or their managers; asks for a creator's email; asks whether anyone replied or to answer a reply; or asks to open, list or close a mailbox. Not for finding creators or videos — content-search does that; not for email to customers, prospects or anyone who is not a creator — the mailbox refuses it; not for ad copy.
user-invocable: false
---

# creator-outreach

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "creator-outreach"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "creator-outreach"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
