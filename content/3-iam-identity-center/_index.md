+++
title = "Setting Up IAM Identity Center"
date = 2021
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

After completing the setup of the landing zone, you will receive an email invitation to join AWS IAM Identity Center sent to your root email. In real-world projects, when new members join the team or when access needs to be granted to partners, adding users to the IAM Identity Center allows you to easily manage their access to AWS accounts and related applications.

#### Confirm the Invitation

Check your inbox and accept the invitation to join.

![Target Group](/images/3/3.1.png?width=90pc)

You will be redirected to the login page; enter your root account email.

![Target Group](/images/3/3.2.png?width=90pc)

You will be required to enable MFA. If you're not familiar with **MFA**, you can refer to the following documentation MFA. [MFA](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html)
  
![Target Group](/images/3/3.3.png?width=90pc)

After setting up a new password and MFA, you will be redirected to the **AWS access portal**. Here, you will see a list of AWS accounts that you have access to. This portal helps you easily manage and access your AWS accounts. Additionally, the AWS access portal provides a **Create shortcut** feature to generate secure shortcut links to AWS Management Console pages, making it easier to bookmark or share with those who have AWS account access.

![Target Group](/images/3/3.4.png?width=90pc)

You can also log in using the CLI. For CLI setup details for AWS, refer [here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

You can use AWS IAM Identity credentials, which AWS recommends using the command **aws configure sso**.

![Target Group](/images/3/3.5.png?width=90pc)

![Target Group](/images/3/3.6.png?width=90pc)

You will be redirected to a confirmation web page, and after confirming, you will be successfully logged in. Try using CLI commands, such as displaying S3 buckets, to test.

![Target Group](/images/3/3.7.png?width=90pc)
![Target Group](/images/3/3.8.png?width=90pc)

Now you can use your AWS IAM Identity Center user to access AWS accounts.

![Target Group](/images/3/3.9.png?width=90pc)

#### Adding Users to IAM Identity Center

1. Go back to the **AWS Control Tower** homepage → **Users and access** → **View in IAM Identity Center**. 

![Target Group](/images/3/3.10.png?width=90pc)

2. Once on the homepage, select users and proceed to add a user.

![Target Group](/images/3/3.11.png?width=90pc)

![Target Group](/images/3/3.12.png?width=90pc)

You can configure additional details in the sections below as needed → Next.

![Target Group](/images/3/3.13.png?width=90pc)

3. After adding a user, you will also receive an invitation in your email. Proceed to update the **password** and configure **MFA** as previously done in the steps above.

4. Now you can see that your IAM Identity Center has a new user added.

![Target Group](/images/3/3.14.png?width=90pc)