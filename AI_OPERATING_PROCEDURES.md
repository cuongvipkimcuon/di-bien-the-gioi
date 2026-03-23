# AI Operating Procedures — Dự án Dị Biến Thế Giới

> **TÀI LIỆU NỘI BỘ:** Các quy tắc hoạt động tự động mà AI phải tuân theo trong mọi session làm việc với dự án này.

**Ngày Có Hiệu Lực:** 2026-03-23
**Phiên Bản:** 1.0
**Trạng Thái:** ✅ ACTIVE (Cuong kích hoạt)

---

## 🎯 5 Giải Pháp Tiết Kiệm Token — BẮTBUỘC

### **Giải Pháp #1: KHÔNG Include Chat Cũ**

**Quy Tắc:**
- Mỗi request mới → **KHÔNG lặp lại nội dung từ request trước**
- Chỉ tham chiếu khi thực sự cần (VD: "dựa trên kết quả grep vừa rồi")
- Không nói: "Tôi vừa hỏi X, bây giờ Y"
- Hãy nói: Thẳng vào "Y"

**Tiết Kiệm:** ~10-15% tokens/request (30-50 tokens)

**Cách Thực Hiện:**
- Request lần 1: Tìm kiếm
- Request lần 2: (Không nhắc lại request 1) Hỏi việc tiếp theo
- Chat history tự giữ context

---

### **Giải Pháp #2: Batch Request Liên Quan**

**Quy Tắc:**
- Nhiều task **LIÊN QUAN** nhau → 1 request duy nhất
- Nhiều task **KHÔNG LIÊN QUAN** → tách riêng request

**Không TỐTTED:**
```
Request 1: "Grep '#cuong' index.md"
Request 2: "Grep '#thao' index.md"
Request 3: "Grep '#tuyetnhi' index.md"
```

**✅ ĐÚNG:**
```
Request 1: "Grep index.md với tags: #cuong, #thao, #tuyetnhi"
```

**Tiết Kiệm:** ~10-20% tokens/session (50-100 tokens)

**Cách Thực Hiện:**
- Khi có 2-3 task giống nhau → group thành 1 request
- Dùng comma hoặc "và" để liệt kê
- VD: "Cập nhật index.md + trang-thai.md" (nếu liên quan)

---

### **Giải Pháp #3: Grep Trước, Đọc Sau**

**Quy Tắc:**
- **BẬC 1:** Grep `index.md` để định vị chương/nhân vật
- **BẬC 2:** Xem kết quả grep
- **BẬC 3:** Quyết định đọc file nào
- **KHÔNG bao giờ:** "Đọc tất cả chương có X và tóm tắt"

**Không Tốt:**
```
"Tìm tất cả chương có Tuyết Nhi và tóm tắt chi tiết từng chương"
→ Dàn trải, đọc 10+ file
```

**✅ ĐÚNG:**
```
"Grep '#tuyetnhi' index.md"
[Xem kết quả: Ch.020, Ch.087, Ch.105, ...]
"Đọc arc 5 summary để hiểu bối cảnh Tuyết Nhi"
[Xem arc summary]
"Nếu cần chi tiết hơn: đọc chương 087"
```

**Tiết Kiệm:** ~20-30% tokens/request (100-150 tokens)

**Cách Thực Hiện:**
- Luôn hỏi grep trước
- Dùng từ khóa: `grep [tag/từ khóa] index.md`
- Sau khi thấy kết quả → hỏi tiếp việc cần làm

---

### **Giải Pháp #4: Ưu Tiên File Nhỏ Trước**

**Thứ Tự Đọc (từ nhỏ → lớn):**

