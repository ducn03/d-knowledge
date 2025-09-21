***

# 📘 **ĐỀ CƯƠNG ÔN TẬP LÝ THUYẾT C++ (CHI TIẾT 12 CHỦ ĐỀ)**

---

### **Câu 1: Bài toán, Thuật toán và Lưu đồ**

#### **a. Khái niệm Bài toán và Thuật toán**

*   **Bài toán (Problem)**: Là một vấn đề cần tìm ra giải pháp để đạt được một mục tiêu xác định (Kết luận) từ những điều kiện ban đầu (Giả thiết). Trong Tin học, một bài toán được biểu diễn dưới dạng: **Input (Đầu vào) → Giải pháp → Output (Đầu ra)**.
*   **Thuật toán (Algorithm)**: Là một **dãy hữu hạn các chỉ thị (hành động) được định nghĩa rõ ràng** nhằm giải quyết một bài toán cụ thể. Nói cách khác, đó là một chuỗi các thao tác được sắp xếp theo một trình tự xác định để biến đổi **Input** thành **Output** mong muốn. Lập trình viên là người phân tích vấn đề và tạo ra các chỉ dẫn này để máy tính thực hiện.

#### **b. Đặc trưng (Tiêu chuẩn) của một Thuật toán**

Một thuật toán tốt cần phải đáp ứng các tiêu chuẩn sau:

1.  **Tính chính xác/đúng (Correctness)**: Thuật toán phải cung cấp kết quả đúng đắn cho mọi bộ dữ liệu đầu vào hợp lệ.
2.  **Tính phổ dụng/tổng quát (Generality)**: Có thể áp dụng cho cả một lớp các bài toán có đầu vào tương tự, không chỉ giải quyết một trường hợp riêng lẻ.
3.  **Tính khách quan/xác định (Determinism)**: Với cùng một đầu vào, thuật toán phải luôn cho ra cùng một kết quả, dù được thực hiện bởi ai hay trên máy tính nào.
4.  **Tính kết thúc/hữu hạn (Finiteness)**: Thuật toán phải dừng lại sau một số bước thực hiện hữu hạn.
5.  **Tính rõ ràng/hiệu quả (Effectiveness)**: Các câu lệnh phải minh bạch, đơn giản và có thể thực hiện được.

#### **c. Các phương pháp biểu diễn thuật toán**

Có 3 phương pháp chính:

1.  **Dùng ngôn ngữ tự nhiên**: Liệt kê các bước bằng ngôn ngữ hàng ngày.
    *   **Ưu điểm**: Dễ hiểu, không cần quy tắc.
    *   **Nhược điểm**: Thường dài dòng, không thể hiện rõ cấu trúc và đôi lúc gây khó hiểu.
2.  **Dùng lưu đồ - sơ đồ khối (Flowchart)**: Là một công cụ trực quan sử dụng các ký hiệu đồ họa để diễn tả thuật toán. Rất hữu ích cho các thuật toán phức tạp.
3.  **Dùng mã giả (Pseudocode)**: Sử dụng ngôn ngữ tựa như ngôn ngữ lập trình với cấu trúc chuẩn hóa.
    *   **Ưu điểm**: Đỡ cồng kềnh hơn lưu đồ.
    *   **Nhược điểm**: Không trực quan bằng lưu đồ.

#### **d. Ví dụ: Giải phương trình bậc nhất `ax + b = 0`**

*   **Biểu diễn bằng ngôn ngữ tự nhiên**:
    1.  Nhập 2 số thực a và b.
    2.  Nếu a = 0:
        *   Nếu b = 0 thì thông báo "Phương trình vô số nghiệm".
        *   Ngược lại (b ≠ 0) thì thông báo "Phương trình vô nghiệm".
    3.  Ngược lại (a ≠ 0):
        *   Tính nghiệm x = -b/a.
        *   Thông báo "Phương trình có nghiệm x = [giá trị]".
    4.  Kết thúc.

