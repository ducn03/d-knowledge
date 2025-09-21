
### **GIẢI ĐỀ THI LẬP TRÌNH C++ OT_001**

---

#### **CÂU 1: Thuật toán và Lưu đồ (1.0 điểm)**

##### a) Thuật toán là gì? Đặc trưng cơ bản

**Thuật toán (Algorithm)** là một tập hợp (dãy) hữu hạn các chỉ thị (hành động) được định nghĩa rõ ràng nhằm giải quyết một bài toán cụ thể. Nói cách khác, thuật toán là một dãy hữu hạn các thao tác được sắp xếp theo một trình tự xác định, sao cho sau khi thực hiện dãy thao tác đó, từ **Input** của bài toán, ta sẽ nhận được **Output** cần tìm.

**Các tiêu chuẩn (đặc trưng) của thuật toán:**
Dựa trên tài liệu môn học, một thuật toán cần đảm bảo các tiêu chuẩn sau:

*   **Tính chính xác/đúng**: Quá trình tính toán phải chính xác và khi kết thúc, thuật toán phải cung cấp kết quả đúng đắn.
*   **Tính phổ dụng/tổng quát**: Thuật toán phải có khả năng áp dụng cho cả một lớp các bài toán có đầu vào tương tự nhau, không chỉ giải quyết một trường hợp riêng lẻ.
*   **Tính khách quan/xác định**: Với cùng một điều kiện đầu vào, thuật toán phải luôn cho ra kết quả như nhau, dù được viết bởi nhiều người khác nhau.
*   **Tính kết thúc/hữu hạn**: Thuật toán bắt buộc phải dừng lại sau một số bước thực hiện hữu hạn.
*   **Tính rõ ràng/hiệu quả**: Các câu lệnh trong thuật toán phải minh bạch và được sắp xếp theo một thứ tự nhất định.

##### b) Lưu đồ là gì?

**Lưu đồ (Flowchart)** là một công cụ trực quan sử dụng các ký hiệu đồ họa để diễn đạt các thuật toán. Việc biểu diễn thuật toán bằng lưu đồ giúp người đọc theo dõi được sự phân cấp các trường hợp và quá trình xử lý, đặc biệt hữu ích với các thuật toán phức tạp.

**Các ký hiệu cơ bản**:
*   **Hình oval**: Bắt đầu/Kết thúc.
*   **Hình chữ nhật**: Xử lý/Tính toán.
*   **Hình thoi**: Điều kiện/Quyết định.
*   **Hình bình hành**: Nhập/Xuất dữ liệu.

---

#### **CÂU 2: Biến trong C/C++ (1.0 điểm)**

##### a) Khái niệm về biến và sự khác nhau giữa biến cục bộ và biến toàn cục

**Biến (Variable)** là một ô nhớ hoặc một vùng nhớ được đặt tên dùng để chứa dữ liệu trong quá trình thực hiện chương trình. Giá trị của biến có thể được thay đổi.

**So sánh biến cục bộ và biến toàn cục**:

| Tiêu chí | Biến cục bộ (Local Variable) | Biến toàn cục (Global Variable) |
| :--- | :--- | :--- |
| **Vị trí khai báo** | Bên trong một hàm hoặc một khối lệnh `{}`. | Bên ngoài tất cả các hàm, thường ở đầu file. |
| **Phạm vi (Scope)** | Chỉ có tác dụng bên trong khối lệnh chứa nó. | Toàn bộ chương trình. |
| **Thời gian tồn tại** | Được tạo ra khi vào khối lệnh và bị hủy khi ra khỏi khối lệnh đó. | Tồn tại suốt quá trình chạy chương trình. |
| **Khởi tạo mặc định**| **Không được tự động khởi tạo**, chứa giá trị rác (garbage value). | **Được tự động khởi tạo** bằng 0 hoặc giá trị tương đương (số là 0, char là `\0`, con trỏ là `NULL`). |

##### b) Giá trị biến khi không khởi tạo và tại sao cần khởi tạo

