+++
title = "Tổng quan"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

## Sơ đồ tổng quan bài thực hành
Trong bài thực hành này chúng ta ta sẽ tạo ra ba Account AWS đại diện cho ba môi trường production, development, và testing.

Hai tài khoản IAM Identity Center bao gồm 
- Tài khoản dt07 (management) có quyền full quyền trong cả 3 môi trường. 
- Tài khoản Duy Thien (được tạo sau) sẽ chỉ có full quyền ở môi trường development và chỉ có quyền đọc ở môi trường test, và không thể truy cập vào môi trường production.

![Diagram](/images/1/1.0.png?width=90pc)