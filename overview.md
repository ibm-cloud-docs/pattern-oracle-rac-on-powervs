---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Pattern Overview
{: #overview}

The objective of this pattern is to provide a solution design for an [Oracle RAC](https://www.oracle.com/database/real-application-clusters/) Database deployment on [IBM Power Systems Virtual Server (PowerVS)](https://www.ibm.com/products/power-virtual-server) that meets high availability requirements for enterprise workloads. This pattern is intended to:

-   Accelerate and simplify solution design by providing a standard IBM PowerVS deployment architecture reference following the IBM Architecture Framework

-   Provide a prescriptive, end-to-end enterprise-class solution design, with diagrams, component architecture decisions along with a rationale for cloud component selection to meet enterprise requirements

-   Design a solution to meet performance, system availability and security needs

-   Focused on PowerVS (AIX) with IBM Cloud VPC

**Note:** As new features and products are made available such as Power 10 systems, Power Edge Router (PER), Monitoring and Logging enhancements, this document will be refreshed.

Oracle RAC on IBM Power Systems Virtual Server (PowerVS) pattern allows customers to run a single Oracle Database across multiple servers/multiple virtual machines in a single zone, in order to maximize availability and enable horizontal scalability, while accessing shared storage. User sessions connecting to Oracle RAC instances can failover without any changes to end user applications.

The IBM Power Systems Virtual Server environment consists of SAN Storage, Power Systems servers, PowerVM Hypervisor, and AIX Operating Systems that are certified for Oracle DB (12c, 18c, 19c) including RAC. IBM PowerVS meets the current requirements of a certified and supported stack. Oracle RAC on IBM PowerVS is a supported configuration.

PowerVS is a fully contained, standalone offering and has its own management control plane. PowerVS is co-located with IBM Cloud Infrastructure with separate networks and direct-attached storage. The environment is in its own pod and the internal networks are fenced but offer connectivity options to IBM Cloud infrastructure or on-premises environments to meet customer requirements. PowerVS provides a simple and easy interface for creating shared storage and network resources required for Oracle RAC implementation. The implementation requires shared storage between the cluster nodes, and public and private networks for RAC communication between the nodes. These PowerVS connectivity options allow instances to easily integrate with IBM Cloud Services such as the Identity and Access Management (IAM) service to securely authenticate users, control access to PowerVS resources with resource groups, and allow access to specific resources for a set of users with access groups, and the Cloud Object Storage (COS) service to store backups.

Following the Architecture Framework, the Oracle RAC on PowerVS covers design considerations for the following aspects and domains:

-   **Compute:** Power Systems Virtual Servers

-   **Storage:** Primary Storage, Backup Storage

-   **Networking:** Enterprise Connectivity, Segmentation, Cloud Native Connectivity, DNS

-   **Security:** Data Security, Application Security, Infrastructure Security

-   **Resiliency:** Backup and Restore, High Availability, Disaster Recovery

-   **Observability:** Monitoring, Logging, Auditing

The Architecture Framework provides a consistent approach to design cloud solutions by addressing requirements across a set of "aspects" and "domains", which are technology-agnostic architectural areas that need to be considered for any enterprise solution. See [Introduction to the Architecture Framework](https://cloud.ibm.com/docs/architecture-framework?topic=architecture-framework-intro) for more details.
