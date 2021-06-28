+++
title = "Khởi tạo Target Group"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

Ở phần này, bạn sẽ tạo một Target Group để làm mục tiêu Load Balancer truyển tải lưu lượng dữ liệu tới.

**Nội dung:**
- [Tạo Target Group](#tạo-target-group)

#### Tạo Target Group

Để tạo Launch Template, chúng ta thực hiện như sau:
1. Truy cập vào **EC2 Management Console**.
2. Ở thanh điều hướng bên trái, chọn **Target Groups**.
3. Ở trang **Target groups**, chọn **Create launch template**.
4. Ở trang **Specify group details**, thiết lập các thông số như sau cho target group:
   - Basic configuration:
     - Choose a target type: Chọn **Instances**
     - Target group name: Nhập tên của target group (VD: **sharenote-tg**)
     - Protocol: **HTTP**
     - Port: **8080** (Port sử dụng bởi ShareNote)
   - Các mục còn lại để mặc định
5. Chọn **Next**.

![Target Group](../../../images/3/3_RegisterTargets.png?width=90pc)

6. Ở trang **Register targets**, chọn **Create target group**.

Danh sách target group sẽ liệt kê target group mà chúng ta vừa tạo trong danh sách.
