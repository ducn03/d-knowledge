# 📘 ĐỀ CƯƠNG ÔN TẬP LÝ THUYẾT & THỰC HÀNH C++

## PHẦN LÝ THUYẾT

### **Câu 1: Thuật toán và Lưu đồ**

#### a. Thuật toán là gì? Đặc trưng cơ bản

**Thuật toán (Algorithm)**: Là tập hợp (dãy) hữu hạn các chỉ thị (hành động) được định nghĩa rõ ràng nhằm giải quyết một bài toán cụ thể nào đó.

**Đặc trưng cơ bản:**
1. **Tính chính xác/đúng**: Quá trình tính toán chính xác, cung cấp kết quả đúng đắn
2. **Tính phổ dụng/tổng quát**: Có thể áp dụng cho một lớp các bài toán có đầu vào tương tự
3. **Tính khách quan/xác định**: Được viết bởi nhiều người nhưng kết quả phải như nhau
4. **Tính kết thúc/hữu hạn**: Thuật toán phải dừng sau một số bước hữu hạn
5. **Tính rõ ràng/hiệu quả**: Các câu lệnh minh bạch được sắp xếp theo thứ tự nhất định

#### b. Lưu đồ (Flowchart)

**Lưu đồ**: Là công cụ trực quan để diễn đạt các thuật toán, giúp theo dõi được sự phân cấp các trường hợp và quá trình xử lý.

**Các ký hiệu cơ bản:**
- **Hình oval**: Bắt đầu/Kết thúc
- **Hình chữ nhật**: Xử lý/Tính toán  
- **Hình thoi**: Điều kiện/Quyết định
- **Hình bình hành**: Nhập/Xuất dữ liệu

#### c. Phương pháp biểu diễn thuật toán

1. **Ngôn ngữ tự nhiên**: Dễ hiểu nhưng dài dòng, không rõ cấu trúc
2. **Lưu đồ**: Trực quan, thể hiện rõ luồng xử lý
3. **Mã giả (pseudocode)**: Tựa ngôn ngữ lập trình, cấu trúc chuẩn hóa

### **Câu 2: Biến và Kiểu dữ liệu**

#### a. Bộ từ vựng C++

**Các thành phần:**
- **Ký tự**: A-Z, a-z, 0-9, ký hiệu toán học (+, -, *, /, =, <, >)
- **Từ khóa**: const, int, float, if, for, while, return, struct, typedef...
- **Tên/Định danh**: Không trùng từ khóa, bắt đầu bằng chữ cái hoặc _
- **Hằng ký tự**: 'A', 'a', '1'
- **Hằng chuỗi**: "Hello World"
- **Dấu chấm phẩy**: Phân cách các câu lệnh
- **Câu chú thích**: // hoặc /* */

#### b. Các kiểu dữ liệu cơ sở

**Kiểu số nguyên:**
- `short`: 2 bytes [-32,768, 32,767]
- `int`: 4 bytes [-2,147,483,648, 2,147,483,647]
- `long`: 4/8 bytes (tùy hệ điều hành)
- `long long`: 8 bytes
- `unsigned`: Các kiểu không dấu

**Kiểu số thực:**
- `float`: 4 bytes (~7 chữ số thập phân)
- `double`: 8 bytes (~15 chữ số thập phân)  
- `long double`: 8 bytes (~15 chữ số thập phân)

**Các kiểu khác:**
- `bool`: true/false (1 byte)
- `char`: ký tự ASCII (1 byte) [-128, 127] hoặc [0, 255]
- `void`: kiểu rỗng

#### c. Biến

**Khái niệm**: Biến là một ô nhớ hoặc vùng nhớ dùng để chứa dữ liệu trong quá trình thực hiện chương trình.

**Phân loại biến:**

**Biến cục bộ (Local variable):**
- Khai báo trong hàm hoặc block
- Chỉ tồn tại trong phạm vi khai báo
- Không tự khởi tạo giá trị
```cpp
void func() {
    int x = 10; // biến cục bộ
}
```

**Biến toàn cục (Global variable):**
- Khai báo ngoài tất cả hàm
- Có thể dùng trong toàn chương trình
- Tự động khởi tạo giá trị (int=0, char='\0', float=0)
```cpp
int x = 5; // biến toàn cục
void func() { 
    cout << x; 
}
```

#### d. Hằng (Constant)

**Khái niệm**: Hằng đại diện cho một giá trị không đổi trong suốt quá trình thực thi của chương trình.

