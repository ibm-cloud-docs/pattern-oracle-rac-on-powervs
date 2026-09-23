---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-23"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for compute
{: #compute-decisions}

The following are compute architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| Architecture decision | Requirements | Decision | Rationale |
|---|---|---|---|
| Compute for Oracle RAC (standard workloads) | Target the environment to match specific workload requirements | [Power Systems Virtual Server](https://cloud.ibm.com/power/overview){: external} — Power10 systems (S1022, E1080) or Power11 systems (S1122, E1150)recommended for new deployments | Power10 and Power11 systems provide improved performance, a 3.0:1 virtual-core-to-entitled-capacity ratio in SPPs (versus 1:1 on Power9), and broader data center availability. |
| Compute for Oracle RAC (maximum isolation) | Oracle license cost control, single-tenant isolation, or hard-partitioning requirements | [Dedicated host](/docs/power-iaas?topic=power-iaas-dedicated-host) | A dedicated host provides a single-tenant server with up to a 20:1 VP-to-EC ratio and full control over LPAR placement, supporting hard-partitioning for Oracle license management. |
{: caption="Compute architecture decisions" caption-side="bottom"}
