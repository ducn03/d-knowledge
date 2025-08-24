# 📘 Kiểu dữ liệu trong Java

Java có **2 nhóm kiểu dữ liệu chính**:
- **Kiểu dữ liệu nguyên thủy (Primitive Type)**
- **Kiểu dữ liệu tham chiếu (Reference Type)**

Ngoài ra còn có **Wrapper Class** để đối tượng hóa các primitive.

---

## I. Kiểu dữ liệu nguyên thủy (Primitive Type)

Java có **8 primitive type**:

| Kiểu     | Kích thước | Phạm vi giá trị | Ví dụ |
|----------|------------|-----------------|-------|
| `byte`   | 8 bit      | -128 → 127 | `byte a = 10;` |
| `short`  | 16 bit     | -32,768 → 32,767 | `short b = 1000;` |
| `char`   | 16 bit     | 0 → 65,535 (Unicode) | `char c = 'A';` |
| `int`    | 32 bit     | -2,147,483,648 → 2,147,483,647 | `int d = 12345;` |
| `float`  | 32 bit     | 6–7 chữ số thập phân | `float e = 3.14f;` |
| `long`   | 64 bit     | -9,223,372,036,854,775,808 → 9,223,372,036,854,775,807 | `long f = 1000000000L;` |
| `double` | 64 bit     | 15–16 chữ số thập phân | `double g = 3.14159265359;` |
| `boolean`| 1 bit      | `true` / `false` | `boolean h = true;` |

### Đặc điểm của Primitive Type
- Lưu trực tiếp giá trị trong **stack memory**
- Giá trị mặc định: `0` (số), `false` (boolean), `'\u0000'` (char)
- Không thể gọi method trực tiếp
- Hiệu suất cao, tiết kiệm bộ nhớ

---

## II. Kiểu dữ liệu tham chiếu (Reference Type)

### 1. Khái niệm
- **Reference type** không lưu trực tiếp giá trị mà **lưu địa chỉ (con trỏ)** trỏ đến object trong **heap memory**
- Nếu chưa gán → giá trị mặc định là `null`
- So sánh bằng `==` → so sánh địa chỉ
- So sánh nội dung → dùng `.equals()`

### 2. Các loại Reference Type

#### **Class**
```java
String s1 = "Java";                // trong string pool
String s2 = new String("Java");    // object mới trong heap

System.out.println(s1 == s2);      // false (khác địa chỉ)
System.out.println(s1.equals(s2)); // true  (cùng nội dung)
```

#### **Array**
```java
int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 3};

System.out.println(arr1 == arr2);            // false (khác địa chỉ)
System.out.println(Arrays.equals(arr1, arr2)); // true (so sánh phần tử)
```

#### **Interface**
```java
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");
```

#### **Object**
```java
Object obj = new Object();
```

### 3. So sánh Primitive vs Reference
```java
int x = 10;               // primitive: lưu trực tiếp 10 (stack)
Integer y = 10;           // wrapper: biến lưu địa chỉ object (heap)
String name = "Java";     // reference: trỏ tới string pool
```

- **Primitive**: lưu trực tiếp trong stack
- **Reference**: trỏ tới object trong heap

---

## III. Wrapper Class (Lớp bao)

### 1. Bảng mapping Primitive ↔ Wrapper

| Kiểu nguyên thủy | Wrapper class |
|------------------|---------------|
| `byte`           | `Byte`        |
| `short`          | `Short`       |
| `char`           | `Character`   |
| `int`            | `Integer`     |
| `float`          | `Float`       |
| `long`           | `Long`        |
| `double`         | `Double`      |
| `boolean`        | `Boolean`     |

### 2. Lợi ích của Wrapper Class

#### Sử dụng trong Collections
Collections chỉ có thể lưu object, không lưu primitive:
```java
List<Integer> numbers = new ArrayList<>(); // ✅ Đúng
List<int> numbers = new ArrayList<>();     // ❌ Sai
```

