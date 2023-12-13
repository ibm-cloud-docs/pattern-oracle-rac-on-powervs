---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Resiliency Architecture Decisions
{: #resiliency-decisions}

| **Architecture Decisions**        | **Requirements** | **Decision**                    |**Rationale**                                                                                                                                                                                       |
|--------------------|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Backup and Restore |                  |                                        |                                                                                                                                                                                                                 |
| Backup - PowerVS   | Backup  LPARS    | Built in Capture and Deploy (Snapshot) | Additional ICOS is required Suitable for system disks only backup/restore                                                                                                                                       |
|                    |                  | Spectrum Protect (SP) for AIX          | Deployment Options:  SP on AIX LPAR in PowerVS SP on IBM Cloud VPC Instance                                                                                                                                     |
|                    |                  | Veeam Backup Restore for AIX           | Network Connection Required to Storage Target endpoint Veeam Agent for IBM AIX v1 is a standalone product and does not integrate with other Veeam products nor can it send backups to a Veeam backup repository |
| Backup – Oracle    | Backup Database  | RMAN                                   | RMAN is a native back and recovery solution. For further best practices from oracle, click [here](https://www.oracle.com/docs/tech/oda-backup-recovery-technical-brief.pdf)                                     |
{: caption="Table 1. Resiliency Architecture Decisions" caption-side="bottom"}

Note: Spectrum Protect is recommended. An alternative option, Veeam is supported as well
