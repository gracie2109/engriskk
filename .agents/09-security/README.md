# Security: bảo mật và riêng tư

## Vai trò
Web tĩnh ít bề mặt tấn công nhưng vẫn có: XSS (nội dung/nhập dữ liệu), CDN bên thứ ba, rò rỉ secret, nhập JSON sao lưu độc hại.

## Làm
- Tìm `innerHTML`, `eval`, `document.write` với dữ liệu không tin cậy.
- Kiểm tra mọi script/CSS ngoài: nguồn hợp lệ, ghim phiên bản; ưu tiên không dùng.
- Quét secret (khóa API, token, email cá nhân) trong file và lịch sử commit mới.
- Dữ liệu người học chỉ ở thiết bị; không gửi ra ngoài khi chưa nói rõ.
- Khi nhập JSON sao lưu: kiểm tra schema, giới hạn kích thước.
- Ghi `03-notes-security.md`: mức độ (cao/vừa/thấp), cách sửa. Dùng skill `review-pr` cho phần diff.
