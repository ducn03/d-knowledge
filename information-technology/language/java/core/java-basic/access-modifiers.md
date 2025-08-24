# 🔐 Access Modifiers trong Java

Access modifiers quy định phạm vi sử dụng của:

- **class**
- **field (biến)**  
- **method**
- **constructor**

👉 **Mục đích**: Bảo vệ dữ liệu, giấu logic bên trong, và chỉ cho phép truy cập hợp lý (theo **Encapsulation**).

---

## 📘 4 mức truy cập trong Java

```
┌──────────────────────────────────────────────┐
│                  public                      │
│ ┌──────────────────────────────────────┐     │
│ │            protected                 │     │
│ │ ┌──────────────────────────────┐     │     │
│ │ │   default (package-private)  │     │     │
│ │ │ ┌───────────────────────┐    │     │     │
│ │ │ │       private         │    │     │     │
│ │ │ └───────────────────────┘    │     │     │
│ │ └──────────────────────────────┘     │     │
│ └──────────────────────────────────────┘     │
└──────────────────────────────────────────────┘
```

**Thứ tự từ hạn chế nhất đến mở nhất:**
- **`private`** → Chỉ trong cùng class
- **`default`** → Trong cùng package  
- **`protected`** → Trong package + subclass ở package khác
- **`public`** → Mọi nơi

---

## 🧱 Chi tiết từng modifier

### 🔹 `private` - Riêng tư tuyệt đối

- Chỉ dùng được bên trong **chính class đó**
- Class kế thừa cũng **không** truy cập được
- Thường dùng cho: dữ liệu nhạy cảm, implementation details

```java
class BankAccount {
    private double balance;        // Chỉ dùng trong class này
    private String accountNumber;  // Bảo mật thông tin
    
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;     // ✅ Truy cập được private field
        }
    }
    
    public double getBalance() {
        return balance;            // ✅ Truy cập được private field
    }
    
    private boolean isValidAmount(double amount) {  // Private method
        return amount > 0 && amount < 1000000;
    }
}

class TestBank {
    public void test() {
        BankAccount account = new BankAccount();
        // account.balance = 1000;     // ❌ Error: private field
        // account.accountNumber = ""; // ❌ Error: private field
        account.deposit(500);          // ✅ OK: public method
    }
}
```

### 🔹 `default` (package-private) - Hàng xóm cùng khu

- Khi **không ghi gì** thì Java coi là package-private
- Chỉ class trong **cùng package** mới truy cập được
- Thường dùng cho: utility classes, internal APIs

```java
// File: Student.java - package com.school
package com.school;

class Student {                    // default class
    int age;                       // default field
    String name;                   // default field
    
    void study() {                 // default method
        System.out.println(name + " is studying");
    }
}

class Teacher {                    // Cùng package com.school
    public void checkStudent() {
        Student student = new Student();  // ✅ OK: cùng package
        student.age = 18;                 // ✅ OK: cùng package
        student.study();                  // ✅ OK: cùng package
    }
}
```

```java
// File: Principal.java - package com.management
package com.management;

import com.school.Student;

class Principal {
    public void checkStudent() {
        // Student student = new Student();  // ❌ Error: khác package
    }
}
```

### 🔹 `protected` - Gia đình + Hàng xóm

Truy cập được từ:
- Class **cùng package**
- Class **con (subclass)**, kể cả ở package khác

```java
// File: Animal.java - package animals
package animals;

public class Animal {
    protected String name;               // Protected field
    protected int age;
    
    protected void eat() {               // Protected method
        System.out.println(name + " is eating");
    }
    
    protected void sleep() {
        System.out.println(name + " is sleeping");
    }
}

class Cat extends Animal {               // Cùng package animals
    public void meow() {
        name = "Kitty";                  // ✅ OK: cùng package
        eat();                           // ✅ OK: cùng package
    }
}
```

```java
// File: Dog.java - package pets (khác package)
package pets;

import animals.Animal;

public class Dog extends Animal {        // Subclass khác package
    public void bark() {
        name = "Buddy";                  // ✅ OK: subclass access
        age = 3;                         // ✅ OK: subclass access
        eat();                           // ✅ OK: subclass access
    }
    
    public void playWith(Animal other) {
        // other.name = "Friend";        // ❌ Error: không phải this object
        // Chỉ truy cập protected qua 'this', không qua object khác
    }
}

class PetShop {                          // Không phải subclass
    public void test() {
        Dog dog = new Dog();
        // dog.name = "Rex";             // ❌ Error: không phải subclass
    }
}
```

