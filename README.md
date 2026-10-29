# ViralMojo skills and plugins

The ViralMojo plugin for Claude Code and Codex: entries for the web agent's 13 skills, the eight channel diggers that run on your own plan, and the start / status commands. It works over the ViralMojo MCP server, which your agent registers for you. The skills' instructions and the diggers' handbooks load from that server when they are used, so they are always the current ones; the plugin itself changes only when a skill is added or renamed.

**Update:** Updating marketplace: viralmojo...Refreshing marketplace cache (timeout: 120s)…
Cloning repository (timeout: 120s): https://github.com/ViralMojo/viralmojo-skill.git
Replacing the existing marketplace clone…
Clone complete, validating marketplace…
✔ Successfully updated marketplace: viralmojo then Checking for updates for plugin "viralmojo@viralmojo"…
✔ viralmojo is already at the latest version (0.1.0)., or turn on auto-update for the  marketplace under Marketplaces in .

**Install:** tell your agent

```
set up https://viralmojo.ai/install.md
```

and it signs you in and installs this plugin. By hand, after `claude mcp add --transport http -s user viralmojo https://api.viralmojo.ai/mcp` and `claude mcp login viralmojo`:

```
claude plugin marketplace add ViralMojo/viralmojo-skill
claude plugin install viralmojo@viralmojo
```

Codex: `codex mcp add viralmojo --url https://api.viralmojo.ai/mcp`, `codex mcp login viralmojo`, then `codex plugin marketplace add ViralMojo/viralmojo-skill`.

Generated from ViralMojo's product repository at `b82ad75b`; edits here are overwritten on the next publish. Layout and per-host notes: `plugins/README.md`.
