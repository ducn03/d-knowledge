# Tổng hợp Đại số Tuyến Tính - Đầy đủ và Chi tiết

## Mục Lục
1. [Ma trận và các phép toán](#1-ma-trận-và-các-phép-toán)
2. [Định thức](#2-định-thức)  
3. [Hệ phương trình tuyến tính và Biện luận](#3-hệ-phương-trình-tuyến-tính-và-biện-luận)
4. [Không gian vector con R^n](#4-không-gian-vector-con-rn)
5. [Cơ sở và Độc lập tuyến tính](#5-cơ-sở-và-độc-lập-tuyến-tính)
6. [Tọa độ và Chuyển cơ sở](#6-tọa-độ-và-chuyển-cơ-sở)
7. [Chéo hóa ma trận](#7-chéo-hóa-ma-trận)

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
A = [1 2]  →  kA = [k  2k]  (với k ∈ R)
    [1 3]        [k  3k]
    [2 1]        [2k  k]
```

### 1.3. Nhân hai ma trận

**Điều kiện**: Ma trận A (n × m) nhân với ma trận B (m × k) = AB (n × k)

**Công thức**: 
```
(AB)ᵢⱼ = Σₖ aᵢₖbₖⱼ = (dòng i của A) × (cột j của B)
```

**Ví dụ đơn giản**:
```
A = [1 2 3] (1×3, vector hàng)
B = [1]     (3×1, vector cột)
    [1]
    [2]

(AB) = [1 2 3] × [1] = 1×1 + 2×1 + 3×2 = 9
                  [1]
                  [2]
```

**Ví dụ tổng quát**:
```
[1 2] × [1 1] = [1×1+2×1  1×1+2×2] = [3 5]
[1 3]   [1 2]   [1×1+3×1  1×1+3×2]   [4 7]
[2 1]           [2×1+1×1  2×1+1×2]   [3 4]
```

**Ví dụ kiểm tra tính giao hoán**:
```
A = [1 2]    B = [2 1]
    [1 1]        [1 3]

AB = [4 7]  ≠  [3 5] = BA
     [3 4]     [4 5]
```
**Kết luận**: Nhân hai ma trận không có tính giao hoán.

### 1.4. Phép chuyển vị

**Định nghĩa**: Biến dòng thành cột

**Ví dụ**:
```
A = [1 -1  1]  →  A^T = [1 -1 -2]
    [-1 2  1]           [-1  2  3] 
    [-2 3  1]           [1   1  1]

B = [1 2]  →  B^T = [1 1 2]
    [1 3]           [2 3 1]
    [2 1]
```

**Các tính chất quan trọng**:
- (A + B)^T = A^T + B^T
- (AB)^T = B^T A^T
- rank(A) = rank(A^T)
- (A^T)^(-1) = (A^(-1))^T

### 1.5. Ma trận khả nghịch

**Định nghĩa**: Ma trận vuông A (n × n) có nghịch đảo A^(-1) nếu:
```
AA^(-1) = A^(-1)A = I (ma trận đơn vị n×n)
```

**Lưu ý**: Không phải ma trận vuông nào cũng khả nghịch được.

**Định lý**: A khả nghịch ⟺ rref(A) = I ⟺ rank(A) = n

#### 1.5.1. Cách tìm ma trận nghịch đảo

**Phương pháp**: 
```
[A|I] → [I|A^(-1)]
```

**Ví dụ chi tiết**:
```
A = [1 1 1]
    [2 3 2]
    [3 8 2]

[1 1 1 | 1 0 0]
[2 3 2 | 0 1 0] : d₂ - 2d₁, d₃ - 3d₁
[3 8 2 | 0 0 1]

→ [1 1 1 | 1  0 0]
  [0 1 0 | -2 1 0] : d₁ - d₂, d₃ - 5d₂  
  [0 5 -1| -3 0 1]

→ [1 0 1 | 3  -1 0]
  [0 1 0 | -2  1 0] : d₃ × (-1)
  [0 0 -1| 7  -5 1]

→ [1 0 1 | 3  -1  0]
  [0 1 0 | -2  1  0] : d₁ - d₃
  [0 0 1 | -7  5 -1]

→ [1 0 0 | 10 -6  1]
  [0 1 0 | -2  1  0]
  [0 0 1 | -7  5 -1]
```

**Vậy**: 
```
A^(-1) = [10 -6  1]
         [-2  1  0]
         [-7  5 -1]
```

#### 1.5.2. Ứng dụng giải hệ phương trình

**Hệ phương trình**:
```
x₁ + x₂ + x₃ = 2
2x₁ + 3x₂ + 2x₃ = 5  
3x₁ + 8x₂ + 2x₃ = 7
```

**Dạng ma trận**: AX = b
```
[1 1 1] [x₁]   [2]
[2 3 2] [x₂] = [5]
[3 8 2] [x₃]   [7]
```

**Nghiệm**: X = A^(-1)b

#### 1.5.3. Bài tập tự giải

Tìm nghịch đảo của:
```
A = [1 -1  1]
    [-1 2  1]
    [-2 3  1]
```

**Lời giải**:
```
[1 -1  1 | 1 0 0]
[-1 2  1 | 0 1 0] : d₂ + d₁, d₃ + 2d₁
[-2 3  1 | 0 0 1]

→ [1 -1 1 | 1 0 0]
  [0  1 2 | 1 1 0] : d₁ + d₂, d₃ - d₂
  [0  1 3 | 2 0 1]

→ [1 0 3 | 2  1 0]
  [0 1 2 | 1  1 0] : d₁ - 3d₃, d₂ - 2d₃
  [0 0 1 | 1 -1 1]

→ [1 0 0 | -1  4 -3]
  [0 1 0 | -1  3 -2]
  [0 0 1 |  1 -1  1]
```

---

## 2. Định thức

### 2.1. Định thức ma trận 2×2

**Công thức**:
```
det([a b]) = ad - bc
   ([c d])
```

### 2.2. Định thức ma trận 3×3

**Khai triển theo cột đầu**:
```
A = [1 -1  1]
    [-1 2  1]  
    [-2 3  1]

det(A) = 1×(-1)^(1+1)|2  1| + (-1)×(-1)^(2+1)|(-1) 1| + (-2)×(-1)^(3+1)|(-1) 1|
                      |3  1|                    |3   1|                     |2   1|
```

**Khai triển theo dòng thứ 2**:
```
det(A) = (-1)×(-1)^(2+1)|(-1) 1| + 2×(-1)^(2+2)|1  1| + 1×(-1)^(2+3)|1 (-1)|
                         |3   1|                |(-2) 1|              |(-2) 3|
```

### 2.3. Phương pháp hiệu quả - Biến đổi sơ cấp

**Nguyên tắc**:
- Đổi chỗ hai dòng: đổi dấu định thức
- Nhân một dòng với k ≠ 0: định thức nhân với k  
- Cộng bội của dòng này vào dòng khác: định thức không đổi

**Ví dụ**:
```
A = [-1  1  4]
    [ 5 -3  0]
    [ 3  2  2]

Biến đổi: d₂ + 5d₁, d₃ + 3d₁

→ [-1  1  4]
  [ 0  2 20]  
  [ 0  5 14]

Tiếp tục: d₃ - (5/2)d₂

→ [-1  1  4]
  [ 0  2 20]
  [ 0  0  4]

det(A) = (-1) × 2 × 4 = -8
```

### 2.4. Ma trận có nhiều số 0

**Chiến lược**: Khai triển theo hàng/cột có nhiều số 0 nhất

**Ví dụ**:
```
A = [1 0 1 2]
    [9 1 3 0]
    [9 2 2 0] 
    [5 0 0 3]
```

Khai triển theo cột 4 (có 2 số 0):
```
det(A) = 2×(-1)^(1+4)×M₁₄ + 0 + 0 + 3×(-1)^(4+4)×M₄₄
       = -2×M₁₄ + 3×M₄₄
```

---

## 3. Hệ phương trình tuyến tính và Biện luận

### 3.1. Quy tắc Cramer

**Dạng hệ**: AX = b
**Điều kiện**: det(A) ≠ 0

**Công thức nghiệm**:
```
x₁ = det(A₁)/det(A)
x₂ = det(A₂)/det(A)  
x₃ = det(A₃)/det(A)
```

**Trong đó**: Aᵢ là ma trận A với cột thứ i được thay bằng vector b

#### 3.1.1. Ví dụ áp dụng

**Hệ phương trình**:
```
x₁ + 2x₃ = 6
-3x₁ + 4x₂ + 6x₃ = 30
-x₁ - 2x₂ + 3x₃ = 8
```

**Ma trận hệ số**:
```
A = [ 1  0  2]    b = [ 6]
    [-3  4  6]        [30]
    [-1 -2  3]        [ 8]
```

**Tính định thức**:
```
det(A) = 44 ≠ 0
```

**Ma trận thay thế**:
```
A₁ = [ 6  0  2]    det(A₁) = -40
     [30  4  6]
     [ 8 -2  3]

A₂ = [ 1  6  2]    det(A₂) = 72  
     [-3 30  6]
     [-1  8  3]

A₃ = [ 1  0  6]    det(A₃) = 152
     [-3  4 30]
     [-1 -2  8]
```

**Nghiệm**:
```
x₁ = -40/44 = -10/11
x₂ = 72/44 = 18/11
x₃ = 152/44 = 38/11
```

### 3.2. Biện luận hệ phương trình theo tham số

#### 3.2.1. Ví dụ 1

**Hệ phương trình**:
```
mx + y + z = 1
x + my + z = m  
x + y + mz = m²
```

**Bước 1**: Tính det(A) theo m
```
A = [m 1 1]
    [1 m 1]
    [1 1 m]

det(A) = m×(m² - 1) - (m - 1) + (1 - m) = m³ - 3m + 2
       = (m - 1)²(m + 2)
```

**Bước 2**: Biện luận

**TH1**: m ≠ 1 và m ≠ -2 ⇒ det(A) ≠ 0
- Theo quy tắc Cramer, hệ có nghiệm duy nhất

**TH2**: m = 1
```
Hệ trở thành: [1 1 1 | 1]
              [1 1 1 | 1] → [1 1 1 | 1]
              [1 1 1 | 1]   [0 0 0 | 0]
                            [0 0 0 | 0]
```
- Hệ có vô số nghiệm: x₁ + x₂ + x₃ = 1
- Đặt x₂ = a, x₃ = b ⇒ x₁ = 1 - a - b

**TH3**: m = -2
```
Hệ trở thành: [-2  1  1 |  1]
              [ 1 -2  1 | -2] → ... → [1 0 0 | ...]
              [ 1  1 -2 |  4]                   [0 1 0 | ...]
                                               [0 0 0 |  3]
```
- Hệ vô nghiệm (xuất hiện dòng 0 0 0 | 3)

#### 3.2.2. Ví dụ 2

**Hệ phương trình**:
```
x + y - 3z = 1
2x + y + mz = 3
x + my + 3z = 2
```

**Bước 1**: Tính det(A)
```
A = [1  1 -3]
    [2  1  m]
    [1  m  3]

det(A) = 1×(3 - m²) - 2×(3 + 3m) + 1×(m + 3)
       = -m² - 5m
       = -m(m + 5)
```

**Bước 2**: Biện luận

**TH1**: m ≠ 0 và m ≠ -5 ⇒ det(A) ≠ 0
- Hệ có nghiệm duy nhất

**TH2**: m = 0
```
[1  1 -3 | 1]
[2  1  0 | 3] → [1  1 -3 | 1]
[1  0  3 | 2]   [0 -1  6 | 1]
                [0 -1  6 | 1]

→ [1  0  3 | 2]
  [0  1 -6 |-1]
  [0  0  0 | 0]
```
- Hệ có vô số nghiệm với z = a (tùy ý):
  - x = 2 - 3a
  - y = -1 + 6a  
  - z = a

**TH3**: m = -5
```
[1  1 -3 | 1]
[2  1 -5 | 3] → ... → [1 0 0 | ...]
[1 -5  3 | 2]                  [0 1 0 | ...]
                               [0 0 0 | -5]
```
- Hệ vô nghiệm

---

## 4. Không gian vector con R^n

### 4.1. Định nghĩa không gian vector con

**Nhắc lại**: R^n = {x = (x₁, x₂, ..., xₙ) : xᵢ ∈ R} là không gian vector.

**Tập W ⊂ R^n** được gọi là không gian vector con nếu:

1. **Chứa phần tử không**: 0 = (0,0,...,0) ∈ W
2. **Ổn định với phép cộng và nhân**: ∀u,v ∈ W và k ∈ R:
   - u + v ∈ W và ku ∈ W
   - Tương đương: u + kv ∈ W

### 4.2. Ví dụ kiểm tra không gian vector con

#### 4.2.1. Ví dụ 1 (Đúng)

```
W = {(z₁, z₂, z₃) : z₁ + 2z₂ - 3z₃ = 0} ⊂ R³
```

**Kiểm tra**:

1. **Chứa 0**: (0,0,0) thỏa 0 + 2×0 - 3×0 = 0 ✓

2. **Ổn định**: Lấy u = (x₁,x₂,x₃), v = (y₁,y₂,y₃) ∈ W và k ∈ R
   - u ∈ W ⇒ x₁ + 2x₂ - 3x₃ = 0
   - v ∈ W ⇒ y₁ + 2y₂ - 3y₃ = 0
   
   Kiểm tra u + v:
   ```
   u + v = (x₁+y₁, x₂+y₂, x₃+y₃)
   (x₁+y₁) + 2(x₂+y₂) - 3(x₃+y₃) = (x₁+2x₂-3x₃) + (y₁+2y₂-3y₃) = 0 + 0 = 0 ✓
   ```
   
   Kiểm tra ku:
   ```
   ku = (kx₁, kx₂, kx₃)  
   kx₁ + 2kx₂ - 3kx₃ = k(x₁ + 2x₂ - 3x₃) = k×0 = 0 ✓
   ```

**Kết luận**: W là không gian vector con của R³.

#### 4.2.2. Ví dụ 2 (Sai)

```
W = {(z₁, z₂) : z₁, z₂ ≥ 0} ⊂ R²
```

**Phản ví dụ**: Lấy u = (1,1) ∈ W và k = -1
- ku = (-1,1) ∉ W vì có tọa độ âm

**Kết luận**: W không là không gian vector con.

### 4.3. Tập sinh (Span)

**Định nghĩa**: Cho họ vector v₁, v₂, ..., vₘ ∈ R^n:
```
span{v₁, v₂, ..., vₘ} = {v = α₁v₁ + α₂v₂ + ... + αₘvₘ : αᵢ ∈ R}
```

**Mệnh đề**: span{v₁, v₂, ..., vₘ} là một không gian vector con của R^n.

**Thuật ngữ**: v = α₁v₁ + α₂v₂ + ... + αₘvₘ gọi là **tổ hợp tuyến tính** theo v₁, v₂, ..., vₘ.

### 4.4. Bài toán thực tế

**Cho**:
```
v₁ = [1]    v₂ = [2]    v₃ = [2]    v₄ = [4]
     [1]         [2]         [3]         [4]
     [1]         [2]         [4]         [4]
```

**Đặt**:
- W = span{v₁, v₂, v₃, v₄}
- V = span{v₁, v₃}

**Nhận xét**: V = W vì v₁, v₃ đã "tốt" rồi → Cần tìm cách "tốt nhất"?

---

## 5. Cơ sở và Độc lập tuyến tính

### 5.1. Độc lập tuyến tính

**Định nghĩa**: Họ vector v₁, v₂, ..., vₘ ∈ R^n được gọi là **độc lập tuyến tính** nếu:
```
c₁v₁ + c₂v₂ + ... + cₘvₘ = 0
```
có duy nhất nghiệm c₁ = c₂ = ... = cₘ = 0.

**Ý nghĩa**: Không thể biểu diễn vector nào thông qua tổ hợp tuyến tính của các vector còn lại.

### 5.2. Cách kiểm tra độc lập tuyến tính

#### 5.2.1. Phương pháp 1: Định nghĩa

**Ví dụ**:
```
v₁ = [1]    v₂ = [2]    v₃ = [2]
     [1]         [2]         [3]
     [1]         [2]         [4]
```

Xét: c₁v₁ + c₂v₂ + c₃v₃ = 0
```
c₁[1] + c₂[2] + c₃[2] = [0]
  [1]     [2]     [3]   [0]
  [1]     [2]     [4]   [0]

⇔ [c₁ + 2c₂ + 2c₃] = [0]
  [c₁ + 2c₂ + 3c₃]   [0]
  [c₁ + 2c₂ + 4c₃]   [0]
```

Hệ phương trình:
```
c₁ + 2c₂ + 2c₃ = 0
c₁ + 2c₂ + 3c₃ = 0
c₁ + 2c₂ + 4c₃ = 0
```

Có nghiệm không tầm thường ⇒ **phụ thuộc tuyến tính**.

#### 5.2.2. Phương pháp 2: Sử dụng rank

**Tương đương 1**: 
```
rank[v₁, v₂, ..., vₘ] = m
```

**Ví dụ**:
```
[1 2 2]        [1 2 2]
[1 2 3] → ... → [0 0 1] 
[1 2 4]        [0 0 0]
```

rank = 2 ≠ 3 ⇒ **phụ thuộc tuyến tính**.

#### 5.2.3. Phương pháp 3: Định thức (ma trận vuông)

**Tương đương 2**: Nếu [v₁, v₂, ..., vₘ] là ma trận vuông:
```
det[v₁, v₂, ..., vₘ] ≠ 0
```

### 5.3. Thuật toán tìm vector độc lập tuyến tính

**Bài toán**: Từ họ vector cho trước, tìm các vector độc lập tuyến tính.

#### 5.3.1. Ví dụ 1

```
v₁ = [1]    v₂ = [0]    v₃ = [2]
     [2]         [1]         [3]
     [-1]        [1]         [-3]
```

**Các bước**:
```
[1  0  2]
[2  1  3] : d₂ - 2d₁, d₃ + d₁
[-1 1 -3]

→ [1  0  2]
  [0  1 -1] : d₃ - d₂  
  [0  1 -1]

→ [1  0  2]
  [0  1 -1]
  [0  0  0]
```

**Kết luận**: 
- v₁ và v₂ độc lập tuyến tính
- v₃ = 2v₁ - v₂

#### 5.3.2. Ví dụ 2

```
[4  2  6  4]
[-5 -2 -3 -1]
[2  1  3  5]
[6  3  9  6]
```

**Biến đổi**:
```
[4  2  6  4] ÷ 4
[-5 -2 -3 -1]     
[2  1  3  5]      
[6  3  9  6]      

→ [1   0.5  1.5  1]
  [0   0.5  4.5  4] : d₂ × 2, d₃ ÷ 3
  [0   0    0    3]
  [0   0    0    0]

→ [1  0.5  1.5  1]
  [0  1    9    8] : d₁ - 0.5d₂
  [0  0    0    1]
  [0  0    0    0]

→ [1  0  -3   1]
  [0  1   9   0] : d₁ - d₃
  [0  0   0   1]
  [0  0   0   0]

→ [1  0  -3   0]
  [0  1   9   0]
  [0  0   0   1]
  [0  0   0   0]
```

**Kết luận**: v₁, v₂, v₄ độc lập tuyến tính. Hơn nữa, v₃ = -3v₁ + 9v₂.

### 5.4. Cơ sở và Số chiều

**Định nghĩa**: v₁, v₂, ..., vₘ ∈ W (với W là kgvt con của R^n) gọi là **cơ sở của W** nếu:
1. v₁, v₂, ..., vₘ độc lập tuyến tính  
2. span{v₁, v₂, ..., vₘ} = W

**Số chiều** của W là số vector trong cơ sở, ký hiệu dim(W).

### 5.5. Tìm cơ sở của không gian nghiệm

#### 5.5.1. Ví dụ đơn giản

**Bài toán**: Chứng minh W là kgvt con và tìm cơ sở, số chiều:
```
W = {(x₁,x₂,x₃) : x₁ + 2x₂ + 3x₃ = 0
                  2x₁ + 3x₂ + 4x₃ = 0  
                  4x₁ + 5x₂ + 6x₃ = 0}
```

**Giải**: Tìm nghiệm tổng quát của hệ:
```
[1 2 3 | 0]
[2 3 4 | 0] : d₂ - 2d₁, d₃ - 4d₁
[4 5 6 | 0]

→ [1  2  3 | 0]
  [0 -1 -2 | 0] : d₂ × (-1)
  [0 -3 -6 | 0]

→ [1 2  3 | 0]
  [0 1  2 | 0] : d₃ + 3d₂, d₁ - 2d₂
  [0 -3 -6| 0]

→ [1 0 -1 | 0]
  [0 1  2 | 0]
  [0 0  0 | 0]
```

Đặt x₃ = a (tùy ý):
```
x₁ - a = 0  ⟹  x₁ = a
x₂ + 2a = 0 ⟹  x₂ = -2a
x₃ = a
```

**Nghiệm tổng quát**:
```
[x₁]     [a ]     [1 ]
[x₂] = a [-2a] = a[-2]
[x₃]     [a ]     [1 ]
```

**Kết luận**: 
- W = span{(1,-2,1)} → W là kgvt con
- Cơ sở: {(1,-2,1)}
- Số chiều: dim(W) = 1

#### 5.5.2. Ví dụ phức tạp

**Bài toán**: Tìm cơ sở của không gian nghiệm:
```
[1 -1  2  0  1 -3 | 0]
[-1 2 -3  1  0  2 | 0]  
[1  0  0  2  1 -2 | 0]
```

**Biến đổi Gauss-Jordan**:
```
[1 -1  2  0  1 -3 | 0]
[0  1 -1  1  1 -1 | 0] : d₂ + d₁, d₃ - d₁
[0  1 -2  2  0  1 | 0]

→ [1  0  1  1  2 -4 | 0] : d₁ + d₂, d₃ - d₂
  [0  1 -1  1  1 -1 | 0]
  [0  0  1 -1 -1  2 | 0]

→ [1  0  0  2  3 -6 | 0] : d₁ - d₃, d₂ + d₃
  [0  1  0  0  0  1 | 0]
  [0  0  1 -1 -1  2 | 0]
```

**Phân tích**: 3 phương trình, 6 ẩn → 3 ẩn tự do

**Ẩn cơ sở**: x₁, x₂, x₃ (tương ứng với các cột có pivot)
**Ẩn tự do**: x₄, x₅, x₆

Đặt x₄ = a, x₅ = b, x₆ = c:
```
x₁ + 2a + 3b - 6c = 0  ⟹  x₁ = -2a - 3b + 6c
x₂ + c = 0            ⟹  x₂ = -c
x₃ - a - b + 2c = 0   ⟹  x₃ = a + b - 2c
```

**Nghiệm tổng quát**:
```
[x₁]   [-2a - 3b + 6c]     [-2]     [-3]     [6 ]
[x₂]   [-c           ] = a [ 0] + b [-0] + c [-1]
[x₃] = [a + b - 2c   ]     [ 1]     [ 1]     [-2]
[x₄]   [a            ]     [ 1]     [ 0]     [ 0]
[x₅]   [b            ]     [ 0]     [ 1]     [ 0]
[x₆]   [c            ]     [ 0]     [ 0]     [ 1]
```

**Kết luận**:
- W = span{v₁, v₂, v₃} với:
  ```
  v₁ = [-2, 0, 1, 1, 0, 0]ᵀ
  v₂ = [-3, 0, 1, 0, 1, 0]ᵀ  
  v₃ = [6, -1, -2, 0, 0, 1]ᵀ
  ```
- Cơ sở: {v₁, v₂, v₃}
- Số chiều: dim(W) = 3

### 5.6. Phương pháp tổng quát tìm cơ sở không gian nghiệm

#### 5.6.1. Các bước thực hiện

**Bước 1**: Lập ma trận hệ số mở rộng [A|0]

**Bước 2**: Dùng phép khử Gauss-Jordan để đưa về dạng RREF

**Bước 3**: Xác định ẩn cơ sở và ẩn tự do
- **Ẩn cơ sở**: Tương ứng với các cột có pivot (số 1 dẫn đầu)
- **Ẩn tự do**: Các ẩn còn lại

**Bước 4**: Viết nghiệm tổng quát
- Biểu diễn ẩn cơ sở theo ẩn tự do
- Đặt ẩn tự do bằng tham số

**Bước 5**: Tách vector cơ sở
- Viết nghiệm dưới dạng vector cột
- Tách thành tổng các vector theo từng tham số

#### 5.6.2. Mẹo nhận biết ẩn cơ sở

**Quan sát ma trận RREF**:
```
[1  0  -3   0]  ← Hàng 1: pivot ở cột 1 ⟹ x₁ là ẩn cơ sở
[0  1   9   0]  ← Hàng 2: pivot ở cột 2 ⟹ x₂ là ẩn cơ sở  
[0  0   0   1]  ← Hàng 3: pivot ở cột 4 ⟹ x₄ là ẩn cơ sở
[0  0   0   0]
```

**Kết luận**: 
- Ẩn cơ sở: x₁, x₂, x₄
- Ẩn tự do: x₃

---

## 6. Tọa độ và Chuyển cơ sở

### 6.1. Khái niệm tọa độ

**Định nghĩa**: Cho B = {v₁, v₂, ..., vₘ} là cơ sở của W. 
Với v ∈ W, **tọa độ của v theo cơ sở B** là:
```
[v]ᵦ = (c₁, c₂, ..., cₘ)ᵀ
```
thỏa mãn: v = c₁v₁ + c₂v₂ + ... + cₘvₘ

### 6.2. Ví dụ tính tọa độ

**Cho**: B = {v₁ = (0,1), v₂ = (1,1)} là cơ sở của R²

**Tìm**: [v]ᵦ với v = (2,3)

**Giải**: 
Ta cần tìm c₁, c₂ sao cho:
```
v = c₁v₁ + c₂v₂
(2,3) = c₁(0,1) + c₂(1,1)
(2,3) = (c₂, c₁ + c₂)
```

Hệ phương trình:
```
c₂ = 2
c₁ + c₂ = 3  ⟹  c₁ = 1
```

**Kết quả**: [v]ᵦ = (1,2)ᵀ

**Cách khác**: Giải hệ ma trận
```
[v₁ v₂ | v] = [0 1 | 2]  ⟹  [v]ᵦ = [1]
              [1 1 | 3]                [2]
```

### 6.3. Ma trận chuyển cơ sở

**Định nghĩa**: Ma trận chuyển từ cơ sở S sang cơ sở S':
```
P_{S→S'} = [[v₁]ₛ | [v₂]ₛ | ... | [vₙ]ₛ]
```
trong đó S' = {v₁, v₂, ..., vₙ}

**Công thức chuyển đổi**:
```
[v]ₛ = P_{S→S'} × [v]ₛ'
```

### 6.4. Ví dụ chi tiết chuyển cơ sở

**Cho**:
```
S = {u₁ = (-1,4,-3), u₂ = (-1,3,-2), u₃ = (1,-1,1)}
S' = {v₁ = (2,1,-3), v₂ = (-1,2,1), v₃ = (-2,3,1)}
α = (-22,-17,9)
```

#### 6.4.1. Kiểm tra S là cơ sở của R³

**Ma trận A**:
```
A = [-1  4 -3]
    [-1  3 -2]
    [ 1 -1  1]
```

**Tính det(A)**:
```
det(A) = -1×(3×1 - (-2)×(-1)) - (-1)×(4×1 - (-3)×(-1)) + 1×(4×(-2) - (-3)×3)
       = -1×(3-2) + 1×(4-3) + 1×(-8+9)
       = -1 + 1 + 1 = 1 ≠ 0
```

**Kết luận**: S là cơ sở của R³.

#### 6.4.2. Tìm tọa độ của α theo các cơ sở

**Tọa độ theo S**:
Giải hệ: [-1  4 -3 | -22]
        [-1  3 -2 | -17]
        [ 1 -1  1 |   9]

**Kết quả**: [α]ₛ = [4, -3, 2]ᵀ

**Tọa độ theo S'**:
Tương tự, ta được: [α]ₛ' = [13, 0, 6]ᵀ

#### 6.4.3. Tìm ma trận chuyển cơ sở

**Cần tìm**: P_{S→S'} sao cho [α]ₛ = P_{S→S'} × [α]ₛ'

**Phương pháp**:
```
P_{S→S'} = [[v₁]ₛ | [v₂]ₛ | [v₃]ₛ]
```

**Tính [v₁]ₛ**: Giải hệ A[v₁]ₛ = v₁
```
[-1  4 -3 | 2 ]
[-1  3 -2 | 1 ]  ⟹  [v₁]ₛ = [c₁]
[ 1 -1  1 | -3]            [c₂]
                           [c₃]
```

Tương tự cho [v₂]ₛ và [v₃]ₛ.

### 6.5. Các tính chất quan trọng

#### 6.5.1. Tính chất cơ bản

1. **P_{B₀→B} = [u₁ | u₂ | ... | uₙ]** với B₀ là cơ sở chính tắc
2. **P_{B→B'} = (P_{B'→B})⁻¹**
3. **P_{B→A} = P_{B→C} × P_{C→A}** (tính bắc cầu)

#### 6.5.2. Công thức tổng quát

**Với hai cơ sở bất kỳ**:
```
P_{B→A} = B⁻¹ × A
```
trong đó:
- A là ma trận có cột là các vector của cơ sở A  
- B là ma trận có cột là các vector của cơ sở B

### 6.6. Ví dụ áp dụng công thức tổng quát

**Cho**:
```
A = [3  4 -6]    B = [1 -1  1]
    [0  1 -1]        [-1 2  1]
    [-2 -3 4]        [-2 3  1]
```

**Tính**:
```
P_{B→A} = B⁻¹A = [3  4 -6]⁻¹ [1 -1  1]
                 [0  1 -1]    [-1 2  1]
                 [-2 -3 4]    [-2 3  1]
```

---

## 7. Chéo hóa ma trận

### 7.1. Khái niệm cơ bản

#### 7.1.1. Trị riêng (Eigenvalue)

**Định nghĩa**: Số thực λ được gọi là trị riêng của ma trận vuông A nếu:
```
det(A - λI) = 0
```

Phương trình này gọi là **phương trình đặc trưng**.

#### 7.1.2. Vector riêng (Eigenvector)  

**Định nghĩa**: Vector x ≠ 0 được gọi là vector riêng ứng với trị riêng λ nếu:
```
(A - λI)x = 0
```

### 7.2. Ví dụ cơ bản

**Cho**:
```
A = [2  3]
    [0 -1]
```

#### 7.2.1. Tìm trị riêng

**Phương trình đặc trưng**:
```
det(A - λI) = det([2-λ   3  ]) = (2-λ)(-1-λ) = 0
                 ([0   -1-λ])
```

**Nghiệm**: λ₁ = 2, λ₂ = -1

#### 7.2.2. Tìm vector riêng

**Với λ₁ = 2**:
```
(A - 2I)x = 0
[0  3] [x₁] = [0]  ⟹  3x₂ = 0  ⟹  x₂ = 0
[0 -3] [x₂]   [0]      -3x₂ = 0

Đặt x₁ = a  ⟹  x = a[1]
                     [0]
```

**Vector riêng**: v₁ = (1,0)ᵀ

**Với λ₂ = -1**:
```
(A + I)x = 0  
[3  3] [x₁] = [0]  ⟹  x₁ + x₂ = 0  ⟹  x₁ = -x₂
[0  0] [x₂]   [0]

Đặt x₂ = a  ⟹  x = a[-1]
                     [ 1]
```

**Vector riêng**: v₂ = (-1,1)ᵀ

### 7.3. Định lý chéo hóa

**Định lý**: Ma trận A chéo hóa được khi và chỉ khi A có đúng n vector riêng độc lập tuyến tính.

**Dạng chéo hóa**:
```
A = PDP⁻¹
```
trong đó:
- D là ma trận chéo chứa các trị riêng
- P là ma trận có cột là các vector riêng tương ứng

**Ví dụ**:
```
A = [2  3] = [1 -1] [2  0] [1 -1]⁻¹
    [0 -1]   [0  1] [0 -1] [0  1]
           = P      D      P⁻¹
```

### 7.4. Ứng dụng: Tính lũy thừa ma trận

**Công thức**:
```
A² = (PDP⁻¹)(PDP⁻¹) = PD²P⁻¹
Aⁿ = PDⁿP⁻¹
```

**Ưu điểm**: Dễ tính Dⁿ vì D là ma trận chéo:
```
Dⁿ = [λ₁ⁿ  0   ...  0 ]
     [0   λ₂ⁿ  ...  0 ]
     [⋮    ⋮   ⋱   ⋮ ]
     [0    0   ... λₙⁿ]
```

### 7.5. Ví dụ phức tạp

**Cho**:
```
A = [2 1 1]
    [1 2 1]  
    [1 1 2]
```

#### 7.5.1. Tìm trị riêng

**Phương trình đặc trưng**:
```
det(A - λI) = det([2-λ  1    1  ])
                 ([1   2-λ   1  ])
                 ([1    1   2-λ ])
```

**Khai triển theo dòng 1**:
```
= (2-λ)[(2-λ)² - 1] - 1[(2-λ) - 1] + 1[1 - (2-λ)]
= (2-λ)[(2-λ)² - 1] - (2-λ-1) + (1-2+λ)
= (2-λ)[(2-λ)² - 1] - (2-λ-1) + (λ-1)
```

**Rút gọn**:
```
= (2-λ)³ - (2-λ) - (2-λ) + (λ-1) + (λ-1)
= (2-λ)³ - 2(2-λ) + 2(λ-1)
= (2-λ)³ - 2(2-λ) - 2(2-λ)
= (2-λ)[(2-λ)² - 4] 
= (2-λ)(2-λ-2)(2-λ+2)
= (2-λ)(-λ)(4-λ)
= -λ(2-λ)(4-λ)
```

**Nghiệm**: λ₁ = 0, λ₂ = 2, λ₃ = 4

**Chú ý**: Theo tính toán trong tài liệu gốc, ta có λ = 4 và λ = 1 (bội 2).

#### 7.5.2. Tìm vector riêng với λ = 4

```
(A - 4I)x = 0
[-2  1  1] [x₁]   [0]
[ 1 -2  1] [x₂] = [0] : d₁ ↔ d₂
[ 1  1 -2] [x₃]   [0]

→ [ 1 -2  1] [x₁]   [0]
  [-2  1  1] [x₂] = [0] : d₂ + 2d₁, d₃ - d₁
  [ 1  1 -2] [x₃]   [0]

→ [1 -2  1] [x₁]   [0]
  [0 -3  3] [x₂] = [0] : d₂ ÷ (-3)
  [0  3 -3] [x₃]   [0]

→ [1 -2  1] [x₁]   [0]
  [0  1 -1] [x₂] = [0] : d₃ - 3d₂, d₁ + 2d₂
  [0  3 -3] [x₃]   [0]

→ [1  0 -1] [x₁]   [0]
  [0  1 -1] [x₂] = [0]
  [0  0  0] [x₃]   [0]
```

Đặt x₃ = a:
```
x₁ = a, x₂ = a, x₃ = a  ⟹  x = a[1]
                               [1]
                               [1]
```

**Vector riêng**: v₁ = (1,1,1)ᵀ

#### 7.5.3. Tìm vector riêng với λ = 1

```
(A - I)x = 0  
[1 1 1] [x₁]   [0]
[1 1 1] [x₂] = [0] : d₂ - d₁, d₃ - d₁
[1 1 1] [x₃]   [0]

→ [1 1 1] [x₁]   [0]
  [0 0 0] [x₂] = [0]
  [0 0 0] [x₃]   [0]
```

Đặt x₂ = a, x₃ = b:
```
x₁ + a + b = 0  ⟹  x₁ = -a - b

x = a[-1] + b[-1]
     [ 1]    [ 0]
     [ 0]    [ 1]
```

**Vector riêng**: v₂ = (-1,1,0)ᵀ, v₃ = (-1,0,1)ᵀ

#### 7.5.4. Ma trận chéo hóa

```
P = [1 -1 -1]    D = [4 0 0]
    [1  1  0]        [0 1 0]
    [1  0  1]        [0 0 1]

A = PDP⁻¹
```

### 7.6. Chéo hóa trực giao

#### 7.6.1. Định lý

**Định lý**: Mọi ma trận đối xứng đều chéo hóa được (trực giao).

**Dạng chéo hóa trực giao**:
```
A = PDP^T
```
trong đó P là ma trận **trực chuẩn** (P^T P = I).

#### 7.6.2. Quy trình Gram-Schmidt

**Mục đích**: Từ các vector riêng, tạo ra hệ vector trực chuẩn.

**Các bước**:
1. **Trực giao hóa**: Dùng công thức Gram-Schmidt
2. **Chuẩn hóa**: Chia cho độ dài vector

**Ví dụ**:
Với các vector riêng:
```
v₁ = (1,1,1)ᵀ
v₂ = (-1,1,0)ᵀ
v₃ = (-1,0,1)ᵀ
```

**Chuẩn hóa**:
```
||v₁|| = √(1² + 1² + 1²) = √3  ⟹  p₁ = (1/√3, 1/√3, 1/√3)ᵀ

||v₂|| = √(1 + 1 + 0) = √2     ⟹  p₂ = (-1/√2, 1/√2, 0)ᵀ

||v₃|| = √(1 + 0 + 1) = √2     ⟹  p₃ = (-1/√2, 0, 1/√2)ᵀ
```

**Chú ý**: Cần kiểm tra tính trực giao giữa các vector trước khi chuẩn hóa.

### 7.7. Bài tập

#### 7.7.1. Bài 1

Chéo hóa ma trận:
```
A = [1  1]
    [0 -1]
```

#### 7.7.2. Bài 2  

Chéo hóa ma trận:
```
A = [3 -1  1]
    [2  0  1]
    [1 -1  2]
```

---

## Phụ lục: Công thức tổng hợp

### Ma trận cơ bản
```
• Ma trận nghịch đảo 2×2: A⁻¹ = (1/det(A)) × [d -b; -c a]
• Định thức 2×2: det([a b; c d]) = ad - bc
• Định thức 3×3: Khai triển theo hàng/cột hoặc biến đổi sơ cấp
```

### Hệ phương trình
```
• Quy tắc Cramer: xᵢ = det(Aᵢ)/det(A)
• Điều kiện có nghiệm duy nhất: det(A) ≠ 0
• Biện luận: So sánh rank(A) và rank([A|b])
```

### Không gian vector
```
• Độc lập tuyến tính: rank[v₁,...,vₘ] = m
• Cơ sở: Độc lập tuyến tính + Sinh ra không gian
• Số chiều: Số vector trong cơ sở
```

### Chuyển cơ sở
```
• Chuyển đổi tọa độ: [v]ₛ = P_{S→S'} × [v]ₛ'
• Ma trận chuyển cơ sở: P_{B→A} = B⁻¹A
• Tính chất: P_{B→B'} = (P_{B'→B})⁻¹
```

### Chéo hóa
```
• Trị riêng: det(A - λI) = 0
• Vector riêng: (A - λI)x = 0
• Chéo hóa: A = PDP⁻¹
• Lũy thừa: Aⁿ = PDⁿP⁻¹
• Ma trận đối xứng: A = PDPᵀ (P trực chuẩn)
```