**Cách định nghĩa:**

**Cách 1: Sử dụng #define**
```cpp
#define PI 3.14
```

**Cách 2: Sử dụng const**
```cpp
const float PI = 3.14;
```

**Các loại hằng:**
- **Hằng số nguyên**: 212, 0213 (hệ 8), 0x4B (hệ 16)
- **Hằng số thực**: 102.0, 1.23e-3, 45.0
- **Hằng luận lý**: true, false
- **Hằng chuỗi**: "Hello World"

### **Câu 3: Cấu trúc điều khiển**

#### a. Cấu trúc rẽ nhánh

**Cấu trúc if:**
```cpp
if (điều_kiện) {
    // lệnh thực hiện
}
```

**Cấu trúc if-else:**
```cpp
if (điều_kiện) {
    // lệnh 1
} else {
    // lệnh 2
}
```

**Cấu trúc switch-case:**
```cpp
switch (biểu_thức) {
    case hằng_số_1:
        // câu lệnh 1
        break;
    case hằng_số_2:
        // câu lệnh 2
        break;
    default:
        // câu lệnh mặc định
}
```

**Lưu ý về switch-case:**
- Biểu thức điều kiện phải là kiểu số nguyên
- Các hằng số phải khác nhau
- Không có `break` sẽ thực hiện "fall through"
- `default` không bắt buộc

#### b. Cấu trúc lặp

**Vòng lặp for:**
```cpp
for (khởi_tạo; điều_kiện; cập_nhật) {
    // thân vòng lặp
}
```

**Vòng lặp while:**
```cpp
while (điều_kiện) {
    // thân vòng lặp
}
```

**Vòng lặp do-while:**
```cpp
do {
    // thân vòng lặp
} while (điều_kiện);
```

**Lệnh điều khiển vòng lặp:**
- `break`: Thoát khỏi vòng lặp
- `continue`: Bỏ qua phần còn lại, chuyển lần lặp tiếp theo

### **Câu 4: Hàm (Function)**

#### a. Cú pháp hàm

```cpp
kiểu_trả_về tên_hàm([danh_sách_tham_số]) {
    // các câu lệnh
    return giá_trị_trả_về;
}
```

#### b. Các bước viết hàm

1. **Tên hàm**: Xác định chức năng
2. **Đầu vào**: Số lượng tham số, kiểu dữ liệu
3. **Đầu ra**: Kiểu dữ liệu đầu ra (void nếu không có)
4. **Nội dung**: Các lệnh thực hiện công việc

#### c. Truyền tham số

**Truyền tham trị (Pass by value):**
- Tham số chứa bản sao giá trị của đối số
- Thay đổi tham số không ảnh hưởng đối số
```cpp
void func(int x) {
    x = 10; // không ảnh hưởng biến gốc
}
```

**Truyền tham chiếu (Pass by reference):**
- Tham số trỏ đến cùng địa chỉ với đối số
- Thay đổi tham số ảnh hưởng trực tiếp đối số
```cpp
void swap(int& a, int& b) {
    int temp = a;
    a = b;
    b = temp;
}
```

#### d. Phạm vi biến (Scope)

- **Biến cục bộ**: Trong khối ngoặc nhọn {}
- **Biến toàn cục**: Bên ngoài tất cả hàm
- **Nguyên mẫu hàm (Prototype)**: Khai báo hàm trước, định nghĩa sau

### **Câu 5: Mảng (Array)**

#### a. Mảng một chiều

**Khái niệm**: Mảng là tập hợp các phần tử có cùng kiểu dữ liệu, được lưu trữ liên tiếp trong bộ nhớ.

**Khai báo:**
```cpp
kiểu_dữ_liệu tên_mảng[số_phần_tử];
```

**Khởi tạo:**
```cpp
int a[4] = {29, 137, 50, 4};      // Khởi tạo đầy đủ
int b[4] = {91, 106};             // Khởi tạo một phần (phần còn lại = 0)
int c[4] = {0};                   // Khởi tạo toàn 0
int d[] = {22, 16, 56, 19};       // Tự xác định kích thước
```

**Truy xuất:**
```cpp
tên_mảng[chỉ_số]  // chỉ số từ 0 đến n-1
```

#### b. Mảng hai chiều

**Khai báo:**
```cpp
kiểu_dữ_liệu tên_mảng[số_dòng][số_cột];
```

