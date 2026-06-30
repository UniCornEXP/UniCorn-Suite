# Uni-Snapshot

*Standalone add-on — requires [Uni-Inspector](uni-inspector.md)*

Local backup snapshots of your project — manual, or automatic on any of 7 triggers — with smart
retention and a per-snapshot file-level diff log. This is not version control: no branching, no
content diffs, just fast point-in-time copies you can fall back to between real VCS commits.

| Feature | What it costs you |
|---|---|
| Manual snapshot | One click |
| Automatic snapshots, 7 triggers | Configurable per-trigger, 5-minute floor on the interval |
| Rolling + unlimited pinned retention | Nothing — Editor only, auto-pruned |
| File-level diff log + folder-tree view | Nothing — computed from cheap size/timestamp comparison |
| Configurable backup scope + size estimate | Nothing — Editor only |
| ZIP export | Nothing — Editor only |

## Quick Start

1. Click **Take Snapshot Now** to copy your configured backup scope (`Assets/` and
   `ProjectSettings/` by default) into a new timestamped snapshot.
2. Pick an **Automation Plan**: **Off**, **Safe** (scheduled interval only), **Advanced** (every
   trigger on), or **Custom** (choose your own). Triggers: Scheduled Interval, Editor Startup,
   Before Play Mode, Before Script Recompile, Before Build, Before Package Import, Platform
   Switch. Before Play Mode and Before Build genuinely finish *before* the action proceeds; the
   rest are best-effort — Unity exposes no public blocking hook for them, so a very large
   project's copy could still be in flight when the triggering action completes.
3. Snapshots appear as a scrollable, zig-zagging trail of dots, oldest (left) to newest (right),
   each labeled with what triggered it — click any dot to see Added/Modified/Removed counts and a
   foldable folder tree below, with changed files colored green/amber/red, for what changed since
   the previous one.
4. Ctrl/Cmd-click a second dot to compare two arbitrary points directly instead of just "vs
   previous" — both dots glow while the comparison is active.
5. **Pin** any number of snapshots to keep them forever; everything else rolls off automatically
   past your configured "keep last N" count.
6. **Restore** always takes a fresh safety-net snapshot of your current state first, so a restore
   is never a one-way door.
7. **Backup Scope** (foldout in the header) lets you add or remove which project folders get
   backed up, with a live size estimate you refresh on demand.
8. **Export ZIP** on any snapshot saves its files as a standalone `.zip`.

> Snapshots live in a `UniSnapshots` folder next to your project's `Assets` folder — not inside
> `Library`, which Unity can wipe via Clear Cache. Add it to your VCS ignore file.

## What gets backed up

Whatever folders are listed in **Backup Scope** (`Assets/` and `ProjectSettings/` by default),
plus `Packages/packages-lock.json` unconditionally. `Library/`, `Temp/`, `obj/`, `.vs/`, `Logs/`,
`UserSettings/`, `.git/`, and Uni-Snapshot's own output folder are always excluded regardless of
scope. Embedded packages (full source under `Packages/`) aren't captured.

## Why ZIP, not `.unitypackage`

A true `.unitypackage` export of an arbitrary past snapshot isn't safely automatable from inside
the live, open Editor: the snapshot's `.meta` files carry the *original* GUIDs, which collide with
the live asset already owning those same GUIDs at its real path the instant Unity tries to import
them anywhere — even a scratch subfolder. ZIP export sidesteps this entirely (zero GUID risk) and
still gets you the same outcome: one portable file you can hand off, archive, or restore by hand
into any project later.

---
See also: [Troubleshooting](troubleshooting.md)
