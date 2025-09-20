# ĐỀ THI TRẮC NGHIỆM LẬP TRÌNH C++ - ĐỀ 3 (GIẢI CHI TIẾT)

## **CÂU 1:** Kết quả của đoạn mã sau là gì?
```cpp
int a = 5, b = 2;
float c = a / b;
cout << c;
```
**a) 2**  
**b) 2.5**  
**c) 2.0**  
**d) Lỗi kiểu dữ liệu**

### ✅ **ĐÁP ÁN: A) 2**

**📝 Giải thích chi tiết:**
- `a = 5` và `b = 2` đều là kiểu `int`
- Phép toán `a / b` = `5 / 2` thực hiện **phép chia nguyên** → kết quả = 2
- Giá trị 2 được gán vào biến `float c` → c = 2.0
- Khi `cout << c`, mặc định in ra "2" (không hiện phần thập phân .0)

**🔧 Để có kết quả 2.5:**
```cpp
float c = (float)a / b;  // Ép kiểu
// hoặc
float c = a / (float)b;
// hoặc
float c = 5.0 / 2;
```

---

## **CÂU 2:** Toán tử nào có độ ưu tiên cao nhất trong C++?
**a) =**  
**b) ++**  
**c) &&**  
**d) !=**

### ✅ **ĐÁP ÁN: B) ++**

**📊 Bảng độ ưu tiên toán tử (cao → thấp):**

| Độ ưu tiên | Toán tử | Mô tả |
|------------|---------|-------|
| 1 | `++`, `--` | Tăng/giảm tiền tố & hậu tố |
| 2 | `!=`, `==`, `<`, `>` | So sánh |
| 3 | `&&` | Logic AND |
| 4 | `=`, `+=`, `-=` | Gán |

**💡 Ghi nhớ:** Toán tử một ngôi (++, --, !) luôn có độ ưu tiên cao hơn toán tử hai ngôi.

---

## **CÂU 3:** Kết quả đoạn mã sau là gì?
```cpp
int a = 3;
cout << ++a * 2;
```
**a) 6**  
**b) 8**  
**c) 7**  
**d) 4**

### ✅ **ĐÁP ÁN: B) 8**

**📝 Phân tích từng bước:**
1. `a = 3` ban đầu
2. `++a` (tăng trước): a = 3 + 1 = 4
3. `++a * 2` = `4 * 2` = 8

**🔀 So sánh với tăng sau:**
```cpp
cout << a++ * 2;  // Kết quả: 6 (dùng a=3 trước, sau đó a=4)
cout << ++a * 2;  // Kết quả: 8 (tăng a=4 trước, rồi tính)
```

---

## **CÂU 4:** Hàm sizeof(int) trả về gì (trên hệ thống 32-bit)?
**a) 2**  
**b) 4**  
**c) 8**  
**d) 1**

### ✅ **ĐÁP ÁN: B) 4**

**📏 Bảng kích thước kiểu dữ liệu:**

| Kiểu | 16-bit | 32-bit | 64-bit |
|------|--------|--------|--------|
| `char` | 1 byte | 1 byte | 1 byte |
| `short` | 2 bytes | 2 bytes | 2 bytes |
| `int` | 2 bytes | **4 bytes** | 4 bytes |
| `long` | 4 bytes | 4 bytes | 8 bytes |
| `long long` | 8 bytes | 8 bytes | 8 bytes |

**💻 Code kiểm tra:**
```cpp
cout << "sizeof(int) = " << sizeof(int) << " bytes" << endl;
```

---

## **CÂU 5:** Biến nào sau đây là con trỏ hợp lệ trong C++?
**a) int x = &a;**  
**b) int *p;**  
**c) int p*;**  
**d) int &p = *a;**

### ✅ **ĐÁP ÁN: B) int *p;**

**📝 Phân tích từng lựa chọn:**

| Lựa chọn | Phân tích | Kết quả |
|----------|-----------|---------|
| a) `int x = &a;` | Gán địa chỉ cho biến `int` thường | ❌ Sai |
| **b) `int *p;`** | **Khai báo con trỏ đến `int`** | **✅ Đúng** |
| c) `int p*;` | Cú pháp sai (dấu * sai vị trí) | ❌ Sai |
| d) `int &p = *a;` | Tham chiếu đến giá trị không xác định | ❌ Sai |

