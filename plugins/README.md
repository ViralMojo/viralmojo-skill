# ViralMojo plugins (host mode)

Plugins that put ViralMojo inside the user's own AI host. The host's model is the agent; ViralMojo's MCP server (`backend/app/mcp/`, `https://api.viralmojo.ai/mcp`) provides the web agent's tools over the user's existing account and brand brain, with the web's billing. These plugins carry the rest: the web agent's skills, its standing behaviour, and the routines that replace what the web app does around its agent (the per-turn workspace anchor, the step trace, the result cards, background runs). The workspace itself is read in the web app on every host: there is no workspace pane or card inside a host.

A first sign-in from a host makes the account, and `start_onboarding_build` runs the one-time brand build from there (2026-10-25); plans and payment, and connecting the Meta ad account, stay in the web app.

## Layout

```
.claude-plugin/marketplace.json        Claude Code marketplace (repo root)
.agents/plugins/marketplace.json       Codex / ChatGPT marketplace (repo root)
plugins/
  claude/viralmojo/                    Claude Code plugin
    .claude-plugin/plugin.json
    .mcp.json                          the MCP server, ${VIRALMOJO_MCP_URL:-https://api.viralmojo.ai/mcp}
    hooks/hooks.json                   SessionStart: one line of context
    commands/{start,status}.md         /viralmojo:start, /viralmojo:status
    agents/dig-<channel>.md            seven channel diggers            (generated)
    skills/viralmojo/SKILL.md          host-mode main skill             (authored)
    skills/<13 bundles>/               the web agent's skills, verbatim (generated)
  codex/viralmojo/                     OpenAI plugin (Codex, ChatGPT desktop)
    plugin.json                        Agent Plugins 1.0 manifest + extensions.com.openai
    .codex-plugin/plugin.json          legacy Codex manifest (same metadata)
    mcp.json / .mcp.json               the MCP server, OAuth (portable / legacy form)
    skills/viralmojo/SKILL.md          host-mode main skill, Codex variant (authored)
    skills/{research,creative,strategy,performance}/
      SKILL.md                         router                           (authored)
      references/<bundle>/<bundle>.md  the bundle's SKILL.md, verbatim  (generated)
      references/<bundle>/references/  the bundle's references, verbatim (generated)
    agents/viralmojo-dig-<channel>.toml  Codex custom agents, copy-in   (generated)
  shared/dig-agent-core.md             the digger prompt both hosts' agents render from
  shared/dig-channels.json             one blurb per dig channel
```

## How it maps to the web agent

