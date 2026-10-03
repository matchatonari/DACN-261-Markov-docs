---
tags:
  - dacn/DACN-261-Markov/main
---

# WeightAssigner
- `__init__()` chỉ có prompt.
## assign_weights(self, structured_prd: dict, agent_ratios: dict) -> dict
- Normalize macro-weights (Ratios)
- Get micro-weights from each Agent
	- Validation
	- Fallback weights: cái nào cũng 0.25.
## \_validate\_weights(self, weights: dict) -> dict
- Đảm bảo tổng trọng số = 1.0 và làm tròn đến 1 chữ số thập phân.
    - Nếu sai lệch do LLM ảo giác, chuẩn hóa lại.
- Đảm bảo có đủ 4 key
- Sửa lỗi làm tròn làm tổng khác 1.0
- Nếu sau khi round mà tổng != 1.0, điều chỉnh phần tử lớn nhất
## \_extract\_json(self, text: str) -> str
---
# MockLLM
Mock LLM for local testing.