*   **Biểu diễn bằng mã giả**:
    ```pseudocode
    Input: a, b
    Output: nghiệm của phương trình ax + b = 0

    If a = 0 Then
    Begin
      If b = 0 Then
        Xuất "Phương trình vô số nghiệm"
      Else
        Xuất "Phương trình vô nghiệm"
    End
    Else
      Xuất "Phương trình có nghiệm x = -b/a"
    ```

---

### **Câu 2: Kiểu dữ liệu, Biến và Hằng**

#### **a. Bộ từ vựng của C++**

Chương trình C++ được xây dựng từ các thành phần cơ bản sau:
*   **Ký tự**: Bảng chữ cái Latin, chữ số, và các ký tự đặc biệt.
*   **Từ khóa (Keywords)**: Các từ dành riêng cho ngôn ngữ (ví dụ: `int`, `for`, `if`, `return`), không được dùng để đặt tên.
*   **Tên/Định danh (Identifiers)**: Tên do người lập trình đặt. Quy tắc: không trùng từ khóa, bắt đầu bằng chữ cái hoặc `_`, không chứa khoảng trắng.
*   **Hằng**: Hằng ký tự ('A'), hằng chuỗi ("Xin Chao").
*   **Dấu chấm phẩy (`;`)**: Dùng để kết thúc một câu lệnh.
*   **Chú thích (Comments)**: `//` hoặc `/* */`. Trình biên dịch sẽ bỏ qua các chú thích.

#### **b. Các kiểu dữ liệu cơ sở**

*   **Kiểu số nguyên**: `short`, `int` (thường 4 bytes), `long`, `long long` và các phiên bản không dấu `unsigned`.
*   **Kiểu số thực**: `float` (4 bytes), `double` (8 bytes), `long double`.
*   **Kiểu luận lý/logic**: `bool` (1 byte), chỉ nhận giá trị `true` (khác 0) hoặc `false` (bằng 0).
*   **Kiểu ký tự**: `char` (1 byte), lưu trữ mã ASCII của ký tự.
*   **Kiểu rỗng**: `void`, dùng cho hàm không trả về giá trị hoặc con trỏ chung.

#### **c. Biến (Variable)**

*   **Khái niệm**: Là một vùng nhớ được đặt tên dùng để lưu trữ dữ liệu. Giá trị của biến có thể thay đổi trong quá trình chạy chương trình.
*   **Phân loại biến**:
    *   **Biến cục bộ (Local)**: Khai báo bên trong một hàm hoặc khối lệnh `{}`. Chỉ tồn tại trong phạm vi đó. **Không được tự động khởi tạo** (chứa giá trị rác).
    *   **Biến toàn cục (Global)**: Khai báo bên ngoài tất cả các hàm. Có phạm vi toàn chương trình. **Được tự động khởi tạo bằng 0** (hoặc giá trị tương đương).

#### **d. Hằng (Constant)**

*   **Khái niệm**: Đại diện cho một giá trị không đổi trong suốt chương trình.
*   **Cách định nghĩa**:
    1.  `#define TEN_HANG GIA_TRI`: Chỉ thị tiền xử lý. Tên hằng sẽ được thay thế bằng giá trị trước khi biên dịch, không chiếm bộ nhớ.
    2.  `const kieu_du_lieu TEN_HANG = GIA_TRI;`: Biến hằng, có kiểu dữ liệu và chiếm dung lượng bộ nhớ.

#### **e. Ví dụ**
```cpp
#include <iostream>

#define PI 3.14 // Định nghĩa hằng bằng #define
const int MAX_USERS = 100; // Định nghĩa hằng bằng const

int global_counter = 0; // Biến toàn cục, tự động khởi tạo bằng 0

int main() {
    int local_variable = 10; // Biến cục bộ, phải khởi tạo
    float radius = 5.5;
    char initial = 'A';
    bool is_active = true;

    // Sử dụng biến và hằng
    double area = PI * radius * radius;
    global_counter++;

    std::cout << "Local variable: " << local_variable << std::endl;
    std::cout << "Global counter: " << global_counter << std::endl;
    std::cout << "Area of circle: " << area << std::endl;
    
    return 0;
}
```

