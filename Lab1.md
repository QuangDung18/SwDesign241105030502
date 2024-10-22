# Lab 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## 1. Phân tích kiến trúc 
### 1.a Đề xuất kiến trúc: Kiến trúc phù hợp với hệ thống "Payroll System" là kiến trúc mô hình Model-View-Controler.
- Wiew
    + Tầng này cung cấp giao diện tương tác cho các tác nhân như Employee, Payroll Administrator, và Commissioned Employee. Giao diện có thể là web hoặc desktop, nơi người dùng đăng nhập, quản lý các tác vụ như tạo nhân viên, duy trì bảng lương, hoặc tạo báo cáo.
    + Các khía cạnh như bảo mật đăng nhập (Login) và truy cập giao diện đồ họa (GUI) để nhập dữ liệu là trọng tâm tại tầng này.
- Controler
    + Đây là nơi xử lý tất cả logic nghiệp vụ như duy trì dữ liệu nhân viên, xử lý bảng lương, quản lý đơn mua hàng (Purchase Order) và tạo các báo cáo hành chính.
    + Mỗi tác vụ như "Maintain Employee Info" hay "Run Payroll" sẽ có các dịch vụ riêng được triển khai tại tầng này. Framework Java Spring có thể được sử dụng để phát triển tầng này, trong đó các dịch vụ RESTful có thể xử lý các yêu cầu từ giao diện người dùng.
    + Kiến trúc này cho phép dễ dàng triển khai logic xử lý đặc thù cho các tác vụ khác nhau mà không làm ảnh hưởng đến các tầng khác.
- Model
    + Dữ liệu của hệ thống, như bảng lương, thông tin nhân viên và các báo cáo, sẽ được lưu trữ trong cơ sở dữ liệu. Trong trường hợp này, SQL (MySQL, chẳng hạn) có thể được sử dụng với Wampserver mà bạn đang dùng.
    + Dữ liệu cần được truy xuất an toàn và chính xác cho các chức năng như quản lý và lưu trữ thông tin nhân viên, bảng lương và đơn mua hàng.
### 1.b Vẽ biểu đồ package mô tả kiến trúc:
