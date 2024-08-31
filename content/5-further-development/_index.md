+++
title = "Further Development"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

When setting up a landing zone, two accounts are created by default: the Log archive account and the Audit account. We can further expand the scenario in several ways as follows:

#### Integrating AWS Service Catalog
AWS Service Catalog is a powerful tool that allows you to provision, manage, and control the deployment of standardized AWS products within your organization. This is crucial to ensure that the deployed services comply with predefined standards and security policies.

**Expansion and Application:**

  - **Create Standardized Service Catalogs:** You can create service catalogs that include CloudFormation templates and resources such as EC2, RDS, or Lambda, pre-configured according to your organization’s standards. This ensures that teams within the organization can only deploy approved services that comply with security policies.

  - **Manage Service Versions:** AWS Service Catalog allows you to manage multiple versions of products, making it easier for the organization to maintain and update AWS services with new improvements while ensuring compliance with internal regulations.

  - **Control Costs and Access:** By integrating with IAM, you can control who can deploy which products and monitor the use of AWS resources, helping to manage costs and ensure resources are not misused.

#### Setting Up Centralized Monitoring and Notifications
**Amazon CloudWatch** and **Amazon SNS** play a crucial role in setting up centralized monitoring and alerts for your AWS environment, helping you quickly detect and respond to incidents or unusual activities.

**Expansion and Application:**
  - **Log Archive Account:**
    - **Required Services:** Amazon CloudTrail, AWS Config, Amazon S3, and Amazon CloudWatch.
    - **Role:** This account stores all logs from CloudTrail and Config, providing a centralized and secure repository for activity logs across all AWS accounts.
    - **Specific Application:**
      - **CloudWatch:** Set up CloudWatch Logs to monitor logs from CloudTrail and AWS Config, establish metrics and alerts to detect abnormal activities or security policy violations.
      - **S3:** Store logs long-term in S3 with retention policies and encryption to secure information.
  
  - **Audit Account:**
    - **Required Services:** AWS IAM, AWS Config, Amazon CloudWatch, and Amazon SNS.
    - **Role:** This account is responsible for cross-account auditing, providing inspection rights and alerts on security violations or non-compliant activities.
    - **Specific Application:**
      - **IAM:** Create cross-account audit roles to allow read-only access to other accounts without requiring higher permissions.
      - **CloudWatch:** Set up security monitoring metrics, such as tracking changes in security configurations or unusual access patterns.
      - **SNS:** Configure SNS to send alerts via email or SMS to the security team when critical events occur, such as changes in access permissions or invalid configurations.

![Application Load Balancer](/images/5/5.1.png?width=90pc)