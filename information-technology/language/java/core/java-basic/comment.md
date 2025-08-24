# Comment trong Java

Comment là những dòng chú thích trong code mà **Java Compiler sẽ bỏ qua**.  
Chúng **không ảnh hưởng** tới chương trình, nhưng giúp **con người đọc hiểu code dễ hơn**.

---

## 🎯 Comment dùng để làm gì?

- **Giải thích logic**: Mô tả đoạn code đang làm gì
- **Ghi chú lý do**: Tại sao lại code như vậy thay vì cách khác
- **Đánh dấu đặc biệt**: Sử dụng các tag như `TODO`, `FIXME`, `NOTE`
- **Viết tài liệu API**: Dùng Javadoc để tạo documentation
- **Tạm thời tắt code**: Disable một phần code mà không xóa

---

## 🔹 Các loại comment trong Java

### 1. Single-line comment (`//`)

Dùng `//` để viết ghi chú **một dòng**.

```java
// Đây là single line comment
int age = 22; // Tuổi của người dùng

// TODO: Cần validate input
// FIXME: Bug khi age < 0
int score = calculateScore(age);
```

**Đặc điểm:**
- Chỉ áp dụng cho 1 dòng
- Mọi thứ sau `//` đều bị ignore
- Thường dùng cho ghi chú ngắn gọn

### 2. Multi-line comment (`/* */`)

Dùng `/* ... */` để viết comment **nhiều dòng**.

```java
/*
Đây là multi-line comment
Có thể viết nhiều dòng
Để giải thích logic phức tạp
*/
int weight = 50;

/* 
Thuật toán tính điểm:
- Lấy điểm cơ bản = 100
- Trừ đi số lỗi * 5
- Cộng thêm bonus nếu có
*/
int finalScore = baseScore - (errors * 5) + bonus;
```

**Đặc điểm:**
- Có thể spanning nhiều dòng
- Bắt đầu bằng `/*` và kết thúc bằng `*/`
- Thường dùng cho explanation dài

### 3. Javadoc comment (`/** */`)

Dùng `/** ... */` để viết **tài liệu chính thức** cho class, method, field.

```java
/**
 * Lớp Calculator để thực hiện các phép tính cơ bản.
 * 
 * @author Tên tác giả
 * @version 1.0
 * @since 2024
 */
public class Calculator {
    
    /**
     * Chiều cao của đối tượng tính bằng cm.
     */
    private int height = 170;
    
    /**
     * Cộng hai số nguyên.
     * 
     * @param a Số thứ nhất (phải >= 0)
     * @param b Số thứ hai (phải >= 0)
     * @return Tổng của a và b
     * @throws IllegalArgumentException nếu tham số < 0
     */
    public int add(int a, int b) {
        if (a < 0 || b < 0) {
            throw new IllegalArgumentException("Tham số phải >= 0");
        }
        return a + b;
    }
}
```

**Các tag Javadoc thường dùng:**

| Tag | Mô tả | Ví dụ |
|-----|-------|-------|
| `@param` | Mô tả tham số | `@param name Tên người dùng` |
| `@return` | Mô tả giá trị trả về | `@return Tổng của hai số` |
| `@throws` | Mô tả exception | `@throws IOException Lỗi đọc file` |
| `@author` | Tác giả | `@author John Doe` |
| `@version` | Phiên bản | `@version 1.2.3` |
| `@since` | Từ phiên bản nào | `@since JDK 8` |
| `@see` | Tham khảo thêm | `@see Calculator#subtract(int, int)` |

---

## 📌 Best Practices

### ✅ Nên làm

| Loại comment | Khi nào dùng | Ví dụ |
|--------------|---------------|-------|
| `//` | Ghi chú ngắn, rõ ràng | `// Khởi tạo connection` |
| `/* */` | Giải thích logic phức tạp | `/* Thuật toán sắp xếp bubble sort */` |
| `/** */` | Documentation cho API public | `/** Tính diện tích hình chữ nhật */` |

### ❌ Tránh làm

```java
// ❌ Comment hiển nhiên (redundant)
int x = 5; // Gán x bằng 5

// ❌ Comment dài thay vì refactor code
/* 
Hàm này rất phức tạp làm rất nhiều thứ bla bla bla...
40 dòng comment để giải thích 1 hàm
*/
public void complexFunction() { /* 100 dòng code */ }

// ❌ Comment sai lệch với code
// Tính tổng hai số
public int subtract(int a, int b) { // Code thực tế là trừ!
    return a - b;
}
```

### ✅ Cách viết comment tốt

```java
public class BankAccount {
    
    /**
     * Rút tiền từ tài khoản.
     * 
     * @param amount Số tiền cần rút (phải > 0)
     * @return true nếu rút thành công, false nếu không đủ tiền
     */
    public boolean withdraw(double amount) {
        // Kiểm tra số tiền hợp lệ
        if (amount <= 0) {
            return false;
        }
        
        // Kiểm tra số dư đủ không (bao gồm phí)
        double totalDeduction = amount + WITHDRAWAL_FEE;
        if (balance < totalDeduction) {
            return false; // Không đủ tiền
        }
        
        // Thực hiện rút tiền
        balance -= totalDeduction;
        
        // TODO: Ghi log transaction
        // FIXME: Cần thêm validation cho daily limit
        
        return true;
    }
}
```

---

## 🛠️ Generate Documentation từ Javadoc

Để tạo HTML documentation từ Javadoc comments:

```bash
# Tạo doc cho tất cả file .java trong thư mục hiện tại
javadoc *.java

# Tạo doc với package cụ thể
javadoc -d docs com.example.mypackage

# Tạo doc với title và author
javadoc -doctitle "My API Documentation" -author *.java
```

---

## 📋 Ví dụ hoàn chỉnh

```java
/**
 * Ứng dụng Calculator đơn giản để demo các loại comment.
 * 
 * @author Developer
 * @version 1.0
 */
public class CommentExample {
    
    // Hằng số PI dùng cho tính toán hình tròn
    private static final double PI = 3.14159;
    
    /**
     * Method chính để chạy chương trình.
     * 
     * @param args Tham số dòng lệnh (không sử dụng)
     */
    public static void main(String[] args) {
        // Khởi tạo calculator
        CommentExample calc = new CommentExample();
        
        /* 
         * Test các phép tính cơ bản
         * và in kết quả ra console
         */
        int result1 = calc.add(5, 3);
        int result2 = calc.multiply(4, 6);
        
        System.out.println("5 + 3 = " + result1); // Output: 8
        System.out.println("4 * 6 = " + result2); // Output: 24
        
        // TODO: Thêm phép chia và validation
    }
    
    /**
     * Cộng hai số nguyên.
     * 
     * @param a Số thứ nhất
     * @param b Số thứ hai  
     * @return Tổng của a và b
     */
    public int add(int a, int b) {
        return a + b; // Phép cộng đơn giản
    }
    
    /**
     * Nhân hai số nguyên.
     * 
     * @param a Số thứ nhất
     * @param b Số thứ hai
     * @return Tích của a và b
     */
    public int multiply(int a, int b) {
        return a * b; // Phép nhân đơn giản
    }
}
```

---

## ✅ Tóm tắt

- **Comment không chạy** nhưng giúp code dễ hiểu và bảo trì
- **3 loại chính**: `//` (1 dòng), `/* */` (nhiều dòng), `/** */` (Javadoc)
- **Viết comment đúng lúc, đúng chỗ** - không quá nhiều, không quá ít
- **Javadoc** giúp tạo documentation chuyên nghiệp
- **Luôn sync comment với code** - đừng để comment outdated