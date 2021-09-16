+++
title = "Khởi tạo Auto Scaling Group"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

Ở phần này, chúng ta sẽ triển khai một Auto Scaling Group cho ứng dụng ShareNote để đảm bảo ứng dụng của chúng ta sẽ được triển khai với tính sẵn sàng cao, và có khả năng tăng số lượng EC2 instance khi người dùng truy cập vào hệ thống tăng.

#### Tạo AutoScaling Group

1. Truy cập vào **EC2 Management Console**.
2. Ở thanh điều hướng bên trái, chọn **Auto Scaling Groups**.
3. Ở trang **Auto Scaling Groups**, chọn **Create an Auto Scaling group**.

![Launch Template](/images/asg/034.png?width=90pc)

4. Bắt đầu với trang **Choose launch template or configuration**, thiết lập các thông tin như sau:
  + Name: Nhập vào tên của Auto Scaling Group (VD: **sharenote-asg**)
  + Launch template: Chọn launch template chúng ta đã tạo trước đó (VD: sharenote-template)
  + Kéo màn hình xuống dưới và click **Next**.

![Launch Template](/images/asg/035.png?width=90pc)

5. Ở trang **Configure settings**:
  + Mục **Network**, phần **Subnets**  Lựa chọn 2 subnet ở hai AZ  **ap-northeast-1a** và **ap-northeast-1b**.
  + Kéo màn hình xuống dưới và click **Next**.

![Launch Template](/images/asg/036.png?width=90pc)

6. Ở trang **Configure advanced options**:
   + Mục **Load balancing - optional** click chọn **Attach to an existing load balancer**.
   + Click chọn **Choose from your load balancer target groups**.
   + Click chọn target group  mà chúng ta đã tạo trước đó. (VD: **sharenote-tg**)
   + Kéo màn hình xuống dưới và click **Next**.

![Launch Template](/images/asg/037.png?width=90pc)

7. Ở trang **Configure group size and scaling policies**:
    - Group size - optional:
      - Desired capacity: Nhập **1**. (Default)
      - Minimum capacity: Nhập **1**. (Default)
      - Maximum capacity: Nhập **3**.

![Launch Template](/images/asg/038.png?width=90pc)

8. Tại mục **Scaling policies - optional:** Lựa chọn trong bài thực hành này nhằm tạo điều kiện dễ dàng hơn cho bước kiểm tra được thực hiện tiếp theo. Bạn hoàn toàn có thể thiết lập chính sách scale tài nguyên theo nhu cầu của bạn.
  + Chọn **Target tracking scaling policy**.
  + Metric type: Chọn **Application Load Balancer request count per target**.
  + Target group: Chọn target group mà chúng ta đã tạo (VD: **sharenote-tg**).
  + Target value: Nhập **30**.
  + Click **Next**.

![Launch Template](/images/asg/039.png?width=90pc)

9. Ở trang **Add notifications**, chọn **Next**.
10. Ở trang **Add tags**, chọn **Next**.
11. Ở trang **Review**, chọn **Create Auto Scaling Group**

Quá trình khởi tạo Auto Scaling Group sẽ được thực hiện, Auto Scaling Group vừa được tạo sẽ hiển thị trong danh sách, và bạn có thể chọn vào nó để xem thông tin chi tiết. 

Vhúng ta có thể theo dõi các EC2 instance hiện có trong Auto Scaling Group ở trang **Instance management**. Các instance có tình trạng **InService** là các instance đã sẵn sàng hoạt động.

![Launch Template](/images/asg/040.png?width=90pc)


Đến đây, chúng ta đã hoàn thành việc triển khai ứng dụng Share Note với Auto Scaling Group và Elastic Load Balancer. Với mô hình này, bạn có thể triển khai ứng dụng của mình với tính sẵn sàng cao, dễ dàng mở rộng và cân bằng tải các yêu cầu từ người dùng.

Ở bước kế tiếp, chúng ta sẽ thử nghiệm tính năng thêm EC2 Instance dựa trên việc tăng số lượng truy cập đến ứng dụng của chúng ta.

{{%notice tip%}}
Trước khi thực hiện bước kế tiếp hãy kiểm tra cấu hình Automatic scaling của Auto Scaling Group của chúng ta có giống như dưới đây không. Nếu quá trình tạo scaling policy bị lỗi, chúng ta có thể click **Create dynamic scaling policy** để tiến hành tạo lại scaling policy mới.
{{%/notice%}}

![Launch Template](/images/asg/041.png?width=90pc)
