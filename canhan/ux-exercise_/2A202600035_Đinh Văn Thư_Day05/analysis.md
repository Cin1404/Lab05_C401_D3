# UX exercise — MoMo Moni AI

**Sản phẩm:** MoMo — Trợ thủ AI Moni (Phân loại chi tiêu + Chatbot tài chính)

## Phần 1 — Khám phá (trước khi dùng)

**Marketing hứa gì?**

- Trang chính thức MoMo (momo.vn/tro-thu-tai-chinh) và App Store/Play Store mô tả Moni là **“Trợ thủ AI quản lý chi tiêu”**: “Chỉ cần chat, AI ghi chép hộ khoản chi”, “Tự động phân loại chi tiêu”, “Nhắc nhở tránh chi tiêu quá tay”, “Biến chuyện khó thành chuyện nhẹ nhàng”.
- Hứa hẹn: AI thông minh, cá nhân hóa, giúp người dùng quản lý tiền dễ dàng hơn, tiết kiệm thời gian, hiểu thói quen chi tiêu của user.

**Dùng thử thực tế (trong app MoMo phiên bản 2026):**

- Tính năng chính: Auto-tag category cho mọi giao dịch (QR, chuyển tiền, thanh toán hóa đơn…).
- Có giao diện chat riêng với Moni (voice/text) để ghi chi tiêu thủ công hoặc hỏi tư vấn tài chính.
- Báo cáo tháng hiển thị biểu đồ chi tiêu theo category do AI phân loại.

## Phần 2 — Phân tích 4 paths

### 1. Khi AI **đúng**

- User chi 50k tại Circle K → Moni tự tag “Ăn uống” ngay lập tức.
- User thấy: icon category + tên danh mục xuất hiện rõ trong chi tiết giao dịch và báo cáo.
- Hệ thống confirm: không hỏi thêm, chỉ highlight tag và cho nút “Chỉnh sửa” nhỏ (không bắt buộc).
- Value moment rất rõ, user cảm thấy “AI hiểu mình”.

### 2. Khi AI **không chắc**

- User chuyển tiền 200k cho bạn hoặc giao dịch lạ (mua online quốc tế, chi phí y tế…) → Moni thường tag “Khác” hoặc không tag gì.
- Hệ thống xử lý: im lặng (không hiện gợi ý), user phải tự vào chỉnh.
- Không có thông báo “Confidence thấp – bạn muốn phân loại không?” hay gợi ý alternatives.
- User phải chủ động mở chi tiết giao dịch để sửa.

### 3. Khi AI **sai**

- User mua sách trên Shopee → Moni tag “Mua sắm” thay vì “Học tập / Sách vở”.
- User biết sai khi xem báo cáo tháng (không có thông báo realtime).
- Cách sửa:
  1. Vào “Lịch sử giao dịch”
  2. Chọn giao dịch
  3. Nhấn “Chỉnh sửa” → chọn category mới
- Tổng cộng **3–4 bước**, không có nút nhanh “Sửa category” ngay trong báo cáo.
- Không có confirm “AI đã học từ lần sửa này” hoặc “Lần sau sẽ chính xác hơn”.

### 4. Khi user **mất tin**

- Sau 4–5 lần tag sai liên tục (đặc biệt giao dịch chuyển tiền, phí dịch vụ), user ngừng tin báo cáo chi tiêu tự động.
- Không có **exit/opt-out** rõ ràng (không tìm thấy nút “Tắt auto-tag” hoặc “Chuyển sang tag thủ công toàn bộ”).
- Fallback: chỉ có cách sửa thủ công từng giao dịch hoặc chat với Moni hỏi “Tại sao tag sai?” (nhưng Moni không sửa được history).
- User dễ bỏ luôn tính năng, chuyển sang ghi chi tiêu thủ công.

## Path nào xử lý tốt nhất? Tại sao?

**Path 1 (AI đúng)** → xử lý **tốt nhất**.  
UI mượt, value moment xuất hiện ngay, không làm phiền user. Đây là điểm mạnh nhất của Moni, giúp user cảm thấy “AI hữu ích”.

## Path nào yếu nhất hoặc không tồn tại?

**Path 3 (AI sai) + Path 4 (user mất tin)** là **yếu nhất**.

- Recovery flow dài, không graceful failure.
- Không có confidence score, không giải thích lý do tag, không có feedback loop rõ ràng (user sửa nhưng không biết AI có học không).
- Không có fallback về con người hoặc chế độ “manual first”.

## Gap giữa marketing và thực tế

- **Marketing:** “Trợ thủ AI thông minh”, “tự động phân loại”, “hiểu bạn”, “quản lý chi tiêu dễ dàng”.
- **Thực tế:** Auto-tag chỉ chính xác cao với giao dịch quen thuộc (~70-80%). Edge case (chuyển tiền, chi phí phức tạp) thường sai hoặc tag “Khác”. Không có cơ chế sửa nhanh, không visible learning, không confidence → user nhanh mất niềm tin.
- **Gap lớn nhất:** Marketing không đề cập đến uncertainty của AI. User kỳ vọng 100% chính xác nhưng thực tế phải sửa tay rất nhiều → dễ gây frustration.

## Sketch “Làm tốt hơn” (chọn path yếu nhất: Path 3 + 4)

- **As-is (bên trái):** Giao dịch → Auto-tag → Xem báo cáo → Phát hiện sai → 3–4 bước sửa thủ công → Không feedback loop.
- **To-be (bên phải):**
  - Thêm confidence score (low → highlight vàng + nút “Bạn muốn chỉnh không?”).
  - Nút “Sửa nhanh” 1-tap ngay trong báo cáo.
  - Sau khi user sửa → AI hiện “Cảm ơn! Moni đã học và sẽ chính xác hơn lần sau”.
  - Có toggle “Tắt auto-tag” hoặc “Manual mode” dễ tìm trong settings.

_(Ảnh sketch.jpg hoặc sketch.pdf đính kèm trong thư mục ux-exercise/)_

**Nice to have:** Tôi đã chụp và annotate 4 screenshot màn hình (chi tiết giao dịch, báo cáo tháng, chat Moni, phần chỉnh sửa) → xem trong thư mục `extras/screenshots/` nếu cần.

---

**Hoàn thành ngày 08/04/2026**
