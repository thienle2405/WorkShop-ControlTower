+++
title = "Khởi tạo Target Group"
date = 2021
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

Ở phần này, bạn sẽ tạo một Target Group để làm mục tiêu Load Balancer truyển tải lưu lượng dữ liệu tới.

#### Tạo Target Group

Để tạo Target Group, chúng ta thực hiện như sau:
1. Truy cập vào **EC2 Management Console**.
2. Ở thanh điều hướng bên trái, kéo xuống dưới sau đó chọn **Target Groups**.


![Target Group](/images/asg/023.png?width=90pc)

3. Ở trang **Target groups**, chọn **Create Target Group**.

4. Ở trang **Specify group details**, thiết lập các thông số như sau cho target group:
   - Basic configuration:
     - Choose a target type: Chọn **Instances**.
     - Target group name: Nhập tên của target group (VD: **sharenote-tg**).
     - Protocol: **HTTP**.
     - Port: **8080** (Port sử dụng bởi ShareNote).
   - Các mục còn lại để mặc định.

![Target Group](/images/asg/024.png?width=90pc)

5. Kéo màn hình xuống cuối trang, click **Next**.

6. Ở trang **Register targets**,
  + Click chọn EC2 instance chúng ta đã tạo.
  + Click **Create target group**.

![Target Group](/images/asg/024-2.png?width=90pc)

Danh sách target group sẽ liệt kê target group mà chúng ta vừa tạo trong danh sách.

![Target Group](/images/asg/025.png?width=90pc)