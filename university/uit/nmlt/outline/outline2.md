# GIẢI ĐỀ THI LẬP TRÌNH C++

## CÂU 1: Thuật toán và Lưu đồ (1.0 điểm)

### a) Thuật toán là gì?

**Thuật toán** là một tập hợp hữu hạn các bước thực hiện được xác định rõ ràng để giải quyết một bài toán cụ thể hoặc thực hiện một công việc nào đó.

**Đặc điểm của thuật toán:**
- **Tính hữu hạn**: Thuật toán phải kết thúc sau một số bước hữu hạn
- **Tính xác định**: Mỗi bước phải được mô tả rõ ràng, không gây nhập nhằng
- **Có đầu vào**: Có thể có 0 hoặc nhiều đầu vào
- **Có đầu ra**: Có ít nhất 1 đầu ra
- **Tính hiệu quả**: Mỗi bước phải đơn giản và có thể thực hiện được

### b) Lưu đồ là gì? Vẽ lưu đồ tính tổng các số lẻ từ 1 đến n

**Lưu đồ (Flowchart)** là một biểu đồ sử dụng các ký hiệu đồ họa để mô tả trình tự các bước thực hiện của thuật toán.

**Các ký hiệu cơ bản:**
- Hình oval: Bắt đầu/Kết thúc
- Hình chữ nhật: Xử lý/Tính toán
- Hình thoi: Điều kiện/Quyết định
- Hình bình hành: Nhập/Xuất dữ liệu

**Lưu đồ tính tổng các số lẻ từ 1 đến n:**

```
        [Bắt đầu]
             |
        [Nhập n]
             |
        [sum = 0]
        [i = 1]
             |
        <i <= n?>
         /      \
      Không     Có
        |        |
        |    <i % 2 == 1?>
        |      /        \
        |   Không      Có
        |     |         |
        |     |    [sum = sum + i]
        |     |         |
        |    [i = i + 2] |
        |     |         |
        |     \_________/
        |        |
        |   [Quay về điều kiện i <= n]
        |
    [In sum]
        |
    [Kết thúc]
```

---

## CÂU 2: Biến trong C/C++ (1.0 điểm)

### a) Khái niệm về biến và sự khác nhau giữa biến cục bộ và biến toàn cục

**Biến** là một vùng nhớ được đặt tên để lưu trữ dữ liệu, có thể thay đổi giá trị trong quá trình thực hiện chương trình.

**So sánh biến cục bộ và biến toàn cục:**

| Tiêu chí | Biến cục bộ | Biến toàn cục |
|----------|-------------|---------------|
| **Phạm vi** | Chỉ trong hàm/khối lệnh khai báo | Toàn bộ chương trình |
| **Vị trí khai báo** | Bên trong hàm/khối lệnh | Bên ngoài tất cả hàm |
| **Thời gian tồn tại** | Khi vào hàm tạo, ra khỏi hàm hủy | Suốt quá trình chạy chương trình |
| **Bộ nhớ** | Stack | Data segment |
| **Khởi tạo mặc định** | Không được khởi tạo | Được khởi tạo = 0 |

### b) Giá trị biến khi không khởi tạo và tại sao cần khởi tạo

**Khi khai báo biến mà không khởi tạo:**
- **Biến cục bộ**: Chứa giá trị rác (garbage value) - không xác định
- **Biến toàn cục**: Được tự động khởi tạo = 0

**Tại sao cần khởi tạo biến:**
- Tránh lỗi logic do giá trị rác không mong muốn
- Đảm bảo chương trình hoạt động đúng như mong đợi
- Tăng tính ổn định và dễ debug
- Tuân thủ nguyên tắc lập trình tốt

---

## CÂU 3: Hàm trong C++ (1.0 điểm)

### a) Cấu trúc khai báo và định nghĩa hàm

**Cấu trúc khai báo hàm:**
```cpp
kiểu_trả_về tên_hàm(danh_sách_tham_số);
```

**Cấu trúc định nghĩa hàm:**
```cpp
kiểu_trả_về tên_hàm(danh_sách_tham_số)
{
    // Thân hàm
    // Các câu lệnh
    return giá_trị; // (nếu hàm có kiểu trả về khác void)
}
```

**Ví dụ:**
```cpp
// Khai báo
int tinhTong(int a, int b);

// Định nghĩa
int tinhTong(int a, int b)
{
    int tong = a + b;
    return tong;
}
```

