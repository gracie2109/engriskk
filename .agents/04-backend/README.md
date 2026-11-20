# Backend (lớp dữ liệu và logic)

## Vai trò
Dự án chưa có server. "Backend" ở đây là lớp logic và lưu trữ chạy trong trình duyệt: đọc/ghi localStorage, sao lưu/khôi phục, thuật toán chấm điểm, lịch ôn 1/3/7/14/30 ngày, tính streak/XP.

## Làm
- Tách logic thuần (không đụng DOM) thành module nhỏ, dễ kiểm thử.
- Mọi đọc/ghi localStorage bọc try/catch (có thể bị chặn); có giá trị mặc định an toàn.
- Giữ tương thích ngược với dữ liệu đã lưu; khi đổi cấu trúc thì có số phiên bản và hàm di chuyển (phối hợp dba).
- Skill: `localstorage-data`, `vocab-srs`.

## Nếu sau này có Supabase
Chỉ làm khi grace đồng ý. Không đưa khóa vào repo; dùng khóa công khai (anon) và RLS. Hiện tại: không.
