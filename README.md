<div align="center">
  <img src="image/image.png" alt="Zunny Cloud" width="200" style="border-radius: 50%; box-shadow: 0 10px 20px rgba(0,0,0,0.2);">
  
  # ☁️ Zunny Cloud – Windows RDP Server
  
  **Tự động khởi tạo máy chủ Windows với RDP, Tailscale và wallpaper thương hiệu**
  
  ![](https://img.shields.io/badge/Platform-Windows_2022-blue?style=flat-square&logo=windows)
  ![](https://img.shields.io/badge/RDP-Ready-00C8FF?style=flat-square)
  ![](https://img.shields.io/badge/Powered%20by-Zun_Technologies-0A192F?style=flat-square)
  
</div>

---

## 🚀 Giới thiệu

Workflow GitHub Actions này tự động **tạo một máy chủ Windows ảo**, cấu hình Remote Desktop (RDP), kết nối qua mạng **Tailscale** và cài đặt hình nền thương hiệu Zunny. Mỗi lần chạy sẽ tạo một user mới với mật khẩu ngẫu nhiên (bắt đầu bằng `Zunny` + 6 ký tự), đảm bảo an toàn và riêng tư.

**Dùng cho:**  
- Kiểm thử ứng dụng trên Windows  
- Truy cập tạm thời vào môi trường Windows  
- Chạy tác vụ tự động cần giao diện đồ họa  

---

## 📦 Tính năng

| Tính năng | Mô tả |
|-----------|-------|
| **RDP sẵn sàng** | Bật Remote Desktop, mở port 3389, cấu hình bảo mật tối ưu |
| **User động** | Tạo user `ZunnyUser` + mật khẩu random (12 ký tự) – thay đổi mỗi lần chạy |
| **Wallpaper tự động** | Set hình nền từ `image/image.png` qua Scheduled Task (áp dụng ngay khi đăng nhập) |
| **Kết nối an toàn** | Dùng Tailscale – không cần mở port công cộng, có IP riêng (100.x.x.x) |
| **Giám sát phiên** | Hiển thị thời gian còn lại, log trạng thái RDP mỗi 2 phút |
| **Dọn dẹp tự động** | Xóa user, đóng Tailscale, khôi phục firewall sau khi hết thời gian |

---

## 🕹️ Cách sử dụng

### 1. Cấu hình repository
- Fork hoặc clone repository này về.
- Đặt ảnh nền muốn dùng vào đường dẫn `image/image.png` (hỗ trợ PNG).
- Thêm **secret** `TAILSCALE_AUTH_KEY` vào repository settings (lấy từ tài khoản Tailscale).

### 2. Chạy workflow
- Vào tab **Actions** → Chọn workflow **ZUNNY CLOUD RDP SERVER**.
- Nhấn **Run workflow** → Chọn thời gian sử dụng (1h, 3h hoặc 5h40m).
- Chờ khoảng 2-3 phút để quá trình hoàn tất.

### 3. Kết nối RDP
- Sau khi workflow chạy xong, phần **THÔNG TIN KẾT NỐI** sẽ hiển thị:
  - **Địa chỉ:** IP Tailscale (ví dụ `100.118.179.2`)
  - **Tài khoản:** `ZunnyUser`
  - **Mật khẩu:** `ZunnyXXXXXX` (12 ký tự)
- Mở **Remote Desktop Connection** (mstsc) trên máy tính của bạn (đã cài Tailscale hoặc dùng VPN).
- Nhập IP, user, password và kết nối.

> **Lưu ý:** Bạn cũng có thể dùng địa chỉ `localhost` nếu chạy workflow trên cùng máy, nhưng khuyến nghị dùng Tailscale.

---

## 📊 Thông tin đầu ra

Sau khi kết nối thành công, bạn sẽ thấy:

- **Desktop** với hình nền thương hiệu Zunny.
- **Quyền Administrator** đầy đủ.
- **Tailscale** đã được cài và kết nối.

Workflow tự động giám sát và dừng sau thời gian đã chọn.  
Mọi dữ liệu sẽ bị xóa (user bị xóa, firewall đóng, Tailscale ngắt).

---

## 🧩 Tuỳ chỉnh

### Thay đổi thời gian mặc định
Sửa `default: '5h40m'` trong file `Rdp.yml` (dòng `duration`).

### Thay đổi hình nền
Ghi đè file `image/image.png` bằng ảnh mong muốn (khuyến nghị kích thước 1920x1080).

### Tắt Scheduled Task wallpaper
Nếu không muốn set wallpaper, xóa hoặc comment step `CÀI ĐẶT WALLPAPER ZUNNY (SCHEDULED TASK)`.

---

## ❓ Hỏi đáp nhanh

**Q: Tôi không thấy địa chỉ Tailscale?**  
A: Đảm bảo bạn đã thêm `TAILSCALE_AUTH_KEY` hợp lệ. Nếu vẫn lỗi, workflow sẽ fallback về `localhost`.

**Q: Mật khẩu được lưu ở đâu?**  
A: Mật khẩu chỉ hiển thị trong log của workflow (có thể copy) và được xóa sau khi workflow kết thúc.

**Q: Tôi có thể kéo dài thời gian không?**  
A: Không – workflow tự động dừng sau thời gian đã chọn. Hãy chạy lại workflow mới nếu cần.

**Q: Chi phí?**  
A: GitHub Actions chạy trên máy ảo miễn phí (2 lõi, 7GB RAM, 14GB SSD) với giới hạn 2.000 phút/tháng đối với tài khoản miễn phí. Bạn nên kiểm tra hạn mức của mình.

---

## 📫 Liên hệ & Hỗ trợ

- **Telegram Bot:** [@Zunnycloud_bot](https://t.me/Zunnycloud_bot)
- **Email:** [zunny932@gmail.com](mailto:zunny932@gmail.com)

---

<div align="center">
  <sub>© 2026 Zun Technologies – Built with ☁️ and 💙 by Zunny</sub>
</div>
