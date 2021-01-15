+++
title = "Deploy ShareNote Application on Auto Scaling Group"
date = 2020
weight = 1
chapter = false
+++

# Deploy ShareNote Application on Auto Scaling Group

Ở bài thực hành này, chúng ta sẽ tiến hành việc triển khai ứng dụng với Auto Scaling Group nhằm đảm bảo khả năng co dãn của ứng dụng đó theo nhu cầu của người truy cập.
Thêm vào đó, chúng ta cũng sẽ triển khai Elastic Load Balancer nhằm cân bằng tải và điều phối các yêu cầu truy cập từ phía người dùng đến Application Tier của chúng ta.

Hãy chắc chắn rằng bạn đã xem qua tài liệu [Triển khai Ứng dụng ShareNote trên Máy ảo Windows/Ubuntu]() và nắm được cách triển khai ứng dụng trên máy ảo. Chúng ta sẽ cần sử dụng máy ảo được triển khai Share Note cho việc triển khai đồng loạt và mở rộng trong Auto Scaling Group.