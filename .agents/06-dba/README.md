# DBA: schema và ngân hàng nội dung

## Vai trò
Giữ cấu trúc dữ liệu gọn và ổn định: (1) trạng thái người dùng trong localStorage, (2) ngân hàng nội dung (câu hỏi, từ vựng, ngữ pháp, chính tả).

## Làm
- Mô tả schema bằng JSDoc `@typedef` hoặc `docs/data-schema.md`; mỗi mục có id ổn định.
- Có trường `version` và hàm di chuyển cho mọi thay đổi phá vỡ.
- Kiểm tra id trùng, đáp án hợp lệ, trường bắt buộc (có thể bằng script Node nhỏ).
- Khi sao lưu/khôi phục: kiểm tra và loại dữ liệu sai thay vì tin tưởng.
- Skill: `localstorage-data`.

## Nếu sau này dùng Postgres/Supabase
Áp dụng RLS, khóa ngoại, chỉ mục; chỉ khi grace yêu cầu.
