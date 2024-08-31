+++
title = "Dọn dẹp tài nguyên"
date = 2021-06-08T18:57:03+07:00
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

Để xóa **AWS IAM Identity Center**, **AWS Control Tower**, và **AWS Organizations**, bạn cần thực hiện các bước cẩn thận để đảm bảo rằng mọi tài nguyên và cấu hình liên quan được gỡ bỏ đúng cách mà không ảnh hưởng đến môi trường AWS của bạn. Dưới đây là hướng dẫn chi tiết từng bước:

### 1. Xóa AWS IAM Identity Center:
**Lưu ý:** Trước khi xóa AWS IAM Identity Center, hãy đảm bảo rằng bạn không còn cần các thiết lập về quản lý danh tính và quyền truy cập của dịch vụ này.

**Các bước thực hiện:**

**1. Xóa Permission Sets:**
- Truy cập vào AWS Management Console.
- Điều hướng đến IAM Identity Center (trước đây là AWS SSO).
- Chọn Permission Sets, và xóa từng permission set không còn cần thiết.
  
**2. Xóa Users và Groups:**
- Chọn Users và Groups, sau đó xóa từng người dùng và nhóm không còn cần thiết.

**3. Xóa Cấu Hình Nhà Cung Cấp Danh Tính Bên Ngoài (Nếu Có):**
- Nếu bạn đã thiết lập kết nối với nhà cung cấp danh tính bên ngoài (Identity Provider - IdP), hãy xóa cấu hình này trong mục Settings của IAM Identity Center.

**4. Vô Hiệu Hóa IAM Identity Center:**
- Vào Settings trong IAM Identity Center.
- Nhấp vào Disable IAM Identity Center để vô hiệu hóa dịch vụ.

### Xóa AWS Control Tower:
**Lưu ý:** Hãy chắc chắn rằng bạn đã di chuyển hoặc sao lưu bất kỳ dữ liệu nào quan trọng trong các tài khoản được quản lý bởi Control Tower.

**Các bước thực hiện:**

**1. Dừng AWS Control Tower:**
- Truy cập AWS Management Console và điều hướng đến AWS Control Tower.
- Chọn Landing zone settings.
- Nhấp vào Decommission landing zone để bắt đầu quá trình gỡ bỏ AWS Control Tower.
  
**2. Xóa Các Tài Nguyên Được Tạo Bởi Control Tower:**
- CloudFormation Stacks: Xóa tất cả các stack liên quan đến AWS Control Tower, bắt đầu với những stack phụ thuộc trước khi xóa stack chính.
- AWS Service Catalog Products: Gỡ bỏ các sản phẩm được tạo qua AWS Service Catalog.
  
**3. Xóa Các Tài Khoản Chia Sẻ (Log Archive, Audit):**
- Nếu các tài khoản Log Archive và Audit không còn cần thiết, bạn có thể chuyển hoặc xóa chúng.
  
### Xóa AWS Organizations:
**Lưu ý:** Đảm bảo rằng bạn đã gỡ bỏ tất cả các tài khoản con (child accounts) khỏi tổ chức trước khi xóa AWS Organizations.

**Các bước thực hiện:**

**1. Di Chuyển Hoặc Xóa Các Tài Khoản Con:**
- Truy cập vào AWS Organizations từ AWS Management Console.
- Chọn các tài khoản con, và chuyển chúng ra khỏi tổ chức hoặc xóa nếu chúng không còn cần thiết.
  
**2. Xóa Các OUs (Organizational Units) và SCPs:**
- Xóa tất cả các Organizational Units (OUs) và Service Control Policies (SCPs) đã tạo trong tổ chức.

**3. Xóa Tổ Chức:**
- Sau khi đã xóa tất cả các tài khoản con, OUs và SCPs, quay lại màn hình chính của AWS Organizations.
- Chọn Delete Organization để gỡ bỏ AWS Organizations hoàn toàn.