### 🔹 `public` - Công khai toàn cầu

- Có thể truy cập từ **mọi nơi**, bất kể package nào
- Thường dùng cho: API công khai, main methods

```java
// File: Calculator.java - package com.utils
package com.utils;

public class Calculator {
    public static final double PI = 3.14159;  // Public constant
    
    public int add(int a, int b) {            // Public method
        return a + b;
    }
    
    public double calculateArea(double radius) {
        return PI * radius * radius;
    }
}
```

```java
// File: App.java - package com.app (khác package)
package com.app;

import com.utils.Calculator;

public class App {
    public static void main(String[] args) {
        Calculator calc = new Calculator();    // ✅ OK: public class
        int result = calc.add(5, 3);          // ✅ OK: public method
        double area = calc.calculateArea(2.5); // ✅ OK: public method
        System.out.println(Calculator.PI);     // ✅ OK: public field
    }
}
```

---

## 📊 Bảng so sánh Access Modifiers

| Modifier | Same Class | Same Package | Subclass (khác package) | Anywhere |
|----------|------------|--------------|-------------------------|----------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| `default` | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

### Ví dụ minh họa bảng

```java
// File: AccessDemo.java - package demo
package demo;

public class AccessDemo {
    public int publicVar = 1;      // Mọi nơi
    protected int protectedVar = 2; // Package + subclass
    int defaultVar = 3;            // Chỉ package
    private int privateVar = 4;     // Chỉ class này
    
    public void testSameClass() {
        // ✅ Tất cả đều OK trong cùng class
        System.out.println(publicVar);    // ✅
        System.out.println(protectedVar); // ✅
        System.out.println(defaultVar);   // ✅
        System.out.println(privateVar);   // ✅
    }
}

class SamePackage {                // Cùng package demo
    public void test() {
        AccessDemo demo = new AccessDemo();
        System.out.println(demo.publicVar);    // ✅ public
        System.out.println(demo.protectedVar); // ✅ protected
        System.out.println(demo.defaultVar);   // ✅ default
        // System.out.println(demo.privateVar); // ❌ private
    }
}
```

```java
// File: DifferentPackage.java - package other
package other;

import demo.AccessDemo;

public class DifferentPackage extends AccessDemo {  // Subclass
    public void test() {
        System.out.println(publicVar);    // ✅ public
        System.out.println(protectedVar); // ✅ protected (inheritance)
        // System.out.println(defaultVar);   // ❌ default
        // System.out.println(privateVar);   // ❌ private
    }
}

class NonSubclass {                      // Không phải subclass
    public void test() {
        AccessDemo demo = new AccessDemo();
        System.out.println(demo.publicVar);    // ✅ public only
        // System.out.println(demo.protectedVar); // ❌
        // System.out.println(demo.defaultVar);   // ❌
        // System.out.println(demo.privateVar);   // ❌
    }
}
```

---

## 💡 Best Practices

### 1. **Class top-level**
```java
// ✅ Hợp lệ
public class PublicClass { }
class DefaultClass { }

// ❌ Không hợp lệ cho top-level class
// private class PrivateClass { }   // Compile error
// protected class ProtectedClass { } // Compile error
```

### 2. **Encapsulation Pattern**
```java
public class User {
    private String email;           // Private data
    private int age;
    
    // Public getters/setters với validation
    public String getEmail() {
        return email;
    }
    
    public void setEmail(String email) {
        if (isValidEmail(email)) {   // Private validation
            this.email = email;
        }
    }
    
    public int getAge() {
        return age;
    }
    
    public void setAge(int age) {
        if (age >= 0 && age <= 150) {
            this.age = age;
        }
    }
    
    private boolean isValidEmail(String email) {  // Private helper
        return email != null && email.contains("@");
    }
}
```

### 3. **API Design**
```java
public class FileProcessor {
    // Public API - cho external users
    public void processFile(String filename) {
        if (validateFile(filename)) {
            readFile(filename);
            parseData();
            saveResults();
        }
    }
    
    // Private implementation - hide complexity
    private boolean validateFile(String filename) { /* */ return true; }
    private void readFile(String filename) { /* */ }
    private void parseData() { /* */ }
    private void saveResults() { /* */ }
}
```

