# Giải đề — OT\_00 (Bài tập thực hành thêm)

**Tóm tắt:** Tài liệu gốc (`OT_00.pdf`) là một tập slide có 12 bài tập nhưng file OCR/preview thiếu nội dung chi tiết (nhiều chỗ hiển thị `???`). Mình đã tạo file này để: (1) nêu rõ chỗ thiếu, (2) cung cấp mẫu lời giải tổng quát / template code cho các bài tập thường gặp với cùng tên (SUM, Max, x ? y ?, S = ?, ...), để bạn dán đề chính xác (nếu cần) hoặc dùng trực tiếp nếu dạng bài giống.

---

## Hướng dẫn chung

* Mỗi bài mình đưa: *Mô tả dạng bài* (khi đề cụ thể bị thiếu), *Ý tưởng lời giải*, và *Mã mẫu C++* (có thể biên dịch với `g++ -std=c++17`).
* Nếu bạn upload lại trang có nội dung đầy đủ cho câu nào, mình sẽ sửa phần đó cho đúng đề và trả lại file md cập nhật.

---

## Bài 1 — (Slide 1)

**Trạng thái:** Nội dung đề không thể đọc rõ (slide có tiêu đề `Bài tập thực hành thêm`).

**Giả định phổ biến:** Tính tổng các phần tử mảng hoặc tính SUM từ 1..n.

**Ý tưởng:** Dùng vòng lặp `for` hoặc công thức tổng trực tiếp.

**Mã mẫu (tổng 1..n):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    long long n; if(!(cin>>n)) return 0;
    long long sum = n*(n+1)/2; // công thức
    cout<<sum<<"\n";
}
```

**Mã mẫu (tổng mảng):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n; cin>>n; vector<long long>a(n);
    for(int i=0;i<n;i++) cin>>a[i];
    long long sum=0; for(auto v:a) sum+=v;
    cout<<sum<<"\n";
}
```

---

## Bài 2 — (Slide 2)

**Trạng thái:** Nội dung không rõ.

**Có thể là:** Đếm số phần tử thỏa điều kiện, lọc, sắp xếp.

**Mã mẫu (đếm số chẵn trong mảng):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n; cin>>n; vector<int>a(n);
    for(int i=0;i<n;i++) cin>>a[i];
    int cnt=0; for(int v:a) if(v%2==0) cnt++;
    cout<<cnt<<"\n";
}
```

---

## Bài 3 — (Slide 3) — `SUM ???`

**Trạng thái:** Đề gốc hiển thị `SUM ???` nên nội dung cụ thể bị thiếu.

**Hai khả năng thường gặp:**

1. Tính tổng các chữ số/n phần tử thỏa điều kiện.
2. Tính tổng dãy có công thức.

**Mã mẫu (tổng chữ số):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    long long x; cin>>x; x = llabs(x);
    int s=0; while(x){ s += x%10; x/=10; }
    cout<<s<<"\n";
}
```

---

## Bài 4 — (Slide 4) — `Max is ???`

**Trạng thái:** Có vẻ yêu cầu tìm phần tử lớn nhất.

**Mã mẫu (max trong mảng):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n; if(!(cin>>n)) return 0; vector<long long>a(n);
    for(int i=0;i<n;i++) cin>>a[i];
    cout<< *max_element(a.begin(), a.end()) <<"\n";
}
```

---

## Bài 5 — (Slide 5) — `x ? y ?`

**Trạng thái:** Chuỗi `x ? y ?` không đủ thông tin. Có thể là phép toán so sánh, hoặc bài hỏi giá trị của x,y sau một đoạn chương trình.

**Mẫu: Tính x và y sau dãy phép gán:**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int x,y; cin>>x>>y;
    // ví dụ: x = x + y; y = x - y;
    x = x + y; y = x - y; x = x - y; // hoán đổi
    cout<<x<<" "<<y<<"\n";
}
```

---

## Bài 6 — (Slide 6) — `S = ?`

**Trạng thái:** Có thể là tính tổng S theo công thức: S = 1+2+... hoặc S = 1/2 + 1/4 + ... hoặc S = ∑ i/(i+1)

**Mã mẫu (S = 1 + 1/2 + ... + 1/n, in double):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n; cin>>n; double S=0;
    for(int i=1;i<=n;i++) S += 1.0/i;
    cout<<fixed<<setprecision(6)<<S<<"\n";
}
```

---

## Bài 7 — (Slide 7)

**Trạng thái:** Thiếu nội dung. Có thể là bài về vòng lặp / chuỗi.

**Mẫu (đếm chữ số = số chữ số của số nguyên):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    long long x; cin>>x; x = llabs(x);
    int d = (x==0)?1:0;
    while(x){ d++; x/=10; }
    cout<<d<<"\n";
}
```

---

## Bài 8 — (Slide 8)

**Trạng thái:** Thiếu nội dung.

**Mẫu (tính tổng các số lẻ <= n):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n; cin>>n; long long s=0;
    for(int i=1;i<=n;i+=2) s+=i;
    cout<<s<<"\n";
}
```

---

## Bài 9 — (Slide 9)

**Trạng thái:** Thiếu nội dung.

**Mẫu (kiểm tra số nguyên tố):**

```cpp
#include <bits/stdc++.h>
using namespace std;
bool isPrime(int x){ if(x<=1) return false; for(int i=2;i*1ll*i<=x;i++) if(x%i==0) return false; return true; }
int main(){ int n; cin>>n; cout<<(isPrime(n)?"YES":"NO")<<"\n"; }
```

---

## Bài 10 — (Slide 10)

**Trạng thái:** Thiếu nội dung.

**Mẫu (sắp xếp mảng tăng dần):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){ int n; cin>>n; vector<int>a(n); for(int i=0;i<n;i++) cin>>a[i]; sort(a.begin(), a.end()); for(int v:a) cout<<v<<" "; cout<<"\n"; }
```

---

## Bài 11 — (Slide 11)

**Trạng thái:** Thiếu nội dung.

**Mẫu (tìm phần tử xuất hiện nhiều nhất):**

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){ int n; cin>>n; vector<int>a(n); for(int i=0;i<n;i++) cin>>a[i]; unordered_map<int,int> cnt; for(int v:a) cnt[v]++;
    int best=a[0], m=0; for(auto &p:cnt) if(p.second>m){ m=p.second; best=p.first; }
    cout<<best<<"\n";
}
```

---

## Bài 12 — (Slide 12)

**Trạng thái:** Slide có tiêu đề nhưng nội dung chi tiết **không có** trong bản preview.

**Lời nhắc:** Nếu đây là bài tổng hợp (tính S, tính max, thao tác mảng...), dán đề phần này và mình sẽ giải chi tiết.

---

## Kết luận & bước tiếp theo

1. Mình đã tạo file này để bạn mở và xem. **Nội dung gốc của OT\_00 thiếu nhiều chi tiết**, vì vậy mình cung cấp các template lời giải phổ biến cho các dạng bài thường gặp tương ứng với tên slide (SUM, Max, S=?,...).
2. Hãy **upload lại trang/ảnh** chỉ chứa đề chi tiết của bài bạn muốn mình giải (ví dụ: chỉ câu 3 hoặc câu 4). Mình sẽ sửa chính xác và cập nhật file md ngay.

---

*Muốn mình tiếp tục — upload file đề tiếp theo (OT\_01, OT\_02, ...) hoặc upload ảnh/scan của slide nào đó để mình giải chi tiết.*