**🔧 Cách khai báo con trỏ đúng:**
```cpp
int *p;           // Khai báo con trỏ
int *p = nullptr; // Khởi tạo con trỏ NULL
int x = 10;
int *p = &x;      // Con trỏ trỏ đến x
```

---

## **CÂU 6:** Câu lệnh delete[] p; dùng để làm gì?
**a) Giải phóng biến thông thường**  
**b) Cấp phát mảng**  
**c) Giải phóng mảng động**  
**d) Không hợp lệ**

### ✅ **ĐÁP ÁN: C) Giải phóng mảng động**

**🔗 Quy tắc cấp phát - giải phóng:**

| Cấp phát | Giải phóng | Mục đích |
|----------|------------|----------|
| `new int` | `delete p` | Biến đơn |
| `new int[n]` | `delete[] p` | Mảng động |

**💻 Ví dụ đầy đủ:**
```cpp
// Cấp phát mảng động
int *p = new int[5];

// Sử dụng mảng
for(int i = 0; i < 5; i++) {
    p[i] = i * 2;
}

// Giải phóng mảng động
delete[] p;
p = nullptr;  // Tránh dangling pointer
```

---

## **CÂU 7:** Chọn phát biểu sai về con trỏ:
**a) Con trỏ lưu địa chỉ của biến khác**  
**b) Con trỏ phải được cấp phát bằng new**  
**c) Có thể truyền con trỏ vào hàm**  
**d) Con trỏ có thể trỏ tới struct**

### ✅ **ĐÁP ÁN: B) Con trỏ phải được cấp phát bằng new**

**📝 Phân tích từng phát biểu:**

✅ **a) Đúng** - Con trỏ lưu địa chỉ:
```cpp
int x = 10;
int *p = &x;  // p lưu địa chỉ của x
```

❌ **b) SAI** - Con trỏ không bắt buộc dùng `new`:
```cpp
int x = 5;
int *p = &x;     // Trỏ đến biến thường (không cần new)
int *q = new int; // Cấp phát động (dùng new)
```

✅ **c) Đúng** - Truyền con trỏ vào hàm:
```cpp
void func(int *p) {
    *p = 20;
}
```

✅ **d) Đúng** - Con trỏ trỏ tới struct:
```cpp
struct Point { int x, y; };
Point *p = new Point;
```

---

## **CÂU 8:** Cho đoạn mã:
```cpp
int x = 10;
int &y = x;
y++;
cout << x;
```
**Kết quả là:**
**a) 10**  
**b) 11**  
**c) 12**  
**d) Lỗi**

### ✅ **ĐÁP ÁN: B) 11**

**📝 Hiểu về Reference (Tham chiếu):**

**Trace thực thi:**
1. `x = 10` - Biến x có giá trị 10
2. `int &y = x` - y là **tham chiếu** (alias) của x
3. `y++` - Tăng y lên 1, tức là tăng x lên 1 → x = 11
4. `cout << x` - In ra 11

**🔀 So sánh Reference vs Pointer:**
```cpp
// Reference (Tham chiếu)
int x = 10;
int &y = x;    // y là alias của x
y = 20;        // x cũng thành 20

// Pointer (Con trỏ)  
int x = 10;
int *p = &x;   // p trỏ đến x
*p = 20;       // x thành 20
```

---

## **CÂU 9:** Dòng nào khai báo hàm có tham số mặc định hợp lệ?
**a) void test(int x = 5, int y);**  
**b) void test(int x, int y = 5);**  
**c) void test(int = x);**  
**d) void test(x = 5);**

### ✅ **ĐÁP ÁN: B) void test(int x, int y = 5);**

**📏 Quy tắc tham số mặc định:**

❌ **Sai:** Tham số mặc định ở giữa
```cpp
void func(int a = 1, int b);  // Lỗi!
```

✅ **Đúng:** Tham số mặc định ở cuối
```cpp
void func(int a, int b = 1);           // OK
void func(int a = 1, int b = 2);       // OK  
void func(int a, int b = 1, int c = 2); // OK
```

**💻 Ví dụ sử dụng:**
```cpp
void test(int x, int y = 5) {
    cout << x << " " << y << endl;
}

// Gọi hàm
test(3);     // x=3, y=5 (dùng giá trị mặc định)
test(3, 7);  // x=3, y=7 (ghi đè giá trị mặc định)
```

---

