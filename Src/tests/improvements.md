# Improvement Proposals

## 1. RAG-lite (Critical)

### Implementation
- Query → retrieve KB → generate answer

### Rules
- Policy MUST have source
- Show timestamp

### Impact
- ↓ hallucination
- ↑ trust

---

## 2. Confidence Routing

### Flow

if confidence < 0.7:
    ask clarify
elif no data:
    escalate
else:
    answer

### Impact
- giảm sai nguy hiểm

---

## 3. Structured Responses

### Templates

Policy:
- bullet + threshold

Income:
- table

Situation:
- checklist

### Impact
- dễ đọc
- giảm cognitive load

---

## 4. Feedback Loop

### Signals
- Sai
- Chưa rõ
- Escalate

### Pipeline
1. Log
2. Cluster errors
3. Update prompt / KB

### Impact
- system improves over time

---

## 5. Guardrails

### Apply to:
- thu nhập
- policy
- tai nạn

### Rules
- add disclaimer
- suggest CSKH

---

## 6. Intent Clarification

### UI
- buttons instead of free text

### Impact
- ↑ accuracy
- ↓ misclassification

---

## 7. Continuous Evaluation

- run test cases daily
- track metrics dashboard

---

## Priority (important for demo)

1. RAG (must have)
2. Confidence routing
3. Recovery UX
4. Feedback loop