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
Bảng lưu thông tin các xe bus
- ID: Khóa chính
- Biển số xe bus
- sức chứa xe bus
- mô hình xe bus

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/b8d4800f-a96b-4dbc-a11f-9bfd6fc632c3)

Bảng để lưu thông tin về các tuyến đường
- ID duy nhất cho mỗi tuyến đường, tự động tăng
- Tên tuyến đường
- Điểm bắt đầu của tuyến
- Điểm kết thúc của tuyến
- Khoảng cách của tuyến đường

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/9ebc8a3f-8316-4e65-86d7-4fb651260573)

bảng Driver để lưu thông tin về các tài xế
- ID duy nhất cho mỗi tài xế, tự động tăng
- Tên tài xế
- Số giấy phép lái xe
- Số điện thoại tài xế

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/714c68fd-007e-4971-abba-cad7bc7b1a6b)

bảng Schedule để lưu thông tin lịch trình của các xe buýt
- ID duy nhất cho mỗi lịch trình, tự động tăng
- ID xe buýt
- ID tuyến đường
- ID tài xế
- Thời gian khởi hành
- Thời gian đến
- Khóa ngoại tới bảng Bus
- Khóa ngoại tới bảng Route
- Khóa ngoại tới bảng Driver

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/ce9399e9-acbf-4408-a7b8-41d36753afc9)

Sơ đồ đánh giá liên kết

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/fea1c673-d1df-471d-9f10-72b9ee5dde0d)

### 2.Thêm dữ liệu vào các bảng

- thêm dữ liệu vào bảng bus

INSERT INTO Busss (LicensePlate, Capacity, Model)

SELECT 'ABC-1234', 50, 'Model X'

UNION ALL

SELECT 'XYZ-5678', 45, 'Model Y';

- Thêm dữ liệu vào bảng Route:

INSERT INTO Route (RouteName, StartLocation, EndLocation, Distance)

VALUES ('Route 1', 'Start Point A', 'End Point B', 30.5),

       ('Route 2', 'Start Point C', 'End Point D', 45.2);
  
- Thêm dữ liệu vào bảng NewDriver:

INSERT INTO NewDriver (Name, LicenseNumber, PhoneNumber)

VALUES ('John Doe', '123456789', '123-456-7890'),

       ('Jane Smith', '987654321', '987-654-3210');

- Sử dụng BusID = 1, RouteID = 1, DriverID = 1 để thêm dữ liệu vào Schedule:

INSERT INTO Schedule (BusID, RouteID, DriverID, DepartureTime, 
ArrivalTime)

VALUES (1, 1, 1, '2024-06-20 08:00:00', '2024-06-20 10:00:00'),

       (2, 2, 2, '2024-06-21 09:00:00', '2024-06-21 11:00:00');

## Thiết lập chức năng

### 1.Chức năng cơ bản

1.1 thêm,xóa,sửa thông tin xe buýt:
- thêm một xe buýt mới

EXEC AddBus 'ABC-1234', 50, 'Model X';

- xóa một xe buýt theo ID:

EXEC DeleteBus 1;

- sửa thông tin một xe buýt theo ID

EXEC UpdateBus 2, 'XYZ-5678', 45, 'Model Y';

1.2 hiển thị thông tin tất cả các xe buýt

- Sử dụng thủ tục ShowAllBuses để in ra thông tin chi tiết của tất cả các xe buýt:

EXEC ShowAllBuses;

1.3 thêm dữ liệu vào các bảng chính:

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/2b5e8dd6-8ec2-4764-a195-44b94ddcf156)

1.4 thêm lịch trình ( Schdule ) cho xe buýt:

- Sử dụng các thông tin đã có từ các bảng Busss, Route, NewDriver để thêm lịch trình vào bảng Schedule:

  ![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/89a89af8-aa91-4218-a267-599685f51a88)

1.5 hiển thị các thông tin từ view đã tạo:

- Sử dụng view DriverScheduleDetails để hiển thị thông tin chi tiết về tài xế và các lịch trình mà họ điều khiển:

  ![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/2f18f9ab-2494-48da-8ad5-80259589eb4a)

1.6 Truy vấn trông tin từ các bảng chính:

- Lấy thông tin tất cả các tuyến xe buýt:

SELECT * FROM Route;

- Lấy thông tin lịch trình của một xe buýt cụ thể:
  
SELECT ScheduleID, RouteName, DepartureTime, ArrivalTime

FROM Schedule

JOIN Route ON Schedule.RouteID = Route.RouteID

WHERE BusID = 1;

- Lấy thông tin tài xế và lịch trình của họ:

SELECT Driver.Name, Route.RouteName, Schedule.DepartureTime, 

Schedule.ArrivalTime

FROM NewDriver

JOIN Schedule ON NewDriver.DriverID = Schedule.DriverID

JOIN Route ON Schedule.RouteID = Route.RouteID;

1.7 Sử dụng trigger và thủ tục để cập nhật và xử lý dữ liệu (như đã định nghĩa trong các trigger và thủ tục):

- Trigger UpdateAvgTravelTime để tính và in ra thời gian di chuyển trung bình khi có thêm lịch trình mới.

- Thủ tục ShowAllBuses để duyệt và in ra thông tin chi tiết của tất cả các xe buýt.

1.8 chức năng thêm sửa xóa xe buýt

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/94364ca8-f3bf-4d35-b9db-7378a907c53f)

### 2.Chức năng nâng cao 

2.1 tự dộng cập nhật thông tin liên quan khi xóa hoặc nhập dữ liệu

- Trigger để cập nhật thời gian di chuyển trung bình khi xóa một lịch trình:

CREATE TRIGGER UpdateAvgTravelTimeAfterDelete

ON Schedule

AFTER DELETE

AS

BEGIN

    DECLARE @RouteID INT;
    DECLARE @NewAvgTime FLOAT;
    SELECT @RouteID = DELETED.RouteID FROM DELETED;
    SELECT @NewAvgTime = AVG(DATEDIFF(MINUTE, DepartureTime, ArrivalTime))
    FROM Schedule
    WHERE RouteID = @RouteID;
    PRINT 'New average travel time for route ' + CAST(@RouteID AS VARCHAR) + ' is ' + CAST(@NewAvgTime AS VARCHAR);
    
END;

2.2 cập nhật lịch trình xe buýt

- Thủ tục cập nhật thông tin một lịch trình:

CREATE PROCEDURE UpdateSchedule

    @p_ScheduleID INT,
    @p_BusID INT,
    @p_RouteID INT,
    @p_DriverID INT,
    @p_DepartureTime DATETIME,
    @p_ArrivalTime DATETIME
AS

BEGIN

    UPDATE Schedule
    SET BusID = @p_BusID,
        RouteID = @p_RouteID,
        DriverID = @p_DriverID,
        DepartureTime = @p_DepartureTime,
        ArrivalTime = @p_ArrivalTime
    WHERE ScheduleID = @p_ScheduleID;
END;

2.3 Tự động kiểm tra tính hợp lệ của dữ liệu:

- Trigger để kiểm tra tính hợp lệ của thời gian khi thêm hoặc cập nhật lịch trình:

CREATE TRIGGER CheckScheduleTime

ON Schedule

BEFORE INSERT, UPDATE

AS

BEGIN

    DECLARE @DepartureTime DATETIME;
    
    DECLARE @ArrivalTime DATETIME;
    
    SELECT @DepartureTime = inserted.DepartureTime, @ArrivalTime = inserted.ArrivalTime FROM inserted;
    
    IF @DepartureTime >= @ArrivalTime
    BEGIN
        RAISERROR('Departure time must be before arrival time.', 16, 1);
        ROLLBACK;
    END
END;

2.4 Báo cáo chi tiết:

- View hiển thị thông tin chi tiết về các lịch trình trong một khoảng thời gian:

CREATE VIEW DetailedScheduleByDate AS

SELECT ScheduleID, Bus.LicensePlate, Route.RouteName, Driver.Name, 

DepartureTime, ArrivalTime

FROM Schedule

JOIN Busss ON Schedule.BusID = Busss.BusID

JOIN Route ON Schedule.RouteID = Route.RouteID

JOIN NewDriver ON Schedule.DriverID = NewDriver.DriverID