### b) Kiểu dữ liệu hàm có thể trả về

**Hàm có thể trả về các kiểu:**
- **Kiểu cơ bản**: int, float, double, char, bool
- **void**: Không trả về giá trị
- **Kiểu con trỏ**: int*, char*, float*
- **Kiểu cấu trúc**: struct, class
- **Kiểu tham chiếu**: int&, float&

**Ví dụ minh họa:**
```cpp
// Trả về int
int timMax(int a, int b) {
    return (a > b) ? a : b;
}

// Trả về void
void inThongTin() {
    cout << "Hello World!";
}

// Trả về con trỏ
int* taoMang(int n) {
    return new int[n];
}

// Trả về cấu trúc
struct Point {
    int x, y;
};

Point taoPoint(int x, int y) {
    Point p;
    p.x = x;
    p.y = y;
    return p;
}
```

---

## CÂU 4: Đệ quy (1.0 điểm)

### a) Đệ quy là gì? So sánh đệ quy và vòng lặp

**Đệ quy** là kỹ thuật lập trình trong đó một hàm gọi chính nó để giải quyết bài toán con nhỏ hơn.

**Cấu trúc đệ quy:**
- **Điều kiện dừng (base case)**: Trường hợp đơn giản nhất
- **Bước đệ quy**: Hàm gọi chính nó với tham số khác

**So sánh đệ quy và vòng lặp:**

| Tiêu chí | Đệ quy | Vòng lặp |
|----------|---------|----------|
| **Dễ hiểu** | Trực quan với bài toán có cấu trúc đệ quy | Dễ hiểu hơn với người mới |
| **Bộ nhớ** | Tiêu tốn nhiều (do stack) | Tiêu tốn ít |
| **Tốc độ** | Chậm hơn (overhead gọi hàm) | Nhanh hơn |
| **Ngăn xếp** | Có thể bị tràn stack | Không có vấn đề này |
| **Độ phức tạp code** | Ngắn gọn, elegant | Có thể dài hơn |

### b) Ví dụ minh họa

**Tính giai thừa n!:**

```cpp
// Đệ quy
int giaiThua_DeQuy(int n) {
    if (n <= 1)  // Điều kiện dừng
        return 1;
    return n * giaiThua_DeQuy(n - 1);  // Bước đệ quy
}

// Vòng lặp
int giaiThua_VongLap(int n) {
    int ketQua = 1;
    for (int i = 1; i <= n; i++) {
        ketQua *= i;
    }
    return ketQua;
}
```

**Dãy Fibonacci:**
```cpp
// Đệ quy
int fibonacci_DeQuy(int n) {
    if (n <= 1)
        return n;
    return fibonacci_DeQuy(n-1) + fibonacci_DeQuy(n-2);
}

// Vòng lặp
int fibonacci_VongLap(int n) {
    if (n <= 1) return n;
    int a = 0, b = 1, c;
    for (int i = 2; i <= n; i++) {
        c = a + b;
        a = b;
        b = c;
    }
    return b;
}
```

---

## CÂU 5: Phân tích chương trình (0.5 điểm)

```cpp
#include <iostream>
using namespace std;
int main()
{
    int x = 3, y = 9;
    y++;                // y = 10
    y += x;             // y = 10 + 3 = 13
    if(!(y == 13))      // !(13 == 13) = !true = false
        cout << x << "_" << y << endl;
    else                // Thực hiện nhánh else
        cout << x << "_" << y << endl;
    return 0;
}
```

**Kết quả:** `3_13`

---

## CÂU 6: Phân tích chương trình (0.5 điểm)

```cpp
#include <iostream>
using namespace std;
int main()
{
    int i = 0;
    while(i = 10)       // Gán i = 10, điều kiện luôn true (10 ≠ 0)
    {
        cout << i << "\t";  // In ra 10
        break;              // Thoát khỏi vòng lặp
        i++;                // Không bao giờ thực hiện
    }
    return 0;
}
```

**Kết quả:** `10`

**Giải thích:** `i = 10` là phép gán (không phải so sánh), giá trị trả về là 10 (true), nên vào vòng lặp và in 10, sau đó break thoát.

---

## CÂU 7: Phân tích chương trình (0.5 điểm)

```cpp
#include <iostream>
using namespace std;
int main()
{
    int a[]={5, 10, 9, 8, 4};  // a[0]=5, a[1]=10, a[2]=9, a[3]=8, a[4]=4
    int t = 0, i = 1;
    for(; i < 4; i++)          // i chạy từ 1 đến 3
        t += a[i];
    cout << t;
    return 0;
}
```

