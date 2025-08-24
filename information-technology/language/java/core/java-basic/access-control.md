# 🔐 Access Control – Kiểm soát quyền truy cập trong Java

Java cung cấp **4 mức kiểm soát truy cập (access modifiers)** để quy định phạm vi sử dụng của **class, method, field**:

- `public` - Truy cập từ mọi nơi
- `protected` - Truy cập trong package và subclass
- **default** (không ghi gì – còn gọi là **package-private**)
- `private` - Chỉ truy cập trong cùng class

---

## 🏪 Ví dụ hình ảnh minh họa

Tưởng tượng **Java Package** như một **siêu thị**:

- **Package** = Khu vực trong siêu thị (ví dụ: khu thực phẩm, khu quần áo)
- **Class** = Sản phẩm trong khu vực đó
- **Access Modifier** = Cửa ra vào hoặc khóa bảo mật

```
🏢 Siêu thị Java Mall
├── 🏪 Package A (Khu thực phẩm)
│   ├── 🔓 public: Ai cũng mua được
│   ├── 🔒 protected: Nhân viên + VIP
│   ├── 📦 default: Chỉ nhân viên khu này
│   └── 🔐 private: Chỉ chủ cửa hàng
└── 🏪 Package B (Khu quần áo)
    └── Không thể mua đồ từ khu thực phẩm (trừ public)
```

---

## 📦 Ví dụ code cụ thể

### Package 1: com.example.internals
```java
// File: InternalClass.java
package com.example.internals;

class InternalClass {  // default access
    public String publicField = "Everyone can see";
    protected String protectedField = "Package + Subclass";
    String defaultField = "Package only";        // default
    private String privateField = "Class only";
    
    public void publicMethod() {
        System.out.println("Public method - accessible everywhere");
    }
    
    protected void protectedMethod() {
        System.out.println("Protected method - package + inheritance");
    }
    
    void defaultMethod() {  // default access
        System.out.println("Default method - package only");
    }
    
    private void privateMethod() {
        System.out.println("Private method - this class only");
    }
}
```

### Package 2: com.example.api
```java
// File: APIClass.java  
package com.example.api;

import com.example.internals.InternalClass;

public class APIClass {
    public void someMethod() {
        // ❌ Compile Error - InternalClass có default access
        // InternalClass obj = new InternalClass(); 
        
        System.out.println("Cannot access InternalClass from different package");
    }
}
```

### Package 1: com.example.internals (Same package test)
```java
// File: TestClass.java
package com.example.internals;

public class TestClass {
    public void testAccess() {
        InternalClass obj = new InternalClass(); // ✅ OK - cùng package
        
        // Test truy cập các field
        System.out.println(obj.publicField);     // ✅ OK
        System.out.println(obj.protectedField);  // ✅ OK  
        System.out.println(obj.defaultField);    // ✅ OK
        // System.out.println(obj.privateField); // ❌ Error
        
        // Test truy cập các method
        obj.publicMethod();    // ✅ OK
        obj.protectedMethod(); // ✅ OK
        obj.defaultMethod();   // ✅ OK
        // obj.privateMethod(); // ❌ Error
    }
}
```

---

## 🧾 Bảng so sánh chi tiết

| Modifier | Cùng class | Cùng package | Subclass (khác package) | Class khác package |
|----------|------------|--------------|--------------------------|-------------------|
| `public` | ✅ | ✅ | ✅ | ✅ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `default` | ✅ | ✅ | ❌ | ❌ |
| `private` | ✅ | ❌ | ❌ | ❌ |

### Giải thích từng mức:

#### 🌍 `public` - Công khai toàn cầu
```java
public class PublicClass {
    public int publicVar = 10;
    public void publicMethod() { }
}
// Có thể truy cập từ BẤT KỲ ĐÂU
```

#### 🏠 `protected` - Gia đình + Hàng xóm
```java
protected class ProtectedClass {  // ❌ Lỗi - class không thể protected
    protected int protectedVar = 20;
    protected void protectedMethod() { }
}
// Truy cập được: cùng package + subclass
```

#### 📦 `default` - Hàng xóm cùng khu phố
```java
class DefaultClass {              // default access
    int defaultVar = 30;          // default access
    void defaultMethod() { }      // default access
}
// Chỉ truy cập được trong cùng package
```

#### 🔐 `private` - Riêng tư tuyệt đối
```java
public class PrivateExample {
    private int privateVar = 40;
    private void privateMethod() { }
    
    // Chỉ truy cập được trong chính class này
    public void accessPrivate() {
        System.out.println(privateVar);  // ✅ OK
        privateMethod();                 // ✅ OK
    }
}
```

---

## 🏗️ Ví dụ Inheritance với Protected

### Package: com.example.parent
```java
package com.example.parent;

public class ParentClass {
    public String publicField = "Public";
    protected String protectedField = "Protected";
    String defaultField = "Default";
    private String privateField = "Private";
    
    protected void protectedMethod() {
        System.out.println("Protected method in parent");
    }
}
```

