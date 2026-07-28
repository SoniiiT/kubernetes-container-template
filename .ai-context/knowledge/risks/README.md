# Risks and review items

## High priority

- Secret and credential-like material is tracked in several files, including standalone key/certificate/credential payloads and inline chart defaults. Rotate affected credentials and move them to approved secret management before production use.
- `Traefik` and Teleport configuration includes TLS verification bypass settings. Confirm the trust model before exposing services.
- Rook cleanup and host-backed storage are data-destructive when teardown confirmation is enabled or host paths are removed.

## Medium priority

- Several images use `latest` or `master`; chart values do not have a central lockfile or version matrix.
- Issuer names and TLS Secret names are inconsistent across examples (some references include an `-issuer` suffix), so each route must be checked against the selected certificate resources.
- The repository lacks CI, schema validation, render tests, and install orchestration.
- Large Argo CD and Rook files are generated or upstream-derived; refresh drift is likely.

## Low priority

- Placeholder directories contain empty markers, and `IPBan/emtpy.md` has a filename typo.
- README documentation does not describe install order, chart versions, or secret handling.
