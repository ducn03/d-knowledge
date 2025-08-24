# 🔄 Vòng đời của một Object trong Java (Object Life-Cycle)

Hiểu rõ vòng đời của object sẽ giúp bạn làm chủ **Java OOP**.  
Quá trình này diễn ra từ lúc object được tạo ra bằng `new`, sử dụng trong chương trình, cho đến khi **không còn reference nào trỏ tới nó** và cuối cùng bị dọn dẹp bởi **Garbage Collector (GC)** của JVM.

---

## 📚 Ví dụ: So sánh với sách trong thư viện

```java
Book javaBook = new Book("The Java Book");
```

---

## 🔹 Bước 1: Khai báo biến tham chiếu

```java
Book javaBook;
```

👉 **Bạn chỉ tạo ra một biến tham chiếu `javaBook` kiểu `Book`, nhưng chưa tạo object thật sự.**

💡 **Giống như:** Bạn đặt một chỗ trống để "giữ chỗ" cho cuốn sách – chứ sách chưa được in ra.

---

## 🔹 Bước 2: Khởi tạo object bằng new

```java
new Book("The Java Book");
```

👉 **JVM tạo object thật trên heap, gọi constructor để khởi tạo giá trị "The Java Book", rồi trả về một địa chỉ (reference).**

💡 **Giống như:** Thư viện vừa in xong sách và dán mã số định danh cho nó.

---

## 🔹 Bước 3: Gán tham chiếu

```java
javaBook = new Book("The Java Book");
```

👉 **Giờ `javaBook` giữ địa chỉ trỏ tới object đó:**
```
javaBook ────▶ [Book object on heap]
```

💡 **Giống như:** Bạn gán thẻ mượn sách vào đúng cuốn sách tương ứng.

---

## 🌀 Gán lại reference (Reassignment)

```java
Book refBook = javaBook;
javaBook = null;
```

- `refBook = javaBook;` → Cả 2 biến cùng trỏ tới cùng 1 object
- `javaBook = null;` → Biến `javaBook` không còn giữ gì, nhưng object vẫn tồn tại vì `refBook` vẫn trỏ vào.

```
javaBook → null
refBook ──▶ [Book object]
```

⛔ **Vì còn ít nhất 1 reference → object chưa bị GC.**

---

## 🚮 Khi nào object bị Garbage Collected?

Chỉ khi **không còn bất kỳ biến nào giữ reference** thì object mới trở thành **unreachable** và được GC thu gom.

```java
refBook = null;
```

Giờ object mất hết reference:
```
javaBook → null
refBook → null
Object → 🪦 eligible for GC
```

---

## 🔄 Vòng đời Object - Diagram

```
STEP 1: DECLARATION
┌─────────────────┐
│     STACK       │              HEAP
├─────────────────┤        ┌──────────────┐
│ Book javaBook   │        │              │
│ (uninitialized) │        │              │
└─────────────────┘        └──────────────┘

STEP 2: INSTANTIATION
┌─────────────────┐
│     STACK       │              HEAP
├─────────────────┤        ┌──────────────┐
│ Book javaBook   │───────▶│ Book object  │
│ (ref: 0x1001)   │        │ title: "..."  │
└─────────────────┘        └──────────────┘

STEP 3: REASSIGNMENT
┌─────────────────┐
│     STACK       │              HEAP
├─────────────────┤        ┌──────────────┐
│ Book javaBook   │───────▶│ Book object  │
│ (ref: 0x1001)   │        │ title: "..."  │◀─┐
│                 │        └──────────────┘  │
│ Book refBook    │──────────────────────────┘
│ (ref: 0x1001)   │
└─────────────────┘

STEP 4: NULL ASSIGNMENT
┌─────────────────┐
│     STACK       │              HEAP
├─────────────────┤        ┌──────────────┐
│ Book javaBook   │        │ Book object  │
│ (null)          │        │ title: "..."  │◀─┐
│                 │        └──────────────┘  │
│ Book refBook    │──────────────────────────┘
│ (ref: 0x1001)   │
└─────────────────┘

STEP 5: ALL REFERENCES NULL
┌─────────────────┐
│     STACK       │              HEAP
├─────────────────┤        ┌──────────────┐
│ Book javaBook   │        │ Book object  │
│ (null)          │        │ 🪦 GC ready  │
│                 │        └──────────────┘
│ Book refBook    │
│ (null)          │
└─────────────────┘
```

---

## ✅ Tóm lại – Vòng đời Object

1. **Tạo bằng `new`**
2. **Khởi tạo bằng constructor**
3. **Sử dụng**
4. **Mất hết reference**
5. **Bị dọn bởi Garbage Collector**

---

## 🤯 Mẹo quan trọng

- **`null` không có nghĩa là object biến mất ngay!**
- **Chỉ khi tất cả reference đều `null` thì object mới được GC dọn dẹp.**
- **GC trong Java là tự động, bạn không cần (và không nên) ép gọi thủ công.**

---

## 📝 Ví dụ thực tế

```java
public class ObjectLifeCycleExample {
    public static void main(String[] args) {
        // Step 1: Declaration
        Book book1, book2;
        
        // Step 2: Instantiation
        book1 = new Book("Java Fundamentals");
        
        // Step 3: Multiple references
        book2 = book1;  // Cả 2 đều trỏ đến cùng object
        
        // Step 4: Partial dereferencing
        book1 = null;   // Object vẫn tồn tại vì book2 vẫn trỏ tới
        
        // Step 5: Complete dereferencing
        book2 = null;   // Giờ object eligible for GC
        
        // Step 6: GC sẽ tự động dọn dẹp (không thể dự đoán khi nào)
        System.gc(); // Chỉ là suggestion, không đảm bảo GC chạy ngay
    }
}
```

---

## 🔍 Reference Types và GC

### Strong Reference (Default)
```java
Book book = new Book("Title"); // Strong reference
// Object sẽ không bị GC miễn còn strong reference
```

### Weak Reference (Advanced)
```java
import java.lang.ref.WeakReference;

WeakReference<Book> weakBook = new WeakReference<>(new Book("Title"));
// Object có thể bị GC ngay cả khi còn weak reference
```

### Null Reference
```java
Book book = null; // Không trỏ đến object nào
// Truy cập sẽ throw NullPointerException
```

---

## ⚠️ Memory Leaks và Best Practices

### ❌ Tránh Memory Leaks
```java
// BAD: Collection giữ reference, ngăn GC
List<Book> books = new ArrayList<>();
for (int i = 0; i < 1000000; i++) {
    books.add(new Book("Book " + i));
}
// Tất cả Book objects không thể bị GC

// GOOD: Clear references khi không cần
books.clear(); // Cho phép GC dọn dẹp
books = null;  // Thậm chí clear cả collection reference
```

### ✅ Best Practices
1. **Set references to null** khi không cần nữa
2. **Close resources** (files, connections) trong finally/try-with-resources  
3. **Avoid static collections** chứa nhiều objects
4. **Use weak references** cho caches khi phù hợp