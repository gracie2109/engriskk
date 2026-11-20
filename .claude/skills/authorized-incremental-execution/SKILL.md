---
name: authorized-incremental-execution
description: Execute an agreed plan incrementally and autonomously, but only within explicitly authorized project scope and permissions. Use when planning or implementing coding tasks, refactors, fixes, or multi-step work.
---

> **Trong repo này:** phạm vi được phép = repo `gracie2109/engriskk`. Báo cáo cuối ngày gộp thành một tin tiếng Việt ngắn (xem `.agents/_common/conventions.md`).

# Authorized Incremental Execution

## Core rule

Once the user has approved a plan, execute it incrementally and continuously within the explicitly authorized project scope and permissions. Avoid unnecessary interruptions and routine progress updates. Provide a consolidated end-of-day report when the user is available or asks for a report.

**Principle:** Plan once, execute continuously, respect authorization boundaries, and report results at the end of the day.

## 1. Confirm authorization and scope

- Work only in the project, repository, directories, and scope the user has explicitly authorized.
- Repository or directory access does not automatically grant permission to modify it.
- Do not modify other projects, repositories, shared configurations, global settings, or unrelated files unless explicitly authorized.
- If the authorized project or scope is unclear, ask before making changes.
- Follow the host tool's actual permission controls. This skill is guidance, not a replacement for technical access controls.

## 2. Plan, then execute incrementally

- If the user asks for a plan first, inspect the authorized project and propose a practical plan with scope, steps, risks, and validation.
- Once the user agrees to the plan, begin implementation; do not stop after planning.
- Work through tasks in sequence, keeping changes small and coherent.
- Validate and test each meaningful step before moving on when feasible.
- Track completed work, remaining work, test outcomes, and blockers internally so the final report is accurate.
- Do not repeatedly ask for confirmation for actions already covered by the agreed plan and authorized scope.

## 3. Interrupt only when necessary

Pause and ask the user when:
- Authorization, requirements, or acceptance criteria are materially unclear.
- A decision would significantly change the agreed scope or architecture.
- An action is destructive, irreversible, externally visible, or risky and is not clearly authorized.
- Additional access or permissions are required.
- Continuing would require bypassing a security control or permission boundary.

When blocked, investigate safe alternatives within the authorized scope. Never bypass access controls, permission restrictions, or security safeguards.

## 4. Communication and end-of-day reporting

- Do not send routine progress messages, intermediate summaries, or repeated check-ins.
- Continue with the next agreed task whenever the current task is complete and no blocker requires user input.
- Do not claim work continues in the background after the active session or execution environment has stopped.
- At the end of the working day, when a reporting opportunity is available, provide one consolidated report containing:
  1. Completed work.
  2. Files or areas changed.
  3. Tests and validation performed, including failures.
  4. Remaining tasks and current status.
  5. Blockers or decisions needed from the user.
  6. Recommended next steps.
- If the user is not present at the end of the day, provide the report at the next available interaction. Do not imply that this skill schedules or sends messages by itself.
- Notify the user promptly if an urgent blocker or authorization issue arises; do not wait until end of day.

## 5. Definition of done

Before reporting a task as complete:
- Review the changes made within the authorized scope.
- Run relevant tests, checks, or builds when feasible.
- Clearly disclose checks that were not run and any known limitations.
- Do not conceal failures or report unverified work as successful.

## Response style

Be concise and execution-focused. Prefer making verified progress over narrating each step. Ask for user input only when it is genuinely necessary.
