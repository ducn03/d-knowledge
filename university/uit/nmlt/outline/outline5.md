# Giải Đề Thi OT_04 - Lập Trình C++

#### **Câu 1: Các phương pháp biểu diễn thuật toán (0.5 điểm)**

Có 3 phương pháp chính để biểu diễn một thuật toán:

1.  **Dùng ngôn ngữ tự nhiên**:
    *   **Mô tả**: Sử dụng ngôn ngữ thường ngày để liệt kê các bước của thuật toán. Phương pháp này không yêu cầu người đọc hay người viết phải nắm các quy tắc cụ thể.
    *   **Nhược điểm**: Thường dài dòng, không thể hiện rõ cấu trúc của thuật toán và đôi lúc có thể gây khó hiểu hoặc hiểu lầm cho người đọc.

2.  **Dùng lưu đồ (Flowchart) - Sơ đồ khối**:
    *   **Mô tả**: Là một công cụ trực quan sử dụng các ký hiệu đồ họa để diễn đạt thuật toán.
    *   **Ưu điểm**: Giúp người đọc theo dõi được sự phân cấp các trường hợp và quá trình xử lý, đặc biệt hữu ích với các thuật toán có tính rắc rối, khó theo dõi.

3.  **Dùng mã giả (Pseudocode)**:
    *   **Mô tả**: Là một ngôn ngữ tựa ngôn ngữ lập trình, sử dụng các cấu trúc chuẩn hóa (tựa Pascal, C), ký hiệu toán học, biến và hàm để mô tả thuật toán.
    *   **Ưu điểm**: Đỡ cồng kềnh hơn so với lưu đồ khối.
    *   **Nhược điểm**: Không trực quan bằng lưu đồ khối.

---

#### **Câu 2: Ngôn ngữ lập trình là gì? (0.5 điểm)**

Dựa trên các tài liệu, **ngôn ngữ lập trình C++** được cấu thành từ một **bộ từ vựng** riêng, giúp lập trình viên viết ra các chỉ dẫn để máy tính có thể thực thi. Bộ từ vựng này bao gồm các thành phần chính sau:

*   **Ký tự**: Gồm bộ chữ cái Latin (A-Z, a-z), bộ chữ số thập phân (0-9), các ký hiệu toán học và các ký tự đặc biệt.
*   **Từ khóa (Keywords)**: Là những từ dành riêng cho ngôn ngữ C++, được viết bằng chữ thường và không thể dùng để đặt tên biến hay hàm (ví dụ: `const`, `int`, `float`, `if`, `for`).
*   **Tên/Định danh (Identifier)**: Là một dãy ký tự dùng để chỉ tên hằng, biến, hàm do người lập trình đặt. Tên phải tuân theo các quy tắc như: không trùng từ khóa, ký tự đầu tiên phải là chữ cái hoặc dấu gạch dưới `_`.
*   **Hằng**: Gồm hằng ký tự (ví dụ: `'A'`) và hằng chuỗi (ví dụ: `"Xin Chao"`).
*   **Dấu chấm phẩy (`;`)**: Dùng để phân cách và kết thúc các câu lệnh.
*   **Câu chú thích (Comments)**: Là các ghi chú trong mã nguồn (`//` hoặc `/* */`) mà trình biên dịch sẽ bỏ qua, giúp người đọc dễ hiểu code hơn.

---

#### **Câu 3: Lợi ích của việc sử dụng hàm (0.5 điểm)**

Sử dụng hàm trong lập trình mang lại nhiều lợi ích quan trọng, vì hàm là một đoạn chương trình có tên, có đầu vào, đầu ra và thực hiện một chức năng chuyên biệt. Các lợi ích chính bao gồm:

1.  **Tái sử dụng (Reusability)**: Một hàm có thể được viết một lần và được gọi để sử dụng nhiều lần từ nhiều nơi khác nhau trong chương trình với các đối số khác nhau, tránh việc lặp lại code.
2.  **Dễ sửa lỗi và cải tiến**: Khi cần thay đổi hoặc sửa lỗi một chức năng nào đó, ta chỉ cần chỉnh sửa trong thân hàm đó mà không ảnh hưởng đến các phần khác của chương trình.
3.  **Cấu trúc rõ ràng**: Việc chia chương trình lớn thành các hàm nhỏ giúp mã nguồn trở nên có cấu trúc, dễ đọc và dễ quản lý hơn.

---

#### **Câu 4: Khái niệm về Biến trong C/C++ (0.5 điểm)**

**Biến (Variable)** trong C/C++ được định nghĩa là một ô nhớ hoặc một vùng nhớ dùng để chứa dữ liệu trong quá trình thực hiện chương trình. Các đặc điểm chính của biến bao gồm:

*   **Lưu trữ dữ liệu**: Mỗi biến được cấp một vùng nhớ với địa chỉ duy nhất để lưu trữ giá trị.
*   **Có kiểu dữ liệu cụ thể**: Mỗi biến phải thuộc một kiểu dữ liệu xác định (ví dụ: `int`, `float`, `char`), và kích thước của biến phụ thuộc vào kiểu dữ liệu đó.
*   **Có tên định danh**: Tên biến phải tuân theo quy tắc đặt tên của C++ (không trùng từ khóa, bắt đầu bằng chữ cái hoặc `_`, không chứa khoảng trắng).
*   **Giá trị có thể thay đổi**: Giá trị được lưu trong biến có thể được thay đổi trong suốt quá trình chạy chương trình.

**Cú pháp khai báo**: `kiểu_dữ_liệu tên_biến;` hoặc `kiểu_dữ_liệu tên_biến = giá_trị;`.
**Ví dụ**: `int so_nguyen;` hoặc `float diem_trung_binh = 8.5;`.

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