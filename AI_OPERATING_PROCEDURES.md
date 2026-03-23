# AI Operating Procedures — Dự án Dị Biến Thế Giới

> **TÀI LIỆU NỘI BỘ:** Các quy tắc hoạt động tự động mà AI phải tuân theo trong mọi session làm việc với dự án này.

**Ngày Có Hiệu Lực:** 2026-03-23
**Phiên Bản:** 1.0
**Trạng Thái:** ✅ ACTIVE (Cuong kích hoạt)

---

## 🎯 9 Giải Pháp Tiết Kiệm Token + Data Integrity — BẮTBUỘC

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

### **Giải Pháp #6: Ghi File, Show Brief Status**

**Quy Tắc:**
- Tất cả response **DÀI** (> 500 từ hoặc xử lý phức tạp) → **ghi vào file**
- Chat chỉ show: "✅ Success" + link file + small note
- Giúp tiết kiệm tokens display (response dài = nhiều tokens)

**Không Tốt:**
```
Request: "Phân tích Arc 5"
Response: [2000 từ analysis trực tiếp trong chat]
→ 2000 từ = ~500-800 tokens display
```

**✅ ĐÚNG:**
```
Request: "Phân tích Arc 5 và lưu vào file"
Response: "✅ Analysis saved: `arc5-analysis.md`
📝 Tóm tắt: Arc 5 là giai đoạn Tân Việt xuất hiện..."
```

**Tiết Kiệm:** ~10-20% tokens/request (nếu response dài)

**Cách Thực Hiện:**
- Response > 500 từ → tự động ghi file
- File được lưu trong workspace (`/outputs/` hoặc project folder)
- Chat show: status + link + 1-2 dòng summary
- User có thể đọc file đầy đủ sau

---

### **Giải Pháp #7: Combine Dependent Tasks**

**Quy Tắc:**
- Task **CÓ LIÊN QUAN & PHỤ THUỘC** → 1 request duy nhất (sequential)
- Task **KHÔNG LIÊN QUAN** → tách request riêng
- Ví dụ: "Grep → analyze → write" = 1 request (tasks sequential)
- Ví dụ: "Viết chương" + "Cập nhật index.md" = 2 request (không liên quan)

**Không Tốt:**
```
Request 1: "Grep '#cuong' index.md"
Request 2: "Phân tích Cường"
Request 3: "Viết cảnh Cường trong Ch.128"
→ 3 request, mỗi request header + context setup
```

**✅ ĐÚNG:**
```
Request 1: "Grep '#cuong' index.md, sau đó phân tích Cường,
rồi viết cảnh Cường trong Ch.128"
→ 1 request, tasks sequential
→ Grep result → reuse cho Analyze → reuse cho Write
```

**Tiết Kiệm:** ~5-15% tokens/session (chỉ khi tasks dependent)

**Cách Thực Hiện:**
- Trước khi request → kiểm tra: "Task này phụ thuộc vào task trước không?"
- Nếu YES: Combine thành 1 request (dùng "sau đó", "rồi")
- Nếu NO: Tách request riêng

---

### **Giải Pháp #8: Data Integrity Priority + Smart Data Loading (QUAN TRỌNG)**

**BƯỚC 0 - KIỂM TRA LIÊN QUAN (Filter Không Cần Load):**

**Trước khi load bất kỳ file nào, hỏi:**
- ❓ Câu hỏi này có **liên quan trực tiếp** đến nội dung dữ liệu truyện không?

**Ví Dụ KHÔNG Cần Load:**
- "Viết 1 bài luận về tiểu thuyết web" → Không liên quan → ❌ Không load
- "Tiểu thuyết web là gì?" → Kiến thức chung → ❌ Không load
- "Phong cách viết nên như thế nào?" → Kiến thức viết chung → ❌ Không load (trừ khi hỏi cụ thể về style.md)
- "Hãy tạo bảng thống kê nhân vật" → Không yêu cầu verify dữ liệu gốc → ❌ Có thể không load

