---

copyright:
  years: 2023
lastupdated: "2023-12-15"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for storage
{: #storage-decisions}

The following are storage architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| **Architecture Decision**                    | **Requirements**     | **Decision**   | **Rationale**                                                              |
|--------------------------------|----------------------|----------------------|----------------------------------------------------------------------------------------|
| Primary Storage Production     | Oracle Production DB | Tier 1               | Tier 1 is recommended for Oracle RAC production                                        |
| Primary Storage Non-Production | Oracle Dev/Test DB   | Tier 3               | Recommended for all non-DB tiers (App. Servers) as well as the non-production DB LPARs |
| Backup Storage                 | For DB backup        | Tier 3               | Backup of DB using RMAN                                                                |
| Archive Storage                | For all LPARS        | Cloud Object Storage | Recommended for cost effective, long term backups                               |
{: caption="Table 1. Storage Architecture Decisions" caption-side="bottom"}
