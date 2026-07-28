# Project map

## Shape

`kubernetes-container-template` is a collection of Kubernetes manifests and Helm chart values. It provides reusable service templates, shared ingress and certificate examples, and storage/operator manifests. It has no application source tree, package manifest, chart source, test suite, CI workflow, or environment-specific overlay visible in the repository.

## Top-level areas

| Area | Contents | Guidance |
| --- | --- | --- |
| `Traefik/` | Traefik Helm values, dashboard route, middlewares, external-name route | Shared ingress controller and security boundary. |
| `Cert-Manager/` | Helm values, ACME/self-signed issuers, certificate examples | Certificate resources are namespace-scoped; issuer names and TLS secret names must align with consumers. |
| `Ceph-Rook/` | Rook common RBAC, operator, CRDs, CephCluster, pools, filesystems, StorageClasses, dashboard route | Apply in dependency order; storage deletion can be destructive. |
| `Argo-CD/` | Auto-generated Argo CD install manifest, Traefik route, RBAC/OIDC snippets | `deployment.yaml` is generated upstream content and should not be hand-edited. |
| `Teleport/` | Cluster Helm values, agent values, reverse-proxy route and TLS resources | `clusterName` is a lifecycle invariant; ingress is managed outside the chart. |
| `Authentik/`, `GrayLog/`, `Homepage/`, `Kasm/`, `Kestra/`, `Moodle/`, `Portainer/` | Chart values and/or Traefik routes | Values are chart inputs, not standalone deployable charts. |
| `NGINX-Web/` | Standalone Deployment, Service, Traefik route, Certificate | Small raw-manifest example. |
| Empty service directories | `empty.md` placeholders | Intended extension points with no implementation yet. |
| Root metadata | `README.md`, `renovate.json` | High-level overview and Renovate recommended preset. |

## Navigation

- Start with the target service directory.
- Check its `*-values.yaml` for chart input and its `ingress.yaml` for exposure/TLS.
- Follow issuer and TLS secret references into `Cert-Manager/`.
- Follow `traefik.io/v1alpha1` resources into `Traefik/`.
- Follow storage class references into `Ceph-Rook/`.
- Treat files marked auto-generated or upstream-derived as replacement artifacts, not hand-maintained logic.
- Read `.ai-context/knowledge/feature-guides/` before adding or removing a subsystem.
