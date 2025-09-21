# Tổng hợp kiến thức Toán học - Giải tích (Phiên bản đầy đủ)

## Mục lục
1. [Tích phân và Tích phân suy rộng](#1-tích-phân-và-tích-phân-suy-rộng)
2. [Chuỗi số và Chuỗi lũy thừa](#2-chuỗi-số-và-chuỗi-lũy-thừa)
3. [Đạo hàm và Ứng dụng](#3-đạo-hàm-và-ứng-dụng)
4. [Giới hạn hàm nhiều biến và Chứng minh không tồn tại](#4-giới-hạn-hàm-nhiều-biến-và-chứng-minh-không-tồn-tại)
5. [Cực trị hàm nhiều biến](#5-cực-trị-hàm-nhiều-biến)
6. [Đạo hàm riêng và Đạo hàm theo hướng](#6-đạo-hàm-riêng-và-đạo-hàm-theo-hướng)
7. [Tích phân bội](#7-tích-phân-bội)
8. [Tích phân đường](#8-tích-phân-đường)

---

## 1. Tích phân và Tích phân suy rộng

### 1.1. Định nghĩa

**Tích phân xác định:** 
```
∫[a→b] f(x)dx với f liên tục trên [a,b]
```

**Tích phân suy rộng có hai loại:**
- **Loại 1:** Có cận vô hạn
- **Loại 2:** Hàm có điểm gián đoạn vô cực trong khoảng lấy tích phân

### 1.2. Ví dụ cơ bản

**Ví dụ 1 (hội tụ):** 
```
∫[1→∞] (1/x²)dx = lim[t→∞] ∫[1→t] (1/x²)dx = lim[t→∞] [-1/x]₁ᵗ = 1
```

**Ví dụ 2 (phân kỳ):**
```
∫[1→∞] (1/x)dx = lim[t→∞] [ln x]₁ᵗ = ∞
```

**Ví dụ 3 (điểm gián đoạn):**
```
∫[2→5] 1/√(x-2) dx = lim[t→2⁺] [2√(x-2)]ₜ⁵ = 2√3
```

### 1.3. Công cụ so sánh cốt lõi (P-integral)

**Tại vô cực:**
```
∫[a→∞] 1/xᵖ dx
```
- Hội tụ nếu p > 1
- Phân kỳ nếu p ≤ 1

**Tại điểm gián đoạn 0:**
```
∫[0→a] 1/xᵖ dx
```
- Hội tụ nếu p < 1
- Phân kỳ nếu p ≥ 1

### 1.4. Lộ trình 4 bước "Phá đảo" tích phân suy rộng

**Bước 1: Ước lượng "Sức mạnh"**
Bảng xếp hạng khi x→∞:
1. Hàm mũ: eˣ, 3ˣ (mạnh nhất)
2. Lũy thừa: xⁿ
3. Logarit: ln(x) (yếu nhất trong các hàm tăng)
4. Hàm bị chặn: sin(x), cos(x), arctan(x)

**Bước 2: Lựa chọn tiêu chuẩn**
- **Tiêu chuẩn so sánh giới hạn:** `L = lim[x→∞] f(x)/g(x)`
- **Tiêu chuẩn so sánh trực tiếp:** Dùng bất đẳng thức

**Bước 3 và 4:** Áp dụng và kết luận

### 1.5. Ví dụ minh họa chi tiết

**Ví dụ:** `∫[1→∞] (ln(x)+3)/x³ dx`
- So sánh với g(x) = 1/x²
- L = lim[x→∞] [(ln(x)+3)/x³] / [1/x²] = 0
- Vì L = 0 và ∫[1→∞] 1/x² dx hội tụ → Tích phân ban đầu hội tụ

---

## 2. Chuỗi số và Chuỗi lũy thừa

### 2.1. Định nghĩa chuỗi số

**Chuỗi số:** `∑[k=1→∞] aₖ`
**Tổng riêng phần:** `sₙ = ∑[k=1→n] aₖ`
- Hội tụ nếu sₙ → s (hữu hạn)
- Phân kỳ nếu sₙ không hội tụ hoặc hội tụ về vô cùng

### 2.2. Chuỗi cơ bản

**Chuỗi hình học:** `∑ arⁿ⁻¹`
- Hội tụ nếu |r| < 1, tổng = a/(1-r)
- Phân kỳ nếu |r| ≥ 1

**Chuỗi p-series:** `∑ 1/nᵖ`
- Hội tụ nếu p > 1
- Phân kỳ nếu p ≤ 1

### 2.3. Tiêu chuẩn xét hội tụ

**1. Điều kiện cần (Tiêu chuẩn phân kỳ):**
Nếu `lim[n→∞] aₙ ≠ 0` thì chuỗi phân kỳ

**2. Tiêu chuẩn so sánh trực tiếp:**
Nếu 0 ≤ aₙ ≤ bₙ và ∑bₙ hội tụ thì ∑aₙ hội tụ

**3. Tiêu chuẩn so sánh giới hạn:**
```
L = lim[n→∞] aₙ/bₙ
```
- Nếu 0 < L < ∞: hai chuỗi cùng tính chất
- Nếu L = 0 và ∑bₙ hội tụ thì ∑aₙ hội tụ
- Nếu L = ∞ và ∑bₙ phân kỳ thì ∑aₙ phân kỳ

**4. Tiêu chuẩn tỉ số (D'Alembert):**
```
L = lim[n→∞] |aₙ₊₁/aₙ|
```
- L < 1: hội tụ tuyệt đối
- L > 1: phân kỳ
- L = 1: không kết luận

**5. Tiêu chuẩn căn thức (Cauchy):**
```
L = lim[n→∞] ⁿ√|aₙ|
```
Kết luận tương tự tiêu chuẩn tỉ số

**6. Tiêu chuẩn đan dấu (Leibniz):**
Chuỗi `∑ (-1)ⁿuₙ` hội tụ nếu:
- uₙ > 0, giảm dần
- lim[n→∞] uₙ = 0

### 2.4. Chuỗi lũy thừa

**Dạng tổng quát:** `∑ aₙ(x-c)ⁿ`

**Bán kính hội tụ R:**
```
L = lim[n→∞] |aₙ₊₁/aₙ|
```
Chuỗi hội tụ khi |x-c| < 1/L = R

**Miền hội tụ:** (c-R, c+R) cộng các điểm biên (nếu hội tụ)

### 2.5. Ví dụ chi tiết

**Ví dụ 1:** `∑ (-3)ⁿxⁿ/√(n+1)`

Bước 1: Tìm bán kính
```
|aₙ₊₁/aₙ| = 3|x| √(n+1)/√(n+2) → 3|x|
```
Chuỗi hội tụ khi 3|x| < 1 ⟹ R = 1/3

Bước 2: Xét biên
- Tại x = 1/3: ∑(-1)ⁿ/√(n+1) hội tụ (đan dấu)
- Tại x = -1/3: ∑1/√(n+1) phân kỳ (p = 1/2 ≤ 1)

Miền hội tụ: (-1/3, 1/3]

---

## 3. Đạo hàm và Ứng dụng

### 3.1. Định nghĩa

```
f'(x₀) = lim[h→0] [f(x₀+h) - f(x₀)]/h
```

**Ý nghĩa:**
- Hệ số góc tiếp tuyến
- Tốc độ thay đổi tức thời

### 3.2. Các ví dụ tính đạo hàm từ định nghĩa

**Ví dụ 1:** f(x) = √x
```
f'(x) = lim[h→0] (√(x+h) - √x)/h = 1/(2√x)
```

**Ví dụ 2:** f(x) = |x| tại x = 0
```
lim[h→0⁺] |h|/h = 1
lim[h→0⁻] |h|/h = -1
```
Đạo hàm không tồn tại tại x = 0

### 3.3. Ứng dụng

**Phương trình tiếp tuyến:**
```
y = f'(x₀)(x - x₀) + y₀
```

**Tìm cực trị:**
- Điều kiện cần: f'(x₀) = 0
- Điều kiện đủ:
  - f''(x₀) > 0: cực tiểu
  - f''(x₀) < 0: cực đại

**Thuật toán tìm cực trị trên [a,b]:**
1. Tìm điểm tới hạn: f'(x) = 0 hoặc không tồn tại
2. Tính f tại các điểm tới hạn và tại a, b
3. So sánh để tìm max, min

### 3.4. Quy tắc L'Hôpital

```
lim[x→a] f(x)/g(x) = lim[x→a] f'(x)/g'(x)
```
(Khi có dạng 0/0 hoặc ∞/∞)

---

## 4. Giới hạn hàm nhiều biến và Chứng minh không tồn tại

### 4.1. Định nghĩa giới hạn

```
lim[(x,y)→(a,b)] f(x,y) = L
```

### 4.2. Cách tính giới hạn

**Thay trực tiếp:** Nếu hàm liên tục tại điểm đó

**Ví dụ:**
```
lim[(x,y)→(1,2)] (x²y + 2xy) = 1² · 2 + 2 · 1 · 2 = 6
```

### 4.3. Chứng minh giới hạn không tồn tại

**Phương pháp:** Tìm hai đường khác nhau tiến đến điểm mà cho giới hạn khác nhau

**Ví dụ 1:** `lim[(x,y)→(0,0)] (x²-y²)/(x²+y²)`
- Theo trục Ox (y=0): giới hạn = 1
- Theo trục Oy (x=0): giới hạn = -1
- Kết luận: giới hạn không tồn tại

**Ví dụ 2:** `lim[(x,y)→(0,0)] xy²/(x²+y⁴)`
- Theo y=0: giới hạn = 0
- Theo x=0: giới hạn = 0
- Theo x=y²: giới hạn = 1/2
- Kết luận: giới hạn không tồn tại

**Các đường thường dùng:**
- y = 0, x = 0
- y = kx
- y = x², x = y²
- Đường parabol tổng quát

### 4.4. Ví dụ nâng cao

**Ví dụ 3:** `lim[(x,y)→(0,0)] xy/(x+y)`
Cần tìm đường phù hợp để có giới hạn khác 0:
- Chọn x = y²-y, ta được giới hạn → -1

---

## 5. Cực trị hàm nhiều biến

### 5.1. Cực trị không điều kiện

**Điều kiện cần:** `∇f(a,b) = 0`, tức `fₓ(a,b) = 0` và `f_y(a,b) = 0`

**Ma trận Hessian:**
```
D(x,y) = |fₓₓ  fₘy| = fₓₓf_yy - f²ₘy
         |fₘy  f_yy|
```

**Điều kiện đủ:** Giả sử ∇f(a,b) = 0
- D(a,b) > 0 và fₓₓ(a,b) > 0: (a,b) là cực tiểu
- D(a,b) > 0 và fₓₓ(a,b) < 0: (a,b) là cực đại  
- D(a,b) < 0: (a,b) là điểm yên ngựa

### 5.2. Ví dụ chi tiết

**Ví dụ:** f(x,y) = x⁴ + y⁴ - 4xy + 1

Bước 1: Tìm điểm tới hạn
```
fₓ = 4x³ - 4y = 0  ⟹  y = x³
f_y = 4y³ - 4x = 0  ⟹  x = y³
```
Thế vào: x = (x³)³ = x⁹ ⟹ x(x⁸-1) = 0
Nghiệm: (0,0), (1,1), (-1,-1)

Bước 2: Tính định thức
```
fₓₓ = 12x²,  f_yy = 12y²,  fₘy = -4
D(x,y) = 144x²y² - 16
```

Bước 3: Phân loại
- (0,0): D = -16 < 0 → điểm yên ngựa
- (1,1): D = 128 > 0, fₓₓ = 12 > 0 → cực tiểu
- (-1,-1): D = 128 > 0, fₓₓ = 12 > 0 → cực tiểu

### 5.3. Cực trị có điều kiện (trên miền đóng bị chặn)

**Thuật toán:**
1. Tìm điểm tới hạn trong miền: ∇f = 0
2. Tìm cực trị trên biên của miền
3. So sánh tất cả giá trị

**Ví dụ:** f(x,y) = x² - 2xy + 2y trên D = {0 ≤ x ≤ 3, 0 ≤ y ≤ 2}

Bước 1: Điểm tới hạn
```
fₓ = 2x - 2y = 0
f_y = -2x + 2 = 0
```
Nghiệm: (1,1) với f(1,1) = 1

Bước 2: Trên các cạnh biên
- y = 0: f(x,0) = x² → min tại (0,0), max tại (3,0)
- x = 3: f(3,y) = -4y + 9 → min tại (3,2), max tại (3,0)
- y = 2: f(x,2) = x² - 4x + 4 → min tại (2,2), max tại (0,2) và (3,2)
- x = 0: f(0,y) = 2y → min tại (0,0), max tại (0,2)

Bước 3: So sánh
Min = 0 tại (0,0) và (2,2), Max = 9 tại (3,0)

---

## 6. Đạo hàm riêng và Đạo hàm theo hướng

### 6.1. Đạo hàm riêng

**Định nghĩa:**
```
fₓ(x,y) = lim[h→0] [f(x₀+h,y₀) - f(x₀,y₀)]/h
f_y(x,y) = lim[h→0] [f(x₀,y₀+h) - f(x₀,y₀)]/h
```

**Cách tính:** Đạo hàm theo một biến, coi biến kia là hằng số

### 6.2. Đạo hàm cấp cao

- fₓₓ = (fₓ)ₓ
- fₓᵧ = (fₓ)ᵧ
- fᵧᵧ = (fᵧ)ᵧ
- fᵧₓ = (fᵧ)ₓ

**Định lý Schwarz:** Nếu fₓ, fᵧ liên tục thì fₓᵧ = fᵧₓ

### 6.3. Ví dụ tính toán

**Ví dụ 1:** f(x,y) = x³ + x²y³ - 2y²
```
fₓ = 3x² + 2xy³
fᵧ = 3x²y² - 4y
fₓₓ = 6x + 2y³
fᵧᵧ = 6x²y - 4
fₓᵧ = 6xy² = fᵧₓ
```

**Ví dụ 2:** f(x,y) = cos(y²x)
```
fₓ = -y² sin(y²x)
fᵧ = -2xy sin(y²x)
fₓₓ = -y⁴ cos(y²x)
fᵧᵧ = -2x sin(y²x) - 4x²y² cos(y²x)
fₓᵧ = -2y sin(y²x) - 2xy³ cos(y²x)
```

### 6.4. Mặt phẳng tiếp xúc

```
z - z₀ = fₓ(x₀,y₀)(x - x₀) + fᵧ(x₀,y₀)(y - y₀)
```

### 6.5. Đạo hàm hợp

Nếu z = f(x,y) với x = x(t), y = y(t):
```
dz/dt = (∂z/∂x)(dx/dt) + (∂z/∂y)(dy/dt)
```

**Ví dụ:** z = x²y + 3xy⁴ với x = sin(2t), y = cos(t)
```
dz/dt = (2xy + 3y⁴)(2cos(2t)) + (x² + 12xy³)(-sin(t))
```

### 6.6. Đạo hàm theo hướng

Cho vector đơn vị u = (a,b) với a² + b² = 1:
```
D_u f(x₀,y₀) = ∇f(x₀,y₀) · u = fₓ(x₀,y₀)a + fᵧ(x₀,y₀)b
```

**Ví dụ:** f(x,y) = x³ - 3xy + 4y², u = (cos(π/6), sin(π/6)), tại P(1,2)
```
∇f(1,2) = (-3, 13)
D_u f(1,2) = -3·cos(π/6) + 13·sin(π/6) = -3√3/2 + 13/2
```

---

## 7. Tích phân bội

### 7.1. Tích phân kép trên hình chữ nhật

Trên R = [a,b] × [c,d]:
```
∬_R f(x,y)dA = ∫[a→b]∫[c→d] f(x,y)dy dx = ∫[c→d]∫[a→b] f(x,y)dx dy
```

### 7.2. Tích phân kép trên miền tổng quát

**Miền loại I:** D = {a ≤ x ≤ b, g(x) ≤ y ≤ h(x)}
```
∬_D f(x,y)dA = ∫[a→b]∫[g(x)→h(x)] f(x,y)dy dx
```

**Miền loại II:** D = {c ≤ y ≤ d, p(y) ≤ x ≤ q(y)}
```
∬_D f(x,y)dA = ∫[c→d]∫[p(y)→q(y)] f(x,y)dx dy
```

### 7.3. Ví dụ chi tiết

**Ví dụ:** `∬_D (x + 2y)dA` với D = {0 ≤ x ≤ 2, x² ≤ y ≤ 2x}

```
∬_D (x + 2y)dA = ∫[0→2]∫[x²→2x] (x + 2y)dy dx
                = ∫[0→2] [xy + y²]_{y=x²}^{y=2x} dx
                = ∫[0→2] [x(2x) + (2x)² - x(x²) - (x²)²] dx
                = ∫[0→2] [2x² + 4x² - x³ - x⁴] dx
                = ∫[0→2] [6x² - x³ - x⁴] dx
```

### 7.4. Đổi thứ tự tích phân

**Ví dụ:** Đổi từ dxdy sang dydx
```
∬_D (x + 2y)dA = ∫[0→4]∫[y/2→√y] (x + 2y)dx dy
```

---

## 8. Tích phân đường

### 8.1. Tích phân đường loại 1

```
∫_C f(x,y)ds
```

**Cách tính:** Nếu C có phương trình tham số x = x(t), y = y(t), t ∈ [a,b]:
```
ds = √[(dx/dt)² + (dy/dt)²] dt
∫_C f(x,y)ds = ∫[a→b] f(x(t),y(t))√[(x'(t))² + (y'(t))²] dt
```

### 8.2. Ví dụ tích phân đường loại 1

**Ví dụ:** `∫_C (2 + x²y)ds` trên nửa đường tròn đơn vị trên

1. Tham số hóa: x = cos(t), y = sin(t), t ∈ [0,π]
2. Tính ds: ds = dt
3. Tính tích phân:
```
∫_C (2 + x²y)ds = ∫[0→π] (2 + cos²(t)sin(t))dt = 2π + 2/3
```

### 8.3. Tích phân đường loại 2

```
∫_C P(x,y)dx + Q(x,y)dy
```

**Cách tính:** Nếu C: x = x(t), y = y(t), t ∈ [a,b]:
```
∫_C P(x,y)dx + Q(x,y)dy = ∫[a→b] [P(x(t),y(t))x'(t) + Q(x(t),y(t))y'(t)]dt
```

### 8.4. Tính chất

- Tích phân loại 1: `∫_C f ds = ∫_{-C} f ds` (không phụ thuộc hướng)
- Tích phân loại 2: `∫_C P dx + Q dy = -∫_{-C} P dx + Q dy` (phụ thuộc hướng)

### 8.5. Ví dụ tích phân đường loại 2

**Ví dụ:** `∫_C y²dx + xdy` từ (-5,-3) đến (0,2)

Tham số hóa đoạn thẳng:
```
x = -5(1-t), y = -3 + 5t, t ∈ [0,1]
dx = 5dt, dy = 5dt

∫_C y²dx + xdy = ∫[0→1] [(-3+5t)²·5 + (-5(1-t))·5] dt
```

---

## Phụ lục: Công thức và Bảng tra cứu

### A. Giới hạn đặc biệt
- `lim[x→0] sin(x)/x = 1`
- `lim[n→∞] (1 + 1/n)ⁿ = e`
- `lim[n→∞] (1 - 1/n)ⁿ = e⁻¹`

### B. Chuỗi Taylor cơ bản
- `eˣ = 1 + x + x²/2! + x³/3! + ...`
- `sin(x) = x - x³/3! + x⁵/5! - ...`
- `cos(x) = 1 - x²/2! + x⁴/4! - ...`

### C. Tích phân cơ bản
- `∫ 1/x dx = ln|x| + C`
- `∫ eˣ dx = eˣ + C`
- `∫ sin(x) dx = -cos(x) + C`
- `∫ cos(x) dx = sin(x) + C`

### D. Quy tắc tham số hóa đường thẳng
Từ điểm (x₀,y₀) đến (x₁,y₁):
```
x = x₀(1-t) + x₁t
y = y₀(1-t) + y₁t
với t ∈ [0,1]
```

### E. Công thức Newton-Raphson
```
xₙ = xₙ₋₁ - f(xₙ₋₁)/f'(xₙ₋₁)
```

---

## 9. Tọa độ cực và Chuyển đổi tọa độ trong tích phân

### 9.1. Tọa độ cực (r, θ)

**Chuyển đổi:**
```
x = r cos θ
y = r sin θ
r² = x² + y²
tan θ = y/x
```

**Jacobian:** `J = r`

**Công thức tích phân:**
```
∬_D f(x,y)dA = ∬_D f(r cos θ, r sin θ) r dr dθ
```

### 9.2. Ví dụ tọa độ cực

**Ví dụ 1:** Tính `∬_D (x² + y²) dA` với D là hình tròn x² + y² ≤ 4

```
D trong tọa độ cực: 0 ≤ r ≤ 2, 0 ≤ θ ≤ 2π
∬_D (x² + y²) dA = ∫₀²π ∫₀² r² · r dr dθ = ∫₀²π ∫₀² r³ dr dθ = 8π
```

**Ví dụ 2:** Tính diện tích miền giới hạn bởi r = 1 + cos θ

```
Diện tích = ∫₀²π ∫₀^(1+cosθ) r dr dθ = (3π)/2
```

### 9.3. Tọa độ trụ (r, θ, z)

**Chuyển đổi:**
```
x = r cos θ
y = r sin θ  
z = z
```

**Jacobian:** `J = r`

**Tích phân ba:** 
```
∭_E f(x,y,z)dV = ∭_E f(r cos θ, r sin θ, z) r dr dθ dz
```

---

## 10. Định lý Green và Tích phân đường loại 2

### 10.1. Định lý Green

Cho C là đường cong đóng, định hướng dương bao quanh miền D:

```
∮_C P dx + Q dy = ∬_D (∂Q/∂x - ∂P/∂y) dA
```

### 10.2. Điều kiện độc lập đường đi

Tích phân `∫_C P dx + Q dy` độc lập đường đi khi và chỉ khi:
```
∂P/∂y = ∂Q/∂x
```

**Hàm thế:** Nếu ∂P/∂y = ∂Q/∂x thì tồn tại hàm f sao cho:
```
∇f = (P, Q)
hay f_x = P và f_y = Q
```

### 10.3. Ví dụ ứng dụng Định lý Green

**Ví dụ:** Tính `∮_C (x² - y²) dx + 2xy dy` với C là đường tròn x² + y² = 4

```
P = x² - y², Q = 2xy
∂P/∂y = -2y, ∂Q/∂x = 2y
∂Q/∂x - ∂P/∂y = 2y - (-2y) = 4y

Áp dụng Green:
∮_C = ∬_D 4y dA = ∫₀²π ∫₀² 4r sin θ · r dr dθ = 0
```

---

## 11. Phương trình vi phân (Bổ sung cơ bản)

### 11.1. Phương trình tách biến

**Dạng:** `dy/dx = g(x)h(y)`

**Cách giải:**
```
dy/h(y) = g(x)dx
∫ dy/h(y) = ∫ g(x)dx + C
```

### 11.2. Phương trình tuyến tính cấp 1

**Dạng:** `dy/dx + P(x)y = Q(x)`

**Nghiệm:**
```
y = e^(-∫P(x)dx) [∫ Q(x)e^(∫P(x)dx) dx + C]
```

### 11.3. Ví dụ phương trình vi phân

**Ví dụ 1:** `dy/dx = xy`
```
dy/y = x dx
ln|y| = x²/2 + C
y = Ae^(x²/2)
```

**Ví dụ 2:** `dy/dx + y = e^x`
```
Hệ số tích phân: μ(x) = e^x
Nghiệm: y = e^(-x)[∫ e^x · e^x dx + C] = e^(-x)[e^(2x)/2 + C] = e^x/2 + Ce^(-x)
```

---

## 12. Chuỗi Fourier (Giới thiệu cơ bản)

### 12.1. Chuỗi Fourier của hàm tuần hoàn

Cho hàm f(x) tuần hoàn chu kỳ 2π:

```
f(x) = a₀/2 + Σ(aₙ cos(nx) + bₙ sin(nx))
```

**Hệ số Fourier:**
```
a₀ = (1/π) ∫₋π^π f(x) dx
aₙ = (1/π) ∫₋π^π f(x) cos(nx) dx
bₙ = (1/π) ∫₋π^π f(x) sin(nx) dx
```

### 12.2. Ví dụ chuỗi Fourier

**Hàm vuông:** f(x) = 1 nếu 0 < x < π, f(x) = -1 nếu -π < x < 0

```
f(x) = (4/π) Σ sin((2n-1)x)/(2n-1)
     = (4/π)[sin(x) + sin(3x)/3 + sin(5x)/5 + ...]
```

---

## 13. Phương pháp số (Numerical Methods)

### 13.1. Phương pháp Newton-Raphson (Bổ sung chi tiết)

**Mục tiêu:** Giải phương trình f(x) = 0

**Công thức lặp:**
```
xₙ₊₁ = xₙ - f(xₙ)/f'(xₙ)
```

**Điều kiện hội tụ:**
- f'(x) ≠ 0 gần nghiệm
- Chọn x₀ đủ gần nghiệm thực

### 13.2. Phương pháp tích phân số

**Quy tắc hình thang:**
```
∫ₐᵇ f(x)dx ≈ (b-a)/2 [f(a) + f(b)]
```

**Quy tắc Simpson:**
```
∫ₐᵇ f(x)dx ≈ (b-a)/6 [f(a) + 4f((a+b)/2) + f(b)]
```

### 13.3. Phương pháp Euler cho phương trình vi phân

**Bài toán:** dy/dx = f(x,y), y(x₀) = y₀

**Công thức Euler:**
```
yₙ₊₁ = yₙ + h·f(xₙ, yₙ)
xₙ₊₁ = xₙ + h
```

---

## 14. Ma trận Hessian và Dạng toàn phương (Bổ sung)

### 14.1. Ma trận Hessian

Cho f(x,y), ma trận Hessian tại (a,b):

```
H = [fₓₓ  fₓᵧ]
    [fₓᵧ  fᵧᵧ]
```

**Định thức:** `D = fₓₓfᵧᵧ - f²ₓᵧ`

### 14.2. Phân loại điểm tới hạn (Tổng kết)

Tại điểm tới hạn (a,b) với ∇f(a,b) = 0:

```
D > 0, fₓₓ > 0 → Cực tiểu
D > 0, fₓₓ < 0 → Cực đại  
D < 0         → Điểm yên ngựa
D = 0         → Không kết luận
```

### 14.3. Ví dụ phân tích hoàn chỉnh

**Bài toán:** f(x,y) = x³ + y³ - 3xy

```
Bước 1: fₓ = 3x² - 3y = 0 ⟹ y = x²
        fᵧ = 3y² - 3x = 0 ⟹ x = y²

Thế: x = (x²)² = x⁴ ⟹ x(x³ - 1) = 0
Nghiệm: (0,0), (1,1)

Bước 2: fₓₓ = 6x, fᵧᵧ = 6y, fₓᵧ = -3
        D(x,y) = 36xy - 9

Tại (0,0): D = -9 < 0 → Điểm yên ngựa
Tại (1,1): D = 27 > 0, fₓₓ = 6 > 0 → Cực tiểu
```

---

## 15. Ứng dụng thực tế

### 15.1. Bài toán tối ưu hóa

**Ví dụ:** Thiết kế hộp có thể tích lớn nhất từ tấm tôn vuông

Cho tấm tôn vuông cạnh a, cắt 4 góc để gấp thành hộp.

```
V(x) = x(a-2x)² với 0 < x < a/2
V'(x) = (a-2x)² - 4x(a-2x) = (a-2x)(a-6x)
V'(x) = 0 ⟹ x = a/6
```

### 15.2. Bài toán vật lý

**Trọng tâm:** 
```
x̄ = (1/A)∬ₐ x dA
ȳ = (1/A)∬ₐ y dA
```

**Mômen quán tính:**
```
Iₓ = ∬ₐ y² ρ(x,y) dA
Iᵧ = ∬ₐ x² ρ(x,y) dA
```

---

## 16. Công thức tham khảo nhanh

### 16.1. Tích phân cơ bản

```
∫ 1/(x²+a²) dx = (1/a)arctan(x/a) + C
∫ 1/√(a²-x²) dx = arcsin(x/a) + C  
∫ x/(x²+a²) dx = (1/2)ln(x²+a²) + C
∫ eᵃˣ dx = (1/a)eᵃˣ + C
```

### 16.2. Chuỗi Taylor thường dùng

```
eˣ = 1 + x + x²/2! + x³/3! + ...
sin(x) = x - x³/3! + x⁵/5! - ...
cos(x) = 1 - x²/2! + x⁴/4! - ...
ln(1+x) = x - x²/2 + x³/3 - ... (|x| < 1)
(1+x)ᵅ = 1 + αx + α(α-1)x²/2! + ... (|x| < 1)
```

### 16.3. Bảng đạo hàm cơ bản

```
(xⁿ)' = nxⁿ⁻¹
(eˣ)' = eˣ
(ln x)' = 1/x
(sin x)' = cos x
(cos x)' = -sin x
(tan x)' = sec²x
(arcsin x)' = 1/√(1-x²)
(arctan x)' = 1/(1+x²)
```

---

## 17. Lời khuyên ôn thi

### 17.1. Chiến lược làm bài

1. **Đọc kỹ đề:** Xác định dạng bài và phương pháp
2. **Kiểm tra điều kiện:** Miền xác định, điều kiện hội tụ
3. **Tính toán cẩn thận:** Kiểm tra từng bước
4. **Kiểm tra kết quả:** So sánh với trường hợp đặc biệt

### 17.2. Các lỗi thường gặp

- **Tích phân suy rộng:** Quên xét điểm gián đoạn
- **Chuỗi số:** Nhầm lẫn tiêu chuẩn so sánh
- **Giới hạn hàm nhiều biến:** Không thử đủ đường
- **Cực trị:** Quên kiểm tra biên miền
- **Tích phân bội:** Sai thứ tự tích phân

### 17.3. Mẹo ghi nhớ

- **P-integral:** "p > 1 hội tụ ở vô cực, p < 1 hội tụ ở 0"
- **Chuỗi hình học:** "|r| < 1 thì hội tụ"
- **Định lý Green:** "Quay ngược kim đồng hồ là dương"
- **Jacobian:** "Nhớ nhân với r trong tọa độ cực"

---