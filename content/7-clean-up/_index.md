+++
title = "Dọn dẹp tài nguyên"
date = 2021-06-08T18:57:03+07:00
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

Chúng ta sẽ dọn dẹp tài nguyên theo thứ tự như sau:
1. **Xóa Auto Scaling Group**:
    - Truy cập **EC2 Management Console** 
    - Trên thanh điều hướng bên trái, chọn Auto Scaling Groups
    - Chọn Auto Scaling Group liên quan tới bài lab.
    - Click Delete
    - Gõ delete vào ô trống và nhấn delete
2. **Xóa Load Balancer**:
    - Truy cập **EC2 Management Console** 
    - Trên thanh điều hướng bên trái, chọn Load Balancers
    - Chọn Load Balancer liên quan tới bài lab.
    - Click Actions.
    - Click Delete.
3. **Xóa Target Group**:
    - Truy cập **EC2 Management Console** 
    - Trên thanh điều hướng bên trái, chọn Target Groups
    - Chọn Target Group liên quan tới bài lab.
    - Click Actions.
    - Click Delete.
    - Click Yes, delete
4. **Xóa Launch Template**:
    - Truy cập **EC2 Management Console** 
    - Trên thanh điều hướng bên trái, chọn Launch Templates
    - Chọn Launch Template liên quan tới bài lab.
    - Click Actions.
    - Click Delete template
    - Gõ delete vào ô trống và nhấn delete 
5. **Xóa AMI**:
    - Truy cập **EC2 Management Console** 
    - Trên thanh điều hướng bên trái, chọn AMIs
    - Chọn AMI liên quan tới bài lab.
    - Click Actions.
    - Click Deregister.
    - Click Continue.
6. **Terminate EC2 instance**
    - Truy cập **EC2 Management Console** 
    - Trên thanh điều hướng bên trái, chọn Intances
    - Chọn tất cả EC2 Instance liên quan tới bài lab.
    - Click Actions.
    - Click Manage Instance State.
    - Chọn Terminate.
    - Click Change State
7. **Xóa DB Instance**
    - Truy cập **RDS Management Console**  
    - Trên thanh điều hướng bên trái, chọn Databases
    - Chọn tất cả DB Instance liên quan tới bài lab.
    - Click Actions.
    - Click Delete
    - Bỏ chọn *Create final snapshot?* và chọn *I acknowledge that upon instance deletion, automated backups, including system snapshots and point-in-time recovery, will no longer be available*
    - Gõ *delete me* vào ô trống.
    - Click *Delete*
8. **Xóa Security Group**
    - Truy cập **EC2 Management Console** 
    - Trên thanh điều hướng bên trái, chọn Security Groups
    - Chọn tất cả Security Groups liên quan tới bài lab.
    - Click Actions.
    - Click Delete security groups
    - Click Delete