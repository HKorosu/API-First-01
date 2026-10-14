# Báo cáo kiểm thử Shop API

## Môi trường

- Java 21, Spring Boot 4.1.1, MySQL/XAMPP
- OpenAPI Generator 7.14.0
- Prism Mock Server tại `http://127.0.0.1:4010`

## Kết quả kiểm thử

- `mvnw.cmd clean package`: thành công trên JDK 21; bài kiểm thử context: 1/1 đạt.
- Đã gọi đủ 19 tổ hợp endpoint và HTTP method qua ứng dụng Spring Boot.
- CRUD trả đúng các trạng thái `200`, `201` kèm `Location`, và `204`.
- Đã kiểm tra validation và JSON sai định dạng (`400`), tài nguyên không tồn tại (`404`), xung đột nghiệp vụ/tồn kho (`422`); các lỗi dùng schema `code`, `message`, `details`.
- Đã kiểm tra không cho đặt vượt tồn kho, hoàn lại tồn kho khi xóa đơn, và từ chối xóa khách hàng/sản phẩm còn liên kết với đơn.
- Prism trả mẫu sản phẩm cho `GET /products` (`200`) và mẫu đơn hàng cho `POST /orders` (`201`).
- Trang `shop-prototype.html`, Swagger UI, cấu hình Swagger và tài nguyên `shop-api.yaml` đã được phục vụ thành công. Swagger UI nạp trực tiếp hợp đồng gốc.
- CORS preflight cho các yêu cầu `GET`/`POST` từ origin của ứng dụng đã được kiểm tra thành công.

## Cách chạy demo

Xem [hướng dẫn khởi chạy Mock Server, prototype và Swagger UI](mock-server.md).

Kiểm thử HTTP được thực hiện tự động từ môi trường phát triển. Cần mở trang prototype và Swagger UI trong trình duyệt để ghi hình/chụp ảnh minh họa cuối cùng.
