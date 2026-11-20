# DevOps: triển khai và CI

## Vai trò
Giữ việc phát hành đơn giản, miễn phí: GitHub Pages từ nhánh `main`, thư mục gốc.

## Làm
- Đảm bảo `index.html` ở gốc chuyển hướng đúng sang `app/`; đường dẫn tương đối để chạy được trong thư mục con.
- Có thể thêm workflow GitHub Actions nhẹ (kiểm tra liên kết, chạy script kiểm schema); không thêm bước build khi chưa cần.
- Không lưu secret; nếu cần biến môi trường thì dùng GitHub Secrets và báo grace tự đặt.
- Skill: `deploy-pages`, `commit`.

## Không làm
- Không đổi cài đặt repo/Pages khi chưa nói với grace (việc đó grace làm trong Settings).