| Web | Claude Code plugin | Codex plugin |
|---|---|---|
| Base prompt `backend/app/prompts/main/SKILL.md` | skill `viralmojo` (same standing behaviour, plus host routines) | skill `viralmojo` (`$viralmojo`), same shared sections |
| 13 skill bundles, Level-1 catalog | 13 plugin skills `viralmojo:<bundle>`, byte-identical | four routers (OpenAI imports ≤ 5 skills) carrying the 13 bundles as references, byte-identical |
| Workspace anchor on every call | `workspace_anchor` at session start, and once per turn after the turn's last write; the SessionStart hook says to load the skill | same, from the skill and the server's `instructions` |
| `dig_channel` subagent (our LLM, billed) | `viralmojo:dig-<channel>` agents — the web digger's prompt + handbook, same search tools; reasoning on the user's plan, only searches billed | `dig_channel`; optional copy-in custom agents |
| Step trace with sources | the skill states queries and item counts in every reply that rests on a search | same |
| Workspace pane | none — the workspace is read in the web app; `open_workspace(path)` returns the node's web URL (`?node=<path>`, which the web shell opens) to hand over as a link | same |
| Result cards (static ad, parsed link, search collection) | none — the reply prints the ad's copy block, describes the parsed record, lists the kept items one line each | same |
| Runs survive disconnects | long calls become jobs: `job_status(job_id, wait_seconds=…)`, up to 200 s; asking again for a finished job returns the same result | same, waits up to 45 s (Codex's 60 s tool limit) |
| Chat attachments | `upload_attachment` + the multipart POST it spells out, then the web's attachment marker | same, where the client has a shell |
| Paywall card | `SUBSCRIPTION_REQUIRED` relayed with the billing link, never retried | same |

## Install

### Claude Code (CLI, desktop Code tab, VS Code)

Users install from the **public mirror** `ViralMojo/viralmojo-skill`, a generated copy of this directory (`dev/scripts/publish-skill-repo.sh`; re-run it after every change to `plugins/` lands on `main`). The mirror carries no `.mcp.json`: the server is registered first with the host's own commands, so `install.md` (served at `viralmojo.ai/install.md`) has the agent run, in this order:

```
claude mcp add --transport http -s user viralmojo https://api.viralmojo.ai/mcp
claude mcp login viralmojo
claude plugin marketplace add ViralMojo/viralmojo-skill
claude plugin install viralmojo@viralmojo
```

The plugin's tools are then the hand-added server's, `mcp__viralmojo__<tool>`; the dig agents and the two commands list that prefix. `/viralmojo:start` opens a session.

From this (private) repo, for us: `claude plugin marketplace add ViralMojo/viralmojo-skill` + `claude plugin install viralmojo@viralmojo` installs the copy WITH `.mcp.json` (server `plugin:viralmojo:viralmojo`, signed in from `/mcp`); with a hand-added server beside it the agent sees every tool twice under two prefixes — remove one (`claude mcp remove viralmojo`, or disable the plugin's server in `/mcp`). Against the dev box the dig agents need a server named `viralmojo` (their tool lists carry that prefix, not `viralmojo-dev`): `claude mcp add --transport http -s user viralmojo https://dev.viralmojo.ai/mcp`, or `VIRALMOJO_MCP_URL=https://dev.viralmojo.ai/mcp` with this repo's plugin.

Claude Code asks before every MCP tool call, and a plugin cannot ship `permissions`, so only `workspace_anchor` / `account_status` (pre-approved by the two commands) run without a prompt. To stop the prompts on the free reads, add them to `permissions.allow` in `~/.claude/settings.json` (or the project's `.claude/settings.json`):

```json
{
  "permissions": {
    "allow": [
      "mcp__plugin_viralmojo_viralmojo__workspace_anchor",
      "mcp__plugin_viralmojo_viralmojo__read_node",
      "mcp__plugin_viralmojo_viralmojo__read_table",
      "mcp__plugin_viralmojo_viralmojo__list_tree",
      "mcp__plugin_viralmojo_viralmojo__grep_workspace",
      "mcp__plugin_viralmojo_viralmojo__search_nodes",
      "mcp__plugin_viralmojo_viralmojo__read_record",
      "mcp__plugin_viralmojo_viralmojo__read_competitor",
      "mcp__plugin_viralmojo_viralmojo__read_pool_videos",
      "mcp__plugin_viralmojo_viralmojo__read_ad_performance",
      "mcp__plugin_viralmojo_viralmojo__read_swipe_file",
      "mcp__plugin_viralmojo_viralmojo__account_status",
      "mcp__plugin_viralmojo_viralmojo__job_status",
      "mcp__plugin_viralmojo_viralmojo__load_skill",
      "mcp__plugin_viralmojo_viralmojo__read_skill_reference"
    ]
  }
}
```

For a server added by hand (below) the names are `mcp__viralmojo__<tool>` instead. Writes and paid calls keep their prompt; the skill's own confirm-before-write is a separate gate for the brand brain, not the host.

Against the dev box: start Claude Code with `VIRALMOJO_MCP_URL=https://dev.viralmojo.ai/mcp` set (the `.mcp.json` URL expands it). From a checkout, without the marketplace: `claude --plugin-dir plugins/claude/viralmojo`.

Server only, no plugin: `claude mcp add --transport http viralmojo https://api.viralmojo.ai/mcp`; its tools are `mcp__viralmojo__<tool>`. The skills then come through the server's `load_skill` tool; the dig agents and commands are the plugin's. With both the plugin and a hand-added server, the agent sees every tool twice under two prefixes — remove one (`claude mcp remove viralmojo`, or disable the plugin's server in `/mcp`). The dig agents and commands list both prefixes: a name whose server is not connected is skipped at launch (checked 2026-10-18 with only the hand-added server: `dig-reddit` launched with its 11 tools), and an agent refuses to launch only when neither server is connected.

### Codex (CLI, IDE, Codex in the ChatGPT desktop app)

```
codex mcp add viralmojo --url https://api.viralmojo.ai/mcp
codex mcp login viralmojo
codex plugin marketplace add ViralMojo/viralmojo-skill
```

then restart the ChatGPT desktop app, open the Plugins Directory, choose the ViralMojo marketplace and install the plugin (the public mirror's copy carries no server, so the sign-in is the `codex mcp login` above; this repo's own copy, `codex plugin marketplace add ViralMojo/viralmojo-skill`, keeps `mcp.json` and signs in on install — OAuth, CIMD with DCR fallback). Invoke it with `$viralmojo`. Not validated end to end on a real Codex install.

Optional dig agents that run on the user's plan: `cp plugins/codex/viralmojo/agents/*.toml ~/.codex/agents/`. Codex plugins do not carry custom agents (custom agents are standalone TOML files under `~/.codex/agents/` or `.codex/agents/`), so the plugin defaults to the server's `dig_channel`.

Server only, no plugin: `codex mcp add viralmojo --url https://api.viralmojo.ai/mcp`, then sign in when Codex asks (or `codex mcp login viralmojo`).

### Chat hosts (claude.ai, Claude Desktop, Cowork, ChatGPT)

Add `https://api.viralmojo.ai/mcp` as a custom connector. No plugin is needed: the server's `instructions` and the `load_skill` / `read_skill_reference` tools carry the experience. These hosts get the agent only — no cards, no workspace pane; `open_workspace` returns the web link. The Claude plugin also installs on claude.ai and Cowork (remote server, no `bin/`), where `VIRALMOJO_MCP_URL` is not set and the prod URL applies.

## Editing

Generated files are never edited in place. Change the source — a bundle in `backend/app/skill_bundles/` (itself copied from the demo repo, see `dev/scripts/check-skill-sync.sh`), `plugins/shared/dig-agent-core.md`, or `plugins/shared/dig-channels.json` — then:

```
dev/scripts/check-plugin-sync.sh --write   # regenerate copies and agents
dev/scripts/check-plugin-sync.sh           # check (CI runs this)
cd backend && VIRALMOJO_DISABLE_DB_TESTS=1 .venv/bin/pytest tests/test_plugins_sync.py
claude plugin validate --strict plugins/claude/viralmojo && claude plugin validate .
```

Authored by hand: both `skills/viralmojo/SKILL.md` files, the four Codex routers, the two commands, the hook, the manifests and MCP configs. `backend/tests/test_plugins_sync.py` pins that every sentence of the web base prompt's Standing behavior, When no capability matches and Reading tool errors sections appears in both `viralmojo` skills (each standing rule under its own title; host additions are extra sentences, never edits of the web's), that the shared sections are identical between the two skills, that every backticked tool name in any plugin file is a main-catalog tool or a host-mode tool, that each router carries its bundles' descriptions verbatim, and that the diggers hold the web digger's tool subset and handbook. Bump `version` in the three manifests together — `plugins/claude/viralmojo/.claude-plugin/plugin.json`, `plugins/codex/viralmojo/plugin.json` and `plugins/codex/viralmojo/.codex-plugin/plugin.json`; the two marketplace files and the `.mcp.json` / `mcp.json` files carry no version. Claude Code pins users to it.

## Dry-run against the dev box

Use a dev-box test account (Clerk dev instance) that has finished the onboarding build, plus one non-entitled account for the paywall case.

- **Claude Code.** `VIRALMOJO_MCP_URL=https://dev.viralmojo.ai/mcp claude --plugin-dir plugins/claude/viralmojo`, then `/mcp` to sign in. For a local MCP process in `MCP_AUTH_MODE=dev-token`, add it by hand with its header (`claude mcp add --transport http viralmojo http://localhost:5002/mcp --header "Authorization: Bearer <dev token>"`): the skills and agents accept both the plugin's and the hand-added server's tool names (disable the plugin's own server in `/mcp` so the tools are not listed twice).
- **Codex.** `codex plugin marketplace add ./` from the repo root, install from the local marketplace, and point it at the dev box by disabling the plugin's prod server (`[plugins."viralmojo".mcp_servers.viralmojo]` with `enabled = false` in `~/.codex/config.toml`) and adding `codex mcp add viralmojo --url https://dev.viralmojo.ai/mcp`.

Then walk the same scenarios on each and compare against the web agent on the same account:

1. `/viralmojo:start` (Codex: `$viralmojo`) — `workspace_anchor` is called; the reply describes what the brain holds and what is empty, with no capability list.
2. "What's our positioning?" — answered from reads, no skill, no search.
3. "What do people on Reddit say about <category>?" — a light pull on ViralMojo's tools (not the host's web search); the reply names the queries, subreddits and item counts and links each quote.
4. "Do a deep dig on Reddit and X for <angle>" — Claude Code: two `viralmojo:dig-*` agents side by side, one merged report; Codex: two `dig_channel` calls with `wait_seconds` ≤ 45 and `job_status` polling.
5. "Write five hooks for <product>" — the creative skill loads, `run_voice_review` runs, the reply closes with a Voice Review section.
6. "Save the second one as an idea" — the write is confirmed in words first, then `workspace_anchor` is called once after the turn's last write, and the reply gives the node's `open_workspace` link.
7. On the non-entitled account, any search — `SUBSCRIPTION_REQUIRED` is relayed with the billing link and not retried; reads still answer.
8. "Make me a static ad" (with a local product photo) — `upload_attachment` + the multipart POST, the ad is generated once, and the reply prints its copy block (primary text, headline, description, CTA, template, what it tests) and offers to keep it, since the host cannot show it.

Pass = the same tool calls and the same credits on the ledger (`host_call:<tool>` rows) as the web run, minus the web's LLM tokens.

## Known gaps

- Codex plugins carry no agents and this plugin ships no Codex hooks: OpenAI's public directory refuses plugins with lifecycle hooks, so the session-start reminder rides the server's `instructions` and the skill instead.
- Claude Code documents only the all-unresolved case of an agent's `tools:` list (it refuses to launch); skipping the unresolved half of the dig agents' two-prefix list is observed behaviour (2026-10-18), not a documented guarantee. If a release changes it, generate one prefix in `check-plugin-sync.sh` (`TOOL_PREFIXES`).
- The Codex `mcp.json` URL is fixed to prod (no variable expansion in that format); dev testing goes through `codex mcp add`.
- Codex can also read the repo's `.claude-plugin/marketplace.json` as a legacy marketplace; both marketplaces are named `viralmojo` and list one plugin each.
- Directory listings: Anthropic's directory policy on AI image generation applies to `generate_image`; OpenAI's no-in-plugin-commerce rule is met because the plugin only links to the web app's billing pages and sells nothing itself. A public OpenAI listing also needs a `supportURL` and review cases, not set here.

## Sources (read 2026-10-14)

- Claude Code — plugin manifest: https://code.claude.com/docs/en/plugins/manifest-reference ; components (skills, commands, agents, hooks, MCP naming `mcp__plugin_<plugin>_<server>__<tool>`): https://code.claude.com/docs/en/plugins/components ; marketplace: https://code.claude.com/docs/en/plugins/marketplace-reference ; subagent frontmatter: https://code.claude.com/docs/en/sub-agents ; hooks (SessionStart context): https://code.claude.com/docs/en/hooks ; MCP (`${VAR:-default}` in `.mcp.json`, timeouts): https://code.claude.com/docs/en/mcp
- OpenAI — packaging (Agent Plugins 1.0 `plugin.json`, `extensions.com.openai`, `mcp.json` auth, marketplaces, `codex plugin marketplace add`): https://developers.openai.com/plugins/build/plugins ; skills: https://developers.openai.com/plugins/build/skills ; skill import limits (five skills): https://developers.openai.com/plugins/build/mcp-server ; manifest fields and listing limits: https://developers.openai.com/plugins/deploy/submission ; Codex custom agents (TOML, not plugin-carried): https://developers.openai.com/codex/subagents