**Khởi tạo:**
```cpp
int a[2][3] = {{1,2,3}, {4,5,6}};
```

**Truy xuất:**
```cpp
tên_mảng[chỉ_số_dòng][chỉ_số_cột]
```

**Các khái niệm quan trọng:**
- **Đường chéo chính**: a[i][i] (i = j)
- **Đường chéo phụ**: a[i][n-1-i] 
- **Nửa trên đường chéo chính**: i < j
- **Nửa dưới đường chéo chính**: i > j

#### c. Các tác vụ cơ bản trên mảng

**Nhập mảng:**
```cpp
void nhapMang(int a[], int n) {
    for(int i = 0; i < n; i++) {
        cout << "a[" << i << "] = ";
        cin >> a[i];
    }
}
```

**Xuất mảng:**
```cpp
void xuatMang(int a[], int n) {
    for(int i = 0; i < n; i++) {
        cout << a[i] << " ";
    }
}
```

**Tìm kiếm:**
```cpp
int timKiem(int a[], int n, int x) {
    for (int i = 0; i < n; i++) {
        if (a[i] == x) return i;
    }
    return -1;
}
```

#### d. Truyền mảng cho hàm

```cpp
void sapXep(int A[], int n);        // Cách 1
void sapXep(int A[100], int n);     // Cách 2
void sapXep(int *A, int n);         // Cách 3 (con trỏ)

// Mảng 2 chiều
void nhapMaTran(int A[][MAXC], int m, int n);
void nhapMaTran(int (*A)[MAXC], int m, int n);
```

### **Câu 6: Con trỏ (Pointer)**

#### a. Khái niệm con trỏ

**Con trỏ**: Là một biến lưu trữ địa chỉ của một địa chỉ bộ nhớ, thường là địa chỉ của một biến khác.

**Toán tử quan trọng:**
- `&`: Toán tử lấy địa chỉ (Address-of Operator)
- `*`: Toán tử truy cập giá trị (Dereferencing Operator)

#### b. Khai báo và sử dụng con trỏ

**Khai báo:**
```cpp
kiểu_dữ_liệu *tên_con_trỏ;
int *p;          // con trỏ trỏ đến int
float *pf;       // con trỏ trỏ đến float
char *pc;        // con trỏ trỏ đến char
```

**Khởi tạo và sử dụng:**
```cpp
int a = 10;
int *p = &a;     // p trỏ đến a
cout << *p;      // xuất giá trị của a thông qua con trỏ
*p = 20;         // thay đổi giá trị a thông qua con trỏ
```

#### c. Con trỏ và mảng

**Mối quan hệ:**
- Tên mảng là một hằng con trỏ trỏ đến phần tử đầu tiên
- `arr == &arr[0]`
- `arr[i] == *(arr + i)`

```cpp
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;    // p trỏ đến phần tử đầu tiên

// Truy xuất thông qua con trỏ
cout << *(p + 2);    // tương đương arr[2]
cout << p[2];        // tương đương arr[2]
```

#### d. Phép toán số học trên con trỏ

**Phép cộng/trừ:**
```cpp
p + n;    // tăng n * sizeof(kiểu_dữ_liệu) bytes
p - n;    // giảm n * sizeof(kiểu_dữ_liệu) bytes
p++;      // tăng 1 phần tử
p--;      // giảm 1 phần tử
```

**Phép so sánh:**
```cpp
p1 == p2;    // so sánh địa chỉ
p1 < p2;     // so sánh thứ tự địa chỉ
p1 - p2;     // khoảng cách (số phần tử)
```

#### e. Con trỏ và từ khóa const

```cpp
int x = 5;
const int *p1 = &x;      // không thể thay đổi *p1
int * const p2 = &x;     // không thể thay đổi p2
const int * const p3 = &x; // không thể thay đổi cả p3 và *p3
```

### **Câu 7: Cấp phát động (Dynamic Memory Allocation)**

#### a. Khái niệm

**Cấp phát tĩnh**: Kích thước xác định tại compile time
**Cấp phát động**: Kích thước xác định tại runtime, linh hoạt hơn

**Cấu trúc bộ nhớ chương trình C++:**
- **STACK**: Lưu biến cục bộ, tham số hàm (LIFO)
- **HEAP**: Vùng cấp phát động (RAM trống và bộ nhớ ảo)
- **Vùng dữ liệu**: Biến toàn cục và tĩnh
- **Mã chương trình**: Các lệnh và hằng

