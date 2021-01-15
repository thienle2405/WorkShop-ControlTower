+++
title = "Tạo Security Group"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1. </b>"
+++

**Nội dung:**
- [Tạo Security Group](#tạo-security-group)

Chúng ta sẽ bắt đầu với việc tạo một Security Group cho bài thực hành này.

Để xác định các rule Inbound cần có, chúng ta liệt kê ra các yêu cầu như sau:
- Người dùng truy cập từ ngoài vào ứng dụng Share Note thông qua cổng 80 với giao thức HTTP với Source IP bất kì.
- Load Balancer sẽ điều phối các yêu cầu này đến các server thông qua cổng 8080 với Source IP trong VPC.
- Các Application server sẽ giao tiếp với Database thông qua cổng 3306 với Source IP trong VPC.
- Chúng ta sẽ mở truy cập SSH để có thể kết nối đến instance để triển khai ứng dụng.

{{% notice note %}}
Trên thực tế, chúng ta nên tạo các security group riêng biệt cho từng thành phần. Tuy nhiên trong khuôn khổ bài thực hành này, chúng ta sẽ sử dụng một security group (Các rule không trùng lẫn nhau).
{{% /notice %}}

#### Tạo Security Group

Dựa vào đó, chúng ta bắt đầu tạo Security Group theo các bước như sau:
1. Truy cập vào **AWS Management Console**. Lựa chọn **Services** ở thanh điều hướng và tìm kiếm dịch vụ **EC2**.
2. Ở thanh điều hướng bên trái, chọn **Security Groups**.
3. Ở trang **Security Groups**, chọn **Create Security Group**.
4. Ở trang **Create security group**, thiết lập các thông số như sau:
   - Basic details:
     - Security group name: Nhập vào tên security group (VD: **sharenote-sg**)
     - Description: Nhập vào diễn giải của security group.
   - Inbound rules: Thêm các **Inbound rule** như đề cập ở trên. Chọn **Add rule** để thêm một rule.
     - Type: **HTTP** | Source: **Anywhere**
     - Type: **Custom TCP** | Port range: **8080** | Source: Custom **172.31.0.0/16** (VPC CIDR block)
     - Type: **MySQL/Aurora** | Source: Custom **172.31.0.0/16** (VPC CIDR block)
     - Type: **SSH** | Source: **My IP**
![Security Group](../../../images/1/1.png?width=90pc)
5. Chọn **Create security group**.

Chúng ta đã hoàn thành việc tạo Security Group.