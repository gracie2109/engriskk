---
name: static-web-frontend
description: Quy tắc viết giao diện web tĩnh JS thuần cho engriskk: file nhỏ, tách UI/logic/helper, không build, an toàn DOM, dùng offline.
---

# Web tĩnh, JS thuần

- Không build, không framework. Dùng ES modules (`<script type="module">`) khi tách file; đường dẫn tương đối.
- Cấu trúc đề xuất khi tách `app/index.html`: `app/css/` (tokens, layout, components), `app/js/ui/` (vẽ màn hình), `app/js/logic/` (chấm điểm, SRS, streak), `app/js/store/` (localStorage), `app/js/helpers/`, `app/data/` (ngân hàng nội dung dạng JS/JSON). Mỗi file dưới ~300 dòng.
- Design tokens bằng CSS variables (`--teal`, `--amber`, `--green`), có chế độ tối bằng `prefers-color-scheme` + nút chuyển.
- DOM: dùng `textContent`/`createElement`; chỉ dùng `innerHTML` với chuỗi tự viết, không với dữ liệu nhập.
- Chuỗi giao diện tiếng Việt, gom một chỗ để dễ sửa.
- Không phụ thuộc micro/mạng: có phương án dự phòng (hẹn giờ + tự chấm, bản offline).
- Mọi `localStorage` qua lớp store (xem skill `localstorage-data`).
