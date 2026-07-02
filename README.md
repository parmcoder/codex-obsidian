<p align="center">
  <img src="plugins/codex-obsidian/assets/icon.svg" alt="Codex Obsidian icon" width="180">
</p>

<p align="center">
  <strong>Codex Obsidian</strong><br>
  A Grade A local-first Codex plugin for Obsidian writing, open formats, and official desktop CLI workflows.
</p>

Codex Obsidian bundles Obsidian-focused writing, Markdown, Bases, Canvas, web import, and official desktop CLI skills behind one install surface. Current Plugin Eval result: **100/100**, **Grade A**, **low risk**.

## Highlights

- `Plugin Eval 100/100`
- One install for Obsidian docs, open formats, web import, and CLI workflows
- Explicit-only skill loading keeps trigger and invoke budgets small
- Local-first: no hosted service, account system, analytics, or telemetry

## What It Adds

- `codex-obsidian-writer` for technical docs, ADRs, runbooks, API notes, Mermaid, Canvas, and Bases
- `codex-obsidian-markdown`, `codex-obsidian-bases`, `codex-obsidian-canvas`, and `codex-obsidian-web-import`
- `codex-obsidian-cli` plus focused CLI skills for bookmarks, admin, devtools, sync/publish, workspace, and workflows
- One install surface instead of separate plugin and skills setup

## Evaluation

Current local Plugin Eval result:

```text
Score: 100/100
Grade: A
Risk: low
Checks: 0 fail, 0 warn, 0 info
```

Re-run it locally:

```bash
node /Users/parmcoder/.codex/plugins/cache/openai-curated-remote/plugin-eval/0.1.2/scripts/plugin-eval.js analyze plugins/codex-obsidian --format markdown
```

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

- `Use codex-obsidian-writer to turn this architecture sketch into an ADR.`
- `Use codex-obsidian-markdown to clean up this note's frontmatter and wikilinks.`
- `Use codex-obsidian-cli to read Projects/Plan.md from my vault.`

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
