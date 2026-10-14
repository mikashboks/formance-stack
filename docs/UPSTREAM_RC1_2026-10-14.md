# Formance Stack rc.1 compatibility review

This local integration merges upstream `ec87f668de540423bc4dbfc4897ba72aff7e298d` into the existing MiKashBoks checkout. The original `de8715a39682a8f7975940aa331f4423175a0e8f` and its custom instruction/context files remain in ancestry and in the merged tree. The fork had documentation changes only relative to upstream `1c5d03ee73a8255f3e7c48531de43ffb7649d96f`; upstream's source removals and move from `libs/events` to `events` do not discard MiKashBoks application code. Both event catalogue locations remain generated.

Ledger is pinned to public `v3.0.0-rc.1`. For a private Stack composition, supply `MIKASHBOKS_LEDGER_OPENAPI` pointing to the exact reviewed MiKashBoks Ledger `openapi.yml`; the build copies it before applying path prefixes. The local override is necessary to retain private historical-balance API documentation. The release identity must describe the private candidate, not an upstream image.

The v3 skipped-order event now requires `reason` and `code`, with optional string `facts`, matching rc.1's public failure projection. Older v1/v2 event schemas remain preserved. Generation uses the lockfile and skips package lifecycle scripts. The unused static-documentation dependency was removed; YAML is pinned to 2.9.0 and the dependency audit reports zero vulnerabilities. The Go event tests and vet pass, and both generated catalogue locations reproduce.

The Linux development shell provides Go from its existing Nix pin. Speakeasy is pinned consistently to 1.759.2. Release and base-image publishing workflows require manual dispatch; no publishing was performed.

Full Stack API composition remains unverified: the standard Speakeasy workflow requests an external login. A follow-up attempt with registry upload disabled was rejected by automatic approval review because private API schema data or metadata may still leave the machine. No alternative external execution was attempted after that rejection. Local event/schema input checks do not establish that the composed SDK output passes Speakeasy's composition invariants.
