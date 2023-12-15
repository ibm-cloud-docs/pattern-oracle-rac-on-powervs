---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute considerations
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
For details on reserved capacity, see [Shared Processor Pools](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-manage-SPP)

When creating the PowerVS LPARS (also referred as instances and VMs)

Clients have the option to deploy LPARs in shared processor pool (SPP) to reduce 3rd part vendor license cost to enable LPARs to share the cpu capacity in the SPP, similar to on-premises (which has also placement policy option i.e., anti-affinity to make sure the LPARs for Oracle RAC are on different physical servers).

Dedicated cores allow no noisy neighbor and cost more as opposed to shared capped option. Recommendation is to set processor mode that matches client’s needs (dedicated, shared capped, shared uncapped). Clients will run production with shared capped in a shared pool unless they want dedicated cores.

There is also an option to select the appropriate policy between Same Server and Different Server under the placement group colocation policy. For Oracle RAC deployments, it is strongly recommended to select “Different Server” option for the placement group. When selected, a new server placement group is created to ensure that all LPARs in the group are deployed onto different physical servers. If additional RAC nodes need to be added later, the same specific server placement group must be specified to ensure that all LPARs of the cluster are deployed on different physical servers.

Users can also select the appropriate pinning option (Hard/Soft/None) from the Virtual server pinning list. Select the Hard pin option to restrict the movement of a LPAR to a different host. It is recommended to select Hard pin for LPARs running Oracle databases to control the use of licensed cores and to prevent LPM activity

There is an option to select between dedicated, capped shared, or uncapped shared processor mode for their virtual CPUs (vCPUs). Recommendation is to use shared uncapped for LPAR configuration and shared capped for the shared processor pool. Clients use dedicated cores to mitigate noisy neighbor in PowerVS multi-tenant environment for Production Oracle RAC workloads.

Select the processor mode and number of cores based on your Oracle licensing terms.

Leverage on-premise HMC report to review the current CPU and memory utilization, and performance of workloads and then right size LPARs in PowerVS

Leverage the resize LPAR function to change LPAR’s core and memory dynamically up to 8x the CPU and Memory of the initial allocations without restarting the LPAR (assuming required capacity is available on that physical server). If there’s a need to go above 8x the initial LPAR configuration, the user has to shut down the LPAR, configure and restart

Determine the need for a high availability (HA) solution for all non-production workloads such as Dev/Test/Non-Critical environments. Run at least one identical non-production/DR RAC environment to apply the patches and fixes to test before rolling out to production environments

Data centers with PowerVS systems are hosted in various regions globally
For up-to-date specifications, see [Power Virtual Server Infrastructure Customization](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-about-virtual-server#hardware-specifications)


For Oracle RAC, it is recommended to provision at least 2 nodes in a single zone on two separate physical servers using placement group for High Availability of production workload. Deviation from this setup can cause latency. Databases typically experience growth over time so database size and expected data growth rates should be taken into consideration when planning database deployments although there is the capability to extend storage capacity/volume size extension or add new shared volumes to the database.

-   For Oracle RAC workloads which require less than 12 cores and 950GB of memory select S922 system. S922 system CPU capacity ranges 0.25 to 15 cores and has up to 950GB memory

-   For Oracle RAC workloads requiring more than 12 cores and 950GB of memory select E980 system. E980 system CPU capacity ranges 0.25 to 143 cores and up to 22.5TB of memory
