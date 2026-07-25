---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Đề xuất triển khai Smart Healthcare Appointment System trên AWS

### 1. Tóm tắt điều hành

Smart Healthcare Appointment System là một nền tảng được thiết kế nhằm hỗ trợ bệnh nhân đặt lịch khám, quản lý hồ sơ sức khỏe và kết nối với các cơ sở y tế một cách nhanh chóng, minh bạch và thuận tiện hơn. Mục tiêu của hệ thống không chỉ dừng lại ở việc xây dựng một website đặt lịch đơn thuần, mà còn hướng tới một nền tảng y tế số có cấu trúc rõ ràng, bảo mật cao và có khả năng mở rộng lâu dài để đáp ứng lưu lượng lớn trong các khung giờ cao điểm.

Trong thời gian thực tập, em tập trung chủ yếu vào phần backend và hạ tầng, đồng thời hỗ trợ kết nối giao diện người dùng với các thành phần xử lý bất đồng bộ và các dịch vụ AWS. Vì vậy, bản đề xuất này phản ánh đồng thời góc nhìn sản phẩm và tư duy kỹ thuật, đóng vai trò như cầu nối giữa một dự án học thuật và một nền tảng y tế đám mây có định hướng triển khai thực tế.

Một điểm quan trọng của hệ thống là không đi theo hướng kiến trúc nguyên khối truyền thống. Thay vào đó, hệ thống được thiết kế theo mô hình tách lớp rõ ràng giữa frontend, business logic, hàng đợi bất đồng bộ và tầng dữ liệu. Cách tiếp cận này giúp tăng độ sẵn sàng, cải thiện an toàn dữ liệu bệnh nhân và tạo nền tảng ổn định cho vận hành lâu dài.

### 2. Phát biểu bài toán

Trong môi trường y tế hiện nay, việc đặt lịch khám và quản lý hồ sơ bệnh án thường còn rời rạc hoặc vận hành thủ công, dẫn đến nhiều vấn đề:

- Bệnh nhân phải chờ đợi lâu tại quầy tiếp nhận hoặc gặp tình trạng nghẽn hệ thống trong giờ đăng ký cao điểm.
- Dữ liệu lịch hẹn và thông tin sức khỏe cá nhân có nguy cơ bị lộ nếu không được phân vùng và bảo vệ chặt chẽ.
- Hệ thống dễ bị nghẽn cổ chai khi lưu lượng tăng đột biến, gây ảnh hưởng trực tiếp đến hoạt động khám chữa bệnh.
- Khó đồng bộ trạng thái lịch hẹn giữa bệnh nhân, bác sĩ và các bộ phận khác nhau trong cơ sở y tế.

#### Các vấn đề hiện tại

Nếu hệ thống được xây dựng theo mô hình monolithic đơn giản, nơi mọi request đều được đưa trực tiếp tới một máy chủ backend duy nhất, hệ thống sẽ rất dễ quá tải khi số lượng người dùng đồng thời tăng cao. Ngoài ra, việc thiếu cơ chế xử lý bất đồng bộ hoặc thiếu phân vùng mạng an toàn cũng khiến khả năng mở rộng và mức độ bảo vệ dữ liệu y tế bị hạn chế.

Một vấn đề khác là nhiều hệ thống hiện nay chỉ giải quyết phần lưu trữ dữ liệu cơ bản, nhưng chưa tối ưu tốt về khả năng chịu tải, giám sát lỗi theo thời gian thực và tuân thủ các tiêu chuẩn bảo mật phù hợp với môi trường dữ liệu nhạy cảm.

#### Giải pháp đề xuất

Smart Healthcare Appointment System được đề xuất với cấu trúc như sau:

- Frontend cung cấp trải nghiệm tìm kiếm, đặt lịch, quản lý hồ sơ sức khỏe và tra cứu thông tin bác sĩ.
- Backend Node.js/Express xử lý business logic, xác thực, phân quyền và điều phối luồng lịch hẹn.
- PostgreSQL lưu trữ metadata của lịch hẹn, thông tin bệnh nhân, bác sĩ và trạng thái y tế.
- Amazon S3 lưu trữ hồ sơ y tế, kết quả xét nghiệm và hình ảnh khám chữa bệnh để giảm tải cho backend và phù hợp với mô hình object storage.
- Các dịch vụ mở rộng như CloudFront, SQS, CloudWatch và SNS được đưa vào để tăng hiệu năng, xử lý hàng đợi trong giờ cao điểm, giám sát hệ thống và tối ưu chi phí.

Trọng tâm của giải pháp là kiến trúc nhiều lớp kết hợp với cơ chế hàng đợi bất đồng bộ để xử lý các luồng đặt lịch cao điểm, trong khi backend tập trung vào metadata và business logic của hệ thống y tế. Kiến trúc này phù hợp với một nền tảng số có dữ liệu tăng liên tục và số lượng người dùng đồng thời lớn.

