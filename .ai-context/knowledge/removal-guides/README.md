# Removal guidance

There are no service-specific approved removal runbooks in the repository. Use these safeguards for any removal:

- Identify whether the resource is shared infrastructure (`Traefik`, cert-manager, Rook-Ceph, MetalLB) or a leaf service.
- Search all manifests for namespace, Service, Secret, StorageClass, issuer, middleware, and route references before deleting.
- Snapshot or migrate persistent data before deleting PVCs, databases, Ceph resources, or host-backed storage.
- Remove ingress and certificates together, but retain shared issuers and middlewares while still referenced.
- Treat generated upstream files as replaceable artifacts and record the upstream source/version before removal.
- Validate the rendered/apply plan and perform a dry-run before destructive operations.