---

### **Câu 3: Các phép toán và Biểu thức**

*   **Toán tử gán (`=`)**: Gán giá trị cho biến.
*   **Toán tử toán học**: `+`, `-`, `*`, `/`, `%`. Lưu ý: phép `/` giữa hai số nguyên là **chia lấy phần nguyên**; nếu một trong hai toán hạng là số thực, kết quả sẽ là số thực.
*   **Toán tử tăng/giảm (`++`, `--`)**: Có 2 dạng: tiền tố (`++x`, tăng trước rồi mới thực hiện biểu thức) và hậu tố (`x++`, thực hiện biểu thức trước rồi mới tăng).
*   **Toán tử quan hệ**: `==`, `!=`, `>`, `<`, `>=`, `<=` dùng để so sánh, trả về `true` hoặc `false`.
*   **Toán tử luận lý**: `&&` (AND), `||` (OR), `!` (NOT).
*   **Biểu thức (Expression)**: Là sự kết hợp giữa toán hạng (biến, hằng) và các toán tử.
*   **Độ ưu tiên toán tử**: Các toán tử có thứ tự ưu tiên thực hiện khác nhau. Ví dụ `*`, `/` ưu tiên hơn `+`, `-`; `++` ưu tiên cao hơn `*`.

#### **Ví dụ**
```cpp
#include <iostream>

int main() {
    int a = 10, b = 4;
    
    // Phép toán học
    int sum = a + b; // 14
    int int_div = a / b; // 2 (chia nguyên)
    float float_div = (float)a / b; // 2.5 (ép kiểu để chia thực)
    int remainder = a % b; // 2 (phần dư)

    std::cout << "Integer division: " << int_div << std::endl;
    std::cout << "Float division: " << float_div << std::endl;

    // Phép tăng/giảm
    int x = 5;
    int y = ++x; // x=6, y=6 (tăng trước)
    std::cout << "Prefix increment: x=" << x << ", y=" << y << std::endl;
    
    x = 5;
    y = x++; // x=6, y=5 (tăng sau)
    std::cout << "Postfix increment: x=" << x << ", y=" << y << std::endl;

    // Phép quan hệ và luận lý
    bool result = (a > b) && (x == 6); // (true && true) -> true
    std::cout << "Logical result: " << result << std::endl; // in ra 1

    return 0;
}
```

---

### **Câu 4: Cấu trúc điều khiển**

#### **a. Cấu trúc rẽ nhánh**

*   **`if`**: Thực hiện một khối lệnh nếu điều kiện đúng (khác 0).
*   **`if-else`**: Thực hiện khối lệnh 1 nếu điều kiện đúng, ngược lại thực hiện khối lệnh 2.
*   **`switch-case`**: Cho phép rẽ nhiều nhánh dựa trên giá trị của một biểu thức kiểu số nguyên. Dùng `break` để thoát khỏi `switch`, `default` cho trường hợp còn lại.

#### **b. Cấu trúc lặp**

*   **`for`**: Lặp lại một khối lệnh với số lần xác định trước. Cú pháp: `for (khởi_tạo; điều_kiện; cập_nhật)`.
*   **`while`**: Lặp lại một khối lệnh khi điều kiện lặp còn đúng. Điều kiện được kiểm tra *trước* mỗi lần lặp.
*   **`do-while`**: Tương tự `while` nhưng khối lệnh được thực thi ít nhất một lần *trước khi* kiểm tra điều kiện.
*   **Lệnh điều khiển lặp**: `break` để thoát khỏi vòng lặp, `continue` để bỏ qua lần lặp hiện tại.