---

## 🧪 Quiz - Kiểm tra hiểu biết

### Câu 1: Đoạn code sau có lỗi gì?
```java
package com.app;

class Helper {
    protected void help() { }
}

public class Main {
    public static void main(String[] args) {
        Helper h = new Helper();
        h.help();  // Có lỗi không?
    }
}
```

<details>
<summary>Đáp án</summary>

**Không có lỗi!** Vì `Main` và `Helper` cùng package `com.app`, nên có thể truy cập `protected` method.
</details>

### Câu 2: Code này compile được không?
```java
package animals;

public class Animal {
    protected String name;
}

package pets;
import animals.Animal;

public class Dog extends Animal {
    public void test(Animal other) {
        this.name = "My name";    // Line A
        other.name = "Other name"; // Line B
    }
}
```

<details>
<summary>Đáp án</summary>

**Line A**: ✅ OK - truy cập protected qua `this`
**Line B**: ❌ Error - không thể truy cập protected qua object khác, chỉ qua `this`
</details>

### Câu 3: Method nào có thể gọi được?
```java
package util;

public class Calculator {
    public void add() { }
    protected void subtract() { }
    void multiply() { }
    private void divide() { }
}

package app;
import util.Calculator;

public class App extends Calculator {
    public void test() {
        // Gọi method nào được?
    }
}
```

<details>
<summary>Đáp án</summary>

- `add()` ✅ - public
- `subtract()` ✅ - protected (subclass)
- `multiply()` ❌ - default (khác package)
- `divide()` ❌ - private
</details>

---

## 📈 Ví dụ thực tế: E-commerce System

```java
// File: Product.java
package com.shop.model;

public class Product {
    private String id;                    // Không ai modify trực tiếp
    private String name;
    private double price;
    protected String category;            // Subclass có thể access
    String supplier;                      // Package-private
    
    public Product(String id, String name, double price) {
        this.id = id;
        this.name = name;
        setPrice(price);                  // Use setter for validation
    }
    
    // Public API
    public String getId() { return id; }
    public String getName() { return name; }
    public double getPrice() { return price; }
    
    public void setPrice(double price) {
        if (price >= 0) {
            this.price = price;
            logPriceChange(price);        // Private method
        }
    }
    
    // Protected - cho subclass customize
    protected double calculateDiscount() {
        return price * 0.1;               // 10% default discount
    }
    
    // Package-private - internal operations
    void updateSupplier(String supplier) {
        this.supplier = supplier;
    }
    
    // Private - implementation detail
    private void logPriceChange(double newPrice) {
        System.out.println("Price changed to: " + newPrice);
    }
}
```

```java
// File: ElectronicsProduct.java
package com.shop.model;

public class ElectronicsProduct extends Product {
    private int warrantyMonths;
    
    public ElectronicsProduct(String id, String name, double price) {
        super(id, name, price);
        category = "Electronics";         // ✅ Protected access
        warrantyMonths = 12;
    }
    
    @Override
    protected double calculateDiscount() {  // Override protected method
        return getPrice() * 0.15;         // 15% discount for electronics
    }
}
```

```java
// File: ShoppingCart.java
package com.shop.cart;

import com.shop.model.Product;

public class ShoppingCart {
    public void addProduct(Product product) {
        // product.id = "hack";           // ❌ Private - không access được
        // product.supplier = "fake";     // ❌ Default - khác package
        
        System.out.println("Added: " + product.getName());  // ✅ Public getter
        double discount = product.calculateDiscount();      // ❌ Protected - khác package + không inherit
    }
}
```

---

## ✅ Kết luận

**Access Modifiers** giúp:

1. **🔒 Bảo mật**: Giấu implementation details
2. **📦 Tổ chức**: Kiểm soát dependencies giữa packages  
3. **🛡️ Encapsulation**: Bảo vệ dữ liệu và business logic
4. **🎯 API Design**: Tạo interface rõ ràng cho users

**Nguyên tắc áng vàng**:
- Bắt đầu với **`private`**
- Mở rộng dần khi cần: `private` → `default` → `protected` → `public`
- Chỉ public những gì **thực sự cần thiết** cho external users

**Kết hợp đúng cách** sẽ giúp code:
- ✅ Dễ bảo trì hơn
- ✅ An toàn hơn  
- ✅ Giảm coupling giữa các modules