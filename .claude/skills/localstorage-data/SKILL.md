---
name: localstorage-data
description: Thiết kế và sửa dữ liệu localStorage của engriskk: schema có version, di chuyển, sao lưu/khôi phục JSON, kiểm tra khi nhập.
---

# Dữ liệu localStorage

- Một khóa chính (hiện là `KEY` trong `app/index.html`); không tự đổi tên khóa vì sẽ mất dữ liệu của grace.
- Schema có `version`; thay đổi phá vỡ thì thêm hàm `migrate(vN -> vN+1)` và test bằng dữ liệu cũ.
- Đọc/ghi bọc try/catch (trình duyệt riêng tư, khung bị chặn); lỗi thì dùng mặc định và báo nhẹ trên UI.
- Sao lưu: xuất JSON, khôi phục: kiểm tra kiểu, giới hạn kích thước (vd 1 MB), loại trường lạ, rồi mới ghi.
- Không lưu secret hay thông tin cá nhân nhạy cảm.
- Kiểm tra bằng `browser-qa`: lưu → tải lại → còn nguyên; dữ liệu cũ → vẫn mở được.
