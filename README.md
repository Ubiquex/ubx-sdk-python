# ubx_sdk

The describe-only Python runtime for [Ubiquex](https://github.com/ubiquex/ubiquex) SDK programs.

A program built on `ubx_sdk` never computes, never reaches a provider, and
never touches a ledger -- it describes a desired end-state (an
`ubx:intent/v1` document) and stops. `resource()` returns a `Computed`
reference, never a real value, so a resource's not-yet-known attribute can
still be wired into a sibling resource's config at describe time.

This package is the runtime shared by every `ubx sdk gen --lang py`
generated bindings package (e.g. `ubx-sdk-aws`, `ubx-sdk-google`,
`ubx-sdk-azure`, `ubx-sdk-kubernetes` -- one combined repo per provider,
UBI-138) -- a program built against it does `import ubx_sdk as ubx` and
calls `ubx.resource(...)`, `ubx.stack(...)`, `ubx.run(...)` against the
binding's own generated `ResourceBinding`/`Config` types.

## What it contains

- `ubx_sdk/__init__.py`: the real runtime, `resource`, `stack`, `run`
- `embed.go`: the real `go:embed` bridge `ubiquex` uses to compile this
  file directly into the `ubx` binary

## Install

```
pip install ubx-sdk
```

Independent convenience for editor/IDE type-checking. Not required for
evaluation to work, `ubx`'s own hermetic WASI evaluator embeds this
repo directly and never consults a real `pip install`.

## Two real roles, one source (UBI-139)

This repo is the canonical source for both:

- The real, published PyPI package (`pip install ubx-sdk`, imported as
  `ubx_sdk`) -- an independent convenience for a program author's own
  editor/IDE type-checking, never required for evaluation to work.
- The runtime `ubx`'s own hermetic WASI evaluator actually executes
  against -- `github.com/ubiquex/ubiquex` mounts this repo as a git
  submodule at `sdk/py/`, and `embed.go`'s own `go:embed` directive
  compiles `ubx_sdk/__init__.py` directly into the `ubx` binary itself
  (`pyeval` extracts it to a temp dir and preopens it into the WASI
  sandbox at evaluation time -- a real `pip install` is never consulted).

Moving or renaming `ubx_sdk/__init__.py` within this repo requires a
matching update to `ubiquex`'s own `sdk/py/embed.go`, or the whole `ubx`
binary fails to build.

See [docs.ubiquex.io](https://docs.ubiquex.io) for the full SDK guide.

## License

Apache-2.0

<!-- README-GEN:BEGIN -->
## Links

- Docs: https://docs.ubiquex.io
- Internals (architecture and design): https://github.com/Ubiquex/ubiquex-internals
- Linear board: https://linear.app/ubiquex
<!-- README-GEN:END -->
