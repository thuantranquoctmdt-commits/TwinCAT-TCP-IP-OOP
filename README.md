# TwinCAT TCP-IP OOP (GIT)

Mô tả
-----
Project mẫu TwinCAT PLC / runtime cấu trúc OOP dành cho ví dụ TCP/IP. Bao gồm cấu hình boot, project TwinCAT (GIT.tsproj) và file cấu hình runtime.

Yêu cầu
-------
- TwinCAT 3 (khuyến nghị >= 3.1.4021; target build trong repo: 3.1.4024)
- Visual Studio (đã dùng VS ~15.0 / VS2017) + TwinCAT XAE
- Quyền để deploy lên TwinCAT RT (x64) hoặc target phù hợp

Cấu trúc thư mục
----------------
- GIT/ - project TwinCAT chính (.tsproj, PLC...)
- GIT/_Boot/TwinCAT RT (x64)/ - file boot / runtime config (CurrentConfig.xml, TargetDescription.xml, Port_851.app ...)
- .vs/ - cấu hình Visual Studio (không cần commit)
- GIT.sln - solution

Hướng dẫn nhanh (mở / build / deploy)
-------------------------------------
1. Mở `GIT.sln` bằng Visual Studio + TwinCAT XAE.
2. Chọn cấu hình tương ứng (Debug/Release) và target TwinCAT RT (x64) nếu cần.
3. Build project trong Visual Studio.
4. Kết nối tới target (local hoặc remote) qua TwinCAT, deploy project:
   - Nếu sử dụng boot autostart: kiểm tra `GIT/_Boot/TwinCAT RT (x64)/CurrentConfig.xml`.
   - Port PLC mẫu sử dụng cổng 851 (xem file Port_851.app / InitCmds).

Thông tin cấu hình
------------------
- RequiredTargetVersion: 3.1.4021 (xem CurrentConfig.xml)
- Boot init commands: nhiều InitCmd đã được thêm (ví dụ Download Symbols, Create TComObj, Start Interrupt...). Xem `CurrentConfig.xml` để biết chi tiết.

Test / Demo
----------
- Cách test phụ thuộc vào PLC code trong project. Nếu có module TCP/IP, mô tả cách kết nối (port, proto) ở đây.
- Ví dụ: kết nối client TCP tới IP:PORT 851 để gửi/nhận dữ liệu (nếu project cung cấp ví dụ).

Ghi chú
-------
- File `.app` và `CurrentConfig.xml` chứa cấu hình boot/runtime; cẩn thận khi chỉnh nếu deploy lên hệ thực.
- Xóa/ẩn thông tin nhạy cảm (IP, mật khẩu, license keys) trước khi public.

Contributing
------------
1. Fork repository.
2. Tạo branch `feature/...` hoặc `fix/...`.
3. Tạo pull request mô tả thay đổi.

License
-------
Thêm file LICENSE hoặc ghi rõ license tại đây (ví dụ: MIT) nếu bạn muốn public theo một giấy phép cụ thể.

Contact / Liên hệ
-----------------
- Repository owner: thuantranquoctmdt-commits
- Thêm email hoặc contact nếu muốn.

---

English summary
----------------

# TwinCAT TCP-IP OOP (GIT)

Description
-----------
Sample TwinCAT PLC / runtime project demonstrating OOP-style TCP/IP usage. Contains TwinCAT project, boot/runtime configuration and example PLC files.

Requirements
------------
- TwinCAT 3 (recommended >= 3.1.4021)
- Visual Studio + TwinCAT XAE

Quick start
-----------
1. Open `GIT.sln` in Visual Studio with TwinCAT XAE.
2. Build and deploy to the target (local/remote TwinCAT runtime).
3. Check boot files under `GIT/_Boot/TwinCAT RT (x64)/` for autostart configuration.

Please update README with more details about how to run any TCP/IP demo inside the PLC code if available.
