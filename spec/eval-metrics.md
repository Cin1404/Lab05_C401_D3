# Eval Metrics — XanhSM Driver Chatbot

## 1. Evaluation Strategy

Chatbot phục vụ tài xế → sai có thể ảnh hưởng **thu nhập / tài khoản / an toàn**.

→ Do đó:
- **High-stakes queries** (thu nhập, policy, tai nạn): ưu tiên **Recall**
  → tránh bỏ sót thông tin quan trọng
- **Low-stakes queries** (FAQ): ưu tiên **Precision**
  → tránh trả lời dài / nhiễu

---

## 2. Metrics Overview

| Metric | Mục tiêu | Priority |
|------|--------|---------|
| Answer Accuracy | Đúng thông tin | 🔴 Critical |
| Task Success Rate | User đạt mục tiêu | 🟠 High |
| Recovery Rate | Sửa lỗi tốt | 🟡 Medium |

---

## 3. Metric 1 — Answer Accuracy

### Definition
Tỷ lệ câu trả lời:
- Đúng hoàn toàn
- Không gây hiểu sai
- Không thiếu thông tin quan trọng

### Label schema
- ✅ Correct
- ⚠️ Partially correct (thiếu info)
- ❌ Incorrect
- 🚨 Misleading (nguy hiểm nhất)

### Formula

Accuracy = (Correct + 0.5 * Partial) / Total

### Measurement setup
- 30–50 test cases
- 2 người chấm (reduce bias)
- Ưu tiên test:
  - policy
  - income
  - accident

### Threshold
- Policy / Income: ≥ 90%
- Overall: ≥ 80%

### Red flags
- Bất kỳ câu trả lời:
  - sai mức thưởng
  - sai mức phạt
  - sai thu nhập
→ FAIL ngay (không cần tính average)

---

## 4. Metric 2 — Task Success Rate

### Definition
User nhận được câu trả lời đủ để:
- hiểu vấn đề
- hoặc thực hiện hành động tiếp theo

### Proxy signals
- Không click “❌ Sai”
- Không click “📞 CSKH”
- Không re-ask cùng intent

### Formula

Task Success = Successful Sessions / Total Sessions

### Measurement
- Simulated sessions (test)
- hoặc log thật (production)

### Threshold
- ≥ 85%

### Breakdown (quan trọng cho demo)
| Case type | Expected success |
|----------|----------------|
| Policy FAQ | ≥ 90% |
| Income query | ≥ 85% |
| Situation handling | ≥ 80% |

### Red flags
- Escalate CSKH > 20% với FAQ đơn giản
- User hỏi lại cùng câu > 2 lần

---

## 5. Metric 3 — Recovery Rate

### Definition
Khi AI:
- sai
- hoặc không chắc

→ có dẫn user về đúng flow không

### What counts as recovery?
- User click “Xem lại” → nhận câu trả lời đúng
- User chọn lại intent → success
- User escalate → đúng flow (acceptable)

### Formula

Recovery Rate = Successful Recovery / Error Cases

### Measurement
- Test explicit error scenarios
- Track button clicks

### Threshold
- ≥ 70%

### Red flags
- User stuck (không có next step)
- Loop vô hạn (ask lại → sai → ask lại)

---

## 6. Supporting Metrics (Optional - bonus)

### 6.1 Latency
- Target: < 5s
- > 8s → user drop mạnh

### 6.2 Response Length
- ≤ 5 dòng
- > 8 dòng → giảm readability

### 6.3 Escalation Rate
- Target: 10–20%
- > 30% → bot vô dụng

---

## 7. Evaluation Setup

### Dataset
- 12–20 curated test cases
- 3 nhóm chính:
  - policy
  - income
  - situation

### Evaluation loop
1. Run test cases
2. Log output
3. Human label
4. Compute metrics
5. Analyze errors

---

## 8. Summary

- Accuracy ≥ 90% (critical queries)
- Task success ≥ 85%
- Recovery ≥ 70%

→ Nếu không đạt:
- Fix KB / prompt / flow trước khi scale