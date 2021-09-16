+++
title = "Thiết lập cấu hình Database cho ShareNote"
date = 2020
weight = 2
chapter = false
pre = "<b>1.3.2 </b>"
+++


#### Thiết lập cấu hình Database cho ShareNote

Chúng ta sẽ bắt đầu tạo một đoạn script thiết lập (startup.sh) để khởi chạy ứng dụng ShareNote. Đoạn script startup.sh sẽ được cấu hình để tự động triển khai khi EC2 Instance khởi chạy.

{{% notice info %}}
Bạn sẽ sử dụng Vi Editor, một trình soạn thảo văn bản được sử dụng phổ biến trên hệ điều hành Linux/Unix, để viết script thiết lập *startup.sh*. Bạn có thể tham khảo thêm tại [**link**](https://vinasupport.com/huong-dan-su-dung-co-ban-lenh-vi-editor-tren-linux/) này hoặc tự tìm hiểu.
{{% /notice %}}


1. Kết nối đến Ubuntu instance đã được khởi tạo.
2. Từ cửa sổ dòng lệnh, nhập lệnh sau để tạo tập tin chứa script bằng **vi editor**.

```bash
sudo vi /etc/init.d/startup.sh
```
{{% notice info %}}
Lưu ý thay thể RDS Endpoint và password chúng ta đã lưu lại ở bước 1.2 .
{{% /notice %}}
3. Nhấn phím **i** rồi nhập nội dung script như sau:

```
# Cập nhật Ubuntu Instane và cài đặt JRE
sudo apt update -y
sudo apt install openjdk-8-jre-headless -y

# Thiết lập cấu hình Database cho ShareNote
export MYSQL_HOST=<Replace with your DB Instance Endpoint>
export MYSQL_DATABASE=NoteDB
export MYSQL_USER=admin
export MYSQL_PASSWORD=<Replace with your password>

# Tải xuống và khởi chạy ứng dụng ShareNote.
wget "https://example-corp-storage.s3.amazonaws.com/deploy-artifact/demo-0.0.1-SNAPSHOT.jar" -O demo-0.0.1-SNAPSHOT.jar
java -jar demo-0.0.1-SNAPSHOT.jar &
```
![ShareNote](/images/asg/013.png?width=90pc)

Dựa vào đoạn mã trên, chúng ta thấy:
- **MYSQL_HOST**: Chứa thông tin **Endpoint** của DB Instance mà chúng ta đã tạo ở phần trước. (Ví dụ: *sharenote-db.cqjdjbyv5rwc.ap-southeast-1.rds.amazonaws.com*)
- **MYSQL_DATABASE**: Là tên của Database được khởi tạo trong quá trình tạo DB instance ở phần trước. (Ví dụ: *NoteDB*)
- **MYSQL_USER**: User mặc định khi khởi tạo. (Ví dụ: *admin*)
- **MYSQL_PASSWORD**: Mật khẩu được đặt cho user admin (Ví dụ: *admin123*)

4. Nhấn phím **ESC** rồi gõ ```:wq!``` để lưu lại script và thoát ra ngoài.

5. Thiết lập thuộc tính của script để bạn có kích hoạt được (*executable*) bằng lệnh:

```bash
sudo chmod +x /etc/init.d/startup.sh
```

6. Bạn có thể kiểm tra script thiết lập của mình bằng cách khởi chạy thử nó với dòng lệnh dưới đây:
    
``` bash
. /etc/init.d/startup.sh
```
7. ShareNote sẽ được khởi chạy và kết nối đến Database như hình sau.

![Success](/images/1/1.3_Success.png?width=90pc)

Tiếp theo chúng ta sẽ cấu hình để script startup.sh tự chạy mỗi khi instance khởi động.
