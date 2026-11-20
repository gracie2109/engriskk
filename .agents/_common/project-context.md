# Bối cảnh dự án (mọi agent đọc trước khi làm)

**Dự án:** Lộ Trình 90 TOEIC (repo `engriskk`), web học tiếng Anh giao tiếp + TOEIC cho một người học là grace.
**Mục tiêu học:** từ TOEIC 250-300 lên 500 (cố gắng 550) trong 90 ngày, ngày 1 = 23/11/2026.

## Hiện trạng kỹ thuật
- Web tĩnh, không backend, không build step: `app/index.html` (ứng dụng luyện tập), `web/index.html` (web lộ trình), `index.html` ở gốc chuyển hướng sang `app/`.
- Dữ liệu người dùng lưu `localStorage`, sao lưu bằng sao chép/dán JSON. Chưa có tài khoản.
- Âm thanh dùng `speechSynthesis` của trình duyệt. Giao diện theo design system Stitch: teal `#0f6b72`, hổ phách (streak/XP), xanh lục (đúng), font Be Vietnam Pro, tab dưới (sidebar từ 900px), sáng/tối.
- Nội dung (câu hỏi, từ vựng, ngữ pháp) là **nội dung gốc tự biên soạn**, không sao chép từ nguồn khác.

## Tài liệu nguồn
- `README.md`, `02-chien-luoc-va-lo-trinh.md`, `03-lich-90-ngay.md`, `04-ke-hoach-web.md`.

## Ràng buộc cứng
1. Miễn phí, đơn giản, chi phí bằng 0. Đây là dự án cá nhân, không doanh thu.
2. Giao diện và giải thích bằng tiếng Việt, bài luyện bằng tiếng Anh.
3. Dùng được tốt trên iPad và điện thoại (cảm ứng, màn nhỏ).
4. Không lưu secret, token, khóa API trong repo.
5. Không hứa điểm TOEIC cụ thể; điểm ước lượng chỉ để tham khảo.
6. Không nói tài liệu trả phí là miễn phí.
