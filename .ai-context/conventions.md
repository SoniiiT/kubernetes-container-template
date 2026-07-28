# Conventions

## Observed implementation conventions

- YAML is the primary format. Most files use two-space indentation, but upstream/generated content and a few hand-written resources vary.
- Service directories use a values file named `<service>-values.yaml` and, when exposed, an `ingress.yaml`.
- Kubernetes resource names are lower-case and service-oriented; namespaces are usually explicit.
- Traefik is selected with `kubernetes.io/ingress.class: traefik` and routes generally use the `websecure` entrypoint.
- TLS examples use `Certificate` resources and named Secrets rather than embedding certificates in route definitions.
- Example domains, email addresses, IPs, and chart defaults remain in source as placeholders and must be replaced before production use.
- Upstream comments are retained in large Rook, Argo CD, Graylog, Kasm, Kestra, Moodle, and Teleport values/manifests.
- `renovate.json` extends `config:recommended`; no repository-owned CI or validation workflow is present.

## Testing and validation conventions

No test runner, chart source, schema test, kubeconform configuration, or CI workflow is present. Safe changes should be validated externally with the relevant upstream Helm chart (`helm lint` and `helm template`) and Kubernetes manifest/schema validation, followed by a dry-run apply in the target cluster. Rook files document an explicit creation order in comments.

## Security conventions and gaps

- TLS and security middleware are part of the intended ingress path.
- RBAC is explicitly configured for Rook, Homepage, Portainer, Graylog, Teleport, and Argo CD integration snippets.
- Secret references are used in several places, but credential-like values and key/certificate payloads are also tracked in the repository. Treat all examples as compromised until rotated and moved to an approved secret-management path.
- `insecureSkipVerify`, generated/default passwords, broad external access settings, and unpinned `latest`/`master` images require an explicit deployment review.

## Documentation conventions

Documentation is sparse and mostly embedded as YAML comments. `README.md` is a short German overview without installation or dependency ordering. New operational guidance belongs in the relevant service directory and `.ai-context/knowledge/`, while provider adapters should remain thin pointers.
