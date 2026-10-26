---
description: Show the ViralMojo account behind this session — plan, credits, and whether paid work and writes are open
allowed-tools: mcp__plugin_viralmojo_viralmojo__account_status, mcp__viralmojo__account_status
---

Call `account_status` and report it to the user in a few plain lines:

- the account's email and plan, and the subscription state in words (active, trial, cancelling, past due, ended) — never a raw status code;
- the credits balance as a number;
- whether this session can write to the brand brain and run paid tools (searches, digs, image generations). Reads are always open, whatever the state.

When writes or paid tools are closed, say why in one sentence and give the matching link from the result as a markdown link — `billing_url` for a payment problem, the web app (`app_url`) for picking a plan. Plan changes, payment and connecting the Meta ad account happen in the ViralMojo web app (`app_url`), never here.

If the tool returns an error, say what happened in plain words; when it means there is no ViralMojo account for this sign-in, give the sign-up link it carries.
