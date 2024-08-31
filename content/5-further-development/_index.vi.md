+++
title = "Phát triển thêm"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

Khi tạo Set up landing zone, mặc định có 2 account được tạo ra là Log archive account và Audit account, chúng ta có thể mở rộng bài toán bằng cách nhiều cách hơn như sau 

#### Tích Hợp AWS Service Catalog
AWS Service Catalog là một công cụ mạnh mẽ cho phép bạn cung cấp, quản lý và kiểm soát việc triển khai các sản phẩm AWS đã được tiêu chuẩn hóa trong tổ chức của bạn. Điều này rất quan trọng để đảm bảo rằng các dịch vụ được triển khai tuân thủ theo các tiêu chuẩn và chính sách bảo mật đã định trước.

**Mở rộng và ứng dụng:**

  - **Tạo Danh Mục Dịch Vụ Tiêu Chuẩn:** Bạn có thể tạo ra các danh mục dịch vụ bao gồm các mẫu CloudFormation, các tài nguyên như EC2, RDS, hoặc Lambda đã được cấu hình sẵn theo các tiêu chuẩn của tổ chức. Điều này giúp đảm bảo rằng các nhóm trong tổ chức chỉ triển khai các dịch vụ đã được phê duyệt và tuân thủ các chính sách bảo mật.

  - **Quản Lý Các Phiên Bản Dịch Vụ:** AWS Service Catalog cho phép quản lý nhiều phiên bản của các sản phẩm, giúp tổ chức dễ dàng duy trì và cập nhật các dịch vụ AWS theo những cải tiến mới mà vẫn đảm bảo tuân thủ các quy định nội bộ.

  - **Kiểm Soát Chi Phí và Quyền Truy Cập:** Bằng cách tích hợp với IAM, bạn có thể kiểm soát ai có thể triển khai các sản phẩm nào và theo dõi việc sử dụng các tài nguyên AWS, giúp kiểm soát chi phí và đảm bảo rằng các tài nguyên không bị lạm dụng.

#### Thiết Lập Giám Sát và Thông Báo Tập Trung
**Amazon CloudWatch** và **Amazon SNS** đóng vai trò quan trọng trong việc thiết lập giám sát và cảnh báo tập trung cho môi trường AWS của bạn, giúp bạn nhanh chóng phát hiện và phản ứng với các sự cố hoặc hoạt động bất thường.

**Mở rộng và ứng dụng:**
  - **Log Archive Account:**
    - **Dịch vụ cần thiết:** Amazon CloudTrail, AWS Config, Amazon S3, và Amazon CloudWatch.
    - **Vai trò:** Tài khoản này lưu trữ tất cả các log từ CloudTrail và Config, cung cấp một kho lưu trữ tập trung và bảo mật cho các bản ghi hoạt động trên toàn bộ các tài khoản AWS.
    - **Ứng dụng cụ thể:**
      - **CloudWatch:** Thiết lập CloudWatch Logs để giám sát các log nhập từ CloudTrail và AWS Config, thiết lập các chỉ số và cảnh báo để phát hiện hoạt động bất thường hoặc vi phạm chính sách bảo mật.
      - **S3:** Lưu trữ dài hạn các log trong S3 với chính sách giữ lại và mã hóa để bảo mật thông tin.
  
  - **Audit Account:**
    - **Dịch vụ cần thiết:** AWS IAM, AWS Config, Amazon CloudWatch, và Amazon SNS.
    - **Vai trò:** Tài khoản này chịu trách nhiệm giám sát chéo tài khoản, cung cấp quyền kiểm tra và cảnh báo về các vi phạm bảo mật hoặc hoạt động không tuân thủ.
    - **Ứng dụng cụ thể:**
      - **IAM:** Tạo các vai trò kiểm toán chéo tài khoản để cho phép truy cập chỉ đọc vào các tài khoản khác mà không cần quyền cao hơn.
      - **CloudWatch:** Thiết lập các chỉ số giám sát bảo mật, như theo dõi sự thay đổi trong cấu hình bảo mật hoặc truy cập bất thường.
      - **SNS:** Cấu hình SNS để gửi cảnh báo qua email hoặc SMS cho nhóm bảo mật khi phát hiện các sự kiện quan trọng, như thay đổi quyền truy cập hoặc cấu hình không hợp lệ.

![Application Load Balancer](/images/5/5.1.png?width=90pc)