### 3. Kiến trúc giải pháp

Kiến trúc dưới đây mô tả định hướng triển khai Smart Healthcare Appointment System trên AWS, bao gồm lớp phân phối nội dung, lớp mạng VPC bảo mật, tầng ứng dụng, tầng dữ liệu và tầng giám sát vận hành:

![Smart Healthcare Appointment System Architecture](/images/2-Proposal/so-do.jpg)

#### Mô tả các thành phần chính

- **Amazon Route 53, Amazon CloudFront, AWS WAF và AWS Certificate Manager**: đóng vai trò lớp Global Edge Security & CDN, giúp phân phối nội dung tĩnh, quản lý domain, cấp phát SSL tự động và giảm thiểu các mối đe dọa web.
- **Internet Gateway và Application Load Balancer**: tiếp nhận request từ phía người dùng, đưa lưu lượng vào Public Subnet và phân phối về backend.
- **Amazon EC2 trong Private Subnet**: chạy backend để xử lý business logic, authentication và điều phối dữ liệu y tế.
- **Amazon RDS PostgreSQL Multi-AZ và Amazon ElastiCache for Redis**: lưu metadata lịch hẹn, thông tin bệnh nhân, tài khoản, trạng thái y tế và cache dữ liệu để tăng tốc độ truy vấn.
- **Amazon S3 (Upload)**: lưu hồ sơ bệnh án, kết quả xét nghiệm và ảnh y tế bằng cơ chế Presigned URL để client upload trực tiếp.
- **Event-Driven Execution Bus (SQS FIFO Queue, AWS Lambda, SNS & SES)**: xử lý bất đồng bộ các luồng đặt lịch cao điểm, gửi thông báo lịch hẹn và email xác nhận.
- **Amazon CloudWatch**: hỗ trợ logging, monitoring và cảnh báo tự động khi hệ thống xảy ra sự cố hoặc quá tải.

#### Ý nghĩa của kiến trúc đối với Smart Healthcare Appointment System

Kiến trúc này cho thấy Smart Healthcare Appointment System không chỉ là một ứng dụng web cơ bản, mà là một hệ thống có lớp bảo mật biên, lớp phân phối nội dung, phân vùng mạng VPC rõ ràng giữa Public/Private Subnet, cơ chế xử lý bất đồng bộ quy mô lớn và khả năng giám sát vận hành nghiêm ngặt. Đây là nền tảng quan trọng để đảm bảo an toàn dữ liệu y tế, khả năng chịu tải và tính mở rộng trong thực tế.

### 4. Triển khai kỹ thuật

Trong phạm vi thực tập, nhóm tập trung vào những hạng mục khả thi và phù hợp với codebase hiện có:

- Phát triển giao diện cho Home, Search, Appointment Booking, Patient Profile và Admin Dashboard.
- Thiết kế luồng đăng nhập mô phỏng và phân quyền cơ bản cho bệnh nhân, bác sĩ và quản trị viên.
- Chuẩn hóa cấu trúc metadata của lịch hẹn để phục vụ tìm kiếm, quản lý và điều phối trạng thái.
- Chuẩn bị luồng upload hồ sơ y tế và hình ảnh khám chữa bệnh theo mô hình presigned URL.
- Hỗ trợ kết nối backend Express với PostgreSQL và S3 ở mức phù hợp với bản demo.

Điều đó cũng có nghĩa là không phải mọi thành phần trong sơ đồ kiến trúc đều đã được triển khai hoàn chỉnh 100%. Những dịch vụ như SQS, CloudWatch và SNS ở thời điểm hiện tại đóng vai trò như định hướng mở rộng logic hơn là thành phần đã hoàn thiện toàn bộ. Việc trình bày rõ điều này giúp báo cáo trung thực với phạm vi thực tế của dự án.

### 5. Lộ trình và các mốc phát triển

#### Giai đoạn 1: Hoàn thiện sản phẩm cốt lõi

- Ổn định trải nghiệm tìm kiếm, đặt lịch, xem hồ sơ và điều hướng người dùng.
- Chuẩn hóa metadata và luồng duyệt lịch hẹn.
- Hoàn thiện admin dashboard và các thống kê cơ bản.

#### Giai đoạn 2: Tích hợp cloud thực tế

- Thiết lập kết nối ổn định giữa frontend, backend Express và PostgreSQL.
- Hoàn thiện cơ chế upload trực tiếp lên S3 bằng presigned URL cho hồ sơ y tế.
- Chuẩn hóa môi trường cấu hình và kiểm thử end-to-end.

#### Giai đoạn 3: Mở rộng hệ thống

- Bổ sung cơ chế background processing cho các tác vụ nặng hoặc bất đồng bộ.
- Tích hợp logging, monitoring và alerting theo hướng production-ready.
- Tối ưu chi phí bằng lifecycle policies và data tiering cho dữ liệu lưu trữ lâu dài.

