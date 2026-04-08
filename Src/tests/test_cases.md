# Test Cases — XanhSM Chatbot

## Structure

Mỗi test case gồm:
- Input
- Expected output
- Expected behavior
- Risk level

---

## Group 1 — Policy

### TC1 — thưởng tuần

Input:
"Bao nhiêu cuốc thì được thưởng?"

Expected:
- 50 → 200k
- 80 → 400k
- Có timestamp / source

Behavior:
- concise (≤5 dòng)
- structured bullet

Risk:
🔴 High (financial)

---

### TC2 — hủy cuốc

Input:
"Hủy cuốc nhiều có bị khóa không?"

Expected:
- >15% → warning
- >25% → khóa
- disclaimer

Behavior:
- MUST include disclaimer

Risk:
🔴 Critical

---

### TC3 — mơ hồ

Input:
"Chính sách mới nhất là gì?"

Expected:
- KHÔNG trả lời trực tiếp
- hỏi lại bằng buttons

Risk:
🟡 Medium

---

## Group 2 — Income

### TC4 — thu nhập hôm nay

Input:
"Hôm nay tôi kiếm được bao nhiêu?"

Expected:
- table breakdown
- timestamp

Risk:
🔴 Critical

---

### TC5 — khiếu nại

Input:
"45k sao còn 30k?"

Expected:
- explain possibilities
- offer escalate

Behavior:
- KHÔNG khẳng định chắc chắn

Risk:
🔴 Critical

---

### TC6 — giải ngân

Input:
"Bao giờ nhận tiền?"

Expected:
- thứ 4 tuần sau
- deadline 17:00

Risk:
🟠 High

---

## Group 3 — Situation

### TC7 — tai nạn

Input:
"Tôi vừa va chạm"

Expected:
- checklist:
  1. an toàn
  2. kiểm tra người
  3. chụp ảnh
  4. gọi hotline

Risk:
🚨 Extreme

---

### TC8 — khách say

Input:
"Khách say tôi hủy được không?"

Expected:
- allowed
- steps

Risk:
🟠 High

---

### TC9 — xe hỏng

Input:
"Xe hỏng giữa ca"

Expected:
- KHÔNG hallucinate
- escalate + hotline

Risk:
🟠 High

---

## Group 4 — Robustness

### TC10 — slang

Input:
"chạy bn cuốc có thưởng"

Expected:
- hiểu = "bao nhiêu cuốc"

---

### TC11 — vague

Input:
"tiền???"

Expected:
- clarify intent

---

### TC12 — multi-intent

Input:
"thưởng + phạt"

Expected:
- split answer OR ask clarify