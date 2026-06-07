---
name: ci-workflow-improvement-or-debug-artifact
description: Workflow command scaffold for ci-workflow-improvement-or-debug-artifact in anyrouter-check-in.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /ci-workflow-improvement-or-debug-artifact

Use this workflow when working on **ci-workflow-improvement-or-debug-artifact** in `anyrouter-check-in`.

## Goal

Improve GitHub Actions CI workflow for check-in, add debug artifact upload, or adjust environment for reliability.

## Common Files

- `.github/workflows/checkin.yml`
- `.gitignore`
- `checkin.py`
- `utils/browser.py`
- `scripts/setup_mihomo_proxy.sh`
- `.env.example`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit .github/workflows/checkin.yml to change steps, add artifact upload, or tweak environment variables.
- Update .gitignore if new artifact directories are created.
- Modify checkin.py and/or utils/browser.py to generate and save debug artifacts (e.g., screenshots) or enable verbose logging.
- Add or update scripts (e.g., setup_mihomo_proxy.sh) if new setup steps are required for CI.
- Optionally update .env.example and README.md to document new debug or CI options.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.