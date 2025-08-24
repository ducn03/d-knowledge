# 📌 Stack và Heap trong Java

> Vui lòng đọc trước phần **Type** để nắm rõ phân biệt **kiểu dữ liệu nguyên thủy (primitive)** và **kiểu dữ liệu tham chiếu (reference)**.

---

## 🗂️ Vùng nhớ trong Java

Trong Java, dữ liệu và biến được lưu trữ trên **2 vùng nhớ chính**:

### **Stack**  
- Chứa các biến cục bộ (local variables) và lời gọi hàm (method call)  
- Mỗi thread có stack riêng  
- Tuổi thọ: biến tồn tại trong phạm vi method đang chạy  

### **Heap**  
- Chứa các **object** và dữ liệu của reference type  
- Chia sẻ giữa tất cả các thread  
- Được quản lý bởi **Garbage Collector (GC)**

---

## 🧑‍💻 Ví dụ minh họa

```java
// Class
public class Main {
    // Method
    public static void main(String[] args) {
        // Kiểu dữ liệu nguyên thủy (primitive)
        int number = 123;
        // number và giá trị 123 đều nằm trên stack
        
        // Kiểu dữ liệu tham chiếu (reference)
        String str = "Char";
        // str (biến tham chiếu) nằm trên stack
        // "Char" (object) nằm trên heap
        // str tham chiếu tới object "Char" trong heap
    }
}
```

---

## 📍 Nguyên tắc lưu trữ

### **Primitive (int, long, double, boolean...):**
- Giá trị lưu trực tiếp trong stack

### **Reference type (String, Integer, Object...):**
- Biến tham chiếu lưu trong stack
- Địa chỉ (reference) trỏ đến object trong heap
- Object luôn nằm ở heap

---

## 🧠 Ghi nhớ nhanh

### **Stack**
- **Phạm vi:** 1 method, 1 thread
- **Chứa:** primitive value + reference (địa chỉ object)

### **Heap**
- **Chia sẻ** giữa nhiều thread
- **Chứa:** object, instance field, dữ liệu reference type

---

## 📊 Bảng so sánh Stack vs Heap

| Đặc điểm | Stack | Heap |
|----------|-------|------|
| **Tốc độ truy cập** | Nhanh | Chậm hơn |
| **Kích thước** | Nhỏ, hạn chế | Lớn hơn |
| **Thread-safe** | Mỗi thread có stack riêng | Chia sẻ giữa các thread |
| **Quản lý bộ nhớ** | Tự động (khi method kết thúc) | Garbage Collector |
| **Chứa gì** | Local variables, method calls | Objects, instance variables |
| **Lỗi khi hết bộ nhớ** | StackOverflowError | OutOfMemoryError |

---

## 🔍 Ví dụ chi tiết

```java
public class MemoryExample {
    // Instance field - lưu trong heap (khi object được tạo)
    private int instanceVar = 10;
    
    public void exampleMethod() {
        // Local variables - lưu trong stack
        int localPrimitive = 5;           // Stack: giá trị 5
        boolean flag = true;              // Stack: giá trị true
        
        // Reference variables - reference lưu trong stack, object trong heap
        String str = "Hello World";       // Stack: reference -> Heap: "Hello World"
        StringBuilder sb = new StringBuilder(); // Stack: reference -> Heap: StringBuilder object
        int[] array = new int[5];         // Stack: reference -> Heap: mảng với 5 phần tử
        
        // Khi method kết thúc:
        // - Tất cả local variables bị xóa khỏi stack
        // - Objects trong heap vẫn tồn tại cho đến khi GC dọn dẹp
    }
}
```

---

## ⚡ Memory Flow Chi Tiết

