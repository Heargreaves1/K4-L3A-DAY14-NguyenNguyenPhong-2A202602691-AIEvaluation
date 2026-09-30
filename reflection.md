# Day 14 — Reflection

## Evaluation Report & Failure Analysis

Dùng kết quả thật trong `artifacts/benchmark_results.json` và kiểm tra lại
answer/context trace trong `artifacts/actual_answers.json` trước khi kết luận.

> ⚠️ **Trạng thái:** `artifacts/actual_answers.json` chưa được sinh (Gemini
> `gemini-3.5-flash` trả 429 vượt quota). Các số retrieval bên dưới là **số thật**
> từ retriever BM25 (`artifacts/retrieval_only_metrics.json`, top_k = 5). Các phần
> cần actual answer (answer-side metrics, 5 Whys, improvement log) sẽ điền sau khi
> chạy lại `python domain_assistant.py` và `python evaluate_answers.py`.

---

## 1. Benchmark Results Summary

**Overall pass rate:** ____%

| Metric | Average | Min | Max | Nhận xét |
|---|---:|---:|---:|---|
| Context Recall | 0.773 | 0.227 (A01) | 1.000 (E01, E05) | Giảm theo độ khó: Easy 0.913, Medium 0.868, Hard 0.624. Retriever hay lấy thiếu ở câu nhiều tài liệu |
| Context Precision | 0.898 | 0.200 (A01) | 1.000 | Cao: chunk đầu thường liên quan. Nhưng ngưỡng "relevant" ≥ 10% token khá lỏng nên precision có thể bị thổi phồng |
| Faithfulness | | | | |
| Relevance | | | | |
| Completeness | | | | |
| Overall Score | | | | |

**Score interpretation**

- Metrics/cases ở mức Good (0.8–1.0): ____
- Metrics/cases ở mức Needs Work (0.6–0.8): ____
- Metrics/cases ở mức Significant Issues (<0.6): ____

**Failure type distribution**

| Failure Type | Count | Percentage |
|---|---:|---:|
| hallucination | | |
| irrelevant | | |
| incomplete | | |
| off_topic | | |
| refusal | | |

**Chẩn đoán tổng quan:** Vấn đề chính nằm ở retrieval, generation hay cả hai?
Dùng ít nhất hai metrics để bảo vệ kết luận.

> *Câu trả lời:*

---

## 2. Top 3 Worst Failures — 5 Whys

Phân loại failure trước khi đề xuất fix. Với mỗi case, kiểm tra cả gold evidence
và retrieved chunks; không suy luận chỉ từ một score.

### Failure 1

**ID và question:**

> *Điền:*

**Expected answer:**

> *Điền:*

**Actual answer:**

> *Điền:*

**Scores:** Context Recall: ____ | Context Precision: ____ | Faithfulness: ____ |
Relevance: ____ | Completeness: ____ | Overall: ____

**Evidence inspection:** Retriever lấy đúng/thiếu/thừa chunks nào?

> *Câu trả lời:*

| Level | Question | Answer |
|---|---|---|
| Symptom | Vấn đề quan sát được là gì? | |
| Why 1 | Tại sao symptom xảy ra? | |
| Why 2 | Tại sao nguyên nhân trên xảy ra? | |
| Why 3 | Tại sao vấn đề đó chưa được ngăn chặn? | |
| Why 4 | Tại sao cơ chế hiện tại chưa phát hiện hoặc xử lý được? | |
| Why 5 | Root cause có thể hành động được là gì? | |

**Root cause từ `find_root_cause()`:**

> *Paste output:*

**Bạn đồng ý hay không? Dẫn evidence từ trace:**

> *Câu trả lời:*

**Proposed fix cụ thể:**

> *Câu trả lời:*

### Failure 2

**ID và question:**

> *Điền:*

**Expected answer:**

> *Điền:*

**Actual answer:**

> *Điền:*

**Scores:** Context Recall: ____ | Context Precision: ____ | Faithfulness: ____ |
Relevance: ____ | Completeness: ____ | Overall: ____

**Evidence inspection:**

> *Câu trả lời:*

