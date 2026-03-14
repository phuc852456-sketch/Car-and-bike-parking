# Hệ Thống Quản Lý Bãi Đỗ Xe

**Car-and-bike-parking** là một giải pháp quản lý bãi đỗ xe hiện đại, bao gồm Backend API được xây dựng bằng NestJS và Ứng dụng di động Android sử dụng Kotlin. Hệ thống cung cấp các tính năng toàn diện để quản lý việc ra vào xe, người dùng và các hoạt động bãi đỗ.

## Mục Lục

- [Tổng Quan](#tổng-quan)
- [Tính Năng](#tính-năng)
- [Kiến Trúc Hệ Thống](#kiến-trúc-hệ-thống)
- [Yêu Cầu](#yêu-cầu)
- [Cài Đặt](#cài-đặt)
- [Cấu Hình](#cấu-hình)
- [Sử Dụng](#sử-dụng)
- [Xác Thực](#xác-thực)
- [Kiểm Thử](#kiểm-thử)
- [Đóng Góp](#đóng-góp)
- [Giấy Phép](#giấy-phép)

## Tổng Quan

Hệ thống quản lý bãi đỗ xe được thiết kế để hỗ trợ quản lý hiệu quả các bãi đỗ thông qua ứng dụng di động và hệ thống backend mạnh mẽ. Dự án bao gồm hai thành phần chính:

- **Backend**: NestJS + TypeScript
- **Ứng dụng di động**: Android + Kotlin

## Tính Năng

### Người Dùng
- Đăng ký / Đăng nhập
- Xác thực dựa trên JWT
- Quản lý hồ sơ cá nhân
- Xem trạng thái bãi đỗ

### Quản Trị Viên
- Quản lý người dùng
- Quản lý bãi đỗ
- Kiểm soát ra vào xe
- Quản lý quyền truy cập

### Tải Hình Ảnh
- Hỗ trợ tải hình ảnh qua Cloudinary

### Bảo Mật
- Xác thực JWT
- Admin Guard
- Auth Guard

## Kiến Trúc Hệ Thống

```
   Ứng dụng di động (Android - Kotlin)
            |
            | REST API
            v
   Backend (NestJS)
            |
            v
   Database
```

### Cấu Trúc Backend

```
src/
├── admin/                    # Quản lý quản trị viên
│   ├── admin.controller.ts
│   ├── admin.service.ts
│   └── admin.module.ts
├── auth/                     # Xác thực & phân quyền
│   ├── auth.controller.ts
│   ├── auth.service.ts
│   └── auth.module.ts
├── guard/                    # Các bảo vệ (Guard)
│   ├── jwt-auth.guard.ts
│   └── admin.guard.ts
├── cloudinary/              # Tích hợp Cloudinary
├── app.module.ts
├── app.controller.ts
└── app.service.ts
```

### Cấu Trúc Ứng dụng Di Động

```
ParkingSystem-done/
├── app/
├── gradle/
├── build.gradle
└── settings.gradle
```

## Yêu Cầu

### Backend
- Node.js >= 16.x
- npm >= 8.x
- MongoDB hoặc PostgreSQL

### Ứng dụng Di Động
- Android Studio >= 4.0
- Android SDK 21+
- Kotlin 1.5+

## Cài Đặt

### Backend

1. **Clone dự án**
```bash
git clone https://github.com/phuc852456-sketch/Car-and-bike-parking.git
cd Car-and-bike-parking
```

2. **Cài đặt dependencies**
```bash
npm install
```

3. **Cấu hình biến môi trường**
```bash
cp .env.example .env
```

4. **Chạy ở chế độ phát triển**
```bash
npm run start:dev
```

Default server: `http://localhost:3000`

#### Các lệnh Backend

| Lệnh | Mô Tả |
|------|-------|
| npm run start | Chạy dự án |
| npm run start:dev | Chạy ở chế độ phát triển (hot reload) |
| npm run build | Build dự án |
| npm run test | Chạy test |

### Ứng dụng Di Động

1. Mở Android Studio
2. Mở thư mục dự án `Car-and-bike-parking`
3. Đồng bộ hóa Gradle files (File > Sync Now)
4. Chọn thiết bị/emulator và nhấn `Run App`

## Cấu Hình

### Biến Môi Trường (.env)

Tạo file `.env` trong thư mục gốc backend:

```env
# Database
DATABASE_URL=mongodb://localhost:27017/parking_system
# Hoặc PostgreSQL: DATABASE_URL=postgresql://user:password@localhost:5432/parking_system

# JWT
JWT_SECRET=your_secret_key_here
JWT_EXPIRATION=7d

# Cloudinary
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Server
PORT=3000
NODE_ENV=development
```

### Cấu Hình Cloudinary

1. Tạo tài khoản tại Cloudinary
2. Lấy API credentials từ dashboard
3. Thêm vào file `.env`

## Sử Dụng

### Backend API

Khi server chạy tại `http://localhost:3000`:

- Truy cập các endpoint API cho quản lý người dùng, hoạt động bãi đỗ, v.v.
- Sử dụng JWT token trong header `Authorization` cho các request được xác thực

### Ứng dụng Di Động

Ứng dụng Android kết nối với Backend API và cung cấp:

- Xác thực người dùng
- Trạng thái bãi đỗ theo thời gian thực
- Quản lý ra vào xe
- Tải lên hình ảnh xe và hồ sơ người dùng

## Xác Thực

Hệ thống sử dụng **JWT (JSON Web Tokens)** để xác thực.

### Quy Trình Xác Thực

```
1. Người dùng đăng nhập
   |
   v
2. Server xác thực thông tin đăng nhập & trả về JWT token
   |
   v
3. Client lưu JWT & gửi nó trong request headers
   |
   v
4. Auth Guard xác thực token trên mỗi request
   |
   v
5. Request được phê duyệt được xử lý
```

### Ví Dụ Request Header

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

## Kiểm Thử

Chạy test suite:

```bash
npm run test
```

Kiểm tra phạm vi test:

```bash
npm run test:cov
```

## Tài Liệu API

**Base URL:** `http://localhost:3000`

- **Auth Endpoints:** `/api/auth`
- **User Endpoints:** `/api/users`
- **Admin Endpoints:** `/api/admin`

Ghi chú: Hãy cân nhắc thêm tài liệu Swagger/OpenAPI để có API docs toàn diện

## Đóng Góp

Chúng tôi rất hoan nghênh các đóng góp! Vui lòng:

1. Fork dự án
2. Tạo nhánh tính năng (git checkout -b feature/amazing-feature)
3. Commit các thay đổi (git commit -m 'Add amazing feature')
4. Push đến nhánh (git push origin feature/amazing-feature)
5. Mở Pull Request

## Giấy Phép

Dự án này được cấp phép theo MIT License - xem file LICENSE để biết chi tiết.

## Tác Giả

**Huynh Thanh Phuc**

- Email: phuc852456@gmail.com
- GitHub: @phuc852456-sketch

Nếu có vấn đề, câu hỏi hoặc đề xuất, vui lòng mở issue trên GitHub hoặc liên hệ với tác giả.