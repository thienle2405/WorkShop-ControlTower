+++
title = "Tạo máy ảo EC2 Ubuntu"
date = 2020
weight = 1
chapter = false
pre = "<b>1.3.1 </b>"
+++

#### Tạo máy ảo EC2 Ubuntu

1. Trong bước này chúng ta sẽ triển khai một Ubuntu Instance. Nếu bạn chưa biết cách làm, hãy tham khảo bài [Sử dụng Máy ảo Linux](https://000004.awsstudygroup.com/vi/1-begin-ec2/1.1-linux-ec2/1.1.1-create-ec2/). 

{{% notice note %}}
Lưu ý, hãy chọn AMI **Ubuntu Server 20.04 LTS (HVM)** thay vì **Amazon Linux 2 AMI (HVM)**.
{{% /notice %}}

![EC2](/images/asg/009.png?width=90pc)

2. Khi tới bước chọn Security Group, đảm bảo bạn lựa chọn Security Group **sharenote-sg**.

![EC2](/images/asg/010.png?width=90pc)

3. Đảm bảo instance đã tạo hoàn tất trước khi thực hiện kết nối vào instance.

![EC2](/images/asg/011.png?width=90pc)


#### Kết nối máy ảo EC2 Ubuntu

1. Chúng ta sẽ thực hiện kết nối vào máy ảo EC2 Ubuntu theo hướng dẫn dưới đây. [Kết nối máy ảo Linux](https://000004.awsstudygroup.com/vi/1-begin-ec2/1.1-linux-ec2/1.1.2-connect-ec2/)

{{% notice note %}}
Vì chúng ta tạo máy ảo EC2 sử dụng hệ điều hành **Ubuntu** nên sẽ sử dụng user **ubuntu** để kết nối tới thay vì user **ec2-user** như máy ảo Amazon Linux.
{{% /notice %}}

![EC2](/images/asg/012.png?width=90pc)