#### **c. Ví dụ**
```cpp
#include <iostream>

int main() {
    // Ví dụ về switch-case
    int day = 4;
    switch (day) {
        case 6:
            std::cout << "Today is Saturday." << std::endl;
            break;
        case 7:
            std::cout << "Today is Sunday." << std::endl;
            break;
        default:
            std::cout << "Looking forward to the Weekend." << std::endl;
    }

    // Ví dụ về vòng lặp for tính tổng
    int sum = 0;
    for (int i = 1; i <= 10; ++i) {
        if (i == 5) {
            continue; // Bỏ qua số 5
        }
        sum += i;
        if (sum > 30) {
            break; // Dừng nếu tổng vượt quá 30
        }
    }
    std::cout << "Sum = " << sum << std::endl;

    return 0;
}
```

---

### **Câu 5: Hàm (Function)**

*   **Khái niệm**: Là một khối lệnh có tên, thực hiện một công việc cụ thể. Giúp **tái sử dụng mã nguồn**, làm chương trình có cấu trúc rõ ràng và dễ bảo trì.
*   **Cú pháp**: `kiểu_trả_về tên_hàm(danh_sách_tham_số) { ... return giá_trị; }`.
*   **Truyền tham số**:
    *   **Truyền tham trị (Pass by value)**: Mặc định. Hàm nhận một bản sao của đối số. Mọi thay đổi trên tham số không ảnh hưởng đến đối số gốc.
    *   **Truyền tham chiếu (Pass by reference)**: Dùng ký hiệu `&`. Hàm làm việc trực tiếp trên đối số gốc. Mọi thay đổi trên tham số sẽ thay đổi đối số gốc.
*   **Nguyên mẫu hàm (Prototype)**: Là việc khai báo hàm trước khi định nghĩa, cho phép gọi hàm ở bất kỳ đâu trong file mã nguồn.

#### **Ví dụ**
```cpp
#include <iostream>

// Nguyên mẫu hàm
void swap_by_value(int x, int y);
void swap_by_reference(int &x, int &y);

int main() {
    int a = 5, b = 10;

    std::cout << "Before swap: a = " << a << ", b = " << b << std::endl;
    swap_by_value(a, b); // Truyền tham trị
    std::cout << "After swap_by_value: a = " << a << ", b = " << b << std::endl; // a và b không đổi

    swap_by_reference(a, b); // Truyền tham chiếu
    std::cout << "After swap_by_reference: a = " << a << ", b = " << b << std::endl; // a và b đã hoán vị

    return 0;
}

// Định nghĩa hàm truyền tham trị (không thay đổi giá trị gốc)
void swap_by_value(int x, int y) {
    int temp = x;
    x = y;
    y = temp;
}

// Định nghĩa hàm truyền tham chiếu (thay đổi giá trị gốc)
void swap_by_reference(int &x, int &y) {
    int temp = x;
    x = y;
    y = temp;
}
```

---

### **Câu 6: Mảng (Array)**

*   **Khái niệm**: Là một tập hợp các phần tử **có cùng kiểu dữ liệu**, được lưu trữ trong các ô nhớ liên tiếp. Kích thước mảng phải được xác định khi khai báo và không thay đổi.
*   **Mảng một chiều**:
    *   **Khai báo**: `kiểu_dữ_liệu tên_mảng[số_phần_tử];`.
    *   **Truy xuất**: `tên_mảng[chỉ_số]`. Chỉ số bắt đầu từ **0**.
*   **Mảng hai chiều**:
    *   **Khai báo**: `kiểu_dữ_liệu tên_mảng[số_dòng][số_cột];`.
    *   **Truy xuất**: `tên_mảng[chỉ_số_dòng][chỉ_số_cột]`.
    *   **Các khái niệm**: Đường chéo chính (`i == j`), đường chéo phụ (`i + j == n - 1`).
