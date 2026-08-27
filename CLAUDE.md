# CLAUDE.md — ubx-sdk-python

## What this is

The describe-only Python runtime for Ubiquex SDK programs — canonical
source: PyPI's `ubx-sdk`, and `ubiquex`'s own `go:embed` build input.
Coordinating repo: `github.com/ubiquex/ubiquex` (a change here can affect
`ubx` itself, not just downstream `ubx-sdk-<provider>` consumers).

## Session protocol

1. Read `STATE.md` first — current state only, rewritten not appended.
2. `STATE.md` is rewritten, not appended, as the LAST act of every session.
   Anything that becomes history moves to `HISTORY.md`.
3. Only reference Linear issue IDs given in the handoff prompt; never infer
   one.

## Git rules (strict)

- PR-only. Never self-merge — push a branch, open a PR, wait for the founder.
- Before pushing more commits to a branch with an open PR, confirm it is
  STILL open (`gh pr list --state open` or `gh pr view <n>`) — a merged PR's
  branch looks identical to any other from `git status` alone, and a push
  after merge lands nowhere near `main`, silently.
- NO AI attribution anywhere in commits or PR bodies.

## Publishing discipline

- This is a shared runtime, not a per-provider repo — a bug here can affect
  every `ubx-sdk-<provider>` repo's own Python bindings AND `ubx` itself
  (`go:embed` build input). Verify the real, separate published package
  directly (`pypi.org/project/ubx-sdk`) before claiming a fix is live — a
  commit to this repo's own `main` is NOT the same as "published". Never
  infer "published" from a commit to the monorepo's own copy alone
  (`ubiquex`'s own CLAUDE.md rule 8). This exact class of mistake already
  happened once, to this repo's own real Go sibling (`ubx-sdk-go`, UBI-131):
  a Go fix was reported "committed and pushed" across multiple session
  summaries, but only the monorepo's own copy had changed — the separate,
  real repo was never touched, still showing its original scaffold commit a
  full day later, caught only when the founder pushed back and a real
  `git log` was run against the actual separate repo, not the monorepo.
