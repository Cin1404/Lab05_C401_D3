# [SPEC draft] Team D3 - C401

**Đề tài: Chatbot hỗ trợ tài xế, giải đáp các câu hỏi chính sách, quy định và hướng xử lý nhanh chóng**

**Track: XanhSM**


## 1. Problem statement

- **User:** Tài xế XanhSM, đặc biệt là tài xế mới hoặc tài xế đang trong ca làm việc
- **User’s need:** Cần tra cứu nhanh, rõ ràng và chính xác các thông tin về chính sách, thu nhập, quy định và cách xử lý tình huống
- **Insight:** Khi gặp vấn đề, tài xế thường phải chờ hỗ trợ 10 - 15 phút hoặc nhận câu trả lời chưa đủ đúng trọng tâm, làm gián đoạn công việc và có thể ảnh hưởng đến quyền lợi

Tài xế XanhSM, đặc biệt là tài xế mới hoặc tài xế đang làm việc trong ca, cần một cách nhanh chóng, rõ ràng và đáng tin cậy để tra cứu chính sách, thu nhập, quy định vận hành và cách xử lý các tình huống phát sinh, bởi vì cách hỗ trợ hiện tại còn chậm và đôi khi chưa trả lời đúng trọng tâm, khiến họ mất thời gian, gián đoạn công việc và có thể ảnh hưởng đến quyền lợi của mình.

## 2. Canvas draft

| VALUE | TRUST | FEASIBILITY |
|---|---|---|
| **User:** Tài xế hỏi chính sách, thu nhập.<br><br>**Pain:** chatbot hiện tại phản hồi lòng vòng, khó hiểu.<br>Chờ hỗ trợ lại mất 10 - 15 phút.<br><br>**Aug:** bot đưa ra thông tin, quy định, chính sách;<br>nhân viên hỗ trợ xử lý mất thời gian.<br><br>**Value:** trả lời 24/7. | **Recall cao:** nếu sai có thể ảnh hưởng quyền lợi tài xế.<br><br>**Khi sai:** tạo nút để user lựa chọn lại / kiểm tra lại.<br><br>**Recovery:** check lại dữ liệu mới, cập nhật lại thông tin.<br>Nếu không ổn thì liên hệ CSKH. | **Cost:** ~ $0.01 / lượt GPT-4o.<br><br>**Latency:** < 5 giây.<br><br>**Risk:** cần hệ thống cập nhật liên tục.<br><br>**Dep:** API Xanh Driver real-time,<br>API ngân hàng real-time. |



**Auto hay aug?** Augmentation - AI gợi ý và cung cấp thông tin, nhưng tài xế vẫn là người quyết định cuối cùng hoặc có thể chuyển sang CSKH khi cần.

**Learning signal:**  
- Tài xế có thể bấm phản hồi như “đúng/sai/chưa rõ”, chọn “xem lại thông tin”, hoặc chuyển sang CSKH.  
- Các case bị sửa, bị escalated sang hỗ trợ viên, hoặc câu trả lời bị đánh dấu sai sẽ là correction signal để cải thiện hệ thống.

## 3. Hướng đi chính
- Prototype: chatbot hỗ trợ tài xế hỏi đáp về chính sách, thu nhập, quy định và xử lý tình huống
- Core UX: trả lời nhanh, ngắn gọn, dễ hiểu, có nút kiểm tra lại hoặc chuyển CSKH
- Mục tiêu: giảm thời gian chờ hỗ trợ từ 10 - 15 phút xuống còn vài giây cho các câu hỏi phổ biến
- Main failure mode: dữ liệu không được cập nhật kịp thời hoặc AI hiểu sai câu hỏi, dẫn đến trả lời sai chính sách/quyền lợi

## 4. Trust / Recovery design
- Hiển thị câu trả lời ngắn gọn, rõ ràng
- Có nút “Kiểm tra lại” hoặc “Cập nhật lại thông tin”
- Có nút “Liên hệ CSKH” nếu AI không chắc hoặc user không tin câu trả lời
- Với các câu hỏi nhạy cảm về quyền lợi/thu nhập/chính sách, AI nên ưu tiên dẫn nguồn hoặc báo đây là thông tin tham khảo

## 5. Feasibility notes
- Model cost: khoảng $0.01/lượt
- Latency: dưới 5 giây
- Data dependency:
  - API Xanh Driver real-time
  - Dữ liệu chính sách/quy định nội bộ
  - Có thể cần API ngân hàng hoặc hệ thống thanh toán nếu liên quan đến thu nhập real-time
- Risk kỹ thuật:
  - Chính sách thay đổi thường xuyên
  - Dữ liệu backend không đồng bộ
  - Khó đảm bảo độ chính xác nếu không có source-of-truth rõ ràng

## 6. Phân công thành viên
- Lưu Thị Ngọc Quỳnh: Problem statement + Canvas bản cuối + tổng hợp nội dung + slide + thuyết trình
- Nguyễn Phương Nam: User research + pain point + user persona
- Đinh Văn Thư: User flow + các case chính   prompt + logic demo
- Nguyễn Quốc Khánh: Use case chính
- Lưu Quang Lực: Trust + failure modes + recovery flow
- Nguyễn Bá Khánh: Feasibility + cost + latency + dependency
- Lý Quốc An:  Data/knowledge base cho chatbot + tổng hợp chính sách, FAQ, câu hỏi mẫu
- Nguyễn Quang Minh: Test case + evaluation metrics + phân tích lỗi + đề xuất cải thiện