**Ví Dụ CẦN Load:**
- "Cường là ai?" → Liên quan nhân vật → ✅ Load nhan-vat/
- "Arc 5 xảy ra gì?" → Liên quan nội dung → ✅ Load arc-summary (hoặc chuong/ để verify)
- "Tuyết Nhi có Gift gì?" → Liên quan dữ liệu → ✅ Load nhan-vat/tuyet-nhi
- "Phát hiện lỗi ở chương X" → Verify dữ liệu → ✅ Load chuong/XXX

**Quy Tắc Phân Cấp Dữ Liệu:**

| Cấp Độ | File | Vai Trò | Độ Tin Cậy |
|--------|------|--------|-----------|
| 🔴 **PRIMARY** | `chuong/001-127.md` | **Nguồn chân lý duy nhất** | 100% ✅ |
| 🟡 **SECONDARY** | arc-summary, nhan-vat, the-gioi | Bổ sung, cross-check | ~80-90% |
| 🟢 **OPTIONAL** | style, trang-thai, index | Tham khảo nhanh | ~70-80% |

**Quy Tắc Xử Lý Mâu Thuẫn (Phá Vỡ #5 Khi Cần):**

**🔴 DEFAULT (Tuân Thủ #5):**
- Mặc định KHÔNG load `chuong/` để tiết kiệm token (per Giải Pháp #5)
- Dùng arc-summary, nhan-vat, the-gioi là đủ

**🚨 EXCEPTION (Phá Vỡ #5 → Dùng #8):**
- **NẾU** phát hiện **mâu thuẫn logic** giữa files (arc-summary vs nhan-vat vs chuong/)
- **HOẶC** user yêu cầu "xác minh tính chính xác 100%"
- **THÌ** AI được phép **lập tức phá vỡ Giải Pháp #5** → Load file gốc trong `chuong/` để trọng tài

**Ưu Tiên:**
```
Token Savings (#5) ← DEFAULT
        ↓
[Phát hiện mâu thuẫn HOẶC user request verify?]
        ↓
Data Integrity (#8) ← OVERRIDE (quality > cost)
```

**Không bao giờ sửa `chuong/`:**
- Không bao giờ sửa `chuong/` dựa trên file khác
- Khi phát hiện mâu thuẫn → báo user & sửa file non-chuong/ tự động

**Khi Nào PHẢI Load `chuong/` (Override #5):**
- ✅ User yêu cầu "xác minh 100%" / "verify accuracy" (explicit request)
- ✅ Phát hiện **mâu thuẫn logic giữa files** (arc-summary vs nhan-vat vs chuong/)
- ✅ Cập nhật/sửa KB → check `chuong/` trước (source of truth)
- ✅ Phân tích chi tiết Arc → load chapters liên quan làm nền tảng
- ⚠️ **EXCEPTION:** Các trường hợp trên được phép phá vỡ Giải Pháp #5 vì quality > token cost

**Khi Nào KHÔNG cần Load `chuong/`:**
- ❌ Chỉ cần overview/tóm tắt → dùng arc-summary + nhan-vat là đủ
- ❌ Token budget cực hạn → dùng file tóm tắt (đầu tiên)
- ❌ **Câu hỏi KHÔNG liên quan dữ liệu truyện** → KHÔNG load bất cứ file nào

**Tiết Kiệm:** ~5-10% tokens (bằng cách không load file khi không cần)

**Cách Thực Hiện:**
- **TRƯỚC:** Kiểm tra "Liên quan dữ liệu truyện không?" → Nếu NO → trả lời trực tiếp
- **Nếu YES:** Tiếp tục load file theo Giải Pháp #8
- Luôn xác nhận dữ liệu bằng `chuong/` khi có nghi ngờ
- Load chapters liên quan khi viết phân tích chi tiết
- Báo user nếu phát hiện lỗi trong file non-chuong/

---

### **Giải Pháp #9: Smart Escalation (Leo Thang Thông Minh)**

**Vấn Đề:**
- Giải Pháp #4 nói "ưu tiên file nhỏ" nhưng không nói khi file nhỏ **không đủ thông tin chi tiết** thì làm gì
- Nếu không leo thang → câu trả lời thiếu, không hữu ích
- Nếu tự động leo thang → vi phạm #5, tiêu tốn token không cần

**Giải Pháp: Leo Thang Có Điều Kiện**

**BƯỚC 1: Phân Loại Câu Hỏi**
| Loại | Ví Dụ | Hành Vi |
|------|-------|--------|
| **Tổng Quan** | "Tuyết Nhi là ai?", "Arc 5 nói gì?" | ✅ KHÔNG leo thang – file nhỏ đủ |
| **Chi Tiết Cụ Thể** | "Gift của Tuyết Nhi hoạt động thế nào?", "Lời thoại chính xác là gì?" | ✅ CÓ THỂ leo thang nếu cần |
| **Verify/Compare** | "Kiểm tra xem có đúng không?", "So sánh hai chương" | ✅ BUỘC leo thang (per #8) |

**BƯỚC 2: Đánh Giá "Thông Tin Đủ Hay Không?"**
Sau khi đọc file nhỏ, kiểm tra:
- ✅ File có trả lời rõ ràng câu hỏi không? → **Dừng, đủ rồi**
- ❌ Thông tin mơ hồ/chung chung nhưng câu hỏi yêu cầu chi tiết? → **Xem xét leo thang**
- ❌ File không có thông tin liên quan? → **Phải leo thang**

**Ví dụ:**
- Hỏi "Tuyết Nhi có Gift gì?" + File có "Gift: Băng Linh" → Đủ, dừng
- Hỏi "Cách Tuyết Nhi dùng Băng Linh trong trận chiến?" + File chỉ nêu tên → Cần leo thang

**BƯỚC 3: Leo Thang Có Kiểm Soát**
Nếu quyết định leo thang:

1. **Báo user** (minh bạch token):
   ```
   "Thông tin trong hồ sơ chưa đủ chi tiết.
   Tôi sẽ tra trong arc summary để có câu trả lời đầy đủ."
   ```

2. **Tuân thủ thứ tự #4** khi leo thang:
   - Thử `arc-summary` trước
   - Chỉ lên `chuong/` nếu arc cũng không đủ

3. **Nếu phải dùng `chuong/`:**
   - KHÔNG đọc toàn bộ file (~40KB)
   - Dùng **grep trước** để định vị đoạn cần
   - Chỉ đọc đoạn liên quan (~2-5KB)

**Không Leo Thang Nếu:**
- ❌ Câu hỏi chỉ cần tổng quan, file nhỏ đã đủ
- ❌ User có thói quen chấp nhận thông tin cơ bản
- ❌ Token budget rất tight (user nhắc "tiết kiệm tối đa")

**Tiết Kiệm:** ~5-15% tokens (tránh đọc full file khi chỉ cần đoạn nhỏ)

**Cách Thực Hiện:**
- Phân loại câu hỏi theo bảng trên
- Đánh giá thông tin từ file nhỏ
- Nếu cần, leo thang có báo cáo + chỉ đọc đoạn cần
- Không tự động leo thang chỉ vì "file ngắn"

---

## 📋 Checklist Tự Động

**Mỗi Request, AI phải Tự Kiểm Tra (Theo Thứ Tự Ưu Tiên):**

**🔴 PRIORITY 0 - FILTER & QUALITY:**
- [ ] **Câu hỏi có liên quan dữ liệu truyện không?** → Nếu NO → Trả lời trực tiếp, KHÔNG load file
- [ ] **Phát hiện mâu thuẫn hoặc user yêu cầu verify?** → Override tất cả, load `chuong/` (#8 PRIORITY)

**🟡 PRIORITY 1 - OPTIMIZATION (Nếu CÓ liên quan):**
- [ ] **Có lặp lại nội dung request trước không?** → Loại bỏ nó (#1)
- [ ] **Có batch được 2-3 task liên quan không?** → Gộp thành 1 (#2)
- [ ] **Cần grep trước không?** → Hỏi grep trước đọc (#3)
- [ ] **File nhỏ nào có thể đáp ứng không?** → Dùng file nhỏ trước (#4)
- [ ] **File nhỏ chứa đủ thông tin chưa, hay cần leo thang?** → Phân loại câu hỏi, leo thang nếu cần (#9)
- [ ] **Có cần chuong/ không?** → Chỉ dùng nếu thực sự cần (#5)
- [ ] **Response sẽ dài > 500 từ không?** → Ghi file, show summary (#6)
- [ ] **Có task liên tiếp phụ thuộc không?** → Combine thành 1 request (#7)

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

### **Ví Dụ 3: Cập Nhật KB & Push Git**

❌ **Cách lãng phí (Chia nhỏ request):**
```
Request 1: "Cập nhật index.md"
Request 2: "Cập nhật trang-thai.md"
Request 3: "Cập nhật arc7-summary.md"
Request 4: "Push lên git"
```
→ 4 request = 4x context loading overhead, AI tốn phí "nổ máy" 4 lần

✅ **Cách tối ưu (Sequential Dependent per #7):**
```
Request 1 (ONLY ONE): "Thực hiện chuỗi tác vụ sau:
1. Cập nhật index.md: Ch.128 [nội dung]
2. Cập nhật trang-thai.md: vị trí mới
3. Cập nhật arc7-summary.md: thêm sự kiện
4. Git push và báo lại trạng thái"
```
→ 1 request = AI gọi tool liên tiếp (edit file 1 → file 2 → file 3 → git push) trong 1 chu kỳ suy nghĩ. Chỉ trả phí 1 lần context loading. (Giải Pháp #7: Combine Dependent Tasks)

---

## 🚀 Kích Hoạt & Hiệu Lực

**Trạng Thái:** ✅ **ACTIVE từ 2026-03-23**

**Ai Kích Hoạt:** Cuong (user)

**Phạm Vi:** Tất cả request trong Cowork session này và các session tiếp theo (cho đến khi có update mới)

**Cách Kiểm Chứng:**
- Nếu user hỏi "bạn tuân theo 7 giải pháp chưa?" → AI phải trả lời "Có, đã tuân theo từ request này"
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

**AI xác nhận tuân theo 9 Giải Pháp từ:**
- ✅ Giải Pháp #1: Không include chat cũ
- ✅ Giải Pháp #2: Batch request liên quan
- ✅ Giải Pháp #3: Grep trước, đọc sau
- ✅ Giải Pháp #4: Ưu tiên file nhỏ
- ✅ Giải Pháp #5: Chỉ dùng chuong/ cuối cùng
- ✅ Giải Pháp #6: Ghi file, show brief status
- ✅ Giải Pháp #7: Combine dependent tasks
- ✅ Giải Pháp #8: Data Integrity Priority (**bảo đảm quality**)
- ✅ Giải Pháp #9: Smart Escalation (**đáp ứng nhu cầu chi tiết**)

**Hiệu Lực:** 2026-03-23 trở đi (Cập nhật: Thêm #9 + Checklist Priority Reorder)

**Mục Tiêu:** Tiết kiệm **30-45% tokens/session** + **100% data accuracy** + **linh hoạt đáp ứng nhu cầu**

---

---

**Cập Nhật: 2026-03-23 Thêm Giải Pháp #6, #7, #8, #9 (Hoàn Chỉnh SOP)**
- Tổng tiết kiệm: **30-45% tokens/session** (filter + smart escalation)
- Data accuracy: **100% (chuong/ là source of truth)**
- Smart loading: **Không load nếu không liên quan + Leo thang thông minh khi cần chi tiết**
- Checklist: **Reorder priority (#8 check ngay sau filter, trước tất cả #1-7)**
- Từ giờ AI sẽ tự động áp dụng **9 giải pháp** (đầy đủ + linh hoạt)
