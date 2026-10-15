# Formance Stack rc.1 compatibility review

This local integration merges upstream `ec87f668de540423bc4dbfc4897ba72aff7e298d` into the existing MiKashBoks checkout. The original `de8715a39682a8f7975940aa331f4423175a0e8f` and its custom instruction/context files remain in ancestry and in the merged tree. The fork had documentation changes only relative to upstream `1c5d03ee73a8255f3e7c48531de43ffb7649d96f`; upstream's source removals and move from `libs/events` to `events` do not discard MiKashBoks application code. Both event catalogue locations remain generated.

Ledger is pinned to public `v3.0.0-rc.1`. For a private Stack composition, supply `MIKASHBOKS_LEDGER_OPENAPI` pointing to the exact reviewed MiKashBoks Ledger `openapi.yml`; the build copies it before applying path prefixes. The local override is necessary to retain private historical-balance API documentation. The release identity must describe the private candidate, not an upstream image.

The v3 skipped-order event now requires `reason` and `code`, with optional string `facts`, matching rc.1's public failure projection. Older v1/v2 event schemas remain preserved. Generation uses the lockfile and skips package lifecycle scripts. The unused static-documentation dependency was removed; YAML is pinned to 2.9.0 and the dependency audit reports zero vulnerabilities. The Go event tests and vet pass, and both generated catalogue locations reproduce.

The Linux development shell provides Go from its existing Nix pin. Speakeasy is pinned consistently to 1.759.2. Release and base-image publishing workflows require manual dispatch; no publishing was performed.

The initial 2026-10-14 upload-disabled run required authentication and did not complete composition. After the user signed in on 2026-10-15, the checksum-verified native build of the same pinned Speakeasy 1.759.2 completed `run -s all --skip-upload-spec --output console`: 11 schemas merged, both overlays applied, zero validation errors, 64 warnings and 30 hints. All `just validate-openapi` invariants passed. The generated document retains both Ledger generations, the private `at`/`temporality` selectors and `CONFIGURED_HISTORICAL_BALANCES` log type. Structured evidence and input/output hashes are in [SPEAKEASY_RC1_2026-10-15.json](SPEAKEASY_RC1_2026-10-15.json).

The warnings comprise 61 optional-request-body observations, one unsupported `not` schema, one non-object error response treated as empty, and one OAuth client-credentials SDK feature restricted to Speakeasy Business tier. This validates composition; no SDK targets are configured or generated. No tier, subscription, API authentication or permissions were changed. Registry upload remained disabled; the lock's previous registry source digests are historical metadata, not proof of this local output. Its CLI and embedded workflow versions now match the 1.759.2 pin.

The owner authorized pushes only to the three existing `origin/upgrade/formance-rc1` branches and opening PRs, with no deployment or protected-branch merge. Existing original branches, commit history, private runtime source and old patch files remain preserved.

## Upgrade branch publication — 2026-10-15

Ledger: https://github.com/mikashboks/formance-ledger/pull/25; Stack: https://github.com/mikashboks/formance-stack/pull/19; Accounting: https://github.com/mikashboks/accounting-service/pull/21. All three `upgrade/formance-rc1` branches were pushed with normal Git history. Original branches and pre-existing work remain preserved; all PRs remain open. No release, protected-branch merge, shared-data migration or deployment was performed by this chat. Final status records are tracked in each repository's `AGENT_FEATURES.md`.
