# ServiceHubPlatform - Use Cases

## 1. Purpose

Tài liệu mô tả các tương tác giữa Actor
và hệ thống ServiceHubPlatform.

Use Cases được xây dựng dựa trên tài liệu
01-business-requirements.md.

## 2. UC-001 - Submit Table Reservation

### 2.1 General Information

Use Case ID: UC-001

Name: Gửi yêu cầu đặt bàn

Primary Actor: Customer

Related Requirement: FR-006

Related Business Rules:
BR-003, BR-004, BR-005

Related NFR:
NFR-003

### 2.2 Preconditions

- Khách hàng đã đăng nhập.
- Nhà hàng đang hoạt động và nhận đặt bàn.
- Nhà hàng đã cấu hình thời gian tiếp nhận.

### 2.3 Trigger

Khách hàng chọn chức năng đặt bàn
tại trang thông tin nhà hàng.

### 2.4 Main Flow

1. Khách hàng mở trang nhà hàng.
2. Hệ thống hiển thị thông tin đặt bàn.
3. Khách hàng chọn ngày và giờ.
4. Khách hàng nhập số lượng người.
5. Khách hàng gửi yêu cầu đặt bàn.
6. Hệ thống kiểm tra dữ liệu hợp lệ.
7. Hệ thống kiểm tra điều kiện tiếp nhận.
8. Hệ thống lưu yêu cầu với trạng thái Pending.
9. Hệ thống thông báo đã tiếp nhận yêu cầu.

### 2.5 Alternative Flows

AF-001 - Invalid Booking Time

Nếu thời gian không hợp lệ,
hệ thống từ chối và thông báo lỗi.

AF-002 - Invalid Party Size

Nếu số người không hợp lệ,
hệ thống yêu cầu nhập lại.

AF-003 - No Available Capacity

Nếu không còn khả năng tiếp nhận,
hệ thống không xác nhận chỗ
và thông báo cho khách hàng.

AF-004 - Saving Failure

Nếu lưu yêu cầu thất bại,
hệ thống thông báo lỗi và không
báo rằng yêu cầu đã được ghi nhận.

### 2.6 Postconditions

Success:

- Yêu cầu đặt bàn đã được lưu.
- Trạng thái ban đầu là Pending.
- Khách hàng có thể xem yêu cầu.

Failure:

- Không có yêu cầu đặt bàn hợp lệ
  mới được ghi nhận.

### 2.7 Design Notes

Pending không đồng nghĩa Confirmed.

Việc xác nhận giữ chỗ cần kiểm tra
sức chứa tại thời điểm xác nhận.

Cơ chế kiểm soát đồng thời và chính sách
xác nhận sẽ được thiết kế chi tiết
trong Giai đoạn 7.

## 3. Use Case Index (Danh mục Use Case cần thêm )(Đã xong)

UC-002: Xác nhận hoặc từ chối đặt bàn.

UC-003: Hủy yêu cầu đặt bàn.

UC-004: Tìm kiếm dịch vụ.

UC-005: Quản lý dịch vụ của cơ sở.

## 4. UC-002 - Confirm or Reject Reservation

### 4.1 General Information

Use Case ID: UC-002

Name: Xác nhận hoặc từ chối đặt bàn

Primary Actor: Provider hoặc Staff được phân quyền

Related Requirement: FR-006

Related Business Rules:
BR-002, BR-004, BR-005

Related NFR: NFR-003

### 4.2 Preconditions

- Actor đã đăng nhập.
- Actor có quyền xử lý đặt bàn tại cơ sở.
- Yêu cầu đặt bàn có trạng thái Pending.

### 4.3 Trigger

Provider hoặc Staff mở yêu cầu đặt bàn
đang chờ xử lý và chọn hành động xử lý.

### 4.4 Main Flow - Confirmation

1. Actor mở danh sách đặt bàn.
2. Hệ thống hiển thị yêu cầu Pending.
3. Actor chọn yêu cầu cần xử lý.
4. Actor chọn xác nhận đặt bàn.
5. Hệ thống kiểm tra quyền truy cập.
6. Hệ thống kiểm tra trạng thái hiện tại.
7. Hệ thống kiểm tra khả năng tiếp nhận.
8. Hệ thống ghi nhận xác nhận an toàn.
9. Trạng thái chuyển thành Confirmed.
10. Hệ thống thông báo kết quả.

