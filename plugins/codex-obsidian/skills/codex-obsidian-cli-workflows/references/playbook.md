# Obsidian CLI Workflows Playbook

Use this playbook to run named workflow IDs through preview/apply orchestration while preserving domain-skill ownership.

## Invocation shape

```text
workflow_id=<command-id> mode=preview|apply vault=<optional-vault> output=inline|note|json
```

Defaults:
- `mode=preview`
- `output=inline`

## Preview behavior requirements

Preview must return:
- workflow summary and intent
- required and optional inputs
- ordered step plan with delegated skill per step
- target summary and ambiguity checks
- risk level and apply prerequisites

## Apply behavior requirements

Apply must:
- require explicit confirmation for medium/high risk workflows
- enforce target matching between preview and apply
- execute only approved matching steps
- summarize mutations and side effects clearly
- stop immediately on capability blockers

## Global orchestration guardrails

1. Keep direct command execution in domain-skill contracts.
2. Fail closed on ambiguous note/base/workspace targets.
3. Preserve exact-path mutation policies in `codex-obsidian-cli`.
4. Preserve capability gating for publish workflows.
5. Preserve runtime-admin/devtools/sync-publish/workspace boundaries.

## Publish capability probe

For `publish.release_gate`:
1. Run `obsidian help publish:status` through delegated sync/publish skill policy.
2. If probe shows unsupported publish commands, return blocker and stop.
3. Only if supported, continue with `publish:status`, `publish:list`, and requested publish mutation commands.

## Delegation map

- `codex-obsidian-cli`: note/tasks/properties/history/template/link workflows
- `codex-obsidian-cli-bookmarks`: bases and bookmark workflows
- `codex-obsidian-cli-admin`: runtime plugin/theme/snippet/command/hotkey operations
- `codex-obsidian-cli-devtools`: diagnostics and screenshot/runtime inspection
- `codex-obsidian-cli-sync-publish`: sync and publish (capability-gated)
- `codex-obsidian-cli-workspace`: vault/workspace/tab/navigation utilities
