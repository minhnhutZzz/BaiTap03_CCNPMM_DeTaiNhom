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

## 🚀 Kết quả kiểm thử API Backend (API Testing)

Dưới đây là các kịch bản kiểm thử API đã được thực hiện bằng Postman để chứng minh tính đúng đắn và sự chặt chẽ trong khâu xử lý lỗi của hệ thống.

### 1. POST Login API - Thành công
**Mô tả:** Khi client cung cấp thông tin đăng nhập (Email/Username và Password) hợp lệ. Hệ thống xử lý thành công, trả về HTTP Status `200 OK` kèm theo thông tin User và chuỗi `access_token` JWT.

<img width="1918" height="877" alt="image" src="https://github.com/user-attachments/assets/5dc85a72-4a48-4bcb-876e-82d28e13cbcb" />

### 2. POST Login API - Sai mật khẩu
**Mô tả:** Khi client nhập đúng Email/Username nhưng sai mật khẩu. Hệ thống từ chối truy cập, trả về HTTP Status `401 Unauthorized` hoặc `400 Bad Request` kèm thông báo lỗi "Thông tin đăng nhập không chính xác".

<img width="1917" height="753" alt="image" src="https://github.com/user-attachments/assets/f633a8ca-95ca-49ea-a404-6f5bd17ba82b" />

### 3. POST Login API - Thiếu Validation
**Mô tả:** Khi request body từ client gửi lên bị thiếu các trường bắt buộc hoặc sai định dạng (email không có `@`). Lớp Middleware Validation bắt lỗi ngay lập tức và trả về HTTP Status `400 Bad Request`.

<img width="1915" height="777" alt="image" src="https://github.com/user-attachments/assets/8854117f-bf6f-4ff9-bc19-9f55863d6b79" />

### 4. POST Login API - Bị chặn RateLimit
**Mô tả:** Khi một IP cố tình gửi quá nhiều request đăng nhập liên tục trong thời gian ngắn. Hệ thống kích hoạt Rate Limit, chặn các request tiếp theo và trả về HTTP Status `429 Too Many Requests`.

<img width="1904" height="761" alt="image" src="https://github.com/user-attachments/assets/3adb05f1-7e05-4880-9882-d54054828bc9" />

---

## 🛠️ Công nghệ & Thư viện sử dụng
- **Nền tảng Backend:** Node.js, Express.js
- **Nền tảng Frontend:** React.js (Vite), TailwindCSS v4
- **State & Gọi API:** Redux Toolkit, Axios, React Router DOM
- **Bảo mật:** `jsonwebtoken`, `bcrypt`, `express-rate-limit`
- **Cơ sở dữ liệu:** MySQL (Sequelize ORM)
- **Validation:** `Joi`
 
