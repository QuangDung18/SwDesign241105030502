# Lab 2: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## 1. Phân tích ca sử dụng "Create Employee"
### 1.1. Các lớp phân tích
1. Boundary: EmployeeUI – Giao diện cho phép người dùng nhập thông tin để tạo nhân viên mới.
2. Control: EmployeeService – Điều khiển quá trình tạo nhân viên, xác nhận dữ liệu và liên lạc với lớp lưu trữ.
3. Entity: Employee – Lưu trữ các thuộc tính của nhân viên như name, address, position, và paymentMethod.
### 1.2. Biểu đồ Sequence cho "Create Employee"
### 1.3. Thuộc tính và quan hệ
## 2. Phân tích ca sử dụng "Maintain Purchase Order"
### 2.1. Các lớp phân tích
1. Boundary: PurchaseOrderUI – Giao diện cho phép người dùng quản lý đơn mua hàng.
2. Control: PurchaseOrderService – Xử lý logic nghiệp vụ liên quan đến duy trì đơn hàng như thêm mới, sửa, hoặc xóa đơn hàng.
3. Entity: PurchaseOrder – Lưu trữ thông tin về đơn hàng như orderID, productDetails, quantity, và orderDate.
### 2.2. Biểu đồ Sequence cho "Maintain Purchase Order"
### 2.3. Thuộc tính và quan hệ
## 3. Phân tích ca sử dụng "Create Administrative Report"
### 3.1. Các lớp phân tích
1. Boundary: ReportUI – Giao diện cho phép người dùng tạo báo cáo hành chính.
2. Control: ReportService – Điều khiển việc tổng hợp dữ liệu từ nhiều nguồn và tạo báo cáo.
3. Entity: Report – Lưu trữ các thuộc tính của báo cáo như reportID, reportDate, và reportDetails.
### 3.2. Biểu đồ Sequence cho "Create Administrative Report"
### 3.3. Thuộc tính và quan hệ
