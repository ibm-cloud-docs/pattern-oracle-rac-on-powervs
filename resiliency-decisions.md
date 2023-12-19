---

copyright:
  years: 2023
lastupdated: "2023-12-15"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for resiliency
{: #resiliency-decisions}

The following are resiliency architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| Architecture decision        | Requirements | Decision                    |Rationale                                                                                                                                                                                      |
|--------------------|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                  |                                        |                                                                                                                                                                                                                 |
| Backup - PowerVS   | Backup LPARS    | Built in Capture and Deploy (Snapshot) | * Additional Cloud Object Storage is required \n * Suitable for system disks back up and restore only                                                                                                                                      |
|                    |                  | IBM Spectrum Protect for AIX          | Deployment Options:  SP on AIX LPAR in PowerVS SP on IBM Cloud VPC Instance                                                                                                                                     |
|                    |                  | Veeam Backup Restore for AIX           | * Network Connection Required to Storage Target endpoint \n * Veeam Agent for IBM AIX v1 is a stand-alone product and does not integrate with other Veeam products nor can it send backups to a Veeam backup repository |
| Backup – Oracle    | Backup Database  | RMAN                                   | RMAN is a native back and recovery solution. For further best practices from oracle, see [Backup and Recovery Best Practices for the Oracle Database Appliance](https://www.oracle.com/docs/tech/oda-backup-recovery-technical-brief.pdf){: external}                                     |
{: caption="Table 1. Resiliency Architecture Decisions" caption-side="bottom"}

IBM Spectrum Protect is recommended. Veeam is a supported alternative option.
{: note}