| Level | Question | Answer |
|---|---|---|
| Symptom | Vấn đề quan sát được là gì? | |
| Why 1 | Tại sao symptom xảy ra? | |
| Why 2 | Tại sao nguyên nhân trên xảy ra? | |
| Why 3 | Tại sao vấn đề đó chưa được ngăn chặn? | |
| Why 4 | Tại sao cơ chế hiện tại chưa phát hiện hoặc xử lý được? | |
| Why 5 | Root cause có thể hành động được là gì? | |

**Root cause và proposed fix:**

> *Câu trả lời:*

### Failure 3

**ID và question:**

> *Điền:*

**Expected answer:**

> *Điền:*

**Actual answer:**

> *Điền:*

**Scores:** Context Recall: ____ | Context Precision: ____ | Faithfulness: ____ |
Relevance: ____ | Completeness: ____ | Overall: ____

**Evidence inspection:**

> *Câu trả lời:*

| Level | Question | Answer |
|---|---|---|
| Symptom | Vấn đề quan sát được là gì? | |
| Why 1 | Tại sao symptom xảy ra? | |
| Why 2 | Tại sao nguyên nhân trên xảy ra? | |
| Why 3 | Tại sao vấn đề đó chưa được ngăn chặn? | |
| Why 4 | Tại sao cơ chế hiện tại chưa phát hiện hoặc xử lý được? | |
| Why 5 | Root cause có thể hành động được là gì? | |

**Root cause và proposed fix:**

> *Câu trả lời:*

---

## 3. Failure Clustering

Một root cause có thể tạo ra nhiều failures. Nhóm theo nguyên nhân có thể sửa,
không chỉ nhóm theo tên metric.

| Cluster | Root Cause | Failure IDs | Priority |
|---|---|---|---|
| 1 | | | High/Medium/Low |
| 2 | | | |
| 3 | | | |

**Nếu chỉ được sửa một cluster, bạn chọn cluster nào và vì sao?**

> *Câu trả lời:*

---

## 4. Improvement Log

Paste output của `generate_improvement_log()`:

```text
[paste Markdown table here]
```

**Ba improvement suggestions ưu tiên**

1. ____
2. ____
3. ____

Với mỗi suggestion, nêu metric dự kiến thay đổi và cách đo lại.

| Suggestion | Target metric | Verification method |
|---|---|---|
| | | |
| | | |
| | | |

---

## 5. Regression Testing Strategy

**Câu 1: Khi nào chạy `run_regression()` trong production workflow?**

> *Câu trả lời:* Mỗi pull request thay đổi thứ gì ảnh hưởng tới câu trả lời:
> system prompt, model/version LLM (vd. đổi gpt-4o-mini sang Gemini), retriever
> (top_k, chunking, BM25 sang dense), hoặc corpus chính sách (khi có Return Policy
> version mới). Chạy golden dataset, so với baseline là lần chạy của bản đang
> production, và lưu kết quả làm artifact của CI. Ngoài ra chạy định kỳ hằng đêm,
> vì provider có thể đổi model phía sau cùng một tên model.

**Câu 2: Threshold drop 0.05 có phù hợp OrbitTech Customer Support không? Vì sao?**

> *Câu trả lời:* Hợp lý làm mức mặc định nhưng chưa đủ. Với 20 câu, một câu đổi
> từ 1.0 xuống 0.0 chỉ kéo trung bình giảm 0.05, nên một lỗi nghiêm trọng ở một câu
> (vd. H01 áp sai version, khách mất quyền trả hàng) có thể lọt qua. Vì vậy cần
> thêm hai quy tắc: (1) so theo từng câu, không chỉ theo trung bình: câu nào pass
> ở baseline mà fail ở bản mới thì báo; (2) nhóm câu an toàn (A01–A03) không cho
> phép giảm chút nào. Ngược lại, output LLM dao động giữa các lần chạy dù
> temperature = 0, nên nên chạy 2–3 lần và lấy trung bình trước khi so với 0.05
> để tránh block oan.

**Câu 3: Metric/failure nào phải block deployment, metric nào chỉ alert?**

> *Câu trả lời:*
> - **Block:** faithfulness trung bình < 0.7 hoặc giảm > 0.05 (bịa chính sách
>   tiền/hạn); bất kỳ câu adversarial nào fail (lộ prompt/dữ liệu khách, làm theo
>   injection); bất kỳ câu nào đang pass ở baseline chuyển sang `hallucination`.
> - **Alert (không block):** relevance và completeness giảm trong khoảng
>   0.02–0.05; context recall/precision giảm (retriever kém đi nhưng cần xem
>   generator có bù được không); leniency/severity bias của judge.