### Package: com.example.child
```java
package com.example.child;

import com.example.parent.ParentClass;

public class ChildClass extends ParentClass {
    public void testInheritance() {
        // ✅ Có thể truy cập
        System.out.println(publicField);     // ✅ public
        System.out.println(protectedField);  // ✅ protected (inheritance)
        
        // ❌ Không thể truy cập  
        // System.out.println(defaultField);   // ❌ default (khác package)
        // System.out.println(privateField);   // ❌ private
        
        protectedMethod(); // ✅ OK - inherited protected method
    }
}
```

---

## 🧠 Lưu ý đặc biệt

### 1. Quy tắc cho Top-level Class
Class cấp cao nhất (top-level class) chỉ có thể là:
- `public` - có thể import từ package khác
- `default` - chỉ dùng trong nội bộ package

```java
// ✅ Hợp lệ
public class PublicTopClass { }

// ✅ Hợp lệ  
class DefaultTopClass { }

// ❌ KHÔNG hợp lệ
private class PrivateTopClass { }   // Compile error
protected class ProtectedTopClass { } // Compile error
```

### 2. Inner Class có thể có mọi access modifier
```java
public class OuterClass {
    public class PublicInner { }
    protected class ProtectedInner { }
    class DefaultInner { }
    private class PrivateInner { }  // ✅ OK cho inner class
}
```

### 3. Interface members mặc định là public
```java
interface MyInterface {
    int CONSTANT = 100;           // implicitly public static final
    void method();                // implicitly public abstract
    
    // Tương đương với:
    // public static final int CONSTANT = 100;
    // public abstract void method();
}
```

---

## 📋 Ví dụ thực tế: Banking System

```java
// File: BankAccount.java
package com.bank.account;

public class BankAccount {
    private String accountNumber;      // Chỉ class này modify
    private double balance;            // Bảo mật số dư
    protected String customerName;     // Subclass có thể access
    String bankCode;                   // Package-private
    public String accountType;         // Public info
    
    public BankAccount(String accountNumber, String customerName) {
        this.accountNumber = accountNumber;
        this.customerName = customerName;
        this.balance = 0.0;
    }
    
    // Public methods - API cho client
    public double getBalance() {
        return balance;
    }
    
    public boolean withdraw(double amount) {
        if (isValidWithdrawal(amount)) {
            balance -= amount;
            return true;
        }
        return false;
    }
    
    // Private method - logic nội bộ
    private boolean isValidWithdrawal(double amount) {
        return amount > 0 && amount <= balance;
    }
    
    // Protected method - subclass có thể override
    protected void logTransaction(String type, double amount) {
        System.out.println(type + ": $" + amount);
    }
    
    // Package-private - chỉ banking package
    void internalAudit() {
        System.out.println("Internal audit for: " + accountNumber);
    }
}
```

```java
// File: SavingsAccount.java  
package com.bank.account;

public class SavingsAccount extends BankAccount {
    private double interestRate;
    
    public SavingsAccount(String accountNumber, String customerName) {
        super(accountNumber, customerName);
        this.interestRate = 0.05;
    }
    
    public void calculateInterest() {
        double interest = getBalance() * interestRate;
        // balance += interest;  // ❌ Cannot access private field
        
        // ✅ Có thể access protected members
        logTransaction("Interest", interest);
        System.out.println("Customer: " + customerName);
    }
}
```

---

## 🎯 Best Practices

### 1. Principle of Least Privilege
```java
// ✅ Tốt - chỉ expose những gì cần thiết
public class GoodClass {
    private String sensitiveData;           // Private by default
    
    public String getSensitiveData() {      // Controlled access
        return sensitiveData;
    }
}

// ❌ Không tốt - expose không cần thiết
public class BadClass {
    public String sensitiveData;            // Anyone can modify
}
```

### 2. Encapsulation Pattern
```java
public class User {
    private String email;                   // Private data
    
    public String getEmail() {              // Public getter
        return email;
    }
    
    public void setEmail(String email) {    // Public setter with validation
        if (isValidEmail(email)) {
            this.email = email;
        }
    }
    
    private boolean isValidEmail(String email) {  // Private helper
        return email != null && email.contains("@");
    }
}
```

### 3. API Design
```java
// ✅ Tốt - Clear public API
public class Calculator {
    public int add(int a, int b) {          // Public API
        return performCalculation(a, b, "+");
    }
    
    private int performCalculation(int a, int b, String op) {  // Implementation detail
        // Complex logic here
        return a + b;  // Simplified
    }
}
```

---

## 📊 Tóm tắt Access Control

| Mức độ | Phạm vi | Sử dụng khi |
|--------|---------|-------------|
| `private` | Chỉ trong class | Dữ liệu nhạy cảm, implementation details |
| `default` | Trong package | Internal API, helper classes |
| `protected` | Package + inheritance | Designed for inheritance |
| `public` | Everywhere | Public API, main interfaces |

---

## ✅ Kết luận

**Access Control** là cách Java:
- 🔒 **Bảo mật** code khỏi truy cập ngoài ý muốn
- 📦 **Tổ chức** code theo modules (packages)
- 🛡️ **Đóng gói** (encapsulation) dữ liệu và logic
- 🎯 **Thiết kế** API rõ ràng cho người dùng

**Nguyên tắc vàng**: Luôn sử dụng **access modifier hạn chế nhất** có thể, sau đó mở rộng khi cần thiết.