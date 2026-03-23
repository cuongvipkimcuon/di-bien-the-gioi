# Hướng dẫn Tiết Kiệm Token Usage — Dự án Dị Biến Thế Giới

> **TỔNG QUAN:** Haiku 4.5 là model nhỏ nhất, tiết kiệm nhất (~40% tokens so với Sonnet). File đã được chia nhỏ là tối ưu rồi. Đây là hướng dẫn chi tiết để **tiết kiệm usage tối đa** khi làm việc với KB.

---

## 🎯 Haiku vs Các Model Khác

| Model | Cỡ | Token Efficiency | Dùng khi nào |
|-------|-----|------------------|------------|
| **Haiku 4.5** | Nhỏ | ✅ 40-50% tokens | **Tìm kiếm, tra cứu, grep, phân tích nhỏ — DÙNG CHÍNH** |
| Sonnet 4.6 | Vừa | 70-80% tokens | Viết chương phức tạp, sáng tạo, reasoning sâu |
| Opus 4.6 | Lớn | 100% tokens | Chỉ cần khi Haiku không xử lý được |

**✅ KHUYÊN:** Giữ Haiku làm mặc định. Chuyển Sonnet chỉ khi cần.

---

## ⚡ Quy Tắc Tiết Kiệm #1: KHÔNG Include Chat Cũ

**TỐI QUAN TRỌNG:** Mỗi request mới, **KHÔNG cần include lại nội dung từ message trước đó** trừ khi bạn muốn tham chiếu.

### ❌ HÀNH VI SAI (Dùng nhiều token):
```
Request 1: "Tìm chương có Tuyết Nhi"
[Claude trả lời, list các chương]

Request 2: "OK, tôi vừa hỏi tìm chương có Tuyết Nhi.
Bây giờ hãy tóm tắt arc 5 để tôi hiểu bối cảnh"
```
❌ Request 2 lặp lại "tôi vừa hỏi tìm chương Tuyết Nhi" → **lãng phí ~30-50 tokens**

### ✅ HÀNH VI ĐÚNG (Tiết kiệm token):
```
Request 1: "Tìm chương có Tuyết Nhi"
[Claude trả lời]

Request 2: "Tóm tắt arc 5 để hiểu bối cảnh"
```
✅ **Gọn gàng, chat tự giữ context** → tiết kiệm ~30-50 tokens/request

---

## ⚡ Quy Tắc Tiết Kiệm #2: Chỉ Request File Cần Thiết

**KHÔNG hỏi:** "Đọc chương 050 và chương 051 và chương 052 để so sánh"
**HÃY HỎI:** "So sánh phong cách viết Ch.050 vs Ch.051" → Claude tự grep + đọc

**KHÔNG hỏi:** "Cập nhật hồ sơ Cường, Thảo, và Nghĩa"
**HÃY HỎI:** "Cập nhật hồ sơ Cường" (xong) → sau đó "Cập nhật Thảo"

→ **Tách request = dễ chia task, không overlap file đọc**

---

## ⚡ Quy Tắc Tiết Kiệm #3: Dùng Grep Trước, Đọc File Sau

### Cách cấu trúc request:
```
1. "Grep index.md để tìm chương có [từ khóa]"
2. [Xem kết quả grep]
3. "Đọc chương XXX để chi tiết"
```

**Không cần hỏi:** "Tìm tất cả chương có Tuyết Nhi + tóm tắt từng chương"
**Hãy hỏi:** "Grep '#tuyetnhi' trên index.md"
→ **Sau khi thấy kết quả → hỏi chi tiết chương nào cần**

---

## ⚡ Quy Tắc Tiết Kiệm #4: Ưu Tiên Đọc File Nhỏ

### Thứ tự độ ưu tiên (từ nhỏ → lớn):
1. `style.md` → ~1KB (phong cách viết)
2. `trang-thai.md` → ~2KB (plot hiện tại)
3. `index.md` → ~5KB (tóm tắt 127 chương)
4. `arc/arcX-summary.md` → ~10-15KB (tóm tắt arc)
5. `nhan-vat/XXX.md` → ~8-12KB (hồ sơ nhân vật)
6. `the-gioi/XXX.md` → ~10-20KB (lore)
7. `chuong/XXX.md` → ~20-40KB (chương gốc — **CUỐI CÙNG**)

