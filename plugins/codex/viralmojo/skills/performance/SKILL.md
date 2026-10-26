---
name: performance
description: Reads the brand's connected Meta ad account through ViralMojo and turns the numbers into judgments: account reads over any window, a single ad's creative read with a keep, iterate, kill or scale verdict, fatigue, where spend goes by placement, who converts by demographic, and whether a brief's test settled. Use when the user asks how their ads are doing, what to kill, iterate or scale, whether an ad is fatiguing, where spend is going, who their ads reach, or whether a test settled its question.
---

# Performance

This is one of ViralMojo's four companion skills. The standing rules and host routines every ViralMojo skill assumes — confirm before writing, never invent, the workspace anchor, job polling inside 45 seconds — live in `$viralmojo`: load it first if it is not loaded in this session.

Pick the one skill below whose description matches the request and read its file before doing the work — its instructions are the web agent's, byte for byte. Load one skill for the work in front of you, not every skill the ask brushes against.

| Skill | File | What it does and when to use it |
|---|---|---|
| `performance-reading` | `references/performance-reading/performance-reading.md` | Reads the brand's connected Meta ad account and turns the numbers into judgments, delivered in chat — account-level reads over any time window, the deep creative read of a single ad (hook, angle, structure, and a keep / iterate / kill verdict), whether an ad is fatiguing, where spend concentrates by placement, who's actually converting by demographic, and checking what a brief's test settled. The account's nodes show data; every diagnosis is produced in conversation. Use when the user asks how their ads are doing, what to kill, iterate, or scale, whether an ad is fatiguing or ready to scale further, where their spend is going, who their ads are reaching, hands an ad to the main agent from its detail, or asks whether a test settled its question. |

Each skill's own links (`references/<file>.md`) resolve inside that skill's folder here: `references/performance-reading/references/<file>.md`. When a skill says to call `load_skill` with another skill's name, open that skill's file through its companion — `$research`, `$creative`, `$strategy` or `$performance` — and when it says `read_skill_reference`, open the file under that skill's own `references/` folder. Where you cannot read the plugin's files in this session, call the `load_skill` and `read_skill_reference` tools instead; they return the same text.
