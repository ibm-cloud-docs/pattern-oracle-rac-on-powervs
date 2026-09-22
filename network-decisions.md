---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-22"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for network
{: #network-decisions}

The following are network architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| Architecture decision | Requirements | Decision | Rationale |
|---|---|---|---|
| From Enterprise (on-premises) to PowerVS | Connectivity between client and IBM PowerVS | Redundant Direct Link (2.0) for HA | Preferred depending on security requirements. Lower cost than DL Dedicated and offers various bandwidth and metering options. |
| From Managed Service Providers | Secure, encrypted connectivity between MSPs and IBM Cloud | Site-to-Site VPN through VPC VPN Gateway | [VPN Gateway](/docs/vpc?topic=vpc-using-vpn) securely connects Virtual Private Cloud (VPC) to another private network (site-to-site) for management purposes. A VPN gateway consists of two back-end instances for high availability in the same zone. |
| From PowerVS to IBM Cloud VPC | Access cloud-native services in VPC | [Power Edge Router (PER)](/docs/power-iaas?topic=power-iaas-per) with Transit Gateway | PER is the current standard for PowerVS-to-VPC connectivity. It provides 400 Gbps aggregate bandwidth, direct access to IBM Cloud services via built-in NAT, and no additional charge. New workspaces are PER-enabled by default. Existing Cloud Connections workspaces should migrate to PER before 1 July 2025 to avoid metering charges. |
| Cloud-native connectivity (to cloud services) | Ability to connect to cloud services over the private network | Virtual Private Endpoints (VPE) | Communicate with IBM Cloud services over the private network by using a Virtual Private Endpoint (VPE). In PER-enabled workspaces, DNS, NTP, and Cloud Object Storage are also accessible directly through the PER built-in NAT. |
| Network segmentation or isolation | Ability to provide network isolation across workloads | VPCs, subnets, and [Network Security Groups (NSGs)](/docs/power-iaas?topic=power-iaas-nsg) | Native VPC isolation by using separate VPCs and subnets in PowerVS for production and nonproduction environments. In PER-enabled workspaces, NSGs provide additional inbound traffic filtering at the subnet and VSI level at no extra cost. |
| BYOIP | Bring Your Own IP (BYOIP) functionality | GRE (Generic Routing Encapsulation) tunnel | Connecting the PowerVS to Transit Gateway for routes to be advertised to enable on-premises user routing. |
| Load balancing (public) | Load balancing over the public network across two regions for DR failover | Cloud Internet Services (CIS) | Public load balancing for resiliency needs. |
| Domain Name System (DNS) | Ability to resolve DNS names on site | IBM continues to forward or relay DNS to client DNS servers on-site | This is the default option in the absence of a specific customer requirement to manage DNS. In PER-enabled workspaces, IBM Cloud DNS is also accessible directly. |
{: caption="Network architecture decisions" caption-side="bottom"}
