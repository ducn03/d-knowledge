# GIẢI ĐỀ THI LẬP TRÌNH C++ - ĐỀ 2

## CÂU 1: Mảng một chiều (1.5 điểm)

**Yêu cầu:** Viết chương trình C++ nhập vào mảng 1 chiều gồm n số nguyên. Thực hiện:
- a) Tính tổng các số nguyên tố có trong mảng
- b) Sắp xếp mảng theo thứ tự giảm dần

### Code giải quyết:

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

// Hàm kiểm tra số nguyên tố
bool laSoNguyenTo(int n) {
    if (n < 2) return false;
    if (n == 2) return true;
    if (n % 2 == 0) return false;
    
    for (int i = 3; i * i <= n; i += 2) {
        if (n % i == 0) return false;
    }
    return true;
}

// Hàm tính tổng số nguyên tố trong mảng
int tongSoNguyenTo(int arr[], int n) {
    int tong = 0;
    for (int i = 0; i < n; i++) {
        if (laSoNguyenTo(arr[i])) {
            tong += arr[i];
        }
    }
    return tong;
}

// Hàm sắp xếp mảng giảm dần (Bubble Sort)
void sapXepGiamDan(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] < arr[j + 1]) {
                // Hoán đổi
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

// Hàm in mảng
void inMang(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int n;
    
    cout << "Nhap so phan tu cua mang: ";
    cin >> n;
    
    int* arr = new int[n];
    
    cout << "Nhap " << n << " so nguyen: " << endl;
    for (int i = 0; i < n; i++) {
        cout << "arr[" << i << "] = ";
        cin >> arr[i];
    }
    
    cout << "\nMang vua nhap: ";
    inMang(arr, n);
    
    // a) Tính tổng số nguyên tố
    int tong = tongSoNguyenTo(arr, n);
    cout << "Tong cac so nguyen to trong mang: " << tong << endl;
    
    // b) Sắp xếp giảm dần
    sapXepGiamDan(arr, n);
    cout << "Mang sau khi sap xep giam dan: ";
    inMang(arr, n);
    
    delete[] arr; // Giải phóng bộ nhớ
    return 0;
}
```

### Giải thích chi tiết:

**Hàm `laSoNguyenTo()`:**
- Số < 2: không phải số nguyên tố
- Số 2: là số nguyên tố duy nhất chẵn
- Số chẵn > 2: không phải số nguyên tố
- Kiểm tra chia hết cho các số lẻ từ 3 đến √n

**Hàm `tongSoNguyenTo()`:**
- Duyệt qua từng phần tử mảng
- Kiểm tra từng phần tử có phải số nguyên tố không
- Cộng dồn các số nguyên tố

**Hàm `sapXepGiamDan()`:**
- Sử dụng thuật toán Bubble Sort
- So sánh 2 phần tử liền kề
- Hoán đổi nếu phần tử trước nhỏ hơn phần tử sau

---

## CÂU 2: Mảng hai chiều (1.5 điểm)

**Yêu cầu:** Viết chương trình nhập vào ma trận vuông cấp n (1 ≤ n ≤ 100) gồm các số nguyên.
- a) Tính tổng các phần tử nằm trên đường chéo chính
- b) Đếm số lượng phần tử là số chẵn nằm ở cột cuối cùng

### Code giải quyết:

```cpp
#include <iostream>
using namespace std;

// Hàm nhập ma trận
void nhapMaTran(int a[][100], int n) {
    cout << "Nhap cac phan tu cua ma tran " << n << "x" << n << ":" << endl;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cout << "a[" << i << "][" << j << "] = ";
            cin >> a[i][j];
        }
    }
}

// Hàm in ma trận
void inMaTran(int a[][100], int n) {
    cout << "Ma tran vua nhap:" << endl;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cout << a[i][j] << "\t";
        }
        cout << endl;
    }
}

