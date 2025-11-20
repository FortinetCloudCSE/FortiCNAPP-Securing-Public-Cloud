---
title: "FortiCNAPP Deployment Modes"
linkTitle: "Chapter 1: Cloud Integrations"
weight: 2
#archetype: "chapter"
---

### Introduction 
In this chapter, we'll access our FortiCNAPP instance and take the first step for ingesting data from the cloud environment. Before we do that, let's take a quick look at the supported options.

#### Supported Cloud Service Providers

##### Amazon Web Services (AWS) ![aws](img/aws.png)
AWS is supported for CloudTrail Log ingestion and service configuration. FortiCNAPP utilizes a cross account role with a combination of AWS managed policies and customer managed policies for specific service APIs. Due to the large number of AWS services, multiple custom polices are created. 

**NOTE:** Fortinet avoids the use of wildcards to shorten the number of policies, which is an anti-pattern in managing cloud identities.

Supported methods for integration with AWS include CloudFormation templates and Terraform modules. You can optionally create resources manually using the AWS portal and/or AWS SDKs. The integration templates create several resources for the data collection process:

1. CloudTrail trail (you may also choose an existing trail)
2. CloudTrail S3 bucket
3. CloudTrail SNS topic
4. SQS queue for topic messages
5. IAM role and policies
6. KMS Keys (for encrypting resources)


##### Microsoft Azure ![azure](img/azure.png)
Azure is supported for Cloud Activity Log ingestion and service configuration. FortiCNAPP utilizes a service principal (app  registration) with Directory Reader role to connect to the Azure tenant and evaluate service configurations for commonly used services such as virtual machines, storage accounts, databases, functions, and app instances. To do so, several Microsoft resource providers are registered. For activity logs, FortiCNAPP creates a diagnostic configuration to send logs to a storage account queue for retrieval. 

Supported methods for integration with Azure include Terraform modules and manual configuration through the Microsoft portal or the CLI. The required resources for the data collection process include:

1. App Registration
2. Client Secret
3. Storage Account
4. Diagnostic Configuration
5. Least-privileged Custom Role


##### Google Cloud Platform (GCP) ![gcp](img/gcp.png)
Google Cloud is supported for Audit Log ingestion and service configuration. FortiCNAPP creates a service account and custom role to use for accessing the Google account. GCP requires manually enabling APIs for any services you wish to interact with. For Audit Logs, FortiCNAPP utilizes a pub/sub configuration with a log router and sink. 

Supported methods for integration with GCP include Terraform modules and manual configuration through the Google Cloud portal or the CLI. The required resources for the data collection process include:

1. Service Accounts 
2. Pub/sub topic & subscription (queue)
3. Log router & sink
4. GCP credentials
5. Custom IAM Role
6. IAM Role bindings


##### Oracle Cloud Infrastructure (OCI) ![oci](img/oci.png)
FortiCNAPP currently offers support for OCI in the form of service configuration. OCI customers can benefit from compliance analysis against common OCI services and generate CIS benchmark reports, as well as a full resource inventory. 

Supported methods for integration with OCI include a Terraform module and manual configuration through the OCI portal or the CLI. The required resources for the data collection process include:

1. OCI User
2. OCI Group
3. OCI User Policy
4. OCI API Key


#### Our First Integration
Let's access our FortiCNAPP instance for the first time and integrate our cloud accounts. Click on the link below to launch FortiCNAPP in your browser. 

**Click this [Link](https://lwint-test-onboarding.lacework.net) to access the portal!**