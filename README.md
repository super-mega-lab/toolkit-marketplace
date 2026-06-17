# Super Mega Lab Plugin Marketplace

Claude Code marketplace shim for Super Mega Lab plugins.

## Usage

```bash
/plugin marketplace add super-mega-lab/toolkit-marketplace
/plugin install sml-toolkit@sml-marketplace
```

## Updating

```bash
/plugin marketplace update sml-marketplace
/plugin update sml-toolkit@sml-marketplace
```

To receive new versions automatically, run `/plugin`, open the **Marketplaces** tab, select `sml-marketplace`, and enable auto-update — Claude Code then installs updates at startup and prompts for `/reload-plugins`. Auto-update is off by default for non-Anthropic marketplaces, and there is no silent update: a new version only appears once the `version` in `marketplace.json` (below) is bumped.

## Available plugins

| Plugin | Description | Repo |
|--------|-------------|------|
| sml-toolkit | General-purpose developer toolkit for AI coding agents | [super-mega-lab/toolkit](https://github.com/super-mega-lab/toolkit) |

## Releasing

This repo is a shim — the plugin lives in [super-mega-lab/toolkit](https://github.com/super-mega-lab/toolkit) and is pulled via the `url` source in `.claude-plugin/marketplace.json`. The `version` field here is the trigger Claude Code reads to detect an update; bumping it (in lockstep with the plugin's own `plugin.json`) is what makes new releases reach users.

1. Push the new plugin content to `toolkit` (its default branch is what the `url` source tracks).
2. Bump `plugins[0].version` in `.claude-plugin/marketplace.json` here to match, then commit and push.

Full procedure: [toolkit README → Releasing](https://github.com/super-mega-lab/toolkit#releasing).