**Tính toán:**
- i = 1: t = 0 + a[1] = 0 + 10 = 10
- i = 2: t = 10 + a[2] = 10 + 9 = 19  
- i = 3: t = 19 + a[3] = 19 + 8 = 27

**Kết quả:** `27`

---

## CÂU 8: Phân tích hàm đệ quy (0.5 điểm)

```cpp
#include <iostream>
using namespace std;
int func(int x)
{
    if (x == 5)
        return 1;
    return func(x + 1) + x;
}
int main()
{
    cout << func(0);
    return 0;
}
```

**Trace thực hiện:**
- func(0) = func(1) + 0
- func(1) = func(2) + 1  
- func(2) = func(3) + 2
- func(3) = func(4) + 3
- func(4) = func(5) + 4 = 1 + 4 = 5

**Tính ngược lại:**
- func(4) = 5
- func(3) = 5 + 3 = 8
- func(2) = 8 + 2 = 10
- func(1) = 10 + 1 = 11
- func(0) = 11 + 0 = 11

**Kết quả:** `11`

---

## CÂU 9: Phân tích con trỏ (0.5 điểm)

```cpp
#include <iostream>
using namespace std;
int main()
{
    int x = 9;
    int *p = &x;        // p trỏ đến địa chỉ của x
    x = *p + 6;         // x = giá_trị_tại_p + 6 = 9 + 6 = 15
    cout << *p << " _ " << x;
    return 0;
}
```

**Giải thích:**
- p trỏ đến x, nên *p = x = 9
- x được gán = *p + 6 = 9 + 6 = 15
- Vì p vẫn trỏ đến x, nên *p cũng = 15

**Kết quả:** `15 _ 15`

---

## CÂU 10: Phân tích mảng 2 chiều (0.5 điểm)

```cpp
#include <iostream>
using namespace std;
int main()
{
    int a[][6]={
        {1, 2, 4, 3},
        {2, 4, 1, 2},
        {1, 2, 7, 3},
        {0, 1, 3, 9}};
    int s = 0;
    for(int i = 0; i < 4; i++)
        for(int j = 0; j < 3; j++)
            if(i != j)
                s = s + a[i][j];
    cout << s;
    return 0;
}
```

**Phân tích từng bước:**
- i=0: j=1→s+=a[0][1]=2, j=2→s+=a[0][2]=4 (s=6)
- i=1: j=0→s+=a[1][0]=2, j=2→s+=a[1][2]=1 (s=9)  
- i=2: j=0→s+=a[2][0]=1, j=1→s+=a[2][1]=2 (s=12)
- i=3: j=0→s+=a[3][0]=0, j=1→s+=a[3][1]=1 (s=13)

**Kết quả:** `13`

---

## CÂU 11: Phân tích hàm tìm min (1.0 điểm)

```cpp
#include <iostream>
using namespace std;
int func(int a[], int n)
{
    int m = a[0];           // m = 9
    for(int i = 0; i < n; i++)
    {
        if(a[i] < m)        // Tìm phần tử nhỏ nhất
            m = a[i];
    }
    return m;
}
int main()
{
    int a[] = {9, 3, 6, 8, 3, 9};
    cout << func(a, 6);
    return 0;
}
```

**Trace thực hiện:**
- i=0: a[0]=9, m=9
- i=1: a[1]=3 < 9 → m=3
- i=2: a[2]=6 > 3 → m=3
- i=3: a[3]=8 > 3 → m=3
- i=4: a[4]=3 = 3 → m=3
- i=5: a[5]=9 > 3 → m=3

**Hàm tìm giá trị nhỏ nhất trong mảng**

**Kết quả:** `3`

---

## CÂU 12: Viết hàm tính biểu thức (1.0 điểm)

**Mô tả Input và Output:**
- **Input**: Số thực x
- **Output**: Giá trị của biểu thức S = 1 + x + x²/2! + x³/3! + ... + x^n/n! (khai triển e^x)

