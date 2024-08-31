+++
title = "Configuring SCPs and Permission Sets"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

In this step, we will configure SCPs and Permission Sets. Let’s clarify these two concepts further:

- **Service Control Policies (SCP):**
  - **Role:** SCPs define which actions are allowed or denied on AWS accounts that belong to an organization in AWS Organizations.
  - **Scope of Application:** SCPs are applied at the account or Organizational Unit (OU) level and affect all roles, users, and services within that account.
  - **Function:** SCPs do not directly grant permissions; they only restrict or allow permissions that have been assigned through IAM roles, IAM policies, or Permission Sets. SCPs will block or allow specific actions regardless of where the permissions come from.
- **Permission Sets:**
  - **Role:** Permission Sets define specific permissions that users or groups can perform when accessing AWS accounts through AWS IAM Identity Center (formerly SSO).
  - **Scope of Application:** Permission Sets apply only to users or groups assigned in IAM Identity Center to access AWS accounts.
  - **Function:** Permission Sets assign detailed permissions (such as ReadOnlyAccess, AdministratorAccess, or other custom permissions) to users, allowing them to perform actions on AWS accounts.

**In summary, SCPs define what an account can do, while Permission Sets define what a user can do when accessing an AWS account. If both are applied, the final permissions will be the intersection of SCPs and Permission Sets.**

In this scenario, we will create three AWS Accounts representing three environments: production, development, and testing. There are two accounts in IAM Identity Center: dt07 (management) with full access in all three environments, and Duy Thien (created later) with full access in the development environment, read-only access in the testing environment, and no access to the production environment.

#### Creating AWS Accounts for Each Environment

Access AWS Control Tower → Select Organization → Create resources

![Application Load Balancer](/images/4/4.1.png?width=90pc)

**Enter Account Details:**
  - **Account email:** Enter the email address to create a new account in the landing zone. This email will be used for notifications and account management.
  - **Display name:** Enter the display name for the account. This name will appear in AWS Control Tower to easily identify the account. In this example, the name is "production".
  
**Access Configuration:**
  - **IAM Identity Center user email:** Enter the email address for the IAM Identity Center user. This is the email that the user will use to log into IAM Identity Center and access AWS accounts.
  - **IAM Identity Center user name:** Enter the username for IAM Identity Center. This is usually the user’s first and last name, which will be used to create the user in IAM Identity Center.
  
**Select OU:** We will add the environments to the Sandbox OU created when setting up the landing zone.

**Complete and Continue:** After entering all the information, click **Create** to proceed with the account creation process.

![Application Load Balancer](/images/4/4.2.png?width=90pc)
![Application Load Balancer](/images/4/4.3.png?width=90pc)

Repeat the same process for the development and testing environments.

![Application Load Balancer](/images/4/4.4.png?width=90pc)

#### Creating SCPs

In AWS Control Tower, Service Control Policies (SCPs) are configured through AWS Organizations, as SCPs are a feature of AWS Organizations.

Access **AWS Organizations** directly from the AWS Management Console. In AWS Organizations, select **Policies** from the left navigation bar → Select the **Service Control Policies (SCPs)** tab. Here, you can create new SCPs or manage existing ones.

![Application Load Balancer](/images/4/4.5.png?width=90pc)

AWS Control Tower automatically creates some SCPs.

![Application Load Balancer](/images/4/4.6.png?width=90pc)

You can view the details of the permissions in **JSON** format

![Application Load Balancer](/images/4/4.7.png?width=90pc)

These SCPs can be attached to OUs or individual AWS accounts. To meet the requirements, we can attach full access to the Sandbox OU, and then restrict permissions based on Permission Sets. Alternatively, you can also restrict permissions directly in SCPs, depending on the use case, as the final permissions will be the intersection of **Permission Sets** and **SCPs**.

![Application Load Balancer](/images/4/4.8.png?width=90pc)

#### Creating Groups for AWS Accounts and IAM Identity Center Users

When a user and an account are both in a group in IAM Identity Center (or through other AWS access mechanisms), the user will have access to that account based on the permission sets assigned to the group.

In **IAM Identity Center**, you will see some pre-created groups in AWS Control Tower. Click **Create Group**.

![Application Load Balancer](/images/4/4.9.png?width=90pc)

As per the requirements, we will create two groups: Project Manager and Developer.

Additionally, AWS Control Tower has also pre-created some Permission Sets for us.

![Application Load Balancer](/images/4/4.10.png?width=90pc)

![Application Load Balancer](/images/4/4.11.png?width=90pc)

Next, assign AWS Accounts to the Project Manager group.

![Application Load Balancer](/images/4/4.12.png?width=90pc)

![Application Load Balancer](/images/4/4.13.png?width=90pc)

Then select the Permission Set, here it is Full Access.

![Application Load Balancer](/images/4/4.15.png?width=90pc)

Continue assigning AWS Accounts to the **Developer** group.

![Application Load Balancer](/images/4/4.16.png?width=90pc)

![Application Load Balancer](/images/4/4.17.png?width=90pc)

Then select the Permission Set, here it is AWSPowerUserAccess, which provides access to everything except **AWS Organizations**.

![Application Load Balancer](/images/4/4.18.png?width=90pc)

![Application Load Balancer](/images/4/4.19.png?width=90pc)

Now we will limit the access of user Duy Thien to ReadOnlyAccess in the testing environment. 

![Application Load Balancer](/images/4/4.20.png?width=90pc)