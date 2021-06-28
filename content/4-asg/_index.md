+++
title = "Khởi tạo Auto Scaling Group"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

Ở phần này, chúng ta sẽ triển khai một Auto Scaling Group cho ứng dụng ShareNote để đảm bảo ứng dụng của chúng ta sẽ được triển khai với tính sẵn sàng cao và đáp ứng mục tiêu của bài thực hành này.

**Nội dung:**
- [Tạo AutoScaling Group](#tạo-autoscaling-group)

#### Tạo AutoScaling Group

1. Truy cập vào **EC2 Management Console**.
2. Ở thanh điều hướng bên trái, chọn **Auto Scaling Groups**.
3. Ở trang **Auto Scaling Groups**, chọn **Create an Auto Scaling group**.
4. Bắt đầu với trang **Choose launch template or configuration**, thiết lập các thông tin như sau:
   - Name: Nhập vào tên của Auto Scaling Group (VD: sharenote-asg)
   - Launch template: Chọn launch template chúng ta đã tạo trước đó (VD: sharenote-template)
5. Chọn **Next**.
![Launch Template](../../../images/4/4_step1.png?width=90pc)
6. Ở trang **Configure settings**:
   - Network:
     - Subnets: Lựa chọn 2 subnet ở hai AZ khác nhau (VD: **ap-northeast-1a** và **ap-northeast-1c**)
7. Chọn **Next**.
![Launch Template](../../../images/4/4_step2.png?width=90pc)
8. Ở trang **Configure advanced options**:
   - Load balancing - optional: Chọn Enable load balancing
     - Chọn **Application Load Balancer or Network Load Balancer**.
     - Choose a target group for your load balancer: Chọn target group mà chúng ta đã tạo trước đó. (VD: **sharenote-tg**)
9. Chọn **Next**.
![Launch Template](../../../images/4/4_step3.png?width=90pc)
10. Ở trang **Configure group size and scaling policies**:
    - Group size - optional:
      - Desired capacity: Nhập **1** (Default)
      - Minimum capacity: Nhập **1** (Default)
      - Maximum capacity: Nhập **3**
    - Scaling policies - optional: Lựa chọn trong bài thực hành này nhằm tạo điều kiện dễ dàng hơn cho bước kiểm tra được thực hiện tiếp theo. Bạn hoàn toàn có thể thiết lập chính sách co dãn theo nhu cầu của bạn.
      - Chọn **Target tracking scaling policy**
      - Metric type: Chọn **Application Load Balancer request count per target**
      - Target group: Chọn target group mà chúng ta đã tạo (VD: **sharenote-tg**)
      - Target value: Nhập **30**
11. Chọn **Next**.
![Launch Template](../../../images/4/4_ScalingPolicy.png?width=90pc)
12. Ở trang **Add notifications**, chọn **Next**.
13. Ở trang **Add tags**, chọn **Next**.
14. Ở trang **Review**, chọn **Create Auto Scaling Group**

Quá trình khởi tạo Auto Scaling Group sẽ được thực hiện, Auto Scaling Group vừa được tạo sẽ hiển thị trong danh sách, và bạn có thể chọn vào nó để xem thông tin chi tiết. 

Auto Scaling Group sẽ triển khai các instance, chúng ta có thể theo dõi ở trang **Instance management**. Các instance có tình trạng **InService** là các instance đã sẵn sàng hoạt động.
![Launch Template](../../../images/4/4_InstanceManagement.png?width=90pc)