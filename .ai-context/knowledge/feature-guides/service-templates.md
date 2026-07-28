# Service template guide

## Surfaces

Implemented chart-facing templates are in `Authentik/`, `GrayLog/`, `Homepage/`, `Kasm/`, `Kestra/`, `Moodle/`, `Portainer/`, and `Teleport/`. `NGINX-Web/` is a raw-manifest example. Service routes and certificates are separate files.

## Safe extension pattern

Pair a values change with the compatible upstream chart version and update the service route/certificate only when exposure changes. Identify embedded dependencies such as PostgreSQL, MariaDB, MongoDB, OpenSearch, Minio, Docker-in-Docker, or Redis before changing persistence or replicas.

## Test obligations

Use the chart's schema and rendered output, then validate namespaces, Service names, ports, PVCs, Secret references, RBAC, probes, and ingress behavior. The repository has no automated chart test harness.

## Removal

Delete or disable chart releases through the chart's supported lifecycle, preserve persistent data until migration is complete, remove route/certificate pairs, and clean only service-specific RBAC and Secrets after confirming no shared consumer remains.
