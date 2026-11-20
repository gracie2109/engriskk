# .agents: đội agent cho Lộ Trình 90 TOEIC

Cấu trúc lấy theo một dự án khác của grace, viết lại cho dự án này (web tĩnh học TOEIC, lưu localStorage, nội dung tiếng Việt).

```
.agents/
  orchestrator.md      quy trình điều phối
  _common/             bối cảnh, quy ước, mẫu bàn giao (mọi agent đọc)
  _work/               chỗ làm việc tạm theo từng tác vụ
  01-pm … 10-devops/   vai trò chi tiết (README.md mỗi thư mục)
  skills/README.md     mục lục skill
.claude/
  agents/              12 sub-agent (Claude Code nạp tự động)
  commands/            /orchestrate /new-task /review /qa /content-check
  skills/              14 skill
```

## Điều chỉnh so với bản gốc
- **backend/dba:** dự án không có server, nên là lớp logic + lưu trữ trong trình duyệt và schema dữ liệu/ngân hàng nội dung.
- **qc = chất lượng nội dung học**, **qa = chạy thử trên trình duyệt**.
- Bỏ skill gắn dự án khác (`gitnexus*`, `modular-antd-frontend`, `review-mr-fe`); thay bằng `static-web-frontend`, `review-pr`.
- Model: kế hoạch Opus, code Sonnet.

## Skill grace gửi thêm
`commit` (từ skill "committ"), `authorized-incremental-execution`, `personal-coding-standards` (có ghi chú áp dụng), `personal-supabase-standards` (**chưa áp dụng**, repo không dùng Supabase).

## Skill đề xuất thêm và lý do
- `toeic-content`, `vocab-srs`: nội dung đúng là giá trị chính của app.
- `localstorage-data`: mất dữ liệu học là rủi ro lớn nhất; cần schema có version + sao lưu an toàn.
- `static-web-frontend`: ép giữ file nhỏ, không build, DOM an toàn.
- `browser-qa`, `ui-a11y-ipad`, `ux-copy-vi`: grace học chủ yếu trên iPad, giao diện tiếng Việt.
- `deploy-pages`: phát hành miễn phí.
- Có sẵn trong môi trường, nên gọi khi cần: `design-skills:accessibility-audit`, `design-skills:ux-writing`, `superpowers:test-driven-development`, `superpowers:systematic-debugging`.

## Cách dùng
`/orchestrate <mô tả>` cho việc lớn; việc nhỏ gọi thẳng agent (vd "dùng agent qc soát 20 câu Part 5").
