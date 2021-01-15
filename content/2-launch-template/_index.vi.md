+++
title = "Khởi tạo Launch Template"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

**Nội dung:**
- [Tạo Launch Template](#tạo-launch-template)

Launch Templates cung cấp cho bạn một cách mới để tạo các mẫu cho việc tạo các yêu cầu khởi chạy của bạn. Launch Templates quy trình hóa và đơn giản hóa quy trình khởi chạy cho các dịch vụ như Auto Scaling, instance Spot Fleet, Spot, và On-Demand.

#### Tạo Launch Template

Để tạo Launch Template, chúng ta thực hiện như sau:
1. Truy cập vào **AWS Management Console**. Lựa chọn **Services** ở thanh điều hướng và tìm kiếm dịch vụ **EC2**.
2. Ở thanh điều hướng bên trái, chọn **Launch Templates**.
3. Ở trang khởi đầu, chọn **Create launch template**.
4. Ở trang **Create launch template**, thiết lập launch template với các thông số như sau:
   - Launch template name and description:
     - Launch template name - required: **sharenote-template** (Tên do bạn chọn)
   - Amazon machine image (AMI):
     - AMI: Lựa chọn **sharenote-image** mà chúng ta đã tạo ở bước trước.

![Launch Template](../../../images/2/1.png?width=60pc)

   - Instance type:
     - Instance type: Lựa chọn **t2.micro** (Đây là lựa chọn cho bài thực hành, thực tế sẽ có yêu cầu cấu hình lớn hơn)
   - Key pair (login)
     - Key pair name: Lựa chọn key pair đang sử dụng của bạn.
   - Network settings:
     - Security groups: Lựa chọn Security Group mà bạn đã tạo ra và phù hợp. (VD: sharenote-sg)
    ![Launch Template](../../../images/2/2.png?width=60pc)
5. Chọn **Create launch template** để tạo template.
6. Chọn **View lauch template** để hoàn thành việc khởi tạo.

![Launch Template](../../../images/2/3.png?width=60pc)