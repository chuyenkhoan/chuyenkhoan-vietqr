# Chuyển Khoản VietQR
Dưới đây là hướng dẫn thanh toán chuyển khoản VietQR cho website, bạn có thể xem trước ví dụ [chuyenkhoan_vietqr_simple.htm](https://github.com/chuyenkhoan/chuyenkhoan-vietqr/blob/main/chuyenkhoan_vietqr_simple.htm) hoặc [chuyenkhoan_vietqr_full.htm](https://github.com/chuyenkhoan/chuyenkhoan-vietqr/blob/main/chuyenkhoan_vietqr_full.htm) để trải nghiệm cách hoạt động của thư viện.

## Bước 1: Thêm thư viện Chuyển khoản VietQR

Thêm đoạn mã sau vào thẻ `<header>` của trang bạn muốn hiện thông tin chuyển khoản:

```html
<!-- Load chuyenkhoan-vietqr lib -->
<script async src="https://chuyenkhoan.com/web/chuyenkhoan-vietqr-1.1.js"></script>
```

Lưu ý: Bạn có thể thêm đoạn mã trên vào trước thẻ đóng `</html>` của trang. 

## Bước 2: Nhập thông tin tài khoản nhận

Bạn tiếp tục thêm đoạn mã sau vào thẻ `<header>` để cấu hình tài khoản ngân hàng nhận tiền.

```html
<header>
...
  
<!-- Config chuyenkhoan-vietqr -->
<script> 
  function ckConfig() { 
    return { 
      ckicon: true, 
      accounts: [
        { 
          "bankName": "$BANK_NAME_1",
          "accountNumber": "$ACCOUNT_NUMBER_1",
          "accountName": "$ACCOUNT_NAME_1"
        },
        { 
          "bankName": "$BANK_NAME_2",
          "accountNumber": "$ACCOUNT_NUMBER_2",
          "accountName": "$ACCOUNT_NAME_2"
        }
      ]
    } 
  } 
</script>

...
</header>
```
Trong đó:
- $BANK_NAME: là tên ngân hàng, ví dụ *Vietcombank, BIDV, VietinBank, MBBank, Techcombank, Agribank, ACB, MSB, hoặc VIB..*
- $ACCOUNT_NUMBER: là số tài khoản nhận tiền, ví dụ: *0451000285534*
- $ACCOUNT_NAME: là tên tài khoản nhận tiền, ví dụ: *CTCP GIAI PHAP THANH TOAN CHUYEN KHOAN*

Bạn có thể cấu hình một hoặc nhiều tài khoản ngân hàng nhận. [Chuyenkhoan.com](https://chuyenkhoan.com) có tiện ích thiết kế Chuyển khoản QR giúp bạn nhập thông tin chính xác hơn, sau đó bạn chỉ việc copy nội dung cấu hình tài khoản.

Lưu ý: ***Chuyenkhoan.com chỉ và chỉ hiện thông tin chuyển khoản do bạn cấu hình, việc tạo mã VietQR được thực hiện ngay trong thư viện chuyenkhoan-vietqr, không gọi đến bất kỳ một website nào khác.***

## Bước 3: Các cách hiện Chuyển khoản VietQR

### 3.1 Hiện hoặc ẩn nút chuyển khoản (Floating Action Button)

Để hiện hoặc ẩn nút chuyển khoản, bạn chỉ cần thay đổi cấu hình ở Bước 2 cho `ckicon: true` hoặc `ckicon: false`.

### 3.2 Hiện thông tin chuyển khoản tĩnh bên trong trang
Để hiện thông tin chuyển khoản tĩnh bên trong trang, bạn thêm đoạn mã sau vào vị trí cần hiển thị
```html
<body>
...
  
<!-- Show chuyenkhoan-vietqr box -->
<div style="margin: auto; align-items: center;" id="chuyenkhoan_vietqr"></div>
  
...
</body>
```

### 3.3 Hiện thông tin chuyển khoản động theo số tiền và nội dung
Để cập nhật số tiền và nội dung chuyển khoản ở mục 3.2, bạn chỉ cần gọi hàm javascript `CKQR.update($amount, $message)`.

### 3.4 Hiện hộp thoại thanh toán chuyển khoản
Khi khách hàng bấm nút *Chuyển khoản* để thanh toán, bạn có thể hiện thông tin thanh toán dạng hộp thoại sử dụng hàm `CKQR.payNow($amount, $message)`.

```html
<body>
...
  
<!-- Show CKQR dialog -->
<button onclick='CKQR.payNow(2022, "Chuyenkhoan.com CMNM 2022")'>Chuyển khoản</button>
  
...
</body>
```

### 3.5 Hiện thông tin chuyển khoản thành công (xác nhận giao dịch tự động)
Vui lòng liên hệ: cskh@chuyenkhoan.com
