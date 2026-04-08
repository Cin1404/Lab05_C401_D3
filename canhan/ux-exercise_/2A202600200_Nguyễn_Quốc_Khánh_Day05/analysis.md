Dưới đây là bản khung (template) Markdown giúp bạn hệ thống lại các ý tưởng trước khi đặt bút sketch lên giấy. Tôi sẽ chọn **MoMo — Trợ thủ AI Moni** làm đối tượng phân tích vì đây là sản phẩm có sự thay đổi UI rõ rệt nhất khi tích hợp AI.

---

# PHÂN TÍCH UX AI: TRỢ THỦ MONI (MOMO)

## Phần 1 — Khám phá (15 phút)

### Marketing & Lời hứa
* **Kênh:** Banner trong app, bài PR trên các báo công nghệ, thông báo đẩy (push notification).
* **Lời hứa:** "Quản lý chi tiêu thông minh", "Tự động phân loại giao dịch", "Hỏi đáp tài chính như người thật". Marketing nhấn mạnh vào sự **tiện lợi** và **cá nhân hóa**.

### Trải nghiệm thực tế
* **Điểm chạm UI:** Một biểu tượng Moni đặc trưng (linh vật) xuất hiện ở góc hoặc trong tab "Lịch sử giao dịch".
* **Phản ứng của AI:** Khi thực hiện một giao dịch (ví dụ: chuyển tiền ăn uống), Moni tự động gán nhãn category.
* **Thay đổi UI:** Xuất hiện các bong bóng gợi ý (suggestion chips) để user hỏi nhanh về tổng chi tiêu tháng.

---

## Phần 2 — Phân tích 4 paths (10 phút)

| Path | Trạng thái thực tế tại MoMo (Moni) |
| :--- | :--- |
| **1. Khi AI đúng** | Hệ thống hiển thị icon hạng mục chính xác (Ví dụ: Ăn uống). User thấy hài lòng, không cần thao tác thêm. |
| **2. Khi AI không chắc** | Moni thường sẽ chọn một hạng mục "Chung" hoặc "Khác". Hệ thống không đặt câu hỏi ngược lại mà âm thầm chọn một nhãn an toàn. |
| **3. Khi AI sai** | User phải vào chi tiết giao dịch -> Chọn "Sửa hạng mục". Quy trình mất khoảng 3 chạm (tap). Ít có thông báo "Tôi có phân loại sai không?" |
| **4. Khi user mất tin** | User có thể tắt tính năng tự động phân loại trong cài đặt hoặc đơn giản là lờ đi. Có nút liên hệ CSKH nhưng nằm sâu trong Menu hỗ trợ. |

### Đánh giá nhanh:
* **Path tốt nhất:** **Path 1 (Khi AI đúng)**. MoMo làm rất mượt phần nhận diện các Merchant lớn (Starbucks, Highlands) để phân loại ngay lập tức.
* **Path yếu nhất:** **Path 3 & 4**. Khi AI sai (ví dụ: chuyển tiền cho bạn bè nhưng bị tính là chi tiêu), việc sửa đổi mang tính thủ công cao. Không có cơ chế "Feedback loop" rõ ràng để AI học từ lỗi sai ngay tại màn hình chính.
* **Khoảng cách (Gap):** Marketing hứa hẹn "Trợ thủ thông minh" nhưng thực tế đôi khi chỉ là một bộ lọc (filter) tự động có gắn mác AI.

---

## Phần 3 — Sketch "Làm tốt hơn" (10 phút)

> **Lưu ý:** Phần này bạn hãy vẽ tay ra giấy theo cấu trúc sau.

### Vấn đề chọn: Cải thiện Path 3 (Khi AI sai hạng mục chi tiêu)

#### **Vế trái: As-is (Hiện tại)**
1.  **Màn hình Lịch sử:** Giao dịch hiển thị sai icon (Ví dụ: Chuyển tiền trả nợ nhưng hiện là "Giải trí").
2.  **Điểm gãy:** User nhìn thấy sai nhưng không có cách sửa nhanh. Phải bấm vào xem chi tiết.
3.  **Hành động:** Tap vào giao dịch -> Tìm nút Sửa -> Chọn lại hạng mục -> Lưu. (Quá tốn công cho 1 lỗi nhỏ).

#### **Vế phải: To-be (Đề xuất)**
1.  **Thêm Micro-interaction:** Cho phép **nhấn giữ** vào icon hạng mục ngay tại danh sách Lịch sử để hiện nhanh Menu chọn lại.
2.  **Cơ chế xác nhận:** Khi user sửa, Moni hiện một câu thoại nhỏ: *"Đã nhớ! Lần sau mình sẽ xếp các giao dịch tương tự vào [Hạng mục mới] nhé!"*
3.  **Nút Undo:** Thêm nút hoàn tác nhanh nếu user lỡ tay bấm nhầm.

---
