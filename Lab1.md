# Lab 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## 1. Phân tích kiến trúc 
### 1.1 Đề xuất kiến trúc: Kiến trúc phù hợp với hệ thống "Payroll System" là kiến trúc mô hình Layer.
- Tầng giao diện
    + Tầng này cung cấp giao diện tương tác cho các tác nhân như Employee, Payroll Administrator, và Commissioned Employee. Giao diện có thể là web hoặc desktop, nơi người dùng đăng nhập, quản lý các tác vụ như tạo nhân viên, duy trì bảng lương, hoặc tạo báo cáo.
    + Các khía cạnh như bảo mật đăng nhập (Login) và truy cập giao diện đồ họa (GUI) để nhập dữ liệu là trọng tâm tại tầng này.
- Tầng dịch vụ
    + Đây là nơi xử lý tất cả logic nghiệp vụ như duy trì dữ liệu nhân viên, xử lý bảng lương, quản lý đơn mua hàng (Purchase Order) và tạo các báo cáo hành chính.
    + Mỗi tác vụ như "Maintain Employee Info" hay "Run Payroll" sẽ có các dịch vụ riêng được triển khai tại tầng này. Framework Java Spring có thể được sử dụng để phát triển tầng này, trong đó các dịch vụ RESTful có thể xử lý các yêu cầu từ giao diện người dùng.
    + Kiến trúc này cho phép dễ dàng triển khai logic xử lý đặc thù cho các tác vụ khác nhau mà không làm ảnh hưởng đến các tầng khác.
- Tầng dữ liệu
    + Dữ liệu của hệ thống, như bảng lương, thông tin nhân viên và các báo cáo, sẽ được lưu trữ trong cơ sở dữ liệu. Trong trường hợp này, SQL (MySQL, chẳng hạn) có thể được sử dụng với Wampserver mà bạn đang dùng.
    + Dữ liệu cần được truy xuất an toàn và chính xác cho các chức năng như quản lý và lưu trữ thông tin nhân viên, bảng lương và đơn mua hàng.
