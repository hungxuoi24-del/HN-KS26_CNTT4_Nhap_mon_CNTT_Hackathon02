# BÀI LÀM – HACKATHON 02

- **Mã đề:** 01
- **Họ tên:** Nguyễn Duy Hưng
- **Lớp:** CNTT_04
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
- Hiển thị đường dẫn tuyệt đối của thư mục hiện tại.
    * pwd

- Liệt ke nội dung thư mục gốc, gồm cả file ẩn.
    * ls -Force

- Di chuyển file ghi_chu_ban_giao.txt vào docs.
    * mv .\ghi_chu_ban_giao.txt .\docs\

- Tạo thư mục backup trong thư mục gốc.
    * mkdir backup

- Sao chép data/ban_ve_thang_1.xlsx vào backup.
    * cp .\data\ban_ve_thang_1.xlsx .\backup\

- Xóa file .tmp tại thư mục gốc, không xóa file khác.
    * rm .\temp_101.tmp

- Dùng đường dẫn tương đối vào logs, liệt kê nội dung rồi quay lại thư mục gốc.
    * cd .\logs\
    * ls -Force
    * cd ..

- Liệt kê toàn bộ tự án gồm cả thư mục con và file ẩn.
    * Get-ChildItem -Recurse -Force
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/4/2026   7:43 AM                backup
d-----         11/4/2026   7:37 AM                data
d-----         11/4/2026   7:41 AM                docs
d-----         11/4/2026   7:36 AM                evidence
d-----         11/4/2026   7:38 AM                logs
d-----         11/4/2026   7:34 AM                web
------         11/3/2026   7:06 AM             74 .env
-a----         11/4/2026   7:48 AM           3067 bai_lam.md


    Directory: C:\Rekkei_edu\IT_108_K26\session_24\starter-kit\starter-kit\ho-boi-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM           6106 ban_ve_thang_1.xlsx


    Directory: C:\Rekkei_edu\IT_108_K26\session_24\starter-kit\starter-kit\ho-boi-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM           6106 ban_ve_thang_1.xlsx


    Directory: C:\Rekkei_edu\IT_108_K26\session_24\starter-kit\starter-kit\ho-boi-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM            158 ghi_chu_ban_giao.txt


    Directory: C:\Rekkei_edu\IT_108_K26\session_24\starter-kit\starter-kit\ho-boi-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM            972 visit.log


    Directory: C:\Rekkei_edu\IT_108_K26\session_24\starter-kit\starter-kit\ho-boi-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/4/2026   7:34 AM                images
------         11/3/2026   7:06 AM            574 app.js
------         11/3/2026   7:06 AM            507 index.html
------         11/3/2026   7:06 AM            460 style.css

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
Get-Content .\logs\visit.log | Select-String "status=500" > .\logs\loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-01-28 08:24:34 POST /api/thanh-toan status=500
2026-01-28 08:28:45 POST /api/thanh-toan status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\visit.log | Select-String "status=404").count

```

```text
- Kết quả: 4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\tong_hop.ps1 

```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-01-28 08:07:39 GET /tin-tuc status=404
2026-01-28 08:13:01 GET /ve-cu status=404
2026-01-28 08:34:07 GET /images/be-boi-2.jpg status=404
2026-01-28 08:57:24 GET /khuyen-mai-he status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [ ] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [ ] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [ ] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| :--: | :--: | :--: | :--: |
| 1 | Network | logo.png | đổi thành images/logo-aquazone.png |
| 2 | Console | hienThiBangGia() | sửa thành hienThiBangGiaVe() |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** Tôi đang thực hiện thao tác với tab Console
- **Expected:** Đoạn code chạy thành công mà không phát sinh ngoại lệ
- **Actual:** chương trình trình duyệt bị lỗi khiến ko hiện logo, bảng giá
- **Log:** Uncaught ReferenceError: hienThiBangGia is not defined

### Câu tìm kiếm Google

```text
"Uncaught ReferenceError: hienThiBangGia is not defined" site:stackoverflow.com

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/ban_ve_thang_1.xlsx`, không cần ghi vào đây.
