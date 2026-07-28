# Ingress and TLS feature guide

## Surfaces

- Controller values: `Traefik/traefik-values.yaml`.
- Shared middlewares and dashboard route: `Traefik/`.
- Issuers and certificate examples: `Cert-Manager/`.
- Service-specific routes: each implemented service `ingress.yaml`.

## Dependencies and extension points

Routes depend on Traefik CRDs, an existing target Service, an entrypoint, and a namespace-local TLS Secret. Certificates depend on cert-manager and either the Cloudflare credential Secret or the self-signed CA Secret. New service exposure should follow the existing route/certificate pairing and select the intended issuer explicitly.

## Safe change obligations

Render or apply CRDs before routes, confirm issuer and Secret names, validate the target Service port, and test both TLS and any middleware chain. Recheck whether a route should use staging before production. Do not copy credential payloads into new files.

## Removal

Remove the route and certificate together, then verify no other route references the TLS Secret. Remove unused middleware only after searching all route files. Keep shared issuers while any certificate consumes them; rotate or revoke credentials separately.
