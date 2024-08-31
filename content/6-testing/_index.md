+++
title = "Testing Results"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

In this practical exercise, we will access the two users of the IAM Identity Center to check if they meet the specified requirements.

#### Check if user dt07 has full access to all three environments

Access the **IAM Identity Center** homepage → **Dashboard** → **AWS access portal URL** 

![Testing Result](/images/6/6.1.png?width=90pc)

Enter the password and MFA code to log in.

![Testing Result](/images/6/6.2.png?width=90pc)

The results show that this account can access all three environments with full permissions. 

![Testing Result](/images/6/6.3.png?width=90pc)

Let's try accessing the production environment and creating an EC2 instance.

![Testing Result](/images/6/6.4.png?width=90pc)

The EC2 instance was successfully launched.

![Testing Result](/images/6/6.5.png?width=90pc)

#### Check if user duythien can only access the developer and test environments, with read-only access in the test environment

Log in following the same steps as above.

![Testing Result](/images/6/6.6.png?width=90pc)

The results are as expected

![Testing Result](/images/6/6.7.png?width=90pc)

Now let's try accessing the test environment and attempting to create an EC2 instance.

![Testing Result](/images/6/6.8.png?width=90pc)

Thus, we have completed the content **Managing Multiple Accounts Using AWS Control Tower and Identity Center**.

Wishing you success and good health, and thank you for following through to the end.