```cpp
#include <iostream>
#include <math.h>
using namespace std;

// Hàm tính giai thừa
long long giaiThua(int n) {
    if (n <= 1) return 1;
    return n * giaiThua(n - 1);
}

// Hàm tính e^x bằng khai triển Taylor
double tinhEMuX(double x, int soPhanTu) {
    double ketQua = 0;
    for (int i = 0; i < soPhanTu; i++) {
        ketQua += pow(x, i) / giaiThua(i);
    }
    return ketQua;
}

// Cách tối ưu hơn (không dùng pow và giaiThua)
double tinhEMuX_ToiUu(double x, int soPhanTu) {
    double ketQua = 1.0;  // Số hạng đầu tiên
    double sohang = 1.0;   // Để tính số hạng tiếp theo
    
    for (int i = 1; i < soPhanTu; i++) {
        sohang *= x / i;    // x^i / i! = (x^(i-1) / (i-1)!) * x / i
        ketQua += sohang;
    }
    return ketQua;
}
```

---

## CÂU 13: Cấu trúc Nhân viên (1.0 điểm)

### a) Hàm nhập và xuất cho cấu trúc Nhân viên

```cpp
#include <iostream>
#include <cstring>
using namespace std;

struct NhanVien
{
    int maNV;
    char* hoTen;
    float luong;
};
typedef NhanVien NV;

// Hàm nhập thông tin nhân viên
void nhapNV(NV &nv) {
    cout << "Nhap ma nhan vien: ";
    cin >> nv.maNV;
    
    cin.ignore(); // Xóa ký tự xuống dòng còn lại
    
    cout << "Nhap ho ten: ";
    char temp[100];
    cin.getline(temp, 100);
    
    nv.hoTen = new char[strlen(temp) + 1];
    strcpy(nv.hoTen, temp);
    
    cout << "Nhap luong: ";
    cin >> nv.luong;
}

// Hàm xuất thông tin nhân viên
void xuatNV(const NV &nv) {
    cout << "Ma NV: " << nv.maNV << endl;
    cout << "Ho ten: " << nv.hoTen << endl;
    cout << "Luong: " << nv.luong << endl;
    cout << "------------------------" << endl;
}

// Hàm giải phóng bộ nhớ
void giaiPhongNV(NV &nv) {
    delete[] nv.hoTen;
    nv.hoTen = nullptr;
}
```

### b) Hàm tìm mã nhân viên có lương lớn nhất

```cpp
// Hàm tìm mã nhân viên có lương lớn nhất
int timMaNVLuongMax(const NV ds[], int n) {
    if (n <= 0) return -1; // Mảng rỗng
    
    int viTriMax = 0;
    float luongMax = ds[0].luong;
    
    for (int i = 1; i < n; i++) {
        if (ds[i].luong > luongMax) {
            luongMax = ds[i].luong;
            viTriMax = i;
        }
    }
    
    return ds[viTriMax].maNV;
}

// Hàm demo sử dụng
void demo() {
    int n;
    cout << "Nhap so luong nhan vien: ";
    cin >> n;
    
    NV* dsNV = new NV[n];
    
    // Nhập danh sách
    for (int i = 0; i < n; i++) {
        cout << "Nhap thong tin nhan vien thu " << i + 1 << ":" << endl;
        nhapNV(dsNV[i]);
    }
    
    // Xuất danh sách
    cout << "\nDANH SACH NHAN VIEN:" << endl;
    for (int i = 0; i < n; i++) {
        xuatNV(dsNV[i]);
    }
    
    // Tìm mã nhân viên có lương lớn nhất
    int maNVMax = timMaNVLuongMax(dsNV, n);
    cout << "Ma nhan vien co luong lon nhat: " << maNVMax << endl;
    
    // Giải phóng bộ nhớ
    for (int i = 0; i < n; i++) {
        giaiPhongNV(dsNV[i]);
    }
    delete[] dsNV;
}
```

---

## TỔNG KẾT

**Điểm quan trọng khi làm bài:**

1. **Đọc kỹ đề**: Hiểu rõ yêu cầu từng câu
2. **Phân tích code**: Trace từng bước thực hiện  
3. **Kiến thức cơ bản**: Nắm vững biến, hàm, đệ quy, con trỏ
4. **Cấu trúc dữ liệu**: Hiểu rõ mảng, struct
5. **Quản lý bộ nhớ**: Nhớ delete[] khi dùng new[]
6. **Coding style**: Code rõ ràng, có comment

**Lưu ý:**
- Luôn kiểm tra điều kiện biên  
- Xử lý trường hợp đặc biệt
- Giải phóng bộ nhớ động
- Tránh lỗi runtime như tràn stack, truy cập ngoài mảng