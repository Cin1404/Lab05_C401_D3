# UX exercise — MoMo Moni AI - 2A202600135_NguyenBaKhanh

## Sản phẩm: MoMo — Moni AI Assistant (phân loại chi tiêu)

## 4 paths

### 1. AI đúng

- UI: hiện tag + icon category, không hỏi confirm
- User muốn gửi tiết kiệm khoảng 5 triệu --> Moni gợi ý đúng gói gửi với lãi suất 3%/ năm
- User thấy có số liệu thực tế chọn được gói gửi 
- UI: hiện gói gửi, không cho chọn gói tại khung chat, phải thao tác trang chủ


### 2. AI không chắc
- User hỏi " tháng này tôi muốn gửi một ít tiền "
- AI sẽ Không đủ dữ liệu (không rõ số tiền, mục tiêu)
+ AI Confidence thấp
- AI sẽ không biết số tiền bao nhiêu trả lời chung chung là (Gửi 5 triệu sẽ có lãi suất 3%/ năm )
### 3. AI sai
- User dùng tiền đăng ký học tiếng anh hết 1 triệu
- MONI liệt kê vào " giải trí "
- AI không biết được nên liệt kê vào chỗ nào 
- UI: Không có hỏi lại user và không được fix lại 


### 4. User mất niềm tin
- Sau nhiều lần tag sai, user không tin báo cáo chi tiêu theo task nữa
- Không có option tự chọn nếu có mục chi tiêu mới
- Chưa có thao tác ngay trong chatbot 
## Path yếu nhất: Path 3
- Khi AI sai, chatbot vẫn liệt kê vào mục chi tiêu cũ 
- Không có feedback theo tag mỗi khi lưu 
- User không thao tác được trên chatbot 
- User chán và bỏ dùng Moni

## Gap marketing vs thực tế
- Moni được truyền thông như một công cụ quản lý chi tiêu thông minh.
- Dù vậy, độ chính xác của auto-tag chỉ đạt khoảng 70% trong các tình huống phổ biến, và giảm đáng kể ở các trường hợp ngoại lệ như chuyển khoản hay mua sắm online.
- Điểm lệch lớn nằm ở chỗ thông điệp marketing không phản ánh khả năng sai sót của AI, dẫn đến kỳ vọng quá cao từ phía người dùng.

## Sketch
(Ảnh đính kèm: sketch.jpg)
- As-is: giao dịch → auto-tag → user thấy kết quả → nếu sai phải vào sửa thủ công + mất thời gian
- To-be: giao dịch → auto-tag → nếu chưa có dữ liệu về khoản chi tiêu này --> thêm nút vật lý để chọn tên khoản tiền -->
AI  ghi nhớ nó cho các lần sau --> " Mục chi tiêu mới đã được cập nhật, cảm ơn bạn"
  
