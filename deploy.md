---
copyright:
  years: 2025, 2026
lastupdated: "2026-09-24"

subcollection: pattern-oracle-rac-on-powervs

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Deploying Oracle RAC on PowerVS pattern

{: #rac-pattern-overview}

This guide outlines on using a deployable architecture to assist you in deploying 2 node Oracle Real Application Cluster (RAC) into IBM Power Virtual Server running AIX.  The deployment creates and prepares Power Virtual Server instances for Oracle RAC database workloads. 


## Before you begin
{: #rac-pattern-prereqs}

You need the following items to deploy and configure this reference architecture:

* An [IBM Cloud account](https://cloud.ibm.com/registration).
* Required IAM access policies.
* Some manual steps are required.  Follow the [Planning section](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-powervs-oracle-97af9ca3-851c-4c09-9afb-4cdcebd4f4a2-global/readme/terraform/terraform/58e0274d-7756-47fb-a6ba-785fc7659fb9-global) within the deployable architecture.

  
## Provision Architecture
{: #rac-pattern-provision}

You can provision the PowerVS Automation for Oracle Real Application Clusters pattern via the IBM Cloud catalog.  

1. Access the [PowerVS Automation for Oracle Real Application Clusters](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-powervs-oracle-97af9ca3-851c-4c09-9afb-4cdcebd4f4a2-global?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2Fc2VhcmNoPXBvd2VydnMjc2VhcmNoX3Jlc3VsdHM%3D&kind=terraform&format=terraform&version=58e0274d-7756-47fb-a6ba-785fc7659fb9-global) deployable architecture to provision.

## Additonal Services
{: #rac-pattern-additonal}

You can add additional services onto the PowerVS Automation for Oracle Real Application Clusters pattern.  The addtional services include:

1. [Account Infrastructure base](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-account-infra-base-63641cec-6093-4b4f-b7b0-98d2f4185cd6-global) for creating and configuring the foundational components of an IBM Cloud account.
2. [IBM Cloud VPC Landing Zone](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-slz-vsi-ef663980-4c71-4fac-af4f-4a510a9bcf68-global?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2Fc2VhcmNoPWxhbmRpbmcjZGVwbG95YWJsZV9hcmNoaXRlY3R1cmVfdGFi&kind=terraform&format=terraform&version=bac4140a-512e-4a68-b566-498275ea2c9e-global) for creating and configuring a IBM Cloud VPC with VSI's.
2. [IBM Cloud Observability](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-observability-a3137d28-79e0-479d-8a24-758ebd5a0eab-global) for provisioning and configuring logging, monitoring, and activity tracking.
3. [IBM Cloud Event Notifications](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-event-notifications-c7ac3ee6-4f48-4236-b974-b0cd8c624a46-global) for a high-throughput message bus that is built with Apache Kafka.
4. [ Security and Compliance Center Workload Protection](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-scc-workload-protection-4322cf44-2289-49aa-a719-dd79e39b14dc-global?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2Fc2VhcmNoPXNlY3VyaXR5I3NlYXJjaF9yZXN1bHRz) for compliance posture of your deployed resources.
