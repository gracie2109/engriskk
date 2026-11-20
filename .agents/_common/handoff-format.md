# Định dạng bàn giao giữa các agent

Mỗi agent kết thúc bằng một ghi chú trong `.agents/_work/<task-id>/` (xem `_work/README.md`), theo mẫu:

```
## Từ: <agent>  → Cho: <agent kế tiếp>
**Kết quả:** 1-2 câu.
**File đã đổi:** danh sách đường dẫn.
**Đã kiểm tra:** ...
**Chưa kiểm tra / rủi ro:** ...
**Việc cần agent kế tiếp làm:** ...
```

Quy tắc: không bàn giao khi chưa ghi rõ "chưa kiểm tra". Không giấu việc bỏ dở.
