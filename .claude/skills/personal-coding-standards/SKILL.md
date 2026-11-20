---
name: personal-coding-standards
description: Coding standards checklist for this repo. Use when implementing features, refactoring, adding constants/config/helpers/hooks, organizing modules, deciding whether to create an abstraction, or reviewing code/diffs.
---

> **Áp dụng cho repo này (web tĩnh, JS thuần):** các ví dụ bên dưới (`app/utils/`, `digo-common`, PropTypes, styled-components, react-i18next, GitNexus, `env.sh`) lấy từ dự án khác của grace. Ở đây hãy hiểu theo cách tương ứng: hằng số/cấu hình đặt trong `app/` theo phạm vi nhỏ nhất đúng; không có React/GitNexus; đổi tên thì dùng tìm kiếm toàn repo. Quy tắc `.agents/_common/conventions.md` (file dưới ~300 dòng, commit tiếng Anh) ưu tiên hơn.

# Coding Standards (this repo)

Project rules (`CLAUDE.md`, `modular-antd-frontend`, `commit`) override this file, except security.

## Before writing code

1. Read the surrounding code and the project's `CLAUDE.md` / skills.
2. Search for existing constants, helpers, hooks, sagas, validators that already do the job
   (`app/utils/`, `digo-common/utils/`, the feature's own `constants/`, `helpers/`, `hooks/`).
3. Match the project's naming, folder layout and idioms (plain JavaScript, PropTypes,
   styled-components, react-i18next), even where they differ from your defaults.

## Where does a constant/config go?

Choose the smallest scope that is still correct:

| Scope | Use when | Example in this repo |
|---|---|---|
| Local (top of file) | Used by one file only | a debounce delay in one component |
| Feature | Shared inside one feature | `app/containers/Services/constants/index.js` |
| Shared/domain | Used by several features | `app/utils/constants.js`, `digo-common/utils/constants.js` (permissions, roles) |
| Config/environment | Varies per environment or is secret | values read via `process.env` / `env.sh` (e.g. `URL`, `TENANT_ID`) |

Promote scope only when a second real consumer appears.

## What counts as a magic value

Literal strings/numbers carrying business meaning: statuses, states, events, roles,
permissions, timeouts, limits, retry counts, routes, API paths, MQTT topics, pricing/business rules.

Not magic: `0`, `1`, `''`, array indexes, obvious math, UI-only trivial values.

## When to extract a module

Extract only if at least one holds: clear single responsibility, real reuse, or it belongs
to a specific domain.

Do NOT extract: single-use code with no domain meaning, wrappers that only forward calls,
a file created "because the rule says so".

Split a file that has grown into a grab-bag of unrelated functions, by domain.

## Over-engineering guard

- Is there a second concrete use today? If not, keep it inline.
- Does it make the current architecture more complex? If yes, don't.
- Can you explain the reason from the current code, not a hypothetical future?

## Scope discipline

- Touch only what the task needs; no drive-by refactors or renames
  (renames go through GitNexus `rename`, see `CLAUDE.md`).
- Note unrelated problems in the reply instead of fixing them.
- Don't alter business behavior; if a fix seems to require it, ask first.

## Review mode

- Report only findings you are confident in, with evidence (file/line, concrete failure scenario).
- Don't edit code during a review unless asked.
- Prioritize: security → correctness → duplication of business logic → maintainability → style.

## Security checklist

- No secrets in source, tests, fixtures, or commits.
- Don't commit real values from `.env` / `env.sh`; never expose server-only keys to the client bundle.
- Authorization enforced server-side / at the data layer, not only in UI
  (UI permission checks such as `app/utils/checkPermission.js` are convenience only).