**Rule:** Khi hỏi vấn đề, đọc file nhỏ trước. Chỉ lên `chuong/` khi không đủ thông tin.

---

## ⚡ Quy Tắc Tiết Kiệm #5: Batch Request Khi Có Liên Quan

### ❌ KHÔNG HIỆU QUẢ:
```
Request 1: "Grep '#cuong' trên index.md"
Request 2: "Grep '#thao' trên index.md"
Request 3: "Grep '#tuyetnhi' trên index.md"
```
❌ 3 request riêng lẻ

### ✅ HIỆU QUẢ:
```
Request 1: "Grep index.md theo các tag: #cuong, #thao, #tuyetnhi"
```
✅ 1 request duy nhất → tiết kiệm 2 request

---

## 📋 Checklist Tiết Kiệm Cho Mỗi Session

**Trước khi bắt đầu request:**
- [ ] Không include lại nội dung request cũ (trừ khi cần tham chiếu rõ)
- [ ] Tách request thành chunk nhỏ nếu có nhiều task không liên quan
- [ ] Batch request liên quan thành 1 request
- [ ] Dùng grep trước, đọc file sau
- [ ] Ưu tiên file nhỏ (style → trang-thai → index)
- [ ] Chỉ lên chuong/ khi arc summary chưa đủ

---

## 🔄 Quy Trình Tối Ưu Cho Session

### Session bình thường (tìm kiếm, phân tích):
```
1. "Grep index.md: [từ khóa]"
   ↓
2. [Xem kết quả]
   ↓
3. "Đọc arc/arcX-summary.md"
   ↓
4. [Xem tóm tắt]
   ↓
5. "Đọc nhan-vat/XXX.md để hiểu chi tiết"
   ↓
6. [Nếu còn cần] "Đọc chuong/XXX.md"
```

### Session viết chương mới:
```
1. "Đọc style.md" ← TRƯỚC TIÊN
   ↓
2. [Xem phong cách]
   ↓
3. "Đọc trang-thai.md để biết vị trí nhân vật"
   ↓
4. [Xem vị trí]
   ↓
5. "Viết chương X"
```

### Session cập nhật KB:
```
1. "Cập nhật index.md: Ch.128"
   ↓
2. [Xem cập nhật]
   ↓
3. "Cập nhật nhan-vat/luu-chi-cuong.md"
   ↓
4. "Push lên git"
```

---

## 🎯 Tóm Tắt Chiến Lược

| Tình Huống | Chiến Lược |
|-----------|-----------|
| Tìm kiếm chương | Grep → đọc arc summary → chi tiết nếu cần |
| Hỏi về nhân vật | Đọc hồ sơ nhân vật (không đọc chương gốc) |
| Hỏi về lore | Đọc `the-gioi/` file liên quan |
| Viết chương | Đọc `style.md` → `trang-thai.md` → viết |
| Cập nhật KB | Cập nhật `index.md` trước, sau đó file chi tiết |
| **Tiết kiệm tối đa** | **Grep + file nhỏ + không lặp context + batch request** |

---

## 💡 Bonus: Các Mẹo Khác

1. **Dùng grep option**: `grep -c` để đếm, `grep -n` để xem line number
2. **Từ khóa tìm kiếm**: Dùng tag (#nhân vật, #sự kiện) thay vì tên đầy đủ
3. **Request focused**: Mỗi request = 1 mục đích chính (tìm HOẶC phân tích HOẶC viết)
4. **File cũ**: Nếu giới hạn context, chỉ cần `index.md` + `trang-thai.md`
5. **Git**: Push sau mỗi batch chương (3-5 chương/lần) để không conflict

---

**💪 Goal:** Mỗi session dùng **25-30% ít token** hơn bình thường bằng kỷ luật chia request.
