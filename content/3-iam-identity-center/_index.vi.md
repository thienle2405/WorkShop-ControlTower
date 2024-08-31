+++
title = "Thiết lập IAM Identity Center"
date = 2021
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

Sau khi hoàn tất set up landing zone, bạn sẽ nhận được một email về lời mời tham gia AWS IAM Identity Center đến email root của bạn. Sau đó chúng ta sẽ thêm user cho IAM Identity Center, trong dự án thực tế, khi có thêm thành viên mới trong nhóm hoặc khi cần cấp quyền truy cập cho các đối tác, việc thêm người dùng vào IAM Identity Center giúp bạn dễ dàng quản lý quyền truy cập của họ vào các tài khoản AWS và ứng dụng liên quan.

#### Xác nhận lời mời

Kiểm tra hòm thư, và chấp nhận lời mời tham gia 

![Target Group](/images/3/3.1.png?width=90pc)

Bạn sẽ dược điều hướng sang trang đăng nhập, hãy nhập email tài khoản root của bạn vào 

![Target Group](/images/3/3.2.png?width=90pc)

Bạn sẽ bắt buộc phải có tính năng MFA, nếu chưa biết **MFA** là gì, bạn có thể tham khảo tài liệu sau [MFA](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html)
  
![Target Group](/images/3/3.3.png?width=90pc)

Sau khi thiết lập password mới và MFA, bạn sẽ được chuyển hướng đến **AWS access portal**. Tại đây, bạn sẽ thấy danh sách các tài khoản AWS mà bạn có quyền truy cập. Cổng thông tin này giúp bạn dễ dàng quản lý và truy cập vào các tài khoản AWS của mình.
Ngoài ra, AWS access portal còn cung cấp tính năng Create shortcut để tạo các liên kết rút gọn an toàn đến các trang trong AWS Management Console, giúp dễ dàng đánh dấu hoặc chia sẻ với những người có quyền truy cập vào tài khoản AWS.

![Target Group](/images/3/3.4.png?width=90pc)

Bạn cũng có thể đăng nhập bằng CLI. Chi tiết cài đặt CLI cho AWS bạn xem [tại đây](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

Chúng ta có thể sử dụng AWS IAM Identity credentials, đây là một cách mà AWS khuyến nghị bằng cách sử dụng câu lệnh **aws configure sso**

![Target Group](/images/3/3.5.png?width=90pc)

![Target Group](/images/3/3.6.png?width=90pc)

Bạn sẽ được chuyển hướng đến một trang web xác nhận, sau khi xác nhận thì bạn đã đăng nhập thành công, hãy thử sử dụng câu lệnh cli để test ví dụ như hiển thị S3 bucket. 

![Target Group](/images/3/3.7.png?width=90pc)
![Target Group](/images/3/3.8.png?width=90pc)

Bây giờ ta có thể sử dụng user của AWS IAM Identy Center để truy cập vào account AWS 

![Target Group](/images/3/3.9.png?width=90pc)

#### Thêm user cho IAM Identity Center

1. Vào lại trang chủ của **AWS Control Tower** → **Users and access** → **View in IAM Identity Center**. 

![Target Group](/images/3/3.10.png?width=90pc)

2. Sau khi vào trang chủ, ta chọn user và tiến hành thêm một user 

![Target Group](/images/3/3.11.png?width=90pc)

![Target Group](/images/3/3.12.png?width=90pc)

Các phần bên dưới ta có thể cấu hình chi tiết thêm tùy vào nhu cầu → Next.

![Target Group](/images/3/3.13.png?width=90pc)

3. Sau khi thêm một user, bạn cũng sẽ nhận được một lời mời đến email của bạn, tiến hành cập nhật **password** và cấu hình **MFA** như các bước trên đã làm.

4. Bây giờ bạn có thể thấy IAM Identity Center của bạn có thêm một user mới được thêm vào

![Target Group](/images/3/3.14.png?width=90pc)
