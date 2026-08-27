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
- NO AI attribution anywhere in commits or PR bodies.

## Publishing discipline

- This is a shared runtime, not a per-provider repo — a bug here can affect
  every `ubx-sdk-<provider>` repo's own Python bindings AND `ubx` itself
  (`go:embed` build input). Verify the real, separate published package
  directly (`pypi.org/project/ubx-sdk`) before claiming a fix is live — a
  commit to this repo's own `main` is NOT the same as "published"
  (`ubiquex`'s own CLAUDE.md rule 8; this exact class of mistake already
  happened once, UBI-131, reported "published" when only the monorepo's own
  copy had changed).
