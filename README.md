# 🚀 Windows RDP via GitHub Actions

Dự án này cung cấp quy trình tự động (Workflow) để tạo một máy ảo **Windows Server 2022** miễn phí trên hạ tầng GitHub Actions, cho phép kết nối từ xa qua **Remote Desktop Protocol (RDP)** sử dụng đường hầm **Ngrok**.


---

## 📋 Yêu cầu chuẩn bị

1.  **Tài khoản GitHub** (đã kích hoạt Actions).
2.  **Tài khoản Ngrok** (Miễn phí). Đăng ký tại [ngrok.com](https://dashboard.ngrok.com/signup).
3.  **Ngrok Authtoken**: Lấy tại [Dashboard Ngrok](https://dashboard.ngrok.com/get-started/your-authtoken).

---

## ⚙️ Cài đặt & Cấu hình

### Bước 1: Thêm Ngrok Token vào Secrets
Để bảo mật, không điền trực tiếp token vào file code. Hãy làm như sau:

1.  Vào repository của bạn trên GitHub.
2.  Chọn **Settings** ➔ **Secrets and variables** ➔ **Actions**.
3.  Nhấn nút **New repository secret**.
4.  Điền thông tin:
    * **Name:** `NGROK_AUTHTOKEN`
    * **Secret:** *(Dán mã token Ngrok của bạn vào đây)*
5.  Nhấn **Add secret**.

### Bước 2: Tạo Workflow
Tạo file `.github/workflows/rdp.yml` và dán nội dung code workflow vào.

---

## 🎮 Hướng dẫn chạy

1.  Vào tab **Actions** trên thanh menu của Repository.
2.  Ở cột bên trái, chọn workflow **Windows RDP **.
3.  Nhấn nút **Run workflow** ➔ **Run workflow**.
4.  Chờ khoảng **1-2 phút** để quá trình khởi tạo hoàn tất.
5.  Click vào job đang chạy, xem phần **Summary** hoặc log của bước "Start ngrok" để lấy thông tin kết nối.

---

## 🔌 Cách kết nối (Remote Desktop)

### 1. Thông tin đăng nhập
* **Địa chỉ (Computer):** Lấy từ log (ví dụ: `0.tcp.ap.ngrok.io:1xxxxx`)
* **Username:** `runneradmin`
* **Password:** `Win2026A!` *(Hoặc mật khẩu bạn đã sửa trong code)*

### 2. Cấu hình Client để Giảm Lag 
Do máy chủ đặt xa, bạn có thể cấu hình `Remote Desktop Connection (mstsc)` như sau trước khi bấm Connect để tránh bị delay chuột:

1.  Mở **Remote Desktop Connection**, nhấn **Show Options**.
2.  Tab **Display**:
    * Colors: Chọn **High Color (16 bit)**.
3.  Tab **Experience**:
    * Chọn profile: **Modem (56 kbps)**.
    * **Bỏ tick tất cả** các ô bên dưới (Desktop background, font smoothing, animations...).
    * Chỉ giữ lại: *Reconnect if the connection is dropped*.
4.  Nhấn **Connect**.

---

## ⚠️ Lưu ý quan trọng (Disclaimer)

1.  **CẤM ĐÀO COIN (NO MINING):** Tuyệt đối không sử dụng VPS này để đào tiền ảo, treo tool chiếm dụng CPU liên tục. Tài khoản GitHub của bạn sẽ bị **khóa vĩnh viễn**.
2.  **Thời gian sử dụng:** Tối đa 6 giờ cho mỗi lần chạy (giới hạn của GitHub).
3.  **Dữ liệu:** Dữ liệu sẽ bị xóa sạch sau khi tắt workflow. Hãy sao lưu dữ liệu quan trọng ra ngoài (Google Drive, v.v.).
4.  **Hiệu năng:** Đây là máy ảo không có GPU, không phù hợp để xem video, chơi game hay các tác vụ đồ họa nặng. Chỉ dùng để test code, build phần mềm hoặc lướt web nhẹ.

---

