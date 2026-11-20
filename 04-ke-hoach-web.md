# Kế hoạch web "Lộ Trình 90 TOEIC"

Link: https://claude.ai/artifact/ScYDjdf9JF53jcjyMMgwtw  (mã nguồn: app/index.html)

## Phạm vi (bản miễn phí, không backend)
- Dữ liệu lưu trong trình duyệt (localStorage), có sao chép/dán để sao lưu. Không có tài khoản thật.
- Giao diện theo design system Stitch: teal #0f6b72, hổ phách cho streak/XP, xanh lục cho đúng, Be Vietnam Pro, thanh tab dưới (sidebar từ 900px), sáng/tối.

## Luồng theo kiểu Đậu TOEIC (cách làm, không sao chép nội dung)
Onboarding (tên, mức, mục tiêu, thời gian/ngày, ngày bắt đầu) → nhiệm vụ hằng ngày + streak + XP → lộ trình 90 ngày → luyện nghe chép (so sánh từng từ) → thi thử (ngắn/đầy đủ, ước lượng điểm) → từ vựng ôn lặp lại → ôn câu sai theo lịch 1/3/7/14/30 ngày → tiến độ (biểu đồ, độ chính xác từng Part, lịch 13 tuần).

## Nội dung gốc, tự biên soạn
40 câu Part 5, 15 câu Part 2, 4 hội thoại (8 câu) Part 3, 4 bài đọc (12 câu) Part 7, 40 câu chép chính tả, 100 từ vựng, 17 bài ngữ pháp, 6 chủ đề nói. Lịch 90 ngày lấy từ 03-lich-90-ngay.md.

## Giới hạn đã biết
- Âm thanh dùng giọng đọc của trình duyệt (speechSynthesis), khác nhau theo thiết bị.
- Micro có thể bị chặn trong khung artifact: có chế độ hẹn giờ + tự chấm.
- Điểm ước lượng chỉ để tham khảo. Ngân hàng câu hỏi còn nhỏ (75 câu), cần mở rộng dần.
- Chưa có đăng nhập đa thiết bị, chưa cài như app (PWA).
