+++
title = "Thiết lập Control Tower"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++
Khi bạn bắt đầu sử dụng AWS Control Tower, hệ thống sẽ hướng dẫn bạn qua quy trình thiết lập vùng hạ cánh (landing zone) – một môi trường đa tài khoản được chuẩn hóa theo các phương pháp tốt nhất của AWS. Vùng hạ cánh này không chỉ tự động hóa việc tạo các tài khoản AWS mới mà còn tích hợp sẵn các biện pháp bảo mật và tuân thủ, giúp bạn dễ dàng quản lý tài nguyên và duy trì sự nhất quán trên toàn bộ tổ chức.

#### Thiết lập landing zone

Để thiết lập landing zone, ta thực hiện các bước sau:
1. Truy cập vào AWS → Sử dụng thanh tìm tiếp và nhập từ khóa **Control Tower** → Chọn **Set up landing zone**.

![Launch Template](/images/2/2.1.png?width=90pc)

2. Ở trang **Set up landing zone**, bạn sẽ được mô tả thông tin chi tiết về AWS Control Tower, mô tả về giá và chọn vùng
   - AWS Control Tower sẽ có các quyền cần thiết để quản lý các đơn vị tổ chức (OUs) và tài khoản trong hạ tầng AWS Organizations của bạn.
   - AWS Control Tower không mở rộng quản lý đối với các OUs và tài khoản hiện có. Thay vào đó, nó thiết lập một vùng hạ cánh riêng biệt chứa các tài nguyên được quản lý bởi AWS Control Tower, hoạt động song song với hạ tầng AWS Organizations hiện tại của bạn.
   - Khi bạn thêm một tổ chức hiện có vào AWS Control Tower, quá trình này được gọi là "Registering" (Đăng ký) tổ chức. Khi bạn thêm một tài khoản AWS vào AWS Control Tower, quá trình này được gọi là "Enrolling" (Ghi danh) tài khoản.
   - Sau khi thiết lập vùng hạ cánh, bạn có thể đăng ký (Register) các OUs hiện có chứa tối đa 300 tài khoản. Nếu một OU chứa nhiều hơn 300 tài khoản, bạn không thể đăng ký nó trong AWS Control Tower.
   - AWS Control Tower sẽ công bố các sự kiện đến AWS CloudTrail.

  ![Launch Template](/images/2/2.2.png?width=90pc)

  Tiếp theo là về **giá cả**, Bạn sẽ chịu phí cho các dịch vụ AWS liên quan mà AWS Control Tower sử dụng, dựa trên mức độ sử dụng.
  Lựa chọn **Home Region** cẩn thận vì nó sẽ quyết định nơi các tài nguyên chính sẽ được triển khai và không thể thay đổi sau khi thiết lập. Ở đây mình sẽ chọn Region Singapore.

  ![Launch Template](/images/2/2.3.png?width=90pc)

  Bạn cũng có thể chọn thêm các vùng để triển khai, nhưng bắc buộc phải có một **Home Region.**

  ![Launch Template](/images/2/2.4.png?width=90pc)

  Tiếp theo là **Region deny setting** (Cài đặt từ chối vùng), cho phép thiết lập các kiểm soát nhằm cấm truy cập vào các dịch vụ và hoạt động của AWS theo từng vùng (Region).Tùy chọn này có thể được kích hoạt cho vùng hạ cánh (landing zone) và cho các Đơn vị Tổ chức (OUs) riêng lẻ.

  ![Launch Template](/images/2/2.5.png?width=90pc)

3. Bước tiếp theo là **Configure organizational units (OUs)** (Cấu hình các đơn vị tổ chức), trong đó bạn sẽ thiết lập cấu trúc OU cho vùng hạ cánh (landing zone) của mình.
   - **Foundational OU**: AWS Control Tower sẽ tự động tạo một OU bảo mật (Security OU) để giúp bạn bắt đầu với cấu trúc OU được lên kế hoạch tốt. OU này chứa hai tài khoản chia sẻ: tài khoản lưu trữ log (log archive account) và tài khoản kiểm toán bảo mật (security audit account). Bạn có thể thay đổi tên OU này nếu cần, nhưng tên phải là duy nhất và có thể chỉnh sửa sau khi thiết lập vùng hạ cánh.
   - **Additional OU**: Để thiết lập hệ thống đa tài khoản, AWS Control Tower khuyến nghị bạn tạo thêm một OU phụ trong quá trình thiết lập vùng hạ cánh. OU này có thể được sử dụng để lưu trữ bất kỳ tài khoản sản xuất hoặc phát triển nào. Bạn có tùy chọn tạo OU mới hoặc bỏ qua bước này.

  ![Launch Template](/images/2/2.6.png?width=90pc)

  Tạo mới OU có tên là **Sandbox** để chứa các tài khoản AWS đại diện cho từng môi trường (production, development, test,...)

  ![Launch Template](/images/2/2.7.png?width=90pc)

