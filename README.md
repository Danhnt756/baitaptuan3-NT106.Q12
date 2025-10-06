BÀI TẬP TUẦN 3 – MÔN LẬP TRÌNH MẠNG CĂN BẢN  
Nhóm sinh viên thực hiện  
  22520973	Ngô Vũ Hạo Nguyên  
  22521251	Nguyễn Duy Thế Sơn  
  24520262	Nguyễn Tấn Danh  
  24521230	Phan Lê Tuấn  
  24521940 Hứa Thiện Nhân  
  
--Mô tả bài tập  

Ứng dụng quản lý người dùng gồm 3 form chính:  
Form Đăng ký (RegisterForm):  
Người dùng nhập Tên đăng nhập, Mật khẩu, Xác nhận mật khẩu, Email.  
Thông tin được kiểm tra hợp lệ, mã hóa mật khẩu bằng SHA256 và lưu vào SQL Server.  
  
Form Đăng nhập (LoginForm):  
Kiểm tra tên đăng nhập và mật khẩu đã mã hóa với dữ liệu trong SQL Server.  
Nếu hợp lệ → chuyển đến màn hình chính (MainForm).  
Nếu sai → hiển thị thông báo lỗi.  
  
Form Chính (MainForm):  
Hiển thị nút Đăng xuất để quay lại trang đăng nhập.  
Ứng dụng được lập trình bằng C# WinForms, kết nối cơ sở dữ liệu bằng ADO.NET (SqlConnection, SqlCommand).  

--Hướng dẫn cài đặt  
  
 Yêu cầu  
Visual Studio 2022 (hoặc 2019)  
.NET Framework 4.7.2 trở lên  
SQL Server (LocalDB hoặc SQL Server Express)  
  
--Tạo cơ sở dữ liệu  
Mở SQL Server Management Studio (SSMS)  
Chạy câu lệnh sau để tạo Database:  
CREATE DATABASE UserManagerDB;  
GO  
USE UserManagerDB;  
GO  
CREATE TABLE Users (  
    Id INT IDENTITY(1,1) PRIMARY KEY,  
    Username NVARCHAR(50) NOT NULL,  
    PasswordHash NVARCHAR(255) NOT NULL,  
    Email NVARCHAR(100) NOT NULL  
);  
Lưu database lại (hoặc export ra file UserManagerDB.sql để chia sẻ).  
  
--Cấu hình kết nối trong code  
  
Trong file DbHelper.cs, sửa lại dòng kết nối đúng với máy:  
public static string ConnectionString =  
    "Server=localhost\\SQLEXPRESS;Database=UserManagerDB;Integrated Security=True;";  
  
--Nếu bạn dùng LocalDB thì thay bằng:  
public static string ConnectionString =  
    "Server=(localdb)\\MSSQLLocalDB;Database=UserManagerDB;Integrated Security=True;";  

--Chạy chương trình  
Mở solution ex2.2.sln bằng Visual Studio  
Bấm Start (F5) để chạy  
Màn hình đầu tiên là Đăng nhập, chọn Đăng ký để tạo tài khoản mới.  
Sau khi đăng ký thành công → đăng nhập lại để vào form chính.  
  
🧭 Hướng dẫn sử dụng  
Đăng ký người dùng mới  
Nhập đầy đủ thông tin → bấm Đăng ký  
Nếu hợp lệ sẽ lưu vào SQL Server.  
Đăng nhập  
Nhập đúng tài khoản đã đăng ký → vào màn hình chính.  
Đăng xuất  
Bấm nút Đăng xuất để quay lại trang đăng nhập.  
  
🖼️ Các màn hình giao diện  
🪪 1. Form Đăng ký  
Nhập: Tên đăng nhập, Mật khẩu, Xác nhận mật khẩu, Email  
Nút: “Đăng ký” và “Quay lại đăng nhập”  
  
🔐 2. Form Đăng nhập  
Nhập: Tên đăng nhập, Mật khẩu  
Nút: “Đăng nhập” và “Đăng ký”  
   
🏠 3. Form Chính  
Hiển thị nút “Đăng xuất” để quay lại trang đăng nhập.  
  
📦 Cấu trúc thư mục  
├── ex2.2/  
│   ├── DbHelper.cs  
│   ├── LoginForm.cs  
│   ├── RegisterForm.cs  
│   ├── MainForm.cs  
│   ├── Program.cs  
│   ├── Properties/  
│   └── ex2.2.sln  
└── UserManagerDB.sql  
  
🧠 Kiến thức áp dụng  
Sử dụng WinForms (Windows Form App)  
Kết nối SQL Server bằng ADO.NET  
Mã hóa mật khẩu với SHA256  
Kiểm tra dữ liệu đầu vào (validation)  
Tổ chức code theo hướng đối tượng (OOP)  
