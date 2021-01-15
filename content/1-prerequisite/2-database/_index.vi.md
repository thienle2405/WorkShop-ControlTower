+++
title = "Tạo ShareNote Database"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2. </b>"
+++

**Nội dung:**
- [1. Tạo cơ sở dữ liệu với AWS RDS](#1-tạo-cơ-sở-dữ-liệu-với-aws-rds)
- [2. Triển khai Multi-AZ Database](#2-triển-khai-multi-az-database)

Ở bước này, chúng ta sẽ khởi tạo một database cho ứng dụng ShareNote được triển khai ở bước tiếp theo. Với database, chúng ta sẽ sử dụng dịch vụ Amazon RDS.

{{% notice info %}}
Ứng dụng ShareNote sử dụng MySQL nên chúng ta cũng sẽ lựa chọn MySQL Engine.
{{% /notice %}}

#### 1. Tạo cơ sở dữ liệu với AWS RDS 

Chúng ta sẽ bắt đầu khởi tạo Database cho Share Note.

1. Truy cập vào **AWS Management Console**. Lựa chọn **Services** ở thanh điều hướng và tìm kiếm dịch vụ **RDS**.
2. Chọn **Create database**.
3. Lựa chọn các thông số thiết lập cho Database: (Các thông số không được nhắc đến sẽ giữ ở thiết lập mặc địnhđịnh)
   - Choose a database creation method: Chọn **Standard create**
   - Engine options: Chọn **MySQL**
   - Templates: Chọn **Free tier** (Đây là lựa chọn đối với mục tiêu là bài thực hành.)
   - Settings:
     - DB instance identifier: **sharenote-db** (hoặc tên mà bạn mong muốn)
     - Credentials Settings:
       - Master password: Nhập mật khẩu với độ phức tạp theo yêu cầu.
       - Confirm password: Nhập lại một lần mật khẩu
      ![Database](../../../images/1/2.png?width=90pc)
     - Connectivity:
       - Additional connectivity configuration
         - VPC security group: Chọn **Choose existing** (hoặc **Create new** để tạo mới) để chọn Security Group phù hợp
         - Existing VPC security groups: Chọn **sharenote-sg** (hoặc tên Security Group đang có của bạn)
   - Additional configuration:
     - Database options:
       - Initial database name: Nhập vào **NoteDB** (Tên database sẽ được khởi tạo ban đầu)
      ![Database](../../../images/1/3.png?width=90pc)
     - Deletion protection: Chọn vào lựa chọn **Enable deletion protection**
4. Kiểm tra lại và chọn **Create database**.
5. Database sẽ được khởi tạo và ở trạng thái ```Creating```. Hãy đợi cho Status chuyển sang ```Available``` là đã sẵn sàng sử dụng.
![Database](../../../images/1/4.png?width=90pc)
6. Chọn vào **sharenote-db** trong danh sách **Databases**.
7. Ở trang thông tin database, mục **Endpoint & port**, ghi chú lại **Endpoint** của database. Chúng ta sẽ sử dụng thông tin này cho việc cấu hình ở bước kế tiếp.
![Database](../../../images/1/5.png?width=90pc)

Đến đây, chúng ta đã hoàn thành việc tạo Database cho Share Note.

#### 2. Triển khai Multi-AZ Database

Việc triển khai khả năng Dự phòng cho database với AWS RDS là cực kì dễ dàng.

{{% notice note %}}
Đối với trường hợp triển khai trên môi trường **Dev/Test** (hoặc **Production**) bạn nên lựa chọn **Multi-AZ deployment** để tạo thêm một standby instance ở AZ khác phục vụ cho mục tiêu dự phòng.
{{% /notice %}}