*   **Truyền mảng cho hàm**: Khi truyền mảng vào hàm, thực chất là truyền địa chỉ của phần tử đầu tiên. Mọi thay đổi trên mảng trong hàm sẽ ảnh hưởng đến mảng gốc.

#### **Ví dụ**
```cpp
#include <iostream>

// Hàm nhận vào một mảng 1 chiều và in ra các phần tử
void print_array(int arr[], int size) {
    for (int i = 0; i < size; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    // Mảng một chiều
    int numbers[] = {10, 20, 30, 40, 50}; // Tự xác định kích thước
    numbers = 25; // Thay đổi phần tử thứ hai
    print_array(numbers, 5);

    // Mảng hai chiều (ma trận)
    int matrix = {
        {1, 2, 3},
        {4, 5, 6}
    };
    std::cout << "Element at is: " << matrix << std::endl; // In ra 6

    return 0;
}
```

---

### **Câu 7: Con trỏ (Pointer)**

*   **Khái niệm**: Con trỏ là một biến đặc biệt **lưu trữ địa chỉ bộ nhớ** của một biến khác.
*   **Các toán tử quan trọng**:
    *   **`&` (Address-of)**: Lấy địa chỉ của một biến.
    *   **`*` (Dereferencing)**: Truy cập giá trị tại địa chỉ mà con trỏ đang trỏ tới.
*   **Khai báo**: `kiểu_dữ_liệu *tên_con_trỏ;`.
*   **Con trỏ và Mảng**: Tên của một mảng chính là một **hằng con trỏ** trỏ đến phần tử đầu tiên của mảng đó (`arr` tương đương với `&arr`). Do đó, `arr[i]` tương đương với `*(arr + i)`.

#### **Ví dụ**
```cpp
#include <iostream>

int main() {
    int var = 20;
    int* ptr; // Khai báo một con trỏ kiểu int

    ptr = &var; // Gán địa chỉ của var cho con trỏ ptr

    std::cout << "Value of var: " << var << std::endl; // 20
    std::cout << "Address of var: " << &var << std::endl;
    
    std::cout << "Value of ptr (address it holds): " << ptr << std::endl;
    
    // Sử dụng toán tử * để truy cập giá trị tại địa chỉ ptr đang giữ
    std::cout << "Value pointed to by ptr: " << *ptr << std::endl; // 20

    // Thay đổi giá trị của var thông qua con trỏ
    *ptr = 50;
    std::cout << "New value of var: " << var << std::endl; // 50

    return 0;
}
```

---

### **Câu 8: Cấp phát động (Dynamic Memory Allocation)**

*   **Khái niệm**:
    *   **Cấp phát tĩnh**: Kích thước bộ nhớ được xác định tại thời điểm biên dịch, lưu trên vùng nhớ **Stack**.
    *   **Cấp phát động**: Bộ nhớ được cấp phát trong khi chương trình đang chạy, lưu trên vùng nhớ **Heap**. Kích thước linh hoạt.
*   **Toán tử `new` và `delete`**:
    *   **`new`**: Dùng để cấp phát bộ nhớ động. Ví dụ: `int *ptr = new int;`.
    *   **`new[]`**: Dùng để cấp phát mảng động. Ví dụ: `int *arr = new int;`.
    *   **`delete` và `delete[]`**: Dùng để giải phóng vùng nhớ tương ứng, tránh **rò rỉ bộ nhớ (memory leak)**.
*   **Lưu ý**: Sau khi `delete`, nên gán con trỏ bằng `NULL` hoặc `nullptr` để tránh "con trỏ lạc" (dangling pointer).

