# Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## Mục tiêu
* Cấu hình tệp tin ẩn `.gitignore` để tự động bỏ qua các file nhạy cảm hoặc file rác hệ thống.
* Sử dụng lệnh gỡ bỏ file đã commit ra khỏi cache theo dõi của Git một cách an toàn.
* Chỉnh sửa thông điệp hoặc nội dung của commit gần nhất thông qua tùy chọn `amend`.

## Yêu cầu
**Bối cảnh:** Học viên vô tình commit nhầm file chứa thông tin bảo mật `credentials.txt` lên Git. Học viên cần gỡ bỏ file này khỏi sự theo dõi mà không làm mất file vật lý trên đĩa cứng, cấu hình để Git bỏ qua file này trong tương lai, và sửa lại tin nhắn commit gần nhất cho sạch sẽ.

**Ràng buộc:** Không sử dụng lệnh xóa vật lý file trên hệ điều hành, phải giữ lại tệp tin ở thư mục làm việc cục bộ.

## File nộp bài
* `.gitignore`: File quy định bỏ qua tệp `credentials.txt`.
* `README.md`: Báo cáo cách thực hiện các bước khắc phục.

## Các bước xử lý sự cố (Báo cáo thực hành)

1. **Tạo mô phỏng lỗi (Giả sử đã lỡ commit):**
   ```bash
   echo "secret_password_123" > credentials.txt
   git add credentials.txt
   git commit -m "Thêm file credentials (Commit lỗi)"
   ```

2. **Gỡ bỏ file khỏi hệ thống theo dõi của Git (nhưng giữ nguyên file vật lý):**
   - Lệnh sử dụng (Rất quan trọng):
   ```bash
   git rm --cached credentials.txt
   ```
   *(Tùy chọn `--cached` giúp Git ngừng theo dõi file nhưng không xóa file khỏi thư mục làm việc)*

3. **Cấu hình file .gitignore để Git không báo file này nữa:**
   - Cập nhật `.gitignore` (như file đính kèm) và đưa vào staging:
   ```bash
   git add .gitignore
   ```

4. **Sửa lại nội dung và thông điệp commit gần nhất bằng Amend:**
   - Ghi đè lại commit trước đó bằng thay đổi mới (đã rút file credentials ra và thêm .gitignore vào) kèm message mới:
   ```bash
   git commit --amend -m "Thêm cấu hình .gitignore, gỡ bỏ tệp nhạy cảm"
   ```

## Kết quả Kiểm tra

**1. Kiểm tra trạng thái làm việc hiện tại:**
```bash
git status
```
*(Học viên dán log trạng thái terminal ở đây, credentials.txt sẽ không còn nằm trong mục Untracked)*

**2. Kiểm tra lịch sử commit gần nhất:**
```bash
git log -n 1
```
*(Học viên dán kết quả lệnh git log ở đây để minh chứng commit message đã được sửa đổi sạch sẽ)*
