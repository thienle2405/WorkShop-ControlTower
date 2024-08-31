+++
title = "Quản lý nhiều tài khoản bằng AWS Control Tower và Identity Center"
date = 2021
weight = 1
chapter = false
+++

# Quản lý nhiều tài khoản bằng AWS Control Tower và Identity Center

#### Tổng quan

Trong các dự án AWS, việc vận hành hiệu quả và đảm bảo bảo mật là yếu tố quan trọng hàng đầu. Một trong những phương pháp tốt nhất để đạt được điều này là chia tách các môi trường (như phát triển, thử nghiệm, sản xuất) trên các tài khoản AWS khác nhau. Việc phân chia như vậy giúp kiểm soát quyền truy cập tốt hơn, cô lập các tài nguyên, và giảm thiểu rủi ro bảo mật khi có sự cố xảy ra trong một tài khoản.

Bài viết này sẽ hướng dẫn cách sử dụng **AWS IAM Identity Center** (trước đây là AWS SSO) kết hợp với **AWS Control Tower** để thiết lập và quản lý môi trường đa tài khoản một cách an toàn. **AWS Control Tower** giúp thiết lập một landing zone chuẩn hóa, tự động hóa việc tạo các tài khoản AWS với các biện pháp bảo mật và tuân thủ được tích hợp sẵn. Trong khi đó, **IAM Identity Center** đơn giản hóa việc quản lý quyền truy cập và phân quyền cho người dùng trên các tài khoản AWS, giúp dễ dàng kiểm soát ai có thể làm gì trong từng tài khoản cụ thể.

#### AWS Control Tower
**AWS Control Tower** là dịch vụ giúp đơn giản hóa việc thiết lập và quản lý môi trường AWS đa tài khoản an toàn, tuân thủ các thực tiễn tốt nhất của AWS. Nó thiết lập một **Landing zone** an toàn với các tài khoản AWS, kiến trúc mạng cơ bản, và các kiểm soát bảo mật và tuân thủ.

#### Các tính năng chính của AWS Control Tower bao gồm:
1. **Account Vending**: AWS Control Tower tự động hóa việc tạo các tài khoản AWS mới, áp dụng các chính sách và cấu hình đã được xác định trước trong quá trình thiết lập tài khoản. Điều này giúp đảm bảo tính nhất quán và tuân thủ trên tất cả các tài khoản.
2. **Multi-account structure:** Control Tower thiết lập một môi trường đa tài khoản dựa trên các phương pháp tốt nhất của AWS, bao gồm việc sử dụng AWS Organizations để tạo và quản lý các tài khoản, và các Đơn vị Tổ chức (OUs) để tổ chức các tài khoản.
3. **Guardrails:** Control Tower thực hiện các guardrails, là các chính sách được cấu hình sẵn, để đảm bảo an ninh, tuân thủ, và các phương pháp hoạt động tốt nhất. Guardrails giúp ngăn chặn các hành động và cấu hình không tuân thủ.
   + **Detective Guardrails:** Giúp cung cấp khả năng hiển thị vào môi trường AWS, ví dụ như bật AWS CloudTrail và AWS Config.
   + **Preventive Guardrails:** Ngăn chặn các hành động hoặc cấu hình không tuân thủ, ví dụ như buộc sử dụng MFA cho người dùng IAM và ngăn chặn việc tạo S3 buckets không an toàn.
   + **Infrastructure Guardrails:** Xử lý các yếu tố cơ bản trong môi trường AWS, bao gồm việc thiết lập AWS Landing Zone, tổ chức tài khoản và cấu hình VPCs.
   + **Data Residency Guardrails:** Đáp ứng các yêu cầu về lưu trữ và chủ quyền dữ liệu, ví dụ như thiết lập các AWS Regions phù hợp.
   + **Operational Guardrails:** Tập trung vào các thực tiễn vận hành tốt nhất, như cấu hình AWS CloudWatch Alarms và định nghĩa các chính sách sao lưu và lưu giữ dữ liệu.

#### Service Control Policies (SCPs)
**SCPs** là loại guardrail cho phép thiết lập các quyền và hạn chế chi tiết trên các dịch vụ và hành động trong tài khoản hoặc OU, đảm bảo chỉ những hành động được phép mới có thể thực hiện.

#### Audit
Cung cấp khả năng giám sát tuân thủ thông qua AWS Config và AWS CloudTrail, giúp theo dõi các thay đổi, tuân thủ và điều tra các sự cố bảo mật.

#### Centralized Logging and Monitoring
Tích hợp với **AWS Config**, **AWS CloudTrail**, và **AWS Config Rules** để cung cấp khả năng ghi nhật ký và giám sát tập trung, đảm bảo tuân thủ và bảo mật cho môi trường AWS.

#### AWS Organizations
**AWS Organizations** là dịch vụ giúp tổ chức và quản lý nhiều tài khoản AWS trong một môi trường tập trung. Nó cho phép tạo cấu trúc phân cấp tài khoản với các OUs và áp dụng các SCPs để quản lý quyền truy cập và bảo mật trên các tài khoản AWS trong toàn tổ chức.

#### AWS IAM Identity Center (trước đây là SSO)
+ Service này kế thừa AWS Single Sign-On và là dịch vụ quản lý tập trung từng người dùng trong môi trường có nhiều tài khoản được vận hành trong AWS organization, giúp bạn dễ dàng đăng nhập vào từng tài khoản.
+ Là service được khuyên dùng for managing human user access to AWS resources
+ Cho phép bạn kết nối không chỉ các aws account, mà còn Bussiness Cloud App hoặc Custom SAML2.0-enable Apps
+ IAM Identity Center kết hợp với MS AD để lưu và retrieve thông tin user

![Diagram](/images/home/IAMIdentityCenter.png?width=60pc)

#### Nội dung:
1. [Tổng quan ](1-overview)
2. [Thiết lập Control Tower ](2-control-tower)
3. [Thiết lập IAM Identity Center](3-iam-identity-center)
4. [Khởi tạo SCP và Permission sets](4-scp-permissionsets)
5. [Phát triển thêm ](5-further-development) 
6. [Kiểm tra kết quả](6-testing)