// a) Tính tổng các phần tử trên đường chéo chính
int tongDuongCheoChinh(int a[][100], int n) {
    int tong = 0;
    for (int i = 0; i < n; i++) {
        tong += a[i][i]; // Phần tử trên đường chéo chính có chỉ số i = j
    }
    return tong;
}

// b) Đếm số chẵn ở cột cuối cùng
int demSoChanCotCuoi(int a[][100], int n) {
    int dem = 0;
    int cotCuoi = n - 1; // Chỉ số cột cuối cùng
    
    for (int i = 0; i < n; i++) {
        if (a[i][cotCuoi] % 2 == 0) { // Kiểm tra số chẵn
            dem++;
        }
    }
    return dem;
}

int main() {
    int n;
    int a[100][100];
    
    do {
        cout << "Nhap cap cua ma tran vuong (1 <= n <= 100): ";
        cin >> n;
    } while (n < 1 || n > 100);
    
    // Nhập ma trận
    nhapMaTran(a, n);
    
    // In ma trận
    inMaTran(a, n);
    
    // a) Tính tổng đường chéo chính
    int tongCheoChinh = tongDuongCheoChinh(a, n);
    cout << "\nTong cac phan tu tren duong cheo chinh: " << tongCheoChinh << endl;
    
    // Hiển thị các phần tử đường chéo chính
    cout << "Cac phan tu tren duong cheo chinh: ";
    for (int i = 0; i < n; i++) {
        cout << a[i][i] << " ";
    }
    cout << endl;
    
    // b) Đếm số chẵn ở cột cuối
    int soLuongChan = demSoChanCotCuoi(a, n);
    cout << "\nSo luong phan tu chan o cot cuoi cung: " << soLuongChan << endl;
    
    // Hiển thị các phần tử ở cột cuối
    cout << "Cac phan tu o cot cuoi cung: ";
    for (int i = 0; i < n; i++) {
        cout << a[i][n-1] << " ";
    }
    cout << endl;
    
    return 0;
}
```

### Giải thích chi tiết:

**Đường chéo chính:**
- Các phần tử có chỉ số hàng = chỉ số cột (i = j)
- Trong ma trận n×n: a[0][0], a[1][1], ..., a[n-1][n-1]

**Cột cuối cùng:**
- Chỉ số cột = n-1
- Các phần tử: a[0][n-1], a[1][n-1], ..., a[n-1][n-1]
- Số chẵn: n % 2 == 0

---

## CÂU 3: Struct + mảng Struct (2.0 điểm)

**Yêu cầu:** Khai báo cấu trúc SanPham gồm mã sản phẩm, tên sản phẩm, đơn giá, số lượng tồn.
- a) Nhập vào mảng n sản phẩm
- b) In ra sản phẩm có số lượng tồn lớn nhất
- c) Tính tổng giá trị hàng tồn kho (tổng đơn giá × số lượng của tất cả sản phẩm)

### Code giải quyết:

```cpp
#include <iostream>
#include <string>
#include <iomanip>
using namespace std;

// Khai báo cấu trúc SanPham
struct SanPham {
    int maSP;
    string tenSP;
    float donGia;
    int soLuongTon;
};

// a) Hàm nhập thông tin một sản phẩm
void nhapSanPham(SanPham &sp) {
    cout << "Nhap ma san pham: ";
    cin >> sp.maSP;
    cin.ignore(); // Xóa ký tự newline còn lại
    
    cout << "Nhap ten san pham: ";
    getline(cin, sp.tenSP);
    
    cout << "Nhap don gia: ";
    cin >> sp.donGia;
    
    cout << "Nhap so luong ton: ";
    cin >> sp.soLuongTon;
    
    cout << "------------------------" << endl;
}

