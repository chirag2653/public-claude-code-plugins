# Claude Code Agent Toolkit

A shareable **plugin marketplace for [Claude Code](https://claude.com/claude-code)** — a single place to install and stay current on Chirag Jain's agent extensions: skills, and (over time) hooks, MCP servers, and slash commands. Anything that can be packaged as a Claude Code plugin lives here.

Add the marketplace once, install what you want, and you'll automatically pick up updates whenever a plugin is improved — no re-cloning, no chasing links.

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

These plugins intentionally **omit a pinned version**, so each one tracks its source repo's latest commit. To pull the newest versions:

```
/plugin marketplace update claude-code-agent-toolkit
```

Claude Code also refreshes marketplaces at startup, so you'll generally get updates automatically.

## What's inside

| Plugin | What it does |
|---|---|
| **openai-image-generation** | Generate images with OpenAI's `gpt-image-2` via a tested Python CLI (`--json` mode, exit-code contract, 4-tier API-key discovery). |
| **gemini-image-generation** | Generate images with Google's Gemini image-preview models via a tested Node.js CLI. Every Gemini image API knob exposed as a flag. |
| **website-to-skill-folder** | Turn any website into an AI-searchable skill folder — scrapes via Firecrawl into ripgrep-searchable markdown with YAML frontmatter. |

Each plugin lives in its own repository under [`chirag2653`](https://github.com/chirag2653); this repo is just the catalog that points at them.

## License

[MIT](./LICENSE) © Chirag Jain
