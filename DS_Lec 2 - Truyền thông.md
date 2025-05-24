# 📘 Tóm tắt kiến thức”

## 1. Tiến trình và luồng
- **Tiến trình (Process):** Là chương trình đang chạy. Có không gian địa chỉ riêng biệt.
- **Luồng (Thread):** Là luồng thực thi trong tiến trình. Các luồng chia sẻ tài nguyên như bộ nhớ, dữ liệu.

---

## 2. So sánh đa tiến trình và đa luồng

| Tiêu chí        | Đa tiến trình    | Đa luồng         |
|-----------------|------------------|------------------|
| Không gian nhớ  | Riêng biệt       | Chia sẻ          |
| Giao tiếp       | Phức tạp         | Dễ dàng          |
| Hiệu năng       | Thấp hơn         | Cao hơn          |
| Lập trình       | Dễ hơn           | Khó hơn (đồng bộ)|

---

## 3. Cài đặt luồng
- Luồng thường được hỗ trợ bởi các **gói luồng**: tạo, hủy, đồng bộ.
- Hai mô hình:
  - **User-mode threads** (luồng kiểu người dùng)
  - **Kernel-mode threads** (luồng kiểu nhân)

---

## 4. Luồng kiểu người dùng (User-mode threads)
✅ **Ưu điểm:**
- Tạo và hủy luồng nhanh, tiết kiệm tài nguyên.
- Chuyển ngữ cảnh nhanh.

❌ **Nhược điểm:**
- Nếu một luồng gọi hàm hệ thống bị chặn → toàn bộ tiến trình bị chặn.

---

## 5. Luồng kiểu nhân (Kernel-mode threads)
✅ **Ưu điểm:**
- Tránh được việc chặn toàn bộ tiến trình.

❌ **Nhược điểm:**
- Tạo, hủy, đồng bộ tốn chi phí (vì cần lời gọi hệ thống).
- Giảm hiệu năng tổng thể.

---

## 6. Tiến trình nhẹ (Lightweight Process - LWP)
- Kết hợp ưu điểm của cả hai mô hình trên.
- Hệ thống quản lý nhiều LWP tương ứng với luồng người dùng.
- Hỗ trợ đa CPU và tiết kiệm tài nguyên.

---

## 7. Luồng trong hệ phân tán (Distributed Systems - HPT)

### Server:
- **Đơn luồng:** Chỉ xử lý 1 yêu cầu tại 1 thời điểm.
- **Đa luồng:** Xử lý song song nhiều yêu cầu. Có thể sử dụng **Dispatcher** để điều phối luồng xử lý.

### Client:
- Tách biệt luồng giao diện và luồng xử lý logic.
- Tạo luồng riêng biệt để tương tác với từng server.

---

## 8. Mô hình tổ chức server đa luồng

| Mô hình                | Mô tả                                                        | Ưu điểm                               | Nhược điểm                                 |
|------------------------|--------------------------------------------------------------|----------------------------------------|---------------------------------------------|
| **Thread-per-request** | Mỗi request tạo 1 luồng và tự hủy sau khi xử lý             | Không cần hàng đợi, tối ưu băng thông | Quá nhiều request → tăng chi phí tài nguyên |
| **Thread-per-connection** | Mỗi kết nối tạo 1 luồng                                      | Quản lý kết nối rõ ràng               | Dễ mất cân bằng tải                          |
| **Thread-per-object**  | Mỗi object có 1 luồng quản lý                                | Rõ ràng trong xử lý RPC               | Dễ bị trễ nếu luồng bị quá tải               |

---

## 9. Bài tập yêu cầu
- **Chọn một ứng dụng cụ thể** sử dụng mô hình client-server.
- **Trình bày mô hình đa luồng**, chỉ rõ:
  - Chức năng chính
  - Mô hình tổ chức client/server
  - Sơ đồ luồng
  - Lý do lựa chọn mô hình
