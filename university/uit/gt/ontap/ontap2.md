# Giải Đề Ôn Tập Giải Tích - Tổng Hợp Hoàn Chỉnh

## I. TỔNG HỢP LÝ THUYẾT

### 1. Tích phân suy rộng

#### Điều kiện hội tụ:
- **Tích phân từ 1 đến ∞:** $\int_1^{\infty} \frac{1}{x^p} dx$ hội tụ khi $p > 1$, phân kỳ khi $p \leq 1$
- **Tích phân có điểm kỳ dị:** $\int_a^b \frac{1}{(x-c)^q} dx$ hội tụ khi $q < 1$

#### Phương pháp so sánh:
- Nếu $0 \leq f(x) \leq g(x)$ và $\int g(x)dx$ hội tụ thì $\int f(x)dx$ hội tụ
- Nếu $f(x) \sim g(x)$ khi $x \to \infty$ thì hai tích phân cùng tính chất

### 2. Chuỗi số

#### Các tiêu chuẩn cơ bản:
- **Tiêu chuẩn tỉ số:** $\lim_{n \to \infty} \left|\frac{a_{n+1}}{a_n}\right| = L < 1$ ⟹ hội tụ
- **Tiêu chuẩn căn:** $\lim_{n \to \infty} \sqrt[n]{|a_n|} = L < 1$ ⟹ hội tụ  
- **Tiêu chuẩn so sánh:** So với chuỗi $p$-series: $\sum \frac{1}{n^p}$ hội tụ khi $p > 1$
- **Tiêu chuẩn đan dấu (Leibniz):** $\sum (-1)^n u_n$ hội tụ nếu $u_n \searrow 0$

### 3. Chuỗi lũy thừa

#### Bán kính hội tụ:
$$R = \frac{1}{\lim_{n \to \infty} \left|\frac{a_{n+1}}{a_n}\right|}$$

#### Miền hội tụ:
- Hội tụ tuyệt đối trong $|x-c| < R$
- Kiểm tra riêng tại các điểm biên $x = c \pm R$

### 4. Giới hạn hàm nhiều biến

#### Cách chứng minh giới hạn không tồn tại:
- Tìm hai đường tiến tới điểm mà cho giá trị giới hạn khác nhau
- Các đường thường dùng: trục tọa độ, đường thẳng $y = kx$, parabola $y = kx^2$

### 5. Đạo hàm riêng và cực trị

#### Điều kiện cần cho cực trị:
$$\nabla f(a,b) = (f_x, f_y) = (0,0)$$

#### Điều kiện đủ (định thức Hessian):
$$D(a,b) = f_{xx}f_{yy} - f_{xy}^2$$
- $D > 0$ và $f_{xx} > 0$ ⟹ cực tiểu
- $D > 0$ và $f_{xx} < 0$ ⟹ cực đại  
- $D < 0$ ⟹ điểm yên ngựa

#### Đạo hàm theo hướng:
$$D_{\vec{u}}f = \nabla f \cdot \vec{u}$$
Hướng tăng nhanh nhất là hướng của $\nabla f$

---

## II. GIẢI ĐỀ CHI TIẾT

### Câu 1: Xét sự hội tụ hay phân kỳ của tích phân

#### 1.1. $\int_1^{\infty} \frac{x^3 + \sin x}{x^5 + 2x + 1} dx$

**Lời giải:**
- Khi $x \to \infty$: $\frac{x^3 + \sin x}{x^5 + 2x + 1} \sim \frac{x^3}{x^5} = \frac{1}{x^2}$
- Vì $|\sin x| \leq 1$ nên tử số $\sim x^3$, mẫu số $\sim x^5$
- Ta có $\int_1^{\infty} \frac{1}{x^2} dx$ hội tụ (vì $p = 2 > 1$)
- **Kết luận:** Tích phân hội tụ

#### 1.2. $\int_1^{\infty} \frac{2x^2 + \arctan x}{x^{7/2} + 5x + 3} dx$

