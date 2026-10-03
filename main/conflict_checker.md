---
tags:
  - dacn/DACN-261-Markov/main
---
# ConflictChecker
## \_\_init\_\_()
- `rules_path`: `../data/conflict_rules.json`
- `penalty`: `1000` (có thể sửa được).
## check_conflicts(self, architecture: dict) -> float
Kiểm tra xem bản kiến trúc có vi phạm bất kỳ luật xung đột tuyệt đối nào không.
- param: architecture: dict dạng {"database": "MySQL", "compute": "Monolith", ...}
- return: Điểm phạt C(s) (VD: 1000 nếu vi phạm, 0 nếu không vi phạm)
## \_is\_violated(self, architecture: dict, conditions: dict) -> bool
Một rule bị vi phạm nếu kiến trúc HIỆN TẠI match TẤT CẢ các điều kiện trong rule.