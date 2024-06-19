# QUẢN LÝ HỆ THỐNG TUYẾN XE BUÝT
- Tác Giả: Nguyễn Xuân Bắc
- MSSV: K215480106004
- Lớp: K57KMT
- Ngày làm: 19/6/2024
## CHỨC NĂNG
### 1.Quản Lý
1.1 Quản lý Tuyến đường

- Thêm, sửa đổi, xóa tuyến đường: Cho phép quản lý viên thêm mới, chỉnh sửa hoặc xóa bỏ thông tin về các tuyến đường.
- Hiển thị chi tiết tuyến đường: Cung cấp thông tin chi tiết về các tuyến đường như điểm bắt đầu, điểm kết thúc, khoảng cách, thời gian dự kiến.

1.2 Quản lý Xe buýt

- Thêm, sửa đổi, xóa xe buýt: Cho phép quản lý viên thêm mới, chỉnh sửa hoặc xóa bỏ thông tin về các xe buýt.
- Xem trạng thái hoạt động của xe buýt: Theo dõi trạng thái của từng xe buýt, bao gồm tình trạng hoạt động, lịch trình hiện tại.

1.3 Quản lý Lịch trình

- Thêm, sửa đổi, xóa lịch trình: Cho phép quản lý viên lập lịch cho các xe buýt trên các tuyến đường khác nhau.
- Đặt lịch và hiển thị lịch trình: Lập lịch và hiển thị lịch trình điều hành của từng xe buýt trên các tuyến đường.

1.4 Quản lý tài xế

- Thêm, sửa đổi, xóa thông tin tài xế: Cho phép quản lý viên quản lý thông tin cá nhân và chứng chỉ của tài xế.
- Xếp lịch làm việc cho tài xế: Gán tài xế vào các lịch trình và xe buýt cụ thể.

### 2.Chức năng truy vấn

2.1 Tạo Cơ Sở Dữ Liệu và Các Bảng:
- Tạo bảng Bus để lưu thông tin về các xe buýt.
- Tạo bảng Route để lưu thông tin về các tuyến đường.
- Tạo bảng Driver để lưu thông tin về các tài xế.
- Tạo bảng Schedule để lưu thông tin lịch trình của các xe buýt.

2.2 Viết Hàm Thêm, Xóa, Sửa:
- Thủ tục AddBus: Thêm một xe buýt mới vào bảng Bus.
- Thủ tục DeleteBus: Xóa một xe buýt dựa trên BusID từ bảng Bus.
- Thủ tục UpdateBus: Sửa thông tin của một xe buýt dựa trên BusID từ bảng Bus.

2.3 Tạo Các View:
- View DetailedSchedule: Hiển thị thông tin chi tiết về lịch trình bao gồm thông tin từ các bảng Schedule, Bus, Route, và Driver.

2.4 Sử Dụng Trigger:
- Trigger UpdateAvgTravelTime: Tính toán lại thời gian di chuyển trung bình cho một tuyến đường khi có lịch trình mới được thêm vào trong bảng Schedule.

2.5 Sử Dụng Cursor:
- Thủ tục ShowAllBuses sử dụng cursor để duyệt qua danh sách các xe buýt trong bảng Bus và hiển thị thông tin chi tiết của từng xe buýt.

2.6 Ví Dụ Sử Dụng Thực Tế:
- Các ví dụ sử dụng thực tế cho phép thêm, xóa, sửa thông tin xe buýt và hiển thị thông tin chi tiết của các xe buýt.

# Thiết kế chương trình trong SQL
### 1. Tạo các bảng
- Bảng lưu thông tin các xe bus
- ID: Khóa chính
- Biển số xe bus
- sức chứa xe bus
- mô hình xe bus
  