#### Các phương thức tiện ích
```java
Integer.parseInt("123");        // Chuyển String → int
Double.valueOf("3.14");         // Chuyển String → Double
Integer.MAX_VALUE;              // Giá trị lớn nhất
```

#### Hỗ trợ Autoboxing & Unboxing
```java
int x = 5;
Integer y = x;  // Autoboxing (tự động chuyển int → Integer)
int z = y;      // Unboxing (tự động chuyển Integer → int)
```

### 3. Wrapper Cache (Integer Cache)

Java cache một số giá trị để tiết kiệm bộ nhớ.

#### Phạm vi cache mặc định:
- **Integer**: -128 → 127
- **Byte**: -128 → 127
- **Short**: -128 → 127
- **Long**: -128 → 127
- **Character**: 0 → 127
- **Boolean**: cache `true` và `false`

#### Ví dụ về Cache:
```java
Integer a = 100;
Integer b = 100;
System.out.println(a == b); // true (cache)

Integer c = 200;
Integer d = 200;
System.out.println(c == d); // false (ngoài cache)
```

#### Thay đổi phạm vi cache:
```bash
-XX:AutoBoxCacheMax=<value>
```

---

## IV. So sánh tổng hợp

| Đặc điểm | Primitive | Reference Type | Wrapper Class |
|----------|-----------|----------------|---------------|
| **Lưu trữ** | Giá trị trực tiếp | Địa chỉ object | Đối tượng (bao primitive) |
| **Nơi lưu** | Stack | Heap (object) + Stack (reference) | Heap |
| **Giá trị mặc định** | `0`, `false`, `'\u0000'` | `null` | `null` |
| **Ví dụ** | `int x = 10;` | `String s = "Java";` | `Integer n = 10;` |
| **Dùng trong Collections** | ❌ | ✅ | ✅ |
| **Method tiện ích** | ❌ | ✅ | ✅ |
| **Autoboxing/Unboxing** | ❌ | ❌ | ✅ |
| **Caching** | ❌ | ❌ | ✅ |

---

## V. Minh họa Stack vs Heap vs Cache

```java
int x = 10;              // primitive (stack: 10)
Integer y = 10;          // wrapper (cache từ -128→127)
Integer z = 200;         // wrapper (heap, object mới)
String s = "Java";       // string pool (heap, cache)
String t = new String("Java"); // object mới (heap)
```

### Sơ đồ bộ nhớ:
```
STACK                    HEAP
┌─────────────┐         ┌──────────────────────────────┐
│ x: 10       │         │  Integer Cache (-128→127)    │
│ y: ────────────────────→  [10] ←─ y trỏ tới          │
│ z: ────────────────────→  Object(200) ←─ z trỏ tới   │
│ s: ────────────────────→  String Pool                │
│ t: ────────────────────→  │  "Java" ←─ s trỏ tới     │
└─────────────┘         │  Object("Java") ←─ t trỏ tới │
                        └──────────────────────────────┘
```

**Giải thích:**
- `x`: primitive, nằm trực tiếp trong stack
- `y`: wrapper, tham chiếu đến object từ Integer cache
- `z`: wrapper, tạo object mới trong heap
- `s`: reference, trỏ đến object trong string pool
- `t`: reference, trỏ đến object mới trong heap

---

## VI. Lưu ý quan trọng

### 1. Khi nào dùng Primitive?
- Khi cần hiệu suất cao
- Biến đơn giản, không cần method
- Tính toán số học

### 2. Khi nào dùng Wrapper?
- Sử dụng Collections
- Cần method tiện ích
- Có thể nhận giá trị `null`
- Làm việc với Generic

### 3. Best Practices
```java
// ✅ Tốt
int count = 0;                    // primitive cho biến đơn giản
List<Integer> numbers = new ArrayList<>(); // wrapper cho collections

// ❌ Không nên
Integer count = 0;                // không cần wrapper cho biến đơn giản
```