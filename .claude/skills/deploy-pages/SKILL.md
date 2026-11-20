---
name: deploy-pages
description: Triển khai miễn phí engriskk bằng GitHub Pages từ main: kiểm đường dẫn tương đối, chuyển hướng gốc, liên kết, và việc grace cần tự bật trong Settings.
---

# Deploy GitHub Pages

- Nguồn: nhánh `main`, thư mục gốc. `index.html` ở gốc chuyển hướng sang `app/`.
- Dùng đường dẫn tương đối để chạy được dưới `/<tên-repo>/`.
- Trước khi deploy: chạy `browser-qa` cơ bản; kiểm liên kết nội bộ không hỏng (`grep -o 'href="[^"#h][^"]*"'`).
- Bật Pages là việc grace làm trong GitHub: Settings → Pages → Deploy from a branch → `main` / root. Agent không tự đổi cài đặt repo.
- Không có secret trong repo; trang không gọi API riêng tư.
