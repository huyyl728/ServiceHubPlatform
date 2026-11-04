# ServiceHubPlatform - Business Requirements

## 1. Project Overview

ServiceHubPlatform là nền tảng đa dịch vụ được xây dựng
bằng ASP.NET Core 10 MVC.

Hệ thống kết nối khách hàng với các cơ sở cung cấp
dịch vụ như nhà hàng, sân thể thao, salon và spa.

Dự án được phát triển theo kiến trúc Modular Monolith,
hướng tới khả năng bảo trì và mở rộng lâu dài.

## 2. Business Objectives

- Giúp khách hàng tìm kiếm dịch vụ thuận tiện.
- Hỗ trợ đặt lịch và đặt bàn trực tuyến.
- Cho phép chủ cơ sở quản lý dịch vụ và lịch đặt.
- Cung cấp chương trình ưu đãi và hội viên.
- Phát triển chức năng đặt món và giao hàng.
- Hỗ trợ quản trị và giám sát nền tảng.

## 3. Target Users

### 3.1 Customer
Khách hàng tìm kiếm, đặt dịch vụ và đánh giá.

### 3.2 Provider
Chủ cơ sở quản lý chi nhánh, dịch vụ và ưu đãi.

### 3.3 Staff
Nhân viên xử lý công việc theo quyền được cấp.

### 3.4 Admin
Quản trị viên kiểm duyệt và quản lý nền tảng.

## 4. Business Scope

Các nhóm chức năng dự kiến:

- Quản lý tài khoản và phân quyền.
- Quản lý cơ sở, chi nhánh và dịch vụ.
- Tìm kiếm và khám phá dịch vụ.
- Đặt lịch và đặt bàn.
- Hội viên và voucher.
- Đặt món và giao hàng.
- Thanh toán, đánh giá và thông báo.
- Dashboard quản trị.

## 5. Project Status

Giai đoạn 1: Đã hoàn thành khởi tạo dự án.

Giai đoạn 2: Đang phân tích nghiệp vụ và
thiết kế kiến trúc, cơ sở dữ liệu.

Các chức năng nghiệp vụ hiện vẫn đang được thiết kế.

## 6. Functional Requirements

FR-001: Hệ thống cho phép người dùng đăng ký,
đăng nhập và quản lý thông tin tài khoản.

FR-002: Chủ cơ sở có thể đăng ký cơ sở kinh doanh
và quản lý các chi nhánh được cấp quyền.

FR-003: Chủ cơ sở có thể tạo, cập nhật và quản lý
danh mục, thông tin và hình ảnh dịch vụ.

FR-004: Khách hàng có thể tìm kiếm và lọc dịch vụ
theo từ khóa, danh mục và các tiêu chí phù hợp.

FR-005: Hệ thống hiển thị gợi ý dịch vụ, địa điểm
nổi bật và các nội dung khám phá phù hợp.

FR-006: Khách hàng có thể đặt lịch hoặc đặt bàn,
xem trạng thái và thực hiện hủy theo quy định.

FR-007: Hệ thống hỗ trợ voucher, chương trình
hội viên và ưu đãi theo từng cơ sở.

FR-008: Khách hàng có thể chọn món, quản lý
giỏ hàng và tạo đơn giao hàng.

FR-009: Hệ thống ghi nhận giao dịch, hỗ trợ
thanh toán mô phỏng và lịch sử thanh toán.

FR-010: Khách hàng có thể đánh giá và lưu
dịch vụ vào danh sách yêu thích.

FR-011: Hệ thống hỗ trợ gửi và hiển thị
thông báo liên quan đến hoạt động người dùng.

FR-012: Quản trị viên có thể quản lý nền tảng
và xem thông tin thống kê.

## 7. Acceptance Criteria Example

Feature: FR-006 - Booking and Reservations

AC-006-01: Khách hàng chọn được ngày,
giờ và số lượng người hợp lệ.

AC-006-02: Hệ thống không xác nhận
đặt bàn khi không đủ sức chứa.

AC-006-03: Đặt bàn thành công được
ghi nhận trong cơ sở dữ liệu.

AC-006-04: Khách hàng có thể xem
trạng thái đặt bàn của mình.

## 8. Non-Functional Requirements

Các yêu cầu dưới đây là mục tiêu thiết kế ban đầu.
Các ngưỡng định lượng cần được kiểm chứng bằng
kiểm thử trong môi trường được xác định.

### NFR-001 - Performance

Hệ thống cần phản hồi nhanh đối với các thao tác
tìm kiếm và xem thông tin dịch vụ.