### 4.5 Alternative Flows

AF-001 - Reject Reservation

Actor chọn từ chối yêu cầu Pending.
Hệ thống kiểm tra quyền và trạng thái.
Nếu hợp lệ, hệ thống ghi nhận Rejected.

AF-002 - Insufficient Capacity

Nếu không đủ khả năng tiếp nhận,
hệ thống không xác nhận yêu cầu.
Yêu cầu giữ trạng thái Pending để
nhân viên xử lý theo quy trình.

AF-003 - Unauthorized Actor

Nếu Actor không có quyền,
hệ thống từ chối thao tác.

AF-004 - Invalid Status

Nếu yêu cầu không còn ở trạng thái
Pending, hệ thống từ chối xử lý.

AF-005 - Concurrent Confirmation

Nếu nhiều yêu cầu cạnh tranh
cùng một tài nguyên hoặc khung giờ,
hệ thống phải bảo đảm không xác nhận
vượt quá khả năng tiếp nhận.

### 4.6 Postconditions

Confirmation Success:

- Trạng thái là Confirmed.
- Khả năng tiếp nhận được ghi nhận
  nhất quán với đặt bàn đã xác nhận.

Rejection Success:

- Trạng thái là Rejected.

Failure:

- Không có xác nhận không hợp lệ
  được ghi nhận.

### 4.7 Design Notes

Các trạng thái Pending, Confirmed,
Rejected là thiết kế ban đầu.

Cần áp dụng cơ chế kiểm soát đồng thời
và giao dịch phù hợp khi xác nhận.

Chi tiết sẽ được triển khai ở
Giai đoạn 7 - Booking and Reservations.

## 5. UC-003 - Cancel Reservation

### 5.1 General Information

Use Case ID: UC-003

Name: Hủy yêu cầu đặt bàn

Primary Actor: Customer

Related Requirement: FR-006

Related Business Rules: BR-005, BR-006

Related NFR: NFR-002, NFR-003

### 5.2 Preconditions

- Khách hàng đã đăng nhập.
- Yêu cầu đặt bàn thuộc khách hàng.
- Trạng thái hiện tại cho phép hủy.
- Chính sách hủy cho phép thực hiện.

### 5.3 Trigger

Khách hàng chọn chức năng hủy
tại trang chi tiết đặt bàn.

### 5.4 Main Flow

1. Khách hàng mở lịch sử đặt bàn.
2. Hệ thống hiển thị thông tin đặt bàn.
3. Khách hàng chọn hủy đặt bàn.
4. Hệ thống hiển thị thông tin xác nhận hủy.
5. Khách hàng xác nhận thao tác.
6. Hệ thống kiểm tra quyền sở hữu đặt bàn.
7. Hệ thống kiểm tra trạng thái hiện tại.
8. Hệ thống kiểm tra chính sách hủy.
9. Hệ thống thực hiện hủy và cập nhật
   sức chứa đã giữ nếu cần.
10. Trạng thái được chuyển thành Cancelled.
11. Hệ thống thông báo hủy thành công.

### 5.5 Alternative Flows

AF-001 - Unauthorized Cancellation

Nếu đặt bàn không thuộc khách hàng,
hệ thống từ chối thao tác.

AF-002 - Invalid Booking Status

Nếu trạng thái không cho phép hủy,
hệ thống từ chối và thông báo lý do.

AF-003 - Cancellation Policy Violation

Nếu không đáp ứng chính sách hủy,
hệ thống từ chối yêu cầu.

AF-004 - Concurrent Modification

Nếu đặt bàn đã bị thay đổi bởi
một thao tác khác, hệ thống phải
kiểm tra lại điều kiện trước khi hủy.

AF-005 - Database Failure

Nếu lưu thay đổi thất bại,
hệ thống không được thông báo
rằng đặt bàn đã hủy thành công.

### 5.6 Postconditions

Success:

- Trạng thái đặt bàn là Cancelled.
- Lịch sử đặt bàn vẫn được lưu.
- Sức chứa đã giữ được giải phóng
  nếu đặt bàn trước đó chiếm sức chứa.
- Dữ liệu liên quan phải nhất quán.

Failure:

- Không ghi nhận thay đổi hủy
  không hợp lệ.