WHERE DepartureTime BETWEEN '2024-06-20' AND '2024-06-21';

2.5 quản lý người dùng và phân quyền

- Tạo các vai trò và phân quyền:

CREATE ROLE BusManager;

CREATE ROLE ScheduleManager;

GRANT SELECT, INSERT, UPDATE, DELETE ON Busss TO BusManager;

GRANT SELECT, INSERT, UPDATE, DELETE ON Schedule TO ScheduleManager;

GRANT SELECT ON Route TO BusManager, ScheduleManager;

GRANT SELECT ON NewDriver TO BusManager, ScheduleManager;

2.6 thủ tục lưu trữ phức tạp:

- Thủ tục tính toán và cập nhật số lượng lịch trình cho mỗi tài xế:

CREATE PROCEDURE UpdateDriverScheduleCount

AS

BEGIN

    UPDATE NewDriver
    SET ScheduleCount = (SELECT COUNT(*) FROM Schedule WHERE Schedule.DriverID = NewDriver.DriverID);
END;

2.7 Quản lý sự thay đổi:

- Bảng lịch sử và trigger để lưu trữ các thay đổi:

CREATE TABLE ScheduleHistory (

    HistoryID INT PRIMARY KEY IDENTITY(1,1),
    ScheduleID INT,
    BusID INT,
    RouteID INT,
    DriverID INT,
    DepartureTime DATETIME,
    ArrivalTime DATETIME,
    ChangeDate DATETIME DEFAULT GETDATE(),
    ChangeType VARCHAR(10)
);

CREATE TRIGGER LogScheduleChanges

ON Schedule

AFTER INSERT, UPDATE, DELETE

AS

BEGIN

    DECLARE @ChangeType VARCHAR(10);
    IF EXISTS (SELECT * FROM inserted)
    BEGIN
        IF EXISTS (SELECT * FROM deleted)
            SET @ChangeType = 'UPDATE';
        ELSE
            SET @ChangeType = 'INSERT';
    END
    ELSE
        SET @ChangeType = 'DELETE';

    INSERT INTO ScheduleHistory (ScheduleID, BusID, RouteID, DriverID, DepartureTime, ArrivalTime, ChangeType)
    SELECT ISNULL(i.ScheduleID, d.ScheduleID), ISNULL(i.BusID, d.BusID), ISNULL(i.RouteID, d.RouteID), ISNULL(i.DriverID, d.DriverID),
           ISNULL(i.DepartureTime, d.DepartureTime), ISNULL(i.ArrivalTime, d.ArrivalTime), @ChangeType
    FROM inserted i
    FULL OUTER JOIN deleted d ON i.ScheduleID = d.ScheduleID;
END;

2.8 Tạo báo cáo thống kê:

- Thủ tục lưu trữ để tạo báo cáo thống kê số lượng xe buýt, tài xế và lịch trình:

CREATE PROCEDURE GenerateStatisticsReport

AS

BEGIN

    SELECT 
        (SELECT COUNT(*) FROM Busss) AS TotalBuses,
        (SELECT COUNT(*) FROM NewDriver) AS TotalDrivers,
        (SELECT COUNT(*) FROM Schedule) AS TotalSchedules;
END;

2.9  Chức năng tìm kiếm nâng cao:

- Tìm kiếm lịch trình theo tên tài xế:

CREATE PROCEDURE SearchScheduleByDriverName

    @DriverName VARCHAR(100)
AS

BEGIN
    SELECT ScheduleID, Bus.LicensePlate, Route.RouteName, 
    
    NewDriver.Name, DepartureTime, ArrivalTime
    FROM Schedule
    JOIN Busss ON Schedule.BusID = Busss.BusID
    JOIN Route ON Schedule.RouteID = Route.RouteID
    JOIN NewDriver ON Schedule.DriverID = NewDriver.DriverID
    WHERE NewDriver.Name LIKE '%' + @DriverName + '%';
END;

- Kết Quả

![image](https://github.com/BacNguyen003/BTL_CSDL_QuanLyTuyenXe-Buyt/assets/170489566/9c1cc45f-0b3e-4a5d-a169-018cfbf76f23)







