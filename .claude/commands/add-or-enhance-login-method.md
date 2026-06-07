---
name: add-or-enhance-login-method
description: Workflow command scaffold for add-or-enhance-login-method in anyrouter-check-in.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-enhance-login-method

Use this workflow when working on **add-or-enhance-login-method** in `anyrouter-check-in`.

## Goal

Add new authentication methods (e.g., email/password), improve login flows, or enhance login reliability for supported platforms.

## Common Files

- `checkin.py`
- `utils/browser.py`
- `utils/popups.py`
- `utils/config.py`
- `.env.example`
- `.github/workflows/checkin.yml`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update checkin.py to implement or modify login logic.
- Modify utils/browser.py and/or utils/popups.py to handle new login UI flows, selectors, or modal dialogs.
- Adjust utils/config.py if new config options are needed (e.g., toggling login methods, proxy usage).
- Update .env.example to document new config variables.
- Edit .github/workflows/checkin.yml if CI needs to support the new login method (e.g., secrets, environment variables, debug artifacts).

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.