Mục tiêu sơ bộ: P95 thời gian phản hồi của API
tìm kiếm không vượt quá 2 giây với 50 người
dùng đồng thời.

Điều kiện kiểm thử, dữ liệu và phần cứng sẽ
được xác định trước khi đánh giá hiệu năng.

### NFR-002 - Security

Hệ thống phải xác thực người dùng và kiểm tra
quyền truy cập đối với chức năng được bảo vệ.

Mật khẩu phải được xử lý bằng cơ chế băm mật khẩu
an toàn, không lưu dưới dạng văn bản thuần.

Thông tin bí mật không được đưa vào GitHub.
Website công khai phải sử dụng HTTPS.

### NFR-003 - Data Consistency

Hệ thống phải đảm bảo tính nhất quán dữ liệu
khi nhiều người dùng thực hiện đặt dịch vụ
đồng thời.

Không được xác nhận vượt quá số chỗ còn trống.

Cần kiểm thử các tình huống đặt trùng hoặc
cạnh tranh tài nguyên.

### NFR-004 - Usability

Giao diện phải hỗ trợ desktop và mobile.

Các biểu mẫu cần có thông báo lỗi rõ ràng.
Người dùng phải nhận biết được kết quả thao tác.

### NFR-005 - Maintainability

Mã nguồn phải được phân chia trách nhiệm rõ ràng
theo kiến trúc đã thống nhất.

Domain không phụ thuộc vào Web, Application
hoặc Infrastructure.

Những nghiệp vụ quan trọng cần có kiểm thử tự động.

### NFR-006 - Observability

Hệ thống cần ghi nhận lỗi và các sự kiện quan trọng
để hỗ trợ giám sát, phân tích và xử lý sự cố.

Log không được làm lộ mật khẩu, token hoặc
thông tin bí mật.

### NFR-007 - Reliability and Recovery

Các giao dịch quan trọng phải có cơ chế xử lý lỗi
phù hợp để hạn chế trạng thái dữ liệu không nhất quán.

Trước khi triển khai chính thức, cần xây dựng
quy trình sao lưu và kiểm tra khả năng khôi phục
dữ liệu PostgreSQL.

## 9. Business Rules

Các quy tắc dưới đây là bản thiết kế ban đầu.
Chi tiết sẽ được hoàn thiện khi phân tích từng module.

### BR-001 - Business Approval

Cơ sở kinh doanh phải được quản trị viên phê duyệt
trước khi được công khai dịch vụ trên nền tảng.

### BR-002 - Business Data Access

Provider và Staff chỉ được quản lý dữ liệu của
cơ sở hoặc chi nhánh mà họ được cấp quyền.

### BR-003 - Valid Booking Time

Khách hàng chỉ có thể đặt dịch vụ tại những
thời điểm được cơ sở cho phép tiếp nhận.

### BR-004 - Booking Capacity

Hệ thống không được xác nhận đặt lịch hoặc đặt bàn
vượt quá khả năng phục vụ của cơ sở.

Quy tắc phải được đảm bảo ngay cả khi có
nhiều yêu cầu đặt đồng thời.

### BR-005 - Booking Status

Trạng thái đặt lịch chỉ được thay đổi theo
những chuyển đổi hợp lệ đã được quy định.

Không được thực hiện chuyển đổi trạng thái
trái với quy trình nghiệp vụ.

### BR-006 - Booking Cancellation

Việc hủy lịch phải tuân thủ chính sách hủy
được áp dụng cho dịch vụ hoặc cơ sở tương ứng.

### BR-007 - Voucher Eligibility

Voucher chỉ được áp dụng khi đáp ứng các
điều kiện về hiệu lực, đối tượng sử dụng
và giới hạn sử dụng.

### BR-008 - Business Membership

Quyền lợi hội viên chỉ được áp dụng tại
cơ sở tương ứng, trừ khi chương trình
quy định rõ phạm vi áp dụng khác.

### BR-009 - Order Validation

Đơn đặt món phải có các mục hàng hợp lệ.

Tổng tiền phải được xác định từ dữ liệu
giá và các khoản phí áp dụng của hệ thống.

### BR-010 - Review Eligibility

Người dùng chỉ được đánh giá khi có
giao dịch đủ điều kiện theo quy định
của nền tảng.

### BR-011 - Payment Consistency

Một giao dịch thanh toán phải được ghi
nhận với trạng thái nhất quán.

Hệ thống phải ngăn việc ghi nhận thành công
trùng lặp cho cùng một lần thanh toán.
