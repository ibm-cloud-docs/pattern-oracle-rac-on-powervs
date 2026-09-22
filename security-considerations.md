---

copyright:
  years: 2023, 2025
lastupdated: "2026-09-22"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Security design
{: #security-design}

IBM provides a cloud-based key management services that integrate with PowerVS: Key Protect.
{: shortdesc}

- IBM Key Protect is a full-service multi-tenant encryption solution that allows data to be secured and stored in IBM Cloud by using envelope encryption techniques. You can integrate Key Protect with Power Systems Virtual Server to securely store and protect encryption key information for AIX and Linux.

For more information, see [Integrating Power Virtual Server with IBM Cloud Key Management Services](/docs/power-iaas?topic=power-iaas-integrate-hpcs).

Transparent Data Encryption (TDE) is a well-established technology to encrypt sensitive data in databases. TDE is used by Oracle Database. With TDE, a database system encrypts data on database storage media, such as table spaces and files, and on backup media. The database system automatically and transparently encrypts and decrypts data when it is used by authorized users and applications. Database users do not need to be aware of TDE and database applications do not need to be adapted specifically for TDE. Typically, TDE uses a two-tiered key hierarchy: a TDE master encryption key and a TDE data encryption key. The TDE data encryption key is used to encrypt and decrypt user data. The TDE master encryption key is used to encrypt and decrypt the TDE data encryption key. You can keep complete and exclusive control of TDE master encryption keys by storing them in IBM Cloud Hyper Protect Crypto Services by using the PKCS #11 integration feature. For more information, see [Using Hyper Protect Crypto Services PKCS #11 for Oracle Transparent Database Encryption](/docs/hs-crypto?topic=hs-crypto-tutorial-tde-pkcs11).

## Network security groups
{: #security-nsg}

In Power Edge Router (PER)-enabled PowerVS workspaces, you can use **Network Security Groups (NSGs)** to enforce network-level security for Oracle RAC LPARs. NSGs define inbound security rules to allow or deny specific traffic based on source, destination, port, and protocol (TCP, UDP, ICMP). All outbound traffic is automatically allowed.

NSGs provide an additional layer of microsegmentation within the PowerVS environment that complements VPC security groups, ACLs, and firewall controls in the Edge VPC. You can use NSGs to restrict access to RAC cluster interconnect subnets, limit database listener ports to specific source CIDRs, and prevent unauthorized lateral movement between LPARs.

NSGs are included at no additional cost and do not affect network throughput or latency. For more information, see [Network security groups in IBM Power Virtual Server](/docs/power-iaas?topic=power-iaas-nsg).
