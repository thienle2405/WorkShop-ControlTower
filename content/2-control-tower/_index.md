+++
title = "Setting Up Control Tower"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++
When you start using AWS Control Tower, the system will guide you through the process of setting up a landing zone—a multi-account environment standardized according to AWS best practices. This landing zone not only automates the creation of new AWS accounts but also integrates security and compliance measures, making it easier for you to manage resources and maintain consistency across the entire organization.

#### Setting up the landing zone

To set up the landing zone, follow these steps:
1. Go to AWS → Use the search bar and enter the keyword **Control Tower** → Select **Set up landing zone**.

![Launch Template](/images/2/2.1.png?width=90pc)

2. On the **Set up landing zone** you will be provided with detailed information about AWS Control Tower, including pricing and region selection:
   - AWS Control Tower will have the necessary permissions to manage organizational units (OUs) and accounts within your AWS Organizations infrastructure.
   - AWS Control Tower does not extend governance to existing OUs and accounts. Instead, it sets up a separate landing zone containing resources managed by AWS Control Tower, operating in parallel with your existing AWS Organizations infrastructure.
   - When you add an existing organization to AWS Control Tower, this process is called "Registering" the organization. When you add an AWS account to AWS Control Tower, this process is called "Enrolling" the account.
   - After setting up the landing zone, you can register existing OUs containing up to 300 accounts. If an OU contains more than 300 accounts, it cannot be registered in AWS Control Tower.
   - AWS Control Tower will publish events to AWS CloudTrail.

  ![Launch Template](/images/2/2.2.png?width=90pc)

  Regarding **pricing**, you will incur charges for related AWS services used by AWS Control Tower based on usage levels. Choose your **Home Region** carefully as it will determine where the primary resources will be deployed and cannot be changed after setup. Here, we select the Singapore Region.

  ![Launch Template](/images/2/2.3.png?width=90pc)

  You can also select additional regions for deployment, but a **Home Region** is mandatory.

  ![Launch Template](/images/2/2.4.png?width=90pc)

  The next step is the **Region deny setting**, which allows you to configure controls that prohibit access to AWS services and operations by region. This option can be enabled for the landing zone and for individual OUs.

  ![Launch Template](/images/2/2.5.png?width=90pc)

3. The next step is to **Configure organizational units (OUs)**, where you will set up the OU structure for your landing zone.
   - **Foundational OU**: AWS Control Tower automatically creates a Security OU to help you start with a well-planned OU structure. This OU contains two shared accounts: the log archive account and the security audit account. You can change the name of this OU if necessary, but it must be unique and can be edited after setting up the landing zone.
   - **Additional OU**: To establish a multi-account system, AWS Control Tower recommends creating an additional OU during the landing zone setup. This OU can be used to store any production or development accounts. You have the option to create a new OU or opt out of this step.

  ![Launch Template](/images/2/2.6.png?width=90pc)

  Create a new OU named **Sandbox** to house AWS accounts representing different environments (production, development, test, etc.).

  ![Launch Template](/images/2/2.7.png?width=90pc)

4. The next step is to configure **shared accounts**.

  The management account will be the root account created during AWS setup. As mentioned, you will need multiple Gmail accounts, or if you don't have many Gmail accounts, follow the tip by using the original email but adding **+something** to it. Create the security audit account and the log archive account.

  ![Launch Template](/images/2/2.8.png?width=90pc)

  ![Launch Template](/images/2/2.9.png?width=90pc)

5. The next step involves **additional configurations** during AWS Control Tower setup.
  
  - **AWS Control Tower Sets Up AWS Account Access with IAM Identity Center:** This is the default and recommended choice for new users or when you want to use groups and permission sets managed by AWS Control Tower.
  - **Self-managed AWS Account Access with IAM Identity Center or Another Method**: This option is suitable if you have specific requirements for managing AWS account access and do not want AWS Control Tower to manage access. You will need to configure IAM Identity Center or another access method manually.

  Regarding **AWS CloudTrail Configuration**, the purpose is to log actions within AWS Control Tower as events. This helps track and record changes and actions occurring within your AWS organization. When enabled, AWS Control Tower aggregates information from all accounts into an organization CloudTrail and transfers logged information to a designated Amazon S3 bucket. This enables comprehensive tracking of activities within the organization.

  ![Launch Template](/images/2/2.10.png?width=90pc)

  Configure log settings and KMS encryption for Amazon S3 in AWS Control Tower. 
  - **Log configuration for Amazon S3 - optional:**
    - **Amazon S3 bucket retention for logging:** Allows you to enter the number of years to retain logs, defaulting to 1 year. The retention period must be an integer from 1 to 15, with values under 1 year expressed in days.
    - **Amazon S3 bucket retention for access logging:** Sets the retention period for access logs, defaulting to 10 years. The retention must also be between 1 and 15 years, or expressed in days if less than 1 year.
  - **KMS Encryption - optional:**
    - AWS Key Management Service (KMS) helps create and manage encryption keys and control resources in AWS Control Tower.
    - You can choose "Enable and customize encryption settings" if you wish to use KMS encryption for AWS CloudTrail and AWS Config logs.
    - Note: Multi-region keys are not supported.
  
  ![Launch Template](/images/2/2.11.png?width=90pc) 

6. The final step is to review and proceed to set up the landing zone.
   
   ![Launch Template](/images/2/2.12.png?width=90pc) 

   ![Launch Template](/images/2/2.13.png?width=90pc) 

   ![Launch Template](/images/2/2.14.png?width=90pc) 

   ![Launch Template](/images/2/2.15.png?width=90pc) 

We will have to wait for some time, and the setup details will be displayed.

![Launch Template](/images/2/2.16.png?width=90pc) 