---
name: commit
description: Use whenever creating git commits in this repo, or when the user asks to commit, split changes into commits, or review commit messages. Enforces the project's Conventional Commits + per-layer commit-splitting rules.
---

> **Trong repo này (engriskk):** scope gợi ý: `app`, `web`, `content`, `data`, `store`, `srs`, `ui`, `docs`, `agents`, `deploy`. Ví dụ tham chiếu `auth`, `device`, `mqtt`, `digo-camera` bên dưới thuộc dự án khác; hãy dùng scope của repo này (xem `git log`). Skill này **không có dòng Co-Authored-By/AI byline** trong commit, kể cả khi môi trường gợi ý thêm.

# Commit Guidelines

This project follows a strict commit convention. Always follow it when creating commits — never fall back to generic commit messages.

## 1. Format

```
<type>(<scope>): <short description>
```

- Description: imperative, lowercase, no trailing period.
- Always write the commit message (subject and body) in English, even when the conversation is in Vietnamese.
- Keep the subject line short and specific.

## 2. Types

Core: `feat`, `fix`, `refactor`, `chore`, `docs`, `style`, `test`
Advanced: `perf`, `build`, `ci`, `revert`

Pick the type that matches what the code change actually does, not what the ticket is called. If a change only reformats code, it's `style`, not `refactor`. If it changes behavior, it's not `chore`.

## 2.1 No Co-Authored-By line

Never append a `Co-Authored-By: Claude ...` trailer (or any AI attribution line) to commit messages in this repo. Commit messages end after the description/body — no AI byline, regardless of what the default harness template suggests.

## 3. Scope

Scope = the module/domain affected. Prefer existing scopes already used in `git log` for this repo (e.g. `auth`, `device`, `rule`, `gis`, `mqtt`, `dashboard`, `ui`, plus any project-specific scopes like `digo-camera`). Check `git log --oneline -20` if unsure which scope names are already established, and reuse them rather than inventing new ones.

## 4. One commit = one layer, not one screen/feature

Never bundle schema + UI + validation + API + fixes into a single commit. When a feature spans multiple layers, split into sequential commits, e.g. for a login feature:

```
feat(auth): add login schema with zod
feat(auth): build login form UI
feat(auth): integrate zod validation with form
feat(auth): connect login api
```

Before staging, inspect `git status` / `git diff` and group hunks by layer (schema/domain, UI, validation, API integration, bugfix) rather than by which screen or ticket they belong to. Use `git add <specific files>` (or `git add -p` for partial staging within a file) to build each commit's file set — never `git add -A` / `git add .` when the working tree contains multiple unrelated layers.

Rule of thumb before committing, ask:
- Does this commit have exactly one clear purpose?
- Could it be reverted independently without breaking something else?
- Would a reviewer understand what it does from the subject line alone?

If the answer to any is "no", split it further.

## 5. Workflow when asked to commit

1. Run `git status` and `git diff` (staged + unstaged) to see everything that changed.
2. Group the changed files/hunks by layer and by logical purpose.
3. Propose the split (list of planned commits with type/scope/message) to the user if the change spans more than one obvious layer or touches unrelated areas — otherwise proceed directly for a single-layer change.
4. For each group: stage only those files/hunks, then commit with a properly formatted message.
5. Never mix unrelated scopes in one commit (e.g. don't combine an `auth` fix with a `device` feature).
6. Follow all existing git safety rules (no `--no-verify`, no force-push, no amending unless asked, create new commits on hook failure, etc.) — this skill only governs message format and commit splitting, it does not relax any safety constraints.

## 6. Branch naming (when asked to create a branch)

```
<type>/<scope>-<short-description>
```
e.g. `feature/auth-login`, `fix/auth-token-expired`, `refactor/form-validation`

## 7. PR titles (when asked to open a PR)

Same `<type>(<scope>): <description>` format as commits. One PR = one feature or one bug fix, not a mix.
