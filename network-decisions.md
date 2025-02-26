---

copyright:
  years: 2023
lastupdated: "2023-12-15"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for network
{: #network-decisions}

The following are network architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| Architecture decision                                   | Requirements                                                                                                           | Decision                                                      | Rationale                                                                                                                                                                                                                                                   |
|-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| From Enterprise (on-premises) to PowerVS       | Connectivity that is needed between client and IBM PowerVS                                                                         | Redundant Direct Link (2.0) for H/A                                     | Preferred depending on security requirements. Lower cost than DL Dedicated and offers various bandwidth and metering options                                                                                                                                        |
| From Managed Service Providers                | Secure, encrypted connectivity between MSPs and IBM Cloud                                                                  | Site-to-Site VPN through VPC VPN Gateway                                | [VPN Gateway](/docs/vpc?topic=vpc-using-vpn) - securely connect Virtual Private Cloud (VPC) to another private network (site-to-site) for management purposes. A VPN gateway consists of two back-end instances for high availability in the same zone |
| From PowerVS to IBM Cloud VPC                 | Access Cloud Native services in VPC                                                                                        | Redundant Direct Link (2.0) for H/A                                     | DL and Transit Gateway(TGW), both are required for PowerVS to VPC network connectivity. DL is included as part of the PowerVS offering for this connectivity only                                                                                                                            |
| Cloud Native Connectivity (to cloud services) | Ability to connect to cloud services over the private network                                                              | Virtual Private Endpoints                                               | Communicate with IBM Cloud services over the private network by using a Virtual Private Endpoint (VPE)                                                                                                                                                                         |
| Network segmentation or isolation                | Ability to provide network isolation across workloads                                                                      | VPCs and subnets separate PowerVS LPARs                                 | Native VPC isolation by using separate VPCs and subnets in PowerVS for prod, nonprod environments for separation of workload or separation of PowerVS LPARs                                                                                                      |
| BYOIP                                         | Bring Your Own IP (BYOIP) functionality                                                                                    | GRE (Generic Routing Encapsulation) Tunnel                               | Connecting the PowerVS to TGW for routes to be advertised to enable on-premises user routing                                                                                                                                                                                 |
|  Load Balancing (Public)                      | Load balancing over the public network across two regions if an outage occurs (DR) for failover to the other region. | Cloud Internet Services (CIS)                                           | Public load balancing for resiliency needs.                                                                                                                                                                                                                                 |
| Domain Name System (DNS)                      | Ability to resolve DNS names on site                                                                                       | IBM continues to forward or relay the DNS to client DNS Servers onsite | This is the default option in the absence of a specific customer requirement to manage DNS                                                                                                                                                                                  |
{: caption="Network Architecture Decisions" caption-side="bottom"}
