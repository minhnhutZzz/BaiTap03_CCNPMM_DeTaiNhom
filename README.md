# 🛡️ Hệ thống Đăng nhập (Login Authentication & Frontend UI)

**Thông tin sinh viên thực hiện:**
- **Họ và tên:** Đào Minh Nhựt
- **MSSV:** 23110282
- **Chuyên ngành:** Công nghệ phần mềm (Software Engineering)
- **Môn học:** Các công nghệ phần mềm mới
- **Phân công Nhóm 4:** Phụ trách toàn bộ tính năng Đăng nhập (Backend API & Frontend React)

---

## 📖 Giới thiệu dự án
Dự án này triển khai chức năng Đăng nhập (Login) hoàn chỉnh từ Front-end đến Back-end một cách an toàn và tối ưu, tuân thủ các tiêu chuẩn bảo mật hiện đại. Chức năng được thiết kế với kiến trúc rõ ràng, kết hợp UI/UX thân thiện bằng React.js và tích hợp nhiều lớp bảo vệ (Rate Limit, JWT) ở Node.js để đảm bảo tính an toàn tối đa cho hệ thống cũng như dữ liệu của người dùng.

## ✨ Các tính năng nổi bật (Key Features) do Đào Minh Nhựt thực hiện

### 1. 🎨 Giao diện Frontend Hiện đại (React.js + TailwindCSS v4)
- Xây dựng giao diện Đăng nhập mang phong cách **Glassmorphism** (kính mờ) hiện đại, bắt mắt.
- Xử lý trạng thái (State) loading, tự động vô hiệu hóa nút bấm trong lúc chờ API phản hồi để tránh người dùng nhấn nhiều lần.
- Quản lý trạng thái đăng nhập toàn cục bằng **Redux Toolkit** (`authSlice`), tự động lưu Token và điều hướng (Navigate) sang trang Profile.
- Cấu hình **Axios** chặn bắt Request (Interceptor) để giao tiếp mượt mà với Backend.

### 2. 🔑 Xác thực bằng JWT (JSON Web Token)
- Sử dụng tiêu chuẩn **JWT** để cấp phát Access Token sau khi người dùng xác thực thành công.
- Token được ký (sign) bằng secret key an toàn, bao gồm các thông tin cần thiết (payload) và thời gian sống (expiration time) giới hạn.
- Cơ chế xác thực **Stateless**, giúp tối ưu hiệu suất server và dễ dàng mở rộng (scale) hệ thống.

### 3. 🛡️ Data Validation (Kiểm tra dữ liệu đầu vào)
- Xác thực chặt chẽ mọi dữ liệu đầu vào từ client trước khi tiến hành xử lý logic (ví dụ: email phải đúng định dạng, mật khẩu không được bỏ trống và phải đạt độ dài/độ phức tạp tối thiểu).
- Trả về các thông báo lỗi (Error Messages) rõ ràng cho Frontend để hiển thị trực tiếp lên màn hình đăng nhập cho người dùng.

### 4. 🚦 Rate Limiting (Chống Spam/Brute-force)
- Tích hợp cơ chế giới hạn số lượng request từ một địa chỉ IP trong một khoảng thời gian nhất định đối với endpoint Đăng nhập.
- Bảo vệ hệ thống khỏi các cuộc tấn công **Brute-force** (dò mật khẩu liên tục), giữ cho server luôn hoạt động ổn định.

### 5. 🔐 Authorization (Phân quyền truy cập)
- Sau khi xác thực danh tính (Authentication), hệ thống tiếp tục kiểm tra quyền (Authorization) của người dùng đối với các tài nguyên cụ thể.
- Đảm bảo người dùng chỉ có thể thực hiện các thao tác và truy cập vào các API Endpoint tương ứng với Role của mình (VD: User, Admin).

---
# Giao diện trang Login 


## 🛠️ Công nghệ & Thư viện sử dụng
- **Nền tảng Backend:** Node.js, Express.js
- **Nền tảng Frontend:** React.js (Vite), TailwindCSS v4
- **State & Gọi API:** Redux Toolkit, Axios, React Router DOM
- **Bảo mật:** `jsonwebtoken`, `bcrypt`, `express-rate-limit`
- **Cơ sở dữ liệu:** MySQL (Sequelize ORM)
- **Validation:** `Joi`
 
