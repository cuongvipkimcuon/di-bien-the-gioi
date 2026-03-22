# Hướng dẫn sử dụng Knowledge Base — Dị Biến thế Giới

> Đọc file này TRƯỚC khi làm bất kỳ thao tác nào liên quan đến truyện.

---

## Cấu trúc thư mục

```
/
├── HUONG_DAN.md          ← (file này) bản đồ toàn bộ KB
├── index.md              ← TÓM TẮT 127 CHƯƠNG, đọc đầu tiên khi cần định vị
├── chuong/               ← Văn bản gốc từng chương (001.md → 127.md)
├── nhan-vat/             ← File hồ sơ từng nhân vật
└── the-gioi/             ← Lore thế giới, hệ thống sức mạnh, tổ chức
```

---

## Cách tìm kiếm thông minh

### Bước 1 — Xác định phạm vi bằng index.md
`index.md` có đúng 127 dòng, mỗi dòng format:
```
Ch.XXX | Nhân vật chính | Địa điểm | Sự kiện cốt lõi
```
**Dùng Grep trên index.md** để định vị nhanh chương cần đọc thay vì đọc toàn bộ văn bản gốc.

Ví dụ:
- Tìm chương có Tuyết Nhi → `grep "Tuyết Nhi" index.md`
- Tìm chương ở Đầm Sen → `grep "Đầm Sen" index.md`
- Tìm khi VÔ lần đầu xuất hiện → `grep "\[VÔ\]" index.md`

### Bước 2 — Đọc hồ sơ nhân vật trước khi đọc chương gốc
Hồ sơ nhân vật đã tổng hợp sẵn toàn bộ thông tin theo chủ đề. Tiết kiệm hơn nhiều so với đọc chương gốc.

### Bước 3 — Đọc chương gốc chỉ khi cần chi tiết cụ thể
File gốc ở `chuong/XXX.md`. Chỉ cần đọc khi hồ sơ nhân vật chưa đủ.

---

## Danh sách file nhân vật (nhan-vat/)

| File | Nhân vật | Vai trò |
|------|----------|---------|
| `luu-chi-cuong.md` | Lưu Chí Cường | Nhân vật chính. [VÔ], Ý Chí Đế Vương, Jack Heart |
| `moc-thao.md` | Mộc Thảo | Nữ chính. Gift [Hồi Phục] cấp 5, cháu gái Phan Sơn |
| `nghia.md` | Lưu Chí Nghĩa | Em trai Cường. [Sáng Tạo] + nhiều Gift ẩn, sức mạnh bí ẩn |
| `tuyet-nhi.md` | Đỗ Tuyết Nhi | "Hắc Hồ Ly". [Khải Huyền: Chinh Phục], Lục Quỷ Đế, trùm Tân Việt thật sự |
| `phan-son.md` | Phan Sơn | Đại tướng. [Thời Gian], Ý Chí Đế Vương hoàn thiện, "Tiến Trình Hòa Bình" |
| `vo-quoc-thanh.md` | Võ Quốc Thanh | "Phượng Hoàng Bất Tử". 4 Gift cấp 5, Song Hỏa Kiếm POLYGON + AROUD |
| `nguyen-huong-thuy.md` | Nguyễn Hương Thủy | Trung tá. [Thánh Thủy], [Hắc Thủy], [Cảm Xúc] |
| `ngoc-lan.md` | Ngọc Lan | Queen Spade. [Giấc Ngủ], Kim Giáp, con mất của Spade King & Queen |
| `hoang-nha-uyen.md` | Hoàng Nhã Uyên | [Thánh Quang], cháu thứ 5 Phan tộc, con nuôi Hoàng Gia |
| `jason-bui.md` | Jason Bùi "Cánh Bạc" | Tam Giác Quỷ. [Không Gian] + [Thiên Sứ] Seraphim, con trai Bùi Vịnh |
| `lisa-pham.md` | Lisa Phạm | Tam Giác Quỷ. [Linh Hồn], bị Tuyết Nhi nhốt Ch.087, được cứu Ch.124 |
| `benny-chuong.md` | Benny Chương | "Thợ Săn Tàn Nhẫn". [Kiến Tạo Địa Hình], cánh tay máy |
| `do-duy-nhat.md` | Đỗ Duy Nhất | Trùm Tân Việt (danh nghĩa). Cha Tuyết Nhi, đang bị Phan Sơn che giấu |
| `ingah.md` | Ingah | "Con trai thất lạc Hoàng gia". [Hủy Diệt], mắt trái bạc, bí ẩn |
| `duong-tinh.md` | Dương Tính | King Heart (đình chỉ). [Khói Độc], hôn phu Hồng Hoa |
| `truong-quoc-huy.md` | Trương Quốc Huy | [Thôi Miên], hôn phu Hoàng Anh, cộng tác với kẻ xấu |
| `ke-ao-den.md` | Kẻ Áo Đen | Phản diện bí ẩn. Gift [Hủy Diệt] (tím đen), biết Cường là "kẻ tái sinh" |
| `ong-bien.md` | Ông Biên | Bác Cường. Thủ trưởng Tình báo Sài Thành |
| `duc.md` | Đức | Bạn lớp 10C1. [Tìm Kiếm], lớp trưởng sau Thúy Vy |
| `phong.md` | Phong | Bạn lớp 10C1. [Trình Diễn Ký Ức], gia đình giàu có |
| `thu-quynh.md` | Thu Quỳnh | Chị cả Cường (con nuôi). Trưởng R&D Cục Tình Báo |

