# anatomy.md

> Auto-maintained by OpenWolf. Last scanned: 2026-09-21T16:32:36.039Z
> Files: 90 tracked | Anatomy hits: 0 | Misses: 0

> Project structure index. Auto-maintained by OpenWolf hooks and daemon.
> Run `openwolf scan` to generate, or wait for the first Claude Code session.
> Status: Pending initial scan

## ./

- `AGENTS.md` — Agent context (~186 tok)
- `CLAUDE.md` — OpenWolf (~198 tok)
- `README.md` — Project documentation (~190 tok)
- `renovate.json` (~33 tok)

## .ai-context/

- `architecture.md` — Architecture (~810 tok)
- `conventions.md` — Conventions (~588 tok)
- `dependencies.md` — Dependencies (~680 tok)
- `manifest.json` (~400 tok)
- `project-map.md` — Project map (~584 tok)

## .ai-context/indexes/

- `files.json` (~3204 tok)
- `symbols.json` — Declares protections (~1482 tok)

## .ai-context/knowledge/

- `README.md` — Project documentation (~154 tok)

## .ai-context/knowledge/business-rules/

- `invariants.md` — Observed invariants (~357 tok)

## .ai-context/knowledge/decisions/

- `index.md` — Decisions (~49 tok)
- `README.md` — Project documentation (~57 tok)

## .ai-context/knowledge/feature-guides/

- `ceph-storage.md` — Rook-Ceph storage feature guide (~308 tok)
- `gitops-identity.md` — Argo CD and identity guide (~206 tok)
- `ingress-and-tls.md` — Ingress and TLS feature guide (~301 tok)
- `service-templates.md` — Service template guide (~272 tok)

## .ai-context/knowledge/removal-guides/

- `README.md` — Project documentation (~202 tok)

## .ai-context/knowledge/risks/

- `README.md` — Project documentation (~311 tok)

## .github/

- `copilot-instructions.md` — Copilot project context (~117 tok)

## Argo-CD/

- `ingress.yaml` — K8s IngressRoute: argocd-server (~252 tok)

## Argo-CD/authentik/

- `oidc.authentik.clientSecret` — Secret: argocd-secret (~26 tok)
- `oidc.config` — ConfigMap: argocd-cm (~86 tok)
- `policy.csv` — ConfigMap: argocd-rbac-cm (~25 tok)

## Authentik/

- `authentik-values.yaml` — Declares name (~169 tok)
- `ingress.yaml` — K8s IngressRoute: authentik (~188 tok)

## Bind9/

- `empty.md` (~1 tok)

## Bitwarden/

- `empty.md` (~1 tok)

## Ceph-Rook/

- `cluster.yaml` — ################################################################################################################ (~5407 tok)
- `common.yaml` — ################################################################################################### (~10055 tok)
- `crds.yaml` — ############################################################################# (~224999 tok)
- `dashboard-external-ingress.yaml` — K8s IngressRoute: rook-ceph-mgr-dashboard (~199 tok)
- `operator.yaml` — ################################################################################################################ (~8225 tok)
- `storageclass-block-storage.yaml` — K8s CephBlockPool: replicapool (~844 tok)
- `storageclass-shared-file-storage.yaml` — K8s CephFilesystem: myfs (~429 tok)

## Cert-Manager/

- `cert-manager-values.yaml` (~62 tok)

## Cert-Manager/certificates/cloudflare+letsencrypt/

- `certificates-production.yaml` — K8s Certificate: example-production (~86 tok)
- `certificates-staging.yaml` — K8s Certificate: example-staging (~83 tok)

## Cert-Manager/certificates/selfsigned/

- `certificates-selfsigned.yaml` — K8s Certificate: example-selfsigned (~80 tok)

## Cert-Manager/issuer/cloudflare+letsencrypt/

- `letsencrypt-production.yaml` — K8s ClusterIssuer: letsencrypt-production (~144 tok)
- `letsencrypt-staging.yaml` — K8s ClusterIssuer: letsencrypt-staging (~145 tok)

