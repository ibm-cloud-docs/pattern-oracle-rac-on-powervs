---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-23"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute design
{: #compute-design}

Power Virtual Servers are available with flexible hardware configurations across multiple IBM Power server generations. You can define a custom size of the IBM Power Virtual Server to use for Oracle RAC.
{: shortdesc}

The following IBM Power servers can host a Power Virtual Server:

| System | Model | Generation |
| - | - | - |
| IBM Power System S1022 | 9105-22A | Power10 |
| IBM Power System E1080 | 9080-HEX | Power10 |
| IBM Power System E1050 | 9043-MRX | Power10 |
| IBM Power System S1122 | 9824-22A | Power11 |
| IBM Power System E1150 | 9043-MRU | Power11 |
{: caption="IBM Power server types available for Power Virtual Server" caption-side="bottom"}

For new Oracle RAC deployments, Power10 (S1022, E1080) or Power11 (S1122, E1150) systems are recommended for improved performance, higher virtual-core density, and better Oracle licensing flexibility. Not all server types are available in every data center. See [Power Virtual Server Infrastructure Pricing](/docs/power-iaas?topic=power-iaas-pricing-virtual-server-on-cloud) to confirm availability for your target region.

The Flexibility of IBM Power Systems Virtual Servers capability includes:

* Cores (CPU)
* Memory (RAM)
* Data volume size, volume type, performance tier
* Network interfaces (public or private)
* PowerVM Host Pinning Policy (soft or hard)
* PowerVM Host CPU Binding (dedicated or shared)
* Reserved Capacity through Shared Processor Pool Option

For details on reserved capacity, see [Shared Processor Pools](/docs/power-iaas?topic=power-iaas-manage-SPP).

When you create the PowerVS LPARs (also referred to as instances and VMs):

Clients have the option to deploy LPARs in a shared processor pool (SPP) to reduce third-party vendor license cost. LPARs share the CPU capacity in the SPP, similar to an on-premises deployment. The SPP also has a placement policy option (anti-affinity) to make sure the LPARs for Oracle RAC are on different physical servers.

On Power10 and later systems, you can provision a VSI in an SPP with up to a **3.0:1 virtual core–to–entitled capacity ratio** for entitled capacities up to 3.0 cores. On Power9 systems, the ratio is 1:1. This Power10 capability allows greater workload density and can reduce Oracle processor license costs.

Dedicated cores allow no noisy neighbor and cost more than the shared capped option. The recommendation is to set a processor mode that matches the client's needs (dedicated, shared capped, shared uncapped). Clients run production with shared capped in a shared pool unless they require dedicated cores.

## Dedicated hosts
{: #compute-dedicated-hosts}

For Oracle RAC workloads with the most stringent requirements for Oracle license cost control, performance isolation, and security, IBM Power Virtual Server offers **dedicated hosts**. A dedicated host is a single-tenant, dedicated server that provides total isolation from other tenants. Key benefits include:

- An increased virtual-processor-to-entitled-capacity ratio of up to **20:1**
- Detailed visibility of host capacity information including core and memory consumption
- Ability to control placement of all virtual server instances across the dedicated host
- Can also include a shared processor pool capability unique to the host

For more information, see [Getting started with dedicated hosts](/docs/power-iaas?topic=power-iaas-dedicated-host).

## Placement and pinning
{: #compute-placement-pinning}

There is also an option to select the appropriate policy between Same Server and Different Server under the placement group colocation policy. For Oracle RAC deployments, it is strongly recommended to select the **Different Server** option for the placement group. When selected, a new server placement group is created to ensure that all LPARs in the group are deployed onto different physical servers. If more RAC nodes need to be added later, the same specific server placement group must be specified to ensure that all LPARs of the cluster are deployed on different physical servers.

You can also select the appropriate pinning option (Hard/Soft/None) from the Virtual server pinning list. Select the Hard pin option to restrict the movement of an LPAR to a different host. It is recommended to select Hard pin for LPARs running Oracle databases to control the use of licensed cores and to prevent Live Partition Mobility (LPM) activity.

There is an option to select between dedicated, capped shared, or uncapped shared processor mode for virtual CPUs (vCPUs) deployed into a shared process pool (SPP). The recommendation is to use shared uncapped for LPAR configuration and shared capped for the shared processor pool. Clients use dedicated cores to mitigate noisy neighbors in the PowerVS multi-tenant environment for production Oracle RAC workloads.

Select the processor mode and number of cores based on your Oracle licensing terms.

Use an on-premises HMC report to review the current CPU and memory utilization and performance of workloads, and then right size LPARs in PowerVS.

Use the resize LPAR function to change an LPAR's cores and memory dynamically up to 8x the initial allocations without restarting the LPAR (assuming that the required capacity is available on that physical server). If there is a need to go above 8x the initial LPAR configuration, the user must shut down the LPAR, configure it, and restart.

Determine the need for a high availability (HA) solution for all nonproduction workloads such as dev, test, or noncritical environments. Run at least one identical nonproduction or DR RAC environment to apply patches and fixes before you roll out to production environments.

For Oracle RAC, it is recommended to provision at least two nodes in a single zone on two separate physical servers that use a placement group for high availability of production workloads. Deviation from this setup can cause latency. Databases typically experience growth over time, so database size and expected data growth rates should be considered when you plan database deployments. You can extend storage capacity by using volume size extension or by adding new shared volumes to the database.

For up-to-date specifications on available cores and memory for each system type, see [Power Virtual Server Infrastructure Pricing](/docs/power-iaas?topic=power-iaas-pricing-virtual-server-on-cloud).
