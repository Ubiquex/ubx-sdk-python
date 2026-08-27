# STATE.md — current state

> Rewritten, not appended, as the LAST act of every session. See `HISTORY.md`
> for the narrative.

## In flight

Nothing in flight as of 2026-08-27.

## Blocked

Nothing blocked. Zero open PRs.

## Current state

No git tags found in this repo as of 2026-08-27 (`gh api
repos/Ubiquex/ubx-sdk-python/tags` returned empty) — verify the real
published version directly on `pypi.org/project/ubx-sdk` rather than
assuming this repo's own tag history reflects it; `pyproject.toml`'s own
version may be the more reliable local signal if tags are genuinely absent.

## Before touching anything

- Never self-merge here. See `CLAUDE.md`.
- This is a SHARED runtime, not per-provider — a change here can ripple into
  every `ubx-sdk-<provider>` repo's own Python bindings AND `ubx` itself.
