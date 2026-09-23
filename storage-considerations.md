---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-23"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Storage design
{: #storage-design}

PowerVS provides shared storage capability that is required for implementing Oracle RAC cluster and Oracle ASM. Oracle ASM (Automatic Storage Management) is used to provide data consistency across nodes in RAC. Oracle ASM is a critical component of Oracle RAC architecture.
{: shortdesc}

The storage tiers in Power Systems Virtual Server are based on I/O operations per second (IOPS). The performance of your storage volumes is limited to the maximum number of IOPS based on volume size and storage tier. The following storage tiers are available:

| Tier | IOPS performance | Example: 100 GB volume | Notes |
|------|-----------------|------------------------|-------|
| **Tier 0** | 25 IOPS/GB | 2,500 IOPS | Highest performance; 2.5x faster than Tier 1 and 8.3x faster than Tier 3 |
| **Tier 1** | 10 IOPS/GB | 1,000 IOPS | Recommended for standard Oracle RAC production workloads |
| **Tier 3** | 3 IOPS/GB | 300 IOPS | Suitable for lower I/O workloads, dev/test, and non-DB tiers |
| **Fixed IOPS** | 5,000 IOPS regardless of size | 5,000 IOPS | Limited to volumes of 200 GB or less; break-even with Tier 0 at 200 GB |
{: caption="Power Virtual Server storage tiers" caption-side="bottom"}

Tier 0 is recommended for Oracle RAC production workloads with the highest IOPS requirements. Tier 1 is appropriate for most production workloads as well as storing AIX and Oracle binaries for production use. Tier 3 storage can be selected for lower I/O tier workloads, such as dev or test environments. Fixed IOPS is typcially used in production to support Oracle Redo. When you choose a storage tier, consider not just the average I/O load but more importantly the peak IOPS of your storage workload.

Another key area is the Volume affinity and anti-affinity policy. It allows users to control the placement of a new volume based on an existing PVM instance (VM) or volume. When the user sets an affinity policy for a new storage volume, the volume is created within the same storage provider as an existing PVM instance or volume. With an anti-affinity policy, the new volume is created in a different storage provider other than the storage provider that the existing PVM instance or volume is located in. For Oracle RAC, select the anti-affinity policy to provision storage volumes across different storage pools within a data center

Object storage is designed for high durability, resiliency, and security and is the most efficient way to store database backups. IBM Cloud Object Storage can be used in the following use cases:

- [Capturing and exporting a virtual machine (VM)](/docs/power-iaas?topic=power-iaas-capturing-exporting-vm)

- [Importing a boot image](/docs/power-iaas?topic=power-iaas-importing-boot-image)

- [Backup repository](/docs/power-iaas?topic=power-iaas-backup-strategies)
