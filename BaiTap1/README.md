# Bài 1: Khởi tạo Local Repository và Cấu hình danh tính

## Mục tiêu
* Khởi tạo thành công một Git repository trống tại thư mục làm việc cục bộ.
* Thiết lập thông tin danh tính tác giả (tên và email) ở cấp độ cục bộ (local).
* Tạo tệp tin mới, đưa vào vùng chuẩn bị (Staging Area) và tiến hành commit đầu tiên.
* Đọc và phân tích trạng thái thư mục làm việc và lịch sử commit thông qua lệnh `log`.

## Yêu cầu
**Bối cảnh:** Bạn bắt đầu một dự án phần mềm mới và muốn quản lý mã nguồn bằng Git ở local.

**Ràng buộc:** Cấu hình email và tên tác giả bắt buộc phải sử dụng tùy chọn `--local` (không sử dụng `--global` để tránh ảnh hưởng đến các cấu hình toàn cục khác của máy tính).

## Kiểm tra
**Lệnh kiểm tra:**
```bash
# Kiểm tra cấu hình email cục bộ:
git config --local user.email

# Kiểm tra cấu hình tên cục bộ:
git config --local user.name

# Xem lịch sử commit:
git log --oneline
```

**Kết quả mong đợi:**
* Lệnh cấu hình in ra đúng email và tên đã cấu hình riêng cho dự án này.
* `git log` hiển thị tối thiểu 1 commit đầu tiên với thông điệp rõ nghĩa.

## Hướng dẫn nộp bài (Các lệnh thực hành)

Học viên thực hiện lần lượt các lệnh sau trên terminal của mình:
```bash
# 1. Khởi tạo Local Repository
git init

# 2. Cấu hình danh tính cục bộ (thay thế bằng tên và email của bạn)
git config --local user.name "Ten Cua Ban"
git config --local user.email "email.cua.ban@example.com"

# 3. Tạo một file mới (ví dụ: tạo tệp tin text)
echo "Hello Git" > index.txt

# 4. Thêm file vào Staging Area
git add index.txt

# 5. Commit
git commit -m "Initial commit: Khởi tạo dự án"

# 6. Kiểm tra lại thông tin để chụp ảnh nộp
git config --local --list
git log --oneline
```

### Kết quả Log Terminal (Minh chứng thực tế)
```bash
$ git config --local --list
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
user.name=Học Viên DevOps
user.email=hocvien@example.com

$ git log --oneline
0d76b93 (HEAD -> main, origin/main) Initial commit: Khởi tạo dự án
```
