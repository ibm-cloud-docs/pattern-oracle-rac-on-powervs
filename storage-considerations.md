---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Storage considerations
{: #storage-considerations}

PowerVS provides shared storage capability that is required for implementing Oracle RAC cluster and Oracle ASM. Oracle ASM (Automatic Storage Management) is used to provide data consistency across nodes in RAC. Oracle ASM is a critical component of Oracle RAC architecture. For each Power Systems Virtual Server instance, the user has two options a) storage tier - Tier 1 (NVMe-based flash storage) and b) Tier 3 (SSD flash storage). The storage tiers in Power Systems Virtual Server are based on I/O operations per second (IOPS). This means that the performance of your storage volumes is limited to the maximum number of IOPS based on volume size and storage tier. Although the exact numbers might change over time, the Tier 1 storage is currently set to 10 IOPS/GB and the Tier 3 storage is currently set to 3 IOPS/GB. For example, a 100 GB Tier 1 storage volume can receive up to 1000 IOPS and a 100 GB Tier 3 storage volume can receive up to 300 IOPs.

Tier 1 is recommended for Oracle RAC production. Tier 3 storage can be selected for lower I/O tier workloads. When choosing a storage tier, consider not just the average I/O load, but more importantly the peak IOPS of your storage workload is considered.

Another key area is the Volume affinity and anti-affinity policy. It allows users to control the placement of a new volume based on an existing PVM instance (VM) or volume. When the user sets an affinity policy for a new storage volume, the volume is created within the same storage provider as an existing PVM instance or volume. With an anti-affinity policy, the new volume is created in a different storage provider other than the storage provider that the existing PVM instance or volume is located in. For Oracle RAC, select the anti-affinity policy, to provision storage volume(s) across different storage pool(s) within a data center

Object storage is designed for high durability, resiliency and security and is the most efficient way to store database backups. IBM Cloud Object Storage can be used in the following use cases:

-   [Capturing and exporting a virtual machine (VM)](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-capturing-exporting-vm)

-   [Importing a boot image](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-importing-boot-image)

-   [Backup repository](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-backup-strategies)
