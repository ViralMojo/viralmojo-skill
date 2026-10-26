# ViralMojo skills and plugins

The ViralMojo plugin for Claude Code and Codex: the web agent's 13 skills, the seven channel diggers that run on your own plan, and the start / status commands. It works over the ViralMojo MCP server, which your agent registers for you.

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

Generated from ViralMojo's product repository at `a5b73f9a`; edits here are overwritten on the next publish. Layout and per-host notes: `plugins/README.md`.
