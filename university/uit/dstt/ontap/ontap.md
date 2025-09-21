# Tổng hợp Đại số Tuyến Tính

## Mục Lục
1. [Ma trận và các phép toán](#1-ma-trận-và-các-phép-toán)
2. [Định thức](#2-định-thức)
3. [Hệ phương trình tuyến tính và quy tắc Cramer](#3-hệ-phương-trình-tuyến-tính-và-quy-tắc-cramer)
4. [Không gian vector con và độc lập tuyến tính](#4-không-gian-vector-con-và-độc-lập-tuyến-tính)
5. [Cơ sở và tọa độ](#5-cơ-sở-và-tọa-độ)
6. [Chéo hóa ma trận](#6-chéo-hóa-ma-trận)

---

## 1. Ma trận và các phép toán

### 1.1. Phép cộng hai ma trận
**Điều kiện**: Hai ma trận phải cùng kích thước n × m

**Công thức**: 
```
(A + B)ᵢⱼ = aᵢⱼ + bᵢⱼ
```

**Ví dụ**:
```
[1 2]   [2 1]   [3 3]
[1 3] + [0 2] = [1 5]
[2 1]   [1 3]   [3 4]
```

### 1.2. Nhân ma trận với số thực
**Công thức**: Nhân từng phần tử của ma trận với số thực k

**Ví dụ**:
```
A = [1 2]  →  kA = [k  2k]
    [1 3]        [k  3k]
    [2 1]        [2k  k]
```

### 1.3. Nhân hai ma trận
**Điều kiện**: Ma trận A (n × m) nhân với ma trận B (m × k) = AB (n × k)

**Công thức**: 
```
(AB)ᵢⱼ = Σₖ aᵢₖbₖⱼ = (dòng i của A) × (cột j của B)
```

**Ví dụ**:
```
[1 2 3] × [1]   = 1×1 + 2×1 + 3×2 = 9
          [1]
          [2]
```

**Lưu ý**: Phép nhân ma trận không có tính giao hoán: AB ≠ BA

### 1.4. Phép chuyển vị
**Định nghĩa**: Biến dòng thành cột

**Ví dụ**:
```
A = [1 -1  1]  →  A^T = [1 -1 -2]
    [-1 2  1]           [-1  2  3]
    [-2 3  1]           [1   1  1]
```

**Tính chất**:
- (A + B)^T = A^T + B^T
- (AB)^T = B^T A^T
- rank(A) = rank(A^T)
- (A^T)^(-1) = (A^(-1))^T

### 1.5. Ma trận khả nghịch
**Định nghĩa**: Ma trận vuông A (n × n) có nghịch đảo A^(-1) nếu:
```
AA^(-1) = A^(-1)A = I
```

**Điều kiện**: A khả nghịch ⟺ rref(A) = I ⟺ rank(A) = n

**Cách tìm**:
```
[A|I] → [I|A^(-1)]
```

---

## 2. Định thức

### 2.1. Ma trận 2×2
```
det([a b]) = ad - bc
   ([c d])
```

### 2.2. Ma trận 3×3
Sử dụng khai triển theo hàng hoặc cột:
```
det(A) = aᵢⱼ × (-1)^(i+j) × Mᵢⱼ
```
trong đó Mᵢⱼ là định thức con.

### 2.3. Tính chất
- Nếu có một hàng/cột toàn số 0 → det = 0
- Đổi chỗ hai hàng → đổi dấu định thức
- Nhân một hàng với k → định thức nhân với k
- Cộng bội của hàng này vào hàng khác → định thức không đổi

---

## 3. Hệ phương trình tuyến tính và quy tắc Cramer

### 3.1. Dạng tổng quát
```
AX = b
```
trong đó A là ma trận hệ số, X là vector ẩn, b là vector hằng số.

### 3.2. Quy tắc Cramer
**Điều kiện**: det(A) ≠ 0

**Nghiệm**:
```
xᵢ = det(Aᵢ)/det(A)
```
trong đó Aᵢ là ma trận A với cột thứ i được thay bằng vector b.

### 3.3. Biện luận hệ phương trình theo tham số

**Bước 1**: Tính det(A) theo tham số
**Bước 2**: Biện luận:
- Nếu det(A) ≠ 0: Hệ có nghiệm duy nhất (dùng Cramer)
- Nếu det(A) = 0: Dùng phương pháp Gauss để kiểm tra
  - Nếu rank(A) = rank([A|b]): Hệ có vô số nghiệm
  - Nếu rank(A) < rank([A|b]): Hệ vô nghiệm

---

## 4. Không gian vector con và độc lập tuyến tính

### 4.1. Không gian vector con W ⊂ R^n
**Điều kiện**:
1. Chứa phần tử không: 0 ∈ W
2. Ổn định với phép cộng và nhân: ∀u,v ∈ W, k ∈ R: u + kv ∈ W

### 4.2. Tập sinh (Span)
```
span{v₁, v₂, ..., vₘ} = {v = α₁v₁ + α₂v₂ + ... + αₘvₘ : αᵢ ∈ R}
```

### 4.3. Độc lập tuyến tính
**Định nghĩa**: Họ vector {v₁, v₂, ..., vₘ} độc lập tuyến tính nếu:
```
c₁v₁ + c₂v₂ + ... + cₘvₘ = 0
```
có duy nhất nghiệm c₁ = c₂ = ... = cₘ = 0

**Kiểm tra**:
1. **Phương pháp 1**: rank[v₁, v₂, ..., vₘ] = m
2. **Phương pháp 2**: (Nếu ma trận vuông) det[v₁, v₂, ..., vₘ] ≠ 0

### 4.4. Tìm cơ sở của không gian nghiệm

**Các bước**:
1. Lập ma trận hệ số mở rộng [A|0]
2. Đưa về dạng RREF bằng phép khử Gauss-Jordan
3. Xác định ẩn cơ sở và ẩn tự do
4. Viết nghiệm tổng quát
5. Tách thành các vector cơ sở

**Ví dụ**: Tìm cơ sở của W = {(x₁,x₂,x₃) : x₁ + 2x₂ + 3x₃ = 0}

Nghiệm tổng quát: x₃ = a (tùy ý)
```
[x₁]     [1 ]
[x₂] = a [-2]
[x₃]     [1 ]
```

Vậy W = span{(1,-2,1)}, dim(W) = 1

---

## 5. Cơ sở và tọa độ

### 5.1. Cơ sở
**Định nghĩa**: B = {v₁, v₂, ..., vₘ} là cơ sở của W nếu:
1. Độc lập tuyến tính
2. span{v₁, v₂, ..., vₘ} = W

### 5.2. Tọa độ
**Định nghĩa**: Tọa độ của v theo cơ sở B:
```
[v]ᵦ = [c₁, c₂, ..., cₘ]^T
```
thỏa mãn: v = c₁v₁ + c₂v₂ + ... + cₘvₘ

### 5.3. Ma trận chuyển cơ sở
```
P_{B→B'} = [[v₁]ᵦ ; [v₂]ᵦ ; ... ; [vₙ]ᵦ]
```

**Tính chất**:
- P_{B→B'} = (P_{B'→B})^(-1)
- P_{B→A} = P_{B→C} × P_{C→A}
- P_{B→A} = B^(-1) × A

---

## 6. Chéo hóa ma trận

### 6.1. Trị riêng và vector riêng
**Trị riêng λ**: Nghiệm của phương trình đặc trưng
```
det(A - λI) = 0
```

**Vector riêng**: Nghiệm khác 0 của hệ
```
(A - λI)x = 0
```

### 6.2. Chéo hóa
**Định nghĩa**: A chéo hóa được nếu:
```
A = PDP^(-1)
```
trong đó D là ma trận chéo, P là ma trận khả nghịch.

**Điều kiện**: A chéo hóa được ⟺ A có đúng n vector riêng độc lập tuyến tính.

### 6.3. Các bước chéo hóa

**Bước 1**: Tìm trị riêng bằng cách giải det(A - λI) = 0

**Bước 2**: Với mỗi trị riêng λᵢ, tìm vector riêng bằng cách giải (A - λᵢI)x = 0

**Bước 3**: Lập ma trận:
- P: ma trận có các cột là vector riêng
- D: ma trận chéo có các phần tử là trị riêng tương ứng

### 6.4. Ứng dụng
**Tính lũy thừa ma trận**:
```
A^n = PD^nP^(-1)
```

### 6.5. Chéo hóa trực giao
**Điều kiện**: Ma trận A đối xứng

**Kết quả**: A = PDP^T với P là ma trận trực chuẩn

**Quy trình Gram-Schmidt**: Để trực chuẩn hóa các vector riêng

---

## Công thức quan trọng cần nhớ

### Ma trận 2×2
```
A^(-1) = 1/det(A) × [d  -b]  (với det(A) = ad - bc)
                    [-c   a]
```

### Quy tắc Cramer
```
x₁ = det(A₁)/det(A), x₂ = det(A₂)/det(A), ...
```

### Kiểm tra độc lập tuyến tính
```
rank[v₁, v₂, ..., vₘ] = m
```

### Chuyển cơ sở
```
[v]ᵦ = P_{B'→B} × [v]ᵦ'
```

### Chéo hóa
```
A = PDP^(-1), A^n = PD^nP^(-1)
```