```
STACK                                   HEAP
┌─────────────────────────┐              ┌──────────────────────────────────────┐
│     main() method       │              │                                      │
│                         │              │  ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓    │
│  int number = 123       │              │  ┃         STRING POOL           ┃    │
│  ┌─────────────────────┐ │              │  ┃                               ┃    │
│  │ value: 123          │ │              │  ┃  0x1001: "Hello"              ┃    │
│  └─────────────────────┘ │              │  ┃  0x1002: "World"              ┃    │
│                         │              │  ┃  0x1003: "Java"               ┃    │
│  String str1 = "Hello"  │─────────────┐│  ┃  ...                          ┃    │
│  ┌─────────────────────┐ │             ││  ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛    │
│  │ ref: 0x1001         │ │             ││                                      │
│  └─────────────────────┘ │             ││                                      │
│                         │             ││  ┌──────────────────────────────────┐ │
│  String str2 = "Hello"  │─────────────┤│  │      REGULAR OBJECTS             │ │
│  ┌─────────────────────┐ │             ││  │                                  │ │
│  │ ref: 0x1001         │ │             ││  │  0x2001: String("Hi")           │ │
│  └─────────────────────┘ │             ││  │    - char[] value = {'H','i'}   │ │
│                         │             ││  │    - int hash = 0               │ │
│  String str3 = new ... │─────────────┐││  │                                  │ │
│  ┌─────────────────────┐ │           │││  │  0x3001: Person object          │ │
│  │ ref: 0x2001         │ │           │││  │    - String name = null         │ │
│  └─────────────────────┘ │           │││  │    - int age = 0                │ │
│                         │           │││  │                                  │ │
│  Person p = new ...     │─────────────┤││  │  0x4001: int[] array            │ │
│  ┌─────────────────────┐ │           │││  │    - length: 3                  │ │
│  │ ref: 0x3001         │ │           │││  │    - elements: [0, 0, 0]        │ │
│  └─────────────────────┘ │           │││  └──────────────────────────────────┘ │
│                         │           │││                                       │
│  int[] arr = new ...    │─────────────┤││                                      │
│  ┌─────────────────────┐ │           │││                                      │
│  │ ref: 0x4001         │ │           │││                                      │
│  └─────────────────────┘ │           │││                                      │
└─────────────────────────┘           │││                                      │
                                      │││                                      │
                         ┌────────────┘││                                      │
                         └─────────────┘│                                      │
                          ┌─────────────┘                                      │
                          └────────────────────────────────────────────────────┘
```

### 🔍 Giải thích chi tiết:

#### 📦 Stack (Vùng nhớ ngăn xếp)
- **Primitive variables**: Lưu trực tiếp giá trị (như `int number = 123`)
- **Reference variables**: Lưu địa chỉ trỏ đến object trong heap (như `0x1001`)
- **Đặc điểm**: Nhanh, tự động dọn dẹp khi method kết thúc

#### 🏠 Heap (Vùng nhớ đống)
- **String Pool**: Vùng đặc biệt lưu String literals để tối ưu bộ nhớ
- **Regular Objects**: Vùng lưu các object thường (tạo bằng `new`)
- **Đặc điểm**: Chậm hơn, cần Garbage Collector dọn dẹp

#### 🎯 String Pool Optimization:
```java
String str1 = "Hello";        // Lưu trong String Pool
String str2 = "Hello";        // Tái sử dụng object từ String Pool  
String str3 = new String("Hi"); // Tạo object mới trong Regular Objects

// So sánh:
str1 == str2  // true (cùng reference)
str1 == str3  // false (khác reference)
```

### 🏊‍♂️ String Pool Explained

**String Pool** là vùng đặc biệt trong heap để tối ưu hóa String literals:

```java
// Cả 3 biến đều trỏ đến cùng 1 object trong String Pool
String s1 = "Hello";
String s2 = "Hello"; 
String s3 = "Hello";

// Tạo object mới trong heap (KHÔNG dùng String Pool)
String s4 = new String("Hello");

// So sánh
System.out.println(s1 == s2);    // true (cùng reference)
System.out.println(s1 == s4);    // false (khác reference)
System.out.println(s1.equals(s4)); // true (cùng nội dung)
```

---

## ✅ Tóm tắt

- **Primitive → stack**
- **Reference → stack (biến) + heap (object)**
- **Object thì chắc chắn nằm trên heap**
- **Stack chỉ chứa giá trị (primitive) hoặc địa chỉ (reference) trỏ về heap**

---

## 💡 Lưu ý quan trọng

1. **Performance:** Stack nhanh hơn heap do locality và đơn giản hóa
2. **Memory Management:** Stack tự động dọn dẹp, heap cần Garbage Collector
3. **Size Limit:** Stack có giới hạn kích thước nhỏ hơn heap
4. **Thread Safety:** Mỗi thread có stack riêng, nhưng chia sẻ heap
5. **Debugging:** Hiểu stack/heap giúp debug memory leaks và performance issues