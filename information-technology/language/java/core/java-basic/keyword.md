# 🔑 Keywords trong Java

Trong Java, **keyword** là những từ được ngôn ngữ đặt trước, có nghĩa đặc biệt, dùng để xây dựng cấu trúc của chương trình.

👉 Bạn **không thể** dùng keyword để đặt tên biến, method, hay class.

---

## 📋 Danh sách đầy đủ 50 Keywords trong Java

Java có **50 keywords** được chia thành các nhóm chức năng:

### 🏗️ Nhóm Access Modifiers
| Keyword | Ý nghĩa |
|---------|---------|
| `public` | Truy cập từ bất kỳ đâu |
| `private` | Chỉ truy cập trong cùng class |
| `protected` | Truy cập trong package và subclass |
| *default* | Truy cập trong cùng package (không có keyword, để trống) |

### 🎯 Nhóm Class & Object
| Keyword | Ý nghĩa |
|---------|---------|
| `class` | Khai báo một class |
| `interface` | Khai báo một interface |
| `extends` | Kế thừa từ class khác |
| `implements` | Triển khai interface |
| `new` | Tạo object mới từ class |
| `this` | Tham chiếu đến object hiện tại |
| `super` | Tham chiếu đến class cha |
| `static` | Thành viên thuộc class, không phụ thuộc object |
| `final` | Không thể thay đổi/kế thừa |
| `abstract` | Class/method trừu tượng |

### 🔧 Nhóm Data Types
| Keyword | Ý nghĩa |
|---------|---------|
| `byte` | Kiểu số nguyên 8-bit |
| `short` | Kiểu số nguyên 16-bit |
| `int` | Kiểu số nguyên 32-bit |
| `long` | Kiểu số nguyên 64-bit |
| `float` | Kiểu số thực 32-bit |
| `double` | Kiểu số thực 64-bit |
| `char` | Kiểu ký tự Unicode 16-bit |
| `boolean` | Kiểu logic (true/false) |
| `void` | Phương thức không trả về gì |

### 🎛️ Nhóm Control Flow
| Keyword | Ý nghĩa |
|---------|---------|
| `if` | Câu lệnh điều kiện |
| `else` | Phần else của if |
| `switch` | Câu lệnh switch-case |
| `case` | Từng trường hợp trong switch |
| `default` | Trường hợp mặc định trong switch |
| `for` | Vòng lặp for |
| `while` | Vòng lặp while |
| `do` | Vòng lặp do-while |
| `break` | Thoát khỏi vòng lặp/switch |
| `continue` | Bỏ qua iteration hiện tại |
| `return` | Trả giá trị từ method |

### ⚠️ Nhóm Exception Handling
| Keyword | Ý nghĩa |
|---------|---------|
| `try` | Khối code có thể gây exception |
| `catch` | Bắt và xử lý exception |
| `finally` | Code luôn chạy dù có exception hay không |
| `throw` | Ném một exception |
| `throws` | Khai báo exception method có thể ném |

### 📦 Nhóm Package & Import
| Keyword | Ý nghĩa |
|---------|---------|
| `package` | Khai báo package |
| `import` | Import package hoặc class khác |

### 🔄 Nhóm Multithreading
| Keyword | Ý nghĩa |
|---------|---------|
| `synchronized` | Đồng bộ hóa thread |
| `volatile` | Biến được chia sẻ giữa các thread |

### 📌 Nhóm Literals & Values
| Keyword | Ý nghĩa |
|---------|---------|
| `true` | Giá trị boolean đúng |
| `false` | Giá trị boolean sai |
| `null` | Giá trị rỗng cho reference type |

### 🚫 Nhóm Reserved (không dùng)
| Keyword | Trạng thái |
|---------|------------|
| `const` | Reserved (không sử dụng) |
| `goto` | Reserved (không sử dụng) |

### 🔍 Nhóm Other
| Keyword | Ý nghĩa |
|---------|---------|
| `instanceof` | Kiểm tra kiểu object |
| `native` | Method được implement bằng ngôn ngữ khác |
| `strictfp` | Floating-point tính toán chính xác |
| `transient` | Field không được serialize |
| `assert` | Kiểm tra điều kiện debug |

---

## 🧪 Lưu ý quan trọng

### 1. Phân biệt chữ hoa/thường
Keywords trong Java **phân biệt chữ hoa/thường** (case-sensitive):

```java
// ✅ Đúng - keyword hợp lệ
public class MyClass { }

// ❌ Sai - không phải keyword, nhưng có thể dùng làm tên (không khuyến khích)
public class Public { } // "Public" khác với "public"
```

