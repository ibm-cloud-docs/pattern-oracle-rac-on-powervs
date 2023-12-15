---

copyright:
  years: 2023
lastupdated: "2023-12-15"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Pattern overview
{: #overview}

Oracle RAC on IBM Power Systems Virtual Server (PowerVS) pattern allows customers to run a single Oracle Database across multiple servers/multiple virtual machines in a single zone, in order to maximize availability and enable horizontal scalability, while accessing shared storage. User sessions connecting to Oracle RAC instances can failover without any changes to end user applications.

The IBM Power Systems Virtual Server environment consists of SAN Storage, Power Systems servers, PowerVM Hypervisor, and AIX Operating Systems that are certified for Oracle DB (12c, 18c, 19c) including RAC. IBM PowerVS meets the current requirements of a certified and supported stack and Oracle RAC on IBM PowerVS is a supported configuration.

PowerVS is a fully contained, standalone offering and has its own management control plane. PowerVS is co-located with IBM Cloud Infrastructure with separate networks and direct-attached storage. The environment is in its own pod and the internal networks are fenced but offer connectivity options to IBM Cloud infrastructure or on-premises environments to meet customer requirements. PowerVS provides a simple and easy interface for creating shared storage and network resources required for Oracle RAC implementation. The implementation requires shared storage between the cluster nodes, and public and private networks for RAC communication between the nodes. These PowerVS connectivity options allow instances to easily integrate with IBM Cloud Services such as the Identity and Access Management (IAM) service to securely authenticate users, control access to PowerVS resources with resource groups, and allow access to specific resources for a set of users with access groups, and the Cloud Object Storage (COS) service to store backups.

The objective of this pattern is to provide a solution design for an [Oracle RAC](https://www.oracle.com/database/real-application-clusters/) Database deployment on [IBM Power Systems Virtual Server (PowerVS)](https://www.ibm.com/products/power-virtual-server) that meets high availability requirements for enterprise workloads. This pattern is intended to:

-   Accelerate and simplify solution design by providing a standard IBM PowerVS deployment architecture reference following the IBM Architecture Framework

-   Provide a prescriptive, end-to-end enterprise-class solution design, with diagrams, component architecture decisions along with a rationale for cloud component selection to meet enterprise requirements

-   Design a solution to meet performance, system availability and security needs

-   Focused on PowerVS (AIX) with IBM Cloud VPC