// Hàm nhập mảng sản phẩm
void nhapDanhSachSanPham(SanPham ds[], int n) {
    cout << "NHAP THONG TIN " << n << " SAN PHAM:" << endl;
    for (int i = 0; i < n; i++) {
        cout << "San pham thu " << (i + 1) << ":" << endl;
        nhapSanPham(ds[i]);
    }
}

// Hàm xuất thông tin một sản phẩm
void xuatSanPham(const SanPham &sp) {
    cout << "Ma SP: " << sp.maSP << endl;
    cout << "Ten SP: " << sp.tenSP << endl;
    cout << "Don gia: " << fixed << setprecision(2) << sp.donGia << " VND" << endl;
    cout << "So luong ton: " << sp.soLuongTon << endl;
    cout << "Gia tri ton kho: " << fixed << setprecision(2) 
         << (sp.donGia * sp.soLuongTon) << " VND" << endl;
    cout << "------------------------" << endl;
}

// Hàm xuất danh sách sản phẩm
void xuatDanhSachSanPham(const SanPham ds[], int n) {
    cout << "\nDANH SACH SAN PHAM:" << endl;
    for (int i = 0; i < n; i++) {
        cout << "San pham thu " << (i + 1) << ":" << endl;
        xuatSanPham(ds[i]);
    }
}

// b) Tìm sản phẩm có số lượng tồn lớn nhất
int timSanPhamTonLonNhat(const SanPham ds[], int n) {
    int viTriMax = 0;
    for (int i = 1; i < n; i++) {
        if (ds[i].soLuongTon > ds[viTriMax].soLuongTon) {
            viTriMax = i;
        }
    }
    return viTriMax;
}

// c) Tính tổng giá trị hàng tồn kho
double tongGiaTriTonKho(const SanPham ds[], int n) {
    double tongGiaTri = 0;
    for (int i = 0; i < n; i++) {
        tongGiaTri += ds[i].donGia * ds[i].soLuongTon;
    }
    return tongGiaTri;
}

// Hàm hiển thị thống kê
void hienThiThongKe(const SanPham ds[], int n) {
    cout << "\n========== THONG KE ==========" << endl;
    
    // b) Sản phẩm có số lượng tồn lớn nhất
    int viTriMax = timSanPhamTonLonNhat(ds, n);
    cout << "SAN PHAM CO SO LUONG TON LON NHAT:" << endl;
    xuatSanPham(ds[viTriMax]);
    
    // c) Tổng giá trị tồn kho
    double tongGiaTri = tongGiaTriTonKho(ds, n);
    cout << "TONG GIA TRI HANG TON KHO: " << fixed << setprecision(2) 
         << tongGiaTri << " VND" << endl;
    
    cout << "================================" << endl;
}

int main() {
    int n;
    
    cout << "Nhap so luong san pham: ";
    cin >> n;
    
    // Cấp phát động mảng struct
    SanPham* danhSach = new SanPham[n];
    
    // a) Nhập danh sách sản phẩm
    nhapDanhSachSanPham(danhSach, n);
    
    // Xuất danh sách vừa nhập
    xuatDanhSachSanPham(danhSach, n);
    
    // Hiển thị thống kê
    hienThiThongKe(danhSach, n);
    
    // Giải phóng bộ nhớ
    delete[] danhSach;
    
    return 0;
}
```

### Giải thích chi tiết:

**Cấu trúc SanPham:**
- `maSP`: Mã định danh sản phẩm
- `tenSP`: Tên sản phẩm (dùng string để dễ xử lý)
- `donGia`: Giá một đơn vị sản phẩm
- `soLuongTon`: Số lượng còn trong kho

**Các hàm chính:**
- `nhapSanPham()`: Nhập thông tin một sản phẩm
- `xuatSanPham()`: Hiển thị thông tin một sản phẩm với định dạng đẹp
- `timSanPhamTonLonNhat()`: Trả về chỉ số của sản phẩm có số lượng tồn lớn nhất
- `tongGiaTriTonKho()`: Tính tổng giá trị = Σ(đơn giá × số lượng tồn)

---

## CÂU 4: Con trỏ + cấp phát động (2.0 điểm)

**Yêu cầu:** Viết chương trình sử dụng cấp phát động (new/delete) để:
- a) Nhập vào số nguyên n và tạo mảng động n phần tử kiểu float
- b) Tìm và in ra phần tử có giá trị lớn nhất trong mảng đó
- c) Giải phóng vùng nhớ đã cấp phát

### Code giải quyết:

```cpp
#include <iostream>
#include <iomanip>
#include <limits> // Cho numeric_limits
using namespace std;

