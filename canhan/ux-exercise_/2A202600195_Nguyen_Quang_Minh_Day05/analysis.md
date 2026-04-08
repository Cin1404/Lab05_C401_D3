# UX Exercise — MoMo Moni AI

## Sản phẩm
MoMo — Moni AI Assistant  
AI feature: Tự động phân loại chi tiêu + chatbot tài chính

---

## Phần 1 — Khám phá

### Marketing promise
- Moni được quảng bá là “trợ lý tài chính thông minh”
- Tự động:
  - Phân loại chi tiêu
  - Hiểu hành vi người dùng
  - Đưa ra insight & gợi ý tiết kiệm
- Kỳ vọng:
  → Không cần chỉnh tay (fully automated)
  → Báo cáo chi tiêu chính xác

---

### Thực tế sử dụng
- Auto-tag hoạt động tốt với:
  - Thanh toán offline (ăn uống, siêu thị)
- Nhưng yếu với:
  - Chuyển khoản (P2P)
  - Mua online (Shopee, Lazada)

- UI:
  - Hiển thị category ngay
  - Không có confidence level
  - Không hỏi user khi không chắc
  - Không rõ AI có học từ chỉnh sửa không

---

## Phần 2 — Phân tích 4 paths

### 1. Khi AI đúng
- Ví dụ: Thanh toán 45k tại Highlands → tag “Ăn uống”
- User thấy:
  - Category hiển thị ngay
  - Không cần làm gì thêm

- UX:
  - Nhanh, mượt (zero friction)
  - Nhưng không có feedback reinforce trust

→ Đánh giá: Tốt về speed, yếu về trust-building

---

### 2. Khi AI không chắc
- Ví dụ: Chuyển khoản 200k cho bạn

- Thực tế:
  - Không tag hoặc tag “Khác”
  - Không hỏi user

- User phải:
  - Tự vào chỉnh nếu muốn

- Vấn đề:
  - Không có suggestion
  - Không có clarification question
  - AI im lặng → giống như không tồn tại

→ Đánh giá: Path này rất yếu

---

### 3. Khi AI sai
- Ví dụ:
  - Mua sách → bị tag “Mua sắm” thay vì “Học tập”

- User sửa:
  1. Mở transaction
  2. Click edit
  3. Chọn lại category

- Issues:
  - 3 bước → friction cao
  - Không có feedback “AI đã học”
  - Không có explain vì sao sai

→ User không biết sửa có giúp hệ thống improve không

→ Đánh giá: Recovery tồn tại nhưng yếu

---

### 4. Khi user mất niềm tin
- Sau nhiều lần sai:
  - User không tin báo cáo

- Nhưng:
  - Không có:
    - Nút tắt auto-tag
    - Chế độ manual
    - Fallback rõ ràng

→ User bị kẹt trong hệ thống AI

→ Đánh giá: Path này gần như không tồn tại

---

## Tổng kết 4 paths

| Path | Đánh giá |
|------|--------|
| AI đúng | Tốt |
| AI không chắc | Rất yếu |
| AI sai | Trung bình |
| User mất tin | Không có |

→ Path yếu nhất: 2 và 4

---

## Gap: Marketing vs Reality

### Marketing
- “AI thông minh”
- “Tự động quản lý chi tiêu”
- Ngầm hiểu: chính xác cao

### Reality
- Accuracy chỉ tốt với case phổ biến
- Edge cases xử lý kém
- Không có UX cho uncertainty

### Gap lớn nhất
→ Marketing assume AI luôn đúng  
→ Product không xử lý AI sai

---

## Phần 3 — Sketch (mô tả)

### AS-IS

Transaction xảy ra  
→ Auto-tag (không explain)  
→ User thấy category  

Nếu sai:  
→ Vào detail → edit → save (3 bước)  

→ Kết thúc (không feedback loop)

**Breaking points:**
- Không có confidence
- Không hỏi khi unsure
- Không learning signal visible

---

### TO-BE

Transaction xảy ra  
→ Auto-tag + confidence  

Nếu confidence thấp:  
→ Hiện prompt:  
"Bạn muốn phân loại giao dịch này?"  
→ 3 options + skip  

Nếu user sửa:  
→ Hiện: "Đã ghi nhận — lần sau sẽ chính xác hơn"  

→ Dashboard hiển thị:
- AI accuracy
- Số lần user chỉnh sửa

---

## Thay đổi đề xuất

### Thêm
- Confidence indicator
- Suggestion UI khi unsure
- Feedback sau correction
- Accuracy dashboard

### Bớt
- Silent auto-tag

### Đổi
- Từ automation hoàn toàn  
→ Sang AI hỗ trợ (augmentation)

---

## Insight chính

AI product không fail vì model  
→ Fail vì UX không xử lý uncertainty

MoMo:
- Optimize cho AI đúng
- Bỏ qua AI sai / không chắc / mất niềm tin

---

## Kết luận

Moni không phải AI yếu  
→ Vấn đề là UX chưa thiết kế cho AI sai