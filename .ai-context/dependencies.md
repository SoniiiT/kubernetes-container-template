# Dependencies

| Dependency | Evidence | Role and impact |
| --- | --- | --- |
| Kubernetes | All raw manifests and chart values | Runtime platform; cluster version must support the referenced API versions and CRDs. |
| Helm and upstream charts | `*-values.yaml` files; no `Chart.yaml` in the repo | Values are not deployable alone and must be paired with compatible chart versions. |
| Traefik | `Traefik/traefik-values.yaml`, `traefik.io/v1alpha1` resources | Ingress, TLS termination, middleware, external services, and dashboard exposure. |
| cert-manager | `Cert-Manager/`, `cert-manager.io/v1` resources | ACME/self-signed certificate issuance and Secret lifecycle. |
| Let's Encrypt | ACME issuer URLs in `Cert-Manager/issuer/cloudflare+letsencrypt/` | Public certificate authority; staging and production issuers are separate. |
| Cloudflare DNS | DNS-01 solver configuration and referenced credential Secret | Required for wildcard certificate issuance; account details are intentionally not indexed. |
| MetalLB | Fixed `loadBalancerIP` comment in `Traefik/traefik-values.yaml` | Supplies the Traefik LoadBalancer address on a bare-metal/private cluster. |
| Rook-Ceph | `Ceph-Rook/` resources, Rook image and Ceph image | Distributed block/filesystem storage and operator lifecycle. |
| Argo CD | Auto-generated `Argo-CD/deployment.yaml` and route | GitOps controller; generated manifest should be refreshed from its upstream source. |
| Authentik | `Authentik/` values and Argo OIDC snippets | Identity provider and SSO integration for selected services. |
| Teleport | `Teleport/` values and route | Kubernetes/access proxy with local authentication and second-factor settings. |
| Graylog | Graylog values, OpenSearch/MongoDB dependency flags | Centralized logging; persistent journal and database dependencies. |
| Kestra | Kestra values with Minio/PostgreSQL toggles and Docker-in-Docker | Workflow orchestration; webserver, executor, indexer, scheduler, and worker deployments. |
| Kasm | Kasm values and ingress | Remote workspace platform with PostgreSQL, Redis, and multiple service images. |
| Moodle | Bitnami Moodle values and MariaDB dependency | Learning platform with persistent application/database storage. |
| Homepage and Portainer | Values and/or ingress resources | Cluster dashboard and container-management UI. |
| NGINX | `NGINX-Web/deployment.yaml` | Minimal raw web workload example. |
| Renovate | `renovate.json` | Dependency-update automation using the recommended preset; no workflow is included here. |

Versions are mostly embedded in values, while some images intentionally use `latest` or `master`. The repository does not provide a lockfile or a central version matrix.
