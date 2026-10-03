---
tags:
  - dacn/DACN-261-Markov/main
---

# MockLLM
## invoke(self, prompt: str)
Mock LLM để test logic mà không tốn API call (trả về JSON).
# get_mock_component_scores()
Bảng điểm Hard-code $V_k(c)$ cho 14 linh kiện để tiết kiệm 56 lần gọi API lúc test.
# generate_architectures(catalog)
Vét cạn tạo ra tất cả tổ hợp kiến trúc từ catalog.
# calculate_architecture_vk(arch: dict, component_scores: dict)
Tính $V_k(s)$ cho bản thiết kế $s$ bằng trung bình cộng $V_k(c)$ của 4 linh kiện.
# run_pipeline(prd_path: str, agent_ratios: dict, use_mock: bool = True)
- Phân tích PRD (Task 2.1) bằng [[prd_analyzer]].
- Phân bổ trọng số (Task 2.2) bằng [[weight_assigner]].
- Chấm điểm Linh kiện (Task 3.1)
- Sinh không gian kiến trúc & Tính hàm thoả dụng $U_i$ (Task 4.1) bằng `generate_architectures(catalog)` và [[DACN-261-Markov/main/conflict_checker|conflict_checker]].
- Tìm mức kỳ vọng lý tưởng (Max Utility) cho từng người
	- Nhớ kiểm tra conflict bằng `c_s = conflict_checker.check_conflicts(arch)`
	- Ghi nhận cực đại để khởi tạo $d_i$
- Giải bài toán mặc cả Nash (Task 4.2)
- Khởi tạo điểm sàn $d_i$ ở mức lý tưởng
- Tìm tập khả thi
	- Ràng buộc chặt chẽ: $U_i \ge d_i$ cho TẤT CẢ các bên
	- Tính tích Nash Logarit (cộng một hằng số nhỏ epsilon để tránh $\log 0$)
		$$\sum_i\log(u_i-d_i)$$
	- Nếu có nghiệm:
		- Chọn kiến trúc có Tích Nash cao nhất
	- Nếu vô nghiệm (deadlock tại vòng này) -> Áp dụng nhượng bộ (Distance-based Concession):
		- Hạ điểm sàn $d_i$ của tất cả mọi người xuống $\delta$ (nếu chưa chạm đáy)
- IN KẾT QUẢ
# main()
Gọi `run_pipeline`.