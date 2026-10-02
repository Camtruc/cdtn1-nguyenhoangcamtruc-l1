# SRS rút gọn – L1 Hồ sơ khách hàng & Phân khúc

**Track:** DA  
**Luồng:** L1 – Hồ sơ khách hàng & Phân khúc

## 1. Phạm vi
Nhân viên tìm kiếm, xem và cập nhật thông tin khách hàng, sau đó tính toán và gán khách hàng vào các phân khúc VIP, Thường xuyên, mới hoặc ngủ đông theo quy tắc, kết thúc khi thông tin phân khúc khách hàng được lưu thành công.

## 2. User Stories
| Mã | User Story | MoSCoW |
|---|---|---|
| US01 | Là Sales, tôi muốn xem phân khúc của khách hàng để tư vấn và chăm sóc phù hợp. | MUST |
| US02 | Là Marketing, tôi muốn tính tổng giá trị mua hàng của khách hàng để đánh giá giá trị khách hàng. | MUST |
| US03 | Là Marketing, tôi muốn tính số lần mua và thời gian từ lần mua gần nhất để đánh giá hành vi mua hàng. | MUST |
| US04 | Là Marketing, tôi muốn gán khách hàng vào VIP, Thường xuyên, Mới hoặc Ngủ đông theo quy tắc để phục vụ chương trình marketing. | MUST |
| US05 | Là Quản lý cửa hàng, tôi muốn xem số lượng khách hàng theo từng phân khúc để theo dõi cơ cấu khách hàng. | SHOULD |
| US06 | Là Quản lý cửa hàng, tôi muốn xem danh sách khách hàng theo phân khúc để lập kế hoạch chăm sóc. | SHOULD |
| US07 | Là Sales, tôi muốn tìm kiếm khách hàng theo thông tin định danh để tra cứu hồ sơ nhanh. | SHOULD |
| US08 | Là Sales, tôi muốn cập nhật thông tin khách hàng để hồ sơ được đầy đủ và chính xác. | COULD |

### Acceptance Criteria – MUST
**US01**
- Given khách hàng tồn tại và đã có phân khúc, When Sales xem hồ sơ, Then phân khúc được hiển thị.
- Given khách hàng tồn tại nhưng chưa có phân khúc, When Sales xem hồ sơ, Then hệ thống thông báo khách hàng chưa được phân khúc.

**US02**
- Given khách hàng có giao dịch hợp lệ, When Marketing tính tổng giá trị mua hàng, Then hệ thống trả về tổng giá trị.
- Given khách hàng không có giao dịch hợp lệ, When Marketing tính tổng, Then hệ thống trả về 0.

**US03**
- Given khách hàng có lịch sử mua hàng, When Marketing tính hành vi, Then hệ thống xác định số lần mua và thời gian từ lần mua gần nhất.
- Given khách hàng không có lịch sử mua hàng, When Marketing tính hành vi, Then hệ thống thông báo chưa đủ dữ liệu.

**US04**
- Given khách hàng có đủ dữ liệu, When Marketing thực hiện phân khúc, Then hệ thống áp dụng quy tắc được phê duyệt và gán một trong bốn phân khúc.
- Given khách hàng không đủ dữ liệu, When Marketing thực hiện phân khúc, Then hệ thống không gán phân khúc và thông báo thiếu dữ liệu.

## 3. Use Case
- UC01 – Tra cứu hồ sơ khách hàng
- UC02 – Xem phân khúc khách hàng
- UC03 – Cập nhật thông tin khách hàng
- UC04 – Tính tổng giá trị mua hàng
- UC05 – Tính chỉ số hành vi mua hàng
- UC06 – Gán phân khúc khách hàng
- UC07 – Xem thống kê phân khúc
- UC08 – Xem danh sách khách hàng theo phân khúc