1. **`style.md`** (~1KB) ← Phong cách viết
2. **`trang-thai.md`** (~2KB) ← Plot hiện tại
3. **`index.md`** (~5KB) ← Tóm tắt 127 chương (grep)
4. **`arc/arcX-summary.md`** (~10-15KB) ← Tóm tắt arc
5. **`nhan-vat/XXX.md`** (~8-12KB) ← Hồ sơ nhân vật
6. **`the-gioi/XXX.md`** (~10-20KB) ← Lore thế giới
7. **`chuong/XXX.md`** (~20-40KB) ← Chương gốc ⛔ CUỐI CÙNG

**Quy Tắc:**
- Câu hỏi về phong cách? → `style.md` (ĐỪNG đọc chương gốc)
- Câu hỏi về hiện trạng? → `trang-thai.md` (ĐỪNG grep)
- Câu hỏi về nhân vật? → Hồ sơ nhân vật (ĐỪNG đọc chương)
- Câu hỏi về lore? → `the-gioi/` file (ĐỪNG đọc arc)

**Tiết Kiệm:** ~15-25% tokens/request (75-125 tokens)

**Cách Thực Hiện:**
- AI tự quyết định file nhỏ nhất thích hợp
- Chỉ leo thang đến file lớn hơn nếu thông tin chưa đủ
- Ví dụ: Nếu hồ sơ nhân vật có đủ info → KHÔNG đọc chương gốc

---

### **Giải Pháp #5: Chỉ Dùng Chuong/ Cuối Cùng**

**Quy Tắc:**
- `chuong/XXX.md` là file **LỚNHẤT** (20-40KB) → chỉ dùng khi thực sự cần
- Đây là bước cuối cùng nếu arc summary + hồ sơ nhân vật chưa đủ

**Không Tốt:**
```
"Đọc chương 050 để tìm hiểu về cách Cường dùng Ý Chí Đế Vương"
→ Đọc 40KB chỉ để tìm 1 đoạn text
```

**✅ ĐÚNG:**
```
"Hồ sơ Cường nói gì về Ý Chí Đế Vương?"
[Đọc nhan-vat/luu-chi-cuong.md → ~10KB, đầy đủ thông tin]
[Nếu cần chi tiết cách dùng trong trận đấu cụ thể]
"Đọc chương 050 để xem chi tiết cách sử dụng"
```

**Tiết Kiệm:** ~30-40% tokens/request (150-200 tokens)

**Cách Thực Hiện:**
- AI dừng lại ở `nhan-vat/` hoặc `arc/` nếu đủ info
- Chỉ "leo thang" lên `chuong/` khi user chỉ định hoặc khi cần chi tiết cực kỳ cụ thể

---

## 📋 Checklist Tự Động

**Mỗi Request, AI phải Tự Kiểm Tra:**

- [ ] **Có lặp lại nội dung request trước không?** → Loại bỏ nó
- [ ] **Có batch được 2-3 task liên quan không?** → Gộp thành 1
- [ ] **Cần grep trước không?** → Hỏi grep trước đọc
- [ ] **File nhỏ nào có thể đáp ứng không?** → Dùng file nhỏ trước
- [ ] **Có cần chuong/ không?** → Chỉ dùng nếu thực sự cần

---

## 🎬 Ví Dụ Áp Dụng

### **Ví Dụ 1: Tìm Kiếm Nhân Vật**

❌ **Cách lãng phí:**
```
"Tôi muốn biết Tuyết Nhi là ai, hành động của cô ở các chương nào,
Gift của cô là gì, và cô có liên quan gì với Lục Quỷ Đế.
Hãy đọc toàn bộ chương gốc liên quan và tóm tắt."
```
→ Đọc 10+ chương gốc (400+ KB)

✅ **Cách tối ưu:**
```
Request 1: "Grep '#tuyetnhi' index.md để xem chương nào có Tuyết Nhi"
[Xem kết quả: Ch.020, 087, 105, ...]

Request 2: "Đọc nhan-vat/tuyet-nhi.md"
[Xem hồ sơ → Đã có Gift, lịch sử, liên quan Lục Quỷ Đế]

Request 3 (nếu cần): "Đọc arc5-summary.md để hiểu bối cảnh Arc 5 của Tuyết Nhi"
```
→ Tổng cộng: 5 + 12 + 15 = 32 KB (tiết kiệm 90%!)

