# 📘 ĐỀ CƯƠNG ÔN TẬP LÝ THUYẾT & THỰC HÀNH C++

## PHẦN LÝ THUYẾT

### **Câu 1: Thuật toán và Lưu đồ**

#### a. Thuật toán là gì? Đặc trưng cơ bản

**Thuật toán**: Là một dãy hữu hạn các bước được sắp xếp theo một trình tự xác định để giải quyết một bài toán.

**Đặc trưng cơ bản:**

1. **Tính xác định**: Mỗi bước phải rõ ràng, không mơ hồ
2. **Tính hữu hạn**: Phải kết thúc sau một số hữu hạn bước
3. **Có đầu vào**: Dữ liệu ban đầu
4. **Có đầu ra**: Kết quả sau khi xử lý
5. **Tính hiệu quả**: Thực hiện được trong thời gian hợp lý

#### b. Lưu đồ

**Lưu đồ (Flowchart)**: Là sơ đồ trực quan thể hiện các bước thực hiện một thuật toán bằng các khối (hình chữ nhật, hình thoi, mũi tên...).

**Vai trò trong lập trình:**
- Giúp dễ hình dung luồng xử lý của chương trình
- Giúp phát hiện lỗi logic trước khi viết code
- Tối ưu hóa, cải tiến chương trình

**Ví dụ**: Lưu đồ tính tổng từ `1` đến `n`

```
Bắt đầu
   ↓
Nhập n
   ↓
i = 1, sum = 0
   ↓
i <= n ? ----Không----> In sum → Kết thúc
   │
  Có
   ↓
sum = sum + i
   ↓
i = i + 1
   ↓
Quay lại bước kiểm tra i <= n ?
```

### **Câu 2: Biến và Mảng**

#### a. Biến trong C/C++

**Biến**: Là tên gọi dùng để tham chiếu đến một vùng nhớ lưu trữ dữ liệu.

**Phân biệt:**

**Biến cục bộ:**
- Khai báo trong hàm/khối lệnh
- Chỉ tồn tại khi hàm được gọi
- Ví dụ:

```cpp
void func() {
    int x = 10; // biến cục bộ
}
```

**Biến toàn cục:**
- Khai báo ngoài tất cả hàm
- Có thể dùng trong nhiều hàm
- Ví dụ:

```cpp
int x = 5; // biến toàn cục
void func() { 
    cout << x; 
}
```

#### b. Mảng trong C++

- Khi khai báo mảng cần biết số phần tử để **cấp phát bộ nhớ liên tục**
- Phải **kiểm tra độ dài mảng** để tránh:
  - Tràn bộ nhớ (array out of bounds)
  - Sai logic tính toán

### **Câu 3: Hàm và Cách truyền tham số**

#### a. Lợi ích của hàm

**Lợi ích:**
- Tái sử dụng mã nguồn
- Chia nhỏ chương trình → dễ quản lý
- Dễ bảo trì, dễ gỡ lỗi

**Ví dụ**: Hàm tính giai thừa

```cpp
int factorial(int n) {
    int result = 1;
    for(int i = 1; i <= n; i++) 
        result *= i;
    return result;
}
```

#### b. Truyền tham trị & tham chiếu

**Tham trị (call by value)**: Sao chép giá trị biến → không ảnh hưởng biến gốc

**Tham chiếu (call by reference)**: Truyền địa chỉ → thay đổi trực tiếp biến gốc

**Ví dụ:**

```cpp
void swapByValue(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
}

void swapByRef(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}
```

### **Câu 4: Đệ quy**

#### a. Đệ quy

**Đệ quy**: Hàm tự gọi lại chính nó để giải quyết bài toán nhỏ hơn.

**Ưu điểm:**
- Code ngắn gọn, dễ viết cho bài toán có tính lặp tự nhiên (giai thừa, dãy Fibonacci, cây, đồ thị...)

**Nhược điểm:**
- Dễ gây tràn ngăn xếp (stack overflow)
- Tốc độ chậm hơn vòng lặp nếu không tối ưu

#### b. Ví dụ: Tính giai thừa bằng đệ quy

```cpp
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

### **Câu 5: Phân tích bài toán**

**Các bước phân tích:**

1. Xác định **đầu vào** (Input)
2. Xác định **đầu ra** (Output)
3. Xác định **xử lý (Processing)**: Thuật toán, công thức
4. Vẽ **lưu đồ** hoặc viết **giả mã**
5. Chuyển sang **chương trình C++**

### **Câu 6: Ngôn ngữ lập trình**

**Ngôn ngữ lập trình**: Là tập hợp các quy tắc, từ khóa và cú pháp cho phép con người viết ra chương trình để máy tính hiểu và thực thi.

**Ví dụ**: C, C++, Java, Python...

---

## PHẦN THỰC HÀNH

### 1. **Lưu đồ thuật toán**
Vẽ lưu đồ tính tổng 1 → n

### 2. **Kiểu dữ liệu**
- `int`, `float`, `double`, `char`, `bool`
- Ví dụ:

```cpp
int a = 5;
float b = 3.14;
char c = 'A';
```

### 3. **Các phép toán**
- **Số học**: `+ - * / %`
- **So sánh**: `== != > < >= <=`
- **Logic**: `&& || !`
- **Gán**: `= += -= *= /=`

### 4. **Cấu trúc điều khiển**
- `if...else`, `switch...case`
- `for`, `while`, `do...while`

### 5. **Hàm**
Có tham số, có giá trị trả về

**Ví dụ:**
```cpp
int sum(int a, int b) { 
    return a + b; 
}
```

### 6. **Hàm đệ quy**
**Ví dụ**: Tính Fibonacci

```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n-1) + fib(n-2);
}
```

### 7. **Mảng một chiều**
```cpp
int arr[5] = {1, 2, 3, 4, 5};
```

### 8. **Mảng hai chiều**
{% raw %}
```cpp
int a[2][3] = {{1,2,3},{4,5,6}};
```
{% endraw %}

### 9. **Chuỗi ký tự**
```cpp
char str[] = "Hello";
```

### 10. **Con trỏ**
```cpp
int x = 10;
int *p = &x;
cout << *p; // 10
```

### 11. **Kiểu dữ liệu cấu trúc (struct)**
```cpp
struct Student {
    char name[50];
    int age;
    float score;
};
```

---

## 📝 LƯU Ý KHI ÔN TẬP

- Luyện tập vẽ lưu đồ cho các bài toán cơ bản
- Nắm vững sự khác biệt giữa biến cục bộ và toàn cục
- Hiểu rõ cách truyền tham số trong hàm
- Thực hành viết hàm đệ quy cho các bài toán đơn giản
- Luyện tập với mảng một chiều và hai chiều
- Làm quen với con trỏ và struct

**Chúc bạn ôn tập hiệu quả!** 🎯