# Remote Control Center v4 (Client - Server)

Một dự án quản trị máy tính từ xa (Remote Control/Administration Tool) được viết hoàn toàn bằng **Python**, sử dụng giao diện đồ hoạ hiện đại **CustomTkinter** với tính năng tự động co dãn màn hình thông minh. Ứng dụng hoạt động theo mô hình Client-Server, cho phép kết nối, giám sát và điều khiển PC qua mạng LAN (hoặc qua Internet nếu cấu hình Port Forwarding/VPN).

---

## 🚀 Các Tính Năng Chính

Cả Server và Client đều sở hữu giao diện đồ hoạ (GUI) thân thiện tích hợp hàng loạt các tính năng mạnh mẽ sau đây:

- 💻 **Remote Terminal**: Gửi lệnh CMD từ xa và nhận kết quả tức thì.
- ⚙️ **Task Manager**: Quản lý đa tiến trình; xem chi tiết Ứng dụng / Process chạy ngầm; bộ lọc theo tên; hỗ trợ Start/Kill bất kỳ tiến trình nào.
- 📁 **File Manager**: Duyệt cây thư mục ở máy trạm, Upload (tải lên) và Download (tải xuống) file dễ dàng.
- 📺 **Screen Mirroring**: Trực tiếp truyền phát (stream) màn hình của máy Server thời gian thực.
- 📷 **Webcam Capture**: Truyền phát hình ảnh trực tiếp từ Webcam của máy Server.
- ⌨️ **Keylogger**: Lắng nghe và ghi lại thao tác bàn phím (có thể Start/Stop/Lấy log).
- ℹ️ **System Info**: Cung cấp thông tin phần cứng Server (OS, CPU, RAM, Disk).
- 📦 **Installed Software**: Trích xuất chi tiết danh sách tất cả các phần mềm đã cài đặt trên thiết bị Server.
- 🔌 **Power Management**: Điều khiển nguồn máy (Shutdown, Restart, Sleep).
- 🛠️ **Multi-Session Tabs**: Quản lý cùng lúc nhiều phiên kết nối tới nhiều PC khác nhau trong các Tab độc lập của Client.
- 🛡️ **Tự động cấp quyền & Mở Firewall**: Server tự động kích hoạt quyền Admin và thêm/xóa chỉ mục ngoại lệ Tường lửa Windows cho kết nối ổn định.
- 📐 **Dynamic UI Scaling**: UI tự động nội suy và co dãn tuỳ thuộc vào mọi độ phân giải màn hình (Base: 2K Resolution).

---

## 🛠️ Cài đặt & Yêu cầu hệ thống

### 1. Yêu cầu hệ thống:
- Hệ điều hành: Windows 10 / 11.
- Python: Version 3.8 trở lên.

### 2. Thư viện cài đặt:
Cần cài đặt một vài package Python tương ứng cho dự án bằng lệnh:
```bash
pip install customtkinter pillow opencv-python pynput
```
> ***Lưu ý:*** Có thể có một số module đi kèm hệ thống Windows không cần cài (như `socket`, `threading`, `ctypes`, v.v...).

---

## 📖 Hướng Dẫn Sử Dụng

Dự án được phân tách gọn gàng thành hai modules chính là `server` và `client`.

### 1. Khởi chạy Server (Máy bị điều khiển)
- Mở Terminal/CMD dưới quyền Administrator (hệ thống sẽ pop-up UAC hỏi nếu bạn chưa mở).
- Đi tới thư mục dự án và chạy tệp:
  ```bash
  python server.py
  ```
- Trên giao diện của Server, nhấp vào **`Start Hosting Session`**. Server sẽ in ra địa chỉ IP hiện tại để Client trỏ về.

### 2. Khởi chạy Client (Máy điều khiển)
- Mở Terminal/CMD và chạy tệp:
  ```bash
  python client.py
  ```
- Nhập địa chỉ IP hiển thị trên màn hình Server của bạn và nhấn phím **Enter** hoặc nút **`Connect`**.
- Sau khi kết nối thành công, tất cả tính năng điều khiển sẽ sáng bật. Bạn có thể mở nhiều Tab để kết nối tới nhiều Server cùng lúc thông qua thanh Tab "Connections".

---

## 🏗️ Cấu trúc thư mục

```
RemoteControl_v4/
│
├── client/                     # Module mã nguồn cho Client
│   ├── features/               # Các chức năng tách rời (Task Manager, Screen, File...)
│   ├── app.py                  # Giao diện chính của Client
│   ├── network.py              # Xử lý kết nối nền (socket logic, heartbeat loop)
│   ├── session.py              # Quản lý 1 phiên kết nối (quy tụ client features)
│   └── theme.py                # Tuỳ chỉnh giao diện nếu có
│
├── server/                     # Module mã nguồn cho Server
│   ├── app.py                  # Giao diện chính và Server Socket Manager
│   ├── handlers.py             # Logic thực thi lệnh hệ thống từ Client gửi qua
│   ├── keylogger.py            # Chạy nền listener theo dõi bàn phím
│   └── streaming.py            # Xử lý việc thu thập và gửi ảnh Screen/Webcam
│
├── client.py                   # Điểm neo entry-point chạy ứng dụng Client
├── server.py                   # Điểm neo entry-point chạy ứng dụng Server
└── README.md                   # File hướng dẫn
```

---

## ⚠️ Khuyến cáo pháp lý (Disclaimer)
Công cụ này được tạo ra vì mục đích  **nghiên cứu, học tập kiến thức Quản trị mạng và Lập trình Python**. Người phát triển chia sẻ kiến thức này hoàn toàn **không** chịu trách nhiệm về bất cứ hình thức lạm dụng, phá hoại hay xâm nhập trái phép vào máy tính của người khác. **Chỉ được tải, cài đặt và giám sát sự đồng thuận trên máy tính thuộc quyền sở hữu cá nhân/mạng nội bộ của bạn!**
