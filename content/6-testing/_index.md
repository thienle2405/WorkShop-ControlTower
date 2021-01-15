+++
title = "Testing results"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

**Contents:**
- [Testing Auto Scaling of deployed Share Note application](#testing-auto-scaling-of-deployed-share-note-application)

Trong bài thực hành này, chúng ta sẽ tiến hành tăng số lượng yêu cầu truy cập đến ứng dụng thông qua việc mở đồng loạt nhiều kết nối sử dụng công cụ [Webserver Stress Tool 8](https://www.paessler.com/tools/webstress)

#### Testing Auto Scaling of deployed Share Note application

1. Kiểm tra số lượng instance hiện có trong Auto Scaling Group là 1.

![Testing Result](../../../images/6/1.png?width=90pc)

2. Tiến hành tạo số lượng truy cập lớn đến Endpoint của Load Balancer.

![Testing Result](../../../images/6/2.png?width=90pc)

![Testing Result](../../../images/6/3.png?width=90pc)

3. Sau một khoảng thời gian, kiểm tra phản hồi của Auto Scaling Group. Ta thấy số lượng instance được tăng lên số lượng tối đa mà chúng ta thiết lập là 3.

![Testing Result](../../../images/6/4.png?width=90pc)

![Testing Result](../../../images/6/5.png?width=90pc)

4. Kiểm tra truy cập vào ứng dụng từ trình duyệt không bị gián đoạn.

![Testing Result](../../../images/6/6.png?width=90pc)

Chúc mừng bạn vừa hoàn thành bài thực hành Triển khai ứng dụng ShareNote với Auto Scaling Group và Elastic Load Balancer.