# Hướng dẫn sử dụng Knowledge Base — Dị Biến thế Giới

> Đọc file này TRƯỚC khi làm bất kỳ thao tác nào liên quan đến truyện.

---

## Cấu trúc thư mục

```
/
├── HUONG_DAN.md          ← (file này) bản đồ toàn bộ KB
├── style.md              ← PHONG CÁCH VIẾT: giọng văn, cấu trúc, hội thoại, thói quen dùng từ
├── trang-thai.md         ← TRẠNG THÁI HIỆN TẠI: vị trí nhân vật, plot threads mở, quan hệ
├── index.md              ← TÓM TẮT 127 CHƯƠNG có tags, đọc đầu tiên khi cần định vị
├── arc/                  ← Summary từng arc (arc1 → arc7), dùng thay chương gốc khi có thể
│   ├── arc1-summary.md   ← Arc 1: Nhập Học (Ch.001-014)
│   ├── arc2-summary.md   ← Arc 2: Hồn Giới (Ch.015-028)
│   ├── arc3-summary.md   ← Arc 3: Yêu Nhau (Ch.029-053)
│   ├── arc4-summary.md   ← Arc 4: Anh Hùng Chiến (Ch.054-074)
│   ├── arc5-summary.md   ← Arc 5: Tân Việt Xuất Hiện (Ch.075-093)
│   ├── arc6-summary.md   ← Arc 6: Doanh Trại (Ch.094-112)
│   └── arc7-summary.md   ← Arc 7: Biệt Phủ (Ch.113-127) — ARC HIỆN TẠI
├── chuong/               ← Văn bản gốc từng chương (001.md → 127.md)
├── nhan-vat/             ← File hồ sơ từng nhân vật
└── the-gioi/             ← Lore thế giới, hệ thống sức mạnh, tổ chức
```

---

## Cách tìm kiếm thông minh

### Bước 0A — Câu hỏi về phong cách / viết chương mới → đọc style.md TRƯỚC TIÊN
Mọi câu hỏi kiểu "viết theo phong cách tác giả", "tiếp tục chương mới", "cách tác giả hay dùng từ gì", "giọng văn thế nào" → **chỉ cần đọc `style.md`**. Không cần đọc chương gốc để tìm phong cách.

### Bước 0B — Câu hỏi về "hiện tại" → đọc trang-thai.md trước
Mọi câu hỏi kiểu "X đang ở đâu", "plot nào đang mở", "quan hệ hiện tại thế nào" → đọc `trang-thai.md` là đủ trong 90% trường hợp. Không cần tra index hay chương gốc.

### Bước 1 — Xác định phạm vi bằng index.md
`index.md` có đúng 127 dòng, mỗi dòng format:
```
Ch.XXX | Nhân vật chính | Địa điểm | Sự kiện cốt lõi #tag1 #tag2
```
**Dùng Grep trên index.md** để định vị nhanh chương cần đọc.

Ví dụ:
- Tìm chương có Tuyết Nhi → `grep "#tuyetnhi" index.md`
- Tìm chương liên quan Hồn Giới → `grep "#hongioi" index.md`
- Tìm sự kiện VÔ → `grep "#vo" index.md`
- Tìm theo tên trực tiếp → `grep "Đầm Sen" index.md`

**Danh sách tags chuẩn:**
- Nhân vật: `#cuong #mocthao #tuyetnhi #nghia #phanson #vqt #ngoclan #nhauyen #jasonbui #lisapham #bennychuong #huongthuy #ingah #duongtinh #truongquochuy #ongbien #thuquynh #doduynhat`
- Hệ thống: `#hongioi #lucquyde #tanviet #carders #vo #ychidewuong #ahc #hoilienminh #hethong`
- Địa điểm/sự kiện: `#doantrai #bietphu #damsen #phantoc #romance #death #reveal #chuyensinh`

### Bước 2 — Lazy loading theo chiều sâu (QUAN TRỌNG)
Khi câu hỏi liên quan đến một arc cụ thể:
- **Arc được hỏi trực tiếp** → đọc chương gốc `chuong/XXX.md`
- **Arc trước đó** (bối cảnh/tiền đề) → chỉ đọc `arc/arcX-summary.md`
- **Arc không liên quan** → bỏ qua hoàn toàn

