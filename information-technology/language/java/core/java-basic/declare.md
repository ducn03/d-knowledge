# 🧱 Khai báo Class, Field, và Method trong Java

---

## 1. Khai báo Class (Declaring Classes)

Một **class** trong Java là bản thiết kế (blueprint) để tạo ra **object**, bao gồm:
- **Dữ liệu** (field/attribute)
- **Hành vi** (method)

### 📌 Cú pháp
```java
[accessModifier] class ClassName [extends SuperClass] [implements Interface1, Interface2, ...] {
    // class body
}
```

### 📘 Ví dụ
```java
public class MyClass extends MySuperClass implements MyInterface {
    private int myField;

    public MyClass() {
        // constructor
    }

    public void myMethod() {
        // method logic
    }
}
```

### 🏷️ Quy tắc đặt tên class
- Không chứa dấu cách
- Không bắt đầu bằng số
- Chỉ dùng: chữ cái (A–Z, a–z), số (0–9), _, $
- Không được trùng keyword Java (int, for, class, new…)
- Phân biệt chữ hoa/thường (MyClass ≠ myclass)
- **Best practice**: CamelCase, chữ cái đầu viết hoa → `CustomerService`, `UserProfile`

### 🧬 Kế thừa và Interface
- **Kế thừa**: Java chỉ cho extends 1 class duy nhất
```java
class B extends A { ... }
```

- **Interface**: có thể implements nhiều interface
```java
class C implements Interface1, Interface2 { ... }
```

### 🧱 Thành phần trong class
| Thành phần | Mục đích |
|------------|----------|
| Field | Lưu trữ dữ liệu |
| Constructor | Khởi tạo object |
| Method | Định nghĩa hành vi |
| Nested class | Class lồng bên trong |

---

## 2. Khai báo Field (Declaring Fields)

### 🧾 Field là gì?
- Field (biến thành viên, attribute, instance variable) là biến được khai báo ở cấp class, không nằm trong method
- Dùng để lưu trạng thái của object
- Ví dụ: Mỗi Person có `name`, `age`, `isActive` → chính là field

### 🔧 Cú pháp
```java
[accessModifier] [specifiers] type fieldName [= initialValue];
```

### 📘 Ví dụ
```java
public class MyClass {
    public static final int MAX_VALUE = 100;   // constant
    private String name;                       // instance field
    protected double salary;                   // instance field
    boolean active = true;                     // default (package-private)
}
```

### 1️⃣ Access Modifier
Field có thể dùng đủ cả 4 loại: `public`, `protected`, `(default)`, `private`

### 2️⃣ Specifiers
| Từ khóa | Ý nghĩa |
|---------|---------|
| `static` | Thuộc class, dùng chung |
| `final` | Không thể gán lại (constant) |
| `static final` | Hằng số toàn cục |
| `transient` | Không ghi khi serialize object |
| `volatile` | Đảm bảo đọc/ghi nhất quán trong đa luồng |

**Ví dụ hằng số:**
```java
public static final String COMPANY_NAME = "CodeCopilot Inc.";
```

### 3️⃣ Quy tắc đặt tên field
- Không bắt đầu bằng số
- Không trùng keyword
- Dùng chữ cái, _, $
- Phân biệt hoa/thường
- Không chứa ký tự đặc biệt

👉 **Best practice**: 
- Dùng camelCase
- Chữ cái đầu viết thường → `customerName`, `isActive`

### 4️⃣ Giá trị khởi tạo
Có thể hoặc không gán khi khai báo:
```java
private boolean isActive = true; // khởi tạo
private int count;               // mặc định = 0
private String name;             // mặc định = null
```

⚠️ **Với static final** → phải gán giá trị khi khai báo:
```java
public static final double PI = 3.14159; // ✅
```

---

## 3. Khai báo Method (Declaring Methods)

### 📌 Method là gì?
- Một khối lệnh (block) thực hiện hành động hoặc trả về giá trị
- Giúp: tái sử dụng code, tổ chức logic rõ ràng, dễ kiểm thử

### 🧾 Cú pháp
```java
[accessModifier] [specifiers] returnType methodName([parameters]) [throws Exception1, Exception2] {
    // method body
}
```

### 🧪 Ví dụ
```java
public static String addParenthesis(String s) {
    return "(" + s + ")";
}

private int sum(int a, int b) {
    return a + b;
}

protected void setName(String name) throws IllegalArgumentException {
    if (name == null || name.isEmpty()) {
        throw new IllegalArgumentException("Name cannot be null or empty");
    }
    this.name = name;
}
```

### 📖 Thành phần chi tiết

#### 1️⃣ Access Modifier
| Modifier | Ý nghĩa |
|----------|---------|
| `public` | Gọi được ở bất kỳ đâu |
| `private` | Chỉ trong cùng class |
| `protected` | Cùng package + subclass |
| `(default)` | Chỉ trong cùng package |

#### 2️⃣ Specifiers
| Specifier | Ý nghĩa |
|-----------|---------|
| `static` | Gọi trực tiếp từ class, không cần object |
| `final` | Không thể override |
| `abstract` | Không có thân, phải override ở subclass |
| `synchronized` | Chỉ 1 thread chạy method tại 1 thời điểm |

#### 3️⃣ Return type
Kiểu dữ liệu trả về (hoặc `void` nếu không trả gì).

#### 4️⃣ Method name
camelCase, rõ nghĩa → `calculateSalary`, `printInfo`, `isLoggedIn`

#### 5️⃣ Parameters
```java
public void greet(String name)
public void add(int a, int b)
public void log(final String message) // final → không đổi giá trị
```

#### 6️⃣ throws clause
```java
public void setName(String name) throws IllegalArgumentException
```

#### 7️⃣ Method body
Chứa logic, câu lệnh, vòng lặp, điều kiện, return,...

### 📘 Ví dụ thêm
```java
// Không có tham số
public void printHello() {
    System.out.println("Hello");
}

// Có nhiều tham số
public void printPerson(String name, int age, boolean isStudent) {
    System.out.println("Name: " + name);
    System.out.println("Age: " + age);
    System.out.println("Student? " + isStudent);
}
```

---

## ✅ Tóm tắt

- **Class**: blueprint → chứa field, constructor, method
- **Field**: biến thành viên của class → lưu trạng thái object
- **Method**: hành vi → thực hiện logic, có thể trả giá trị

👉 **Nắm vững class – field – method là nền tảng để hiểu OOP trong Java.**