// Hàm nhập mảng động
void nhapMangDong(float* arr, int n) {
    cout << "Nhap " << n << " so thuc:" << endl;
    for (int i = 0; i < n; i++) {
        cout << "arr[" << i << "] = ";
        cin >> arr[i];
    }
}

// Hàm xuất mảng
void xuatMang(float* arr, int n) {
    cout << "Mang vua nhap: ";
    for (int i = 0; i < n; i++) {
        cout << fixed << setprecision(2) << arr[i] << " ";
    }
    cout << endl;
}

// b) Tìm phần tử lớn nhất
float timPhanTuLonNhat(float* arr, int n, int& viTri) {
    float max = arr[0];
    viTri = 0;
    
    for (int i = 1; i < n; i++) {
        if (arr[i] > max) {
            max = arr[i];
            viTri = i;
        }
    }
    
    return max;
}

// Hàm hiển thị thông tin chi tiết về mảng
void hienThiThongTin(float* arr, int n) {
    cout << "\n========== THONG TIN MANG ==========" << endl;
    
    // Thống kê cơ bản
    float tong = 0;
    float min = arr[0], max = arr[0];
    int viTriMin = 0, viTriMax = 0;
    
    for (int i = 0; i < n; i++) {
        tong += arr[i];
        
        if (arr[i] < min) {
            min = arr[i];
            viTriMin = i;
        }
        
        if (arr[i] > max) {
            max = arr[i];
            viTriMax = i;
        }
    }
    
    cout << "So phan tu: " << n << endl;
    cout << "Tong cac phan tu: " << fixed << setprecision(2) << tong << endl;
    cout << "Trung binh cong: " << fixed << setprecision(2) << (tong / n) << endl;
    cout << "Phan tu nho nhat: " << fixed << setprecision(2) << min 
         << " (tai vi tri " << viTriMin << ")" << endl;
    cout << "Phan tu lon nhat: " << fixed << setprecision(2) << max 
         << " (tai vi tri " << viTriMax << ")" << endl;
    
    cout << "===================================" << endl;
}

// Kiểm tra tính hợp lệ của input
bool kiemTraNhapLieu(int n) {
    if (n <= 0) {
        cout << "Loi: So phan tu phai lon hon 0!" << endl;
        return false;
    }
    if (n > 1000000) {
        cout << "Cảnh bao: So phan tu qua lon, co the gay tran bo nho!" << endl;
        cout << "Ban co chac chan muon tiep tuc? (y/n): ";
        char choice;
        cin >> choice;
        return (choice == 'y' || choice == 'Y');
    }
    return true;
}

