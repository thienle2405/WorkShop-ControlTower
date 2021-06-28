+++
title = "Khởi tạo AMI từ Máy ảo"
date = 2020
weight = 4
chapter = false
pre = "<b>1.4. </b>"
+++
Ở bước này, bạn sẽ khởi tạo một **Amazon Machine Image (AMI)** cho Ubuntu Instance vừa được thiết lập ở bước trước. **AMI** là một bản chụp cấu hình của EC2 Instance cho phép bạn triển khai nhiều EC2 Instance với cấu hình tương tự với EC2 Instance gốc. **AMI** thường được sử dụng bên trong **Launch Template** để tạo khuôn mẫu cho các EC2 Instances.

**Nội dung:**
- [Khởi tạo AMI từ Máy ảo](#khởi-tạo-ami-từ-máy-ảo)

#### Khởi tạo AMI từ Máy ảo

1. Truy cập vào **EC2 Management Console**. Chọn **Instances**.
2. Trong danh sách instance, chọn Ubuntu instance mà chúng ta đã thiết lập ở phần trước.
3. Chọn menu **Actions**.
4. Trong **Image and templates**, chọn **Create image**.
![AMI](../../../images/1/1.4_CreateAMI.png?width=90pc)
5. Ở trang **Create image**, thiết lập các thông tin cho AMI như sau:
   - Image name: Nhập tên AMI (VD: sharenote-image)
   - Các thông số khác có thể để mặc định
6. Chọn **Create image**.
7. AMI sẽ bắt đầu được khởi tạo và chúng ta có thể kiểm tra AMI bằng cách chọn **AMIs** ở thanh điều hướng bên tay trái.
8. Đợi cho **Status** chuyển thành **Available** thì AMI đã sẵn sàng để sử dụng.

Đến đây, chúng ta đã hoàn thành các bước chuẩn bị cho việc triển khai ShareNote với Auto Scaling Group.

Ở phần kế tiếp, chúng ta sẽ bắt đầu khởi tạo và triển khai nội dung chính của bài thực hành này.