Ví dụ: câu hỏi về sự kiện Arc 5 nhưng cần hiểu bối cảnh từ Arc 3:
→ Đọc `arc/arc3-summary.md` (bối cảnh) + `chuong/075-093.md` (chi tiết Arc 5)

### Bước 3 — Đọc hồ sơ nhân vật
Hồ sơ nhân vật tổng hợp toàn bộ thông tin theo chủ đề. Dùng khi cần thông tin xuyên suốt nhiều arc về 1 nhân vật.

### Bước 4 — Đọc chương gốc chỉ khi cần chi tiết cụ thể
File gốc ở `chuong/XXX.md`. Chỉ cần đọc khi arc summary + hồ sơ nhân vật chưa đủ.

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
| `hon-gioi.md` | Thế giới Linh Hồn: cơ chế, 2 lần Cường vào (Ch.024-028 & Ch.107-108), 10 mảnh hồn |
| `tan-viet.md` | Tổ chức Tân Việt / Hội Thống Trị: cơ cấu, Tam Giác Quỷ, timeline sự kiện |

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

## 7 Arc truyện

| Arc | Chương | Tên | Sự kiện chính |
|-----|--------|-----|---------------|
| Arc 1 | Ch.001-014 | Nhập Học | Cường chuyển sinh, nhập học Xà Cừ, hình thành Hội Liên Minh 10C1, Đại Dương hóa quỷ |
| Arc 2 | Ch.015-028 | Hồn Giới | Cường "chết" ở Đầm Sen, Mộc Thảo vào Hồn Giới cứu, 10 mảnh hồn, lời nguyền biến thể ác tính |
| Arc 3 | Ch.029-053 | Yêu Nhau | Hậu Hồn Giới, gia đình hai bên, lời nguyền 6 ngày, Cường tỏ tình thành công |
| Arc 4 | Ch.054-074 | Anh Hùng Chiến | Giải đấu AHC, Ngọc Lan đột nhập biệt thự Phan Sơn, Đỗ Duy Nhất lộ diện |
| Arc 5 | Ch.075-093 | Tân Việt Xuất Hiện | Kẻ Áo Đen, Lisa Phạm tấn công, Tuyết Nhi bộc lộ [Khải Huyền], Benny phục kích |
| Arc 6 | Ch.094-112 | Doanh Trại | AHC nội bộ, doanh trại Phan Sơn, Hương Thủy, Nghi thức Lên Đồng, Hồn Giới lần 2 |
| Arc 7 | Ch.113-127 | Biệt Phủ | Jason Bùi tấn công, mê cung, Tam Giác Quỷ, VQT tham chiến, Lục Quỷ Đế toàn xuất |

---

## Câu hỏi hay gặp → đọc file nào

| Câu hỏi | File cần đọc |
|---------|-------------|
| **Viết chương mới / hỏi về phong cách viết** | **`style.md` — ĐỌC ĐẦU TIÊN, không cần đọc chương gốc** |
| X đang ở đâu? Plot nào đang mở? | `trang-thai.md` |
| Arc X tóm tắt như thế nào? | `arc/arcX-summary.md` |
| Cường có Gift gì? Ý Chí Đế Vương hoạt động thế nào? | `nhan-vat/luu-chi-cuong.md` |
| Hồn Giới là gì? Cường vào mấy lần? | `the-gioi/hon-gioi.md` |
| Tuyết Nhi thực sự là ai? Lục Quỷ Đế là gì? | `nhan-vat/tuyet-nhi.md` + `the-gioi/luc-quy-de.md` |
| Tân Việt gồm những ai? Cơ cấu tổ chức? | `the-gioi/tan-viet.md` |
| Carders là gì? Jack Heart là ai? | `the-gioi/chu-cong-va-to-chuc.md` |
| Phan Sơn che giấu ai và vì sao? | `nhan-vat/phan-son.md` + `nhan-vat/do-duy-nhat.md` |
| Nghĩa có những Gift gì? | `nhan-vat/nghia.md` |
| Jason Bùi / Lisa / Benny là ai? | `nhan-vat/jason-bui.md`, `nhan-vat/lisa-pham.md`, `nhan-vat/benny-chuong.md` |
| Nhân vật phụ X xuất hiện ở chương nào? | `nhan-vat/nhan-vat-phu.md` (grep tên) |
| Chương X có gì xảy ra? | `index.md` (grep `Ch.0XX`) → `chuong/XXX.md` nếu cần chi tiết |

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