#### **Ví dụ**
```cpp
#include <iostream>

int main() {
    int n;
    std::cout << "Enter the size of the array: ";
    std::cin >> n;

    // Cấp phát động một mảng số nguyên
    int* arr = new int[n];

    // Kiểm tra cấp phát thành công
    if (arr == nullptr) {
        std::cout << "Error: memory could not be allocated";
        return 1;
    }

    // Sử dụng mảng
    for (int i = 0; i < n; ++i) {
        arr[i] = i * 10;
    }

    // In mảng
    for (int i = 0; i < n; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;

    // Giải phóng bộ nhớ đã cấp phát
    delete[] arr;
    arr = nullptr; // Gán bằng nullptr để đảm bảo an toàn

    return 0;
}
```

---

### **Câu 9: Đệ quy (Recursion)**

*   **Khái niệm**: Là kỹ thuật lập trình trong đó một hàm tự gọi lại chính nó để giải quyết một bài toán con nhỏ hơn.
*   **Cấu trúc hàm đệ quy**:
    1.  **Trường hợp cơ sở (Base case)**: Điều kiện dừng, là trường hợp đơn giản nhất mà hàm có thể trả về kết quả trực tiếp mà không cần gọi lại chính nó.
    2.  **Bước đệ quy (Recursive step)**: Hàm gọi lại chính nó với dữ liệu đầu vào được thu nhỏ lại, tiến gần hơn đến trường hợp cơ sở.
*   **Call Stack**: Mỗi lần gọi hàm sẽ tạo một "khung ngăn xếp" (stack frame). Gọi đệ quy quá sâu có thể gây ra lỗi **tràn bộ nhớ stack (stack overflow)**.
*   **So sánh với vòng lặp**: Đệ quy thường cho mã nguồn ngắn gọn, trực quan nhưng thường chậm hơn và tốn bộ nhớ hơn vòng lặp.

#### **Ví dụ: Tính giai thừa**
```cpp
#include <iostream>

// Hàm đệ quy tính giai thừa của n (n!)
long long factorial(int n) {
    // Điều kiện dừng (Base case)
    if (n == 0 || n == 1) {
        return 1;
    }
    // Bước đệ quy (Recursive step)
    else {
        return n * factorial(n - 1);
    }
}

int main() {
    int num = 5;
    std::cout << "Factorial of " << num << " is " << factorial(num) << std::endl; // Kết quả: 120
    return 0;
}
```

---

### **Câu 10: Kiểu cấu trúc (Struct)**

*   **Khái niệm**: Cho phép nhóm nhiều biến (có thể khác kiểu dữ liệu) lại với nhau thành một kiểu dữ liệu mới duy nhất để mô tả một đối tượng.
*   **Khai báo**: Dùng từ khóa `struct`. Có thể kết hợp với `typedef` để khai báo biến ngắn gọn hơn.
*   **Truy xuất thành phần**:
    *   Dùng **toán tử chấm (`.`)** với biến struct thông thường: `sv.maSV`.
    *   Dùng **toán tử mũi tên (`->`)** với biến con trỏ trỏ tới struct: `p_sv->maSV`.
*   **Mảng cấu trúc**: Có thể khai báo mảng mà mỗi phần tử là một biến struct.

#### **Ví dụ**
```cpp
#include <iostream>
#include <string>

// Khai báo cấu trúc SinhVien
struct SinhVien {
    std::string maSV;
    std::string hoTen;
    float diemTB;
};

void printStudent(SinhVien sv) {
    std::cout << "Ma SV: " << sv.maSV << std::endl;
    std::cout << "Ho ten: " << sv.hoTen << std::endl;
    std::cout << "Diem TB: " << sv.diemTB << std::endl;
}

int main() {
    // Khai báo và khởi tạo một biến cấu trúc
    SinhVien sv1 = {"21520001", "Nguyen Van A", 8.5};
    
    // Truy xuất và in thông tin
    printStudent(sv1);

    // Con trỏ tới struct
    SinhVien* ptr_sv = &sv1;
    ptr_sv->diemTB = 9.0; // Dùng toán tử -> để thay đổi dữ liệu qua con trỏ
    
    std::cout << "\nAfter update via pointer:" << std::endl;
    printStudent(sv1);

    return 0;
}
```

