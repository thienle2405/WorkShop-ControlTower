+++
title = "Kiểm tra Kết quả"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

Trong bài thực hành này, chúng ta sẽ truy cập vào hai user của IAM Identity Center để xem có đáp ứng được yêu cầu đề ra hay không?

#### Kiểm tra user dt07 có toàn quyền truy cập vào cả ba môi trường

Truy cập vào trang chủ **IAM Identity Center** → **Dashboard** → **AWS access portal URL**

![Testing Result](/images/6/6.1.png?width=90pc)

Nhập password và mã MFA để đăng nhập

![Testing Result](/images/6/6.2.png?width=90pc)

Kết quả cho chúng ta thấy tài khoản này có thể truy cập vào 3 môi trường với Full quyền. 

![Testing Result](/images/6/6.3.png?width=90pc)

Ta thử vào môi trường production và tạo thử một EC2 

![Testing Result](/images/6/6.4.png?width=90pc)

EC2 được khởi chạy thành công 

![Testing Result](/images/6/6.5.png?width=90pc)

#### Kiểm tra user duythien chỉ có thể truy cập vào 2 môi trường developer và test, và chỉ có quyền đọc ở môi trường test 

Đăng nhập như các bước trên

![Testing Result](/images/6/6.6.png?width=90pc)

Kết quả đúng như mong đợi 

![Testing Result](/images/6/6.7.png?width=90pc)

Bây gờ chúng ta thử truy cập vào môi trường test và tạo thử một EC2

![Testing Result](/images/6/6.8.png?width=90pc)

Vậy là chúng ta đã hoàn thành nội dung **Quản lý nhiều tài khoản bằng AWS Control Tower và Identity Center** 

Chúc các bạn thành công và nhiều sức khỏe, cảm ơn đã theo dõi đến cuối cùng. 