**Lời giải:**
- Khi $x \to \infty$: $\frac{2x^2 + \arctan x}{x^{7/2} + 5x + 3} \sim \frac{2x^2}{x^{7/2}} = \frac{2}{x^{3/2}}$
- Vì $\arctan x \to \pi/2$ (bị chặn), nên $2x^2 + \arctan x \sim 2x^2$
- Ta có $\int_1^{\infty} \frac{1}{x^{3/2}} dx$ hội tụ (vì $p = 3/2 > 1$)
- **Kết luận:** Tích phân hội tụ

#### 1.3. $\int_1^{\infty} \frac{\ln x + x}{x^3 - 1} dx$

**Lời giải:**
- Khi $x \to \infty$: $\frac{\ln x + x}{x^3 - 1} \sim \frac{x}{x^3} = \frac{1}{x^2}$
- Vì $\ln x < x$ với mọi $x > 0$, nên $\ln x + x \sim x$
- Ta có $\int_1^{\infty} \frac{1}{x^2} dx$ hội tụ
- **Kết luận:** Tích phân hội tụ

### Câu 2: Sự hội tụ của chuỗi số

#### 2.1. $\sum_{n=1}^{\infty} \frac{\ln n + 3}{n^3}$

**Lời giải:**
- Khi $n \to \infty$: $\frac{\ln n + 3}{n^3} \sim \frac{\ln n}{n^3}$
- Vì $\ln n < n^{\epsilon}$ với mọi $\epsilon > 0$, ta có $\frac{\ln n}{n^3} \leq \frac{1}{n^{2.5}}$
- Chuỗi $\sum \frac{1}{n^{2.5}}$ hội tụ (p-series với $p = 2.5 > 1$)
- **Kết luận:** Chuỗi hội tụ

#### 2.2. $\sum_{n=1}^{\infty} \frac{n^2 2^n}{n!}$

**Lời giải:**
Sử dụng tiêu chuẩn tỉ số:
$$\left|\frac{a_{n+1}}{a_n}\right| = \frac{(n+1)^2 2^{n+1}}{(n+1)!} \cdot \frac{n!}{n^2 2^n} = \frac{2(n+1)^2}{n^2(n+1)} = \frac{2(n+1)}{n^2}$$

Khi $n \to \infty$: $\frac{2(n+1)}{n^2} = \frac{2n + 2}{n^2} \to 0 < 1$
- **Kết luận:** Chuỗi hội tụ

#### 2.3. $\sum_{n=1}^{\infty} \left(\frac{n}{2n+1}\right)^n$

**Lời giải:**
Sử dụng tiêu chuẩn căn:
$$\sqrt[n]{|a_n|} = \frac{n}{2n+1}$$

Khi $n \to \infty$: $\frac{n}{2n+1} = \frac{1}{2 + 1/n} \to \frac{1}{2} < 1$
- **Kết luận:** Chuỗi hội tụ

### Câu 3: Tìm bán kính và miền hội tụ

#### 3.1. $\sum_{n=1}^{\infty} \frac{(-1)^n (x+1)^n}{2^n n^2}$

**Lời giải:**
Sử dụng tiêu chuẩn tỉ số:
$$\left|\frac{a_{n+1}}{a_n}\right| = \frac{1}{2} \cdot \frac{n^2}{(n+1)^2} \cdot |x+1| \to \frac{|x+1|}{2}$$

Chuỗi hội tụ khi $\frac{|x+1|}{2} < 1 \Rightarrow |x+1| < 2$
**Bán kính:** $R = 2$

**Kiểm tra tại biên:**
- Tại $x = 1$ (tức $x+1 = 2$): $\sum \frac{(-1)^n}{n^2}$ hội tụ (đan dấu)
- Tại $x = -3$ (tức $x+1 = -2$): $\sum \frac{1}{n^2}$ hội tụ

**Miền hội tụ:** $M = [-3, 1]$

#### 3.2. $\sum_{n=1}^{\infty} \frac{(x-3)^n}{n \cdot 5^n}$

**Lời giải:**
$$\left|\frac{a_{n+1}}{a_n}\right| = \frac{|x-3|}{5} \cdot \frac{n}{n+1} \to \frac{|x-3|}{5}$$

**Bán kính:** $R = 5$

