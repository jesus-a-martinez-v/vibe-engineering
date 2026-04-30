
# GITHUB ISSUES GUIDE FOR AI DEV AGENTS

Use this guide every session. No exceptions.

---

## 1. CORE PRINCIPLES

- **GitHub Issues** — source of truth. Every task, bug, and decision lives here.

> **No issue, no work.** Never write code or make changes without a corresponding open issue.

---

## 2. INITIALIZATION — BEFORE EVERY TASK

Run this sequence before any planning or implementation:

1. **Search** — use `list_issues` to check if a matching issue already exists (match by title, area, and intent).
2. **Not found** → Create it (see Section 3).
3. **Found** → Update scope/criteria if needed, add a comment on what you're about to do and why.
4. **Create a branch** — always create a dedicated branch for the issue before writing any code. Name it `issue-<number>/<short-slug>` (e.g. `issue-42/add-users-index`). Never work directly on `main`.
5. **Comment the branch name** on the issue (covered in Section 4).

Applies to all tasks — including small changes and quick fixes.

---

## 3. ISSUE RULES

### Scope — Atomic Tasks Only
One issue = one concrete, independently completable outcome. If you can't describe the done state in one sentence, break it down further.

**❌ Too broad:** `[Auth] Build login feature` · `[DB] Design schema`

**✅ Correctly scoped:** `[DB] Create users table` · `[Auth] Implement POST /auth/login` · `[Auth] Add auth middleware`

### Title Format
`[Area] Action-oriented description`
- `[DB] Add index on [users.email](http://users.email)`
- `[API] Fix race condition in user upsert`

### Body Template
```
## Summary
What this is and why it matters.

## Scope
- What's included.
- What's explicitly out of scope (if relevant).

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Notes
Constraints, relevant files, links.
```

### Metadata
- **Label** — most specific default label that fits (see Section 7)
- **Milestone** — assign to active milestone if one exists
- **Assignee** — always assign to `jesus-a-martinez-v`; no exceptions

---

## 4. UPDATING ISSUES

Update whenever:
- **Starting work** — create the branch (see Section 2, step 4), then comment with the branch name
- **Scope changes** — edit the body; never silently widen or shrink scope
- **Blocked** — comment explaining blocker, apply `help wanted`
- **Subtask done** — check off the acceptance criterion
- **Related issue found** — add `Related to #N` or `Blocked by #N`

If work is paused or abandoned, say so in a comment.

---

## 5. CLOSING ISSUES

Close only when all acceptance criteria are met and work is merged or verified.

1. Check off every acceptance criterion in the issue body.
2. Add a closing comment summarizing what was done.
3. Reference the PR: `Closed by #<PR>`.
4. Use a closing keyword in the PR body to auto-close (see Section 6).

Never close speculatively. Incomplete work = open issue.

---

## 6. PULL REQUESTS

Every issue branch **must** be merged into `main` via a PR — never push directly to `main`. Create a PR as soon as a branch has reviewable code. Use **Draft PR** if not complete.

**Title:** `[Area] Short description` (same format as issues)

**Body:**
```
## What
What this PR does.

## Why
Closes #<issue_number>

## How
Key implementation decisions.

## Testing
What was tested and what the reviewer should verify.

## Checklist
- [ ] Self-reviewed
- [ ] Tests added/updated
- [ ] Docs updated if needed
- [ ] No unrelated changes
```

**Closing keywords** (auto-close issue on merge):
- `Closes #N` — general use
- `Fixes #N` — bugs
- `Resolves #N` — enhancements
- `Related to #N` — linked but not closed

---

## 7. LABELS

| Label | Use when |
|---|---|
| `bug` | Something is broken |
| `enhancement` | New feature or improvement |
| `documentation` | Docs missing or incorrect |
| `help wanted` | Blocked or needs external input |
| `question` | Needs clarification before work starts |
| `duplicate` | Same as an existing issue |
| `wontfix` | Acknowledged but intentionally skipped |
| `invalid` | Not a valid issue |

---

## 8. MILESTONES

- Assign to active milestone at issue creation.
- Check existing milestones with `list_milestones` before assigning.
- **Never create a milestone unilaterally** — confirm with the user first.

---

## 9. SESSION CHECKLIST

**Start:**
- [ ] Review open issues (`list_issues`).
- [ ] Run Initialization (Section 2) for each task you'll work on.


**During:**
- [ ] Create issues for anything new.

**End:**
- [ ] Comment progress on every issue touched.
- [ ] Close completed issues.
- [ ] Label new blockers `help wanted` with an explanatory comment.

---

## 10. MCP OPERATIONS REFERENCE

| Operation | When |
|---|---|
| `list_issues` | Session start, initialization search |
| `create_issue` | New task identified |
| `get_issue` | Before updating an issue |
| `update_issue` | Scope, labels, milestone changes |
| `add_issue_comment` | Progress, blockers, start/close notes |
| `close_issue` | Work complete and verified |
| `create_pull_request` | Branch ready for review |
| `update_pull_request` | Status or description changes |
| `list_milestones` | Before assigning a milestone |