### 1.2 Lý do lựa chọn kiến trúc:
- Phân tách rõ ràng giữa các tầng: Giao diện, logic nghiệp vụ, và dữ liệu được phân chia rõ ràng, giúp dễ dàng duy trì và mở rộng hệ thống.
- Tính bảo mật: Đảm bảo chỉ nhân viên được phép mới có thể xem và chỉnh sửa thông tin của mình.
- Tích hợp dễ dàng với các hệ thống bên ngoài: Hỗ trợ tương tác với DB2 database mà không cần thay đổi logic nghiệp vụ.
### 1.3 Biểu đồ Package mô tả kiến trúc
![Diagram](https://www.planttext.com/api/plantuml/png/Z5HBJiCm4Dtt55PMiEY60w2cQeKgKRLguG23CnHJnud63Y92d8m5H-8AsFaOsxI8ICbYvisRDsyq-Vhud6a3P9fIJchWHpWWoxQ46fK18oh5Rg55ojZRX34kGMksB6jPjOZtgoxedZrAv6OBRMdBBYw7w58Pf3jH8WSgkkYxVJsFXLCbPLwKGWLSQn2sjL1ZcvLwh3pbhb53cG_Te482WpkiAp936_i9P4wdronhDEgCZNBsI2-2urdSCCiFB54RGrtcFz1UuuYqChtbULrBmSyudeZsLfMWRF6V3WT3-BAQAevQX-lg78lMaXPnaBoHrkVKVufN4Wc8vlLKXs5Ze_Ffvj9ndO5ZR95lUeV3mHnW9FE0S8ZVW5XPcWytim03BEVEiVEtq9F6smfZsuRu4sZSK84K9QXwjgUpxZRfPkgJReGJcKxeOdxbD3rOkaZeyjMUcmB9zgqsMEfGvnpKiGy7dOMxpo5gYKvu5fIToCOCCrI5-ujy0m00__y30000).
## 2. Cơ chế phân tích 
### Danh sách cơ chế
 1. Cơ chế tính lương: Tính toán lương dựa trên số giờ làm, mức lương cố định, và hoa hồng (nếu có).
 2. Cơ chế quản lý thời gian làm việc: Cho phép ghi nhận thời gian làm việc theo từng dự án.
 3. Cơ chế bảo mật: Đảm bảo quyền truy cập và chỉnh sửa thông tin của nhân viên.
 4. Cơ chế tích hợp với hệ thống DB2: Truy cập dữ liệu từ DB2 nhưng không cập nhật.
 5. Cơ chế thanh toán tự động: Tự động thanh toán vào thứ Sáu hàng tuần và ngày làm việc cuối cùng của tháng.
## 3. Phân tích ca sử dụng "Select Payment"
### 3.1 Các lớp phân tích
1. Employee: Đại diện cho nhân viên, chứa thông tin về nhân viên và phương thức thanh toán.
2. PaymentService: Xử lý yêu cầu thanh toán của nhân viên và liên kết với EmployeeDAO để cập nhật thông tin.
### 3.2. Biểu đồ Sequence cho "Select Payment"
![Diagram](https://www.planttext.com/api/plantuml/png/R9112i8m44NtESNGbIvwWIwaeYww40Nf0OPqj84sYUbKwDbSU2IlO59IjEfgXl__F3xpl3_oZj5ntpO29Hi7kzOsPY0IrijAAekQ8PdKiaW0EoYBkNt4eIND9t8t9McCnFq_Phi-Z24_XPX4I5SUdFdBXYH3P8go24R4PU3esbF7cnhrXM9cJroRQh4KCHKEF3g3tbR8FoblGVh9b4QVbMkHbT5lHgmpCqCPhq-LlzoST1K--G800F__0m00).
### 3.3. Thuộc tính và quan hệ
- Employee: Bao gồm name, address, paymentMethod.
- PaymentService: Quan hệ với EmployeeDAO để cập nhật thông tin thanh toán.
## 4. Phân tích ca sử dụng "Maintain Timecard"
### 4.1. Các lớp phân tích
1. Employee: Đại diện cho nhân viên và có thể ghi nhận thời gian làm việc của họ.
2. Timecard: Ghi nhận thời gian làm việc của nhân viên, bao gồm ngày và số giờ làm việc.
3. TimecardService: Xử lý việc ghi nhận và lưu trữ thời gian làm việc của nhân viên.
4. TimecardDAO: Lưu trữ các thông tin về timecard trong cơ sở dữ liệu.
### 4.2. Biểu đồ Sequence cho "Maintain Timecard"
![Diagram](https://www.planttext.com/api/plantuml/png/R9112i8m44NtESNGbIvwWIwaeYww40Nf0OPqj84sYUbKwDbSU2IlO59IjEfgXl__F3xpl3_oZj5ntpO29Hi7kzOsPY0IrijAAekQ8PdKiaW0EoYBkNt4eIND9t8t9McCnFq_Phi-Z24_XPX4I5SUdFdBXYH3P8go24R4PU3esbF7cnhrXM9cJroRQh4KCHKEF3g3tbR8FoblGVh9b4QVbMkHbT5lHgmpCqCPhq-LlzoST1K--G800F__0m00).
### 4.3. Thuộc tính và quan hệ
- Employee: Quan hệ với Timecard.
- Timecard: Bao gồm date, hoursWorked.
- TimecardService: Quan hệ với TimecardDAO để lưu trữ thời gian làm việc.
## 5. Hợp nhất kết quả phân tích
Các phân tích ca sử dụng "Select Payment" và "Maintain Timecard" cung cấp các thông tin cần thiết về quy trình ghi nhận thời gian và lựa chọn thanh toán. Hai chức năng này sẽ kết hợp với nhau và các cơ chế khác để tạo ra một hệ thống toàn diện.

Hệ thống sẽ đảm bảo:
- Bảo mật cho thông tin nhân viên.
- Chính xác trong tính toán lương.
- Hiệu quả trong việc tự động hóa quy trình thanh toán.
