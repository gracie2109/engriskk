---
name: review-pr
description: Review diff hoặc PR của engriskk (chỉ đọc): đúng/sai, XSS, file quá lớn, tiếng Việt, localStorage, kèm bằng chứng file:dòng.
---

# Review PR

1. `git diff main...HEAD --stat` rồi đọc từng file thay đổi.
2. Thứ tự ưu tiên: bảo mật (XSS, secret) → đúng/sai và hồi quy → trùng lặp logic → dễ bảo trì (file >300 dòng, trộn UI/logic) → trình bày (cảm ứng, sáng/tối, chữ Việt).
3. Chỉ báo điều chắc chắn, kèm `file:dòng` và kịch bản lỗi cụ thể. Không sửa code khi đang review, trừ khi được yêu cầu.
4. Kiểm nội dung học: đáp án đúng, giải thích hợp lý (phối hợp skill `toeic-content`).
5. Kết luận ngắn: đã kiểm gì, chưa kiểm gì.