### 5.7 Design Notes

Không xóa vật lý bản ghi đặt bàn
khi khách hàng thực hiện hủy.

Chính sách hủy và các trạng thái
hợp lệ sẽ được hoàn thiện trong
Giai đoạn 7 - Booking and Reservations.

Cơ chế kiểm soát đồng thời phải
bảo vệ tính nhất quán của dữ liệu.

## 6. UC-004 - Search Services

### 6.1 General Information

Use Case ID: UC-004

Name: Tìm kiếm dịch vụ

Primary Actor: Visitor hoặc Customer

Related Requirements: FR-004, FR-005

Related Business Rules: BR-001

Related NFR: NFR-001

### 6.2 Preconditions

- Hệ thống tìm kiếm đang hoạt động.
- Các dịch vụ công khai đã được cấu hình.
- Người dùng không bắt buộc đăng nhập.

### 6.3 Trigger

Người dùng nhập từ khóa hoặc chọn
một danh mục dịch vụ để tìm kiếm.

### 6.4 Main Flow

1. Người dùng mở trang tìm kiếm.
2. Hệ thống hiển thị ô tìm kiếm và bộ lọc.
3. Người dùng nhập từ khóa.
4. Người dùng gửi yêu cầu tìm kiếm.
5. Hệ thống kiểm tra dữ liệu đầu vào.
6. Hệ thống xác định các kết quả phù hợp
   dựa trên thông tin và danh mục dịch vụ.
7. Hệ thống chỉ lấy các dịch vụ
   được phép hiển thị công khai.
8. Hệ thống sắp xếp và hiển thị kết quả.
9. Người dùng chọn dịch vụ để xem chi tiết.

### 6.5 Alternative Flows

AF-001 - No Search Results

Nếu không tìm thấy kết quả phù hợp,
hệ thống hiển thị thông báo
không có kết quả tìm kiếm.

AF-002 - Invalid Search Input

Nếu dữ liệu tìm kiếm không hợp lệ,
hệ thống yêu cầu điều chỉnh.

AF-003 - Search With Filters

Người dùng chọn danh mục hoặc
các tiêu chí lọc phù hợp.

Hệ thống cập nhật kết quả dựa trên
các điều kiện tìm kiếm đã chọn.

AF-004 - Search Suggestions

Khi người dùng nhập từ khóa,
hệ thống có thể hiển thị gợi ý
liên quan nếu chức năng được hỗ trợ.

AF-005 - Unavailable Services

Dịch vụ chưa được phép công khai
không xuất hiện trong kết quả công khai.

AF-006 - System Error

Nếu xảy ra lỗi xử lý tìm kiếm,
hệ thống hiển thị thông báo phù hợp
và không làm lộ thông tin nhạy cảm.

### 6.6 Postconditions

Success:

- Người dùng xem được kết quả phù hợp.
- Người dùng có thể truy cập trang chi tiết.

No Results:

- Hệ thống hiển thị danh sách rỗng
  và thông báo không có kết quả.

Failure:

- Hệ thống không hiển thị dữ liệu
  nội bộ không được phép công khai.

### 6.7 Design Notes

Chức năng tìm kiếm cần hỗ trợ
các cách diễn đạt linh hoạt.

Không bắt buộc tên dịch vụ phải
khớp hoàn toàn với từ khóa.

Cần xem xét hiệu năng khi dữ liệu
và số lượng người dùng tăng lên.

Thuật toán tìm kiếm và xếp hạng
sẽ được thiết kế trong Giai đoạn 6.

## 7. UC-005 - Manage Business Services

### 7.1 General Information

Use Case ID: UC-005

Name: Quản lý dịch vụ của cơ sở

Primary Actor: Provider

Supporting Actor: Staff được phân quyền

Related Requirements: FR-002, FR-003

Related Business Rules: BR-001, BR-002

Related NFR: NFR-002, NFR-005

### 7.2 Preconditions

- Actor đã đăng nhập.
- Actor có quyền quản lý cơ sở tương ứng.
- Cơ sở đã được đăng ký trong hệ thống.
- Cơ sở có thể tạo bản nháp dịch vụ.
- Chỉ cơ sở đủ điều kiện mới được
  công khai dịch vụ.

### 7.3 Trigger

Actor chọn chức năng quản lý dịch vụ
trong dashboard của cơ sở.