**Kiểm tra tại biên:**
- Tại $x = 8$: $\sum \frac{1}{n}$ phân kỳ
- Tại $x = -2$: $\sum \frac{(-1)^n}{n}$ hội tụ (đan dấu)

**Miền hội tụ:** $M = [-2, 8)$

### Câu 4: Xét sự tồn tại của giới hạn

#### 4.1. $\lim_{(x,y) \to (0,0)} \frac{x^2 y^2}{x^4 + y^4}$

**Lời giải:**
- Theo $x = 0$: $f(0,y) = 0 \Rightarrow \lim = 0$
- Theo $y = 0$: $f(x,0) = 0 \Rightarrow \lim = 0$  
- Theo $x = y$: $f(x,x) = \frac{x^4}{2x^4} = \frac{1}{2} \Rightarrow \lim = \frac{1}{2}$

**Kết luận:** Giới hạn không tồn tại (có giá trị khác nhau)

#### 4.2. $\lim_{(x,y) \to (0,0)} \frac{x^3 y}{x^6 + y^2}$

**Lời giải:**
- Theo $x = 0$: $f(0,y) = 0 \Rightarrow \lim = 0$
- Theo $y = x^3$: $f(x,x^3) = \frac{x^6}{2x^6} = \frac{1}{2} \Rightarrow \lim = \frac{1}{2}$

**Kết luận:** Giới hạn không tồn tại

### Câu 5: Tìm và phân loại điểm cực trị

**Cho:** $f(x,y) = x^3 - 12xy + 8y^3$

**Bước 1:** Tìm điểm tới hạn
$\nabla f = (3x^2 - 12y, -12x + 24y^2) = (0,0)$

Hệ phương trình:
$\begin{cases}
3x^2 - 12y = 0 \Rightarrow x^2 = 4y \\
-12x + 24y^2 = 0 \Rightarrow x = 2y^2
\end{cases}$

Thế $x = 2y^2$ vào phương trình đầu:
$(2y^2)^2 = 4y \Rightarrow 4y^4 = 4y \Rightarrow y^4 - y = 0 \Rightarrow y(y^3 - 1) = 0$

Do đó $y = 0$ hoặc $y^3 = 1 \Rightarrow y = 1$
- Với $y = 0$: $x = 2(0)^2 = 0$ → điểm $(0,0)$
- Với $y = 1$: $x = 2(1)^2 = 2$ → điểm $(2,1)$

**Nghiệm:** $(0,0)$ và $(2,1)$

**Bước 2:** Phân loại
$$D(x,y) = f_{xx}f_{yy} - f_{xy}^2 = (6x)(24y) - (-12)^2 = 144xy - 144$$

- Tại $(0,0)$: $D = -144 < 0$ → **Điểm yên ngựa**
- Tại $(2,1)$: $D = 144 > 0$ và $f_{xx} = 12 > 0$ → **Cực tiểu địa phương**

### Câu 6: Tìm giá trị lớn nhất và nhỏ nhất

**Cho:** $f(x,y) = x^2 - 2xy + 2y$ trên $D = \{0 \leq x \leq 3, 0 \leq y \leq 2\}$

**Bước 1:** Điểm tới hạn bên trong
$$\nabla f = (2x - 2y, -2x + 2) = (0,0) \Rightarrow (x,y) = (1,1)$$
$$f(1,1) = 1$$

**Bước 2:** Cực trị trên biên

- **Biên $x = 0$:** $f(0,y) = 2y$
  - Min: $f(0,0) = 0$, Max: $f(0,2) = 4$

- **Biên $x = 3$:** $f(3,y) = 9 - 4y$  
  - Min: $f(3,2) = 1$, Max: $f(3,0) = 9$

- **Biên $y = 0$:** $f(x,0) = x^2$
  - Min: $f(0,0) = 0$, Max: $f(3,0) = 9$

- **Biên $y = 2$:** $f(x,2) = x^2 - 4x + 4 = (x-2)^2$
  - Min: $f(2,2) = 0$, Max: $f(0,2) = f(3,2) = 4$

**Kết luận:**
- **Giá trị nhỏ nhất:** $0$ tại $(0,0)$ và $(2,2)$
- **Giá trị lớn nhất:** $9$ tại $(3,0)$

