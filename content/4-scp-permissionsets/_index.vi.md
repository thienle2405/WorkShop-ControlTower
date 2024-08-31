+++
title = "Cấu hình SCP và Permission Set"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

Ở bước này, chúng ta sẽ Cấu hình SCP và Permission Set. Chúng ta sẽ cùng làm rõ hơn về hai khái niệm này 

- **Service Control Policies (SCP):**
  - **Vai trò:** SCPs định nghĩa những hành động nào được phép hoặc bị cấm trên các tài khoản AWS thuộc về một tổ chức trong AWS Organizations.
  - **Phạm vi áp dụng:** SCPs được áp dụng ở cấp độ tài khoản hoặc Organizational Unit (OU), và ảnh hưởng đến tất cả các vai trò, người dùng, và dịch vụ trong tài khoản đó.
  - **Chức năng:** SCPs không trực tiếp cấp quyền mà chỉ giới hạn hoặc cho phép các quyền đã được gán qua IAM roles, IAM policies, hoặc Permission Sets. SCPs sẽ chặn hoặc cho phép các hành động cụ thể bất kể quyền đó đến từ đâu.
- **Permission Sets:**
  - **Vai trò:** Permission Sets xác định các quyền cụ thể mà người dùng hoặc nhóm có thể thực hiện khi họ truy cập vào tài khoản AWS thông qua AWS IAM Identity Center (trước đây là SSO).
  - **Phạm vi áp dụng:** Permission Sets chỉ áp dụng cho người dùng hoặc nhóm được gán trong IAM Identity Center để truy cập vào tài khoản AWS.
  - **Chức năng:** Permission Sets gán các quyền chi tiết (như ReadOnlyAccess, AdministratorAccess, hoặc các quyền tùy chỉnh khác) cho người dùng để họ thực hiện các hành động trên tài khoản AWS.

**Nói tóm lại SCP định nghĩa tài khoản đó làm gì, còn Permission Sets định nghĩa user truy cập vào tài khoản aws có quyền làm gì. Nếu có cả 2 thì quyền cuối cùng sẽ là giao của SCP và Permission Sets**

Trong bài ta sẽ tạo ra ba Account AWS đại diện cho ba môi trường production, development, và testing. Hai tài khoản trong IAM Identity Center bao gồm dt07 (management) có quyền full quyền trong cả 3 môi trường. Tài khoản Duy Thien (được tạo sau) sẽ chỉ có full quyền ở môi trường development và chỉ có quyền đọc ở môi trường test, và không thể truy cập vào môi trường production.

#### Tạo Account AWS cho từng môi trường

Truy cập AWS Control Tower → Chọn Organization → Create resources

![Application Load Balancer](/images/4/4.1.png?width=90pc)

**Nhập thông tin chi tiết tài khoản:**
  - **Account email:** Nhập địa chỉ email để tạo tài khoản mới trong vùng hạ cánh (landing zone). Email này sẽ được sử dụng cho các thông báo và quản lý tài khoản.
  - **Display name:** Nhập tên hiển thị cho tài khoản. Tên này sẽ xuất hiện trong AWS Control Tower để dễ dàng nhận diện tài khoản. Trong ví dụ này, tên là "production".
  
**Cấu hình truy cập:**
  - **IAM Identity Center user email:** Nhập địa chỉ email cho người dùng IAM Identity Center. Đây là email mà người dùng sẽ sử dụng để đăng nhập vào IAM Identity Center và truy cập tài khoản AWS.
  - **IAM Identity Center user name:** Nhập tên người dùng cho IAM Identity Center. Tên này thường là tên và họ của người dùng sẽ được sử dụng để tạo người dùng trong IAM Identity Center.
  
**Chọn OU:** Ta sẽ thêm các môi trường vào SandBox Ou đã được tạo khi Set up landing zone.

**Hoàn tất và Tiếp tục:** Sau khi nhập đầy đủ thông tin, nhấp vào **Create** với quá trình tạo tài khoản.

![Application Load Balancer](/images/4/4.2.png?width=90pc)
![Application Load Balancer](/images/4/4.3.png?width=90pc)

Tương tự như môi trường development và môi trường test

![Application Load Balancer](/images/4/4.4.png?width=90pc)

#### Tạo SCPs

Trong AWS Control Tower, cấu hình Service Control Policies (SCPs) được thực hiện thông qua AWS Organizations, vì SCPs là một tính năng của AWS Organizations. 

Truy cập trực tiếp vào AWS Organizations từ AWS Management Console.
Trong **AWS Organizations**, chọn **Policies** từ thanh điều hướng bên trái → Chọn tab **Service Control Policies** (SCPs). Tại đây, bạn có thể tạo mới hoặc quản lý các SCP hiện có.

![Application Load Balancer](/images/4/4.5.png?width=90pc)

Do khi tạo AWS Control Tower sẽ được tạo sẵn một số SCPs

![Application Load Balancer](/images/4/4.6.png?width=90pc)

Ta có thể xem chi tiết bên trong các quyền dưới định dạng **JSON **

![Application Load Balancer](/images/4/4.7.png?width=90pc)

Các SCPs này có thể được gắn trên OU hoặc trên từng Account AWS, ở dây để thực hiện đúng yêu cầu, thì ta có thể gáng full access vào OU Sandbox, sau đó ta sẽ giới hạn quyền dựa vào **Permission Sets**, cũng có thể giới hạn quyền ngay tại SCPs, tùy vào yêu cầu bài toán mà có rất nhiều cách, bởi vì quyền cuối cùng sẽ là giao giữa **Permission Sets** và **SCPs**.

![Application Load Balancer](/images/4/4.8.png?width=90pc)

#### Tạo Group cho Account AWS và user của IAM Identity Center

Khi một user và một account cùng nằm trong một group trên IAM Identity Center (hoặc thông qua các cơ chế phân quyền khác trong AWS), user sẽ có quyền truy cập vào account đó dựa trên các permission sets (bộ quyền) đã được gán cho group.

Truy cập vào **IAM Identity Center**, bạn sẽ thấy có những group được tạo sẵn trong AWS Control Tower. Ấn vào **Create Group**

![Application Load Balancer](/images/4/4.9.png?width=90pc)

Bên cạnh đó AWS Control Tower cũng đã tạo sẵn cho chúng ta một vài **Permissions Sets**

Như yêu cầu thì ta sẽ tạo ra 2 group là Project Manager và Developer 

![Application Load Balancer](/images/4/4.10.png?width=90pc)

![Application Load Balancer](/images/4/4.11.png?width=90pc)

Tiếp theo ta sẽ gáng AWS Accounts cho Group **Project Manager**

![Application Load Balancer](/images/4/4.12.png?width=90pc)

![Application Load Balancer](/images/4/4.13.png?width=90pc)

Sau đó ta sẽ chọn Permission Sets ở đây là Full Access

![Application Load Balancer](/images/4/4.15.png?width=90pc)

Tiếp tục gáng gáng AWS Account cho Group **Developer**

![Application Load Balancer](/images/4/4.16.png?width=90pc)

![Application Load Balancer](/images/4/4.17.png?width=90pc)

Sau đó ta sẽ chọn Permission Sets ở đây là AWSPowerUserAccess tức là có quyền truy cập tất cả trừ **AWS Organizations**

![Application Load Balancer](/images/4/4.18.png?width=90pc)

![Application Load Balancer](/images/4/4.19.png?width=90pc)

Bây giờ ta sẽ giới hạn quyền truy cập ReadOnlyAccess vào trong môi trường testing của user Duy Thien 

![Application Load Balancer](/images/4/4.20.png?width=90pc)