---

### **Ví Dụ 2: Viết Chương Mới**

❌ **Cách lãng phí:**
```
"Tôi muốn viết chương tiếp theo. Trước hết đọc
10 chương gần nhất để xem phong cách,
sau đó đọc hồ sơ tất cả nhân vật,
rồi đọc lore, rồi mới viết."
```
→ Đọc 200+ KB trước khi viết

✅ **Cách tối ưu:**
```
Request 1: "Đọc style.md"
[Xem phong cách viết]

Request 2: "Đọc trang-thai.md"
[Xem vị trí nhân vật hiện tại]

Request 3: "Viết chương 128 với phong cách trên"
```
→ Tổng cộng: 1 + 2 + [viết] = 3 KB (+ writing time)

---

### **Ví Dụ 3: Cập Nhật KB**

❌ **Cách lãng phí:**
```
Request 1: "Cập nhật index.md và trang-thai.md và arc7-summary.md"
→ Đọc 3 file để modify
```

✅ **Cách tối ưu:**
```
Request 1: "Cập nhật index.md: Ch.128 [nội dung]"
Request 2: "Cập nhật trang-thai.md: vị trí mới"
Request 3: "Cập nhật arc7-summary.md: thêm sự kiện"
Request 4: "Push lên git"
```
→ Tách rõ, dễ track, dễ commit

---

## 🚀 Kích Hoạt & Hiệu Lực

**Trạng Thái:** ✅ **ACTIVE từ 2026-03-23**

**Ai Kích Hoạt:** Cuong (user)

**Phạm Vi:** Tất cả request trong Cowork session này và các session tiếp theo (cho đến khi có update mới)

**Cách Kiểm Chứng:**
- Nếu user hỏi "bạn tuân theo 5 giải pháp chưa?" → AI phải trả lời "Có, đã tuân theo từ request này"
- Nếu user thấy AI không tuân theo → User có quyền nhắc "Làm theo giải pháp #X"

---

## 📝 Ghi Chú & Ngoại Lệ

**Khi KHÔNG cần Tuân Theo:**
- Nếu user **YÊUHÀNG chỉ định** (VD: "Đọc chương 050 cho dù có arc summary")
- Nếu **context quá nhỏ** (VD: chỉ có 1 chương gốc duy nhất)
- Nếu **emergency/urgent** (VD: "Nhanh lên, cần ngay")

**Khi CÓ THỂ Linh Hoạt:**
- Nếu request quá phức tạp → Có thể tách thành 2-3 sub-request (vẫn tuân theo)
- Nếu batch request > 3 task → Có thể tách thành 2 batch (vẫn tuân theo)

**Không Bao Giờ Vi Phạm:**
- ❌ Không bao giờ đọc `chuong/` khi `nhan-vat/` đã đủ
- ❌ Không bao giờ lặp lại context cũ (trừ khi user yêu cầu tóm tắt)
- ❌ Không bao giờ quên grep `index.md` khi tìm kiếm

---

## ✅ Xác Nhận Áp Dụng

**AI xác nhận tuân theo 5 Giải Pháp từ:**
- ✅ Giải Pháp #1: Không include chat cũ
- ✅ Giải Pháp #2: Batch request liên quan
- ✅ Giải Pháp #3: Grep trước, đọc sau
- ✅ Giải Pháp #4: Ưu tiên file nhỏ
- ✅ Giải Pháp #5: Chỉ dùng chuong/ cuối cùng

**Hiệu Lực:** 2026-03-23 trở đi

**Mục Tiêu:** Tiết kiệm **25-30% tokens/session** so với quy trình bình thường

---

**CUONG, CÓ CÂU HỎI GÌ VỀ QUY TRÌNH NÀY KHÔNG?**
