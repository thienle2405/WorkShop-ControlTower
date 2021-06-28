+++
title = "Tạo ShareNote Database"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2. </b>"
+++

Ở bước này, chúng ta sẽ khởi tạo một cơ sở dữ liệu (*database*) sử dụng AWS RDS cho ứng dụng ShareNote được triển khai ở bước tiếp theo.

**Nội dung:**
- [1. Tạo cơ sở dữ liệu với AWS RDS](#1-tạo-cơ-sở-dữ-liệu-với-aws-rds)

#### 1. Tạo cơ sở dữ liệu với AWS RDS 

1. Truy cập vào **RDS Management Console** bằng cách gõ và chọn *RDS* trong thanh tìm kiếm.
2. Chọn **Create database**.
3. Lựa chọn các thông số thiết lập sau cho Database: (**Các thông số không được nhắc đến sẽ giữ ở thiết lập mặc định**)
   - Mục **Choose a database creation method**: Chọn **Standard create**
   - Mục **Engine options**: Chọn **MySQL**
  ![ChooseDatabase](../../../images/1/2_ChooseDB&Engine.png?width=90pc)
  {{% notice info %}}
  Ứng dụng ShareNote sử dụng MySQL nên chúng ta cũng sẽ lựa chọn MySQL Engine.
  {{% /notice %}}
   - Mục **Templates**: Chọn **Free tier** (Đây là lựa chọn đối với mục tiêu là bài thực hành.)
  ![ChooseTemplates](../../../images/1/2_Templates.png?width=90pc)
   - Mục **Settings**:
     - **DB instance identifier**: nhập tên cho DB Instance (ví dụ: **sharenote-db**)

     - **Settings**:
       - **Master username**: thiết lập tài khoản master dùng để truy cập vào cơ sở dữ liệu (ví dụ: **admin**).
       - **Master password**: thiết lập mật khẩu với ít nhất 8 kí tự và **hạn chế** nhập kí tự đặc biệt (ví dụ: **admin123**).
  {{% notice note %}}
  Nếu bạn nhập kí tự đặc biệt (ví dụ: ! hoặc @ hoặc #), khi bạn kết nối tới cơ sở dữ liệu trên DB Instance từ EC2 Instance sử dụng hệ điều hành Ubuntu ở phần sau, bạn sẽ phải thực hiện thao tác bỏ qua (escape) đối với các kí tự đặc biệt ấy, và điều đó sẽ gia tăng độ phức tạp của bài lab này một cách không cần thiết.
  {{% /notice %}}
       - **Confirm password**: Nhập lại mật khẩu ở phía trên.
      ![DatabaseUsername&Password](../../../images/1/2_User&Password.png?width=90pc)
    - Mục **DB Instance Class**: dùng để chọn phân loại DB Instance. **Có 3 phân loại**: tiêu chuẩn (*Standard*), tối ưu bộ nhớ (*Memory optimized*), và hiệu suất linh dộng (*Burstable*). Bạn vui lòng để cấu hình mặc định cho bài lab này.
    - Mục **Storage**: dùng để thiết lập cấu hình cho bộ lưu trữ của DB Instance. Bạn vui lòng để cấu hình mặc định cho bài lab này.
    - Mục **Availability & durability**: dùng để kích hoạt tính năng Multi-AZ. Vì bạn đang sử dụng bản **free-tier**, nên bạn không thể sử dụng tính năng này vì nó có tính phí.
    - Mục **Connectivity**:
       - **Virtual private cloud (VPC)**: giữ nguyên VPC mặc định.
       - **Subnet group**: giữ nguyên Subnet group mặc định.
       - **Public access**: chọn **No**
       - **VPC security group**: Chọn **Choose existing** và giữ nguyên **default**.
       - **Existing VPC security groups**: Chọn tên Security Group mà bạn đã tạo ở phần 1 (ví dụ: **sharenote-sg**)
       - **Availability Zone**: chọn **ap-southeast-1b**
      ![Connectivity](../../../images/1/2_Connectivity.png?width=90pc)
   - Mục **Database Authentication**: giữ nguyên mặc định **Password Authentication**.
   - Mở rộng mục **Additional configuration**:
     - **Database options**:
       - **Initial database name**: Nhập vào tên của database sẽ được khởi tạo ban đầu (ví dụ: **NoteDB**)
       - Các phần còn lại, bạn hãy giữ nguyên mặc định.
      ![Addtional Config](../../../images/1/2_AddConfig_DBName.png?width=90pc)
4. Kiểm tra lại và chọn **Create database**.
5. Database sẽ được khởi tạo và ở trạng thái **Creating**. Hãy đợi cho Status chuyển sang **Available** để có thể sử dụng.
6. Chọn vào **sharenote-db** trong danh sách **Databases**.
7. Ở trang thông tin database, tab **Connectivity & security**, ghi chú lại **Endpoint** của database. Chúng ta sẽ sử dụng thông tin này cho việc cấu hình ở bước kế tiếp.
![Database](../../../images/1/2_DBEndpoint.png?width=90pc)

Đến đây, chúng ta đã hoàn thành việc tạo Database cho ShareNote.
