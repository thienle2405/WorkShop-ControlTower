+++
title = "Khởi tạo Load Balancer"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

**Nội dung:**
- [Tạo Load Balancer](#tạo-load-balancer)

Ở bước này, chúng ta sẽ triển khai Load Balancer điều phối các request từ người dùng đến các Share Note instance cho ứng dụng Share Note của chúng ta.

#### Tạo Load Balancer

Chúng ta bắt đầu khởi tạo Load Balancer như sau:
1. Truy cập vào **AWS Management Console**. Lựa chọn **Services** ở thanh điều hướng và tìm kiếm dịch vụ **EC2**.
2. Ở thanh điều hướng bên trái, chọn **Load Balancers**.
3. Ở trang danh sách Load Balancer, chọn **Create Load Balancer**.
4. Ở trang **Select load balancer type**, chọn **Create** ở mục **Application Load Balancer**.
5. Ở trang **Step 1: Configure Load Balancer**, thiết lập các thông số như sau:
  - Basic Configuration:
    - Name: Nhập tên của Load Balancer (VD: **sharenote-elb**)
    - Scheme: **internet-facing**
    - IP address type: **ipv4**
  - Availability Zones:
    - Availability Zones: Chọn hai AZ tương tự chúng ta đã chọn ở phần trước (VD: ap-northeast-1a và ap-northeast-1c)
6. Chọn **Next: Configure Security Settings**

![Elastic Load Balancer](../../../images/5/1.png?width=90pc)

7. Ở trang **Step 2: Configure Security Settings**, chọn **Next: Configure Security Groups**.
8. Ở trang **Step 3: Configure Security Groups**:
   - Assign a security group: Chọn **Select an existing security group**
     - Chọn Security Group mà bạn lựa chọn (VD: **sharenote-sg**)
9. Chọn **Next: Configure Routing**.

![Elastic Load Balancer](../../../images/5/2.png?width=90pc)

10. Ở trang **Step 4: Configure Routing**:
    - Target group:
      - Target group: Chọn **Existing target group**
      - Name: Lựa chọn target group mà chúng ta đã tạo ở bước trước đó (VD: **sharenote-tg**) (Khi chỉ có một target group, hệ thống sẽ tự động chọn nó)
11. Chọn **Next: Register Targets**

![Elastic Load Balancer](../../../images/5/3.png?width=90pc)

12. Ở trang **Step 5: Register Targets**, chọn **Next: Review**.
13. Chọn **Create**.

![Elastic Load Balancer](../../../images/5/4.png?width=90pc)

14. Trang tạo Load Balancer thành công sẽ hiển thị ra cho bạn.

Quá trình tạo Load Balancer sẽ mất khoảng 5-10 phút để hoàn thành. Bạn có thể kiểm tra sự thay đổi trạng thái từ **provisioning** sang **active** ở danh sách Load Balancer.

![Elastic Load Balancer](../../../images/5/5.png?width=90pc)

Hãy ghi chú lại **DNS name** của Load Balancer lại vì đây sẽ là địa chỉ chúng ta dùng để truy cập vào ứng dụng dược triển khai.

![Elastic Load Balancer](../../../images/5/6.png?width=90pc)

![Elastic Load Balancer](../../../images/5/7.png?width=90pc)

Đến đây, chúng ta đã hoàn thành việc triển khai ứng dụng Share Note với Auto Scaling Group và Elastic Load Balancer. Với mô hình này, bạn có thể triển khai ứng dụng của mình với tính sẵn sàng cao, dễ dàng mở rộng và cân bằng tải các yêu cầu từ người dùng.

Ở bước kế tiếp, chúng ta sẽ thử nghiệm việc mở rộng dựa trên tăng số lượng truy cập đến ứng dụng của chúng ta và xem phản hồi của Auto Scaling Group đối với sự gia tăng này.
