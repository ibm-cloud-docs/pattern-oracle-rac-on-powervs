---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Requirements
{: #requirements}

The following represents a baseline set of requirements which are applicable to most clients and critical to successful Oracle RAC on PowerVS deployment.

| **Aspect**                     | **Requirement**                                                                                                                                                                                                     |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Compute**        | Provide different levels of cpu and memory options to match the type of workloads                                                                                                                                                      |
| **Storage**        | Provide different storage Tier level for type of workloads                                                                                                                                                                             |
| **Network**        | Enterprise connectivity to customer data center(s) to provide access to applications from on-prem                                                                                                                                      |
|                                 | Provide network isolation with the ability to segregate applications based on attributes such as data classification, public vs internal apps and function                                                                             |
|                                 | Maintain IP addresses in the target (BYOIP)                                                                                                                                                                                            |
| **Security**       | Provide data encryption at rest                                                                                                                                                                                                        |
|                                 | IDS/IAM Services to target IBM PowerVS environment                                                                                                                                                                                     |
|                                 | Firewalls must be restrictively configured to provide advanced security features and prevent all traffic, both inbound and outbound, except that which is specifically required, documented, and approved and include IPS/IDS services |
| **Resiliency**     | Multi-Region capability to support disaster recovery strategy and solution that allows all production applications to be included leveraging cloud infrastructure DR capabilities                                                      |
|                                 | RTO/RPO = 4 hours/15 minutes; rollback to original environments should occur no later than specified RTOs                                                                                                                              |
|                                 | Provide backup for Infrastructure components and Database hosted in the cloud environment.                                                                                                                                             |
| **Observability**  | Provide Health and System Monitoring with ability to monitor and correlate performance metrics and events and provide alerting across applications and infrastructure                                                                  |
|                                 | Ability to diagnose issues and exceptions and identify error source                                                                                                                                                                    |
|                                 | Automate management processes to keep applications and infrastructure secure, up to date, and available                                                                                                                                |
| **Other**          | Migrate workloads from existing data center to IBM PowerVS                                                                                                                                                                             |
{: caption="Table 1. Oracle RAC on PowerVS Requirements" caption-side="bottom"}