### 6. Ước tính ngân sách

Bảng dưới đây mô tả chi phí ước tính hàng tháng của Smart Healthcare Appointment System, tổng hợp từ AWS Pricing Calculator và được xuất vào ngày 20/06/2026:

| Hạng mục | Chi phí ước tính hàng tháng (USD) | Ghi chú |
| --- | ---: | --- |
| RDS PostgreSQL Multi-AZ | 85.50 | Thành phần tốn chi phí lớn nhất do ưu tiên high availability |
| EC2 Server (t4g.micro x2) | 19.51 | Hai application server chạy trên hai AZ |
| Application Load Balancer | 18.98 | Phân phối lưu lượng và đóng vai trò entry point |
| NAT Instance (t4g.nano) | 4.64 | Hỗ trợ outbound traffic cho private subnets |
| ElastiCache for Redis | 7.50 | Cache dữ liệu và tối ưu hiệu năng truy vấn |
| Các thành phần khác (CloudWatch, SQS, SNS) | 5.07 | Chi phí cho monitoring, logging và xử lý bất đồng bộ |
| **Tổng** | **141.20** | Chi phí tham chiếu cho kiến trúc định hướng |

Mức chi phí trên phù hợp hơn với mô hình production-oriented hoặc một bản demo đầy đủ hơn là môi trường học tập tối giản. Trong giai đoạn thực tập hoặc thử nghiệm, nhóm có thể tối ưu chi phí bằng cách:

- Sử dụng single-AZ cho môi trường dev/test trước khi cần đến high availability.
- Tắt hoặc giảm cấu hình EC2 khi không cần chạy liên tục.
- Dùng lifecycle rules của S3 để chuyển dữ liệu ít truy cập sang Glacier.
- Chỉ bật detailed CloudWatch logs cho các thành phần thực sự cần theo dõi chặt.
- Sử dụng IAM Roles và S3 Gateway Endpoints để giảm rủi ro cấu hình sai thay vì hard-code access keys.

### 7. Đánh giá rủi ro

| Rủi ro | Tác động | Biện pháp giảm thiểu |
| --- | --- | --- |
| Sai lệch giữa frontend, backend và luồng presigned URL | Upload thất bại, hồ sơ bệnh án bị lệch trạng thái | Chuẩn hóa API contract, kiểm thử incremental và kiểm tra end-to-end trước demo |
| Metadata lịch hẹn hoặc thông tin bệnh nhân thiếu nhất quán | Tìm kiếm kém hiệu quả, quản lý lịch hẹn lộn xộn | Xác định metadata bắt buộc, thêm trạng thái review và thiết lập quy trình duyệt |
| Cấu hình quyền truy cập AWS không an toàn | Rò rỉ dữ liệu y tế hoặc leo thang đặc quyền trái phép | Áp dụng IAM Roles, Principle of Least Privilege và tránh hard-code keys |
| Chi phí tăng cao khi duy trì kiến trúc lớn cho môi trường dev | Lãng phí ngân sách khi hệ thống chưa có tải thực | Tách riêng dev/demo, scale down tài nguyên và theo dõi chi phí định kỳ |
| Thiếu khả năng quan sát khi hệ thống xảy ra lỗi | Khó phát hiện và xử lý sự cố đặt lịch kịp thời | Thiết lập metrics, logs, CloudWatch Alarms và SNS notifications |
| Phạm vi thực tập không đủ để hoàn thành toàn bộ kiến trúc | Báo cáo dễ bị hiểu là overclaim | Phân biệt rõ phần đã làm và phần định hướng mở rộng trong roadmap |

### 8. Kết quả kỳ vọng

Smart Healthcare Appointment System mang lại giá trị theo ba hướng chính:

- **Đối với người dùng cuối**: Bệnh nhân và bác sĩ có một nền tảng tập trung để đặt lịch và quản lý hồ sơ y tế nhanh chóng, trực quan và tin cậy hơn.
- **Đối với nhóm phát triển**: Dự án kết nối frontend, backend, tư duy metadata và thiết kế cloud architecture thành một sản phẩm hoàn chỉnh.
- **Đối với định hướng học tập**: Dự án đóng vai trò cầu nối giữa UI/UX, nghiệp vụ y tế thực tế và triển khai hệ thống AWS an toàn.

Ở góc độ cá nhân, bản đề xuất này phản ánh quá trình chuyển dịch từ tư duy chỉ tập trung vào giao diện sang tư duy kết hợp giữa trải nghiệm người dùng, luồng dữ liệu, bảo mật, chi phí và vận hành. Đó cũng là giá trị học tập lớn nhất mà Smart Healthcare Appointment System mang lại cho em trong kỳ thực tập này.
