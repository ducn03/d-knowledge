# Bắt đầu với Java

## 1. Cài đặt JDK và môi trường

### Tải JDK
- Truy cập [Oracle JDK](https://www.oracle.com/apac/java/technologies/downloads/) hoặc [OpenJDK](https://openjdk.org/) để tải JDK mới nhất
- Cài đặt bình thường theo hướng dẫn của hệ điều hành

### Thiết lập biến môi trường

**Windows:**
- Thêm thư mục `bin` của JDK vào `PATH`
- Ví dụ: `C:\Program Files\Java\jdk-21\bin`

**Linux / macOS:**
- Thêm vào `~/.bashrc` hoặc `~/.zshrc`:
```bash
export PATH=$PATH:/usr/lib/jvm/java-21/bin
```

### Kiểm tra cài đặt
Kiểm tra cài đặt thành công bằng lệnh:
```bash
java -version
javac -version
```

## 2. Chương trình Java đầu tiên

Tạo file `Main.java` với nội dung:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello world");
    }
}
```

## 3. Quy tắc cơ bản khi compile

### Tên file phải trùng với tên class
- Ví dụ: class `Main` thì file phải là `Main.java`

### Phương thức main bắt buộc
```java
public static void main(String[] args)
```

**Lưu ý quan trọng:**
- Đây là điểm bắt đầu (entry point) của chương trình
- Nếu sai tên hoặc sai cú pháp, chương trình sẽ không chạy được
- Tham số có thể đặt tên khác (như `args`, `arguments`) nhưng kiểu phải là `String[]`

## 4. Compile và chạy chương trình

### Biên dịch (compile)
```bash
javac Main.java
```

**👉 Lưu ý:**
- Phải gõ đúng tên file kèm `.java`
- Kết quả: sinh ra file `Main.class`

### Chạy chương trình
```bash
java Main
```

**👉 Lưu ý:**
- Chỉ gõ tên class, không cần `.class`

### Kết quả
Chương trình sẽ in ra:
```
Hello world
```

## 5. Các lỗi thường gặp

| Lỗi | Nguyên nhân | Cách khắc phục |
|-----|-------------|----------------|
| `javac: file not found` | Tên file sai hoặc thiếu đuôi `.java` | Kiểm tra tên file và đuôi |
| `class Main is public, should be declared in a file named Main.java` | Tên file không trùng với tên class | Đổi tên file cho đúng |
| `Could not find or load main class` | Sai tên class khi chạy hoặc file `.class` không tồn tại | Kiểm tra tên class và đảm bảo đã compile thành công |
| `Main method not found` | Method `main` sai signature | Sửa lại method `main` cho đúng cú pháp |

## 6. Quy trình hoàn chỉnh

1. **Viết code** → Tạo file `.java`
2. **Compile** → `javac FileName.java` → Tạo ra file `.class`
3. **Run** → `java ClassName` → Chạy chương trình