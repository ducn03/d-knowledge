# Giải đề C/C++ — Đáp án & mã nguồn

> Tóm tắt: Tài liệu này chứa lời giải cho các bài chương trình C/C++ trong ảnh: in ra kết quả cho các chương trình (Câu 1..10, 3..9, 6..8, 10) và hàm thực hiện (Câu 11, 12, 13). Mỗi câu có phân tích ngắn và kết quả.

---

## Câu 1

**Chương trình** (tóm tắt):

```cpp
void f(int b, int& a) { 
    b += 5; 
    a += b; 
    ++b; 
}

int main() { 
    int x = 6, y = 9; 
    f(x + 1, y); 
    cout << x << "_" << y << endl; 
}
```

**Phân tích:** `b` nhận giá trị `x+1` = 7 (tham trị), `a` là tham chiếu tới `y`. Trong hàm: `b` -> 12, `a += b` => y = 9+12 = 21.

**Kết quả:** `6_21`

---

## Câu 2

**Chương trình:**

```cpp
int a[] = {3, 2, 6, 1, 5, 4, 8};
for (int i = 2; i <= 6; i++) {
    if (i == 5) break;
    cout << *a + i << " ";
}
```

**Phân tích:** `*a` là `a[0] = 3`. Vòng in với i = 2,3,4 rồi gặp i==5 -> break.

**Kết quả:** `5 6 7 `

---

## Câu 3

**Chương trình:**

```cpp
int x = 5, y, *p = &x;
(*p)++;
y = *p + 3;
cout << x << "_" << y;
```

**Phân tích:** `(*p)++` tăng `x` từ 5 -> 6. `y = 6 + 3 = 9`.

**Kết quả:** `6_9`

---

## Câu 4

**Chương trình:**

```cpp
int func(int a[], int& n) {
    int t = 1;
    for (int i = n - 1; i > 1; i--) {
        t += a[i];
    }
    n = t / 2;
    return t;
}

int main() { 
    int a[] = {2, 3, 6, 8, 4, 6}; 
    int n = 5;
    cout << func(a, n) << "_" << n;
}
```

**Phân tích:** Với n=5, vòng i = 4,3,2: t = 1+4+8+6 = 19. n = 19/2 = 9 (nguyên).

**Kết quả:** `19_9`

---

## Câu 5

**Chương trình:**

```cpp
int a[][8] = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {2, 4, 6, 8},
    {1, 3, 5, 7}
};
int s = 2;
for (int i = 0; i < 2; i++)
    for (int j = 1; j < 3; j++)
        s += a[i][j];
cout << s;
```

**Phân tích:** Tổng các phần tử a[0][1], a[0][2], a[1][1], a[1][2] = 2+3+6+7 = 18. s = 2+18 = 20.

**Kết quả:** `20`

---

## Câu 6

**Chương trình:**

```cpp
float *p = new float(6.9f);
float x = 3.6f;
p = &x;
*p += x;
cout << x << "_" << *p;
```

**Phân tích:** Sau `p = &x`, `*p += x` làm x = x + x = 7.2.

**Kết quả:** `7.2_7.2`

---

## Câu 7

**Chương trình:**

```cpp
int x = 14, y = 2;
float z = (x + 1) / y;
if (z == 8.5) 
    cout << x * y << endl;
else 
    cout << x / y << endl;
```

**Phân tích:** `(x+1)/y` với cả hai là `int` nên chia nguyên: 15/2 = 7 -> gán vào `z` = 7. So sánh false -> in `x/y` = 14/2 = 7.

**Kết quả:** `7`

---

## Câu 8

**Chương trình:**

```cpp
int a[] = {3, 7, 1, 6, 5, 3, 7};
int t = 1, i = 4;
for (; i >= 2; i--)
    t += a[i];
cout << t;
```

**Phân tích:** i = 4,3,2: t = 1+5+6+1 = 13.

**Kết quả:** `13`

---

## Câu 9

**Chương trình:**

```cpp
int i = 1;
for (; i = 9; i++) {
    cout << i << "\n";
    if (i >= 6) break;
}
```

**Phân tích:** Điều kiện `i = 9` gán 9 cho `i` (không phải so sánh). Khi vào thân, `i` = 9, in 9 rồi `if(i>=6)` đúng -> `break`.

**Kết quả:** `9` (dòng mới)

---

## Câu 10

**Chương trình:**

```cpp
int a[] = {7, 1, 6, 3, 8, 6};
int* p = &a[4];
cout << *p - 4;
```

**Phân tích:** `*p = a[4] = 8` -> `8 - 4 = 4`.

**Kết quả:** `4`

---

## Câu 11 — Viết hàm kiểm tra mảng số đối xứng

**Yêu cầu:** Kiểm tra mảng một chiều chứa các số thực `double` có đối xứng (palindrome) hay không.

**Hàm mẫu (C++):**

```cpp
// file: palindrome.cpp
#include <vector>

/**
 * Kiểm tra mảng có đối xứng hay không.
 * @param a vector<double> đầu vào
 * @return true nếu đối xứng, false nếu không
 */
bool isPalindrome(const std::vector<double>& a) {
    size_t i = 0, j = a.size() ? a.size() - 1 : 0;
    if (a.empty()) return true;
    while (i < j) {
        if (a[i] != a[j]) return false;
        ++i; 
        --j;
    }
    return true;
}

// Ví dụ dùng
//#include <iostream>
//int main(){ std::nothrow; }
```

---

## Câu 12 — Đếm ký tự chữ và số trong chuỗi

**Yêu cầu:** Viết hàm kiểm tra chuỗi có bao nhiêu ký tự số và bao nhiêu ký tự chữ. Mô tả input/output.

**Hàm mẫu (C++):**

```cpp
// file: count_chars.cpp
#include <iostream>
#include <cstring>

/**
 * Đếm chữ và chữ số trong chuỗi.
 * @param s chuỗi đầu vào
 * @param letters tham chiếu để trả về số ký tự chữ
 * @param digits tham chiếu để trả về số ký tự số
 */
void countLettersDigits(const char* s, int& letters, int& digits) {
    letters = 0;
    digits = 0;
    int len = strlen(s);
    for (int i = 0; i < len; i++) {
        char ch = s[i];
        if ((ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z')) {
            ++letters;
        }
        else if (ch >= '0' && ch <= '9') {
            ++digits;
        }
    }
}

// Ví dụ dùng:
// int letters, digits;
// countLettersDigits("Abc123! 4", letters, digits); // letters = 3, digits = 4
```

**Mô tả I/O:**

* Input: một chuỗi `string` (có thể chứa khoảng trắng, ký tự đặc biệt).
* Output: hai số nguyên: `soChu` (số ký tự chữ) và `soSo` (số ký tự số).

---

## Câu 13 — Cấu trúc sách và tìm số trang của quyển có đơn giá lớn nhất

**Struct:**

```cpp
struct Sach {
    char tenS[200];
    int soT;      // số trang
    float donGia; // đơn giá
};
```

**Yêu cầu:** Tìm `soT` của quyển sách **đầu tiên** có `donGia` lớn nhất trong mảng.

**Hàm mẫu (C++):**

```cpp
// file: sach_max_dongia.cpp
#include <iostream>

int soTrangCuaQuyenMaxDonGia(Sach arr[], int n) {
    if (n <= 0) return -1; // báo lỗi / không có sách
    float maxDG = arr[0].donGia;
    int idx = 0;
    for (int i = 1; i < n; ++i) {
        if (arr[i].donGia > maxDG) {
            maxDG = arr[i].donGia;
            idx = i;
        }
    }
    return arr[idx].soT;
}
```

---