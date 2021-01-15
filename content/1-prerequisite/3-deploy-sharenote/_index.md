+++
title = "Deploy ShareNote Instance"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3. </b>"
+++

**Nội dung:**
- [Thiết lập cấu hình Database cho ShareNote](#thiết-lập-cấu-hình-database-cho-sharenote)
- [Thiết lập khởi chạy ứng dụng khi khởi chạy instance](#thiết-lập-khởi-chạy-ứng-dụng-khi-khởi-chạy-instance)

Ứng dụng ShareNote cho phép tạo các ghi chú và chia sẻ cho tất cả các người dùng khác. 
ShareNote có thể được triển khai dễ dàng trên cả Windows và Linux.  
Để tìm hiểu về triển khai ShareNote, bạn có thể truy cập vào [Triển khai Ứng dụng ShareNote trên Máy ảo Windows/Ubuntu]()

{{% notice note %}}
Trong bài thực hành này, chúng ta sẽ sử dụng instance Ubuntu để triển khai Share Note. Instance này sẽ được triển khai Share Note và được sử dụng cho bước tiếp theo.
{{% /notice %}}

#### Thiết lập cấu hình Database cho ShareNote
Đối với bài thực hành này, chúng ta không sử dụng local database nữa mà thay vào đó là sử dụng dịch vụ Amazon RDS.

Chúng ta sẽ bắt đầu tạo một đoạn script thiết lập và khởi chạy ứng dụng ShareNote (startup.sh)
1. Kết nối đến Ubuntu instance đã được khởi tạo.
2. Từ cửa sổ dòng lệnh, nhập lệnh sau để tạo tập tin chứa script (đường dẫn có thể thay đổi)
```bash
$ sudo vi /etc/init.d/startup.sh
```
3. Nhập nội dung script và các thông tin của bạn vào tập tin.
```bash
export MYSQL_HOST=sharenote-rds.cxm2fv9obino.ap-northeast-1.rds.amazonaws.com
export MYSQL_DATABASE=NoteDB
export MYSQL_USER=admin
export MYSQL_PASSWORD=*Replace with your password*

wget "https://example-corp-storage.s3.amazonaws.com/deploy-artifact/demo-0.0.1-SNAPSHOT.jar" -O demo-0.0.1-SNAPSHOT.jar
java -jar demo-0.0.1-SNAPSHOT.jar &
```
4. Lưu tập tin lại với ```:wq``` trong **vi editor**.
5. Thiết lập thuộc tính cho script mà chúng ta vừa viết.
```bash
$ sudo chmod +x /etc/init.d/startup.sh
```

{{%attachments style="blue" title="Related files" pattern=".*(sh)"/%}}

Dựa vào đoạn mã trên, chúng ta thấy:
- MYSQL_HOST:   Chứa thông tin **Endpoint** của Database mà chúng ta đã tạo ở phần trước.
- MYSQL_DATABASE:   Là **tên database** được khởi tạo trong quá trình tạo database instance ở phần trước.
- MYSQL_USER:   User mặc định khi khởi tạo.
- MYSQL_PASSWORD:   Mật khẩu được đặt cho user admin.

![ShareNote](../../../images/1/6.png?width=90pc)

Bạn có thể khởi chạy thử bằng việc chạy đoạn mã trên. Share Note sẽ được khởi chạy và kết nối đến Database và chúng ta có thể truy cập ngay lập tức ở localhost.

#### Thiết lập khởi chạy ứng dụng khi khởi chạy instance
Trên Ubuntu, chúng ta có thể thiết lập hệ thống khởi chạy đoạn script khởi chạy Share Note khi instance được Start.

1. Kết nối đến Ubuntu instance đã được khởi tạo.
2. Chạy lệnh sau để mở thiết lập crontab và thiết lập việc khởi chạy ứng dụng khi instance được khởi chạy.
```bash
$ crontab -e
```
3. Nhập nội dung sau vào cuối các nội dung (đường dẫn đến tập tin script có thể khác và bạn cần thay đổi để phù hợp) để thiết lập khởi chạy script khi khởi động.
```bash
@reboot /etc/init.d/startup.sh
```
4. Nhấn tổ hợp phím ```Ctr + X``` để thoát và ```Y``` để đồng ý lưu thay đổi cho crontab.
![ShareNote](../../../images/1/7.png?width=90pc)

Bạn có thể kiểm tra bằng việc khởi động lại instance.