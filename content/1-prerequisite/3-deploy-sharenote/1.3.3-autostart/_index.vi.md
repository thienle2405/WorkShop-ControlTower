+++
title = "Thiết lập khởi chạy ứng dụng khi khởi chạy instance"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3.3 </b>"
+++

#### Thiết lập khởi chạy ứng dụng khi khởi chạy instance
Trên Ubuntu, chúng ta có thể thiết lập hệ thống để nó tự động triển khai đoạn script khi EC2 Instance được khởi chạy.

1. Ấn phím Enter để tiếp tục trở lại giao diện dòng lệnh , sau khi chạy thử script startup.sh thành công.

![ShareNote](/images/asg/014.png?width=90pc)

2. Chạy lệnh sau để mở thiết lập crontab và thiết lập việc khởi chạy ứng dụng khi instance được khởi chạy.

```bash
crontab -e
```

3. Trong phần chọn editor (*select editor*), gõ số 2 rồi nhấn phím **Enter** để chọn **/user/bin/vim.basic**

![ShareNote](/images/asg/015.png?width=90pc)

4. Nhấn phím **i** để có thể chỉnh sửa rồi nhập nội dung sau vào cuối các nội dung để thiết lập tự động triển khai script khi khởi động. ( Ấn phím mũi tên để xuống dòng )

```bash
@reboot /etc/init.d/startup.sh
```
![ShareNote](/images/asg/016.png?width=90pc)

5. Khi nhập xong, nhấn phím **ESC** rồi gõ ```:wq``` để lưu lại script và thoát ra ngoài crontab.

![ShareNote](/images/1/1.3_Reboot.png?width=90pc)