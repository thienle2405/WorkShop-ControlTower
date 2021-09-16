+++
title = "Triển khai Máy ảo ShareNote"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

Trong bước này, chúng ta sẽ thiết lập cấu hình Database cho ứng dụng ShareNote. Sau đó,chúng ta sẽ thiết lập tự động khởi chạy ứng dụng khi khởi chạy Instance. 

{{% notice info %}}
Nếu bạn đã làm bài số 000005 [Triển Khai AWS RDS Kết Hơp với ShareNote](https://000005.awsstudygroup.com/vi/), bạn có thể thấy rằng bạn đã triển khai ShareNote một cách thủ công. Ở bài này, bạn sẽ thiết lập khởi chạy ứng dụng cho EC2 Instance để mỗi khi một EC2 Instance mới được tạo ra bởi Auto Scaling Group, EC2 Instance đó sẽ tự động được thiết lập để triển khai ứng dụng ShareNote.
{{% /notice %}}

**Nội dung:**
- [Tạo máy ảo EC2 Ubuntu](/1.3.1-createec2/)
- [Thiết lập cấu hình Database cho ShareNote](/1.3.2-configure-db-sharenote/)
- [Thiết lập khởi chạy ứng dụng khi khởi chạy instance](/1.3.3-autostart/)

