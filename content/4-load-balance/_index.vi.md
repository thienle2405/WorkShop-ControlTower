+++
title = "Khởi tạo Load Balancer"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

Ở bước này, chúng ta sẽ triển khai Load Balancer điều phối các request từ người dùng đến các EC2 instance chạy ứng dụng ShareNote của chúng ta.


#### Tạo Load Balancer

1. Truy cập vào **EC2 Management Console**.
2. Ở thanh điều hướng bên trái, kéo xuống dưới và click **Load Balancers**.
3. Ở trang danh sách Load Balancer, click **Create Load Balancer**.

![Application Load Balancer](/images/asg/026.png?width=90pc)

4. Ở trang **Select load balancer type**, chọn **Create** ở mục **Application Load Balancer**.


![Application Load Balancer](/images/asg/027.png?width=90pc)

5. Ở trang **Create Application Load Balancer**, thiết lập các thông số như sau:
    - Basic Configuration:
      - Name: Nhập tên của Load Balancer (VD: **sharenote-lb**)
      - Scheme: **internet-facing**
      - IP address type: **ipv4**

![Application Load Balancer](/images/asg/028.png?width=90pc)

6. Kéo màn hình xuống dưới, tại mục **Network mapping**.
  + Tại mục **VPC** chọn VPC default.
  + Tại mục Mappings Chọn hai AZ **ap-southeast-1a** và **ap-southeast-1b**


![Application Load Balancer](/images/asg/029.png?width=90pc)

7. Kéo màn hình xuống dưới, tại mục **Security Groups**, click chọn **sharenote-sg**.
  + Tại mục Listeners and routing , phần **Default action** click chọn **sharenote-tg** target group mà chúng ta đã tạo ở bước trước đó.


![Application Load Balancer](/images/asg/030.png?width=90pc)

8. Kéo màn hình xuống dưới cùng, click **Create load balancer**.


![Application Load Balancer](/images/asg/031.png?width=90pc)

9. Trang tạo Load Balancer thành công sẽ hiển thị ra cho bạn. Click **View load balancers** để trở về danh sách Load Balancer

Quá trình tạo Load Balancer sẽ mất khoảng 5-10 phút để hoàn thành. Bạn có thể kiểm tra sự thay đổi trạng thái từ **provisioning** sang **active** ở danh sách Load Balancer.

10. Hãy ghi chú lại **DNS name** của Load Balancer lại vì đây sẽ là địa chỉ chúng ta dùng để truy cập vào ứng dụng dược triển khai.

![Application Load Balancer](/images/asg/032.png?width=90pc)

11. Truy cập địa chỉ DNS trên browser của bạn, đảm bảo có thể truy cập tới ứng dụng Share Note.
Tuy nhiên lúc này chúng ta chỉ có 1 máy chủ EC2 duy nhất.

![Application Load Balancer](/images/asg/033.png?width=90pc)

Tiếp theo chúng ta sẽ tiến hành cấu hình tính năng Auto Scaling Group, giúp tự động tăng số lượng EC2 instance của chúng ta khi lượng truy cập tăng cao.
