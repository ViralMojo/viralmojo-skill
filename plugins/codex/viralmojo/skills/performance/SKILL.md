---
name: performance
description: Reads the brand's connected Meta ad account through ViralMojo and turns the numbers into judgments: account reads over any window, a single ad's creative read with a keep, iterate, kill or scale verdict, fatigue, where spend goes by placement, who converts by demographic, and whether a brief's test settled. Use when the user asks how their ads are doing, what to kill, iterate or scale, whether an ad is fatiguing, where spend is going, who their ads reach, or whether a test settled its question.
---

# Performance

This is one of ViralMojo's four companion skills. The standing rules and host routines every ViralMojo skill assumes — confirm before writing, never invent, the workspace anchor, job polling inside 45 seconds — live in `$viralmojo`: load it first if it is not loaded in this session.

Pick the one skill below whose description matches the request and, before doing the work, call the ViralMojo `load_skill` tool with its name; follow the instructions it returns. They are the web agent's own, served by ViralMojo, so they are always the deployed ones. Load one skill for the work in front of you, not every skill the ask brushes against.

| Skill | What it does and when to use it |
|---|---|
| `performance-reading` | Reads the brand's connected Meta ad account and turns the numbers into judgments, delivered in chat — account-level reads over any time window, the deep creative read of a single ad (hook, angle, structure, and a keep / iterate / kill verdict), whether an ad is fatiguing, where spend concentrates by placement, who's actually converting by demographic, and checking what a brief's test settled. The account's nodes show data; every diagnosis is produced in conversation. Use when the user asks how their ads are doing, what to kill, iterate, or scale, whether an ad is fatiguing or ready to scale further, where their spend is going, who their ads are reaching, hands an ad to the main agent from its detail, or asks whether a test settled its question. |

Where a skill points at a reference file (`references/<file>.md`), read it with `read_skill_reference`, the skill's name and the file name; `load_skill` lists the files. Where it says to call `load_skill` with another skill's name, call it — the skill may sit in another companion (`$research`, `$creative`, `$strategy` or `$performance`), and the tool loads it either way. If `load_skill` answers that the skill is not available, tell the user plainly that this capability is not open on their account yet, and do not improvise it.
