# Quy ước chung

## Code
- Mỗi file nhỏ, một trách nhiệm, dưới khoảng 300 dòng. Tách UI, logic, helper, kiểu dữ liệu (JSDoc `@typedef`) thành file riêng.
- Hiện `app/index.html` là một file lớn (khoảng 100 KB). Khi sửa lớn, đề xuất tách dần thành `app/css/`, `app/js/`, `app/data/` thay vì thêm vào file cũ. Chỉ tách khi Tech Lead duyệt.
- Không thêm thư viện nếu JS thuần làm được. Nếu cần CDN, ghim phiên bản cụ thể.
- Tên biến, tên file, comment bằng tiếng Anh; chuỗi hiển thị bằng tiếng Việt.

## Git
- Nhánh: `<type>/<scope>-<short-description>` (vd `feature/app-srs-review`, `fix/store-backup-import`, `docs/agents-setup`).
- Commit message và tiêu đề PR bằng **tiếng Anh**, dạng `<type>(<scope>): <description>` (Conventional Commits; xem skill `commit`). Một commit = một lớp (schema/UI/logic/...), **không** thêm dòng Co-Authored-By hay chữ AI trong commit.
- PR mở vào `main`, mô tả nêu rõ phần đã kiểm tra và chưa kiểm tra.

## Báo cáo
- Báo cáo cho grace bằng tiếng Việt, ngắn, nêu kết quả trước, nêu rõ đã kiểm tra gì và chưa kiểm tra gì.
- Không hỏi việc nhỏ; tự quyết rồi nói đã chọn gì.

## Model
- Lập kế hoạch cho luồng mới: Opus (`claude-opus-5-5`). Viết code: Sonnet (`claude-sonnet-5-5`).
