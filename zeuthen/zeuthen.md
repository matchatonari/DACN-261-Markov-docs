---
tags:
  - dacn/DACN-261-Markov/zeuthen
---
# calculate_zeuthen_cost(current_arch, target_arch, agent, d)
Chi phí nhượng bộ tương đối của agent.
$$W_i=\frac{U_i(\text{current\_arch}) - U_i(\text{target\_arch})}{U_i(\text{current\_arch}) - d_i}$$
W càng nhỏ -> agent càng ít phải hy sinh tương đối -> càng phù hợp để nhượng bộ.
# zeuthen(arch\_by\_id, proposals, d, agents)
So sánh concession cost giữa các cặp Agent.
- Kết quả: agent -> Agent được chọn để nhượng bộ.
- Chọn concession có relative cost thấp nhất.