#### b. Toán tử new và delete

**Cấp phát cho biến:**
```cpp
int *p = new int;        // cấp phát 1 số nguyên
int *p = new int(10);    // cấp phát và khởi tạo giá trị 10
```

**Cấp phát cho mảng:**
```cpp
int *arr = new int[n];   // cấp phát mảng n phần tử
```

**Giải phóng bộ nhớ:**
```cpp
delete p;         // giải phóng biến
delete[] arr;     // giải phóng mảng
p = NULL;         // tránh con trỏ lạc
```

#### c. Kiểm tra cấp phát thành công

```cpp
int *p = new int;
if (p == NULL) {
    cout << "Không đủ bộ nhớ!";
    exit(1);
}
```

#### d. Cấp phát mảng 2 chiều động

```cpp
// Cấp phát
int **p = new int*[m];    // m dòng
for (int i = 0; i < m; i++) {
    p[i] = new int[n];    // n cột cho mỗi dòng
}

// Giải phóng
for (int i = 0; i < m; i++) {
    delete[] p[i];
}
delete[] p;
```

### **Câu 8: Đệ quy (Recursion)**

#### a. Khái niệm

**Đệ quy**: Hàm tự gọi lại chính nó để giải quyết bài toán con nhỏ hơn.

**Thành phần:**
- **Điều kiện dừng (base case)**: Trường hợp cơ sở không cần gọi đệ quy
- **Lời gọi đệ quy**: Gọi hàm với tham số nhỏ hơn hoặc đơn giản hơn

#### b. Phân loại đệ quy

**Đệ quy tuyến tính (Single recursion):**
- Chỉ có một lời gọi đệ quy
- Dễ chuyển thành vòng lặp

```cpp
int giaiThua(int n) {
    if (n == 0) return 1;        // base case
    return n * giaiThua(n-1);    // recursive call
}
```

**Đệ quy phi tuyến (Multiple recursion):**
- Có nhiều lời gọi đệ quy
- Khó chuyển thành vòng lặp

```cpp
int fibonacci(int n) {
    if (n < 2) return n;         // base case
    return fibonacci(n-1) + fibonacci(n-2);  // 2 recursive calls
}
```

**Đệ quy hỗ tương (Mutual recursion):**
- Hàm gọi đệ quy thông qua hàm khác

#### c. Call Stack và đệ quy

- Mỗi lời gọi hàm tạo một frame trong stack
- Stack có kích thước hữu hạn → nguy cơ stack overflow
- Đệ quy sâu có thể gây tràn ngăn xếp

#### d. Ưu nhược điểm

**Ưu điểm:**
- Code ngắn gọn, dễ hiểu
- Phù hợp với bài toán có tính chất đệ quy tự nhiên

**Nhược điểm:**
- Tốn bộ nhớ (stack)
- Có thể chậm hơn vòng lặp
- Nguy cơ tràn ngăn xếp

### **Câu 9: Kiểu cấu trúc (Struct)**

#### a. Khai báo struct

**Cú pháp:**
```cpp
struct tên_kiểu_cấu_trúc {
    kiểu_dữ_liệu thành_phần_1;
    kiểu_dữ_liệu thành_phần_2;
    // ...
};
```

**Ví dụ:**
```cpp
struct SinhVien {
    int maSV;
    string hoTen;
    float diemTB;
};
```

#### b. Sử dụng typedef

```cpp
typedef struct {
    int maSV;
    string hoTen;
    float diemTB;
} SV;

SV sv1;  // Khai báo biến
```

#### c. Truy xuất dữ liệu

**Toán tử chấm (.)**
```cpp
SinhVien sv1 = {123, "Nguyen Van A", 8.5};
cout << sv1.maSV << endl;
cout << sv1.hoTen << endl;
cout << sv1.diemTB << endl;
```

**Toán tử mũi tên (->)** cho con trỏ struct:
```cpp
SinhVien *p = &sv1;
cout << p->maSV << endl;      // tương đương (*p).maSV
cout << p->hoTen << endl;     // tương đương (*p).hoTen
```

#### d. Mảng cấu trúc

```cpp
struct DIEM {
    int x;
    int y;
};

DIEM mang1[20];
DIEM mang2[10] = {{3, 2}, {4, 4}, {2, 7}};
```

### **Câu 10: Chuỗi ký tự (String)**

#### a. Khái niệm

