# ♻️ Garbage Collection (GC) – Dọn rác trong Java

Tưởng tượng bạn là **thủ thư**. Những cuốn sách không ai mượn nữa sẽ bị gỡ khỏi kệ để nhường chỗ cho sách mới. Trong **Java**, điều tương tự xảy ra với các **object không còn được tham chiếu (reference)** – nghĩa là không còn biến nào trỏ tới chúng nữa.

## 📖 Ví dụ
```java
Book refBook = new Book();
refBook = null; // Bây giờ object Book trở thành "rác"
```

## 🔎 Quá trình GC hoạt động
1. **Tìm các object không còn được dùng**  
   GC sẽ tự động quét vùng heap, tìm những object không còn được tham chiếu bởi bất kỳ biến nào.

2. **Thu hồi vùng nhớ**  
   Các object "mồ côi" này sẽ bị xóa khỏi bộ nhớ. Vùng nhớ mà chúng chiếm giữ được trả lại cho heap để JVM có thể tái sử dụng cho object mới.

3. **Quản lý hoàn toàn tự động 🤖**  
   Bạn không cần (và không nên) gọi GC thủ công trong Java. Điều này giúp tránh lỗi phổ biến như:  
   - **Memory leak** (rò rỉ bộ nhớ)  
   - **Double-free** (giải phóng hai lần)  
   Những lỗi này vốn là ác mộng trong C/C++.

## 📌 Java vs. C – Quản lý bộ nhớ
| Ngôn ngữ | Ai giải phóng bộ nhớ? | Rủi ro |
|----------|-----------------------|--------|
| C        | Lập trình viên tự gọi `free()` | Dễ sai sót, crash nếu quên |
| Java     | JVM tự động gọi GC    | An toàn, ít bug hơn |

## ✅ Tóm tắt ý chính
| Ý nghĩa                     | Mô tả ngắn gọn                                                                 |
|-----------------------------|-------------------------------------------------------------------------------|
| `ref = null;`               | Mất 1 reference → nếu không còn reference nào, object sẽ được GC              |
| GC tìm object unreachable   | Object không thể truy cập từ đâu nữa                                          |
| GC giải phóng bộ nhớ        | Java thu hồi vùng nhớ object chiếm giữ                                        |
| Không gọi GC thủ công       | JVM quản lý tự động – lập trình viên yên tâm hơn                              |

## ⚠️ Lưu ý quan trọng
- GC không xảy ra ngay lập tức sau khi object trở thành unreachable.  
- JVM sẽ quyết định thời điểm GC chạy, thường là khi bộ nhớ thấp.