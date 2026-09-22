---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-22"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for resiliency
{: #resiliency-decisions}

The following are resiliency architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| Architecture decision | Requirements | Decision | Rationale |
|---|---|---|---|
| Backup - PowerVS (managed service) | Backup LPARs with a fully managed, cloud-native option | [Secure Automated Backup with Compass for PowerVS](https://cloud.ibm.com/catalog){: external} (Cobalt Iron) | Fully managed backup-as-a-service available from the IBM Cloud catalog. Supports AIX, Linux, and IBM i. Available in single-copy and dual-copy (cross-region) configurations. Billed monthly based on stored data after deduplication and compression. |
| Backup - PowerVS (self-managed) | Backup LPARs with client-managed tooling | Built-in Capture and Deploy (Snapshot) | Additional Cloud Object Storage is required. Suitable for system disk backup and restore only. |
|  |  | IBM Storage Protect for AIX | Deployment options: IBM Storage Protect on an AIX LPAR in PowerVS, or on an IBM Cloud VPC instance. |
|  |  | Veeam Backup and Restore for AIX | Network connection required to storage target endpoint. Veeam Agent for IBM AIX is a stand-alone product and does not integrate with other Veeam products or send backups to a Veeam backup repository. |
| Backup - Oracle | Backup database | RMAN | RMAN is a native backup and recovery solution. For further best practices, see [Backup and Recovery Best Practices for the Oracle Database Appliance](https://www.oracle.com/docs/tech/oda-backup-recovery-technical-brief.pdf){: external}. |
| Storage replication for DR | Infrastructure-level asynchronous replication for disaster recovery | [Global Replication Services (GRS)](/docs/power-iaas?topic=power-iaas-getting-started-GRS) | GRS provides SAN-based asynchronous volume replication between fixed IBM Cloud regional data center pairs, using IBM FlashSystem Global Mirror Change Volume (GMCV) technology. Complements Oracle Data Guard as an infrastructure DR layer. No dedicated replication network is required. |
{: caption="Resiliency architecture decisions" caption-side="bottom"}

IBM Storage Protect is recommended for self-managed OS-level backup. Cobalt Iron Compass is recommended when a fully managed backup service is preferred. Veeam is a supported alternative option.
{: note}