### 7.4 Main Flow - Create Service

1. Actor mở trang quản lý dịch vụ.
2. Hệ thống hiển thị danh sách dịch vụ.
3. Actor chọn thêm dịch vụ mới.
4. Hệ thống hiển thị biểu mẫu.
5. Actor nhập tên, mô tả và giá dịch vụ.
6. Actor chọn danh mục phù hợp.
7. Actor có thể tải ảnh dịch vụ lên.
8. Actor gửi yêu cầu lưu.
9. Hệ thống kiểm tra quyền truy cập.
10. Hệ thống kiểm tra dữ liệu đầu vào.
11. Hệ thống tạo dịch vụ.
12. Hệ thống thông báo kết quả.

### 7.5 Alternative Flows

AF-001 - Update Service

Actor chọn dịch vụ được phép quản lý.

Hệ thống hiển thị thông tin hiện tại.

Actor cập nhật thông tin và lưu lại.

Hệ thống kiểm tra quyền, dữ liệu
và ghi nhận thay đổi hợp lệ.

AF-002 - Deactivate Service

Actor chọn ngừng cung cấp dịch vụ.

Hệ thống kiểm tra điều kiện
và cập nhật trạng thái phù hợp.

Dữ liệu lịch sử cần thiết được giữ lại.

AF-003 - Invalid Input

Nếu dữ liệu đầu vào không hợp lệ,
hệ thống hiển thị thông báo lỗi.

AF-004 - Unauthorized Access

Nếu Actor không có quyền,
hệ thống từ chối thao tác.

AF-005 - Business Not Approved

Nếu cơ sở chưa được phê duyệt,
hệ thống không cho phép công khai
dịch vụ của cơ sở đó.

AF-006 - Invalid Image Upload

Nếu ảnh không đáp ứng yêu cầu
về định dạng hoặc dung lượng,
hệ thống từ chối tải lên.

AF-007 - Saving Failure

Nếu lưu dữ liệu thất bại,
hệ thống thông báo lỗi và không
báo rằng thao tác đã thành công.

### 7.6 Postconditions

Success:

- Dịch vụ được tạo hoặc cập nhật.
- Dữ liệu thuộc đúng phạm vi cơ sở.
- Trạng thái hiển thị tuân thủ
  điều kiện phê duyệt.
- Thông tin dịch vụ được lưu hợp lệ.

Failure:

- Không có thay đổi trái phép
  hoặc không hợp lệ được ghi nhận.

### 7.7 Design Notes

ServiceHubPlatform hỗ trợ nhiều cơ sở
và nhiều chi nhánh.

Một dịch vụ có thể cần được cấu hình
khác nhau tại các chi nhánh.

Cần xác định rõ quyền quản lý
ở cấp cơ sở và cấp chi nhánh.

Ảnh phải được quản lý theo từng
dịch vụ, không dùng chung một
ảnh cho toàn bộ dịch vụ.

Cấu trúc Domain và quan hệ database
sẽ được thiết kế trong Giai đoạn 2.

CRUD và quản lý upload sẽ được
triển khai trong Giai đoạn 5.

## 8. Requirements Traceability Matrix

Bảng liên kết các Use Case đã phân tích
với yêu cầu chức năng, phi chức năng
và quy tắc nghiệp vụ.

| Use Case | Functional Requirements | Business Rules | Non-Functional Requirements |
|---|---|---|---|
| UC-001 | FR-006 | BR-003, BR-004, BR-005 | NFR-003 |
| UC-002 | FR-006 | BR-002, BR-004, BR-005 | NFR-003 |
| UC-003 | FR-006 | BR-005, BR-006 | NFR-002, NFR-003 |
| UC-004 | FR-004, FR-005 | BR-001 | NFR-001 |
| UC-005 | FR-002, FR-003 | BR-001, BR-002 | NFR-002, NFR-005 |

### Traceability Notes

- Đây là bảng truy vết ban đầu.
- Chưa phải toàn bộ Use Case của hệ thống.
- Các mã yêu cầu tham chiếu đến tài liệu
  01-business-requirements.md.
- Bảng sẽ được cập nhật khi nghiệp vụ thay đổi.
- Những Use Case mới sẽ được bổ sung
  trong các giai đoạn phát triển tương ứng.
