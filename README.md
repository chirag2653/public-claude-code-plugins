# Claude Code Agent Toolkit

A shareable **plugin marketplace for [Claude Code](https://claude.com/claude-code)** — a single place to install and stay current on Chirag Jain's agent extensions: skills, and (over time) hooks, MCP servers, and slash commands. Anything that can be packaged as a Claude Code plugin lives here.

Add the marketplace once, install what you want, then **flip on auto-update for this marketplace** (one-time, see [Staying updated](#staying-updated)) — and from then on every new Claude Code session pulls the latest plugin versions automatically. No re-cloning, no chasing links.

## Install

In Claude Code, add the marketplace:

```
/plugin marketplace add chirag2653/claude-code-agent-toolkit
```

Then install any plugin from it:

```
/plugin install openai-image-generation@claude-code-agent-toolkit
/plugin install gemini-image-generation@claude-code-agent-toolkit
/plugin install website-to-skill-folder@claude-code-agent-toolkit
```

Or just run `/plugin` for the interactive browser (Discover / Installed / Marketplaces tabs).

## Staying updated

These plugins intentionally **omit a pinned version**, so each one tracks its source repo's latest commit — every push becomes a new version Claude Code can pick up. How that update reaches your machine depends on a one-time per-marketplace setting:

### Option A — Auto-update (recommended; set once and forget)

Third-party marketplaces like this one ship with **auto-update OFF by default** in Claude Code. Turn it on once:

```
/plugin
```

In the plugin manager, go to **Marketplaces** → select **claude-code-agent-toolkit** → **Enable auto-update**.

After that, Claude Code refreshes this marketplace and pulls new plugin versions **at the start of every new session** — any new terminal you launch `claude` in, any new IDE window, any restart. If a plugin's hooks / MCP / LSP components changed, you'll see a notification to run `/reload-plugins`; pure skill updates just take effect on the next session.

### Option B — Manual update (no opt-in required)

Pull the latest catalog + plugin files on demand:

```
/plugin marketplace update claude-code-agent-toolkit   # refresh the catalog
/plugin update <plugin-name>                           # apply the update, e.g. openai-image-generation
```

### Heads-up: updates don't apply mid-session

Whether automatic or manual, updates land in a **new** cache directory at `~/.claude/plugins/cache/<plugin-id>-<sha>/`. Your *current* Claude Code session keeps using the version it loaded at startup until you restart Claude Code or run `/reload-plugins`. The previous cached version is kept for 7 days so concurrent sessions don't break, then auto-removed.

## What's inside

| Plugin | What it does | Requirements |
|---|---|---|
| **openai-image-generation** | Generate images with OpenAI's `gpt-image-2` via a tested Python CLI (`--json` mode, exit-code contract, 4-tier API-key discovery). | Python 3.10+, `OPENAI_API_KEY`, `pip install openai` |
| **gemini-image-generation** | Generate images with Google's Gemini image-preview models via a tested Node.js CLI. Every Gemini image API knob exposed as a flag. | Node.js ≥ 18, `GEMINI_API_KEY` (no npm deps) |
| **website-to-skill-folder** | Turn any website into an AI-searchable skill folder — scrapes via Firecrawl into ripgrep-searchable markdown with YAML frontmatter. | Python 3, an authenticated `gh` CLI, a [Firecrawl](https://firecrawl.dev) API key |

Each plugin lives in its own repository under [`chirag2653`](https://github.com/chirag2653); this repo is just the catalog that points at them. Each plugin's own README and `SKILL.md` cover its setup in full — the **Requirements** column above is just the at-a-glance list of what you'll need configured before first use.

## License

[MIT](./LICENSE) © Chirag Jain
