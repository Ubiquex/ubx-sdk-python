# HISTORY.md — narrative archive

> Consulted only when a session needs to know why a decision was made, not on
> every open. For what's current, read `STATE.md` instead.

This file is new as of UBI-183 (2026-08-27). Real history predating it lives
in `ubiquex`'s own `HISTORY.md` (search `UBI-131`, `UBI-139`) and in this
repo's own real `git log`/merged-PR history, which is authoritative for what
actually shipped and when.

## Real, known decisions worth carrying forward

**UBI-131: a real "published" claim that wasn't**, for this repo's own real
Go sibling (`ubx-sdk-go`) — the same real risk applies here. A Go fix was
reported "committed and pushed" across multiple session summaries, but only
the monorepo's own copy had changed — `ubx-sdk-go` itself was never touched,
still showing its original scaffold commit a full day later, caught only
when the founder pushed back and a real `git log` was run against that
actual repo, not the monorepo. Verify the actual published PyPI package
directly before trusting any "published" claim about THIS repo; see
`CLAUDE.md`.
