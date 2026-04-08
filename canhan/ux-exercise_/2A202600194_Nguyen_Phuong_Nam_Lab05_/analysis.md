# UX exercise - VN Airline - NEO chatbot

## Sanr phẩm: VN Airline - NEO chatbot

## 4 paths

### 1. AI đúng
- User:"Một chuyến bay có khoảng bao nhiêu người" -> NEO trả lời khoảng 305 người cho một chuyến bay
- User thấy hiện số lượng đầy đủ, không cần làm gì thêm
- UI: hiện nguồn trang thông tin

### AI không chắc
- User hỏi: "Cho tôi giá các vé khởi hành từ Hà Nội tới Đà Nẵng trong ngày hôm nay"
-> NEO: " Bạn có thể tra cứu theo mã đặt chỗ hoặc số hiệu chuyến bay" 
- Không hiểu đúng intent, trả lời lạc hướng
- UI: Không hiển thị thông tin vé máy bay trong ngày mà lại hỏi ngược lại mã vé, mã máy bay
- Vấn đề: không có option quick action, không có clarification:
“Bạn muốn xem giờ bay hay giá vé?”
-> AI không chắc nhưng không hỏi lại đúng cách

### AI sai
- User:" Tôi muốn xem giá vé và thời gian"
- NEO:" NEO đứa ra các phương án tra cứu: mã ghế, mã vé,.."
- Sửa: Bạn có ý là..., Bạn muốn đặt ghế thường hay thương gia,...
- Vấn đề: Hiểu sai intent, không fulfill task

### User mất niềm tin
- Sau nhiều lần trả lời không đúng trọng tâm, User sẽ không muốn hỏi chatbot nữa mà trực tiếp hỏi nhân viên
- Hỏi thông tin vé để đặt vé nhưng liên tục yêu cầu mã vé và số hiệu máy bay
- Không chuyển tiếp qua nhân viên với những task không thể thực thi

## path yếu nhất: Path 4
- Niềm tin của khách hàng sẽ bị mất dần đi khi hỏi nhiều lần chatbot không trả lời đúng trọng tâm
- Khi gặp nhưng câu hỏi ngoài phạm vi, chatbot từ chốt một cách khô khan mà chưa có sự khéo léo
- Không có feedback loop rõ 
- Không có cơ chế hỏi lại thông minh
- Không hiểu intent nhưng vẫn trả lời

## Gap marketing vs thực tế
- Marketing: "Chatbot thông minh, hỗ trợ nhanh chóng, tư vấn du lịch, kiểm tra thông tin chuyến bay, giá vé, giờ bay"
- Thực tế: "Không đưa ra các thông tin chuyến bay, giá vé theo yêu cầu, không trả lời đúng trọng tâm theo yêu cầu của khách hàng

## Sketch
- As in
User hỏi
   ↓
Chatbot match sai intent
   ↓
Trả lời template (lệch hướng)
   ↓
User hỏi lại / bỏ cuộc

#
- To be:
User hỏi
   ↓
Intent detection
   ↓
[High confidence]
→ trả lời đúng + CTA 

[Medium confidence]
→ hỏi lại:
“Bạn muốn xem giá vé hay giờ bay?”
→ đưa option 

[Low confidence]
→ hỏi thêm info:
“Bạn bay ngày nào, từ đâu đến đâu?”
→ guide user 

   ↓
Nếu vẫn fail:
→ “Bạn muốn gặp nhân viên hỗ trợ không?”
→ fallback human 💬

   ↓
User phản hồi
→ system học & cải thiện 🔁
