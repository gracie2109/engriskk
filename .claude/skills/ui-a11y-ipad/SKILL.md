---
name: ui-a11y-ipad
description: Kiểm giao diện engriskk cho iPad/điện thoại và truy cập: vùng chạm 44px, tương phản AA, sáng/tối, cỡ chữ, bàn phím, giảm chuyển động.
---

# UI cho iPad và truy cập

- Vùng chạm ≥ 44×44 px; khoảng cách đủ giữa các nút; không phụ thuộc hover.
- Tương phản chữ ≥ 4.5:1 (AA) ở cả sáng và tối; không chỉ dùng màu để báo đúng/sai (thêm icon/chữ).
- Cỡ chữ nội dung ≥ 16 px (tránh iOS tự phóng to ô nhập); dùng `rem`.
- Hỗ trợ xoay ngang/dọc; thanh tab dưới tránh `env(safe-area-inset-bottom)`.
- `prefers-reduced-motion`: giảm hoạt ảnh. Focus nhìn thấy được khi dùng bàn phím.
- `lang="vi"` cho giao diện, `lang="en"` cho đoạn tiếng Anh để đọc đúng giọng.
- Có thể dùng thêm skill `design-skills:accessibility-audit` để kiểm sâu.
