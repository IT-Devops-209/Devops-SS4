# Bài 2: Quản lý nhánh và Giải quyết xung đột (Merge Conflict)

## Mục tiêu
* Tạo mới và di chuyển linh hoạt giữa các nhánh (branch) cục bộ.
* Cố ý tạo ra xung đột gộp nhánh (Merge Conflict) và xử lý xung đột thủ công.
* Hoàn thành commit gộp nhánh và hiểu cơ chế gộp 3 vùng (3-Way Merge).

## Các bước đã thực hiện để tạo và giải quyết xung đột (Báo cáo mẫu)

1. **Khởi tạo và commit trên nhánh main:**
   - Tạo file `test-conflict.txt` ở nhánh `main` với nội dung: `Nội dung ban đầu từ main.`
   - Thêm vào staging và commit.

2. **Tạo nhánh mới và thay đổi mã nguồn:**
   - Tạo và chuyển sang nhánh `feature-update` bằng lệnh: `git checkout -b feature-update`.
   - Sửa file `test-conflict.txt` thành: `Nội dung cập nhật từ nhánh feature-update.`
   - Commit thay đổi trên nhánh `feature-update`.

3. **Tạo thay đổi mới trên nhánh main (Gây xung đột):**
   - Chuyển về nhánh `main`: `git checkout main`.
   - Sửa cùng dòng trong file `test-conflict.txt` thành: `Nội dung cập nhật từ nhánh main để gây xung đột.`
   - Commit thay đổi trên `main`.

4. **Tiến hành gộp nhánh và ghi nhận xung đột:**
   - Đang ở nhánh `main`, chạy lệnh: `git merge feature-update`.
   - Git báo lỗi **Merge conflict in test-conflict.txt**. 

5. **Giải quyết xung đột thủ công:**
   - Mở file `test-conflict.txt`, xóa các dòng đánh dấu do Git tạo ra (`<<<<<<< HEAD`, `=======`, `>>>>>>> feature-update`).
   - Chỉnh sửa lại thành nội dung cuối cùng thống nhất: `Nội dung đã được giải quyết xung đột kết hợp từ cả 2 nhánh.`
   - Đưa file đã sửa vào staging area: `git add test-conflict.txt`.
   - Tạo commit gộp: `git commit -m "Merge branch 'feature-update' vào main - Đã giải quyết xung đột"` để hoàn tất việc gộp nhánh.

## Kết quả Kiểm tra (Đồ thị lịch sử Git)

Dưới đây là mô phỏng kết quả chạy lệnh `git log --graph --oneline`:
```text
*   a1b2c3d Merge branch 'feature-update' vào main - Đã giải quyết xung đột
|\  
| * e4f5g6h Cập nhật file trên nhánh feature-update
* | i7j8k9l Cập nhật file trên nhánh main (gây conflict)
|/  
*   m0n1o2p Khởi tạo file test-conflict ban đầu trên main
*   0d76b93 Thêm bài tập 1: Khởi tạo Local Repository và Cấu hình danh tính
```
*(Học viên có thể thay thế bằng ảnh chụp thực tế hoặc copy log trực tiếp từ terminal cá nhân)*
