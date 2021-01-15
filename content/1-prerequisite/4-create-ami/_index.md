+++
title = "Create AMI from Instance"
date = 2020
weight = 4
chapter = false
pre = "<b>1.4. </b>"
+++

**Contents:**
- [Create AMI from Instance](#create-ami-from-instance)

Trong bước này, để triển khai trên Auto Scaling Group, chúng ta sẽ bắt đầu tạo một AMI chứa thiết lập và ứng dụng ShareNote.

#### Create AMI from Instance

Để khởi tạo AMI từ instance, chúng ta thực hiện các bước:
1. Truy cập vào **EC2 Management Console**. Chọn **Instances**.
2. Trong danh sách instance, chọn Ubuntu instance mà chúng ta đã thiết lập ở phần trước.
3. Chọn menu **Actions**.
4. Trong **Image and templates**, chọn **Create image**.
![AMI](../../../images/1/8.png?width=90pc)
5. Ở trang **Create image**, thiết lập các thông tin cho AMI như sau:
   - Image name: Nhập tên AMI (VD: sharenote-image)
   - Các thông số khác có thể để mặc định
6. Chọn **Create image**.
7. AMI sẽ bắt đầu được khởi tạo và chúng ta có thể kiểm tra AMI trong mục **Images > AMIs** ở thanh điều hướng bên tay trái.
8. Đợi cho **Status** chuyển thành ```available``` thì AMI đã sẵn sàng để sử dụng.
![AMI](../../../images/1/9.png?width=90pc)

Đến đây, chúng ta đã hoàn thành các bước chuẩn bị cho việc triển khai Share Note với Auto Scaling Group.

Ở phần kế tiếp, chúng ta sẽ bắt đầu khởi tạo và triển khai nội dung chính của bài thực hành này.