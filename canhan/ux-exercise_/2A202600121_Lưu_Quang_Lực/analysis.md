# UX exercise — Trợ lý ảo V-AI

## Sản phẩm: V-AI Assistant (Hỗ trợ người dùng)

## 4 paths

### 1. AI đúng
- User hỏi về chương trình AI thực chiến
- UI: Hiện câu trả lời đúng thông tin về chương trình

### 2. AI không chắc
- User hỏi: Ăn gì quanh Vinuni
- UI: Hiện câu trả lời chung chung, không gợi ý quán cụ thể. Giới thiệu có canteen,
  quán lẩu, quán nướng ở khu Ocean Park.
- Vấn đề: Không hiện tên quán, địa chỉ cụ thể, đánh giá.

### 3. AI sai
- User hỏi: Giá cơm canteen  (Giá thực tế là 50k)
- UI: Giá cơm canteen ở Vinuni là 35k 
- Sửa: Yêu cầu lấy dữ liệu mới nhất, hoặc báo lại giá cơm đã lên 50k.
- UI: Giá cơm canteen ở Vinuni vẫn là 35k
- Vấn đề: Không lấy dữ liệu mới nhất, hoặc không cho rằng canteen là trong
hệ sinh thái của VinGroup, không cho sửa.

### 4. User mất niềm tin
- Sau khi thấy giá cơm không được cập nhật thì người dùng không tin các thông số
  cụ thể mà ứng dụng cung cấp.

## Path yếu nhất: Path 3 + 4
- AI trả lời sai nhưng vẫn “tự tin như đúng”
- Recovery flow không hiệu quả

## Gap marketing vs thực tế
- Marketing: "ứng dụng giúp người dùng dễ dàng sử dụng dịch vụ của VinGroup"
- Thực tế: "Tự tin cung cấp giá cơm canteen trong khi dữ liệu đã lâu. Không phân biệt
  dữ liệu tĩnh và dữ liệu động. Không cung cấp đa dạng loại cơm"
- Gap lớn nhất: AI không sai nhưng độ tin cậy về dữ liệu thấp, hoặc không giới hạn dịch vụ nào
  thuộc VinGroup

## Sketch
(Ảnh đính kèm: sketch.jpg)
- As-is: User hỏi -> AI trả lời sai -> Không được sửa.
- To-be: User hỏi -> AI trả lời sai -> User sửa -> Ghi nhận thông tin user sửa.