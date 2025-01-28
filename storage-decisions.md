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

| Architecture decision                    | Requirements    | Decision   | Rationale                                                         |
|--------------------------------|----------------------|----------------------|----------------------------------------------------------------------------------------|
| Primary Storage Production     | Oracle Production DB | Tier 1               | Tier 1 is recommended for Oracle RAC production                                        |
| Primary Storage Non-Production | Oracle dev or test DB   | Tier 3               | Recommended for all non-DB tiers (App. Servers) as well as the nonproduction DB LPARs |
| Backup Storage                 | For DB backup        | Tier 3               | Backup of DB by using RMAN                                                                |
| Archive Storage                | For all LPARS        | Cloud Object Storage | Recommended for cost effective, long-term backups                               |
{: caption="Storage Architecture Decisions" caption-side="bottom"}
