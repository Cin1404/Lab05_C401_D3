**Lưu Thị Ngọc Quỳnh - 2A202600122**
# Phân tích Moni - Trợ lý tài chính của MoMo

## 1.Khám phá

### 1.1. Tính năng AI
- Quản lý chi tiêu
- Ngân sách
- Phân loại chi tiêu
- Tư vấn tài chính
- Theo dõi chi tiêu
- User tự phân loại giao dịch
- Gợi nhắc các chi tiêu định kỳ

### 1.2. Đánh giá nhanh
- **Đúng:** phân loại đúng một số giao dịch phổ biến, user nhìn nhanh ra loại chi tiêu.
- **Vấn đề chính:** với các giao dịch mơ hồ hoặc edge case, Moni dễ phân loại sai hoặc không rõ ràng.
- **Sai:** phân loại sai khoản chi khiến báo cáo tháng thiếu tin cậy.
- **Mất niềm tin:** khi sai nhiều lần, user có xu hướng không tin báo cáo AI nữa và phải quay về tự kiểm tra.

## 2. 4 paths

### 2.1. AI đúng
- User có giao dịch phổ biến, ví dụ ăn uống / cửa hàng quen thuộc.
- Moni tự nhận diện và gán đúng category chi tiêu.
- User chỉ cần xem kết quả, không phải sửa gì thêm.
- Giá trị mang lại: tiết kiệm thời gian, giúp user hiểu nhanh mình đang chi tiền vào đâu.

### 2.2. AI không chắc
- User có giao dịch mơ hồ, ví dụ chuyển tiền cho bạn bè hoặc giao dịch tên merchant khó hiểu.
- Moni vẫn có thể gán nhãn chưa thật rõ, hoặc không đưa ra gợi ý đủ tốt.
- Vấn đề: hệ thống chưa nói rõ là “không chắc”, nên user khó biết đây là dự đoán hay kết quả chắc chắn.
- Thiếu cơ chế hỏi lại nhanh để user xác nhận category.

### 2.3. AI sai
- Moni gán sai category cho giao dịch.
- User thường chỉ phát hiện khi xem lại báo cáo hoặc chi tiết giao dịch.
- Recovery flow còn bất tiện: user phải vào giao dịch, đổi category, lưu lại.
- Điểm yếu: chưa thấy rõ AI có học từ correction này cho lần sau hay không.

### 2.4. User mất niềm tin
- Sau nhiều lần gán sai hoặc báo cáo chưa chuẩn, user bắt đầu nghi ngờ độ chính xác của Moni.
- Khi đó user có xu hướng:
  - xem giao dịch gốc để tự đối chiếu,
  - tự phân loại lại,
  - hoặc bỏ qua gợi ý AI.
- Vấn đề: chưa có fallback/exit đủ rõ để giúp user lấy lại quyền kiểm soát một cách nhẹ nhàng.

## 3. Path yếu nhất
Tôi lựa chọn path 3 & 4 để thực hiện phân tích:
- Khi AI sai, flow sửa lỗi còn mất công.
- User không biết AI có học từ lần sửa đó không.
- Khi mất niềm tin, chưa có đường lui rõ ràng ngoài việc tự sửa thủ công.
- Đây là gap lớn nhất giữa kỳ vọng “trợ lý thông minh” và trải nghiệm thực tế.

### 3.1. Gap marketing vs thực tế
- **Marketing:** Moni giúp user quản lý chi tiêu thông minh, tự động phân loại và hỗ trợ ra quyết định tài chính.
- **Thực tế:** tính năng hữu ích với giao dịch quen thuộc, nhưng các trường hợp mơ hồ vẫn dễ sai.
- **Gap lớn nhất:** marketing nhấn mạnh sự thông minh, nhưng chưa làm rõ trải nghiệm khi AI sai hoặc không chắc.
- Vì vậy user dễ kỳ vọng Moni “gần như đúng hết”, trong khi trải nghiệm thật vẫn cần chỉnh tay.

### 3.2. Sketch

![ảnh 1](https://prnt.sc/nP63aIFiWTbR) 

![ảnh 2](https://prnt.sc/uajGLniRWM3S)

![ảnh 3](https://prnt.sc/BE9U1Rx5wi-w)

| **As-is** | **To-be** |
|---|---|
| - Giao dịch phát sinh<br>- Moni auto-tag category<br>- User thấy kết quả<br>- Nếu sai, user phải vào sửa thủ công<br>- Không rõ AI có học từ lần sửa hay không | - Giao dịch phát sinh<br>- Moni auto-tag category<br>- Nếu confidence thấp, hiện:<br>&nbsp;&nbsp;&nbsp;&nbsp;- “Bạn muốn phân loại giao dịch này không?”<br>&nbsp;&nbsp;&nbsp;&nbsp;- Gợi ý 2–3 category phù hợp<br>- User chọn nhanh category<br>- Hệ thống ghi nhận correction<br>- Hiện phản hồi rõ: **“Đã học, lần sau sẽ chính xác hơn”** |

## 4. Đề xuất thêm, bớt, đổi các nội dung trong Moni

| Hạng mục | Nội dung | Mục đích UX |
|---|---|---|
| **Thêm** | - Trạng thái “không chắc”<br>- Gợi ý chọn nhanh category<br>- Thông báo rõ khi AI học từ correction<br>- Fallback để user tự kiểm soát dễ hơn | - Giúp user biết đây là dự đoán của AI, không phải kết quả chắc chắn<br>- Giảm công sửa tay, giúp user xác nhận nhanh hơn<br>- Tăng niềm tin rằng việc sửa của user có giá trị cho lần sau<br>- Giúp user có đường lui khi không tin AI |
| **Bớt** | - Bớt việc auto-chốt trong các case mơ hồ<br>- Bớt số bước sửa thủ công | - Tránh việc AI đoán bừa và làm sai category<br>- Làm flow recovery nhẹ hơn, đỡ gây khó chịu |
| **Đổi** | - Đổi từ flow “AI gán xong user tự sửa”<br>- Sang flow “AI gợi ý + user xác nhận + hệ thống học dần” | - Giảm tư duy AI tự quyết hoàn toàn<br>- Tăng trust, tăng cảm giác AI đang hỗ trợ thay vì áp đặt |

## Kết luận
Moni có giá trị rõ ở việc hỗ trợ user nhìn nhanh các khoản chi tiêu và giảm công phân loại thủ công. Tuy nhiên, điểm yếu lớn nhất nằm ở lúc AI sai hoặc không chắc. Để tăng trust, Moni cần làm rõ độ chắc chắn, cho user sửa nhanh hơn và thể hiện rõ feedback loop để user thấy AI thực sự học từ các lần chỉnh sửa.
