# Hệ thống Quản lý Phòng trọ (QLPT)

## Giới thiệu
Hệ thống Quản lý Phòng trọ là một ứng dụng console được phát triển bằng C++ nhằm hỗ trợ việc quản lý và vận hành các nhà trọ, phòng trọ một cách hiệu quả.

## Tính năng chính

### 👥 Quản lý Tài khoản
- **Chủ trọ**: Đăng ký, đăng nhập và quản lý thông tin cá nhân
- **Người thuê**: Đăng ký, đăng nhập và quản lý thông tin cá nhân
- **Hệ thống phân quyền**: Phân biệt quyền hạn giữa chủ trọ và người thuê

### 🏠 Quản lý Phòng trọ
- **Thêm phòng**: Tạo mới thông tin phòng trọ
- **Sửa phòng**: Cập nhật thông tin phòng (giá, diện tích, tiện ích...)
- **Xóa phòng**: Xóa phòng không còn cho thuê
- **Tìm kiếm phòng**: Tìm kiếm theo ID, tên phòng hoặc tiêu chí khác
- **Hiển thị danh sách**: Xem danh sách tất cả phòng trọ

### 📋 Quản lý Hợp đồng
- **Tạo hợp đồng**: Lập hợp đồng thuê phòng
- **Xem hợp đồng**: Hiển thị thông tin hợp đồng theo thời gian hoặc phòng
- **Xóa hợp đồng**: Hủy hợp đồng khi hết hạn
- **Tìm kiếm hợp đồng**: Tìm kiếm hợp đồng theo nhiều tiêu chí

### 💰 Quản lý Hóa đơn
- **Tạo hóa đơn**: Lập hóa đơn tiền phòng, điện, nước
- **Cập nhật hóa đơn**: Sửa thông tin hóa đơn
- **Xóa hóa đơn**: Xóa hóa đơn không hợp lệ
- **Tìm kiếm hóa đơn**: Tìm kiếm theo thời gian hoặc phòng
- **Thống kê doanh thu**: Báo cáo tổng doanh thu

## Cấu trúc Project

```
PBL2/
├── main.cpp              # File chính của chương trình
├── QLPT.h/.cpp          # Class quản lý chính
├── nguoi.h/.cpp         # Class người (base class)
├── chu_tro.h/.cpp       # Class chủ trọ
├── nguoi_thue.h/.cpp    # Class người thuê
├── phong_tro.h/.cpp     # Class phòng trọ
├── hop_dong.h/.cpp      # Class hợp đồng
├── hoa_don.h/.cpp       # Class hóa đơn
├── account.txt          # File lưu thông tin tài khoản
├── chu_tro.txt          # File lưu thông tin chủ trọ
├── nguoi_thue.txt       # File lưu thông tin người thuê
├── phong_tro.txt        # File lưu thông tin phòng trọ
├── hop_dong.txt         # File lưu thông tin hợp đồng
└── hoa_don.txt          # File lưu thông tin hóa đơn
```

## Yêu cầu hệ thống

### Phần mềm
- **Compiler**: GCC 7.0+ hoặc Clang 6.0+
- **C++ Standard**: C++11 hoặc cao hơn
- **OS**: Windows, macOS, Linux

### Thư viện
- `iostream` - Input/Output
- `fstream` - File handling
- `string` - String manipulation
- `iomanip` - Output formatting
- `sstream` - String stream
- `cstdlib` - General utilities

## Hướng dẫn Cài đặt và Chạy

### 1. Clone Repository
```bash
git clone https://github.com/Baotrh8805/TL_ky_3.git
cd TL_ky_3/PBL2
```

### 2. Biên dịch chương trình

#### Trên Linux/macOS:
```bash
g++ -o main main.cpp QLPT.cpp chu_tro.cpp nguoi_thue.cpp phong_tro.cpp hop_dong.cpp hoa_don.cpp nguoi.cpp
```

#### Trên Windows (với MinGW):
```bash
g++.exe -o main.exe main.cpp QLPT.cpp chu_tro.cpp nguoi_thue.cpp phong_tro.cpp hop_dong.cpp hoa_don.cpp nguoi.cpp
```

### 3. Chạy chương trình

#### Trên Linux/macOS:
```bash
./main
```

#### Trên Windows:
```bash
main.exe
```

## Hướng dẫn Sử dụng

### 1. Đăng nhập
- Chạy chương trình và nhập thông tin đăng nhập
- Chọn loại tài khoản: Chủ trọ hoặc Người thuê

### 2. Menu Chủ trọ
- **Quản lý phòng trọ**: Thêm, sửa, xóa, tìm kiếm phòng
- **Quản lý hợp đồng**: Tạo, xem, xóa hợp đồng
- **Quản lý hóa đơn**: Tạo, cập nhật, xóa, thống kê hóa đơn

### 3. Menu Người thuê
- **Xem thông tin cá nhân**: Cập nhật thông tin tài khoản
- **Tìm kiếm phòng**: Tìm phòng phù hợp
- **Xem hợp đồng**: Xem hợp đồng đã ký
- **Xem hóa đơn**: Theo dõi các khoản phí

## Cấu trúc Dữ liệu

### Tài khoản
```cpp
struct tai_khoan {
    string user;    // Tên đăng nhập
    string pass;    // Mật khẩu
    string ID;      // ID người dùng
    bool role;      // Quyền hạn (true: chủ trọ, false: người thuê)
}
```

### Phòng trọ
- ID phòng, tên phòng
- Diện tích, giá thuê
- Trạng thái (trống/đã thuê)
- Tiện ích kèm theo

### Hợp đồng
- ID hợp đồng
- Thông tin chủ trọ và người thuê
- Thời gian thuê
- Điều khoản hợp đồng

### Hóa đơn
- ID hóa đơn
- Chi phí phòng, điện, nước
- Thời gian thanh toán
- Trạng thái thanh toán

## Thuật toán sử dụng

- **Binary Search**: Tìm kiếm nhanh trong danh sách đã sắp xếp
- **Linked List**: Quản lý danh sách tài khoản động
- **File I/O**: Lưu trữ và đọc dữ liệu từ file


- **Repository**: [https://github.com/Baotrh8805/PBL2](https://github.com/Baotrh8805/PBL2)



---