---

### **Câu 11: Chuỗi ký tự (C-style String)**

*   **Khái niệm**: Trong C/C++, chuỗi ký tự kiểu C là một **mảng các ký tự (`char`) kết thúc bằng ký tự null `\0`**.
*   **Khai báo và khởi tạo**: `char ten_chuoi[] = "Hello";`. Trình biên dịch sẽ tự động thêm `\0` vào cuối.
*   **Nhập xuất**: Có thể dùng `gets()` (không an toàn) để nhập và `puts()` để xuất.
*   **Thư viện `<string.h>` (hoặc `<cstring>`)**: Cung cấp nhiều hàm hữu ích để thao tác chuỗi:
    *   `strlen(chuoi)`: Tính độ dài chuỗi (không tính `\0`).
    *   `strcpy(dest, src)`: Sao chép chuỗi `src` vào `dest`.
    *   `strcat(dest, src)`: Nối chuỗi `src` vào cuối chuỗi `dest`.
    *   `strcmp(s1, s2)`: So sánh hai chuỗi. Trả về 0 nếu bằng nhau, <0 nếu s1<s2, >0 nếu s1>s2.

#### **Ví dụ**
```cpp
#include <iostream>
#include <cstring> // Thư viện cho các hàm chuỗi C

int main() {
    char greeting = "Hello";
    char name[] = " World";

    // Nối chuỗi
    strcat(greeting, name); // greeting bây giờ là "Hello World"
    
    // In chuỗi
    std::cout << greeting << std::endl;
    
    // Tính độ dài chuỗi
    std::cout << "Length: " << strlen(greeting) << std::endl; // 11

    // So sánh chuỗi
    if (strcmp(greeting, "Hello World") == 0) {
        std::cout << "The strings are equal." << std::endl;
    }

    return 0;
}
```

---

### **Câu 12: Con trỏ và Cấu trúc (Nâng cao)**

Chủ đề này kết hợp kiến thức từ con trỏ và struct, đặc biệt quan trọng trong việc tạo các cấu trúc dữ liệu động như danh sách liên kết.

*   **Con trỏ trong struct**: Một `struct` có thể chứa thành viên là con trỏ, cho phép nó trỏ đến các dữ liệu khác hoặc thậm chí là một `struct` cùng loại.
*   **Con trỏ đến struct**: Có thể khai báo một con trỏ để lưu địa chỉ của một biến `struct`. Dùng toán tử `->` để truy cập thành viên của `struct` thông qua con trỏ.
*   **Cấp phát động cho struct**: Dùng `new` để tạo một đối tượng `struct` trên vùng nhớ HEAP và dùng `delete` để giải phóng nó.

#### **Ví dụ: Danh sách liên kết đơn**

Đây là ví dụ điển hình nhất về ứng dụng của con trỏ và struct.
```cpp
#include <iostream>

// Định nghĩa một nút (node) trong danh sách liên kết
struct Node {
    int data;          // Dữ liệu của nút
    Node* pNext;       // Con trỏ trỏ đến nút tiếp theo
};

int main() {
    // Tạo một danh sách liên kết đơn giản: 10 -> 20
    
    // Cấp phát động cho nút đầu tiên (head)
    Node* head = new Node();
    head->data = 10;
    head->pNext = nullptr; // Ban đầu chưa trỏ đi đâu

    // Cấp phát động cho nút thứ hai
    Node* second = new Node();
    second->data = 20;
    second->pNext = nullptr;

    // Liên kết nút đầu tiên với nút thứ hai
    head->pNext = second;

    // Duyệt và in danh sách
    std::cout << "Linked list: ";
    Node* current = head;
    while (current != nullptr) {
        std::cout << current->data << " -> ";
        current = current->pNext;
    }
    std::cout << "nullptr" << std::endl;

    // Giải phóng bộ nhớ (quan trọng!)
    delete head;
    delete second;

    return 0;
}
```