## **CÂU 10:** Giá trị của mảng sau là gì?
```cpp
int a[5] = {1, 2, 3};
```
**a) {1, 2, 3, 0, 0}**  
**b) {1, 2, 3, 3, 3}**  
**c) {1, 2, 3}**  
**d) Lỗi**

### ✅ **ĐÁP ÁN: A) {1, 2, 3, 0, 0}**

**📝 Quy tắc khởi tạo mảng:**

**Khởi tạo một phần:**
- Các phần tử được chỉ định: a[0]=1, a[1]=2, a[2]=3  
- Các phần tử còn lại tự động = 0: a[3]=0, a[4]=0

**💻 Các trường hợp khởi tạo mảng:**
```cpp
int a[5] = {1, 2, 3};        // {1, 2, 3, 0, 0}
int b[5] = {0};              // {0, 0, 0, 0, 0}
int c[5] = {};               // {0, 0, 0, 0, 0}
int d[5];                    // Giá trị không xác định (garbage)
int e[] = {1, 2, 3};         // Kích thước tự động = 3
```

---

## **CÂU 11:** Câu nào đúng về struct trong C++?
**a) Không thể chứa hàm**  
**b) Không thể tạo mảng struct**  
**c) Có thể chứa con trỏ**  
**d) Không thể truyền vào hàm**

### ✅ **ĐÁP ÁN: C) Có thể chứa con trỏ**

**📝 Phân tích từng lựa chọn:**

❌ **a) Sai** - Struct có thể chứa hàm (method):
```cpp
struct Point {
    int x, y;
    void print() {  // Hàm trong struct
        cout << x << " " << y;
    }
};
```

❌ **b) Sai** - Có thể tạo mảng struct:
```cpp
struct Student {
    int id;
    string name;
};
Student students[100];  // Mảng struct
```

✅ **c) Đúng** - Struct có thể chứa con trỏ:
```cpp
struct Node {
    int data;
    Node* next;     // Con trỏ trong struct
};
```

❌ **d) Sai** - Có thể truyền struct vào hàm:
```cpp
void printStudent(Student s) {
    cout << s.name;
}
```

---

## **CÂU 12:** Kết quả đoạn mã sau là gì?
```cpp
int a = 5;
int *p = &a;
*p += 2;
cout << a;
```
**a) 5**  
**b) 7**  
**c) 2**  
**d) Lỗi biên dịch**

### ✅ **ĐÁP ÁN: B) 7**

**📝 Trace thực thi:**
1. `a = 5` - Biến a có giá trị 5
2. `int *p = &a` - Con trỏ p trỏ đến địa chỉ của a
3. `*p += 2` - Tăng **giá trị tại địa chỉ p** lên 2
   - Tương đương: `a += 2` → a = 5 + 2 = 7
4. `cout << a` - In ra 7

**🔧 Minh họa bằng hình:**
```
Bộ nhớ:
┌─────────┬─────────┐
│ Địa chỉ │ Giá trị │
├─────────┼─────────┤
│  1000   │    7    │ ← a (ban đầu 5, sau đó +2)
└─────────┴─────────┘
     ↑
     p (trỏ đến địa chỉ 1000)
```

---

## **CÂU 13:** Hàm đệ quy cần có điều kiện gì để tránh chạy vô hạn?
**a) Có tham chiếu**  
**b) Có điều kiện dừng**  
**c) Gọi hàm khác**  
**d) Tăng biến đếm**

### ✅ **ĐÁP ÁN: B) Có điều kiện dừng**

**📝 Cấu trúc hàm đệ quy:**

**Thành phần bắt buộc:**
1. **Base case** (điều kiện dừng) - Trường hợp đơn giản nhất
2. **Recursive case** - Hàm gọi chính nó với tham số đơn giản hơn

**💻 Ví dụ hàm tính giai thừa:**
```cpp
int factorial(int n) {
    // Base case - Điều kiện dừng
    if (n <= 1) {
        return 1;
    }
    
    // Recursive case - Gọi đệ quy
    return n * factorial(n - 1);
}
```

**❌ Đệ quy vô hạn (thiếu điều kiện dừng):**
```cpp
int wrong_factorial(int n) {
    return n * wrong_factorial(n - 1);  // Không bao giờ dừng!
}
```

---