### 2. Không được dùng làm identifier
```java
// ❌ Lỗi compile - không thể dùng keyword làm tên
int public = 5;        // Error: "public" là keyword  
String class = "test"; // Error: "class" là keyword
void if() { }          // Error: "if" là keyword

// ✅ Đúng - có thể dùng tên tương tự
int Public = 5;        // OK
String myClass = "test"; // OK  
void ifStatement() { } // OK
```

### 3. Reserved keywords
```java
// ❌ Không nên dùng (mặc dù compile được)
int const = 10;  // "const" là reserved keyword
int goto = 20;   // "goto" là reserved keyword
```

---

## 🧾 Ví dụ minh họa

```java
// Ví dụ sử dụng nhiều keywords
public class KeywordExample {
    
    // Keywords: public, private, static, final, int
    private static final int MAX_SIZE = 100;
    
    // Keywords: public, static, void, String
    public static void main(String[] args) {
        
        // Keywords: int, new, if, else
        int number = new Integer(50);
        
        if (number > 0) {
            System.out.println("Positive");
        } else {
            System.out.println("Negative or Zero");  
        }
        
        // Keywords: try, catch, finally
        try {
            int result = divide(10, 0);
        } catch (ArithmeticException e) {
            System.out.println("Division by zero!");
        } finally {
            System.out.println("Cleanup code");
        }
    }
    
    // Keywords: private, static, int, throws, if, throw, return
    private static int divide(int a, int b) throws ArithmeticException {
        if (b == 0) {
            throw new ArithmeticException("Cannot divide by zero");
        }
        return a / b;
    }
}
```

**Keywords được sử dụng trong ví dụ:**
`public`, `class`, `private`, `static`, `final`, `int`, `void`, `String`, `new`, `if`, `else`, `try`, `catch`, `finally`, `throws`, `throw`, `return`

---

## 📊 Thống kê Keywords theo nhóm

| Nhóm | Số lượng | Ví dụ |
|------|----------|-------|
| **Data Types** | 8 | `int`, `double`, `boolean`, `void` |
| **Access Modifiers** | 4 | `public`, `private`, `protected`, default |
| **Control Flow** | 11 | `if`, `for`, `while`, `switch` |
| **Class & Object** | 10 | `class`, `extends`, `new`, `this` |
| **Exception Handling** | 5 | `try`, `catch`, `throw`, `throws`, `finally` |
| **Others** | 13 | `import`, `package`, `synchronized`, `volatile` |

---

## ✅ Best Practices

### 1. Naming Convention
```java
// ✅ Tốt - tránh tên gần giống keyword
public class UserAccount { }     // thay vì "Class"
private int userCount;           // thay vì "count" 
public void getUserInfo() { }    // thay vì "getInfo"

// ❌ Không tốt - dễ nhầm lẫn
public class Public { }          // hợp lệ nhưng confusing
private int Int;                 // hợp lệ nhưng confusing
```

### 2. Code Readability  
```java
// ✅ Tốt - dùng keyword đúng cách
public final class Constants {
    public static final int MAX_USERS = 1000;
    private static final String DEFAULT_NAME = "Guest";
}

// ❌ Không tốt - lạm dụng keyword
public static final public class public { } // Redundant và sai
```

---

## 🔍 Kiểm tra Keyword

Để kiểm tra một từ có phải keyword không:

```java
// Method utility để check keyword (ví dụ minh họa)
public static boolean isKeyword(String word) {
    String[] keywords = {
        "abstract", "assert", "boolean", "break", "byte", "case", 
        "catch", "char", "class", "const", "continue", "default",
        "do", "double", "else", "enum", "extends", "final",
        "finally", "float", "for", "goto", "if", "implements",
        "import", "instanceof", "int", "interface", "long",
        "native", "new", "package", "private", "protected",
        "public", "return", "short", "static", "strictfp",
        "super", "switch", "synchronized", "this", "throw",
        "throws", "transient", "try", "void", "volatile", "while"
    };
    
    for (String keyword : keywords) {
        if (keyword.equals(word)) {
            return true;
        }
    }
    return false;
}
```

---

## ✅ Tóm tắt

- Java có **50 keywords** cố định, không thể thay đổi
- Keywords **phân biệt chữ hoa/thường** (case-sensitive)
- **Không được** dùng keywords làm tên biến, method, class
- Keywords tạo nên **cấu trúc cơ bản** của ngôn ngữ Java
- Nên **tránh đặt tên gần giống** keywords để code dễ đọc