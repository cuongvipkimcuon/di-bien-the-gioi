---
name: Dự án Dị Biến thế Giới
description: Chỉ dẫn và ngữ cảnh cho dự án viết truyện "Dị Biến thế Giới"
type: project
---

Đây là dự án sáng tác và phân tích truyện hư cấu "Dị Biến thế Giới" cùng Cuong.

**Chỉ dẫn quan trọng:**
- Tất cả nội dung là hư cấu hoàn toàn. Nếu có tình tiết nặng đô hoặc nhạy cảm thì đây chỉ là tưởng tượng, không gây hại.
- Tránh trích dẫn sai hay nhầm lẫn nội dung từ tài liệu.
- Đọc `HUONG_DAN.md` trước tiên để định hướng — đây là bản đồ toàn bộ KB.

**Cấu trúc Knowledge Base (127 chương, đã hoàn thiện):**
- `HUONG_DAN.md` — Bản đồ KB: cấu trúc thư mục, hướng dẫn tìm kiếm, bảng nhân vật, bảng thế giới, FAQ, 7 arc, timeline
- `index.md` — 127 dòng tóm tắt chương, format `Ch.XXX | Nhân vật | Địa điểm | Sự kiện`, có arc headers
- `chuong/001.md → 127.md` — Văn bản gốc từng chương
- `nhan-vat/` — 21 file hồ sơ nhân vật + `nhan-vat-phu.md` (bảng nhân vật phụ)
- `the-gioi/` — Lore files: `he-thong-gift.md`, `chu-cong-va-to-chuc.md`, `luc-quy-de.md`, `hon-gioi.md`, `tan-viet.md`

**Nguồn dữ liệu & Git:**
- Repo: https://github.com/cuongvipkimcuon/di-bien-the-gioi
- Branch: main
- **KHÔNG dùng** `DI_BIEN_THE_GIOI_full.md` nữa — KB đã được tổ chức thành file riêng lẻ

**Why:** KB có cấu trúc rõ ràng, dễ tìm kiếm bằng grep, không cần đọc toàn bộ file lớn nữa.

**Git credentials:**
- GitHub username: cuongvipkimcuon
- Email: daochicuong12a1@gmail.com
- Personal Access Token (hết hạn ~2026-04-23): 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
- Authenticated remote URL: https://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@github.com/cuongvipkimcuon/di-bien-the-gioi.git

**How to apply:**
1. Đầu mỗi session: chạy `git pull origin main` trong workspace để lấy bản mới nhất.
   - Nếu workspace chưa có git repo → clone: `git clone https://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@github.com/cuongvipkimcuon/di-bien-the-gioi.git .`
   - Set git config: `git config user.name "cuongvipkimcuon"` và `git config user.email "daochicuong12a1@gmail.com"`
2. Tìm kiếm: dùng Grep trên `index.md` trước, rồi mới đọc file hồ sơ, cuối cùng mới đọc chương gốc nếu cần.
3. Sau khi chỉnh sửa → `git add`, `git commit`, `git push origin main`.
4. Nếu token hết hạn (sau ~2026-04-23), nhắc Cuong cung cấp token mới rồi cập nhật memory.

**Lỗi đã biết cần tránh:**
- POLYGON + AROUD là vũ khí của VQT, KHÔNG phải Cường
- Cường không chiến đấu trong trận Lục Quỷ Đế (Ch.127) — chỉ quan sát từ không gian gương