## **CÂU 14:** Cú pháp khai báo mảng 2 chiều đúng là?
**a) int a[3][3];**  
**b) int a[3,3];**  
**c) int [3][3] a;**  
**d) array a[3][3];**

### ✅ **ĐÁP ÁN: A) int a[3][3];**

**📝 Phân tích cú pháp:**

✅ **a) `int a[3][3];`** - Cú pháp đúng C++

❌ **b) `int a[3,3];`** - Cú pháp sai (dấu phẩy thay vì [][])

❌ **c) `int [3][3] a;`** - Thứ tự sai (kiểu dữ liệu phải trước tên biến)

❌ **d) `array a[3][3];`** - Không phải C++ (có thể là ngôn ngữ khác)

**💻 Các cách khai báo mảng 2 chiều:**
```cpp
int a[3][4];                    // 3 hàng, 4 cột
int b[3][4] = {0};             // Khởi tạo tất cả = 0
int c[2][3] = {{1,2,3}, {4,5,6}}; // Khởi tạo có giá trị
int d[][3] = {{1,2,3}, {4,5,6}};   // Tự động xác định số hàng
```

---

## **CÂU 15:** Lệnh nào in ra giá trị thứ 2 trong mảng int a[] = {10, 20, 30};?
**a) a[1]**  
**b) a[2]**  
**c) *a**  
**d) a[0]**

### ✅ **ĐÁP ÁN: A) a[1]**

**📝 Index mảng trong C++:**

**Mảng:** `int a[] = {10, 20, 30};`

| Thứ tự | Index | Giá trị | Cách truy cập |
|--------|-------|---------|---------------|
| 1 | 0 | 10 | `a[0]` |
| **2** | **1** | **20** | **`a[1]`** ← Đáp án |
| 3 | 2 | 30 | `a[2]` |

**🔍 Phân tích các lựa chọn:**
- **a) `a[1]`** ✅ - Phần tử thứ 2 (index 1) = 20
- **b) `a[2]`** ❌ - Phần tử thứ 3 (index 2) = 30  
- **c) `*a`** ❌ - Tương đương `a[0]` = 10
- **d) `a[0]`** ❌ - Phần tử thứ 1 (index 0) = 10

---

## **CÂU 16:** Con trỏ và mảng liên quan thế nào?
**a) Con trỏ không thể trỏ đến mảng**  
**b) Mảng có thể gán cho con trỏ**  
**c) Mảng và con trỏ là hoàn toàn giống nhau**  
**d) Con trỏ không thể dùng toán tử []**

### ✅ **ĐÁP ÁN: B) Mảng có thể gán cho con trỏ**

**📝 Quan hệ mảng - con trỏ:**

**Tên mảng = địa chỉ phần tử đầu tiên**
```cpp
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;  // p trỏ đến arr[0]

// Các cách truy cập tương đương:
cout << arr[2];  // 3
cout << *(arr + 2);  // 3  
cout << p[2];    // 3
cout << *(p + 2); // 3
```

**🔍 Phân tích các lựa chọn:**

❌ **a) Sai** - Con trỏ có thể trỏ đến mảng:
```cpp
int arr[10];
int *p = arr;  // OK
```

✅ **b) Đúng** - Tên mảng có thể gán cho con trỏ:
```cpp
int *p = arr;  // arr tự động chuyển thành địa chỉ
```

❌ **c) Sai** - Có khác biệt:
- Mảng: kích thước cố định, không thể thay đổi địa chỉ
- Con trỏ: có thể trỏ đến địa chỉ khác

❌ **d) Sai** - Con trỏ có thể dùng []:
```cpp
int *p = arr;
cout << p[0];  // OK
```

---

## **CÂU 17:** Lệnh nào dưới đây sai?
**a) int *p = NULL;**  
**b) delete p;**  
**c) int p = new int;**  
**d) p = new int;**

### ✅ **ĐÁP ÁN: C) int p = new int;**

**📝 Phân tích từng lệnh:**

✅ **a) `int *p = NULL;`** - Đúng:
```cpp
int *p = NULL;     // Cách cũ
int *p = nullptr;  // Cách mới (C++11)
```

✅ **b) `delete p;`** - Đúng (nếu p đã được cấp phát):
```cpp
int *p = new int(10);
delete p;  // Giải phóng bộ nhớ
```

