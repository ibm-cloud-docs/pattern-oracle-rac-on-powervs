---

copyright:
  years: 2023
lastupdated: "2023-11-28"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Security considerations
{: #security-considerations}

IBM provides two cloud based key management services that integrate with PowerVS, Key Protect Service which is BYOK and Hyper Protect Crypto Service which is KYOK.

-   IBM Key Protect is a full-service multi-tenant encryption solution that allows data to be secured and stored in IBM Cloud using the latest envelope encryption techniques. User can integrate Key Protect with Power Systems Virtual Server to securely store and protect encryption key information for AIX

-   IBM Cloud Hyper Protect Crypto Services (HPCS) is a dedicated key management service and hardware security module (HSM) based on IBM Cloud. User can integrate HPCS with Power Systems Virtual Server to securely store and protect encryption key information for AIX

More details can be found in [Integrating Power Virtual Server with IBM Cloud Key Management Services](https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-integrate-hpcs).

Transparent Data Encryption (TDE) is a well-established technology to encrypt sensitive data in databases. TDE is used by Oracle database. With TDE, a database system encrypts data on database storage media, such as table spaces and files, and on backup media. The database system automatically and transparently encrypts and decrypts data when it is used by authorized users and applications. Database users do not need to be aware of TDE and database applications do not need to be adapted specifically for TDE. Typically, TDE uses a two-tiered key hierarchy, which is composed of a TDE master encryption key and a TDE data encryption key. The TDE data encryption key is used to encrypt and decrypt user data, while the TDE master encryption key is used to encrypt and decrypt the TDE data encryption key. User can keep complete and exclusive control of their TDE master encryption keys by storing them in IBM Cloud Hyper Protect Crypto Services. For this purpose, users need to utilize the PKCS \#11 integration feature of Hyper Protect Crypto Services. More details can be found in [Using Hyper Protect Crypto Services PKCS #11 for Oracle Transparent Database Encryption](https://cloud.ibm.com/docs/hs-crypto?topic=hs-crypto-tutorial-tde-pkcs11).
