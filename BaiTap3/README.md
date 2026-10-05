# Bài 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub

## Mục tiêu
* Khởi tạo cặp khóa SSH bảo mật phục vụ mục đích xác thực kết nối từ xa.
* Cấu hình liên kết an toàn giữa repository cục bộ với máy chủ GitHub.
* Đẩy (push) mã nguồn và lịch sử commit thành công lên GitHub bằng giao thức SSH.

## Yêu cầu
**Bối cảnh:** Học viên cần đưa dự án cục bộ lên kho lưu trữ đám mây GitHub để lưu trữ và cộng tác nhóm.

**Ràng buộc:** Bắt buộc sử dụng giao thức SSH và thuật toán Ed25519 để sinh khóa (không sử dụng giao thức HTTPS để tránh phải nhập password/token thủ công).

## Các bước thực hiện (Báo cáo mẫu)

1. **Khởi tạo cặp khóa SSH Ed25519:**
   - Chạy lệnh sinh khóa từ Terminal: 
     ```bash
     ssh-keygen -t ed25519 -C "your_email@example.com"
     ```
   - Lưu khóa tại đường dẫn mặc định và có thể thiết lập passphrase (hoặc bỏ qua).

2. **Thêm Public Key vào tài khoản GitHub:**
   - Đọc nội dung khóa công khai: 
     ```bash
     cat ~/.ssh/id_ed25519.pub
     ```
   - Truy cập **Settings > SSH and GPG keys > New SSH key** trên GitHub, đặt tên (VD: *My Laptop*) và dán nội dung khóa công khai vừa copy.

3. **Cấu hình liên kết Remote Repository:**
   - Thiết lập remote `origin` bằng địa chỉ SSH:
     ```bash
     git remote add origin git@github.com:USERNAME/REPOSITORY.git
     ```
     *(Lưu ý: Nếu đang sử dụng HTTPS, ta có thể đổi sang SSH bằng lệnh: `git remote set-url origin git@github.com:USERNAME/REPOSITORY.git`)*

4. **Đẩy mã nguồn lên GitHub:**
   - Thực hiện lệnh push để đưa lịch sử commit lên kho lưu trữ: 
     ```bash
     git push -u origin main
     ```

## Kết quả Kiểm tra

**1. Kiểm tra kết nối SSH tới GitHub:**
```bash
ssh -T git@github.com
```
*(Học viên dán log thông báo thành công của GitHub tại đây, ví dụ: `Hi username! You've successfully authenticated...`)*

**2. Kiểm tra cấu hình remote URL:**
```bash
git remote -v
```
*(Học viên dán log cấu hình remote tại đây để chứng minh đang dùng dạng SSH)*
```text
origin  git@github.com:IT-Devops-209/Devops-SS4.git (fetch)
origin  git@github.com:IT-Devops-209/Devops-SS4.git (push)
```
