---
name: orchestrate
description: Điều phối nhiều agent (pm, tech-lead, design, frontend, backend, dba, qc, qa, security, devops) cho một tác vụ: lập kế hoạch bằng Opus rồi code bằng Sonnet.
---

# Orchestrate

Đọc `.agents/orchestrator.md` và làm theo. Tóm tắt:

1. Tạo `.agents/_work/<yyyymmdd>-<ten>/`.
2. **pm** (Opus) viết `00-brief.md`. **tech-lead** (Opus) viết `01-plan.md`. Việc có giao diện: **design** viết `02-design.md`.
3. Thực thi (Sonnet): **dba** (schema) → **backend** (logic/dữ liệu) → **frontend**. Phần độc lập chạy song song.
4. Kiểm: **frontend-reviewer**, **qc** (nội dung), **qa** (trình duyệt), **security**.
5. **devops** chuẩn bị nhánh/PR. Orchestrator viết `99-summary.md`.
6. Việc nhỏ (sửa chữ, 1 câu hỏi) không cần cả đội: giao thẳng một agent.

Chỉ chạy agent con khi tác vụ đủ lớn; mỗi agent con tốn thời gian và token.
