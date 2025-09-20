# Giải Đề Thi OT_04 - Lập Trình C++

## Câu 1: Các phương pháp biểu diễn thuật toán (0.5 điểm)

Có 3 phương pháp chính để biểu diễn thuật toán:

1. **Ngôn ngữ tự nhiên**: Mô tả thuật toán bằng lời văn, dễ hiểu nhưng có thể gây nhập nhằng.

2. **Lưu đồ (Flowchart)**: Sử dụng các ký hiệu hình học để biểu diễn các bước thực hiện thuật toán một cách trực quan.

3. **Mã giả (Pseudocode)**: Kết hợp giữa ngôn ngữ tự nhiên và cú pháp lập trình, rõ ràng và dễ chuyển đổi thành code.

## Câu 2: Ngôn ngữ lập trình là gì? (0.5 điểm)

**Ngôn ngữ lập trình** là một hệ thống ký hiệu được sử dụng để viết các chương trình máy tính. Nó bao gồm:

- **Cú pháp (Syntax)**: Các quy tắc về cách viết code
- **Ngữ nghĩa (Semantics)**: Ý nghĩa của các lệnh
- **Từ vựng**: Tập hợp các từ khóa, toán tử, và ký hiệu

Ngôn ngữ lập trình giúp lập trình viên giao tiếp với máy tính để tạo ra các ứng dụng phần mềm.

## Câu 3: Lợi ích của việc sử dụng hàm (0.5 điểm)

Việc sử dụng hàm mang lại nhiều lợi ích:

1. **Tái sử dụng code**: Viết một lần, sử dụng nhiều lần
2. **Dễ bảo trì**: Chỉ cần sửa ở một chỗ khi có lỗi
3. **Cấu trúc rõ ràng**: Chia nhỏ chương trình thành các phần độc lập
4. **Giảm lỗi**: Tránh việc viết lại code nhiều lần
5. **Dễ debug**: Kiểm tra từng phần riêng biệt
6. **Làm việc nhóm**: Nhiều người có thể làm việc trên các hàm khác nhau

## Câu 4: Khái niệm về Biến trong C/C++ (0.5 điểm)

**Biến** trong C/C++ là:

- Một vùng nhớ được đặt tên để lưu trữ dữ liệu
- Có **kiểu dữ liệu** xác định (int, float, char, ...)
- Có **tên biến** tuân theo quy tắc đặt tên
- Có **giá trị** có thể thay đổi trong quá trình thực thi

**Cú pháp khai báo**: `kiểu_dữ_liệu tên_biến = giá_trị_khởi_tạo;`

**Ví dụ**: `int x = 10;`, `float pi = 3.14;`

## Câu 5: Lưu đồ tính tổng các số nguyên dương chẵn từ 1 đến n (0.5 điểm)

```
[Bắt đầu]
    ↓
[Nhập n]
    ↓
[Khởi tạo: sum = 0, i = 2]
    ↓
[i <= n?] ──No──→ [Xuất sum]
    ↓Yes                ↓
[sum = sum + i]      [Kết thúc]
    ↓
[i = i + 2]
    ↓
[Quay lại kiểm tra i <= n]
```

## Câu 6: Chương trình C++ tính tổng số chẵn từ 1 đến n (0.5 điểm)

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, sum = 0;
    
    cout << "Nhap n: ";
    cin >> n;
    
    for (int i = 2; i <= n; i += 2) {
        sum += i;
    }
    
    cout << "Tong cac so chan tu 1 den " << n << " la: " << sum << endl;
    
    return 0;
}
```

## Câu 7: Kết quả chương trình (1.0 điểm)

**Phân tích từng bước:**

```cpp
int n=300, S=1;
for(int i=n; i>0; i=i/10)
    S *= i;
```

- **Lần 1**: i = 300, S = 1 × 300 = 300, i = 300/10 = 30
- **Lần 2**: i = 30, S = 300 × 30 = 9000, i = 30/10 = 3  
- **Lần 3**: i = 3, S = 9000 × 3 = 27000, i = 3/10 = 0
- **Kết thúc** vì i = 0

**Kết quả: 27000**

## Câu 8: Kết quả chương trình (1.0 điểm)

**Phân tích:**

```cpp
int x = 20, y = 2;
float z = (x + 1) / y;  // z = 21 / 2 = 10 (phép chia nguyên)
```

- Vì x và y là int, phép chia (x+1)/y = 21/2 = 10 (không phải 10.5)
- z = 10.0 (được chuyển sang float)
- Điều kiện `z == 8.5` là **false**
- Thực hiện `cout << x / y;` → 20/2 = 10

**Kết quả: 10**

## Câu 9: Kết quả chương trình (1.0 điểm)

**Phân tích từng bước:**

```cpp
int a=5;
int &b=a;  // b là tham chiếu đến a
```

1. `cout<<Kiemtra(a)<<",";`
   - Kiemtra(5) → 5-7 = -2
   - In ra: `-2,`

2. `b=20;` → a = 20 (vì b tham chiếu đến a)

3. `a=b-a-1;` → a = 20-20-1 = -1

4. `b++;` → a++ → a = 0 (vì b tham chiếu đến a)

5. `cout<<a<<","<<b;` → In ra: `0,0`

**Kết quả: -2,0,0**

## Câu 10: Kết quả chương trình (1.0 điểm)

**Phân tích:**

```cpp
int a[] = {7, 3, 10, 8, 4, 12};
int n = 5;
```

Trong hàm `func(a,n)`:
- Vòng lặp: `for(int i = n-1; i > 1; i--)`
- i chạy từ 4 xuống 2: i = 4, 3, 2
- `t += a[i]`: t = 0 + a[4] + a[3] + a[2] = 0 + 4 + 8 + 10 = 22

**Kết quả:**
```
22
5
```

## Câu 11: Kết quả chương trình (1.0 điểm)

**Phân tích:**

```cpp
int a[][8] = {
    {1, 5, 3, 4},
    {1, 6, 4, 8},  // i=1
    {2, 4, 6, 8},  // i=2
    {1, 3, 5, 7}
};
int s = 2;
```

Vòng lặp lồng: `i` từ 1 đến 2, `j` từ 0 đến 2:
- i=1, j=0: s += a[1][0] = 2 + 1 = 3
- i=1, j=1: s += a[1][1] = 3 + 6 = 9  
- i=1, j=2: s += a[1][2] = 9 + 4 = 13
- i=2, j=0: s += a[2][0] = 13 + 2 = 15
- i=2, j=1: s += a[2][1] = 15 + 4 = 19
- i=2, j=2: s += a[2][2] = 19 + 6 = 25

**Kết quả: 25**

## Câu 12: Kết quả chương trình (1.0 điểm)

**Phân tích:**

```cpp
int x = 5, y, *p = &x;  // p trỏ đến địa chỉ của x
(*p)++;                  // Tăng giá trị tại địa chỉ p trỏ đến: x = 6
y = x * 3;              // y = 6 * 3 = 18
```

**Kết quả:**
```
6
18
```

---

## Tóm tắt điểm số

| Câu | Điểm | Nội dung |
|-----|------|----------|
| 1-4 | 2.0  | Lý thuyết cơ bản |
| 5-6 | 1.0  | Thuật toán và lập trình |
| 7-12| 7.0  | Đọc hiểu và phân tích code |
| **Tổng** | **10.0** | **Toàn bộ đề thi** |