### Đặc tả UC06 – Gán phân khúc khách hàng
**Actor:** Marketing  
**Tiền điều kiện:** Khách hàng tồn tại và có đủ dữ liệu cần thiết.  
**Hậu điều kiện:** Phân khúc của khách hàng được lưu thành công.

**Luồng chính:**
1. Marketing chọn chức năng gán phân khúc.
2. Hệ thống kiểm tra dữ liệu khách hàng.
3. Hệ thống tính các chỉ số cần thiết.
4. Hệ thống áp dụng quy tắc phân khúc đã được phê duyệt.
5. Hệ thống xác định phân khúc.
6. Hệ thống hiển thị kết quả.
7. Marketing xác nhận kết quả.
8. Hệ thống lưu phân khúc khách hàng.

**Ngoại lệ E1 – Thiếu dữ liệu:** Tại bước 2, nếu dữ liệu không đủ, hệ thống không thực hiện phân khúc, thông báo dữ liệu thiếu và kết thúc use case.

## 4. Functional Requirements
| Mã | Yêu cầu |
|---|---|
| FR01 | Hệ thống cho phép tìm kiếm/tra cứu hồ sơ khách hàng. |
| FR02 | Hệ thống tính tổng giá trị mua hàng của khách hàng. |
| FR03 | Hệ thống tính số lần mua và thời gian từ lần mua gần nhất. |
| FR04 | Hệ thống gán phân khúc theo quy tắc được phê duyệt. |
| FR05 | Hệ thống hiển thị phân khúc khách hàng. |
| FR06 | Hệ thống cho phép quản lý xem số lượng khách hàng theo phân khúc. |

## 5. Non-functional Requirements
| Mã | Yêu cầu/Ngưỡng |
|---|---|
| NFR01 | Tỷ lệ đầy đủ của các trường dữ liệu bắt buộc ≥ 95%. |
| NFR02 | Không có bản ghi trùng theo business key của khách hàng. |
| NFR03 | Kết quả phân khúc phải nhất quán với bộ quy tắc phân khúc đã được phê duyệt. |

## 6. Traceability
| FR | US | Use Case | MoSCoW |
|---|---|---|---|
| FR01 | US07 | UC01 | SHOULD |
| FR02 | US02 | UC04 | MUST |
| FR03 | US03 | UC05 | MUST |
| FR04 | US04 | UC06 | MUST |
| FR05 | US01 | UC02 | MUST |
| FR06 | US05 | UC07 | SHOULD |

## Track DA – Data Requirement Specification

### Nguồn dữ liệu
| Source system | Format | Tần suất cập nhật | Quy mô ước tính |
|---|---|---|---|
| Dữ liệu case study | CSV/nguồn được cung cấp | Chưa xác định từ tài liệu hiện có | Khoảng 10.000 bản ghi đơn hàng theo phiếu phạm vi |

### Data Dictionary
Chưa chốt tên cột, kiểu dữ liệu và missing rate vì chưa có dataset thực tế trong tài liệu hiện có. Không tự tạo các giá trị này.

### Quality Rules
- Completeness của trường bắt buộc ≥ 95%.
- Không trùng business key khách hàng.
- Dữ liệu dùng để phân khúc phải đủ theo quy tắc đã được phê duyệt.

### Câu hỏi phân tích
| Mã | Câu hỏi | Granularity | US |
|---|---|---|---|
| AQ01 | Tổng giá trị mua hàng của từng khách hàng là bao nhiêu? | Khách hàng | US02 |
| AQ02 | Khách hàng mua bao nhiêu lần và lần mua gần nhất cách hiện tại bao lâu? | Khách hàng | US03 |
| AQ03 | Khách hàng thuộc phân khúc nào theo quy tắc? | Khách hàng | US04 |
| AQ04 | Có bao nhiêu khách hàng trong mỗi phân khúc? | Phân khúc | US05 |
| AQ05 | Danh sách khách hàng trong từng phân khúc là gì? | Phân khúc/khách hàng | US06 |
