---
name: browser-qa
description: Kiểm thử web engriskk bằng Playwright có sẵn: chạy server tĩnh, thao tác luồng chính, khung iPad/điện thoại, console, localStorage, chụp ảnh.
---

# Browser QA

```bash
python3 -m http.server 8080 --directory /đường/dẫn/repo &   # trang tĩnh
```

Playwright đã cài sẵn: `require('playwright')`, `chromium.launch()` không cần tùy chọn. Không chạy `playwright install`.

Kiểm tối thiểu: (1) mở `/app/`, không lỗi console; (2) onboarding → màn Hôm nay; (3) làm 1 bài, đúng/sai hiển thị đúng; (4) tải lại, dữ liệu còn; (5) sao lưu/khôi phục; (6) viewport 768×1024 và 390×844; (7) chế độ tối. Ảnh chụp người xem dùng `deviceScaleFactor: 2`, chỉ để mình xem dùng 1; thêm `--trace off` nếu chạy bộ test.

Báo cáo: ca đã chạy (pass/fail), ca chưa chạy và lý do.
