# n8n local

Dự án này cài n8n bằng npm để chạy thử trên Windows. Giao diện chỉ lắng nghe trên máy hiện tại tại cổng `5678`.

## Yêu cầu

- Node.js và npm. Dự án đã được cài và chạy với Node.js 24.
- Kết nối internet để tải các gói khi cài đặt.

## Cài đặt

Mở PowerShell trong thư mục dự án và chạy:

```powershell
cd D:\n8n
npm ci
```

Nếu dự án nằm ở thư mục khác, thay `D:\n8n` bằng đường dẫn tương ứng.

## Khởi động

Trong PowerShell, chạy:

```powershell
cd D:\n8n
$env:N8N_LISTEN_ADDRESS = '127.0.0.1'
$env:N8N_HOST = '127.0.0.1'
$env:N8N_USER_FOLDER = (Join-Path (Get-Location) 'data')
$env:N8N_DIAGNOSTICS_ENABLED = 'false'
$env:N8N_VERSION_NOTIFICATIONS_ENABLED = 'false'
node .\node_modules\n8n\bin\n8n start
```

Giữ cửa sổ PowerShell mở trong khi sử dụng. Truy cập [http://127.0.0.1:5678](http://127.0.0.1:5678); lần đầu, làm theo hướng dẫn trên trang để tạo tài khoản quản trị. Nhấn `Ctrl+C` trong cửa sổ PowerShell để dừng n8n.

Nếu cổng 5678 đã được sử dụng, hãy dừng tiến trình n8n đang chạy trước khi khởi động một phiên khác.

## Dữ liệu và cấu hình

n8n lưu dữ liệu trong `data/.n8n/`, gồm cơ sở dữ liệu và cấu hình của phiên cài đặt. Thư mục `data/`, các tệp log, `.env` và `node_modules/` được loại khỏi Git. Sao lưu thư mục dữ liệu nếu muốn giữ workflow và thông tin kết nối; không chia sẻ công khai vì thư mục này có thể chứa thông tin nhạy cảm.

Một số node hoặc tích hợp cần kết nối internet và thông tin xác thực riêng. Việc sử dụng các dịch vụ bên ngoài có thể phát sinh phí.
