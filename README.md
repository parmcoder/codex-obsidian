# Codex Obsidian

Bundled Codex plugin for Obsidian workflows.

It combines a docs-first writer skill with vendored Obsidian format skills and official-CLI workflow skills, packaged as one installable plugin.

## What It Adds

- `codex-obsidian-writer` for technical docs, ADRs, runbooks, API notes, Mermaid, Canvas, and Bases
- `codex-obsidian-markdown`, `codex-obsidian-bases`, `codex-obsidian-canvas`, and `codex-obsidian-web-import`
- `codex-obsidian-cli` plus focused CLI skills for bookmarks, admin, devtools, sync/publish, workspace, and workflows
- One install surface instead of separate plugin and skills setup

## Install

From a local clone:

```bash
codex plugin marketplace add .
codex plugin add codex-obsidian@codex-obsidian
```

From GitHub:

```bash
codex plugin marketplace add parmcoder/obsidian-doc-writer
codex plugin add codex-obsidian@codex-obsidian
```

This bundled plugin already includes the vendored Obsidian skill content adapted from [greg-asher/codex-obsidian](https://github.com/greg-asher/codex-obsidian) and [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills), so no second install is required for the bundled experience.

## Skill Matrix

- Writing and doc structure: `codex-obsidian-writer`
- Vault markdown and open formats: `codex-obsidian-markdown`, `codex-obsidian-bases`, `codex-obsidian-canvas`
- Web cleanup and import: `codex-obsidian-web-import`
- Official desktop CLI note workflows: `codex-obsidian-cli`
- Focused CLI surfaces: `codex-obsidian-cli-bookmarks`, `codex-obsidian-cli-admin`, `codex-obsidian-cli-devtools`, `codex-obsidian-cli-sync-publish`, `codex-obsidian-cli-workspace`, `codex-obsidian-cli-workflows`

## Example Prompts

- `Use codex-obsidian-writer to turn this architecture sketch into an ADR with a Mermaid sequence diagram.`
- `Use codex-obsidian-markdown to clean up this note's frontmatter, callouts, and wikilinks.`
- `Use codex-obsidian-cli to read Projects/Plan.md from my vault with the official desktop obsidian CLI.`
- `Use codex-obsidian-cli-workflows with workflow_id=tasks.rollup mode=preview output=json.`

## Repository Layout

```text
.agents/plugins/marketplace.json
plugins/codex-obsidian/.codex-plugin/plugin.json
plugins/codex-obsidian/skills/
```

## Attribution

This repo vendors and adapts upstream skill content from:

- [greg-asher/codex-obsidian](https://github.com/greg-asher/codex-obsidian)
- [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)

See [THIRD_PARTY.md](/Users/parmcoder/Open-source/obsidian-doc-writer/THIRD_PARTY.md) for bundled components and license notes.