❌ **c) `int p = new int;`** - SAI:
- `new int` trả về **con trỏ** (địa chỉ)  
- `int p` là **biến thường**, không thể lưu địa chỉ
- **Đúng phải là:** `int *p = new int;`

✅ **d) `p = new int;`** - Đúng (nếu p đã được khai báo):
```cpp
int *p;        // Khai báo trước
p = new int;   // Cấp phát sau
```

---

## **CÂU 18:** Kết quả của func(3) trong hàm sau là gì?
```cpp
int func(int n) {
    if (n == 0) return 0;
    return n + func(n - 1);
}
```
**a) 6**  
**b) 3**  
**c) 0**  
**d) Lỗi**

### ✅ **ĐÁP ÁN: A) 6**

**📝 Trace hàm đệ quy func(3):**

**Hàm tính tổng từ 1 đến n:**
```
func(3) = 3 + func(2)
        = 3 + (2 + func(1))
        = 3 + (2 + (1 + func(0)))
        = 3 + (2 + (1 + 0))
        = 3 + 2 + 1 + 0 = 6
```

**🔄 Chi tiết từng bước:**
1. `func(3)` → `3 + func(2)`
2. `func(2)` → `2 + func(1)`  
3. `func(1)` → `1 + func(0)`
4. `func(0)` → `0` (base case)
5. Tính ngược: 0 → 1+0=1 → 2+1=3 → 3+3=6

**📊 Công thức tổng quát:** `func(n) = 0 + 1 + 2 + ... + n = n*(n+1)/2`
- `func(3) = 3*4/2 = 6` ✅

---

## **CÂU 19:** Giá trị của *(a + 2) nếu int a[5] = {1, 2, 3, 4, 5}; là gì?
**a) 2**  
**b) 3**  
**c) 4**  
**d) 5**

### ✅ **ĐÁP ÁN: B) 3**

**📝 Phép toán con trỏ với mảng:**

**Mảng:** `int a[5] = {1, 2, 3, 4, 5};`

| Index | 0 | 1 | 2 | 3 | 4 |
|-------|---|---|---|---|---|
| Giá trị | 1 | 2 | **3** | 4 | 5 |
| Địa chỉ | a+0 | a+1 | **a+2** | a+3 | a+4 |

**🔍 Phân tích `*(a + 2)`:**
- `a` trỏ đến `a[0]` (địa chỉ đầu tiên)
- `a + 2` trỏ đến `a[2]` (dịch chuyển 2 vị trí)
- `*(a + 2)` = giá trị tại `a[2]` = 3

**💻 Các cách truy cập tương đương:**
```cpp
a[2]      // 3
*(a + 2)  // 3  
2[a]      // 3 (ít dùng)
```

---

## **CÂU 20:** Dòng nào là cách khai báo con trỏ đến struct SinhVien đúng nhất?
**a) SinhVien *sv;**  
**b) SinhVien sv*;**  
**c) *SinhVien sv;**  
**d) pointer SinhVien;**

### ✅ **ĐÁP ÁN: A) SinhVien *sv;**

**📝 Cú pháp khai báo con trỏ struct:**

**Cấu trúc:** `TenStruct *TenBien;`

✅ **a) `SinhVien *sv;`** - Cú pháp đúng

❌ **b) `SinhVien sv*;`** - Sai vị trí dấu *

❌ **c) `*SinhVien sv;`** - Sai cú pháp hoàn toàn

❌ **d) `pointer SinhVien;`** - Không có từ khóa `pointer` trong C++

**💻 Ví dụ hoàn chỉnh:**
```cpp
struct SinhVien {
    int maSV;
    string hoTen;
    float diem;
};

// Các cách khai báo và sử dụng:
SinhVien *sv;                    // Khai báo con trỏ
sv = new SinhVien;               // Cấp phát bộ nhớ
sv->maSV = 123;                  // Truy cập qua con trỏ
sv->hoTen = "Nguyen Van A";      
(*sv).diem = 8.5;                // Cách khác

delete sv;                       // Giải phóng bộ nhớ
```

---

## 🏆 **BẢNG ĐÁP ÁN TỔNG KẾT**

| Câu | Đáp án | Chủ đề | Độ khó |
|-----|--------|--------|--------|
| 1 | **A** | Phép chia nguyên | ⭐⭐ |
| 2 | **B** | Độ ưu tiên toán tử | ⭐⭐ |
| 3 | **B** | Toán tử tăng trước | ⭐⭐