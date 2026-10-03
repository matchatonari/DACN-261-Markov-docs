---
tags:
  - dacn/DACN-261-Markov/AnhDuy
---

>Task 1.3 — Hàm phạt xung đột $C(s)$ dùng chung cho PO / BA / FE
>$$C(s) = C_{hard}(s) + C_{soft}(s)$$
Cứng (big-M tổng quát hoá, mang tính lexicographic, 0 nếu không vi phạm):
$$\Psi(s)    = \sum_{r \in Viol(s)} \lambda_r$$
>- $\lambda    = K * R_{\max} + M$
>- $C_{hard}(s) = \lambda * \Psi(s)$
Vì khi vi phạm thì $\Psi(s) >= \min r$,  $\lambda_r >= 1$ và $\lambda >= R_{\max} + M > R_{\max} - R_{\min}$, nên mọi kiến trúc vi phạm có $U_i$ nhỏ hơn mọi kiến trúc hợp lệ (với mọi agent i).
>
Mềm (ma trận tương thích A lấy bằng chứng từ ontology, đối xứng, trong $[0,1]$):
$$\rho(c,d)  = max( \rho_{c\to d}, \rho_{d\to c} )$$
>- $\rho_{c\to d} = \max_{a \in \text{avoid\_when}(c)} \max_{u \in \text{use\_cases}(d)} S_{hybrid}(a,u)$
>- $A_{XY}[c,d]  = \rho(c,d) * \sigma(c) * \sigma(d)$
>- $C_{soft}(s)  = \eta * \sum_{X<Y} w_{XY} * A_{XY}[c_X, c_Y]$
>- $\eta = \beta * (R_{\max} - R_{\min}) / \sum w_{XY}  \Rightarrow  C_{soft} \le \beta*(R_{\max}-R_{\min}) < \lambda$
($C_{soft}$ không bao giờ lật tính khả thi; nó chỉ nghiêng thứ hạng).

# pair_key(a, b)
Khoá chuẩn hoá cho một cặp category (thứ tự alphabet).
# ConflictChecker
## \_load\_rules(self)
## \_load\_matrix(self)
## calibrate(self, r\_min: float, r\_max: float) -> None
Chốt $\lambda$ và $\eta$ dựa trên dải thưởng hợp lệ thực tế $[r_{\min}, r_{\max}]$.
## soft\_bound(self) -> float
Cận trên của $C_{soft}(s) = \beta * (R_{\max} - R_{\min})$
## hard\_min(self) -> float
Cận dưới của C_hard(s) khi có ít nhất một vi phạm.
- bằng 0
- bằng $\lambda_{base} * \min \text{severity}$
## hard\_penalty(self, architecture: dict)
Trả về ($C_{hard}$, danh sách luật bị vi phạm).
## \_rho(self, cat\_c, c, cat\_d, d) -> float
Đặt $\rho$ vào cache.
## \_rho\_from\_catalog(self, cat\_c, c, cat\_d, d) -> float
### directed(cat\_a, a, cat\_b, b)
?
## \_sigma(self, category, component, engagement) -> float:
Tính $\sigma$.
## soft\_penalty(self, architecture: dict, engagement=None)
Trả về ($C_{soft}$, danh sách đóng góp theo cặp category).
## compute(self, architecture: dict, engagement=None) -> dict
Trả về breakdown đầy đủ của hàm phạt cho một kiến trúc.
## check\_conflicts(self, architecture: dict) -> float
Tương thích ngược: trả về tổng $C(s)$ dưới dạng float.