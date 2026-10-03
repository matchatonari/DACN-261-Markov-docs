---
tags:
  - dacn/DACN-261-Markov/zeuthen
---

# run\_pipeline(prd\_path: str, agent\_ratios: dict, use\_mock: bool = True)
- Sử dụng 50% utility lý tưởng.
- $d_i$ được giữ cố định trong toàn bộ quá trình đàm phán.
- Tạo preference ranking cho từng Agent
- Proposal hiện tại của mỗi Agent, ban đầu mỗi Agent chọn architecture có utility cao nhất đối với chính mình.
- Vòng lặp bargaining
	- Kiểm tra xem 3 Agent đã cùng proposal chưa
	- Nếu chưa thống nhất → [[zeuthen]]
	- Agent nhượng bộ: chuyển xuống architecture tiếp theo trong preference ranking của chính mình.
- Nếu đã có agreement nhưng muốn chọn Nash
	- Với cơ chế trên, agreement là architecture mà cả 3 proposal cùng hội tụ tới.
	- Nếu muốn kiểm tra lại toàn bộ tập architecture khả thi và lấy đúng Nash optimum trong tập đó, làm riêng.
## calculate\_nash\_log(item, d)
- Hàm tính Nash Product
- Architecture không đạt reservation utility ($d_i$) của một agent thì không phải nghiệm bargaining.