int main() {
    int n;
    float* arr = nullptr; // Khởi tạo con trỏ = nullptr
    
    // a) Nhập n và tạo mảng động
    do {
        cout << "Nhap so phan tu cua mang: ";
        cin >> n;
    } while (!kiemTraNhapLieu(n));
    
    try {
        // Cấp phát bộ nhớ động
        arr = new float[n];
        cout << "Da cap phat thanh cong " << n << " phan tu float." << endl;
        cout << "Dia chi bat dau cua mang: " << arr << endl;
        
        // Nhập dữ liệu
        nhapMangDong(arr, n);
        
        // Xuất mảng
        xuatMang(arr, n);
        
        // b) Tìm phần tử lớn nhất
        int viTriMax;
        float giaTriMax = timPhanTuLonNhat(arr, n, viTriMax);
        
        cout << "\nPhan tu co gia tri lon nhat:" << endl;
        cout << "Gia tri: " << fixed << setprecision(2) << giaTriMax << endl;
        cout << "Vi tri: " << viTriMax << " (chi so mang)" << endl;
        cout << "Thu tu: " << (viTriMax + 1) << " (vi tri thu may)" << endl;
        
        // Hiển thị thông tin chi tiết
        hienThiThongTin(arr, n);
        
        // Hiển thị thông tin bộ nhớ
        cout << "\nThong tin bo nho:" << endl;
        cout << "Kich thuoc moi phan tu float: " << sizeof(float) << " bytes" << endl;
        cout << "Tong kich thuoc mang: " << (n * sizeof(float)) << " bytes" << endl;
        
    }
    catch (bad_alloc& e) {
        cout << "Loi: Khong the cap phat bo nho!" << endl;
        cout << "Chi tiet loi: " << e.what() << endl;
        return 1;
    }
    
    // c) Giải phóng vùng nhớ
    if (arr != nullptr) {
        delete[] arr;
        arr = nullptr; // Đặt về nullptr để tránh dangling pointer
        cout << "\nDa giai phong bo nho thanh cong!" << endl;
    }
    
    cout << "Chuong trinh ket thuc." << endl;
    return 0;
}
```

### Giải thích chi tiết:

**Cấp phát động:**
```cpp
float* arr = new float[n]; // Cấp phát n phần tử float
```

**Ưu điểm của cấp phát động:**
- Kích thước mảng được xác định tại runtime
- Tiết kiệm bộ nhớ (chỉ cấp phát khi cần)
- Linh hoạt trong việc quản lý bộ nhớ

**Xử lý lỗi:**
- `try-catch` để bắt lỗi `bad_alloc` khi không đủ bộ nhớ
- Kiểm tra `n <= 0` và `n` quá lớn
- Khởi tạo con trỏ = `nullptr`

**Giải phóng bộ nhớ:**
```cpp
delete[] arr;    // Giải phóng mảng
arr = nullptr;   // Tránh dangling pointer
```

**Lưu ý quan trọng:**
- Luôn `delete[]` sau khi `new[]`
- Kiểm tra `nullptr` trước khi `delete`
- Đặt con trỏ = `nullptr` sau khi `delete`

---

## TỔNG KẾT VÀ LƯU Ý

### Kiến thức đã áp dụng:

1. **Mảng một chiều:**
   - Thuật toán kiểm tra số nguyên tố
   - Thuật toán sắp xếp Bubble Sort
   - Quản lý bộ nhớ động

2. **Mảng hai chiều:**
   - Xử lý ma trận vuông
   - Đường chéo chính (i = j)
   - Truy cập cột cuối cùng

3. **Struct:**
   - Định nghĩa cấu trúc dữ liệu
   - Mảng struct động
   - Tìm kiếm theo tiêu chí
   - Tính toán tổng hợp

4. **Con trỏ và cấp phát động:**
   - `new[]` và `delete[]`
   - Xử lý lỗi `bad_alloc`
   - Quản lý bộ nhớ an toàn
   - Tránh memory leak

### Tips quan trọng:

✅ **Luôn nhớ:**
- Kiểm tra input hợp lệ
- Giải phóng bộ nhớ sau khi sử dụng
- Xử lý trường hợp biên
- Format output đẹp mắt

⚠️ **Tránh các lỗi:**
- Quên `delete[]` → Memory leak
- Truy cập ngoài phạm vi mảng
- Chia cho 0
- Không kiểm tra `nullptr`

🎯 **Coding style tốt:**
- Tên hàm, biến có ý nghĩa
- Comment giải thích logic
- Tách nhỏ thành các hàm
- Consistent formatting