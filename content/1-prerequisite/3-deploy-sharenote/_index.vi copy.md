+++
title = "Triển khai Máy ảo ShareNote"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3. </b>"
+++

Trong bài thực hành này, chúng ta sẽ thiết lập cấu hình Database cho ShareNote. Sau đó,chúng ta sẽ thiết lập tự động khởi chạy ứng dụng khi khởi chạy Instance. 

{{% notice info %}}
Nếu bạn đã làm bài số 000005 [Triển Khai AWS RDS Kết Hơp với ShareNote](https://000005.awsstudygroup.com/vi/), bạn có thể thấy rằng bạn đã triển khai ShareNote một cách thủ công. Ở bài này, bạn sẽ thiết lập khởi chạy ứng dụng cho EC2 Instance để mỗi khi một EC2 Instance mới được tạo ra bởi Auto Scaling Group, EC2 Instance đó sẽ tự động được thiết lập để triển khai ứng dụng ShareNote.
{{% /notice %}}

**Nội dung:**
- [Thiết lập cấu hình Database cho ShareNote](#thiết-lập-cấu-hình-database-cho-sharenote)
- [Thiết lập khởi chạy ứng dụng khi khởi chạy instance](#thiết-lập-khởi-chạy-ứng-dụng-khi-khởi-chạy-instance)

{{% notice note %}}
Để vượt qua bài lab này, bạn cần có triển khai sẵn một Ubuntu Instance. Nếu bạn chưa biết cách làm, hãy tham khảo bài [Sử dụng Máy ảo Linux](https://000004.awsstudygroup.com/0-getting-started-ec2/1-create-ec2-instance/3-working-with-linux-instance/). *Lưu ý, hãy chọn AMI **Ubuntu Server 20.04 LTS (HVM)** thay vì **Amazon Linux 2 AMI (HVM)**.*
{{% /notice %}}

#### Thiết lập cấu hình Database cho ShareNote

Chúng ta sẽ bắt đầu tạo một đoạn script thiết lập (startup.sh) để khởi chạy ứng dụng ShareNote. Đoạn script startup.sh sẽ được cấu hình để tự động triển khai khi EC2 Instance khởi chạy.

{{% notice info %}}
Bạn sẽ sử dụng Vi Editor, một trình soạn thảo văn bản được sử dụng phổ biến trên hệ điều hành Linux/Unix, để viết script thiết lập *startup.sh*. Bạn có thể tham khảo thêm tại [**link**](https://vinasupport.com/huong-dan-su-dung-co-ban-lenh-vi-editor-tren-linux/) này hoặc tự tìm hiểu.
{{% /notice %}}


1. Kết nối đến Ubuntu instance đã được khởi tạo.
2. Từ cửa sổ dòng lệnh, nhập lệnh sau để tạo tập tin chứa script bằng **vi editor**
    ```bash
    sudo vi /etc/init.d/startup.sh
    ```

3. Nhấn phím **i** rồi nhập nội dung script như sau:
    ```bash
    # Cập nhật Ubuntu Instane và cài đặt JRE
    sudo apt update
    sudo apt install openjdk-8-jre-headless

    # Thiết lập cấu hình Database cho ShareNote
    export MYSQL_HOST=<Replace with your DB Isntance Endpoint>
    export MYSQL_DATABASE=NoteDB
    export MYSQL_USER=admin
    export MYSQL_PASSWORD=<Replace with your password>

    # Tải xuống và khởi chạy ứng dụng ShareNote.
    wget "https://example-corp-storage.s3.amazonaws.com/deploy-artifact/demo-0.0.1-SNAPSHOT.jar" -O demo-0.0.1-SNAPSHOT.jar
    java -jar demo-0.0.1-SNAPSHOT.jar &
    ```
4. Nhấn phím **ESC** rồi gõ ```:wq``` để lưu lại script và thoát ra ngoài.
5. Thiết lập thuộc tính của script để bạn có kích hoạt được (*executable*) bằng lệnh:
    ```bash
    sudo chmod +x /etc/init.d/startup.sh
    ```

Dựa vào đoạn mã trên, chúng ta thấy:
- **MYSQL_HOST**: Chứa thông tin **Endpoint** của DB Instance mà chúng ta đã tạo ở phần trước. (Ví dụ: *sharenote-db.caslv76qrmsi.ap-southeast-1.rds.amazonaws.com*)
- **MYSQL_DATABASE**: Là tên của Database được khởi tạo trong quá trình tạo DB instance ở phần trước. (Ví dụ: *NoteDB*)
- **MYSQL_USER**: User mặc định khi khởi tạo. (Ví dụ: *admin*)
- **MYSQL_PASSWORD**: Mật khẩu được đặt cho user admin (Ví dụ: *admin123*)
![ShareNote](../../../images/1/1.3_ViEditor.png?width=90pc)

6. Bạn có thể kiểm tra script thiết lập của mình bằng cách khởi chạy thử nó với dòng lệnh dưới đây:
    ```bash
    . /etc/init.d/startup.sh
    ```
7. ShareNote sẽ được khởi chạy và kết nối đến Database như hình sau.
![Success](../../../images/1/1.3_Success.png?width=90pc)


#### Thiết lập khởi chạy ứng dụng khi khởi chạy instance
Trên Ubuntu, chúng ta có thể thiết lập hệ thống để nó tự động triển khai đoạn script khi EC2 Instance được khởi chạy.

1. Kết nối đến Ubuntu instance đã được khởi tạo.
2. Chạy lệnh sau để mở thiết lập crontab và thiết lập việc khởi chạy ứng dụng khi instance được khởi chạy.
    ```bash
    crontab -e
    ```
3. Trong phần chọn editor (*select editor*), gõ số 2 rồi nhấn phím **Enter** để chọn **/user/bin/vim.basic**
4. Nhấn phím **i** để có thể chỉnh sửa rồi nhập nội dung sau vào cuối các nội dung để thiết lập tự động triển khai script khi khởi động.
    ```bash
    @reboot /etc/init.d/startup.sh
    ```
5. Khi nhập xong, nhấn phím **ESC** rồi gõ ```:wq``` để lưu lại script và thoát ra ngoài crontab.
![ShareNote](../../../images/1/1.3_Reboot.png?width=90pc)