*   **Khi khai báo biến mà không khởi tạo:**
    *   **Biến cục bộ**: Chứa **giá trị rác (garbage value)**, là một giá trị không xác định.
    *   **Biến toàn cục**: Được hệ thống **tự động khởi tạo** bằng giá trị 0 (đối với kiểu số), `\0` (đối với kiểu ký tự), hoặc `NULL` (đối với con trỏ).
*   **Tại sao cần khởi tạo biến (đặc biệt là biến cục bộ):**
    *   Để tránh các lỗi logic khó lường do sử dụng giá trị rác không mong muốn.
    *   Để đảm bảo chương trình hoạt động đúng như dự kiến và tăng tính ổn định.

---

#### **CÂU 3: Hàm trong C++ (1.0 điểm)**

##### a) Cấu trúc khai báo và định nghĩa hàm

**Cấu trúc định nghĩa một hàm** bao gồm các thành phần sau:

```cpp
kiểu_trả_về tên_hàm([danh sách tham số]) {
    <các câu lệnh>
    return <giá_trị_trả_về>;
}
```

*   **`kiểu_trả_về` (Return type)**: Là bất kỳ kiểu dữ liệu nào của C++. Nếu hàm không trả về giá trị thì kiểu là `void`.
*   **`tên_hàm` (Function name)**: Đặt theo quy tắc đặt tên biến.
*   **`danh sách tham số` (Parameter list)**: Khai báo các biến mà hàm nhận vào, giống như khai báo biến thông thường và cách nhau bởi dấu phẩy.
*   **`return <giá_trị_trả_về>`**: Dùng để trả về kết quả đầu ra của hàm. Lệnh `return` cũng sẽ kết thúc việc thực thi của hàm.

##### b) Kiểu dữ liệu hàm có thể trả về

Hàm trong C++ có thể trả về nhiều loại kiểu dữ liệu khác nhau:

*   **Các kiểu dữ liệu cơ bản**: `int`, `float`, `double`, `char`, `bool`.
*   **Kiểu `void`**: Dùng khi hàm không cần trả về giá trị nào.
*   **Kiểu con trỏ**: `int*`, `char*`,... Hàm có thể trả về một địa chỉ bộ nhớ.
*   **Kiểu cấu trúc (`struct`)**: Hàm có thể trả về một đối tượng có kiểu dữ liệu do người dùng định nghĩa.
*   **Kiểu tham chiếu (`&`)**: `int&`, `float&`,... Hàm trả về một tham chiếu đến một biến, cho phép thay đổi giá trị của biến đó từ bên ngoài.

---

#### **CÂU 4: Đệ quy (1.0 điểm)**

##### a) Đệ quy là gì? So sánh đệ quy và vòng lặp

**Đệ quy (Recursion)** là một kỹ thuật lập trình trong đó một vấn đề được giải quyết thông qua kết quả của chính vấn đề đó nhưng với đầu vào đơn giản hơn. Trong C++, điều này được thực hiện bằng một hàm gọi lại chính nó trong thân hàm.

**Cấu trúc hàm đệ quy:**
*   **Trường hợp cơ sở (Base case)**: Một điều kiện dừng, là một input đủ nhỏ để có thể giải quyết mà không cần gọi đệ quy thêm nữa.
*   **Lời gọi đệ quy (Recursive step)**: Hàm gọi lại chính nó với đầu vào được thu nhỏ lại, tiến gần hơn đến trường hợp cơ sở.

**So sánh đệ quy và vòng lặp:**

| Tiêu chí | Đệ quy | Vòng lặp |
| :--- | :--- | :--- |
| **Độ phức tạp code** | Ngắn gọn, trực quan với các bài toán có bản chất đệ quy. | Có thể dài hơn nhưng thường dễ theo dõi với người mới. |
| **Tốc độ thực thi** | Thường **chậm hơn** do chi phí cho các lời gọi hàm (function call overhead). | Thường **nhanh hơn**. |
| **Bộ nhớ sử dụng** | **Tốn nhiều bộ nhớ hơn** do sử dụng **Call Stack** để lưu trạng thái của mỗi lần gọi hàm. | Tốn ít bộ nhớ hơn. |
| **Nguy cơ lỗi** | Có nguy cơ bị **tràn bộ nhớ stack (stack overflow)** nếu lời gọi đệ quy quá sâu. | Không có vấn đề này. |

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