4. Bước tiếp theo ta sẽ cấu hình các tài khoản chia sẻ (shared accounts)

  Tài khoản quản lý sẽ là tại khoản root khi tạo aws, như đã giới thiệu, bạn sẽ cần nhiều tài khoản gmail, hoặc nếu bạn không có nhiều tài khoản gmail thì hãy làm theo Tip mình đã hướng dẫn, sử dụng email gốc nhưng thêm **+something** vào. Tạo tài khoản kiểm toán bảo mật (security audit account) và tài khoản lưu trữ log (log archive account).

  ![Launch Template](/images/2/2.8.png?width=90pc)

  ![Launch Template](/images/2/2.9.png?width=90pc)

5. Bước tiếp theo **cấu hình bổ sung** trong quá trình thiết lập AWS Control Tower
  
  - **AWS Control Tower Sets Up AWS Account Access with IAM Identity Center:** Đây là lựa chọn mặc định và được khuyến nghị cho người dùng mới hoặc khi bạn muốn sử dụng các nhóm và bộ quyền (permission sets) được quản lý bởi AWS Control Tower.
  - **Self-managed AWS Account Access with IAM Identity Center or Another Method**: Lựa chọn này phù hợp nếu bạn có yêu cầu tùy chỉnh cho việc quản lý quyền truy cập tài khoản AWS và không muốn AWS Control Tower quản lý quyền truy cập. Bạn sẽ phải tự cấu hình IAM Identity Center hoặc phương thức truy cập khác.

  Về cấu hình  **AWS CloudTrail Configuration** nhằm mục đích ghi lại các hành động trong AWS Control Tower như các sự kiện (events). Điều này giúp theo dõi và ghi lại các thay đổi, hành động xảy ra trong tổ chức AWS của bạn. Khi kích hoạt, AWS Control Tower sẽ tổng hợp thông tin từ tất cả các tài khoản vào một tổ chức CloudTrail và chuyển thông tin đã ghi nhận vào một bucket Amazon S3 được chỉ định. Điều này giúp theo dõi toàn diện các hoạt động trong tổ chức.

  ![Launch Template](/images/2/2.10.png?width=90pc)

  Cấu hình nhật ký và mã hóa KMS cho Amazon S3 trong AWS Control Tower. 
  - **Log configuration for Amazon S3 - optional:**
    - **Amazon S3 bucket retention for logging:** Cho phép nhập số năm giữ lại nhật ký, mặc định là 1 năm. Thời gian phải là số nguyên từ 1 đến 15, với giá trị dưới 1 năm sẽ được tính theo ngày.
    - **Amazon S3 bucket retention for access logging:** Thiết lập thời gian giữ lại nhật ký truy cập, mặc định là 10 năm. Thời gian giữ tương tự phải nằm trong khoảng từ 1 đến 15 năm, hoặc được tính theo ngày nếu dưới 1 năm.
  - **KMS Encryption - optional:**
    - AWS Key Management Service (KMS) giúp tạo và quản lý các khóa mã hóa, kiểm soát tài nguyên trong AWS Control Tower.
    - Bạn có thể chọn tùy chọn "Enable and customize encryption settings" (Bật và tùy chỉnh cài đặt mã hóa) nếu muốn sử dụng mã hóa KMS cho nhật ký AWS CloudTrail và AWS Config.
    - Lưu ý: Không hỗ trợ các khóa mã hóa đa vùng (multi-region keys).
  ![Launch Template](/images/2/2.11.png?width=90pc) 

6. Bước cuối cùng sẽ là review lại và tiến hành **set up landing zone**
   
   ![Launch Template](/images/2/2.12.png?width=90pc) 

   ![Launch Template](/images/2/2.13.png?width=90pc) 

   ![Launch Template](/images/2/2.14.png?width=90pc) 

   ![Launch Template](/images/2/2.15.png?width=90pc) 

Chúng ta sẽ mất một khoản thời gian chờ đợi, các chi tiết thiết lập cũng sẽ được hiển thị 

![Launch Template](/images/2/2.16.png?width=90pc) 