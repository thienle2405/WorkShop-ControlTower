+++
title = "Overiew"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

## Overview Diagram of the Practical Exercise
In this exercise, we will create three AWS accounts representing three environments: production, development, and testing.

There are two IAM Identity Center accounts:
- The dt07 account (management) has full access in all three environments.
- The Duy Thien account (created later) will have full access in the development environment, read-only access in the testing environment, and no access to the production environment.


![Diagram](/images/1/1.0.png?width=90pc)