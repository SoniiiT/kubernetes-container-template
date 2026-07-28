# Architecture

## Deployment model

The repository is a declarative configuration catalog. Operators are expected to render Helm values with the corresponding upstream chart and apply raw YAML with Kubernetes tooling. There is no repository-owned orchestration layer that installs the components, orders them, provisions namespaces, or substitutes example domains and credentials.

## Main control and data flows

### Ingress and TLS

1. Traefik is configured as a three-replica `LoadBalancer` with a fixed MetalLB address in `Traefik/traefik-values.yaml`.
2. Service routes use Traefik `IngressRoute` CRDs, with a small number of standard Kubernetes `Ingress` resources.
3. Most routes terminate TLS at Traefik and reference a namespace-local TLS Secret.
4. cert-manager `Certificate` resources request those Secrets from either a Cloudflare DNS-01 ACME `ClusterIssuer` or a self-signed `ClusterIssuer`.
5. Some routes attach security middlewares, including default headers, basic auth, CrowdSec plugins, and Teleport-specific TLS/security resources.

Evidence: `Traefik/`, `Cert-Manager/`, and the `ingress.yaml` files under service directories.

### Storage

1. Rook common resources create the `rook-ceph` namespace and RBAC.
2. Rook CRDs and the operator establish the Ceph control plane.
3. `Ceph-Rook/cluster.yaml` defines a Ceph Reef cluster using host-backed data at `/var/lib/rook`, three monitors, two managers, and an enabled dashboard.
4. Block and filesystem pools expose `rook-ceph-block` and `rook-cephfs` StorageClasses for PVC provisioning.
5. Service charts such as Graylog, Kestra, Moodle, and Kasm rely on chart-managed or default dynamic storage rather than declaring a direct Ceph dependency.

Evidence: `Ceph-Rook/common.yaml`, `Ceph-Rook/crds.yaml`, `Ceph-Rook/operator.yaml`, `Ceph-Rook/cluster.yaml`, and the two StorageClass manifests.

### GitOps and identity

The Argo CD install is a large auto-generated upstream manifest. Its route is exposed through Traefik, while `Argo-CD/authentik/policy.csv` and the OIDC files provide Authentik integration snippets. The repository does not contain Argo `Application` resources or a complete GitOps project structure, so deployment ownership remains external.

### Service templates

The application directories combine upstream Helm values with optional route/certificate examples. Authentik, Kasm, Kestra, Graylog, Moodle, Portainer, Homepage, and Teleport include chart-facing configuration. NGINX-Web is a raw Deployment/Service example. Empty directories identify planned templates without implementation.

## Boundaries and integrations

- Kubernetes API: all YAML resources and Helm-rendered resources.
- Traefik CRD API: `IngressRoute`, `Middleware`, `ServersTransport`, and `TLSOption`.
- cert-manager API: `Certificate` and `ClusterIssuer`.
- Rook-Ceph API: `CephCluster`, `CephFilesystem`, and `CephBlockPool`.
- External systems: Cloudflare DNS API through a referenced Secret, Let's Encrypt ACME, MetalLB for the Traefik address, Authentik for Argo CD identity, and upstream container registries/charts.
- External chart lifecycle: chart versions and schema are not pinned in this repository; values must be checked against the selected chart version.
