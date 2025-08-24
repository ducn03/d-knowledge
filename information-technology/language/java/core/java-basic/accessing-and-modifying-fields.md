# 📌 Truy cập và sửa giá trị Field trong Java (Accessing and Modifying Fields)

---

## 🧍‍♂️ 1. Truy cập Field thuộc về object (instance field)

Để truy cập field thuộc về object, bạn cần:
1. Tạo một object từ class  
2. Dùng dấu chấm (`.`) để truy cập field  

```java
Person person = new Person();
String name = person.firstName;
int age = employee.age;
```

---

## ✏️ 2. Sửa giá trị Field của object

Sử dụng toán tử gán `=` như bình thường:

```java
person.firstName = "John";
employee.age = 45;
```

➡️ **Field thay đổi riêng cho từng object.**

---

## 🏛️ 3. Truy cập Field tĩnh (static field)

Vì static field thuộc về class, bạn không cần tạo object để truy cập.

**Cú pháp:**
```java
ClassName.fieldName
```

### 📘 Ví dụ:
```java
double pi = Math.PI;
int max = Integer.MAX_VALUE;
```

---

## ✅ 4. Truy cập Field từ chính bên trong class

Trong cùng class, bạn có thể truy cập trực tiếp bằng tên field — không cần object, không cần class name.

```java
public class Example {
    private static int count = 0;
    private String name;
    
    public void printName() {
        System.out.println(name);          // OK
        System.out.println(count);         // OK
        System.out.println(Example.count); // 👌 khuyến khích rõ ràng hơn với static
    }
}
```

---

## 🔐 5. Tác động của Access Modifier

**Ví dụ class Person:**
```java
public class Person {
    public String name;     // Ai cũng truy cập được
    private int age;        // Chỉ dùng trong Person
    protected String email; // Cùng package + subclass khác package
    double height;          // default → chỉ cùng package
}
```

### 📘 Cách truy cập từng field

#### ✅ public field
```java
Person p = new Person();
p.name = "Alice"; // OK mọi nơi
```

#### ❌ private field
```java
p.age = 30; // ❌ Compile error, vì age là private
```

→ **Phải dùng getter/setter:**
```java
public int getAge() { return age; }
public void setAge(int a) { age = a; }
```

#### ✅ protected field
```java
// OK nếu cùng package
String email = p.email;

class Employee extends Person {
    void setEmail(String e) {
        email = e; // OK trong subclass dù khác package
    }
}
```

#### ✅ default (package-private) field
```java
// OK nếu class Student và Person cùng package
class Student {
    void printHeight(Person p) {
        System.out.println(p.height);
    }
}
```

---

## 🎯 Kinh nghiệm chuẩn hóa

1. **Luôn khai báo field là private**
2. **Dùng getter/setter để:**
   - Bảo vệ dữ liệu
   - Kiểm soát logic khi truy cập

### 📝 Ví dụ Best Practice:
```java
public class Person {
    private String name;
    private int age;
    
    // Getter
    public String getName() {
        return name;
    }
    
    // Setter với validation
    public void setAge(int age) {
        if (age < 0 || age > 150) {
            throw new IllegalArgumentException("Invalid age: " + age);
        }
        this.age = age;
    }
    
    public int getAge() {
        return age;
    }
}
```

---

## 📊 Bảng tổng hợp Access Modifier

| Access Modifier | Cùng class | Cùng package | Subclass khác package | Khác package |
|----------------|------------|--------------|----------------------|--------------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| `default` | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

---

## 💡 Lưu ý quan trọng

- **Instance field**: Cần object để truy cập (`object.field`)
- **Static field**: Truy cập qua class (`ClassName.field`)
- **Encapsulation**: Luôn dùng private field + getter/setter
- **Validation**: Thêm logic kiểm tra trong setter để đảm bảo dữ liệu hợp lệ