---
tags:
  - dacn/DACN-261-Markov/main
---

# PRDAnalyzer
- `__init__()`: chỉ load schema và prompt.
## parse_prd(self, prd_content: str) -> dict
- Dùng LLM để phân tích file PRD thô thành Structured JSON dựa trên Schema.
	- Clean up JSON if LLM returned markdown blocks
## score_component(self, component_category: str, component_name: str, component_desc: dict, rubric_content: str, structured_prd: dict) -> float
- Gọi LLM để chấm điểm 1 component trên 1 bộ rubric (có 3 facets).
- Trả về điểm số trung bình $V_k$ của component đó.
- Fallback
- Tính $V_k$ = trung bình cộng các facets
## \_extract\_json(self, text: str) -> str
- Helper to remove markdown json blocks if any.
- Tìm block `{ ... }` gần nhất trong trường hợp LLM dài dòng.
# MockLLM
Mock LLM for local testing.