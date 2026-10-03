## 1. CÁC BƯỚC THỰC HIỆN CHI TIẾT

### Bước 1: Tạo và chuyển sang nhánh tính năng `feature-update`
```bash
# Tạo nhánh mới và chuyển sang nhánh feature-update
git checkout -b feature-update

# Chỉnh sửa dòng mô tả trong README.md và commit
echo "# Dự Án Quản Lý Học Viên - Phiên bản nâng cao từ nhánh feature-update" > README.md
git add README.md
git commit -m "feat: update project title on feature-update branch"
```

---

### Bước 2: Quay lại nhánh `main` và chỉnh sửa cùng dòng mã
```bash
# Chuyển về nhánh main
git checkout main

# Chỉnh sửa cùng dòng mã trong README.md với nội dung khác
echo "# Dự Án Quản Lý Học Viên - Phiên bản ổn định từ nhánh main" > README.md
git add README.md
git commit -m "fix: update project title on main branch"
```

---

### Bước 3: Thực hiện gộp nhánh và ghi nhận xung đột (Merge Conflict)
```bash
# Đứng từ nhánh main, tiến hành gộp nhánh feature-update
git merge feature-update
```

**Kết quả thông báo trên Terminal:**
```text
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```
> **Nguyên nhân:** Cả 2 nhánh `main` và `feature-update` cùng thay đổi dòng đầu tiên của file `README.md` kể từ commit chung gần nhất. Git không thể tự quyết định lấy phiên bản nào nên kích hoạt cơ chế dừng để người dùng xử lý thủ công.

---

### Bước 4: Xử lý xung đột thủ công (Manual Conflict Resolution)

Mở file `README.md`, Git chèn các thẻ đánh dấu xung đột như sau:
```markdown
<<<<<<< HEAD
# Dự Án Quản Lý Học Viên - Phiên bản ổn định từ nhánh main
=======
# Dự Án Quản Lý Học Viên - Phiên bản nâng cao từ nhánh feature-update
>>>>>>> feature-update
```

**Ý nghĩa các thẻ đánh dấu:**
- `<<<<<<< HEAD`: Bắt đầu đoạn mã thuộc nhánh hiện tại (`main`).
- `=======`: Ranh giới phân chia giữa 2 phiên bản xung đột.
- `>>>>>>> feature-update`: Kết thúc đoạn mã thuộc nhánh đang được gộp vào (`feature-update`).

**Thao tác xử lý thủ công:**
Xóa bỏ hoàn toàn các ký hiệu `<<<<<<<`, `=======`, `>>>>>>>` và kết hợp nội dung mong muốn:
```markdown
# Dự Án Quản Lý Học Viên - Phiên bản hợp nhất hoàn chỉnh (Main & Feature-Update)
```

---

### Bước 5: Đánh dấu đã xử lý và hoàn tất commit gộp nhánh
```bash
# Thêm file đã giải quyết xung đột vào Staging Area
git add README.md

# Tạo commit gộp nhánh hoàn tất
git commit -m "Merge branch 'feature-update' into main - Resolved conflict manually"
```

---

## 2. NỘI DUNG TỆP README.MD SAU KHI GIẢI QUYẾT XUNG ĐỘT HOÀN CHỈNH

```markdown
# Dự Án Quản Lý Học Viên - Phiên bản hợp nhất hoàn chỉnh (Main & Feature-Update)

Dự án đã được gộp thành công giữa hai nhánh `main` và `feature-update`. Toàn bộ xung đột trên file README.md đã được xử lý thủ công an toàn, giữ vững tính toàn vẹn của mã nguồn.
```

---

## 3. KIỂM TRA ĐỒ THỊ NHÁNH (GIT LOG --GRAPH --ONELINE)

Chạy lệnh kiểm tra theo yêu cầu đề bài:
```bash
git log --graph --oneline
```