**Câu 4: Điền evaluation stages vào flow.**

```text
Code/prompt/retrieval change → [Unit tests + dataset validator] → [Golden-set benchmark + run_regression vs baseline] → [Human review các case fail/adversarial] → Deploy
```

> *Giải thích:* Bước 1 rẻ và nhanh: `pytest` kiểm tra evaluation core,
> `validate_golden_dataset.py` đảm bảo dataset không hỏng. Bước 2 là quality gate
> chính: chạy 20 câu qua RAG, tính 5 metrics, `run_regression()` trả
> `passed = False` thì CI dừng. Bước 3: người xem nhanh các câu fail và 3 câu
> adversarial, vì word-overlap không đánh giá được "từ chối đúng cách". Sau
> deploy, online monitoring (tỷ lệ escalate, feedback) đưa câu hỏi mới vào dataset.

---

## 6. Continuous Improvement Loop

```text
Evaluate → Analyze → Improve → Augment benchmark → Repeat
```

| Priority | Action | Metric dự kiến cải thiện | Expected impact |
|---:|---|---|---|
| 1 | Luôn đưa `00_system_scope.md` (luật scope/an toàn) vào prompt thay vì chờ retriever lấy; A01 và A03 hiện không retrieve được file này | Safety (judge), faithfulness câu adversarial | Bot từ chối/sửa tiền đề dựa trên luật thật chứ không dựa vào may mắn |
| 2 | Tăng top_k 5 → 8 hoặc thêm query rewriting tách câu hỏi nhiều ý; H02 thiếu `03`, H03 thiếu `05` | Context recall câu Hard (hiện 0.624) | Generator có đủ điều kiện để trả lời câu nhiều tài liệu |
| 3 | Thay `rerank_by_overlap` bằng cross-encoder reranker | Context precision | Tránh trường hợp như H03/H04, nơi rerank theo từ khoá làm precision giảm |

**Hai hoặc ba failure cases nào cần thêm vào benchmark ở vòng tiếp theo?**

> *Câu trả lời:*

---

## 7. Final Reflection

**Điều gì trong kết quả benchmark trái với dự đoán ban đầu của bạn?**

> *Câu trả lời (phần retrieval):* (1) Reranking không phải lúc nào cũng tốt hơn:
> trung bình precision tăng (0.898 → 0.916) nhưng H03 và H04 lại giảm. (2) H02
> thiếu hẳn tài liệu `03` mà context recall vẫn là 0.697, vì các chunk khác chứa
> nhiều từ chung như "OrbitPlus", "days", "return". Recall theo từ không phát
> hiện được việc thiếu đúng câu quyết định. (3) Ngay cả gold evidence cũng chỉ
> đạt recall trung bình 0.791 so với expected answer (H01 chỉ 0.532), vì expected
> answer chứa suy luận ("September 12 is outside the window") không có nguyên văn
> trong tài liệu. Đó là trần điểm của metric word-overlap.

**Word-overlap heuristics trong lab có giới hạn gì? Nếu đưa hệ thống vào
production, bạn sẽ thay hoặc bổ sung metric nào?**

> *Câu trả lời:* Giới hạn: (1) không hiểu nghĩa: "7 days" và "14 days" chỉ khác
> một token nên câu sai con số vẫn được điểm cao; (2) không hiểu phủ định:
> "is eligible" và "is not eligible" gần như trùng hết; (3) phạt oan câu diễn đạt
> khác từ hoặc câu từ chối đúng; (4) một từ chung như "OrbitPlus" làm chunk nhiễu
> được coi là "relevant" (ngưỡng 10%). Production: dùng faithfulness dạng
> claim-level (tách câu trả lời thành các claim và cho LLM kiểm từng claim với
> context, như RAGAS Faithfulness), answer correctness bằng LLM judge theo rubric
> ở Exercise 3.3, context recall/precision do LLM đánh giá, cộng thêm check tất
> định cho con số (so khớp số ngày, phần trăm, USD với tài liệu) và một bộ test
> safety riêng cho prompt injection và privacy.
