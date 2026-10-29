---
name: brand-assets
description: Keeps the brand's look on file in Brand Assets — builds and maintains the Brand DNA doc (typefaces, colours with hex, photography direction, product details, ad style) from one read of the brand's own site and the photos already kept, keeps the product photos and the logo the user uploads (one folder per product inside Brand Assets), judges whether an unnamed upload is a brand asset at all, and adds a new product's details to the doc. Use when the user asks to build, fill, fix, correct, update or rebuild Brand DNA or the brand's look; uploads or sends product photos or a logo, named or not; or when another skill finds Brand DNA empty or needs an upload kept. Not for making ads — static-ads makes them and only reads what this keeps.
user-invocable: false
---

# brand-assets

This skill's instructions are served by ViralMojo, so they are always the current ones. Before doing the work, call the ViralMojo `load_skill` tool with `name: "brand-assets"`, then follow the instructions it returns for the rest of the task.

Those instructions are the web agent's own. Where they point at a reference file (`references/<file>.md`), read it with `read_skill_reference`, `skill: "brand-assets"` and the file name; `load_skill` lists the files. Where they say to call `load_skill` with another skill's name, call it. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
