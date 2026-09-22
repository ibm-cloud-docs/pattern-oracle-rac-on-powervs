---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-22"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for storage
{: #storage-decisions}

The following are storage architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| Architecture decision | Requirements | Decision | Rationale |
|---|---|---|---|
| Primary Storage Production (high I/O) | Oracle production DB with highest IOPS requirements | Tier 0 | Tier 0 delivers 25 IOPS/GB — 2.5x faster than Tier 1 — and is recommended for the most demanding Oracle RAC production workloads |
| Primary Storage Production (standard) | Oracle production DB | Tier 1 | Tier 1 delivers 10 IOPS/GB and is appropriate for most Oracle RAC production workloads |
| Primary Storage Non-Production | Oracle dev or test DB | Tier 3 | Recommended for all non-DB tiers (app servers) as well as nonproduction DB LPARs |
| Backup Storage | For DB backup | Tier 3 | Backup of DB by using RMAN |
| Archive Storage | For all LPARs | Cloud Object Storage | Recommended for cost-effective, long-term backups |
{: caption="Storage architecture decisions" caption-side="bottom"}
