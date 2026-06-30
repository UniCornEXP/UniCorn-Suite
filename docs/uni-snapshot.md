# Uni-Snapshot

*Standalone add-on — requires [Uni-Inspector](uni-inspector.md)*

Local backup snapshots of your project — manual or automatic — with smart retention and a
per-snapshot file-level diff log. This is not version control: no branching, no content diffs,
just fast point-in-time copies you can fall back to between real VCS commits.

| Feature | What it costs you |
|---|---|
| Manual snapshot | One click |
| Automatic snapshots | Configurable interval, 5-minute floor |
| Rolling + pinned retention | Nothing — Editor only, auto-pruned |
| File-level diff log | Nothing — computed from cheap size/timestamp comparison |

## Quick Start

1. Click **Take Snapshot Now** to copy `Assets/` and `ProjectSettings/` into a new timestamped
   snapshot.
2. Turn on automatic snapshots and set an interval (5 minutes minimum). The copy is spread across
   many frames so it never freezes the Editor, even on large projects.
3. Snapshots appear as a scrollable, zig-zagging trail of dots, oldest (left) to newest (right) —
   click any dot to see Added/Modified/Removed counts and a foldable folder tree below, with
   changed files colored green/amber/red, for what changed since the previous one.
4. Ctrl/Cmd-click a second dot to compare two arbitrary points directly instead of just "vs
   previous" — both dots glow while the comparison is active.
5. **Pin** up to 2 snapshots to keep them forever; everything else rolls off automatically past
   your configured "keep last N" count.
6. **Restore** always takes a fresh safety-net snapshot of your current state first, so a restore
   is never a one-way door.

> Snapshots live in a `UniSnapshots` folder next to your project's `Assets` folder — not inside
> `Library`, which Unity can wipe via Clear Cache. Add it to your VCS ignore file.

## What gets backed up

`Assets/`, `ProjectSettings/`, and `Packages/packages-lock.json`. `Library/`, `Temp/`, `obj/`,
`.vs/`, `Logs/`, `UserSettings/`, `.git/`, and Uni-Snapshot's own output folder are always
excluded. Embedded packages (full source under `Packages/`) aren't captured in v1.

---
See also: [Troubleshooting](troubleshooting.md)
