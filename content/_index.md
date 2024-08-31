+++
title = "Manage multiple accounts using AWS Control Tower and Identity Center"
date = 2021
weight = 1
chapter = false
+++

# Managing Multiple Accounts with AWS Control Tower and Identity Center

#### Introduction

In AWS projects, efficient operation and security assurance are top priorities. One of the best practices to achieve this is by separating environments (such as development, testing, production) across different AWS accounts. Such separation helps improve access control, isolate resources, and minimize security risks if an incident occurs in one account.

This article will guide you on using **AWS IAM Identity Center** (formerly AWS SSO) combined with **AWS Control Tower** to safely set up and manage a multi-account environment. **AWS Control Tower** helps establish a standardized landing zone, automating the creation of AWS accounts with built-in security and compliance measures. Meanwhile, **IAM Identity Center** simplifies managing access and permissions for users across AWS accounts, making it easy to control who can do what in each specific account.

#### AWS Control Tower
**AWS Control Tower** is a service that simplifies setting up and managing a secure, multi-account AWS environment that adheres to AWS best practices. It establishes a secure Landing Zone with AWS accounts, basic network architecture, and security and compliance controls.

#### Key features of AWS Control Tower include:
1. **Account Vending**: AWS Control Tower automates the creation of new AWS accounts, applying predefined policies and configurations during the account setup process. This helps ensure consistency and compliance across all accounts.
2. **Multi-account structure:** Control Tower sets up a multi-account environment based on AWS best practices, including the use of AWS Organizations to create and manage accounts, and Organizational Units (OUs) to organize accounts.
3. **Guardrails:** Control Tower implements guardrails, which are pre-configured policies, to enforce security, compliance, and operational best practices. Guardrails help prevent non-compliant actions and configurations.
   + **Detective Guardrails:** Provide visibility into the AWS environment, such as enabling AWS CloudTrail and AWS Config.
   + **Preventive Guardrails:** Prevent non-compliant actions or configurations, such as enforcing MFA for IAM users and blocking the creation of insecure S3 buckets.
   + **Infrastructure Guardrails:** Handle foundational aspects of the AWS environment, including setting up the AWS Landing Zone, organizing accounts, and configuring VPCs.
   + **Data Residency Guardrails:** Meet data storage and sovereignty requirements, such as setting appropriate AWS Regions.
   + **Operational Guardrails:** Focus on best operational practices, such as configuring AWS CloudWatch Alarms and defining backup and data retention policies.

#### Service Control Policies (SCPs)
**SCPs** are a type of guardrail that allows you to set detailed permissions and restrictions on services and actions within an account or OU, ensuring that only permitted actions can be performed.

#### Audit
Provides compliance monitoring capabilities through AWS Config and AWS CloudTrail, helping to track changes, ensure compliance, and investigate security incidents.

#### Centralized Logging and Monitoring
Integrates with **AWS Config**, **AWS CloudTrail**, and **AWS Config Rules** to provide centralized logging and monitoring capabilities, ensuring compliance and security for the AWS environment.

#### AWS Organizations
**AWS Organizations** is a service that helps organize and manage multiple AWS accounts in a centralized environment. It allows the creation of a hierarchical account structure with OUs and the application of SCPs to manage access and security across AWS accounts in the entire organization.

#### AWS IAM Identity Center (trước đây là SSO)
+ This service inherits AWS Single Sign-On and is a central user management service in an environment with multiple accounts operated in an AWS organization, making it easy for you to log in to each account.
+ It is the recommended service for managing human user access to AWS resources.
+ It allows you to connect not only AWS accounts but also Business Cloud Apps or Custom SAML 2.0-enabled Apps.
+ IAM Identity Center integrates with MS AD to store and retrieve user information.

![Diagram](/images/home/IAMIdentityCenter.png?width=60pc)

#### Contents:
1. [Overview ](1-overview)
2. [Set up Control Tower ](2-control-tower)
3. [Set up IAM Identity Center](3-iam-identity-center)
4. [Config SCP and Permission Sets](4-scp-permissionsets)
5. [Further Development ](5-further-development) 
6. [Testing the Results](6-testing)