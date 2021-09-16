+++
title = "Tạo ShareNote Database"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

Ở bước này, chúng ta sẽ khởi tạo một cơ sở dữ liệu (*database*) sử dụng AWS RDS cho ứng dụng ShareNote được triển khai ở bước tiếp theo.


#### Tạo cơ sở dữ liệu cho ShareNote với AWS RDS 

1. Truy cập vào **RDS Management Console** bằng cách gõ và chọn *RDS* trong thanh tìm kiếm.
2. Chọn **Create database**.
3. Lựa chọn các thông số thiết lập sau cho Database: (**Các thông số không được nhắc đến sẽ giữ ở thiết lập mặc định**).
   - Mục **Choose a database creation method**: Chọn **Standard create**.
   - Mục **Engine options**: Chọn **MySQL**.

![ChooseDatabase](/images/asg/002.png?width=90pc)

  {{% notice info %}}
  Ứng dụng ShareNote sử dụng MySQL nên chúng ta cũng sẽ lựa chọn MySQL Engine.
  {{% /notice %}}

   - Kéo màn hình xuống dưới, mục **Templates**: Chọn **Free tier**.

![ChooseTemplates](/images/1/2_Templates.png?width=90pc)

   - Mục **Settings**:
     - **DB instance identifier**: nhập tên cho DB Instance (ví dụ: **sharenote-db**)

     - **Settings**:
       - **Master username**: thiết lập tài khoản master dùng để truy cập vào cơ sở dữ liệu (ví dụ: **admin**).
       - **Master password**: thiết lập mật khẩu với ít nhất 8 kí tự và **hạn chế** nhập kí tự đặc biệt (ví dụ: **admin123**).
       - **Confirm password**: Nhập lại mật khẩu ở phía trên.
  
  {{% notice tip %}}
  Nếu bạn nhập kí tự đặc biệt (ví dụ: ! hoặc @ hoặc #), khi bạn kết nối tới cơ sở dữ liệu trên DB Instance từ EC2 Instance sử dụng hệ điều hành **Ubuntu** ở phần sau, bạn sẽ phải thực hiện thao tác bỏ qua (escape) đối với các kí tự đặc biệt ấy, và điều đó sẽ gia tăng độ phức tạp của bài lab này một cách không cần thiết.
  {{% /notice %}}


![DatabaseUsername&Password](/images/asg/003.png?width=90pc)

4. Tiếp tục kéo màn hình xuống, mục **DB instance Class**: dùng để chọn phân loại DB Instance. 
  + Click chọn phân loại **Burstatble**.
  + Click chọn DB instance class : **db.t2.micro**.
  + Giữ nguyên tùy chọn cho mục **Storage**.

![Database](/images/asg/004.png?width=90pc)

5. Tiếp tục kéo màn hình xuống, mục **Connectivity**:
  +  **Virtual private cloud (VPC)**: giữ nguyên VPC mặc định.
  + **Subnet group**: giữ nguyên Subnet group mặc định.
  + **Public access**: chọn **No**
  + **VPC security group**: Chọn **Choose existing**.
  + **Existing VPC security groups**: Chọn tên Security Group mà bạn đã tạo ở phần 1 (ví dụ: **sharenote-sg** và để nguyên **default** security group.)
  + **Availability Zone**: chọn **ap-southeast-1a**

![Database](/images/asg/005.png?width=90pc)

6. Kéo màn hình xuống và click để mở rộng mục **Additional configuration**.
  + Tại mục **Database options** phần **Initial database name**: Nhập vào tên của database sẽ được khởi tạo ban đầu (ví dụ: **NoteDB**)
  + Các phần còn lại, bạn hãy giữ nguyên mặc định.

![Database](/images/asg/006.png?width=90pc)

7. Kéo màn hình xuống cuối trang và click **Create database**.

8. Database sẽ được khởi tạo và ở trạng thái **Creating**. Hãy đợi cho Status chuyển sang **Available** để có thể sử dụng.

9. Click **sharenote-db** trong danh sách **Databases**.

11. Ở trang thông tin database, tab **Connectivity & security**, ghi chú lại **Endpoint** của database. Chúng ta sẽ sử dụng thông tin này cho việc cấu hình ở bước kế tiếp.

![Database](/images/asg/008.png?width=90pc)

Trong bước này chúng ta đã hoàn thành việc tạo Database cho ShareNote, tiếp theo chúng ta sẽ tạo một EC2 instance để tiến hành cài đặt ứng dụng ShareNote.
