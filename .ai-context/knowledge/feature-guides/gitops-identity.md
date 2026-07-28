# Argo CD and identity guide

## Surfaces

- Generated Argo CD installation: `Argo-CD/deployment.yaml`.
- Traefik exposure: `Argo-CD/ingress.yaml`.
- Authentik integration snippets: `Argo-CD/authentik/`.

## Safe change obligations

Refresh the generated Argo CD manifest from its upstream release rather than editing it manually. Validate the Argo CD version and CRDs against the target cluster, then verify the route's HTTP and gRPC behavior. Treat OIDC configuration and client credentials as sensitive and rotate them outside source control.

## Removal

Before removing Argo CD, identify managed Applications and external GitOps ownership, disable reconciliation safely, preserve RBAC/identity records needed by replacement tooling, and remove route/certificate resources only after the controller is no longer used.
