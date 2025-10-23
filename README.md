# Bài tập tuần 3 – Môn Lập trình mạng căn bản

## Nhóm sinh viên thực hiện

| MSSV     | Họ và tên          |
| -------- | ------------------ |
| 22521251 | Nguyễn Duy Thế Sơn |
| 24520262 | Nguyễn Tấn Danh    |
| 24521230 | Phan Lê Tuấn       |
| 24521940 | Hứa Thiện Nhân     |
| 22520973 | Ngô Vũ Hạo Nguyên  |

---

## Mô tả bài tập

Ứng dụng quản lý người dùng gồm 3 form chính:

**1. Form Đăng ký (RegisterForm):**

* Người dùng nhập Tên đăng nhập, Mật khẩu, Xác nhận mật khẩu, Email.
* Mật khẩu được mã hóa SHA256 và lưu vào SQL Server.

**2. Form Đăng nhập (LoginForm):**

* Kiểm tra tài khoản, mật khẩu đã mã hóa trong SQL Server.
* Nếu đúng → chuyển đến form chính.
* Nếu sai → thông báo lỗi.

**3. Form Chính (MainForm):**

* Hiển thị nút “Đăng xuất” để quay lại form đăng nhập.

Ứng dụng được lập trình bằng **C# WinForms**, kết nối cơ sở dữ liệu qua **ADO.NET**.

---

## Hướng dẫn cài đặt

### 1. Yêu cầu

* Visual Studio 2019 hoặc 2022
* .NET Framework 4.7.2 trở lên
* SQL Server (LocalDB hoặc SQL Server Express)

### 2. Tạo cơ sở dữ liệu

Chạy các lệnh sau trong SQL Server Management Studio:

```sql
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
```

### 3. Cấu hình kết nối

Trong file `DbHelper.cs`, chỉnh lại chuỗi kết nối phù hợp:

```csharp
public static string ConnectionString =
    "Server=localhost\\SQLEXPRESS;Database=UserManagerDB;Integrated Security=True;";
```

Nếu dùng LocalDB:

```csharp
public static string ConnectionString =
    "Server=(localdb)\\MSSQLLocalDB;Database=UserManagerDB;Integrated Security=True;";
```

### 4. Chạy chương trình

* Mở file `ex2.2.sln` bằng Visual Studio
* Nhấn **Start (F5)** để chạy
* Giao diện đầu tiên là form đăng nhập → có thể chuyển sang đăng ký tài khoản mới

---

## Kiến thức áp dụng

* Windows Forms (C#)
* Kết nối cơ sở dữ liệu bằng ADO.NET
* Mã hóa mật khẩu với SHA256
* Kiểm tra dữ liệu đầu vào
* Lập trình hướng đối tượng (OOP)
