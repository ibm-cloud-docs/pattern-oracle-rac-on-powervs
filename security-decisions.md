---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-22"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for security
{: #security-decisions}

The following are security architecture decisions for the Oracle RAC on Power Virtual Server resiliency pattern.

| Architecture decision | Requirements | Decision | Rationale |
|---|---|---|---|
| **Data encryption at rest** | | | |
| Primary storage | Ability to encrypt system volumes with BYOK | Key Protect or HPCS | By default, storage is encrypted. Use Key Protect for customer-managed key management. |
| Backup storage and archive storage | Ability to encrypt backups | Cloud Object Storage with Key Protect or HPCS | By default, all objects stored in IBM Cloud Object Storage are encrypted using randomly generated keys and an all-or-nothing-transform (AONT). You can use Key Protect for customer-managed key management. |
| Oracle data encryption | Ability to encrypt Oracle data at rest | Transparent Data Encryption (TDE) | TDE encrypts data on database storage media, such as table spaces and data files, and backup files. You can control TDE master keys in Key Protect. |
| **Data encryption in transit** | | | |
| Workload | Ability to encrypt data while in transit, to servers, between servers, and between PowerVS and any attached storage | Secrets Manager | Encryption that uses TLS 1.2 or higher. |
| **IAM** | | | |
| Identity access and role management | Securely authenticate users for platform services and control access to resources consistently across IBM Cloud | IBM Cloud IAM | Use IAM access policies to assign users, service IDs, and trusted profiles access to resources within the IBM Cloud account. |
| Privileged Identity and Access Management | Privileged access management services for administrative purposes | BYO Bastion host (or Privileged Access Gateway) with PAM software deployed in Edge VPC; 2FA authentication through IBM Security | Securely access remote resources over the private network for management purposes. Bastion host is accessed through SSH. Session recording tracks all activities, successful or not, to identify potential threats. |
| Core network protection | Isolated security zones between environments; isolated, private cloud environment | Separate VPCs, subnets, ACLs, and Security Groups separating application from DB as well as production and nonproduction environments; [Network Security Groups (NSGs)](/docs/power-iaas?topic=power-iaas-nsg) in PER-enabled PowerVS workspaces | A design combination using separate VPCs (transit, management, workload) connected through Transit Gateway and edge firewall capabilities. Subnets, Security Groups, and ACLs create an Edge/Transit VPC design. NSGs provide additional inbound traffic control at the PowerVS subnet and VSI level at no extra cost. |
{: caption="Security architecture decisions" caption-side="bottom"}
