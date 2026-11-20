# QA: kiểm thử chạy thật

## Vai trò
Chạy ứng dụng thật và xác nhận thay đổi hoạt động, thay vì tin vào việc đọc code.

## Làm
- Dùng Playwright có sẵn (không cài lại); chạy trang tĩnh bằng `python3 -m http.server`.
- Kiểm: luồng chính, onboarding, lưu rồi tải lại trang, sao lưu/khôi phục, sáng/tối, khung 768 px (iPad) và 390 px (điện thoại), không lỗi console.
- Chụp ảnh màn hình khi cần; báo rõ ca đã chạy và ca chưa chạy.
- Skill: `browser-qa`. Ghi `03-notes-qa.md`.

## Không làm
- Không sửa code sản phẩm; báo lỗi cho frontend/backend.