**Chuỗi ký tự**: Mảng các ký tự kết thúc bằng ký tự '\0' (null terminator)

#### b. Khai báo và khởi tạo

```cpp
char str[100];                    // khai báo
char str1[10] = "Hello";          // khởi tạo
char str2[] = "World";            // tự xác định kích thước
char str3[] = {'H','i','\0'};     // khởi tạo từng ký tự
```

#### c. Nhập xuất chuỗi

```cpp
char str[100];
gets(str);      // nhập chuỗi (có thể chứa khoảng trắng)
puts(str);      // xuất chuỗi
cin >> str;     // nhập (dừng tại khoảng trắng)
cout << str;    // xuất
```

#### d. Các hàm thư viện <string.h>

```cpp
strlen(str);           // độ dài chuỗi
strcpy(dest, src);     // sao chép chuỗi
strcat(dest, src);     // nối chuỗi
strcmp(str1, str2);    // so sánh chuỗi (phân biệt hoa thường)
stricmp(str1, str2);   // so sánh không phân biệt hoa thường
strupr(str);           // chuyển thành chữ hoa
strlwr(str);           // chuyển thành chữ thường
strrev(str);           // đảo ngược chuỗi
strstr(str, substr);   // tìm chuỗi con
```

---

## PHẦN THỰC HÀNH

### **1. Lưu đồ thuật toán**

#### Các bài tập cơ bản:

**a) Tính tổng từ 1 đến n:**
```
Bắt đầu → Nhập n → i=1, sum=0 → i≤n? 
→ sum=sum+i, i=i+1 → Xuất sum → Kết thúc
```

**b) Kiểm tra số nguyên tố:**
```
Bắt đầu → Nhập n → i=2 → i<n? → n%i==0? 
→ "Không phải SNT" / "Là SNT" → Kết thúc
```

**c) Tìm USCLN của 2 số:**
```
Bắt đầu → Nhập a,b → a!=b? → a>b? 
→ a=a-b / b=b-a → Xuất a → Kết thúc
```

### **2. Các bài tập về kiểu dữ liệu và biến**

```cpp
// Khai báo các kiểu dữ liệu
int tuoi = 20;
float diem = 8.5;
char kytu = 'A';
bool ketQua = true;
string hoTen = "Nguyen Van A";

// Sử dụng const và #define
#define PI 3.14159
const int MAX_SIZE = 100;
```

### **3. Cấu trúc điều khiển**

#### a) Bài tập if-else

**Xác định học lực:**
```cpp
void xacDinhHocLuc(float diem) {
    if (diem >= 9.0) 
        cout << "Xuất sắc";
    else if (diem >= 8.0)
        cout << "Giỏi";
    else if (diem >= 6.5)
        cout << "Khá";
    else if (diem >= 5.0)
        cout << "Trung bình";
    else
        cout << "Yếu";
}
```

#### b) Bài tập switch-case

**Menu lựa chọn:**
```cpp
void menu() {
    int choice;
    cout << "1. Cộng\n2. Trừ\n3. Nhân\n4. Chia\n";
    cin >> choice;
    
    switch(choice) {
        case 1: cout << "Chọn phép cộng"; break;
        case 2: cout << "Chọn phép trừ"; break;
        case 3: cout << "Chọn phép nhân"; break;
        case 4: cout << "Chọn phép chia"; break;
        default: cout << "Lựa chọn không hợp lệ";
    }
}
```

#### c) Bài tập vòng lặp

**Tính tổng dãy số:**
```cpp
// Tính S = 1 + 1/2 + 1/3 + ... + 1/n
float tinhTong(int n) {
    float sum = 0;
    for(int i = 1; i <= n; i++) {
        sum += 1.0/i;
    }
    return sum;
}

// Tính S = 1² + 2² + 3² + ... + n²
int tinhTongBinhPhuong(int n) {
    int sum = 0;
    for(int i = 1; i <= n; i++) {
        sum += i * i;
    }
    return sum;
}
```

### **4. Hàm**

#### a) Hàm có tham số và giá trị trả về

```cpp
// Hàm tìm max của 3 số
int timMax3So(int a, int b, int c) {
    int max = a;
    if (b > max) max = b;
    if (c > max) max = c;
    return max;
}

// Hàm kiểm tra số nguyên tố
bool laSoNguyenTo(int n) {
    if (n < 2) return false;
    for(int i = 2; i * i <= n; i++) {
        if (n % i == 0) return false;
    }
    return true;
}
```