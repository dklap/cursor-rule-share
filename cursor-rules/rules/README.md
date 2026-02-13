# MyVoice Cursor Rules

> Cursor Rules version of the MyVoice context management system for automatic distribution.

## Overview

This directory contains MyVoice functionality converted to Cursor Rules format (`.mdc` files with YAML frontmatter). These rules can be:

1. **Used locally** — Cursor automatically loads rules from `.cursor/rules/`
2. **Distributed via GitHub** — Team members can import rules from a shared repository

## File Structure

| File | Purpose | alwaysApply |
|------|---------|-------------|
| `myvoice-core.mdc` | Core behavioral guidelines, context management | ✅ true |
| `myvoice-setup.mdc` | Initial setup wizard for new users | false |
| `myvoice-help.mdc` | Quick reference for all commands | false |
| `trigger-session.mdc` | `/first`, `/close`, `/weekly`, `/review` | ✅ true |
| `trigger-meetings.mdc` | `/standup`, `/prep 1:1`, `/prep lt` | ✅ true |
| `trigger-actions.mdc` | `/followup`, `/decision`, `/escalate`, `/delegate`, `/celebrate` | ✅ true |
| `trigger-review.mdc` | `/review` full context verification | ✅ true |
| `trigger-recap.mdc` | `/recap` post-1:1 summary emails | ✅ true |
| `trigger-teamspace.mdc` | `/teamspace` check-in processing | ✅ true |
| `trigger-transcript.mdc` | `/transcript` meeting notes processing | ✅ true |
| `trigger-git-safety.mdc` | `/push` pre-push validation | ✅ true |
| `template-recap-email.mdc` | Email template for `/recap` | false |

## alwaysApply Explanation

- **`alwaysApply: true`** — Rule is loaded into every conversation automatically. Used for triggers that should always be available.
- **`alwaysApply: false`** — Rule is available but only loaded when explicitly referenced. Used for setup guides, templates, and reference documentation.

## Local Usage

If these files are in your workspace's `.cursor/rules/` directory, Cursor will automatically load rules with `alwaysApply: true`.

To use a specific rule that isn't auto-applied, reference it by name in your conversation.

## Team Distribution (GitHub Import)

### For Repository Maintainer

1. Create a new GitHub repository (e.g., `myvoice-cursor-rules`)
2. Copy this entire `.cursor/rules/` directory to the repository
3. Push to GitHub
4. Share the repository URL with team members

### For Team Members

1. Open Cursor Settings
2. Navigate to **Rules** or **Cursor Rules**
3. Add the GitHub repository URL
4. Rules will be imported and auto-updated when the repo changes

## Original Source Files

These rules were converted from the `shared/` directory:

| Cursor Rule | Original Source |
|-------------|-----------------|
| `myvoice-core.mdc` | `shared/initialization_prompt.md` |
| `myvoice-setup.mdc` | `shared/setup_guide.md` |
| `myvoice-help.mdc` | `shared/help.md` + `shared/triggers/README.md` |
| `trigger-session.mdc` | `shared/triggers/session.md` |
| `trigger-meetings.mdc` | `shared/triggers/meetings.md` |
| `trigger-actions.mdc` | `shared/triggers/actions.md` |
| `trigger-review.mdc` | `shared/triggers/review.md` |
| `trigger-recap.mdc` | `shared/triggers/recap.md` |
| `trigger-teamspace.mdc` | `shared/triggers/teamspace.md` |
| `trigger-transcript.mdc` | `shared/triggers/transcript.md` |
| `trigger-git-safety.mdc` | `shared/triggers/git_safety.md` |
| `template-recap-email.mdc` | `shared/templates/recap_email.md` |

The original files in `shared/` are preserved and can be used as a reference or fallback.

## Cursor Rule Format

Each `.mdc` file follows this structure:

```yaml
---
description: Brief description shown in Cursor UI
alwaysApply: true | false
---

# Rule content in Markdown
...
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Rules not loading | Ensure files are in `.cursor/rules/` directory |
| Triggers not recognized | Verify `alwaysApply: true` in frontmatter |
| GitHub import not working | Check repository URL and Cursor settings |
| Duplicate behavior | Rules may exist both locally and via import |

## Version

- **Created**: February 13, 2026
- **Architecture Decision**: See `active/decisions/Decision_Log_Architecture.md`
