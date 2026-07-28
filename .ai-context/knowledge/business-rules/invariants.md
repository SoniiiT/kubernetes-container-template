# Observed invariants

These are source-backed implementation constraints, not newly invented product rules.

- **Rook creation order (explicit):** create `crds.yaml`, `common.yaml`, and `operator.yaml` before `cluster.yaml`, as documented in `Ceph-Rook/operator.yaml` and `Ceph-Rook/cluster.yaml`.
- **Ceph namespace coupling (explicit):** the Rook operator namespace, `CephCluster` namespace, StorageClass `clusterID`, provisioner prefix, and generated secret namespaces are expected to remain aligned.
- **Teleport identity (explicit):** the Teleport chart comments state that `clusterName` cannot change during a cluster lifespan; changing it requires a new cluster.
- **Ceph deletion guard (explicit):** the Ceph cleanup confirmation is empty by default; setting the documented destruction confirmation is an intentionally destructive operation.
- **Traefik address dependency (explicit):** the configured Traefik `loadBalancerIP` must belong to the MetalLB address range.
- **Ingress/TLS reference alignment (inferred):** an exposed route depends on the referenced service, namespace, TLS Secret, and issuer/certificate names existing in the same intended deployment scope. Evidence: repeated route and `Certificate` pairs across service directories.
- **Helm values pairing (inferred):** a values file must be rendered with the matching upstream chart and chart version; no chart source or lockfile is present locally.