## Cert-Manager/issuer/selfsigned/

- `ca.crt` (~18 tok)
- `clusterissuer-selfsigned.yml` — K8s ClusterIssuer: selfsigned-issuer (~37 tok)
- `selfsigned-ca.yaml` — K8s Secret: selfsigned-ca (~56 tok)

## Cloudflare-DDNS/

- `empty.md` (~1 tok)

## Cloudflare-Tunnel/

- `empty.md` (~1 tok)

## CodeX-Docs/

- `empty.md` (~1 tok)

## Crowdsec/

- `empty.md` (~1 tok)

## FastAPI/

- `empty.md` (~0 tok)

## GitLab/

- `empty.md` (~0 tok)

## GrayLog/

- `graylog-values.yaml` — Default values for Graylog. (~5521 tok)
- `ingress.yaml` — K8s IngressRoute: graylog (~182 tok)

## Hashicorp-Vault-Operator/

- `empty.md` (~1 tok)

## HomeAssistant/

- `empty.md` (~1 tok)

## Homepage/

- `homepage-values.yaml` (~339 tok)
- `ingress.yaml` — K8s IngressRoute: homepage (~184 tok)

## IPBan/

- `emtpy.md` (~0 tok)

## Kasm/

- `ingress.yaml` — K8s IngressRoute: kasm (~179 tok)
- `kasm-values.yaml` — yaml-language-server: $schema=values.schema.json (~4751 tok)

## Kestra/

- `kestra-values.yaml` — ## Image (~2280 tok)

## Kestra/secrets/

- `ssh-key.yaml` — K8s Secret: ssh-key (~49 tok)

## KubeVIP/

- `empty.md` (~1 tok)

## Kubernetes-Dashboard/

- `empty.md` (~1 tok)

## Langhorn/

- `empty.md` (~1 tok)

## MetalLB/

- `empty.md` (~1 tok)

## Moodle/

- `ingress.yaml` — K8s IngressRoute: moodle (~181 tok)
- `moodle-values.yaml` — SPDX-License-Identifier: APACHE-2.0 (~656 tok)

## NGINX-Ingress/

- `empty.md` (~1 tok)

## NGINX-Web/

- `deployment.yaml` — K8s Deployment: nginx (~471 tok)

## Nextcloud/

- `empty.md` (~1 tok)

## PasswordPusher/

- `empty.md` (~0 tok)

## Portainer/

- `portainer-values.yaml` — Default values for portainer. (~278 tok)

## Pterodactyl-Panel/

- `empty.md` (~0 tok)

## RabbitMQ/

- `empty.md` (~0 tok)

## Rancher/

- `empty.md` (~0 tok)

## Read2Burn/

- `empty.md` (~0 tok)

## Teleport/Teleport-Agent/

- `teleport-agent-values.yaml` (~46 tok)

## Teleport/Teleport-Cluster/

- `ingress.yaml` — K8s Certificate: example-production (~838 tok)
- `teleport-cluster-values.yaml` — ################################################# (~11575 tok)

## Traefik/

- `ingress.yaml` — K8s IngressRoute: traefik-dashboard (~224 tok)
- `traefik-values.yaml` (~283 tok)

## Traefik/external/

- `example.yaml` — K8s Service: example-route (~284 tok)

## Traefik/middleware/

- `bouncer-middleware.yaml` — K8s Middleware: bouncer (~80 tok)
- `crowdsec-bouncer-plugin.yaml` — K8s Middleware: crowdsec-bouncer-traefik-plugin (~71 tok)
- `default-headers.yaml` — K8s Middleware: default-headers (~236 tok)
- `middleware.yaml` — K8s Middleware: traefik-dashboard-basicauth (~48 tok)

## UpTimeKuma/

- `empty.md` (~1 tok)

## ZScaler-App-Connector/

- `empty.md` (~1 tok)
