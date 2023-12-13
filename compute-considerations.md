---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute Considerations
{: #compute-considerations}

Power Virtual Servers are available with flexible hardware configurations on both Power S922 and E980. It is permitted to define a custom size of the IBM Power Virtual Server to use for Oracle RAC

The Flexibility of IBM Power Systems Virtual Servers capability includes:

• Cores (CPU)

• Memory (RAM)

• Data volume size / volume type / performance tier

• Network interfaces (Public / Private)

• PowerVM Host Pinning Policy (soft or hard)

• PowerVM Host CPU Binding (dedicated or shared)

• Reserved Capacity via Shared Processor Pool Option
Note: For details on capabilities, check [here](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-creating-power-virtual-server#creating-power-virtual-server)

For Oracle RAC, it is recommended to provision at least 2 nodes in a single zone on two separate physical servers using placement group for High Availability of production workload. Deviation from this setup can cause latency. Databases typically experience growth over time so database size and expected data growth rates should be taken into consideration when planning database deployments although there is the capability to extend storage capacity/volume size extension or add new shared volumes to the database.

-   For Oracle RAC workloads which require less than 12 cores and 950GB of memory select S922 system. S922 system CPU capacity ranges 0.25 to 15 cores and has up to 950GB memory

-   For Oracle RAC workloads requiring more than 12 cores and 950GB of memory select E980 system. E980 system CPU capacity ranges 0.25 to 143 cores and up to 22.5TB of memory
