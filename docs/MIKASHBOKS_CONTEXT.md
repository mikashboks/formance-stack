<!-- Generated MiKashBoks repository context. Refresh from the shared guide. -->
# MiKashBoks dependency context

Reviewed source snapshot: **2026-10-14**. Scope: `accountingservice/formance-stack`.

The canonical local guide is [../../../docs/PROJECT_DEPENDENCIES.md](../../../docs/PROJECT_DEPENDENCIES.md). If that parent folder is unavailable in a standalone or hosted checkout, use this file and verify current source/lockfiles before changing a contract. Evidence paths below are relative to the MiKashBoks root; they are source locations, not grants of file access.

## Related projects

| Consumer → dependency | Type | Relationship | Source evidence |
| --- | --- | --- | --- |
| No specific cross-repository edge recorded | source snapshot | Check current source and configured artifacts before assuming a dependency or independence | Shared dependency guide |

## Working across projects

- Read the current repository guardrails and only the relevant dependency context; existing subsystem, tenant and release rules continue to apply.
- Published package dependencies use their declared versions and lockfiles. A sibling source edit does not change the installed or deployed artifact. Do not add universal local package links. Preserve Ballerine's internal workspace.
- API dependencies normally need an explicit local or approved development endpoint. Attach sibling source only for tasks that change or verify that boundary; request missing project access through the normal workflow.
- For schema/generated-contract changes, check producer and consumer compatibility, provenance and affected tests. Report a missing/skipped contract check explicitly.
- A documentation or code change does not authorize publishing, pushing, deploying, provisioning resources or production activation. Credentials and runtime configuration are supplied separately.
- Recheck dated version observations and live deployment behavior independently. Refresh this snapshot after changes to dependencies, layout or release ownership.

## Refresh

With the shared root available, update `docs/PROJECT_DEPENDENCIES.md` and `docs/PROJECT_DEPENDENCIES.json`, then run `python3 tools/sync-project-context.py --sync` from that root. Use `--check` to verify snapshots and pointers without changing them. Standalone cloud clones carry this snapshot only after it is included in the selected Git revision; local creation does not upload it.
