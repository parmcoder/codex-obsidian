# Obsidian CLI Skill Routing Matrix (2026-04-21)

Use this matrix to pick the right skill and chain them safely.

## Skill ownership

- `codex-obsidian-cli`:
  - note CRUD, search, links, tasks, properties, templates, daily notes, history/diff
- `codex-obsidian-cli-bookmarks`:
  - base discovery/query/create workflows and bookmark listing/creation
- `codex-obsidian-cli-admin`:
  - plugins, restricted mode, themes, snippets, command IDs, hotkeys, command execution
- `codex-obsidian-cli-devtools`:
  - runtime diagnostics: errors, console, DOM/CSS, screenshots, `eval`, `dev:cdp`
- `codex-obsidian-cli-sync-publish`:
  - Sync status/history/restore flows and capability-gated Publish flows
- `codex-obsidian-cli-workspace`:
  - vault/workspace/tab/navigation and utility workflows
- `codex-obsidian-cli-workflows`:
  - one-command orchestration by named workflow ID with preview/apply controls
  - owns workflow IDs only; delegates direct command execution to the six domain skills

## Routing examples

- "Append this to Projects/Plan.md" -> `codex-obsidian-cli`
- "Query Projects.base Roadmap in JSON and bookmark blocked items" -> `codex-obsidian-cli-bookmarks`
- "Install Dataview and enable it" -> `codex-obsidian-cli-admin`
- "Show console errors from my plugin" -> `codex-obsidian-cli-devtools`
- "Check sync status and, if publish commands are supported, publish changed files" -> `codex-obsidian-cli-sync-publish`
- "Load the Daily Review workspace, inspect recents, then open a note in a new tab" -> `codex-obsidian-cli-workspace`
- "Run workflow_id=tasks.rollup mode=preview output=json" -> `codex-obsidian-cli-workflows`
- "Run workflow_id=workspace.focus_mode mode=apply workspace_name=Focus" -> `codex-obsidian-cli-workflows`

## Chaining patterns

### Plugin debugging chain

1. `codex-obsidian-cli-admin`: `plugin:reload id=<plugin-id>`
2. `codex-obsidian-cli-devtools`: `dev:errors` and `dev:console`
3. `codex-obsidian-cli-devtools`: `dev:dom` or `dev:css`
4. `codex-obsidian-cli-devtools`: `dev:screenshot`

### Release chain

1. `codex-obsidian-cli`: `diff` and `history` on target notes
2. `codex-obsidian-cli-sync-publish`: `sync:status` plus publish capability probe (`help publish:status`)
3. if publish is supported: run `publish:status` and `publish:add path=...` or `publish:add changed`
4. if publish is supported: run `publish:list` for verification; otherwise stop with unsupported publish blocker

### Bases research chain

1. `codex-obsidian-cli-bookmarks`: `bases` and `base:views`
2. `codex-obsidian-cli-bookmarks`: `base:query ... format=json`
3. `codex-obsidian-cli-bookmarks`: `bookmark search=...` or `bookmark file=...`
4. `codex-obsidian-cli`: targeted `read path=...` follow-up on resulting files

### Runtime customization chain

1. `codex-obsidian-cli-admin`: read-only inventory (`plugins`, `themes`, `snippets`)
2. `codex-obsidian-cli-admin`: apply runtime change (`theme:set`, `snippet:enable`, `plugin:enable`)
3. `codex-obsidian-cli-devtools`: verify UI/runtime effect (`dev:dom`, `dev:css`, `dev:errors`)

### Workspace context setup -> note workflow handoff

1. `codex-obsidian-cli-workspace`: `workspace:load name=...` and `tabs`/`recents`
2. `codex-obsidian-cli-workspace`: `open path=... newtab` for intended work context
3. `codex-obsidian-cli`: run note-content workflow (`read`, `append`, `tasks`, `properties`)

### Workflow chain: workspace context setup -> note workflow handoff

1. `codex-obsidian-cli-workflows`: `workflow_id=workspace.focus_mode mode=preview|apply`
2. `codex-obsidian-cli-workspace`: `workspace:load`, `tabs`, `open`, `recents`
3. `codex-obsidian-cli`: follow-on note workflow (`read`, `append`, `tasks`, `properties`)

### Navigation sampling -> targeted core note operations

1. `codex-obsidian-cli-workspace`: `random:read folder=...` or inspect `recents`
2. `codex-obsidian-cli-workspace`: resolve and open selected note target
3. `codex-obsidian-cli`: apply targeted edits/analysis with exact `path=` safety

### Workflow chain: navigation sampling -> targeted core note operations

1. `codex-obsidian-cli-workflows`: `workflow_id=recents.triage mode=preview|apply`
2. `codex-obsidian-cli-workspace`: `recents`, `wordcount`, optional `open`
3. `codex-obsidian-cli`: targeted `tasks` or note operations on selected paths

### Workflow chain: publish release gate

1. `codex-obsidian-cli-workflows`: `workflow_id=publish.release_gate mode=preview|apply`
2. `codex-obsidian-cli-sync-publish`: `help publish:status` capability probe (required first)
3. if supported and approved: `publish:status`, `publish:list`, `publish:add|publish:remove`
4. if unsupported: stop with blocker and do not execute `publish:*`

## Guardrail summary

- Keep note-content edits in `codex-obsidian-cli` with exact-path mutation rules.
- Keep base and bookmark workflows in `codex-obsidian-cli-bookmarks`.
- Keep remote-side-effect Sync operations and capability-gated Publish operations in `codex-obsidian-cli-sync-publish`.
- Keep runtime diagnostics and code execution (`eval`, `dev:cdp`) in `codex-obsidian-cli-devtools`.
- Keep runtime admin and customization operations in `codex-obsidian-cli-admin`.
- Keep vault/workspace/tab/navigation and utility operations in `codex-obsidian-cli-workspace`.
- Keep one-command workflow IDs and preview/apply orchestration in `codex-obsidian-cli-workflows`.
