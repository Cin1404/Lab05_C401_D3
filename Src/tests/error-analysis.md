# Error Analysis — XanhSM Chatbot

## Overview

Top 4 failure modes:

1. Hallucination policy
2. Misclassification intent
3. Overconfidence
4. Poor recovery UX

---

## Error 1 — Hallucination Policy

### Trigger
- KB thiếu
- policy update nhưng chưa sync

### Example
AI trả:
"60 cuốc → thưởng 300k" (sai)

### Impact
- mất tiền user
- mất trust ngay lập tức

### Detection
- mismatch với KB
- user feedback “Sai”

### Mitigation
- enforce retrieval (RAG)
- show source + timestamp

---

## Error 2 — Misclassification Intent

### Trigger
- câu mơ hồ
- slang
- multi-intent

### Example
"tiền hôm nay sao thấp"
→ classify thành policy

### Impact
- trả lời irrelevant
- user frustrate

### Detection
- high re-ask rate
- low task success

### Mitigation
- clarification buttons
- better intent classifier

---

## Error 3 — Overconfidence

### Trigger
- model không có data nhưng vẫn trả lời

### Example
AI tự tạo số tiền

### Impact
- sai nhưng user tin → nguy hiểm

### Detection
- answer không có source
- inconsistent outputs

### Mitigation
- confidence threshold
- fallback → "không chắc"

---

## Error 4 — Poor Recovery UX

### Trigger
- user click “Sai”

### Example
không có next step

### Impact
- abandon
- tăng load CSKH

### Detection
- drop-off rate cao

### Mitigation
- recovery flow rõ:
  - retry
  - clarify
  - escalate