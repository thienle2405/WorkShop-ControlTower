+++
title = "Cleaning Up Resources"
date = 2021-06-08T18:57:03+07:00
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

To delete **AWS IAM Identity Center**, **AWS Control Tower**, and **AWS Organizations**, you need to carefully follow the steps to ensure that all related resources and configurations are properly removed without affecting your AWS environment. Below is a detailed step-by-step guide:

### Delete AWS IAM Identity Center
**Note:** Before deleting AWS IAM Identity Center, ensure that you no longer need the identity and access management configurations of this service.

**Steps to follow:**

**1. Delete Permission Sets:**
   - Access the AWS Management Console.
   - Navigate to IAM Identity Center (formerly AWS SSO).
   - Select Permission Sets, and delete each permission set that is no longer needed.
  
**2. Delete Users and Groups:**

- Select Users and Groups, then delete each user and group that is no longer needed.

**3. Delete External Identity Provider Configurations (If Any):**

- If you have set up a connection with an external identity provider (Identity Provider - IdP), delete this configuration in the Settings section of IAM Identity Center.

**4. Disable IAM Identity Center:**

- Go to Settings in IAM Identity Center.

- Click on Disable IAM Identity Center to disable the service.

### Delete AWS Control Tower

**Note:** Make sure you have moved or backed up any important data in the accounts managed by Control Tower.

**Steps to follow:**

**1. Decommission AWS Control Tower:**

- Access the AWS Management Console and navigate to AWS Control Tower.

- Select Landing zone settings.

- Click on Decommission landing zone to begin the process of removing AWS Control Tower.

**2. Delete Resources Created by Control Tower:**

- CloudFormation Stacks: Delete all stacks related to AWS Control Tower, starting with dependent stacks before deleting the main stack.

- AWS Service Catalog Products: Remove products created through AWS Service Catalog.
**3. Delete Shared Accounts (Log Archive, Audit):**

- If the Log Archive and Audit accounts are no longer needed, you can transfer or delete them.
  
### Delete AWS Organizations

**Note:** Ensure that you have removed all child accounts from the organization before deleting AWS Organizations.

**Steps to follow:**

**1. Move or Delete Child Accounts:**

- Access AWS Organizations from the AWS Management Console.

- Select the child accounts, and either move them out of the organization or delete them if they are no longer needed.

**2. Delete OUs (Organizational Units) and SCPs:**

- Delete all Organizational Units (OUs) and Service Control Policies (SCPs) created within the organization.

**3. Delete the Organization:**

- After deleting all child accounts, OUs, and SCPs, return to the main screen of AWS Organizations.
  
- Select Delete Organization to completely remove AWS Organizations.