### Câu 7: Tốc độ thay đổi lớn nhất

**Cho:** $f(x,y) = \sqrt{x^2 + y^3}$ tại $(1,2)$

**Lời giải:**
$$\nabla f = \left(\frac{x}{\sqrt{x^2 + y^3}}, \frac{3y^2}{2\sqrt{x^2 + y^3}}\right)$$

Tại $(1,2)$:
$$\nabla f(1,2) = \left(\frac{1}{\sqrt{1+8}}, \frac{3 \cdot 4}{2\sqrt{1+8}}\right) = \left(\frac{1}{3}, \frac{6}{3}\right) = \left(\frac{1}{3}, 2\right)$$

**Hướng tăng nhanh nhất:** $\left(\frac{1}{3}, 2\right)$

**Tốc độ thay đổi lớn nhất:**
$$|\nabla f(1,2)| = \sqrt{\frac{1}{9} + 4} = \sqrt{\frac{37}{9}} = \frac{\sqrt{37}}{3}$$

---

## III. TÍCH PHÂN BỘI VÀ TÍCH PHÂN ĐƯỜNG

### Tích phân bội

**Ví dụ:** $\iint_D (2x + y) \, dA$ với $D = \{0 \leq x \leq 2, x^2 \leq y \leq 2x\}$

**Lời giải:**
$$I = \int_0^2 \int_{x^2}^{2x} (2x + y) \, dy \, dx$$
$$= \int_0^2 \left[2xy + \frac{y^2}{2}\right]_{x^2}^{2x} dx$$
$$= \int_0^2 \left[4x^2 - 2x^3 + 2x^2 - \frac{x^4}{2}\right] dx$$
$$= \int_0^2 \left(6x^2 - 2x^3 - \frac{x^4}{2}\right) dx$$
$$= \left[2x^3 - \frac{x^4}{2} - \frac{x^5}{10}\right]_0^2 = 16 - 8 - \frac{32}{10} = \frac{24}{5}$$

### Tích phân đường

**Ví dụ:** $\int_C x^3 \, ds$ với $C: y = x^2, 0 \leq x \leq 2$

**Lời giải:**
- Tham số: $x = t, y = t^2, 0 \leq t \leq 2$
- $ds = \sqrt{1 + (2t)^2} dt = \sqrt{1 + 4t^2} dt$
- Tích phân: $\int_0^2 t^3 \sqrt{1 + 4t^2} dt$

---

## IV. PHƯƠNG PHÁP GIẢI TỔNG QUÁT

### Tích phân suy rộng
1. Xét hành vi tại vô cực hoặc điểm kỳ dị
2. So sánh với tích phân chuẩn đã biết
3. Sử dụng phương pháp so sánh giới hạn

### Chuỗi số  
1. Kiểm tra điều kiện cần: $a_n \to 0$
2. Áp dụng tiêu chuẩn phù hợp
3. Với đan dấu: kiểm tra điều kiện Leibniz

### Giới hạn hàm nhiều biến
1. Thử theo các trục tọa độ
2. Thử theo đường thẳng $y = kx$
3. Thử theo đường cong (parabola, hyperbola)
4. Nếu tìm được hai đường cho kết quả khác nhau → giới hạn không tồn tại

### Cực trị hàm nhiều biến
1. Tìm điểm tới hạn: $\nabla f = 0$
2. Tính ma trận Hessian
3. Xét dấu định thức $D$ và $f_{xx}$
4. Với bài toán có ràng buộc: xét cả biên

### Tích phân bội
1. Xác định miền tích phân
2. Chọn thứ tự tích phân phù hợp  
3. Tính tích phân trong từng từ ngoài ra

### Tích phân đường
1. Tham số hóa đường cong
2. Tính $ds$ từ đạo hàm tham số
3. Chuyển về tích phân một biến

---

*Lưu ý: Đây là tài liệu tổng hợp hoàn chỉnh bao gồm cả lý thuyết và bài tập. Các bạn nên nắm vững lý thuyết trước khi làm bài tập để đạt hiệu quả cao nhất.*