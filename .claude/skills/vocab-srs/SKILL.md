---
name: vocab-srs
description: Từ vựng và ôn lặp lại ngắt quãng cho engriskk: định dạng từ, quy tắc lịch ôn 1/3/7/14/30 ngày, ôn câu sai.
---

# Từ vựng và lặp lại ngắt quãng

**Mục từ:** `id`, `word`, `pos`, `ipa` (nếu chắc), `meaning_vi`, `example_en`, `example_vi`, `topic`. Ví dụ phải tự nhiên, thuộc ngữ cảnh công sở.

**Lịch ôn:** đúng → chuyển bậc kế tiếp trong 1/3/7/14/30 ngày; sai → về bậc 1 và thêm vào danh sách ôn câu sai. Logic thuần (nhận ngày hiện tại làm tham số) để dễ kiểm thử.

**Ngày:** dùng ngày theo múi giờ máy, so sánh bằng chuỗi `YYYY-MM-DD`, tránh lỗi chuyển ngày.

**Kiểm:** viết vài ca thử (đúng liên tiếp, sai giữa chừng, bỏ nhiều ngày).
