---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute Architecture Decisions
{: #compute-decisions}

| **Architecture Decision**| **Requirements**| **Decision**| **Rationale**|
|--------------------------|------------------------------------------------------------|----------------------------------------------------------------------|-----------------------------------------|
| **Compute**  | Compute for Oracle RAC | Target environment to match specific workload requirements | [Power Systems Virtual Server](https://cloud.ibm.com/power/overview) | Hardware flexibility For production use |
{: caption="Table 1. Compute Architecture Decisions" caption-side="bottom"}

When creating the PowerVS LPARS (also referred as instances and VMs)

1.  Clients have the option to deploy LPARs in shared processor pool (SPP) to reduce 3rd part vendor license cost to enable LPARs to share the cpu capacity in the SPP, similar to on-premises (which has also placement policy option i.e., anti-affinity to make sure the LPARs for Oracle RAC are on different physical servers).

2.  Dedicated cores allow no noisy neighbor and cost more as opposed to shared capped option. Recommendation is to set processor mode that matches client’s needs (dedicated, shared capped, shared uncapped). Clients will run production with shared capped in a shared pool unless they want dedicated cores.

3.  There is also an option to select the appropriate policy between Same Server and Different Server under the placement group colocation policy. For Oracle RAC deployments, it is strongly recommended to select “Different Server” option for the placement group. When selected, a new server placement group is created to ensure that all LPARs in the group are deployed onto different physical servers. If additional RAC nodes need to be added later, the same specific server placement group must be specified to ensure that all LPARs of the cluster are deployed on different physical servers.

4.  Users can also select the appropriate pinning option (Hard/Soft/None) from the Virtual server pinning list. Select the Hard pin option to restrict the movement of a LPAR to a different host. It is recommended to select Hard pin for LPARs running Oracle databases to control the use of licensed cores and to prevent LPM activity

5.  There is an option to select between dedicated, capped shared, or uncapped shared processor mode for their virtual CPUs (vCPUs). Recommendation is to use shared uncapped for LPAR configuration and shared capped for the shared processor pool. Clients use dedicated cores to mitigate noisy neighbor in PowerVS multi-tenant environment for Production Oracle RAC workloads.

6.  Select the processor mode and number of cores based on your Oracle licensing terms.

Here are some additional considerations:

1.  Leverage on-premise HMC report to review the current CPU and memory utilization, and performance of workloads and then right size LPARs in PowerVS

2.  Leverage the resize LPAR function to change LPAR’s core and memory dynamically up to 8x the CPU and Memory of the initial allocations without restarting the LPAR (assuming required capacity is available on that physical server). If there’s a need to go above 8x the initial LPAR configuration, the user has to shut down the LPAR, configure and restart

3.  Determine the need for a high availability (HA) solution for all non-production workloads such as Dev/Test/Non-Critical environments. Run at least one identical non-production/DR RAC environment to apply the patches and fixes to test before rolling out to production environments

4.  Data centers with PowerVS systems are hosted in various regions globally
    Note: For up-to-date specifications, check [here](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-about-virtual-server)