---

## Danh sách file thế giới (the-gioi/)

| File | Nội dung |
|------|----------|
| `he-thong-gift.md` | Toàn bộ lore Gift: cấp 1-5, 8 Gift đặc biệt cấp 10, bảng Gift đã xuất hiện |
| `chu-cong-va-to-chuc.md` | Hệ thống Carders (J/Q/K/A × 4 suits), Tứ Trụ, quyền hạn, danh sách thành viên |
| `luc-quy-de.md` | 6 Quỷ Đế cổ xưa: MATERIA, SPIRITUA, POWERA, DIMENSIA, TIMEA, MINDA |

---

## Các khái niệm then chốt cần biết

| Khái niệm | Giải thích ngắn |
|-----------|----------------|
| **[VÔ]** | Năng lực Cường — KHÔNG phải Gift, không thuộc hệ năng lượng thế giới. Vô hiệu hóa mọi Gift/ma thuật |
| **Ý Chí Đế Vương** | Biến cảm xúc thành sức mạnh vật lý. 5 trạng thái: Hạnh phúc / U sầu / Thịnh nộ / Thanh thản / Sợ hãi |
| **[Chấp Niệm]** | Năng lượng tâm linh cấm từ ám ảnh/hận thù — tăng sức mạnh nhưng nguy hiểm |
| **[Chấp Niệm Đế Vương]** | Trạng thái berserk khi hai luồng năng lượng hợp nhất |
| **Nghi thức Lên Đồng** | Huấn luyện quân đội chuyển Ý Chí Đế Vương bị động → chủ động. Cường đã hoàn thành (Ch.108) |
| **Hệ thống Saint** | Giáp chiến đấu 4 cấp: Giáp Sắt < Giáp Đồng < Giáp Bạc < Giáp Vàng |
| **Carders / Chủ Công** | 18 chiến binh elite ký hiệu bài Tây (J/Q/K/A × Cơ/Rô/Nhép/Bích). Cường = Jack Heart |
| **Tứ Trụ** | 4 người điều hành Carders: Bộ trưởng QP, Bộ trưởng AN, Cục trưởng TBI, Phan Sơn |
| **Lục Quỷ Đế** | 6 thực thể vũ trụ cổ xưa, tồn tại trước Gift. Tuyết Nhi ký khế ước |
| **Hồn Giới** | Thế giới linh hồn — Cường đã vào 2 lần (Ch.024-028 & Ch.107-108) |
| **Tam Giác Quỷ** | Tổ chức gồm Jason Bùi, Lisa Phạm, Benny Chương dưới trướng Tuyết Nhi |
| **Tiến Trình Hòa Bình** | Kế hoạch bí mật 40 năm của Phan Sơn: đảo chính ngầm qua tham nhũng |

---

## Timeline chính (mốc ngày tháng)

| Ngày | Sự kiện |
|------|---------|
| 01/08/2013 | Cường chuyển sinh, nhập học trường Xà Cừ |
| 15/08/2013 | Ngày học đầu tiên thật sự (Ch.004) |
| 21/12/2013 | Sinh nhật Đức, đi Đầm Sen — Cường "chết" và hồi sinh (Ch.015-028) |
| 24/12/2013 | Thảo tỏ tình, bị từ chối; lời nguyền Tham Lam kích hoạt (Ch.034) |
| 28/12/2013 | Cường chính thức tỏ tình, hai người yêu nhau (Ch.053) |
| 01/01/2014 | Đại Thọ Phan Sơn; Ngọc Lan đột nhập biệt thự (Ch.039-070) |
| 02/01/2014 | Cường tỉnh lại tại nhà Ngọc Lan (Ch.071) |
| 04/01/2014 | Double date Thảo Cầm Viên — trận gấu Chấp Niệm (Ch.080-088) |
| 05/01/2014 | Benny Chương phục kích cổng trường (Ch.091-093); kiểm tra AHC (Ch.096-098) |
| 09/01/2014 | Cường nhập doanh trại Thiếu Sinh Quân Phan Sơn (Ch.102) |
| 10/01/2014 | Jason Bùi tấn công biệt phủ Phan gia đêm (Ch.115-127) |

---

## Lưu ý khi cập nhật KB

1. Luôn cập nhật `index.md` trước (1 dòng/chương)
2. Sau đó cập nhật file nhân vật liên quan
3. Tạo/cập nhật file `the-gioi/` nếu có lore mới
4. Commit và push sau mỗi batch chương
5. **Tránh nhầm lẫn**: POLYGON + AROUD là vũ khí của VQT, không phải Cường
