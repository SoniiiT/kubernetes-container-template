# Rook-Ceph storage feature guide

## Surfaces

- CRDs, common RBAC, operator: `Ceph-Rook/crds.yaml`, `Ceph-Rook/common.yaml`, `Ceph-Rook/operator.yaml`.
- Cluster topology: `Ceph-Rook/cluster.yaml`.
- Block and shared-file storage: `Ceph-Rook/storageclass-block-storage.yaml` and `Ceph-Rook/storageclass-shared-file-storage.yaml`.
- Dashboard exposure: `Ceph-Rook/dashboard-external-ingress.yaml`.

## Dependencies and extension points

The operator and CRDs must exist before `CephCluster`; StorageClasses depend on the cluster namespace, pools, filesystem, CSI drivers, and generated Secrets. PVC consumers should refer to the StorageClass names rather than hard-coding Ceph internals.

## Safe change obligations

Use pinned operator and Ceph images, confirm node/device capacity and failure-domain assumptions, validate CSI support, and test PVC provisioning/expansion before rollout. Do not set cleanup confirmation casually; cluster and host data can be destroyed.

## Removal

Inventory PVCs and data consumers first. Remove workloads before StorageClasses and cluster resources, preserve or migrate data, and follow Rook's documented teardown process. Never treat deleting `CephCluster` or host data as a routine cleanup.
